---
type: blog
title: The Next Generation of GraphQL Federation Speaks gRPC
slug: 2025-06-27-next-generation-graphql-federation-speaks-grpc
series: WunderGraph Blog
date: 2025-06-27
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - gRPC Integration
  - Type Safety
  - Performance Optimization
tags:
  - graphql
  - graphql-federation
  - grpc
  - apollo-connectors
  - api-orchestration
  - performance
entities:
  - GraphQL Federation
  - gRPC
  - Apollo Federation
  - Subgraph Compiler
  - WunderGraph
  - Cosmo
summary: |
  The next generation of GraphQL Federation uses gRPC instead of GraphQL for Subgraph communication, providing compile-time type safety, automatic batching, and zero N+1 issues. By compiling Subgraph SDLs to type-safe gRPC services, teams can maintain GraphQL for frontends while using efficient gRPC for backend communication.
faqs:
  - q: What problem does the Subgraph to gRPC Compiler solve?
    a: It replaces Apollo's `_entities` resolution mechanism with a strictly typed gRPC interface. This eliminates untyped `_Any` payloads, improves correctness, and prevents runtime errors in Subgraph implementations by making entity fetches compile-time safe.
  - q: How does this approach fix the N+1 problem in Federation?
    a: The compiler generates `LookupById` RPC methods that accept repeated keys, enabling automatic batching at the Router level. This applies the DataLoader pattern by default, eliminating repeated entity fetches across Subgraphs.
  - q: Why use gRPC instead of GraphQL for Subgraph services?
    a: Many backend teams already use gRPC internally. By compiling GraphQL SDL to gRPC, Cosmo lets the Router act as a bridge—frontend teams keep GraphQL, backend teams get type-safe gRPC services, and you eliminate shim layers entirely.
  - q: What does the gRPC to GraphQL adapter in the Router do?
    a: It translates GraphQL queries into gRPC messages using schema-first mapping rules. The adapter handles field types, enum conversion, nullability, and input/output schemas while preserving strict typing via deterministic proto generation.
  - q: How does the proto lock file prevent breaking changes?
    a: The compiler tracks all previous field numbers using a lock file. If a field is removed, its number is marked as `reserved` in the proto definition to prevent reuse, avoiding accidental type mismatches and maintaining schema compatibility.
  - q: Where can I try the Subgraph to gRPC Compiler?
    a: You can follow the gRPC Services Quickstart tutorial or read the gRPC Services documentation to get started building gRPC-backed Subgraphs.
canonical_url: https://wundergraph.com/blog/next-generation-graphql-federation-speaks-grpc
---

Apollo introduced the amazing concept of Entities to GraphQL,
allowing you to split a single monolithic GraphQL Schema into multiple Subgraphs and federate them through a Router.

But as amazing as this idea is,
it always felt a bit like a hack.
We're fixing this with our new Subgraph to gRPC Compiler.

## tl;dr:

We've been building a completely new approach to implementing GraphQL Federation.
We take Subgraph SDLs and compile them to gRPC services with out-of-the-box support for data loading,
so you never run into N+1 problems again.
At the same time, this approach lets you leverage the type safety and tooling benefits of the gRPC ecosystem.
This approach is not just multitudes faster than GraphQL Subgraphs
but also makes implementations strictly typed and easier to reason about.

{% partial file="blog-callout.md" /%}

## The Problem: Subgraph Entity Representation fetches are not type-safe

The way Apollo distributes Entities across Subgraphs looks like this:

One Subgraph defines a root field that returns an Entity,
which is defined by adding a `@key` directive to the type.
Then, another Subgraph defines the same Entity and adds an additional field.
Once we compose the two Subgraphs together,
we get a Schema that incorporates all the fields from both Subgraphs.

The first Subgraph could look like this,
defining a `User` Entity:

```graphql
# User Subgraph

type Query {
  me: User!
}

type User @key(fields: "id") {
  id: ID!
  name: String!
}
```

The second Subgraph could look like this,
defining a `User` Entity with an additional field:

```graphql
# Posts Subgraph

type User @key(fields: "id") {
  id: ID!
  posts: [Post!]!
}

type Post {
  id: ID!
  title: String!
}
```

Now, when we compose the two Subgraphs together,
we get a Schema that combines all the fields from both Subgraphs.

```graphql
# Combined Schema

type Query {
  me: User!
}

type User {
  id: ID!
  name: String!
}

type Post {
  id: ID!
  title: String!
}
```

