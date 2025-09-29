---
type: blog
title: "The Evolution of GraphQL Federation and the Entity Layer"
slug: 2025-09-09-evolution-graphql-federation-entity-layer
series: WunderGraph Blog
date: 2025-09-09
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - Entity Layer
  - API Architecture
  - Schema Evolution
  - Enterprise APIs
tags:
  - graphql-federation
  - schema-stitching
  - supergraph
  - microservices
  - enterprise
  - api-design
entities:
  - GraphQL Federation
  - Entity Layer
  - Schema Stitching
  - Apollo Federation
  - Composite Schemas
  - GraphQL
  - Facebook
  - Meta
  - Apollo GraphQL
  - ChilliCream
  - GraphQL Foundation
  - Twitter Strato
  - TAO
  - Entgo
  - Cosmo Connect
  - Cosmo Router
  - WunderGraph
summary: |
  Traces the evolution of GraphQL from monoliths to Schema Stitching to Federation, explaining why the Entity Layer has become the foundation for unified APIs. Covers how GraphQL shifted from frontend-driven technology to enterprise organizational solution, the problems with Schema Stitching, and how Federation with entities enables collaborative schema design and governance at scale. Explains the nine key principles of the Entity Layer and its role in building distributed systems.
faqs:
  - question: "What is the Entity Layer in GraphQL Federation?"
    answer: "The Entity Layer is a conceptual foundation for building unified APIs. It models domains as entities and relationships, enforces consistency across services, and centralizes concerns like batching, caching, access control, and schema governance."
  - question: "Why did Schema Stitching fall out of favor?"
    answer: "Schema Stitching allowed combining multiple GraphQL schemas but lacked composition checks, made execution unpredictable, and required constant maintenance of the stitched schema. Federation solved these issues with entities and composition checks."
  - question: "How has GraphQL's role changed over time?"
    answer: "GraphQL started as a frontend-driven technology for mobile and SPAs, but today it's mainly adopted by enterprises to solve organizational challenges—distributing APIs across multiple teams and services through Federation."
  - question: "Why is GraphQL a good fit for unified APIs?"
    answer: "GraphQL's SelectionSet lets consumers request exactly what they need. This enables efficient data fetching, hides backend complexity, and provides a consistent API contract across multiple services."
canonical_url: https://wundergraph.com/blog/graphql-federation-history-entity-layer
---
## TL;DR

GraphQL started as a monolithic API model and grew through Schema Stitching into modern Federation.
Along the way, enterprises discovered that distributing APIs across teams requires a unifying layer.
That’s where the Entity Layer comes in: a foundation for modeling the domain as entities, enforcing graph integrity, and supporting collaborative schema design and governance to ensure consistency.
This post traces that evolution and explains why the Entity Layer is now a key building block for unified APIs.

