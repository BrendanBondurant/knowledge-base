---
type: blog
title: The Future of Federation: Replacing GraphQL Subgraphs with gRPC Services
slug: 2025-06-30-future-federation-replacing-graphql-subgraphs-grpc-services
series: WunderGraph Blog
date: 2025-06-30
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - gRPC Integration
  - Performance Optimization
  - Type Safety
tags:
  - graphql
  - graphql-federation
  - grpc
  - microservices
  - performance
entities:
  - GraphQL Federation
  - gRPC
  - Apollo Federation
  - WunderGraph
  - Cosmo Router
summary: |
  WunderGraph is moving Federation beyond GraphQL Subgraphs to enable simpler, faster, type-safe APIs using gRPC under the hood. This approach eliminates Apollo's vendor lock-in, solves the N+1 problem automatically, and provides better performance while maintaining GraphQL for client-facing APIs.
faqs:
  - q: Why replace GraphQL Subgraphs with gRPC services?
    a: GraphQL Subgraphs are not type-safe, require manual data loading, and depend heavily on Apollo's specification and tooling. Replacing them with gRPC simplifies the architecture, improves performance, and allows compile-time safety while retaining GraphQL on the client.
  - q: How does using gRPC solve the N+1 problem?
    a: Cosmo Router handles batching and data loading internally. With gRPC, Subgraphs receive batched `LookupById` requests by default, eliminating the need for developers to manually implement the DataLoader pattern.
  - q: What are the performance benefits of gRPC over GraphQL in Subgraphs?
    a: gRPC is faster because it avoids parsing, validation, and planning logic at the Subgraph level. It's a compact binary protocol with predictable performance, unlike GraphQL which adds significant runtime overhead, especially when Subgraphs are written in slower languages.
  - q: Does this approach lock me into Go or a specific language?
    a: No. Any language that supports gRPC can be used to implement a federated service. The protocol between the Cosmo Router and Subgraphs is gRPC, not GraphQL, so developers have more flexibility in tooling and language choice.
  - q: How does this avoid Apollo's vendor lock-in?
    a: By removing GraphQL from Subgraphs, you no longer depend on Apollo's Subgraph Specification or Frameworks. New features in Cosmo can be adopted instantly by updating the Router, there is no need to wait for Apollo or third-party maintainers.
  - q: Will GraphQL still be supported?
    a: Yes. Cosmo will continue to support GraphQL for the client-facing API. The switch to gRPC happens behind the scenes at the service layer, improving backend performance without changing how frontend teams use GraphQL.
canonical_url: https://wundergraph.com/blog/future-federation-replacing-graphql-subgraphs-grpc-services
---

Federation is a very powerful concept.
It lets you split a unified API into multiple subsystems.
The longer we've worked with it,
one question kept coming up:

***Is splitting the GraphQL schema at the Subgraph level and having the Router talk to Subgraphs via GraphQL the right approach?***

