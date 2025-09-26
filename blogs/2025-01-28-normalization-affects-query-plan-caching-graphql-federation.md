---
type: blog
title: How Normalization affects Query Plan Caching in GraphQL Federation
slug: 2025-01-28-normalization-affects-query-plan-caching-graphql-federation
series: WunderGraph Blog
date: 2025-01-28
author: Jens Neuse
co_author: Sergiy Petrunin
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - Query Optimization
  - Cache Performance
  - Query Planning
tags:
  - graphql
  - graphql-federation
  - performance
  - caching
  - query-optimization
entities:
  - GraphQL Federation
  - Query Normalization
  - Query Plan Caching
  - WunderGraph
  - Cosmo Router
summary: |
  Explore how normalization transforms GraphQL queries into canonical forms to boost query plan cache hits in Federation. This deep dive covers three normalization approaches—flattening, variable extraction, and deterministic naming—and explains how the right strategy can dramatically improve performance and analytics while reducing cache storage overhead.
faqs:
  - q: Why is normalization important in GraphQL Federation?
    a: Normalization transforms queries into a canonical form so the query planner can generate more efficient and cacheable query plans. It also increases cache hit rates by reducing variation in query structure caused by aliases, fragments, or argument formatting.
  - q: What are the three forms of normalization in GraphQL?
    a: The three forms are: 1. Flattening the query while preserving structure, which is useful for validation and error reporting. 2. Exporting inline arguments into variables, which is ideal for analytics. 3. Deterministic variable naming, which is designed for optimal query plan caching by making semantically equivalent queries identical in structure.
  - q: Which normalization form improves query plan caching?
    a: The third form — deterministic variable naming — ensures that semantically identical queries generate the same cache key, maximizing the query plan cache hit ratio. It standardizes variable names regardless of what the client sends.
  - q: Why doesn't flattening help with caching?
    a: Flattening inlines arguments directly into the query. Since each variation of argument values produces a unique query string, it leads to a low cache hit ratio and inflated cache storage.
  - q: How do @skip and @include directives affect normalization?
    a: They increase complexity because conditional logic can change query structure. The router must either handle them during planning, execution, or normalization. Removing excluded fields at normalization time is efficient but may require separate query plans for each condition.
  - q: Why not just use optimized REST APIs instead?
    a: "While REST can work for specific use cases, scaling to many teams and services leads to organizational complexity. GraphQL Federation addresses this by enabling unified schemas across decentralized services, reducing the need to manually coordinate S × L × O × W combinations."
---

{% partial file="blog-callout.md" /%}

Query Plan Caching in GraphQL Federation is one of the most important features to optimize the performance of your GraphQL API.
It allows the Router (GraphQL API Gateway) to cache the generated query plan for a specific query and reuse it for subsequent requests.

Query Plan Caching can save up to 10 seconds (or more in extreme cases) of latency per request.
It's not just an optimization, but simply a necessity for any GraphQL API that is used in applications sensitive to latency,
such as mobile apps, web apps, etc.

However, there is a catch: We cannot benefit from a cache if the hit ratio is low.
This article dives into the depth of Query Plan Caching and explains how Normalization affects the hit ratio of the cache.

You'll learn that there's not just one form of normalization.
We will explore the three main forms of normalization, their strengths and weaknesses,
and which use cases they are best suited for.
It'll be interesting to see that one form of normalization is great for caching query plans,
while another one is more suitable for analytics and monitoring.

## What are Query Plans in GraphQL Federation and what's their relationship with Normalization?

In GraphQL Federation, the Router is responsible for fetching data from multiple services (Subgraphs) and merging the results into a single response.
As the nature of GraphQL is to allow clients to request exactly the fields they need,
the Router cannot know ahead of time how to fetch the data from the Subgraphs.
Consequently, based on the incoming query and the meta information about which Subgraph can provide which fields,
the Router generates a query plan that describes exactly what fetches need to be made to the Subgraphs in what order.
In addition, the query plan also contains information about how to merge the results from the Subgraphs into a single response to comply with the client's query.

Generating a query plan is a complex and time-consuming CPU-bound operation that is very hard to parallelize.
You can think of it as a compiler that traverses the query AST,
checks which Subgraph can provide which fields,
and then generates the optimal fetch plan based on the available information.
Once the initial query plan is generated,
additional post processing steps are applied to optimize the plan further,
e.g. by understanding the dependencies between fetches and parallelizing them where possible.