Want the practical differences? Read the companion blog [Cosmo Connect vs Apollo Federation vs GraphQL Federation](https://wundergraph.com/blog/cosmo-connect-vs-apollo-federation-vs-graphql-federation).

## The Problem: Building a Unified API Layer

Across all the different approaches,
it's clear there's agreement on some core principles:

1. A unified API Layer is needed (I'll explain why in a bit)
2. [GraphQL](https://graphql.org/) is the ideal foundation (this will be covered in the next section)
3. Entities are the core building block to distribute a GraphQL Schema across multiple services

The reason we need a unified API Layer is simple.
As your organization grows,
you will continue to add more and more use cases,
which are your API consumers.
To meet all their requirements,
your engineering team won't just add more APIs,
but the team itself will also grow.

You'll typically start with one or a small number of services implementing core business logic,
and after some time, especially if you're a fast-growing, successful company,
you'll quickly scale from 3 teams to 20 or even 100,
and from 5 services to 50 or 300.

Now, there are two ways to approach this:

1. Build all APIs fully in isolation, put them in a catalog, and let API consumers pick and choose which APIs to use. This way, integration is decentralized and the burden is on the API consumer
2. Build a unified API Layer, where integration is centralized and the cost is paid upfront by the API producer

## Why Enterprise API Integration should be centralized, on the producer side

The traditional way to build enterprise APIs is to split your domain across multiple services,
expose these services through REST or gRPC,
and then publish the API contract to an API developer portal.
Protected by an API Gateway,
consumers can explore all existing APIs through a catalog,
and get access with an API key.

However, this approach has many drawbacks.
There's usually little to no collaboration across teams,
which means specifications across services are often inconsistent.
I once worked with a car manufacturer
that had 13 different definitions for the 'Car' entity.
You might request a car from one service and assume that the unique identifier is the same across all services,
but that simply wasn't the case.
The lack of naming conventions and a shared understanding of the domain puts the API consumer in a very bad position.

If, on the other hand, we're building a unified API Layer,
that is, a single GraphQL Schema across all services,
the burden of understanding the domain and the API contract is no longer on the API consumer.
It is now an upfront cost on the API producer side.

Now ask yourself,
what's the better approach?
Isn't it much more efficient for API producers to agree once on what a 'Car' is,
what fields it has,
and which field serves as the unique identifier?
Or should every API consumer who wants to use the 'Car' entity have to understand the domain and API contract of 13 different services?

The answer should be obvious.
API producers have a lot more knowledge about the domain,
they have relationships with the people behind neighboring services,
and it's cheaper and more efficient to agree on a single definition of an entity, rather than putting the burden on the API consumer to figure out that two 'Car' objects are not the same thing.

## Why GraphQL is the optimal choice to build a unified API Layer

If you have followed the narrative so far,
you might agree that a unified API Layer is the way to go,
but it's not yet clear why GraphQL is the optimal choice for the implementation.

{% quote author="Jens Neuse" %}
GraphQL is a great fit for building a unified API Layer because of the **SelectionSet** concept.
It allows API consumers to request only the data they need,
which automatically limits the amount of information that will be requested by the underlying services.
{% /quote %}

Without SelectionSets,
we'd request an infinite amount of data on every path.
We could implement similar functionality with a [REST](https://www.ibm.com/think/topics/rest-apis) API,
but that would essentially mean reinventing GraphQL on top of REST.
With GraphQL, we have a very simple concept to model relationships between entities,
and we can then use the SelectionSet concept to express which fields we'd like to request.

With REST APIs, we could model relationships between entities with links and sparse field sets.
There's nothing wrong with that,
but it puts the burden on the API consumer to understand the API’s structure
and how to use the links to navigate it.

Let me give you an example to make this more concrete.
Here's a user type defined in one service,
extended by another service with payroll information.

```graphql
# User Service
type Query {
  user(id: ID!): User
}

type User @key(fields: "id") {
  id: ID!
  name: String!
}
```

Next, we'll add a new field to the User type in the Payroll Service.

```graphql
# Payroll Service
type User @key(fields: "id") {
  id: ID!
  payrollInformation: PayrollInformation
}

type PayrollInformation @key(fields: "id") {
  id: ID!
  salary: Float!
  department: String!
  position: String!
  startDate: Date!
}
```

A client could make the following request to our Supergraph:

```graphql
query {
  user(id: "1") {
    id
    name
  }
}
```

As we're not requesting the `payrollInformation` field,
the Payroll Service won't be called.

Next, let's create a more complex request that also requests the `payrollInformation` field.

```graphql
query {
  user(id: "1") {
    id
    name
    payrollInformation {
      id
      salary
      department
      position
      startDate
    }
  }
}
```

Here, the Supergraph Router will call the User Service to get the basic user information,
and then use the `@key` field to call the Payroll Service to get the additional payroll information.
In this case, the `user.id` field is used as the key to uniquely identify the user.

The benefits of building our unified API on GraphQL are:
- all service teams have a simple mechanism to agree on the definition of an entity
- if an entity is shared across multiple services, all involved teams have to agree on the unique identifier(s)
- the Router always makes the minimum number of fetches to the underlying services
- nested entity requests are automatically batched
- from an API consumer perspective, the API contract is simple and easy to understand, it looks like a single monolithic GraphQL Schema
- the complexity of the underlying services is completely hidden from the API consumer
- API consumers can easily fetch relationships between entities without having to read through an endless list of REST endpoints
- new fields can be added to an entity without changing the API contract

---

Let's be clear,
a unified API Layer can be built on top of REST APIs,
but you’d have to solve a few small problems,
for example...

- when adding new fields to an entity, they should not be automatically added to existing endpoints, they should only appear in the response if the client explicitly requests them
- when we add new entities to the API, there should be a system that checks across all endpoints to enforce that entities are not duplicated, use the same field names and types for the same values, use exactly the same fields as unique identifiers, and generally ensure that every field can be resolved
- relationships between entities must be modeled consistently across all endpoints, and not following the rules for links and sparse field sets should trigger build-time errors
- enforce across all endpoints that entities are not duplicated
- build a developer portal with a Playground that makes it very easy to navigate the API, follow relationships, and test the API

You can solve all of these problems on your own,
or you just go with GraphQL.
But as we’ll see in the next section,
GraphQL is not the same as it was in the past.
This year, the Query language is more than 10 years old, and it has changed a lot,
especially in usage patterns and the tooling around Federation.

## Tech Twitter and GraphQL: what nobody talks about

Before we get into the history and evolution of GraphQL,
I'd like to comment on the relationship between GraphQL, Tech Twitter, and Hacker News,
and take a reality check on what's really happening in large enterprises.

A lot of people on Tech Twitter and Hacker News have nothing but negative things to say about GraphQL.
There's very little nuance in the discussions,
and one pattern that I often see is that the people who are complaining the loudest are the ones with very little experience using APIs at very large scale.

The sweet spot for GraphQL, especially with Federation,
is when more than 3 teams contribute to an API that spans a large domain.
That said, you don't have to be an engineering department of thousands of engineers to benefit from GraphQL.
Tools like Relay Client, Fragments, and many more are very useful for building high-quality web and mobile applications.
With the recent development of LLMs,
there is now another type of API consumer that benefits from a query language.
The unit that determines the reliability and cost of using an LLM is the amount of tokens that an LLM has to process.
Being able to request exactly the data you need, and nothing more, is a powerful feature for LLMs that comes for free with GraphQL.

Coming back to the topic of Tech Twitter and Hacker News,
here’s what we see happening in enterprises compared to what people say on social media.

Companies that have built APIs for a very long time are suffering from the lack of a unified API Layer.
Terms like 'API Sprawl' and 'API Fatigue' are common,
and the reason for that is that they don't have a centralized platform to manage the full lifecycle of their APIs.
They are using API Gateways to protect and secure their APIs,
but often, topics like 'API Design' and 'API Governance' are handled in a fragmented way.

Companies that have been successfully using GraphQL Federation for a few years now speak a different language.
They have a centralized platform, they have Schema Reviews and Governance in place.
Here are some of the things we're currently working on with our customers:

- For one [Fortune 500 company](https://fortune.com/ranking/fortune500/), we're building a solution to enforce compliance between different services. If service A requests a very sensitive field from service B, we're providing this information to service A, so it can make a decision whether or not the field should be provided to stay compliant. We're able to easily layer this on top of Federation as the concept of Entities gives us the necessary building blocks. All we do is add a simple directive to the field that should be protected. How would you solve this problem with REST APIs?
- Many other customers have asked us to build a proposal workflow for Schema Changes. So we're building a system that lets them define 'Schema Owners'. When someone proposes to add a field to an existing entity, the relevant Schema Owners get notified and involved in a review and approval process. Again, having entities as a fundamental building block of the API is a huge advantage here.

To summarize, I hear a lot of complaints about GraphQL on social media,
I hear the stories of how much enterprises struggle with managing APIs at scale,
and I see a lot of companies who are using GraphQL Federation very successfully.
Those who haven't built a centralized API Layer yet are struggling with the basics,
and the ones who have built such a platform are now solving advanced problems.

What's the issue here?
You don't get much attention on social media if you report that everything runs smoothly.
Social media also gets tired quickly,
and we're in a constant search for the next big topic or controversy,
which currently is LLMs.

As I see it,
GraphQL and Federation are now boring, mature technologies.
They've been battle-tested by many companies for years,
and they are becoming the standard for building API platforms at scale.

## The History and Evolution of GraphQL: From Monoliths to Schema Stitching and Federation

That said, as I mentioned earlier,
GraphQL is not the same as it was 10 years ago.

Ten years is a long time in tech.
If you think back to the years following 2015,
it was a very different landscape.

React was just starting to gain traction,
and TypeScript's momentum was slowly picking up.
I remember people debating whether they should use TypeScript or Flow,
with TypeScript slowly gaining the upper hand,
though it still faced a lot of headwinds.

Over the years, TypeScript has become the de facto standard for JavaScript.
NextJS emerged as the number one framework for building web applications,
which led to a lot of new tools and libraries being created,
like tRPC and the Tanstack suite.

As the webdev stack evolved around TypeScript's powerful new capabilities,
it slowly pushed GraphQL aside.

GraphQL revolutionized the way we build frontend applications,
with Fragments, the Relay Client, and advanced React patterns to efficiently fetch data and update a normalized cache in the frontend.
GraphQL is still extremely strong, you could even say it's stronger than ever,
but for many (simpler) use cases,
a monolithic code base with tRPC and/or Tanstack Query does the job with less complexity.

As such, GraphQL evolved from a technology that was driven by the frontend community to a solution mostly adopted because it solves an organizational problem.
These days, you rarely see GraphQL used in a monolithic code base.
Today, the main reason enterprises adopt GraphQL is they want to distribute their API implementation across multiple teams and services.
If you're familiar with Federation, you know what I'm talking about,
but first let's discuss how we moved from monoliths to Schema Stitching, and then ended up with Federation.

### From GraphQL Monoliths to Schema Stitching

In the early days of GraphQL,
people were primarily building monolithic APIs with the Query Language.
We might have forgotten,
but ten years ago the big trends were mobile apps and single page applications (SPAs).
Bandwidth and data usage were much bigger concerns than they are now,
and GraphQL was a great fit for these use cases.

GraphQL allowed mobile apps to fetch data efficiently,
and it was a great fit for SPAs,
for example with Relay Client, developed and open-sourced by Facebook.

One important detail is that GraphQL and Relay Client were not the only components of Facebook's API Stack.
They also had what they called their `Entity Layer` or `Ent` for short.
The Entity Layer was a key component for distributing and scaling the GraphQL schema implementation.
This Layer handled data loading, batching, and authorization.
It's important to understand this layered system because later on, 
a lot of people would complain that GraphQL doesn't handle authorization,
or that you have to implement your own data loader.
These problems were solved one layer below GraphQL,
but the Ent layer was not open-sourced.

As a side note,
knowing about the Entity Layer also helps to understand why [Facebook implemented GraphQL as a monolith](https://graphql.org/learn/federation/#is-graphql-federation-right-for-you).
The real complexity was not in the Query Language,
but in the Entity Layer.
The GraphQL Layer was a thin layer on top.

The adoption of GraphQL rapidly picked up outside of Facebook,
and because people didn't have their own Entity Layer,
they looked for alternative ways to scale their GraphQL implementation.
This movement led to the creation of Schema Stitching,
a technique where multiple GraphQL Schemas are stitched together to form a single unified graph.

With Schema Stitching,
you could create multiple GraphQL servers,
distribute them across different services or teams,
and then combine them into a single GraphQL Schema.
The idea was to not have a gigantic monolith owned by multiple teams.

As good as Schema Stitching sounded,
it has some significant drawbacks.
Composition checks, like we have with Federation, are nonexistent,
so it’s easy to break the contract.
Another problem is that someone must maintain the stitched schema.
It's not enough to add new functionality to a "Sub Schema",
you also need to add it to the monolith that stitches everything together.
From an execution point of view,
Schema Stitching was an absolute nightmare.
The monolith would delegate requests to different GraphQL Servers,
but there's no Query Planning or similar step in place, making Query execution unpredictable.

Consequently, the hype for Schema Stitching quickly died down,
making room for the next generation of GraphQL: Federation.
Whether inspired by Facebook’s Entity Layer or not,
Apollo had its biggest moment with the [release of the first version of Apollo Federation](https://www.apollographql.com/blog/apollo-federation-f260cf525d21).

Since then, Apollo's drive to innovate in the GraphQL space has slowly faded.
Industry experts argue that Apollo Federation 1.0 was the best,
and since v2 things have just gone downhill.
Working groups these days are mostly driven by the community or other vendors.
Apollo's focus currently is on MCP, which is fair enough.

Coming back to Apollo Federation 1.0.
It was a massive improvement over Schema Stitching,
paving the road for what seems to be the final step in the evolution of GraphQL,
although the `Composite Schema Working Group` might not yet agree with this,
but we'll talk about that in a little bit.

Compared to Schema Stitching,
where `Subgraph Orchestration` was a runtime concern,
Apollo Federation allowed us to declaratively define Subgraphs and their responsibilities.
The key ingredients that made Federation successful were Entities (you guessed it) and composition checks.

What makes Entities special is that they allow us to agree on a single definition of an entity across multiple services
and which `@key` fields should be used to identify the entity.
Combine this with composition checks
and we have all the building blocks needed for multiple teams to contribute their services to a single unified API layer.

For completeness,
here is a quick example of two Subgraphs and how they compose into a Supergraph.

```graphql
# Products Service
type Query {
  products: [Product]
}

type Product @key(fields: "id") {
  id: ID!
  name: String!
}
```

```graphql
# Reviews Service
type Mutation {
  createReview(productId: ID!, review: ReviewInput!): Review
}

input ReviewInput {
  text: String!
}

type Review @key(fields: "id") {
  id: ID!
  product: Product!
  text: String!
}

type Product @key(fields: "id") {
  id: ID!
  reviews: [Review]
}
```

If we run composition, the process of combining the two Schemas into a Supergraph,
we get the following result:

```graphql
# Supergraph
type Query {
  products: [Product]
}

type Mutation {
  createReview(productId: ID!, review: ReviewInput!): Review
}

input ReviewInput {
  text: String!
}

type Product {
  id: ID!
  name: String!
  reviews: [Review]
}

type Review {
  id: ID!
  product: Product!
  text: String!
}
```

In this case, the team behind the Products Service and the team behind the Reviews Service agreed on a single definition of the `Product` entity.
They also agreed on the `@key` field, `Product.id` in this case.
This field will be used by both services to "join" entity fields from both services.

It seems like Federation is a reasonable next step in the evolution of GraphQL.
But for me, it's much more than that.
I believe that Federation, or the Entity Layer in general,
is the foundation for building a unified API across all your data.

## The Entity Layer: A fundamental building block for building distributed systems

The principles behind Federation are rather simple.
We have a single Supergraph that spans our entire domain.
This Supergraph has root fields (Query, Mutation, Subscription) as entry points into the graph.
Root fields are assigned to Subgraphs, which are our backend services.
If two or more Subgraphs are responsible for contributing fields to a non-root object type,
we make that object type an Entity.
An Entity in its simplest form is an object type that has a `@key` directive,
and the key field(s) are used to uniquely identify the entity.
This way, the Router, which is the component to orchestrate all Subgraphs into a Supergraph,
can figure out how to join the data from multiple Subgraphs together.

Here's a very simple example of two Subgraphs and how they compose into a Supergraph.

```graphql
# User Service
type Query {
  user(id: ID!): User
}

type User @key(fields: "id") {
  id: ID!
  name: String!
}
```

```graphql
# Post Service
type Query {
  post(id: ID!): Post
}

type Post @key(fields: "id") {
  id: ID!
  title: String!
}

type User @key(fields: "id") {
  id: ID!
  posts: [Post!]!
}
```

If we compose the two Subgraphs together,
we get the following Supergraph:

```graphql
# Supergraph
type Query {
  user(id: ID!): User
}

type User {
  id: ID!
  name: String!
  posts: [Post!]!
}

type Post {
  id: ID!
  title: String!
}
```

So why call this the Entity Layer and not just stick with Federation?
Federation, and more specifically Apollo Federation,
is closely tied to GraphQL.
Apollo, often referred to as Apollo GraphQL,
is very opinionated about the Query Language.
With Apollo Client & Apollo Server,
it's clear that the company is very much focused on GraphQL,
which is fine,
but it has effects on the overall architecture of Apollo Federation,
which we believe are limiting.
We'll get to that in a bit.

For us, the Entity Layer is a more general concept,
inspired by the Entity (Ent) Framework from Facebook (Meta),
and solutions like Twitter's "Strato".
If you're interested in learning more about where we got this inspiration from,
here's a great [video on Twitter Strato](https://www.youtube.com/watch?v=E1gDNHZr1NA).
I would also like to mention a [post on TAO](https://www.micahlerner.com/2021/10/13/tao-facebooks-distributed-data-store-for-the-social-graph.html),
and the [Entgo](https://entgo.io/) project,
an open source variant of the Entity Layer from Facebook.

In our view, the Entity Layer has 9 key principles:

1. We can model our domain as entities and relationships between them
2. We must not leak implementation details into the API contract
3. The implementation of the root fields and entities can be distributed across multiple services
4. The Entity Layer gives us primitives to enforce the integrity of the graph
5. The unified API layer is API style agnostic, we can "Connect" any API or service to the Entity Layer, and we can build any kind of API on top of it
6. The Entity Layer is responsible for efficiently batching requests
7. Caching and Cache invalidation are handled by the Entity Layer for optimal performance
8. Privacy, Access Control, and Authorization in general are handled by the Entity Layer
9. The Entity Layer supports collaborative Schema Design and Governance to ensure consistency, quality and compliance across the entire organization

Our vision is to bring the Entity Layer to all large enterprises,
help them eliminate API Sprawl,
and give them the primitives needed to efficiently model their domain across heterogeneous backends.
We want them to be able to expose the unified API layer, or subsets of it, to different API consumers with different needs, using the best API style for each use case.

We don't want to be limiting on the backend,
and we don't want to dictate which API style is used to expose the Entity Layer.
Today you could be using REST or GraphQL, and tomorrow you might be looking at MCP, or anything else that comes along.
API Styles are constantly evolving,
but at its very core,
every company has to solve the same problem.
Problems like modeling and distributing the domain across multiple services,
privacy, access control, caching, batching, and so much more.

## Conclusion

GraphQL’s path from monoliths to Federation shows a simple truth: as domains and teams grow, you need a shared layer.
The Entity Layer is introduced as a fundamental building block for unified APIs. 

It brings scattered services together by defining entities, keys, and responsibilities, while its runtime handles batching, caching, and supports collaborative schema design and governance.
That’s why Federation works in practice—and why the Entity Layer is now the foundation for unified APIs.