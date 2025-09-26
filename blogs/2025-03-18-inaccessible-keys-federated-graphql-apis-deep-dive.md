---
type: blog
title: "@inaccessible Keys in Federated GraphQL APIs - A Deep Dive"
slug: 2025-03-18-inaccessible-keys-federated-graphql-apis-deep-dive
series: WunderGraph Blog
date: 2025-03-18
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - API Security
  - Schema Design
  - Data Access Control
tags:
  - graphql
  - graphql-federation
  - schema-governance
  - authorization
  - microservices
entities:
  - GraphQL Federation
  - @inaccessible directive
  - @key directive
  - WunderGraph
  - Cosmo Router
  - Supergraph
summary: |
  The @inaccessible directive in GraphQL Federation enables powerful patterns for hiding sensitive data access keys from public APIs while maintaining internal functionality. This deep dive explores Internal Keys and Zero Trust Data Access patterns, showing how to manage sensitive data access, support legacy migrations, and implement strict access controls in federated GraphQL APIs.
faqs:
  - q: What is the purpose of the `@inaccessible` directive in GraphQL Federation?
    a: The `@inaccessible` directive hides fields from the public client schema while keeping them available in the Supergraph schema for internal use. This allows Routers to use those fields for query planning without exposing them to external clients.
  - q: How does `@inaccessible` work with `@key` in a federated schema?
    a: You can mark specific `@key` fields as `@inaccessible` to define internal identifiers that are used only for joining subgraph data. This enables patterns like Internal Keys and Zero Trust Data Access without leaking internal IDs to the client schema.
  - q: When should I use internal keys with `@inaccessible`?
    a: Use internal keys when you need to join data across subgraphs that use different database identifiers or are undergoing migrations. This helps hide implementation details from clients and supports multiple identifiers during transitions between systems.
  - q: How does the Zero Trust pattern use `@inaccessible`?
    a: In a Zero Trust setup, `@inaccessible` keys are used to pass short-lived access tokens between services. Sensitive data is only accessible if the client obtains authorization from a master service, enforcing strict access control even between internal systems.
  - q: Can I use `@inaccessible` for legacy system migrations?
    a: Yes. By adding a new `@inaccessible` key alongside the existing public key, you can support both legacy and new identifiers during a migration. Once all systems transition, the old key can be safely removed.
  - q: Does `@inaccessible` remove fields from the Supergraph schema?
    a: No. Fields marked as `@inaccessible` remain in the Supergraph schema and are used by the Router for query execution. They are simply omitted from the public-facing client schema.
canonical_url: https://wundergraph.com/blog/inaccessible-keys-federated-graphql-apis-deep-dive
---

Using `@inaccessible` keys in your Subgraphs is a very powerful addition to your federated GraphQL Schema design toolbox.
In this post, we'll be looking at two very powerful patterns that you can implement using `@inaccessible` keys.

1. **Internal Keys** - How to hide data access keys from the public
2. **Zero Trust Data Access** - How to manage access to sensitive data in a federated GraphQL API

{% partial file="blog-callout.md" /%}

Let's take a look at how the `@key` and `@inaccessible` directives work in general.
Then, we'll dive into the two patterns, Internal Keys and Zero Trust Data Access, in more detail.

## The basics of the `@key` directive in GraphQL Federation

You can think of the `@key` directive as a way to define a unique identifier for a type in your federated GraphQL schema.
This identifier can be used by the Router to "join" data from different subgraphs together.

Here's a simple example of how we could use the `@key` directive to join `Posts` from a `Blog` subgraph with `Authors` from a `User` subgraph:

```graphql
# Blog subgraph
type Post @key(fields: "id") {
  id: ID!
  title: String!
  author: User!
}

type User @key(fields: "id") {
  id: ID!
  posts: [Post!]!
}
```

```graphql
# User subgraph
type User @key(fields: "id") {
  id: ID!
  name: String!
}

type Query {
  user(id: ID!): User
}
```

Let's create a query to fetch a user and their posts:

```graphql
query {
  user(id: "1") {
    name
    posts {
      title
    }
  }
}
```

When the Router receives this query, it will look at the `@key` directives in the `Post` and `User` types to figure out how to "join" the data from the `Blog` and `User` subgraphs together.
It will first query the `User` subgraph to get the user's name like this:

```graphql
query {
  user(id: "1") {
    name
  }
}
```