The query planner is very similar to a compiler in the sense that it takes a human-readable query and generates an instruction set that can be executed by the Router.
For this instruction set, we've developed an execution engine that is very similar to a virtual machine,
but optimized for a very specific use case instead of being a general-purpose virtual machine: Fetching and merging data from multiple Subgraphs.

Normalization is a process that is applied to the query before we pass it to the query planner.
This is a crucial step because it allows the query planner to make assumptions about the structure of the query.
In addition, normalization increases the hit ratio of the query plan cache as we will see later in this article.

## Why is Normalization important for the GraphQL Federation Query Planner?

Let's consider the following query:

```graphql
query {
    user(id: "1") {
        id
        name
        email
    }
}
```

Next, let's look at another query:

```graphql
query {
    user(id: "1") {
        ...UserFields
    }
}

fragment UserFields on User {
    id
    name
    email
}
```

Both queries are semantically equivalent.
They will be executed in exactly the same way and return the same result.
However, the second query uses a fragment to define the fields that should be fetched.
This is a common pattern in GraphQL and a convenient way to define reusable sets of fields.

That being said, they are a problem for writing a query planner because they add complexity to traversing the query AST.
Ideally, we would like to focus on the query planning logic without having to worry about all the different ways a query can be written.
This is where normalization comes into play.

After normalization, both queries will be transformed into the exact same representation.
But there's not just one single form of normalization.

## The three forms of Normalization in GraphQL

Before we dive into the details of Normalization,
let's take a step back and look at the structure of GraphQL queries.

Here's a simple example schema:

```graphql
type Query {
    sum(a: Int! b: Int!): Int!
}
```

Let's make the simplest possible query:

```graphql
{ sum(a: 1 b: 2) }
```

This is an anonymous query that directly calls the `sum` field on the `Query` type.
It doesn't have a name, it's not using variables, and it doesn't have any aliases or fragments.
Typically, a GraphQL client would send this query to the Router as a JSON object:

```json
{
    "query": "{ sum(a: 1 b: 2) }"
}
```

Next, we could add a name to the query:

```graphql
query MyQuery {
    sum(a: 1 b: 2)
}
```

The corresponding JSON object would look like this:

```json
{
    "query": "query MyQuery { sum(a: 1 b: 2) }"
}
```

As this is a single query in the document, we can omit the `operationName` field from the JSON object,
but typically a GraphQL client would still include it for clarity:

```json
{
    "query": "query MyQuery { sum(a: 1 b: 2) }",
    "operationName": "MyQuery"
}
```

You might have noticed that this query is not re-usable.
For every pair of numbers we want to sum, the query text will be different.
To give the query re-usability, we can use variables:

```graphql
query MyQuery($a: Int!, $b: Int!) {
    sum(a: $a b: $b)
}
```

This will lead to the following JSON object:

```json
{
    "query": "query MyQuery($a: Int!, $b: Int!) { sum(a: $a b: $b) }",
    "operationName": "MyQuery",
    "variables": { "a": 1, "b": 2 }
}
```

Now we have a query that is re-usable.

### GraphQL Normalization Form 1: Flatten the query but keep the structure

The first form of normalization is to flatten the query but keep the structure.
This brings the query into a canonical form that is easy to use by other tools like the query planner.

Let's take a look at the following example:

```graphql
query ($a: Int!, $b: Int!) {
    ... on Query {
        someQueries {
            ... on Summary {
                ... MyMath
            }
        }
    }
    ... on Query {
        alias: someQueries {
            ... on Summary {
                ... MyMath
            }
        }
    }
}

fragment HomeTask on Tasks {
    ... on Summary {
        sum(a: $a, b: $b)
    }
}

fragment MyLesson on Lessons {
    ... HomeTask
}

fragment MyMath on Math {
    ... MyLesson
}
```

You might already see that although the query looks quite complex,
after normalization it looks rather simple:

```graphql
query {
    someQueries {
        sum(a: 1, b: 2)
    }
    alias: someQueries {
        sum(a: 1, b: 2)
    }
}
```

For completeness, here's the corresponding GraphQL Schema:

```graphql
type Summary implements Tasks & Lessons & Math {
    sum(a: Int!, b: Int!): Int!
}

interface Tasks implements Lessons & Math {
    sum(a: Int!, b: Int!): Int!
}

interface Lessons implements Math {
    sum(a: Int!, b: Int!): Int!
}

interface Math {
    sum(a: Int!, b: Int!): Int!
}

type Query {
    someQueries: Summary
}
```

