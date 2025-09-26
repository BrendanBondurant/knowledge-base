---
type: blog
title: A GraphQL Federation directive for Subgraph-level compliance: @openfed__requireFetchReasons
slug: 2025-09-16-graphql-federation-directive-subgraph-compliance-requirefetchreasons
series: WunderGraph Blog
date: 2025-09-16
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - API Security
  - Compliance
  - Schema Governance
tags:
  - graphql
  - graphql-federation
  - open-federation
  - schema-governance
  - authorization
  - microservices
entities:
  - GraphQL Federation
  - Open Federation
  - WunderGraph
  - Cosmo Router
  - @requires directive
  - @openfed__requireFetchReasons
summary: |
  The @requires directive in GraphQL Federation can leak sensitive fields between subgraphs, creating compliance risks. The new @openfed__requireFetchReasons directive addresses this by attaching fetch reasons to router requests, allowing subgraphs to enforce compliance rules and maintain audit readiness through declarative schema controls.
faqs:
  - q: What is the problem with the `@requires` directive?
    a: It can leak sensitive information from one subgraph to another, even if compliance controls assume the field is restricted. For example, an attacker could use `@requires` to access the `minimumPrice` field in an auction system.
  - q: What does the `@openfed__requireFetchReasons` directive do?
    a: It attaches fetch reasons to router requests. Subgraphs can parse these reasons and use an allowlist to decide whether a sensitive field, like `minimumPrice`, should be returned.
  - q: How does `by_user` help?
    a: The `by_user` field in fetch reasons distinguishes between user-initiated requests and subgraph-initiated ones. This helps subgraphs tell different fetch reasons apart and apply the right controls.
  - q: Is this a replacement for authorization?
    a: No. Authorization is still required to ensure, for example, that only the auction creator can see the `minimumPrice`. The directive addresses compliance and cross-subgraph access, not per-user access control.
  - q: How does this help with compliance audits?
    a: Instead of manually auditing every service in a microservice architecture, organizations can define dependencies and compliance rules directly in the schema. This makes sensitive data access explicit, declarative, and auditable.
  - q: What is @openfed__requireFetchReasons?
    a: It's a GraphQL Federation directive that adds fetch reasons to router requests, allowing subgraphs to enforce compliance and security rules on sensitive fields.
canonical_url: https://wundergraph.com/blog/graphql-federation-directive-subgraph-compliance-requirefetchreasons
---
## TLDR

Most people don’t see `@requires` as a problem, but it’s a real compliance risk. With `@openfed__requireFetchReasons`, subgraphs know exactly why a field is being fetched and can allow or deny access based on clear rules. Sensitive fields like `minimumPrice` stay under control, audits get easier, and compliance becomes declarative.

## Why the @requires directive is a compliance risk in GraphQL Federation