After that, it will query the `Blog` subgraph to get the user's posts like this:

```graphql
query {
  _entities(representations: [{ __typename: "User", id: "1" }]) {
    ... on User {
      posts {
        title
      }
    }
  }
}
```

As you've seen in this example, the Router is sending a representation of the `User` type to the `Blog` subgraph to fetch the user's posts.
A representation is a combination of the `__typename` of an entity and the `@key` fields to uniquely identify the entity.
By looking at the `@key` directive in the `User` type, the Router knows how to construct the representation to send to the `Blog` subgraph.

There are also more advanced use cases for the `@key` directive,
like using multiple fields to define a "composite key" or using multiple `@key` directives to define multiple ways to join data together.
But for now, let's focus on the basics as this is enough to understand the patterns we'll be looking at.

## The `@inaccessible` directive in GraphQL Federation

To understand the `@inaccessible` directive we have to first understand how GraphQL Federation Routers work,
and how they expose data from different subgraphs to the public.

A GraphQL Federation Router is a service that sits in front of your subgraphs,
which it exposes as a single unified GraphQL API, typically called a Supergraph.

One important distinction to make is that the Router does not serve one single GraphQL Schema but two.
The Router has one schema which is publicly accessible and, if enabled, clients can introspect this schema to see what data is available.
As such, we're calling this the "client schema" at WunderGraph.
Other companies call it an "API schema".

Aside from the client schema, the Router also has a Supergraph schema.
The Supergraph schema is a superset of the client schema, or in other words,
the client schema is a subset of the Supergraph schema.

The Supergraph schema can contain information that is required for the Router to correctly plan and execute all queries.
That said, it's possible that fields are `@inaccessible` in the Supergraph schema,
which means that they are not included in the client schema.

We can make fields `@inaccessible` e.g. by using contracts that include or exclude fields based on tags.
This is a pattern to create a materialized view of the Supergraph schema for specific audiences,
e.g. when you'd like to expose only a subset of fields to a partnering company.

Aside from contracts, we can also use `@inaccessible` directly on fields to explicitly hide them from the public.
In combination with the `@key` directive, this allows us to implement very powerful patterns like Internal Keys and Zero Trust Data Access.

One important thing to note is that the `@inaccessible` directive is not removing the field from the Supergraph schema.
The Router will still be using the field to plan and execute queries, but it will never expose the field to the public.

Now that we understand the basics of the `@key` and `@inaccessible` directives,
let's dive into the two patterns we'll be looking at in this post.

## Using the `@inaccessible` directive for Internal Keys in Federated GraphQL APIs

One principle of good API design is to hide implementation details from the public.
This is especially important when it comes to data access keys,
which might or might not be the same identifiers that you're exposing to the public.

Let's imagine we're serving user information from a `User` subgraph, which uses PostgreSQL as a database.
We might be using a serial primary key as the identifier for users in our database as this is the simplest way to implement it.

Our GraphQL Schema of the `User` subgraph might look like this:

```graphql
# User Subgraph
type User @key(fields: "id") {
  id: ID!
  name: String!
}

type Query {
  me: User
}
```

Now, let's imagine we're adding a new subgraph to our architecture that serves `Posts`.
We're expecting billions of posts to be created over time, so we're using Cassandra as the main database for the `Post` subgraph.
Cassandra is a distributed database, and it's not as easy to use serial primary keys as it is with PostgreSQL.
As such, we're using UUIDs as the identifier for posts in our Cassandra database, which creates a mismatch between the `User` and `Post` subgraphs.

This is where the `@inaccessible` directive comes into play.
We can use the directive to add a second "internal" key to the `User` type,
which we can use to join data from the `User` and `Post` subgraphs together.

Here's what our GraphQL Schema of the `User` Subgraph might look like with an internal key:

```graphql
# User subgraph
type User @key(fields: "id") @key(fields: "userPostsID") {
  id: ID!
  userPostsID: ID! @inaccessible
  name: String!
}

type Query {
  me: User
}
```

Following this logic, the `Post` type in the `Post` subgraph would look like this:

```graphql
# Post subgraph
type Post @key(fields: "id") {
  id: ID!
  title: String!
}

type User @key(fields: "userPostsID") {
  userPostsID: ID!
  posts: [Post!]!
}
```

