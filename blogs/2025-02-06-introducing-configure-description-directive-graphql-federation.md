---
type: blog
title: Introducing the @configureDescription directive for GraphQL Federation
slug: 2025-02-06-introducing-configure-description-directive-graphql-federation
series: WunderGraph Blog
date: 2025-02-06
author: David Stutt
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - Schema Composition
  - API Documentation
  - Schema Governance
tags:
  - graphql
  - graphql-federation
  - schema-governance
  - api-documentation
entities:
  - GraphQL Federation
  - @openfed__configureDescription
  - Schema Composition
  - WunderGraph
  - Open Federation
summary: |
  The @openfed__configureDescription directive provides precise control over which descriptions appear in federated GraphQL schemas. This powerful tool allows schema designers to override descriptions, prevent internal documentation from leaking to consumers, and ensure consistent API documentation across teams and subgraphs.
faqs:
  - q: What problem does @openfed__configureDescription solve?
    a: It gives schema designers precise control over which descriptions appear in the federated GraphQL schema. Without it, descriptions are picked based on heuristics like length or frequency, which can unintentionally propagate internal or misleading documentation to consumers.
  - q: How can I override a description in a federated schema?
    a: Use the @openfed__configureDescription(descriptionOverride: "...") directive on the relevant type or field. This replaces the existing description with a custom one, regardless of what's defined in the subgraph's SDL.
  - q: Can I prevent a description from being included in the federated graph?
    a: Yes. Set propagate: false in the directive to explicitly block a description from being propagated. This is useful when a field's comment is meant for internal teams only and not for API consumers.
  - q: What if I only have an extension type?
    a: You can still define a description by applying @openfed__configureDescription(descriptionOverride: "...") to the extension type. This works around GraphQL spec limitations that normally prevent descriptions on extensions.
  - q: What happens if multiple subgraphs use the directive?
    a: Only one coordinate can have propagate: true. Others may use propagate: false, or be omitted. If multiple subgraphs try to propagate a description simultaneously, a composition error is triggered to enforce clarity and coordination.
  - q: Why is this directive important in practice?
    a: Federated schemas often have overlapping definitions and documentation intent. This directive avoids confusion, ensures client-facing descriptions are intentional, and supports consistent API documentation across teams and subgraphs.
canonical_url: https://wundergraph.com/blog/introducing-configure-description-directive-graphql-federation
---

A few weeks ago, one of our customers came to us with an interesting problem: they wanted explicit and granular control 
over the descriptions that were propagated to their federated graph.
As I'm sure you're aware, most constituents of a GraphQL schema may define a description; and an instance of a
constituent (coordinates) could appear in multiple subgraphs—each with its own bespoke description.
However, only one description can be propagated to the federated graph.

{% partial file="blog-callout.md" /%}

## The current state of federated descriptions

GraphQL Federation is a powerful tool that enables teams to compose a single API from multiple subgraphs.
But despite all Federation's strengths, managing metadata such as field and type descriptions across a federated schema 
can still be... challenging.

If multiple subgraphs define conflicting descriptions for the same coordinates, should the federated graph use the first
description it encounters?
How about the one that's most recently defined?
Or maybe the one that's longest?
When and how should a description be overridden by another team?
And should one team "own" a description?
According to the Federation spec, you can't, like, _own_ a description, man.

The current approach to propagating a description by WunderGraph Cosmo composition is simple: pick the longest 
description; in the event of a tie, pick the first encountered.
Apollo takes a slightly more complicated approach that involves propagating the most frequent description among other 
nuances.
But whatever the implementation, not all descriptions are created equal.
And moreover, descriptions can serve completely different functions.
For instance, a subgraph is typically "owned" by a single team.
This team may want to document important information, comments, or explanations in their descriptions...
Descriptions that may not necessarily be intended to be client-facing.

Moreover, instances of a schema constituent can also serve different purposes, which would mean a single description
across subgraphs may not be helpful. Here's an example:

```graphql
interface Interface {
  name: String!
  age: Int!
}

type Object implements Interface {
  id: ID!
  name: String!
  """
  Object.age is not resolved here; added to satisfy the interface "Interface".
  """
  age: Int! @external
}
```