What if we removed GraphQL from the Subgraphs,
simplified the protocol between the [Router](https://cosmo-docs.wundergraph.com/router/intro) and backend services,
and replaced the transport layer with [gRPC](https://grpc.io/)?

There are efforts from the community to formalize a GraphQL Federation spec.
However, it's becoming clear to us that GraphQL *itself* is the limiting factor in improving the developer experience.

That said, this is not an easy topic to unpack.
Let's step back a bit and start by explaining the problems with GraphQL Subgraphs.


## How GraphQL Subgraphs Limit Federation and Developer Experience

We can break down the problems into four main categories:

1. Technical differences between GraphQL and gRPC
2. Performance of GraphQL vs gRPC as a transport layer
3. Apollo gatekeeping the Subgraph Specification & Subgraph Frameworks
4. Adoption of new features across Subgraph Frameworks

Let's go through each of these categories in more detail.

### GraphQL Subgraphs are not type safe

Here's a simple example of a Subgraph SDL:

```graphql
type User @key(fields: "id") {
  id: ID!
  name: String!
}
```

If the Router needs to fetch the `name` for three users, it sends the following JSON to the Subgraph:

```json
{
  "query": "query User($representations: [_Any!]!) { _entities(representations: $representations) { ... on User { name } } }",
  "variables": {
    "representations": [
      { "__typename": "User", "id": "1" },
      { "__typename": "User", "id": "2" },
      { "__typename": "User", "id": "3" }
    ]
  }
}
```

The Subgraph has to implement a handler that accepts a list of `_Any` objects.
If the `__typename` fields match the `User` type,
the Subgraph framework will call the `User` resolver with the `id` field.

This might sound simple and straightforward, but it can very easily cause problems.
Subgraph frameworks will oftentimes only inform you through runtime errors that there's a mismatch between the Subgraph SDL and the implementation.

While GraphQL embraces type safety between the client and the server,
many Federation Frameworks don't enforce type safety strictly enough.
By using gRPC, we can eliminate a whole class of errors at code generation or compile time.

### GraphQL Subgraphs Require Manual Data Loader Implementation

Another problem we're seeing is that Subgraph frameworks don't solve data loading problems for you out of the box.
They make data loading the responsibility of the implementer,
leaving them to solve N+1 issues.

This is a huge problem because it doesn't just require awareness,
it also means that every Subgraph implementer has to build a solution for it.
Wouldn't it be great if the architecture solved the problem for everyone?

This is where our new approach comes in.
Cosmo Router already solves data loading and batching.
The Query Planner and Execution Engine are designed to solve the [N+1 problem](https://www.youtube.com/watch?v=vWQYI5fNytM&t=1s).
By moving GraphQL to the Router level,
we can reuse the existing data loading and batching logic,
meaning that gRPC services, by design,
don't have to worry about data loading or batching.
Requests to gRPC services come in batches out of the box.

### GraphQL vs gRPC: Performance as a Transport Layer

Another topic I'd like to address is the difference in performance between GraphQL and gRPC as the protocol between the Router and the Subgraphs.

In the Router, we've implemented a highly optimized GraphQL parser, normalization, and validation pipeline.
Once the pipeline is done,
if it is possible, we cache the results to avoid running the same query through the pipeline multiple times.
After normalization, we generate a query plan, which is a very CPU intensive operation.
As such, we also implement a query plan cache to reduce latency and CPU usage.

All in all, the Router is probably one of the most optimized GraphQL execution engines out there.

That said, there's a huge problem with the Apollo Subgraph approach.
We can optimize the Router as much as we want, but
if we're sending a GraphQL request to an unoptimized Subgraph,
or a Subgraph implemented in a less performant language,
our performance will always be limited by the Subgraph language and Framework implementation.

By using gRPC and removing GraphQL from the Subgraphs,
we solve multiple problems at once.
We no longer have to parse, normalize, validate, plan and execute GraphQL at the Subgraph level.
It's just a simple gRPC request.
Second, we can much more reliably predict the performance of gRPC services because we're no longer relying on Subgraph Frameworks to implement GraphQL efficiently.

### Apollo Vendor Lock-in and GraphQL Federation

Another problem for the wider community is that Apollo is gatekeeping the Subgraph Specification and some Subgraph Frameworks.
You can only ever innovate at the pace of Apollo,
and to be frank,
their primary goal seems to be adding GraphOS Enterprise features to their Router,
locked behind a paywall.

Our philosophy is to make Cosmo Router the most open and flexible Federation Router on the market.
Cosmo Router is open source,
and we're collaborating with FAANG companies on the implementation
to make it more modular and extensible.
Our business model is to help teams build and evolve great APIs through collaboration.

By removing GraphQL from the Subgraphs,
we're not just removing the dependency on Apollo's Subgraph Specification and Subgraph Frameworks,
we're also opening the door for faster innovation.
We can roll out new features to Cosmo Router and every language that supports gRPC will be able to use them immediately.

### Why Subgraph Frameworks Lag Behind Apollo’s Federation Spec

This is an extension of the previous point.
When a new feature is added to the Subgraph Specification,
there will always be a delay until every Subgraph Framework implements it.

If you look at the [Reference for compatible GraphQL server libraries](https://www.apollographql.com/docs/graphos/schema-design/federated-schemas/reference/compatible-subgraphs),
you'll notice two things:

1. There are gaps in features supported by the different Subgraph Frameworks
2. *A lot* of frameworks depend on Apollo

Like I said previously,
there's a huge risk if you're depending on Frameworks maintained by a single company that forces you into Enterprise contracts.
Just recently it was announced that they had to lay off 25% of their staff.
If they further stumble with their business model,
this could negatively affect the long-term support of all these Frameworks.

Wouldn't it be much better if we could reduce the number of Subgraph Frameworks that need maintenance to zero?
With our approach of replacing GraphQL with gRPC,
our engineering team can focus on a single component,
Cosmo Router, and every language that supports gRPC will always be able to use the latest features with no maintenance overhead.

### The Challenge of Evolving GraphQL Subgraph Frameworks

Adding features to Subgraph Frameworks is a lot of work.
You have to extend the Specification,
which is gatekept by Apollo,
and then every Subgraph Framework must catch up and implement the new features.

This means that it's a community wide effort to improve the developer experience of Federation and roll out new features.
Most Federation users are often stuck with the same features for years, with no meaningful way to contribute.

When the gatekeeper of the Subgraph Specification is focused on adding Enterprise features to support their business model, you're probably stuck forever.

With the Cosmo gRPC approach,
adding a new feature to Federation is as simple as updating the Router,
and it's automatically available to everyone.
Just update the Router and the GraphQL SDL-to-proto compiler, and you're good to go.

## The Future of GraphQL Federation Runs on gRPC

Now that we've extensively covered the problems we're trying to solve,
let's enter a new era of GraphQL Federation.
It's simpler, easier to use, strictly typed, and *much* more performant.
But at the same time, it's still GraphQL on the client side and the workflow is very similar,
so you don't have to learn a whole new way of building APIs.

Here's a quick overview of the new approach:

Like with Apollo Federation,
you start with a Subgraph SDL.
Here's a quick example:

```graphql
type User @key(fields: "id") {
  id: ID!
  name: String!
}
```

Now, you can use the GraphQL SDL-to-proto compiler to generate a gRPC service.
The result looks like this:

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
  reserved 2 to 3;
  string id = 1;
  string name = 4;
}
```

Note how `LookupUserByIdRequestKey` is prefixed with the `repeated` keyword.
We're not just sending a single key to the `resolver`; we're automatically creating a batch.

Now, all you have to do is implement the gRPC service in your language of choice and tell Cosmo Router where to find it.
Here's an example configuration:

```yaml
version: 1
subgraphs:
  - name: users
    routing_url: localhost:4011
    grpc:
      schema_file: ./schema.graphql
      proto_file: ./generated/service.proto
      mapping_file: ./generated/mapping.json
```

That's it.
You can now start the Router and begin querying your GraphQL API.

{% partial file="blog-callout.md" /%}

## Conclusion

If you're one of our users,
you might be wondering if we're going to remove GraphQL support at some point.
We're **absolutely not**, GraphQL will be used by many teams for a long time.
Under the hood of the Router, gRPC is really just an extension of our existing GraphQL execution engine.

That being said,
we absolutely recommend trying out the new approach to see how it works for you.
In the long run,
we expect gRPC to become the standard for implementing federated APIs.

In summary, we're beyond excited to go this route because we believe it will not only improve the developer experience and Federation performance.
Federation over gRPC breaks us free from Apollo’s gatekeeping and opens the door to much faster innovation.

If you're curious about how we built the Subgraph to gRPC Compiler and the GraphQL-to-gRPC mapping layer, we cover it in [The Next Generation of GraphQL Federation Speaks gRPC](https://wundergraph.com/blog/graphql-federation-over-grpc)

If you're as excited as we are,
take a look at the [Cosmo gRPC Service Quickstart](https://cosmo-docs.wundergraph.com/tutorial/grpc-service-quickstart)
and start building your next generation of federated APIs.

We'd love to hear your feedback on this approach.
You can join our [Discord](https://wundergraph.com/discord)
or create an issue on [GitHub](https://github.com/wundergraph/cosmo/issues).

We're looking forward to seeing you on the other side!

---

{% faq /%}

---