The `User` subgraph now has three entry points:
1. `id` - The public key that is exposed to the public
2. `userPostsID` - The internal key that is used to join data from the `User` and `Post` subgraphs together
3. `me` - The query to fetch the currently authenticated user

We're able to "jump" to the `User` subgraph from any other subgraph by either providing the public key `id` or the internal key `userPostsID`.
The `Post` subgraph on the other hand only has one entry point, which uses the internal key `userPostsID`.

With this pattern, we're able to achieve multiple goals:

1. From the outside perspective, the public key `id` is the only identifier that is exposed to the public
2. We're abstracting away the complexity of internally using different identifiers for the same entity
3. We can use different databases for different purposes while still being able to easily join data together

This pattern is very powerful, and you might already see how this can be useful for another very similar scenario:
Migrating old legacy systems!

## Using `@inaccessible` keys to migrate legacy systems in Federated GraphQL APIs

Another way of using the Internal Keys pattern is to migrate legacy systems within your federated GraphQL API.

Let's imagine we're serving user information from a `User` subgraph,
which uses a legacy MySQL database as the main data source.

Our GraphQL Schema of the `User` subgraph might look like this:

```graphql
# legcay User Subgraph
type User @key(fields: "id") {
  id: ID!
  name: String!
}

type Query {
  me: User
}
```

Let's imagine we'd like to migrate the `User` subgraph to a new PostgreSQL database.
This new database will use different identifiers for users, e.g. UUIDs instead of serial primary keys.
The challenge here is that clients and other subgraphs can't immediately switch to using UUIDs as the identifier for users.
We need to be able to support both the old and new identifiers for users over a certain period of time.

This is where the `@inaccessible` directive comes back into play.
We can use the directive to add the new UUID identifier to the `User` type.
Once all of the systems have been migrated to use the new UUID identifier,
we can remove the old identifier from the `User` type.

Here's what the legacy `User` subgraph will look like:

```graphql
# legcay User Subgraph
type User @key(fields: "id") {
  id: ID!
  name: String!
}

type Query {
  me: User @shareable
}
```

We've added the `@shareable` directive to the `me` query to indicate that this field can now be resolved by two different subgraphs.
The new `User` subgraph will look like this:

```graphql
# User subgraph
type User @key(fields: "id") @key(fields: "uuid") {
  id: ID!
  uuid: ID! @inaccessible
  name: String!
}

type Query {
  me: User @shareable
}
```

We can jump to the new `User` subgraph either by using the old identifier `id` or the new identifier `uuid`.
Let's take a look at how a third subgraph, e.g. the `Post` subgraph, could migrate to using the new identifier:

Before the migration, the `Post` subgraph might look like this:

```graphql
# Post Subgraph
type Post @key(fields: "id") {
  id: ID!
  title: String!
}

type User @key(fields: "id") {
  id: ID!
  posts: [Post!]!
}
```

In the "legacy" state, the `Post` subgraph is using the old identifier `id` to extend the `User` type.
After the migration, the `Post` subgraph will look like this:

```graphql
# Post subgraph
type Post @key(fields: "id") {
  id: ID!
  title: String!
}

type User @key(fields: "uuid") {
  uuid: ID!
  posts: [Post!]!
}
```

Once all systems have been migrated to use the new identifier `uuid`, we can remove the old identifier `id` from the `User` type in the `User` subgraph.
Composition checks in systems like WunderGraph Cosmo will ensure that you're no longer using the old identifier `id` in any subgraph.

We've now looked at three scenarios where the Internal Keys pattern can be very useful:
1. Hiding implementation details from the public
2. Differentiating identifiers for the same entity across different databases
3. Migrating legacy systems within your federated GraphQL API

Now, let's take a look at another pattern: Zero Trust Data Access.

## Using the `@inaccessible` directive for Zero Trust Data Access in Federated GraphQL APIs

Another use case we've come across is managing access to sensitive data across different services in a federated GraphQL API.
Let's say we've got a service that gives us access to patients.
This could be part of a health care system where a single person, e.g. a parent, might have access to multiple patients, e.g. their children.

In such a system, we might have one FHIR service that keeps track of information about patients, like their date of birth, while another service keeps track of who has access to which patients.

If a user wants to access the date of birth of a patient, should that service ask the "master service" if the user has access to the patient, or could we handle this in a better way?

Another question we could ask is whether the FHIR service should expose information internally, even if we're not exposing it to the public.
To be more specific, if a service has access to the FHIR service, should it be able to access patient data directly, or can we establish a "zero trust" policy where services can only access patient data if they have been granted access?