Now, let's say we make the following Query:

```graphql
query {
  me {
    id
    name
    posts {
      id
      title
    }
  }
}
```

The Router would make the following request to the User Subgraph:

```graphql
query {
  me {
    id
    name
  }
}
```

Let's assume the response from the User Subgraph is looking like this:

```json
{
  "data": {
    "me": {
      "id": "1",
      "name": "Graf Cue El"
    }
  }
}
```

The Router would then follow up with the following fetch to the Posts Subgraph:

```graphql
query Query($representations: [_Any!]!) {
  _entities(representations: $representations) {
    ... on User {
      posts {
        id
        title
      }
    }
  }
}
```

The full request, including the variables, would look like this:

```json
{
  "query": "query Query($representations: [_Any!]!) { _entities(representations: $representations) { ... on User { posts { id title } } } }",
  "variables": {
    "representations": [
      {
        "__typename": "User",
        "id": "1"
      }
    ]
  }
}
```

The main problem with this approach is that the Subgraph must implement an `_entities` field that accepts a list of `_Any` objects.
There's not much you can do at compile time to ensure that the Subgraph is implemented correctly.
Discussions with our customers show that this "hack" is a common source of bugs.
We've been asked more than once to advise customers on solutions to "prove" the correctness of a Subgraph implementation.

So, let's take a look at the new approach.

## The Solution: Replacing Apollo Subgraphs with gRPC Services

We have been in the market of GraphQL Federation for a few years now,
so we've been able to build a lot of relationships with Federation users and learn about their Architecture,
processes, tooling, and workflows.

One very common pattern we've seen is that many organizations build GraphQL Subgraph shim services that sit on top of gRPC services.
They felt like gRPC was the more mature technology to implement internal APIs,
while GraphQL was more like a frontend-facing technology that sits on top of the internal APIs.
For backend engineers, gRPC seems like an approach that is easy for them to reason about and implement.

All of this made us think about removing the "intermediate" layer of GraphQL Subgraph shim services.
If frontend engineers prefer to work with GraphQL,
and backend engineers want to work with gRPC,
why can't the Router take the responsibility of directly fetching data from the gRPC services and translating between GraphQL Queries and gRPC Messages?

So that's what we've been working on.
A Subgraph to gRPC Compiler
and an Adapter in the Router that translates between the two API styles.

## The Subgraph GraphQL SDL to gRPC Compiler

Let's tackle the problem step by step.
First, we needed to build a compiler that takes a GraphQL SDL and compiles it into a gRPC proto document.

Let's take a look at how the User Subgraph would look like:

```graphql
# User Subgraph

type Query {
  me: User!
}

type User @key(fields: "id") {
  id: ID!
  name: String!
}
```

If we run this through the compiler,
the proto document would look like this:

```protobuf
syntax = "proto3";
package service;

option go_package = "github.com/wundergraph/cosmo/plugin";

// Service definition for UsersService
service UsersService {
  // Lookup User entity by id
  rpc LookupUserById(LookupUserByIdRequest) returns (LookupUserByIdResponse) {}
  rpc QueryMe(QueryMeRequest) returns (QueryMeResponse) {}
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

// Request message for my operation.
message QueryMeRequest {
}
// Response message for my operation.
message QueryMeResponse {
  User me = 1;
}

message User {
  string id = 1;
  string name = 2;
}
```

You'll notice two RPC methods, `LookupUserById` and `QueryMe`.
These are the two entry points we need to implement.
The `QueryMe` method is responsible for returning the `me` root field.
The `LookupUserById` method was generated to satisfy the `@key` directive by creating an entry point to extend the `User` type.

One observation you might have is that the `LookupUserByIdRequestKey` field is repeated.
We're not sending a single key,
which would create an N+1 problem.
Instead, we're implementing the data loader pattern at the Router level,
which automatically batches "lookups" for the same entity and Subgraph.

This is not just an improvement in terms of performance
but it also makes the implementation much easier to reason about.
It's best practice to always implement the data loader pattern at the Subgraph level.
With gRPC replacing GraphQL Subgraphs,
data loading is one less problem backend engineers have to worry about.
It just works, allowing the backend engineer to focus on the business logic.

Just for completeness,
here's the proto document for the Posts Subgraph:

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
   * Order matters - each key maps to a single entity in LookupUserByIdResponse.
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
  reserved 2;
  string id = 1;
  repeated Post posts = 3;
}