The first form of normalization is very important because it allows us to validate the query against the GraphQL Schema.
The advantage of this form of normalization is that we can report errors to the client in a meaningful way.
For example, if the argument type of the `a` arg in the first `sum` field is not an `Int!`, we can tell the client exactly on which path in the query the error occurred.
The two other forms of normalization will change the original query structure so much that it'll be harder for the client to understand where the error occurred.

For simplicity reasons, we have omitted a lot of details in the normalization process.
If you're interested in further details, here's a short list of additional tasks that are typically part of this normalization step:
- Input value coercion (e.g. converting a single value into a list)
- Merging selections (e.g. merging two identical fields into one)
- Deduplication of selections (e.g. removing duplicate fields)
- Removing unnecessary inline fragments (e.g. removing inline fragments without directives)
- Removing fragment definitions (once they are inlined)

That said, the first form of normalization also has its downsides.
We cannot use it for analytics, and we cannot use it for caching query plans.
The reason is that the query contains inline arguments.
For each different set of arguments, we would generate an entry in the analytics database or the query plan cache.
Imagine if our users would call the `sum` field with hundreds of thousands of different pairs of numbers,
we would never really understand how popular this query is.
In addition, the query plan cache would be flooded with entries that are almost identical.

### GraphQL Normalization Form 2: Exporting the variables

The second form of normalization is to export the variables.
Exporting inline arguments into variables has huge benefits for other tools.
An argument could be a scalar, but it could be a list or an input object.
Input objects could contain other input objects, scalars, or variables.

By exporting and normalizing the variables, tools like validation, analytics, and caching don't have to deal with this complexity.
They can build on top of the assumption that every argument is a variable,
and the variables are a simple JSON object.

Here's the same query as above, but with the variables exported:

```graphql
query MyQuery ($a: Int!, $b: Int! $c: Int! $d: Int!) {
    someQueries {
        sum(a: $a, b: $b)
    }
    alias: someQueries {
        sum(a: $c, b: $d)
    }
}
```

The JSON including the extracted variables would look like this:

```json
{
    "query": "query MyQuery ($a: Int!, $b: Int! $c: Int! $d: Int!) { someQueries { sum(a: $a, b: $b) } alias: someQueries { sum(a: $c, b: $d) } }",
    "operationName": "MyQuery",
    "variables": { "a": 1, "b": 2, "c": 1, "d": 2 }
}
```

For each argument, we create a new (unused) variable starting with `a` to `z`, then `aa` to `az`, and so on.

The second form of normalization is great for analytics.
It doesn't matter which pair of numbers the user wants to sum.
If we create a hash of the query text, we can group all queries that are semantically equivalent.

However, the second form of normalization is still not ideal for caching query plans.
For analytics, it's ok to keep the variable names as they are.
This even serves a purpose because the user can better understand the query as it's very close to the original query.
But for caching query plans, this form can still negatively affect the hit ratio of the cache.

### GraphQL Normalization Form 3: Deterministic variable names

The third form of normalization is to use deterministic variable names instead of combining user-defined variable names with exported variables.

Let's get back to the query from the very beginning:

```graphql
query ($a: Int!, $b: Int!) {
    sum(a: $a b: $b)
}
```

Here are a few examples of how clients could send this query to the Router:

```graphql
query MyQuery($e: Int! j: Int!) { sum(a: $e b: $j) }
query MyQuery($j: Int! e: Int!) { sum(a: $e b: $j) }
query MyQuery($k: Int! x: Int!) { sum(a: $k b: $x) }
query MyQuery($a: Int!) { sum(a: $a b: 2) }
query MyQuery($b: Int!) { sum(a: 1 b: $b) }
query MyQuery { sum(a: 1 b: 2) }
query MyQuery { sum(a: 20 b: 11) }
```

Technically, all these queries want to execute the `sum` field, just with different arguments.
The problem is that after the second form of normalization, most of the queries would look different as they have different variable names.

The third form of normalization solves this problem by using deterministic variable names.
The algorithm walks depth-first through the query and assigns each variable a deterministic name,
starting with `a` to `z`, then `aa` to `az`, and so on.
Finally, the algorithm sorts the variables alphabetically.

After this normalization step, all queries from above would look like this:

```graphql
query MyQuery($a: Int!, $b: Int!) { sum(a: $a b: $b) }
```