To answer the above questions, we should establish a "zero trust" environment, which is a better approach.
It should not be enough to gain access to a service to access patient data.
We should always enforce that a client presents valid credentials to access highly sensitive data.

Now, let's take a look at how we can model this scenario using the `@inaccessible` directive.

Here's what our master service might look like:

```graphql
# Master Service
type Patient @key(fields: "id") {
  id: ID!
  shortLivedAccessToken: String! @inaccessible
}

type Query {
  me: Viewer
}

type Viewer {
  patients: [Patient!]!
}
```

The `Patient` type has a field `shortLivedAccessToken` which is marked as `@inaccessible`.
This field cannot be accessed by the public, but it can be used internally to grant access to patient data.
As the name suggests, the access token could be very short-lived and only be valid for a few seconds.

A client would send their credentials to the master service, e.g. by forwarding a JWT token that has been issued by an identity provider.
This JWT token can be opaque and not contain any claims about patient access.
The master service can validate the JWT and issue short-lived tokens to all patients to which the client has access.

You might be wondering if the FHIR service could not just be used to determine if a client has access to a patient by looking at the JWT token.
However, this would mean that multiple services need to implement the same logic over and over again.
By using this pattern, we can centralize the access control logic in the master service, and then re-use this capability across all services that need to access patient data.

Next, let's take a look at what the FHIR service might look like:

```graphql
# FHIR Service
type Patient @key(fields: "id shortLivedAccessToken") {
  id: ID!
  shortLivedAccessToken: String! @inaccessible
  dateOfBirth: Date
}

scalar Date
```

The `Patient` type has two keys, the publicly accessible `id` and the internal key `shortLivedAccessToken`.
By marking the `shortLivedAccessToken` field as `@inaccessible`, it's removed from the client (public) schema, but it's still available in the Supergraph schema, so the Router can fetch the `shortLivedAccessToken` from the master service and pass it to the FHIR service.

This approach leads to the following benefits:

1. We're not leaking sensitive information to the public through claims in JWTs
2. We're not allowing internal services to access sensitive data without the proper authorization
3. The services are decoupled and don't need to communicate directly with each other
4. Authorization can be managed in a decentralized way
5. By using inaccessible keys for authorization, we can even move the authorization logic to a different service if needed

"Zero Trust" in this context means that neither the FHIR service nor the master service allows access to sensitive data without the proper authorization, not even from internal services, like for example the Router.

To gain access to sensitive data, a client must present valid credentials to the master service, which will then issue a short-lived access token, which is the only way to access specific data from the FHIR service.
As long as you're trusting your identity provider and the certificates used to issue and verify JWTs, there's no trust needed between the FHIR service, the master service, and the Router.

## Conclusion

In this deep dive, we've explored how the humble `@inaccessible` directive transforms from a simple schema-hiding mechanism into a powerful tool for solving real architectural challenges in federated GraphQL APIs.

The Internal Keys pattern gives us the freedom to use different identifiers across services without exposing this complexity to our clients.
Whether you're dealing with heterogeneous databases or migrating legacy systems, this pattern provides a clean abstraction layer that shields API consumers from implementation details.

The Zero Trust Data Access pattern takes security to another level by ensuring that even internal services must prove their authorization to access sensitive data.
This approach is particularly valuable in regulated industries like healthcare, where data privacy isn't just good practice—it's the law.

What makes these patterns especially powerful is their versatility.
You can implement them incrementally, adapting to your organization's specific needs without massive refactoring.
And because the complexity is managed at the schema level, your clients remain blissfully unaware of the sophisticated orchestration happening behind the scenes.

As federated GraphQL continues to evolve, I expect we'll discover even more creative uses for directives like `@inaccessible`.
The patterns we've explored today are just the beginning—they demonstrate how thoughtful schema design can solve not just technical challenges but organizational ones as well.

So next time you're designing a federated GraphQL API, remember that `@inaccessible` isn't just about hiding fields—it's about creating cleaner abstractions, enabling smooth migrations, and building more secure systems.
These small schema annotations might just be the key to unlocking a more maintainable and secure API architecture.

I'm curious to hear about your experiences.
Have you used these patterns in your federated GraphQL APIs?
What other patterns have you discovered?

---

{% faq /%}

---