The description for `Object.age` is useful for the owners of the subgraph... 
But it is not useful nor meaningful for the federated graph. 
And such a description could be unintentionally propagated if it "wins" the description-picking algorithm.

Descriptions are crucial for understanding an API and its capabilities.
Inconsistent, redundant, or misleading descriptions can lead to confusion and errors for API consumers.

This is where the `@openfed__configureDescription` directive comes in.
It aims to solve these problems and more by providing schema designers fine-grained control over how descriptions are
propagated, overridden, or even hidden from the federated graph.

You can
[dive straight into the documentation here](https://cosmo-docs.wundergraph.com/federation/directives/openfed__configuredescription),
but this blog post will attempt to go into a little more detail.

## The @openfed__configureDescription directive

The `@openfed__configureDescription` directive is defined as follows:

```graphql
directive @openfed__configureDescription(
    descriptionOverride: String,
    propagate: Boolean! = true
) on ARGUMENT_DEFINITION | ENUM | ENUM_VALUE | FIELD_DEFINITION |
INPUT_FIELD_DEFINITION | INPUT_OBJECT | INTERFACE | OBJECT | SCALAR | SCHEMA
```

Let's take a look at its four main functions:

1. Propagating a description: Ensuring a specific description appears in the federated graph.
2. Overriding a description: Replacing a defined description with a different one.
3. Preventing the propagation of a description: Preventing a specific description from being included in the federated graph.
4. Propagating a description through an extension type: Allowing extension types to define descriptions.


## 1. Propagating a description
In subgraph A, the description for `User` is really only relevant for development and not consumption:
```graphql
# subgraph A
type Profile {
  age: Int!
  name: String!
}

type Query {
  users: [User!]!
}

"""
New User fields should be added to User.profile rather than top-level.
"""
type User @key(fields: "id") {
  id: ID!
  profile: Profile!
}
```

In subgraph B, the description for `User` is much more suited to be propagated in the federated graph.
This is accomplished by the addition of the `@openfed__configureDescription` directive on the Object level:
```graphql
# subgraph B
"""
The User type represents an existing user account.
"""
type User @key(fields: "id") @openfed__configureDescription {
  email: String!
  id: ID!
}
```

The federated graph propagates the description as instructed by the `@openfed__configureDescription` directive:
```graphql
# federated graph
type Profile {
  age: Int!
  name: String!
}

type Query {
  users: [User!]!
}

"""
The User type represents an existing user account.
"""
type User {
  email: String!
  id: ID!
  profile: Profile!
}
```


## 2. Override a description
In subgraph A, the description is again intended for internal development.
However, `User` is defined only in subgraph A... 
And we'd rather a different and more helpful description be propagated to the federated graph.
This is achieved by adding `@openfed__configureDescription(descriptionOverride: ...)` on the Object level:
```graphql
# subgraph A
type Profile {
  age: Int!
  name: String!
}

type Query {
  users: [User!]!
}

"""
New User fields should be added to User.profile rather than top-level.
"""
type User @openfed__configureDescription(descriptionOverride: "The User type represents an existing user account.") {
  id: ID!
  profile: Profile!
}
```

The federated graph propagates the description as instructed by the `descriptionOverride` argument of the
`@openfed__configureDescription` directive:
```graphql
# federated graph
type Profile {
  age: Int!
  name: String!
}

type Query {
  users: [User!]!
}

"""
The User type represents an existing user account.
"""
type User {
  id: ID!
  profile: Profile!
}
```


## 3. Prevent the propagation of a description
In subgraph A, the description for `User.name` is not intended to be public.
Consequently, the `@openfed__configureDescription` directive is added on the field with the `propagate` argument set to
`false`:
```graphql
# subgraph A
interface Account {
  id: ID!
  name: String!
}

type User implements Account @key(fields: "id") {
  id: ID!
  """
  User.name is unresolvable here; it is added to satisfy the "Account" interface.
  """
  name: String! @external @openfed__configureDescription(propagate: false)
}

type Query {
  users: [User!]!
}
```

In subgraph B, there is no description for `User.name` at all:
```graphql
# subgraph B
type User @key(fields: "id") {
  id: ID!
  name: String!
}
```

As instructed by the `@openfed__configureDescription` directive, the federated graph does not propagate any description 
for `User.name`:
```graphql
# federated graph
interface Account {
  id: ID!
  name: String!
}

type Query {
  users: [User!]!
}

type User implements Account {
  id: ID!
  name: String!
}
```

Without the `@openfed__configureDescription` directive, the composition algorithm would have been forced to propagate 
the only available description—one that has no real merit in the federated graph.


## 4. Propagating a description through an extension type
Occasionally, schema designers have no choice but to use an extension type "orphan" ("orphan" here meaning no base
type _appears_ to be defined in the schema).
This could be due to a number of reasons, _e.g._, framework limitations, multi-file schemas, or even legacy syntax.
But [as outlined in the GraphQL spec](https://spec.graphql.org/October2021/#sec-Descriptions), extension types cannot 
define descriptions.

The `@openfed__configureDescription` directive allows you to navigate such restrictions that are beyond your control.
This is achieved by adding the directive on the Object level with the intended description provided to the 
`descriptionOverride` argument.

In subgraph A, `Query` is an extension type "orphan".
However, the ability to define a description would be convenient to describe important behaviour:
```graphql
# subgraph A
type User {
  id: ID!
  name: String!
}

extend type Query @openfed__configureDescription(
  descriptionOverride: "Query fields prefixed with \"rl_\" are rate-limited."
) {
  rl_user(id: ID): User
  rl_users: [User!]!
}
```

In subgraph B, `Query` is also an extension type "orphan".
```graphql
# subgraph B
type Product {
  sku: String!
  upc: Int!
}

extend type Query {
  products: [Product!]!
}
```

As instructed by the `@openfed__configureDescription` directive, the description provided to the `descriptionOverride`
argument is propagated to the federated graph:
```graphql
# federated graph
type Product {
  sku: String!
  upc: Int!
}

"""
Queries prefixed with "rl_" are rate-limited.
"""
type Query {
  products: [Product!]!
  rl_user(id: ID!): User
  rl_users: [User!]!
}

type User {
  id: ID!
  name: String!
}
```

In examples like the above, defining a description for an Object is made difficult due to whatever constraints
prevent that Object's inclusion as a type definition in the schema.
The `openfed__configureDescription` directive offers flexibility in such situations, enabling you and your team to
propagate specific descriptions to your federated graph without restriction.


## Composition rules

The constraints for `@openfed__configureDescription` are relatively simple:
1. The coordinates that define the directive _must_ define a description _or_ provide a non-empty string to the 
`descriptionOverride` argument.
2. No two coordinates may define the `propagate` argument as `true` (the default value). 
However, any number of coordinates may define the `propagate` argument as `false`.


Failure to comply with any of these constraints will produce a composition error.
This ensures the use of the directive and the propagation of descriptions is explicit and collaborative.

## Why does any of this matter?

Clean, well-maintained documentation is crucial for usability and adoption of a GraphQL API. 
By giving teams full control over descriptions in a federated setup, the `@openfed__configureDescription` directive
ensures consistency, helps prevents internal leaks, and allows flexibility through description overrides where 
necessary.

## Final thoughts

The `@openfed__configureDescription` directive is a powerful addition to GraphQL Federation, making it easier to manage 
descriptions across subgraphs.
If you're working with federated schemas, consider adopting `@openfed__configureDescription` to streamline your API 
documentation and enhance the developer experience.
And when you do, we'd absolutely love to hear your feedback.

Have you faced challenges surrounding descriptions in a federated graph?
What about other problems you and your team face that remain unsolved?
Please discuss in the comments or [reach out to us directly](https://wundergraph.com/contact/sales)!

And lastly, if you enjoy solving interesting problems that come from real users of the product you're building,
[WunderGraph is currently hiring](https://wundergraph.com/jobs)! We look forward to reading your application! 😎

{% faq /%}

---