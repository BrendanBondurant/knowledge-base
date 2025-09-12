---
type: blog
title: Cosmo Connect vs Apollo Federation vs GraphQL Federation
slug: 2025-09-09-cosmo-connect-vs-apollo-federation-vs-graphql-federation
series: WunderGraph Blog
date: 2025-09-09
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - API Architecture
  - Entity Layer
tags:
  - graphql
  - graphql-federation
  - apollo-federation
  - cosmo-connect
  - grpc
  - supergraph
  - schema-governance
entities:
  - Apollo Federation
  - GraphQL Federation
  - Cosmo Connect
  - Cosmo Router
  - Composite Schemas
summary: |
  Compares Cosmo Connect, Apollo Federation, and GraphQL Federation through the lens of an entity layer.
  Explains why a unified API layer matters, how batching and entity lookups differ (_entities vs @lookup vs gRPC),
  and when to choose Connect over GraphQL subgraphs. Frames tradeoffs for architecture, governance, and operations.
faqs:
  - q: What is the difference between Apollo Federation and GraphQL Federation?
    a: Apollo Federation extends GraphQL with entity types, @key directives, and the _entities field for batching. GraphQL Federation, defined by the Composite Schemas specification, keeps GraphQL vanilla and uses explicit directives like @lookup for composition.
  - q: When should I use Cosmo Connect instead of GraphQL subgraphs?
    a: Cosmo Connect is best when you want federation without deploying GraphQL servers. It generates strict gRPC contracts from SDL, lets you implement RPCs, and delegates batching, authentication, and retries to the router.
  - q: Does Cosmo Connect work with existing REST APIs and SDKs?
    a: Yes. Cosmo Connect lets you generate gRPC contracts and implement RPCs that integrate directly with REST endpoints or SDKs. The router manages batching, traffic shaping, rate limiting, and retries.
  - q: How does batching differ between Apollo Federation, GraphQL Federation, and Cosmo Connect?
    a: Apollo Federation batches through the _entities field. GraphQL Federation’s @lookup does not batch automatically, requiring routers to synthesize batching strategies such as aliases or multi-requests. Cosmo Connect includes batch-capable gRPC methods by default.
canonical_url: https://wundergraph.com/blog/cosmo-connect-vs-apollo-federation-vs-graphql-federation
---

---
## TL;DR