You've probably never heard of this before,
and you might not even see it as a problem.
But the [`@requires`](https://www.apollographql.com/docs/graphos/schema-design/federated-schemas/reference/directives#requires) directive is a serious security and compliance risk.

Typically, you might be thinking that "attacks" come from the outside.
With security and compliance,
we have to carefully think about the architecture we're building.
In [GraphQL Federation](https://graphql.org/learn/federation/), subgraphs can leak information to other subgraphs through the `@requires` directive.

We're introducing the `@openfed__requireFetchReasons` directive to address this problem.
It lets subgraph owners define an allowlist of subgraphs that can access to a sensitive field.
For organizations that must comply with strict security and data governance regulations,
this directive is a key step toward passing audits.

## How Subgraphs leak information through the `@requires` directive

Let’s look at an example to see how this works.
In our fictional case, we have a company called LeeWay that lets users auction off their old, useless, proprietary software.
We use two subgraphs to implement the auction functionality.
Access to the “minimum price” is sensitive, since an attacker could exploit it to win an auction for almost nothing.

Imagine you're a CTO that bought [Apollo GraphOS](https://www.apollographql.com/graphos) two years ago.
You realize [WunderGraph Cosmo](https://cosmo-docs.wundergraph.com/overview) is not only a better product—more capable and faster than Apollo—but also open source and far less restrictive.
So you decide to dump Apollo and auction your GraphOS license to the highest bidder.

An attacker could extend the auction type with an unsuspicious looking field that `@requires` the `minimumPrice` field.
This way, someone outside auction team could still gain access to it.

From a compliance point of view, everyone thought the `minimumPrice` field was only available to the auction service team.
Security controls were put in place to ensure no staff member outside that team could access it.
The compliance team might not understand how `@requires` works, so they believe everything is safe while the minimumPrice field remains exposed to other subgraphs.

To illustrate the problem, here are the schema definitions for the two subgraphs.

```graphql
# Auction Subgraph

type Query {
  auction(id: ID!): Auction!
}

type Auction @key(fields: "id") {
  id: ID!
  title: String!
  minimumPrice: Int!
}
```

```graphql
# Description Subgraph with exploitable directives.

type Auction @key(fields: "id") {
  id: ID!
  minimumPrice: Int! @external
  description: String! @requires(fields: "minimumPrice")
}
```

If a client queries the `description` field, the Router will fetch `minimumPrice` from the Auction subgraph.
It then passes this value as part of the entity representation to the Description subgraph:

```json
{
  "query": "query($representations: [_Any!]!) { _entities(representations: $representations) { ... on Auction { description } } }",
  "variables": {
    "representations": [
      { "__typename": "Auction", "id": "1", "minimumPrice": 100 }
    ]
  }
}
```

The `minimumPrice` field can be fetched by a client at any time.
This post is not about authorization but about compliance.
Authorization is still needed to make sure only the auction creator can see the `minimumPrice` field.
Here, the focus is on making sure a sensitive field is not exposed to another subgraph without explicit consent.

## The Solution: The `@openfed__requireFetchReasons` directive

To solve the problem, we're introducing the `@openfed__requireFetchReasons` directive.
We'll apply it to the `minimumPrice` field in the Auction Subgraph to see how it works.

```graphql
# Auction Subgraph

type Query {
  auction(id: ID!): Auction!
}

type Auction @key(fields: "id") {
  id: ID!
  title: String!
  minimumPrice: Int! @openfed__requireFetchReasons
}
```

With the directive applied, the Router’s request to the Auction subgraph will include the fetch reasons for the `minimumPrice` field.
These appear in the `extensions` field:

```json
{
  "query": "query($representations: [_Any!]!) { _entities(representations: $representations) { ... on Auction { description } } }",
  "variables": {
    "representations": [
      { "__typename": "Auction", "id": "1", "minimumPrice": 100 }
    ]
  },
  "extensions": {
    "fetch_reasons": [
      {
        "typename": "Auction",
        "field": "minimumPrice",
        "by_subgraphs": ["Description"],
        "is_requires": true
      }
    ]
  }
}
```

The Auction Subgraph can now parse the fetch reasons and use an allowlist to decide whether or not the `minimumPrice` field can be fetched.
To accurately distinguish between the different fetch reasons,
we're also adding a `by_user` field to the fetch reasons.

Let's assume that the Description Subgraph doesn't use the `@requires` directive.
If the user requests the `minimumPrice` field,
the request would look like this:


```json
{
  "query": "query($representations: [_Any!]!) { _entities(representations: $representations) { ... on Auction { description } } }",
  "variables": {
    "representations": [
      { "__typename": "Auction", "id": "1", "minimumPrice": 100 }
    ]
  },
  "extensions": {
    "fetch_reasons": [
      {
        "typename": "Auction",
        "field": "minimumPrice",
        "by_user": true
      }
    ]
  }
}
```

As you can see, the `by_user` field is set to `true`,
which makes it easy to tell this fetch reason apart.
In this case, we would not deny the request,
but we'd still need to check authorization in another step.

## Conclusion

We're very customer focused at WunderGraph and committed to solving advanced compliance and security challenges.
With the `@openfed__requireFetchReasons` directive,
we’re not only addressing a real problem but also raising compliance to a new level.

In a classic microservice architecture, it’s often difficult or even impossible to understand dependencies between services.
This makes it hard to detect security and compliance issues like the one in this post.

With Federation and the `@openfed__requireFetchReasons` directive,
we're turning a compliance nightmare into a declarative problem.
Put the directive on sensitive fields and manage an allowlist of services that can fetch them.

If you're not yet using GraphQL Federation and you're thinking about compliance,
this could be the missing piece to easily pass audits.
Instead of manually auditing every service,
you can now declaratively define dependencies and compliance rules in your schema.

---

{% faq /%}

---