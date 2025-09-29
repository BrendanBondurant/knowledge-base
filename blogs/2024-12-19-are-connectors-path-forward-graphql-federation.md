---
type: blog
title: "Are Connectors the path forward for GraphQL Federation?"
slug: 2024-12-19-are-connectors-path-forward-graphql-federation
series: WunderGraph Blog
date: 2024-12-19
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - Connectors
  - API Design
  - Performance
  - Testing
tags:
  - graphql
  - federation
  - apollo-connectors
  - rest-apis
  - performance
  - federation-testing
  - schema-first
  - microservices
entities:
  - GraphQL Federation
  - Apollo Connectors
  - REST APIs
  - GraphQL
  - Cosmo Router
  - OpenAPI
  - JSON Schema
  - N+1 Problem
  - Schema Stitching
  - Composite Schemas
summary: |
  Deep dive into whether connectors are the right choice for GraphQL Federation. Explores the pros and cons of using @connect directives to integrate REST APIs into federated graphs, covering N+1 problems, testing challenges, response mapping complexity, and the tradeoffs between declarative configuration versus traditional GraphQL subgraphs. Analyzes when connectors work well versus when they create more problems than they solve.
faqs:
  - question: "What are connectors in GraphQL Federation?"
    answer: "Connectors are a way to @connect fields in your GraphQL schema to external data sources like REST APIs without writing resolvers. They use directives to map GraphQL fields to HTTP endpoints and handle response transformation."
  - question: "What are the main problems with connectors in Federation?"
    answer: "Connectors suffer from N+1 problems, complex response mapping for different status codes and headers, difficult testing requirements, and can leak REST API semantics into the GraphQL API. They also make entity root fields confusing and don't support proper batching."
  - question: "When should you use connectors vs GraphQL subgraphs?"
    answer: "Connectors work well for simple REST API integrations with consistent response formats. Use GraphQL subgraphs when you need complex logic, proper batching, custom authorization, or when the REST API design doesn't align well with GraphQL patterns."
  - question: "How do connectors handle the N+1 problem?"
    answer: "They don't handle it well. Connectors are inherently prone to N+1 problems because they attach to individual fields rather than supporting batch operations. This can lead to performance issues when fetching lists of entities."