message Post {
  string id = 1;
  string title = 2;
}
```

## Implementing the gRPC to GraphQL Adapter at the Router level

Mapping between GraphQL and gRPC isn't trivial due to fundamental differences in how both ecosystems model data and APIs.
Both styles are schema-first,
but GraphQL is way more flexible and dynamic,
inheriting the good and bad parts of JSON.
At the same time, gRPC is way more rigid and static.
It's optimized for performance and memory usage, and it comes with data types that aren't available in JSON, such as differentiating between floats, doubles, and integers, while JSON only has numbers.

### Core Mapping Rules between GraphQL and gRPC

Types:

Every GraphQL type becomes a message in Protocol Buffers.
Each field in a GraphQL type gets a corresponding field in the message,
annotated with a unique tag number (like field1 = 1).

Scalars:

Built-in GraphQL scalars are mapped to their Protocol Buffers equivalents:

- String → string
- Int → int32
- Float → double
- Boolean → bool
- ID → string

Custom scalars require explicit definitions or fallback types.

Enums:

GraphQL enums are directly mapped to protobuf enums, with values given numeric identifiers.

Input Types:

GraphQL input objects are mapped in the same way as regular messages,
since both are essentially request payloads.

Queries and Mutations:

These are translated into gRPC service methods,
where the operation name becomes the method name,
and the input/output types are derived from the GraphQL schema.

Example:

```graphql
type Book {
  id: ID!
  title: String!
  pages: Int
}

type Query {
  getBook(id: ID!): Book
}
```

Will roughly become:

```protobuf
message Book {
  string id = 1;
  string title = 2;
  int32 pages = 3;
}

message GetBookRequest {
  string id = 1;
}

message GetBookResponse {
  Book book = 1;
}

service QueryService {
  rpc GetBook(GetBookRequest) returns (GetBookResponse);
}
```

### Challenges of mapping GraphQL to gRPC

One major challenge is the loss of expressiveness.
GraphQL's optionality and unions don't translate directly into Protobuf's more rigid model.
The mapping must enforce stricter typing (e.g., no null vs. nullable fields) and resolve things like default values and repeated fields carefully.
Tag numbering in protobuf also demands discipline and uniqueness,
which is absent in GraphQL.

To handle these, the Cosmo system uses a deterministic field ordering strategy, translates optional/nullable semantics via wrappers,
and ensures that field numbers are stable across schema generations.
It also enforces constraints (e.g., disallowing untagged types) to ensure the mapped proto is valid and future-proof.

### Proto lock file: Keeping track of changes to avoid breaking changes

Another challenge we faced was the significance of field numbers in Protobuf.
In a GraphQL SDL, the order of fields doesn't matter.
You can add new fields to the end of the type definition and later move them to the top,
without affecting the API at all.
In comparison, each field in a Protobuf message has a unique field number.

Imagine the following scenario:

You create a field in a proto file to represent the `id` and `name` of a `User` type.

```protobuf
message User {
  string id = 1;
  string name = 2;
}
```

Now, you decide to remove the `name` field.
Your proto file now looks like this:

```protobuf
message User {
  string id = 1;
}
```

Now, you want to add a new field to the `User` type to represent the `age` of the user.

```protobuf
message User {
  string id = 1;
  int32 age = 2;
}
```

We now have one version of the message where the number 2 is assigned to the `age` field
and a previous version where the number 2 was assigned to the `name` field.
Both fields are not just semantically different;
they are also incompatible types.

To solve this problem,
we've introduced a "proto lock file" that will keep track of previous versions of the proto file.
This way, we can use the `reserved` keyword to block number reuse.

```protobuf
message User {
  reserved 2;
  string id = 1;
  int32 age = 3;
}
```

## Conclusion

As a next step, you can learn more about [gRPC Services](https://cosmo-docs.wundergraph.com/router/gRPC/grpc-services)
in the documentation.

We've also prepared a [quickstart tutorial](https://cosmo-docs.wundergraph.com/tutorial/grpc-service-quickstart)
so you can try out the new approach yourself.

This is our first step towards improving the Federation experience and making it less dependent on GraphQL.
We're very eager to hear your feedback.
Please join our [Discord](https://wundergraph.com/discord)
and let us know what you think.
You can also open an issue on [GitHub](https://github.com/wundergraph/cosmo/issues)
if you have any questions or feedback.

Thanks for reading!


---

{% faq /%}

---