[Cosmo Connect](https://cosmo-docs.wundergraph.com/connect/overview), [Apollo Federation](https://www.apollographql.com/docs/graphos/schema-design/federated-schemas/federation), and GraphQL Federation all build a unified API layer but differ in architecture and batching strategy. Apollo Federation uses GraphQL subgraphs and the `_entities` field for entity resolution and batching. GraphQL Federation ([Composite Schemas](https://graphql.org/blog/2024-05-16-composite-schemas-announcement)) keeps GraphQL vanilla, replacing `_entities` with directives like [`@lookup`](https://github.com/ChilliCream/graphql-platform/blob/master/website/src/docs/fusion/v15/lookups.md), which requires routers to handle batching explicitly. Cosmo Connect generates strict gRPC contracts from SDL, so teams can avoid deploying GraphQL subgraph servers. The Cosmo Router handles batching, retries, authentication, and authorization by default. If you want GraphQL federation without running GraphQL servers, Cosmo Connect is the best fit.

## Comparison at a glance

Cosmo Connect is a new way to integrate APIs into your Supergraph.
You define a Subgraph SDL, use the `wgc` CLI to generate a gRPC Service proto definition,
and then implement the RPC methods in your language of choice.
You don't need to know much about GraphQL or Federation.
A basic understanding of what Entities are is helpful,
but other than that, the overall workflow is very beginner-friendly.

Another big advantage of Cosmo Connect is that the proto compiler, together with the runtime (Router), handles much of the complexity of federating APIs for you.
Topics like data loading, batching, authentication, authorization, traffic shaping, rate limiting, retry logic, and much more are all taken care of.
Building this layer from scratch might seem like a fun challenge at first,
but after a few months,
it'll dawn on you that you're at the beginning of a years-long journey.

If we take Cosmo Connect at face value, it makes total sense to do it this way.
Define a schema, generate a proto, implement RPC methods, and you're done.
The question is, why hasn't it always been done this way?
How did we go from GraphQL monoliths to Schema Stitching, and then spend so many years with weird `_entities` fields and `_Any` workarounds?
And finally, what role do LLMs play in all this?

Lots of questions, and we'll answer them all in this post.
Let's step back and look at the history of GraphQL and how it evolved into Apollo Federation and the newer GraphQL Federation specification under the GraphQL Foundation.

Once you see this history, you’ll understand why we designed Cosmo Connect the way we did, and how it compares to Apollo Federation and GraphQL Federation.

But before we dive into the history,
I'd like to define the problem space we operate in,
and what Cosmo Connect, Apollo Federation, and GraphQL Federation all share.

## The Problem: Building a Unified API Layer

Across all the different approaches,
it's clear there's agreement on some core principles:

1. A unified API Layer is needed (I'll explain why in a bit)
2. GraphQL is the ideal foundation (this will be covered in the next section)
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
We could implement similar functionality with a REST API,
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
knowing about the Entity Layer also helps to understand why Facebook implemented GraphQL as a monolith.
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
Apollo had its biggest moment with the release of the first version of Apollo Federation.

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

Next, let's take a look at Apollo Federation, GraphQL Federation, and Cosmo Connect,
and how they compare.

## Apollo Federation from the perspective of the Entity Layer

Similar to the Entity Framework from Meta,
one of the key principles of Apollo Federation is defining Entities and their relationships in a Schema.
Apollo introduced the idea of the Supergraph, Subgraphs, and the `@key` directive, as we saw in the previous section.

That said, Apollo Federation is tightly coupled to GraphQL.
If you want to use Apollo Federation,
all your Subgraphs have to be GraphQL Services that follow the Apollo Federation Subgraph Specification.
A GraphQL Server Framework like Apollo Server or GraphQL Yoga is required to implement Subgraphs.
As such, adopting Apollo Federation means your organization has to adopt GraphQL as the main tech stack.

However, Apollo recently introduced "Connectors",
a new way to bring existing REST APIs into the Supergraph with a declarative approach.

Let's imagine we've got the following Accounts Service:

```graphql
# accounts.graphql
extend schema
  @link(url: "https://specs.apollo.dev/federation/v2.11")

type Account @key(fields: "id") {
  id: ID!
  email: String
  stripeCustomerId: ID! # stored in your DB
}

type Query {
  account(id: ID!): Account
}
```

We could then add a billing service that joins information from Stripe into the Supergraph.

```graphql
# stripe-billing.graphql
extend schema
  @link(url: "https://specs.apollo.dev/federation/v2.11")
  @link(url: "https://specs.apollo.dev/connect/v0.2", import: ["@source", "@connect"])

"""
Define a reusable Stripe source: base URL + auth header.
We’ll inject STRIPE_API_KEY from router config/env (see router.yaml).
"""
@source(
  name: "stripe"
  http: {
    baseURL: "https://api.stripe.com/v1"
    # You can also put headers here, but production setups often override in router.yaml
  }
)

"""
We extend Account that’s owned by the Accounts subgraph.
We require `id` (key) and use `stripeCustomerId` from the parent via $this.
"""
extend type Account @key(fields: "id") {
  id: ID! @external
  stripeCustomerId: ID! @external

  invoices(limit: Int = 5): [Invoice]
    @connect(
      source: "stripe"
      http: { GET: "/customers/{$this.stripeCustomerId}/invoices?limit={$args.limit}" }
      selection: """
      $.data {
        id
        amount_due
        currency
        status
      }
      """
    )
}

type Invoice {
  id: ID!
  amount_due: Int
  currency: String
  status: String
}
```

While this approach can help achieve the goal of adding REST APIs to the Supergraph,
it's in violation of some of the key principles of the Entity Layer.

One violation is we're leaking implementation details from Stripe into the Supergraph.
Ideally, our API contract would stay free of details like mapping fields from Stripe into the Supergraph.
This is a concern that should be solved in the implementation.
By adding all of this to the API contract,
it becomes overly verbose and harder to reason about.
We want the Entity Layer to be as collaborative as possible,
which is negatively impacted by this approach.

Another important principle for us is that the Entity Layer is API style agnostic.
With [Apollo Connectors](https://www.apollographql.com/graphos/apollo-connectors), this is achieved to some extent,
but it's far from being fully API style agnostic.
If we wanted to connect a REST API with very specific mapping logic,
custom authorization, request signing, and so on,
we'd be stuck again with implementing a GraphQL Subgraph with a GraphQL Server Framework.

On the positive side,
if we're ignoring Apollo Connectors for a moment,
Apollo Federation is very strong in terms of collaborative Schema Design.
Explicitly defining Entities with the `@key` directive is an important characteristic of establishing a shared understanding of the domain,
and how Subgraphs are being tied together through the concept of Entities.

Next, let's take a look at GraphQL Federation.

## GraphQL Federation from the perspective of the Entity Layer

GraphQL Federation has emerged out of the Composite Schema Working Group under the umbrella of the GraphQL Foundation.
If we look at the [contributors](https://github.com/graphql/composite-schemas-spec/graphs/contributors) to the specification,
we can see that the spec is primarily driven by [Pascal Senn](https://github.com/PascalSenn),
[Michael Staib](https://github.com/michaelstaib),
and [Glen Ainscow](https://github.com/glen-84),
all from the [ChilliCream](https://chillicream.com/) company.
There are also a few commits from [Benjie Gillam](https://github.com/benjie),
a member of the GraphQL Technical Steering Committee (TSC),
as well as a few minor contributors,
but it's fair to say that the "GraphQL Composite Schemas Spec" is mainly being developed by ChilliCream.

The [GraphQL Composite Schemas Spec](https://graphql.github.io/composite-schemas-spec/draft/) has four design principles:

1. **Composable**: Rather than defining each source schema in isolation and reshaping it to fit the composite schema later, this specification encourages developers to design the source schemas as part of a larger whole from the start. Each source schema defines the types and fields it is responsible for serving within the context of the larger schema, referencing and extending that which is provided by other source schemas. The GraphQL Composite Schemas specification does not describe how to combine arbitrary schemas.
2. **Collaborative**: The GraphQL Composite Schemas specification is explicitly designed around team collaboration. By building on a principled composition model, it ensures that conflicts and inconsistencies are surfaced early and can be resolved before deployment. This allows many teams to contribute to a single schema without the danger of breaking it. The GraphQL Composite Schemas specification facilitates the coordinated effort of combining collaboratively designed source schemas into a single coherent composite schema.
3. **Evolvable**: A composite schema enables offering an integrated, product-centric API interface to clients; source schema boundaries are an implementation detail, a detail that is not exposed to clients. As each underlying GraphQL service evolves, the same functionality may be provided from a different combination of services. This specification helps to ensure that changes to underlying services can be made whilst maintaining support for existing requests from all clients to the composite schema interface.
4. **Explicitness**: To make the composition process easier to understand as well as to avoid ambiguities that can lead to confusing failures as the system grows, the GraphQL Composite Schemas specification prefers to be explicit about intentions and minimize reliance on inference and convention.

My personal observation beyond the four design principles is that contrary to Apollo Federation,
the Composite Schema Specification / GraphQL Federation tries to achieve composability of Entities without hacks like `_entities` and `_service`,
or `_Any` types.
The goal seems to be to make Federation work with vanilla GraphQL,
which to me is very understandable given that the Specification is living under the GraphQL Foundation.

That said, abandoning the `_entities` approach in favour of explicit `@lookup` directives has consequences for both the execution layer as well as for Collaboration and Schema Design.
While the specification argues that the approach favours "Collaboration",
I'd like to point out that I think the `@lookup` approach is actually counter-collaborative.

Let's take a look at the following example:

```graphql
type Query {
  version: Int # NOT a lookup field.
  productById(id: ID!): Product @lookup
  productByName(name: String!): Product @lookup
}

type Product {
  id: ID!
  name: String!
}
```

In this case, we've got three root fields of which only one is a "regular" root field,
the other ones are lookup fields.
I see a couple of problems with this approach.

Although the goal of the spec is to enable collaboration and to be "explicit",
from my perspective it's actually lacking explicitness and clarity.
While the Apollo approach has some drawbacks,
it's very explicit about what type we're declaring as an entity using the `@key` directive.
With the `@lookup` directive the issue is twofold.

First, we're not explicitly declaring that the `Product` type is an entity.
Instead, the user has to infer that the `Product` type is an entity because there's at least one root field with a `@lookup` directive.
Imagine a large schema with hundreds of root fields and an equal number of type definitions.
It's not immediately clear which types are entities and which are not.

Second, the `@lookup` directive doesn't encourage users to re-use the same fields as keys across different Subgraphs.
As we're not explicitly declaring `@key(fields: "id")` on the `Product` type,
another team could easily declare a different field as the key.
This might not just lead to inconsistencies,
but could also lead to reduced runtime performance if the Router has to make multiple fetches to "build" the required entity keys to load fields from another Subgraph.

Aside from my complaints about clarity and explicitness in terms of collaboration and schema design,
there's also a technical challenge to properly implement the `@lookup` directive.

One of the "features" of the `_entities` "hack" by Apollo Federation is that it automatically batches Subgraph requests.
Here's an example of a request an Apollo Federation compatible Router (like Cosmo Router) would send to a Posts Subgraph to fetch posts for three users.

```json
{
  "query": "query Query($representations: [_Any!]!) { _entities(representations: $representations) { ... on User { posts { id title } } } }",
  "variables": {
    "representations": [
      { "__typename": "User", "id": "1" },
      { "__typename": "User", "id": "2" },
      { "__typename": "User", "id": "3" }
    ]
  }
}
```

With a single request,
the Router can fetch all the posts for the three users.
Let's compare this to the `@lookup` approach.

Let's assume our Posts Subgraph schema looks like this:

```graphql
type Query {
  user(id: ID!): User @lookup
}

type User {
  id: ID!
  posts: [Post!]!
}

type Post {
  id: ID!
  title: String!
}
```

The Router would need to send three requests to the Posts Subgraph to fetch the posts for the three users.

```json
{
  "query": "query User($id: ID!) { user(id: $id) { posts { id title } } }",
  "variables": {
    "id": "1"
  }
}
```

We'd have to repeat this for each user.
Consequently, we're losing the benefits of automatic batching.

There are ways to solve this problem, however.
For example, the Router could send an array of GraphQL requests.

```json
[
  {
    "query": "query User($id: ID!) { user(id: $id) { posts { id title } } }",
    "variables": {
      "id": "1"
    }
  },
  {
    "query": "query User($id: ID!) { user(id: $id) { posts { id title } } }",
    "variables": {
      "id": "2"
    }
  },
  {
    "query": "query User($id: ID!) { user(id: $id) { posts { id title } } }",
    "variables": {
      "id": "3"
    }
  }
]
```

This approach solves the problem of having to send multiple requests (N+1 problem) to the Subgraph,
but that's not ideal either.
The Subgraph must implement a handler that accepts an array of requests,
and we're now producing 3x (or Nx) more GraphQL AST at the Router level,
while the Subgraph has to handle 3x (or Nx) more GraphQL AST at the execution layer.

An alternative approach to using arrays for batching is to use a single request with aliases on the root fields, which could look like this:

```graphql
query Users($a: ID!, $b: ID!, $c: ID!) {
  a: user(id: $a) {
    posts {
      id
      title
    }
  }
  b: user(id: $b) {
    posts {
      id
      title
    }
  }
  c: user(id: $c) {
    posts {
      id
      title
    }
  }
}
```

Again, technically this is possible,
but it's also not ideal.
With complex queries, the overall GraphQL AST can get very large for both the Router and the Subgraph.

Last but not least,
let's take a look at Cosmo Connect and how it compares to the other two approaches.

## Cosmo Connect from the perspective of the Entity Layer

As mentioned in the beginning,
Cosmo Connect takes the ideas from Apollo Federation to the next level.
The goal is to keep the good parts,
remove the hacks,
and make it as easy and collaborative as possible.

Let's start with a very simple example, the Users Service.
Similar to Apollo Federation,
we're defining a Subgraph schema and explicitly defining entities with the `@key` directive.

```graphql
# User Service
type User @key(fields: "id") {
  id: ID!
  name: String!
}
```

Next, we'll run the `wgc` command to generate the gRPC service proto definition.
Our proto will look like this:

```protobuf
syntax = "proto3";
package service;

option go_package = "github.com/wundergraph/cosmo/plugin";

// Service definition for UsersService
service UsersService {
  // Lookup User entity by id
  rpc LookupUserById(LookupUserByIdRequest) returns (LookupUserByIdResponse) {}
}

// Key message for User entity lookup
message LookupUserByIdRequestKey {
  // Key field for User entity lookup.
  string id = 1;
}

// Request message for User entity lookup.
message LookupUserByIdRequest {
  /*
   * List of keys to look up User entities.
   * Order matters - each key maps to one entity in LookupUserByIdResponse.
   */
  repeated LookupUserByIdRequestKey keys = 1;
}

// Response message for User entity lookup.
message LookupUserByIdResponse {
  /*
   * List of User entities in the same order as the keys in LookupUserByIdRequest.
   * Always return the same number of entities as keys. Use null for entities that cannot be found.
   * 
   * Example:
   *   LookupUserByIdRequest:
   *     keys:
   *       - id: 1
   *       - id: 2
   *   LookupUserByIdResponse:
   *     result:
   *       - id: 1 # User with id 1 found
   *       - null  # User with id 2 not found
   */
  repeated User result = 1;
}

message User {
  string id = 1;
  string name = 2;
}
```

All we have to do now is implement the lookup RPC method.
If you pay close attention,
you will notice that the `LookupUserByIdRequestKey` field is repeated.
Batching is handled by the code generator and Router automatically, so you don't have to think about N+1 issues or batching at all.
The gRPC contract is so strict and well-defined
that it is ideal for leveraging LLM code generation to implement RPC methods,
e.g. when you want to connect to an existing REST API,
or use an SDK like Stripe, or Hubspot, or whatever.

At the same time,
we've got clarity and explicitness on the schema design and collaboration part.

You'd think that replacing GraphQL at the Subgraph level with gRPC is already a huge win,
but we're not stopping there.
We've been thinking a lot about different use cases and realized that there are two major categories we'd like to support.

The first one is traditional Subgraphs.
They are standalone services that expose an API through the Router.
With Cosmo Connect, you can use the same topology, except that the Subgraph is now a gRPC service.

The second category is what we call "Router Plugins".
We're implementing them exactly like Subgraphs but not running them as dedicated services.
Instead, they're running as a sub-process of the Router,
keeping the deployment and lifecycle management very lightweight.
The purpose of Router Plugins is to "Connect" existing APIs or services into the Entity Layer without having to run a dedicated service.
If the implementation of a Router Plugin is primarily I/O,
there's no need to run a dedicated service.
As long as the Router environment provides enough CPU and Memory for the sub-process,
you can run the Router Plugin as a co-processor to the Router.

Combined under the umbrella of "Cosmo Connect",
both approaches allow you to choose between a lightweight proxy or a dedicated service.
This gives you the flexibility to choose between simplifying operations or scaling out a more complex architecture.

## Conclusion

In my personal opinion,
we should be explicit about Entities and their keys.
Explicitness is `@key` to collaboration and great schema design.

In terms of implementation,
I don't think GraphQL is the right tech stack to implement a Microservice architecture.
While exposing a unified API Layer with a Query Language has many advantages,
using GraphQL for the backend offers mostly downsides and few benefits.

There's no good reason, on the technical side, to implement Entity lookup functions with a Query Language.
Leveraging the simplicity and performance of gRPC seems to be the best approach.

---

{% faq /%}

---