canonical_url: https://wundergraph.com/blog/graphql-federation-connectors
---
Editors Note: We’ve since explored a different approach using gRPC Plugins and LLMs — see our follow-up on [declarative vs plugin-based API orchestration](https://wundergraph.com/blog/generative-api-orchestration).

Connectors aren't a new concept in the world of GraphQL.
There's quite a lot of tooling out there that allows you to connect a GraphQL API to existing data sources like a REST API using directives instead of resolvers.
However, with the rise in popularity of GraphQL Federation among enterprises,
the question arises whether connectors are the way to go for building a Federated Graph.

As we're getting more and more questions about this topic,
we decided to dedicate a blog post to it.
It's important to understand the pros and cons of using connectors in a Federated Graph
so you can make an informed decision about your Graph Architecture.

Here's one of the key questions we'll be answering in this blog post:

> Should we implement our APIs using REST and then `@connect` them to our Federated Graph?

Let's dive in!

## What are Connectors in the context of GraphQL?

Connectors are a way to `@connect` fields in your GraphQL schema to an external data source without having to write resolvers.
A typical use case for connectors is when you have an existing REST API that you want to use to extend your GraphQL schema.
Instead of writing a resolver that wraps the REST API, you simply put some directives on your schema definition and the GraphQL Server / Router takes care of the rest.

Here are some examples of this pattern.

Example 1: Connecting users and posts to a REST API

```graphql
schema
  @server(port: 8000) {
  query: Query
}

type Query {
  users: [User] @http(url: "http://example.com/users")
  posts: [Post] @http(url: "http://example.com/posts")
}

type User {
  id: Int!
  name: String!
  username: String!
  email: String!
}

type Post {
  id: Int!
  title: String!
  body: String!
  userId: Int!
  user: User @http(url: "http://example.com/users/{{.value.userId}}")
}
```

Example 2: Customers and Articles

In this example, we're using the `@http` directive to connect our GraphQL schema to a REST API.

```graphql
type Query {
  devtoArticles: JSON
    @rest(endpoint: "https://example.com/articles")
  getCustomerList: JSON
    @rest(endpoint: "https://example.com/customers")
  getCustomerById(id: ID!): Customer
    @rest(endpoint: "https://example.com/customers/$id")
  getCustomerByEmailAndName(email: String!, name: String = ""): [Customer]
    @rest(endpoint: "https://example.com/customers?q=email%20eq%20$email&q=name%20eq%20$name")
  getOrderListByCustomerId(customerId: Int!): [Order]
    @rest(endpoint: "https://example.com/orders?q=customerId%20eq%20$customerId")
}

type Mutation {
  addCustomer(name: String!, email: String!): Customer
    @rest(
      method: POST
      endpoint: "https://example.com/customers"
      postbody: "{\"name\": \"{{.Get \"name\"}}\", \"email\": \"{{.Get \"email\"}}\"}"
    )
}
```

Example 3: Posts and Comments

This example uses a `@rest` directive to connect to a REST API.

```graphql
type Query {
  post(id: Int!): JSONPlaceholderPost
    @HttpJsonDataSource(
        host: "jsonplaceholder.typicode.com"
        url: "/posts/{{ .arguments.id }}"
    )
}

type JSONPlaceholderPost {
    userId: Int!
    id: Int!
    title: String!
    body: String!
    comments: [JSONPlaceholderComment]
    @HttpJsonDataSource(
        host: "jsonplaceholder.typicode.com"
        url: "/comments?postId={{ .postId }}"
        params: [
            {
                name: "postId"
                sourceKind: OBJECT_VARIABLE_ARGUMENT
                sourceName: "id"
                variableType: "String"
            }
        ]
    )
    @mapping(mode: NONE)
}
```

This example uses a `@HttpJsonDataSource` directive to connect to a JSONPlaceholder API.

## Connectors in the context of GraphQL Federation

GraphQL Federation adds the concept of Entities and Subgraphs to your GraphQL schema.
As such, connectors need to adapt to this new paradigm which we can see in the following example:

```graphql
type Query {
  user(id: ID!): User
    @connect(
      http: { GET: "https://api.example.com/users/{$args.id}" }
      selection: """
      $.result {
        id
        company: { id: company_id }
      }
      """
      entity: true
    )

  company(id: ID!): Company
    @connect(
      http: { GET: "https://api.example.com/companies/{$args.id}" }
      selection: """
      $.result {
        id
      }
      """
      entity: true
    )
}

type User {
  id: ID!
  company: Company
}

type Company {
  id: ID!
  employees: [User]
    @connect(
      http: { GET: "https://api.example.com/companies/{$this.id}/employees" }
      selection: """
      $.results {
        id
      }
      """
    )
}
```

In this example, we're using the `@connect` directive to connect our GraphQL schema to an external data source.

## The Problems with Connectors in GraphQL Federation

The biggest upside of using connectors is that you don't have to write resolvers.
In fact, you're not even writing Subgraphs at all, and you also don't have to deploy or manage them.
It's all just configuration that lives in the Router, which drastically simplifies the development process.
However, the downsides of this approach might not be so easy to spot at first,
so let's take a closer look at some of the problems we might encounter when using connectors in a Federated Graph.

### GraphQL Federation Connectors suffer badly from the N+1 Problem

The connectors pattern is inherently prone to the N+1 Problem.
This is because connectors use directives as the primary way to connect fields to external data sources.
As lists in GraphQL are defined as a flat hierarchy,
it's only natural that the connectors pattern can only attach a nested data source to a single item instead of a list of items.

Let's revisit the Federation example from above to illustrate this point.
Imagine we had a root field that returns a list of all companies,
and a nested field that returns all employees for each company.

```graphql
type Query {
  companies: [Company]
    @connect(
      http: { GET: "https://api.example.com/companies" }
      selection: """
      $.result {
        id
      }
      """
      entity: true
    )
}

type User {
  id: ID!
  company: Company
}

type Company {
  id: ID!
  employees: [User]
    @connect(
      http: { GET: "https://api.example.com/companies/{$this.id}/employees" }
      selection: """
      $.results {
        id
      }
      """
    )
}
```

If we assume that the API call to `/companies` returns 100 companies,
we'd have to make the following 100 (N) API calls to `/companies/{id}/employees`:

1. `/companies/1/employees`
2. `/companies/2/employees`
3. ...

This results in a total of 100 (N) + 1 (root) = 101 API calls, the N+1 Problem.
This can easily lead to performance issues and slow down your GraphQL API.
It would be much more efficient if the REST API would expose a batch endpoint and/or pagination.

What's more, it's very easy to overlook this problem if we're reducing the scope of our connector Subgraph to a single entity.
Let's take a look at the following example:

```graphql
type Company @key(fields: "id") {
  id: ID!
  employees: [User]
    @connect(
      http: { GET: "https://api.example.com/companies/{$this.id}/employees" }
      selection: """
      $.results {
        id
      }
      """
    )
}

type User @key(fields: "id") {
  id: ID!
}
```

In this case, we're only really extending the `Company` entity with the `employees` field.
It's nearly impossible for us to be aware of the N+1 Problem in this case,
as we're only looking at a single entity.

Consequently, it's crucial for a user of connectors to not just be aware of the N+1 Problem,
but also to assume that another type in the graph might be returning a list of entities which we're using connectors on.

One of the challenges you'll face when using connectors in a Federated Graph is that REST APIs are not designed with GraphQL in mind.
Endpoints are typically designed to return a single entity like in the example above.

If we were using a "regular" Federation Subgraph,
the Router would send the following entities representations call to the Subgraph:

```json
{
  "query": "query($representations: [_Any!]!) { _entities(representations: $representations) { ... on Company { id employees { id } } } }",
  "variables": {
    "representations": [
      { "__typename": "Company", "id": "1" },
      { "__typename": "Company", "id": "2" },
      ...
      { "__typename": "Company", "id": "100" },
    ]
  }
}
```

Entity representations requests from the Router to the Subgraph are batched by default,
resulting in a single request to the Subgraph, independent of the number of entities we're fetching additional data for.

In the context of the question at the beginning of this blog post,
it's important to understand this limitation of connectors and the constraints they impose on the REST APIs you're connecting to.

If you're thinking of implementing Federation purely with connectors,
like an overlay on top of REST APIs,
your REST API design should be optimized for GraphQL,
which results in really awkward looking REST,
while you still have to maintain and synchronize the connector mapping configuration.
This approach is not recommended by us as it's a combination of the worst of both worlds with the added overhead of maintaining the connector part.

### Response Headers, Unions, and Status Codes

So far, we've only looked at examples with very simple REST APIs that only support a single response status code and a single response body.
However, in the real world, REST API design allows for a lot more flexibility than simple "RPC" or "CRUD" style APIs.

Some of the challenges you'll face when using connectors in a Federated Graph are:
- the response body might be different based on the status code, e.g. 200 OK, 401 Unauthorized, 404 Not Found, etc.
- the response body might be different based on the response headers, e.g. `Content-Type: application/json`, `Content-Type: application/xml`, etc.
- it's not unusual for REST APIs to use a field in the response as a discriminator for a union type, e.g. using `oneOf` or `anyOf` semantics like described in OpenAPI

What this means for Connectors is that you can't just assume that the response body is always the same.
You have to consider all the different cases and handle them accordingly,
which not just means that the configuration of such fields will be much more complex,
but also leads us to a very important question:

If a REST API returns a 401 Unauthorized status code,
what's your expected behavior in the GraphQL API?
Should we set the field to `null` and append an error to the response?
Should we implement response unions and return an `UnauthorizedError` type?
What additional information should we include in this error type?
Furthermore, how can we unify error handling across a variety of different REST APIs from different 3rd parties that are not under our control?

It's very likely that we're forced to somehow leak the REST API semantics into our GraphQL API,
which also means that our unified API layer will not look as clean and simple as we'd like it to be,
simply because we're unifying a heterogeneous set of APIs.

We could somehow add enough mapping logic to the connector logic to handle all these cases,
but this means that our Connectors configuration will become very complex and hard to maintain.

### Mapping Connector Responses to GraphQL types

Let's take a look at how such a more complex mapping configuration as described above might look like.
This is not a real example, but it should give you an idea of what we're talking about.

```graphql
type Company @key(fields: "id") {
  id: ID!
  employees: [Employee]
    @connect(
      http: { GET: "https://api.example.com/companies/{$this.id}/employees" }
      selections: [
        {
          status: 200
          selection: """
          $.results {
            id
          }
          """
        },
        {
          status: 401
          selection: """
          $.error {
            message
          }
          """
        }
      ]
    )
}

union Employee = User | UnauthorizedError

type User @key(fields: "id") {
  id: ID!
}

type UnauthorizedError {
  message: String!
}
```

Again, this is just a simplified example to illustrate the point,
but you can see how complex this can get if you have to handle a variety of different response types and status codes.

We could also sketch out an example of how a discriminator field might look like in a connector configuration:

```graphql
type Company @key(fields: "id") {
  id: ID!
  employees: [Employee]
    @connect(
      http: { GET: "https://api.example.com/companies/{$this.id}/employees" }
      selections: [
        {
          discriminator: "type"
          mappings: [
            {
              value: "user"
              selection: """
              $.results {
                id
              }
              """
            },
            {
              value: "error"
              selection: """
              $.error {
                message
              }
              """
            }
          ]
        }
      ]
    )
}

union Employee = User | UnauthorizedError

type User @key(fields: "id") {
  id: ID!
}

type UnauthorizedError {
  message: String!
}
```

Imagine you have to maintain the configuration for 1000 connectors with 5 response variations each,
that's 5000 different configurations you have to maintain and keep in sync with the REST API.

It's very likely that we're already maintaining an OpenAPI specification for the REST API.
With the connectors approach, we're more or less duplicating this work in the GraphQL API layer,
which is a huge overhead and a potential source of errors.

You might be thinking that writing resolvers for the 1k fields would be even more work than just maintaining the connector configuration,
but there's another aspect to consider: Testing!

### How do we test GraphQL Federation Connectors?

The promise of connectors is that we don't have to write resolvers.
This sounds great to management and stakeholders,
because it suggests that we can save a lot of time and money because we need fewer developers to bring the API onto the graph.

However, the reality is that for each configuration branch in a connector,
we have to write tests to ensure that the configuration is correct and matches the REST API semantics.
As such, we need at least one test for each variation in the response body and status code.

As mentioned in the beginning, we're not implementing Subgraphs with connectors.
The connector lives in the Router and is a configuration that's applied to the schema at runtime.

To be able to test the connector configuration,
we have to create a test runner that starts the Router with the Connector configuration,
mocks the REST API responses, and then runs a series of queries against the schema to ensure that the configuration is correct.
Consequently, we need a testing framework that allows us to define the mocks,
run pre-defined queries against the schema,
then caputures the responses and compares them to fixtures we've defined.

Let's list this out in a more structured way:
1. Define the REST API responses we want to mock
2. Define response fixtures for each variation in the response body and status code
3. Start the Router with the Connector configuration
4. Run pre-defined queries against the schema
5. Capture the responses
6. Compare the responses to the fixtures

Where and how will we define the mocks, fixtures, and queries,
and what approach will we use to run the tests?

At the end of the day, we might be back to writing a lot of code,
simply because testing is not possible with just a few `.graphql` files with directives.

### Entity root fields for connectors

Another aspect I'd like to highlight is the fact that connectors take a different approach to extending the Supergraph Schema compared to Subgraphs.
In a Subgraph, if we define an entity with its key fields,
there's a common understanding that the Subgraph has an entry point for this entity,
which gets resolved by the entity resolver.

By contrast, Connectors don't have this concept of entity resolvers.
Instead, we have to define a root field on the Query type and configure it to act as an entity resolver.
To recap, here's an example of how this might look like:

```graphql
type Query {
  user(id: ID!): User
    @connect(
      http: { GET: "https://api.example.com/users/{$args.id}" }
      selection: """
      $.result {
        id
        company: { id: company_id }
      }
      """
      entity: true
    )
}

type User {
  id: ID!
}
```

First of all, this can create confusion for developers who are used to the Subgraph pattern.
From the structure of the SDL, it's not immediately clear that this field is to extend the User entity.
That's because it looks like a regular root field on the Query type.

Secondly, it's not clear if this field is publicly accessible from the client schema of the Supergraph,
or if it's only accessible from within the Supergraph itself.
If we define an entity in a Subgraph, we know that only the Router can make entity representations requests to the Subgraph.

Thirdly, singular root fields, by definition, make batched entity representations requests harder to implement.
With a regular Subgraph, the Router can send an array of entity representations to the Subgraph in a single request,
which is then resolved by the entity resolver.
This works even if the entity is abstract and has multiple concrete types,
because we can use an inline fragment to specify all possible types.

With a singular root field, we have to make a separate request for each entity representation,
which can lead to the N+1 Problem as described in a previous section.
Consequently, defining entity root fields with connectors, by design, makes batched entity representations requests impossible.

### Defining a POST Body with GraphQL Federation Connectors

So far, we've mostly looked at examples where we're using the `GET` method to connect to a REST API.
Now, let's take a look at how we can use the `POST` method with a connector:

```graphql
input CreateProductInput {
  name: String!
}

type Mutation {
  createProduct(input: CreateProductInput): CreateProductPayload
    @connect(
      http: {
        POST: "https://myapi.dev/products"
        body: "$args.input { name }"
      }
      selection: "id"
    )
}
```

In this example, we're passing the field `name` from the input object to the REST API as the body of the `POST` request.
First of all, we need to learn a new syntax, almost like a scripting language, to define the body of the request.
Secondly, this will work if all the data we need to pass to the REST API is available in the input object in the right format.
But what if that's not the case?
What if we need to concatenate multiple fields or create a completely different object structure?
And what's out escape hatch if we exceed the capabilities of the connector configuration?

But that's not all.
We've got another problem to solve which is especially relevant for Mutation fields:
Input validation and sanitization!

### Input Validation & Sanitization for GraphQL Federation Connectors

In the example above, we're passing the `name` field from the input object to the REST API as the body of the `POST` request.
As this is "protected" by the Router, we can at least assume that the input object is valid.
It will definitely have the `name` field, and it will be a string.

But what if we're connecting to an internal REST API that's not properly handling input validation and sanitization?
If our input accepts numbers, should we validate that the input is valid or should we just pass it through?
Should we fail fast and return an error to the client if the input is invalid?
Or should we pass the input through and let the REST API handle the validation?

In case of the latter, we might get a 400 Bad Request response from the REST API,
so our Connector configuration should be able to handle this case properly.

This case highlights a big problem with Connectors.
Let's assume that the REST API has implemented input validation and sanitization properly.

1. We have to duplicate the input validation and sanitization logic in the Connector configuration to be able to return a meaningful error to the client.
2. We have to handle all possible response error codes and response body variations to be able to pass the REST API error message properly to the client.

In both cases, we're duplicating the work that's already done in the REST API.
In both cases, there's also a high likelihood to have drift between the REST API and the Connector configuration,
which can lead to unexpected behavior and security vulnerabilities.

In addition, it's also very confusing for your users if they report a bug with a GraphQL error message,
which you then have to trace back to the correlating REST API error to be able to understand what went wrong.
There will always be a disconnect between the language your API users are speaking (GraphQL),
and the language your backend team is speaking (REST).

### Should Supergraph design follow REST API design or the other way around?

This leads us to another very important question:

> Should we design our Supergraph to follow the design of our REST APIs,
or should we design our REST APIs to follow the design of our Supergraph?

In an ideal world, our Supergraph design is driven by the needs and use cases of our API users.
Our goal is to provide a unified API layer that's easy to use and understand,
and that abstracts away the complexity of the underlying services.
In the best case, our Supergraph design is coherent and consistent,
and follows a clear and simple pattern that's easy to understand and use.
Independent of the underlying services, or the different teams and people that are working on them,
our Supergraph should look as if it was designed by a single person,
with a single vision and a single goal in mind.

Following this line of thought, it's clear that our Supergraph design should be the leading design,
as it's the one that's exposed to our API users,
who in turn are the ones that are bringing new use cases and requirements to the table.
They are not aware of the underlying services and the complexity that comes with them,
and they shouldn't have to be.

Take a look at the following example, pause for a moment, and think about what's wrong with it:

```graphql
patchProduct(input: PatchProductInput): PatchProductPayload
    @connect(
      http: {
        PATCH: "https://myapi.dev/products/{$args.input.id}"
        body: "$args.input { name }"
      }
      selection: "id"
    )
```

We might have the need to expose the functionality to update the name of a product in our Supergraph.
However, our REST API behind the scenes doesn't directly support such an operation because REST APIs are resource-oriented compared to RPC-style GraphQL mutations.
In this case, we could somehow wrap an `updateProductName` operation around the REST API with some additional mapping logic,
or we'd have to resort to a more generic `PATCH` operation that accepts a JSON object as the body.

While the first case might not be possible due to incompatible designs,
the second case leaks the REST API semantics into our Supergraph,
which is not what we want to achieve with a unified API layer.

Furthermore, if we're exposing a `patch` field on the Supergraph,
we need to decide the behavior of fields that are not present vs fields that are `null` in the input object.

In addition, we have to ask ourselves how our Supergraph is going to look like when we have to expose a variety of REST APIs with different designs.
We might end up with a Supergraph that's a patchwork of different designs and patterns,
which is the opposite of what we're trying to achieve in the first place.

### REST API Versioning vs Supergraph Versioning

Another aspect to consider is versioning.
The general consensus in the REST API world is that you should think about versioning your API from the very beginning.
This is because once you've exposed an API to the public, you can't change it anymore without breaking existing clients.

In the GraphQL world, the situation is a bit different.
There's just one schema that's exposed to the clients,
and the specification doesn't provide any tools to version the schema.
Instead, there's the general recommendation to simply have a single schema,
to use deprecation directives to mark fields as deprecated,
and to safely evolve the schema over time without breaking existing clients.

With Connectors in the mix, we have to bridge the gap between these two worlds.
While we're able to deprecate individual fields in a GraphQL Schema,
we can only version whole REST API endpoints or sunset them.

This might lead to a situation where we have to maintain multiple versions of the same REST API endpoint,
just because we're using them in different Connector configuration.
Consequently, we might end up with more (Micro-)Services running compared to a pure GraphQL Federation approach.

## Conclusion

Connectors are a very powerful tool that allows you to bring existing REST APIs onto your Graph without having to implement,
deploy, and manage Subgraphs.
This is especially useful if you're working with a lot of different REST APIs from different 3rd parties,
and the goal is to unify them into a single API layer without much effort.

However, Connectors are not a silver bullet,
and they come with a lot of challenges that you have to be aware of before you start using them in a Federated Graph.
As we've discussed, Connectors are prone to the N+1 Problem,
the configuration can become very complex if you have to handle different response types and status codes,
and testing is not as straightforward as it might seem at first.
In addition, Connectors might lead to a situation where you're leaking the REST API semantics into your GraphQL API.
Another aspect to consider is input validation and sanitization.

If we're aware of the trade-offs and challenges,
Connectors can be a powerful tool to extend your federated graph with existing REST APIs.

However, if you're starting from scratch and thinking about your Graph Architecture,
it might be a better idea to implement Subgraphs instead of solely relying on Connectors to build out your Federated Graph.