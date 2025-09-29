---
type: blog
title: "Cosmo Connect vs Apollo Federation vs GraphQL Federation"
slug: 2025-09-25-cosmo-connect-vs-apollo-federation-vs-graphql-federation
series: WunderGraph Blog
date: 2025-09-25
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - API Architecture
  - Entity Layer
  - gRPC Services
  - Schema Governance
tags:
  - graphql-federation
  - apollo-federation
  - composite-schema
  - cosmo-connect
  - supergraph
  - grpc
  - schema-governance
  - microservices
  - data-loading
entities:
  - Apollo Federation
  - GraphQL Federation
  - Cosmo Connect
  - Cosmo Router
  - Composite Schemas
  - gRPC
  - GraphQL
  - ChilliCream
  - Pascal Senn
  - Michael Staib
  - Glen Ainscow
  - Benjie Gillam
  - GraphQL Foundation
  - GraphQL TSC
summary: |
  Head-to-head comparison of Cosmo Connect, Apollo Federation, and GraphQL Federation through the lens of the Entity Layer. Explains how each approach models entities, handles batching (_entities vs @lookup vs gRPC), and what that means for operations. Covers tradeoffs between GraphQL subgraphs, explicit directives, and gRPC services for building unified APIs at enterprise scale.
faqs:
  - question: "What is the difference between Apollo Federation and GraphQL Federation?"
    answer: "Apollo Federation extends GraphQL with entity types, @key directives, and the _entities field for batching. GraphQL Federation, defined by the Composite Schemas specification, keeps GraphQL vanilla and uses explicit directives like @lookup for composition."
  - question: "When should I use Cosmo Connect instead of GraphQL subgraphs?"
    answer: "Cosmo Connect is best when you want federation without deploying GraphQL servers. It generates strict gRPC contracts from SDL, lets you implement RPCs, and delegates batching, authentication, and retries to the router."
  - question: "Does Cosmo Connect work with existing REST APIs and SDKs?"
    answer: "Yes. Cosmo Connect lets you generate gRPC contracts and implement RPCs that integrate directly with REST endpoints or SDKs. The router manages batching, traffic shaping, rate limiting, and retries."
  - question: "How does batching differ between Apollo Federation, GraphQL Federation, and Cosmo Connect?"
    answer: "Apollo Federation batches through the _entities field. GraphQL Federation's @lookup directive does not batch automatically, requiring routers to synthesize batching strategies such as aliases or multi-requests. Cosmo Connect includes batch-capable gRPC methods by default."
canonical_url: https://wundergraph.com/blog/cosmo-connect-vs-apollo-federation-vs-graphql-federation
---
## TL;DR

Apollo Federation, GraphQL Federation, and Cosmo Connect all build a unified API layer but make different tradeoffs. Apollo uses GraphQL subgraphs and `_entities` for entity resolution. GraphQL Federation (Composite Schemas) keeps vanilla GraphQL with explicit directives like `@lookup`, pushing batching strategy to the router.

Cosmo Connect generates strict gRPC contracts from SDL so you avoid running GraphQL subgraph servers; the Cosmo Router handles batching, auth, and retries by default. Cosmo Connect avoids GraphQL subgraph servers and provides stronger operational guarantees at the router.

## Comparison at a Glance

[Cosmo Connect](https://cosmo-docs.wundergraph.com/connect/overview) is a new way to integrate APIs into your Supergraph.
You define a Subgraph SDL, run the wgc CLI to generate a [gRPC](https://grpc.io/) Service proto,
and then implement RPC methods in your language of choice.

You don’t need to be deep into [GraphQL](https://graphql.org/) or [Federation](https://graphql.org/learn/federation/) to get started.
Knowing what entities are is enough—the workflow is beginner-friendly.

A major advantage is that the proto compiler and the Router take care of the heavy lifting.
Data loading, batching, authentication, authorization, traffic shaping, rate limiting, retries—
all handled for you. Building this on your own is a years-long journey.

So why hasn’t it always been done this way?
How did we go from GraphQL monoliths, to [Schema Stitching](https://the-guild.dev/graphql/stitching),
to years of living with `_entities fields` and `_Any` workarounds?
And finally, what role do LLMs play in this evolution?

We’ll answer those questions by looking at Apollo Federation, GraphQL Federation, and Cosmo Connect through the lens of the [Entity Layer](https://wundergraph.com/blog/graphql-federation-history-entity-layer).

## Apollo Federation from the perspective of the Entity Layer

Similar to the Entity Framework from Meta,
one of the key principles of Apollo Federation is defining Entities and their relationships in a Schema.
Apollo introduced the idea of the Supergraph, Subgraphs, and the `@key` directive.

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