If we now create a hash of the query text, we will have a 100% cache hit ratio for all queries that are semantically equivalent.
As such, the third form of normalization is perfectly suited for caching query plans.
The downside of the third form of normalization is that it's not great for analytics because the query text might look very different from the original query.

Furthermore, there's another problem with the third form of normalization.
Let's assume a client sends a query with a variable name `b` which gets normalized to `a`.
The Router executes the query and something goes wrong which results in an error.
If the Router wants to send back a meaningful error message to the client,
it has to map the variable name `a` back to `b` in the error message,
otherwise the client wouldn't understand the error message.

To solve this problem, we're generating a mapping table that maps the original variable names to the normalized variable names.

## Bonus: How the `@skip` and `@include` directives affect Normalization and the Query Planner

There's one more thing that heavily increases the complexity of Normalization and the query planner: The `@skip` and `@include` directives.

Let's take a look at the following query:

```graphql
query MyQuery ($a: Int!, $b: Int! $c: Int! $d: Int! $withAlias: Boolean!) {
    someQueries {
        sum(a: $a, b: $b)
    }
    alias: someQueries @include(if: $withAlias) {
        sum(a: $c, b: $d)
    }
}
```

Depending on the value of the `withAlias` variable, the `alias` field will be included or skipped.
What sounds like a simple task can actually be quite complex,
because we have to decide whether the processing of the `@include` directive should be done during normalization,
during query planning and execution,
or if we push the problem to the Subgraphs.

One solution is to keep the `@include` directive in the query and let the Subgraphs decide whether to include the field or not.
This is a simple solution that some GraphQL Routers use,
but it has the downside that we might be sending requests to Subgraphs that are completely unnecessary.

Another solution is to include the logic for the `@include` directive in the query plan and have the execution engine decide which fetches to make and which to skip,
based on the value of the `withAlias` variable.
This solution is not just complex to implement,
but it also means that generating the query plan can take very long,
even if we're "excluding" a lot of fields.

The third solution is to normalize the query with the `@include` directive and simply remove selections that are not included.
The downside of this solution is that we have to create one query plan for each combination of `@include` and `@skip` directives.
The upside is that we're only ever planning the fetches that are actually needed and neither the execution engine nor the Subgraphs have to deal with the complexity of the `@include` directive.

## Summary of the three forms of Normalization

Let's recap the three forms of normalization.

### Original Query

```graphql
query MyQuery($j: Int!) { ... on Query { sum(a: $j b: 2) } }
```

### Form 1: Flatten the query but keep the structure

```graphql
query MyQuery($j: Int!) { sum(a: $j b: 2) }
```

### Form 2: Exporting the variables

```graphql
query MyQuery($j: Int! $a: Int!) { sum(a: $j b: $a) }
```

### Form 3: Deterministic variable names

```graphql
query MyQuery($a: Int! $b: Int!) { sum(a: $a b: $b) }
```

## Comparison of the complexity of GraphQL Federation and REST APIs

You might wonder if all this complexity can be justified when we could just create a simple optimized REST API,
and you're absolutely right.

Technically, we could create a REST API that is optimized for the specific use case of a client.
But there's a catch.
The larger your organization grows, the more use cases you have to support.
In addition, it's very unlikely that you can grow your organization with a single monolithic API.
You will have to split your API into multiple services,
and before you know it, you're in a situation where a large number of use cases are dependent on a large number of services.

The resulting problem is not a technical one, but an organizational one.
S products with L use cases dependent on O services provided by W teams.
If the complexity goes out of hand, you'll end up with S * L * O * W different combinations,
leading to a very inefficient organization.

Instead of manually covering all these combinations with optimized REST APIs and BFFs (Backend for Frontends),
GraphQL Federation can replace the "S" with an "F", the "L" with an "A", the "O" with a "S", and the "W" with a "T",
making your organization F * A * S * T again.

## Conclusion

In this article, we've learned that Normalization is a crucial step in the GraphQL Federation query planning process.
We've explored the three main forms of normalization and their strengths and weaknesses.
While the second from of normalization is great for analytics,
only the third one is perfectly suited for caching query plans.

You will have noticed that GraphQL Federation comes with a lot of complexity,
and you might wonder if it's worth it.
Here's my take on this:

{% quote author="Jens Neuse" %}
It's better to have a complex but well understood piece of software than a simple solution that brings a lot of organizational complexity.
{% /quote %}

---

{% faq /%}

---