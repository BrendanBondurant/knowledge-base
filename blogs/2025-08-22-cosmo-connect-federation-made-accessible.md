---
type: blog
title: Cosmo Connect: Federation Made Accessible
slug: 2025-08-22-cosmo-connect-federation-made-accessible
series: WunderGraph Blog
date: 2025-08-22
author: Jesse Thompson
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - API Modernization
  - Microservices Architecture
  - Developer Experience
tags:
  - graphql-federation
  - grpc
  - cosmo-connect
  - microservices
  - api-gateway
  - developer-experience
entities:
  - Cosmo Connect
  - WunderGraph
  - GraphQL Federation
  - gRPC
  - Microservices
  - API Gateway
summary: |
  Cosmo Connect enables backend teams to use gRPC services while frontend teams see a unified GraphQL API, significantly lowering the barrier to federation adoption. This approach eliminates the need for teams to become GraphQL experts while still delivering the benefits of a single API surface and clean contracts across different languages and architectures.
faqs:
  - q: Do backend teams need to implement GraphQL servers when using Cosmo Connect?
    a: No. Backend teams only implement gRPC services. A GraphQL schema contract is still required, but the router maps requests into RPC calls.
  - q: What advantage does gRPC provide over GraphQL for backend services?
    a: gRPC avoids the overhead of JSON and GraphQL parsing, offers strong tooling across many languages, and supports simple request–response semantics.
  - q: How does Cosmo Connect help frontend teams?
    a: Frontend teams still see a unified GraphQL API. The router gathers data from gRPC services behind the scenes and presents one consistent graph.
canonical_url: https://wundergraph.com/blog/cosmo-connect-federation-made-accessible
---


When an organization grows beyond a few teams, one of the first problems it runs into is how to split responsibilities cleanly across services.
**You don’t want your billing engineers poking around in user data**, and you certainly don’t want every change in one service rippling across the whole system.
That’s one of the reasons why microservices exist. ([Ready to dive in? Jump straight to the docs](https://cosmo-docs.wundergraph.com/connect/overview))

But the moment you split your backend into different services, you run into another problem: the frontend is still one experience.
End users don’t want to juggle ten different apps, and frontend teams don’t want to juggle ten different APIs.
**They expect a single pane of glass**.

## The Single Pane of Glass

When I talk about a single pane of glass, I mean one interface that frontend teams can depend on.
Imagine standing in front of a window looking into your system.
With simple API stitching, that glass only shows one room at a time: the accounts room, the billing room, the orders room.
To get the full picture, app developers have to walk around and peek into each room separately.

With GraphQL federation, the glass itself becomes active.
The router can look into all of those rooms, gather what’s needed from each, and align it into a single view.
To the frontend, it looks like one picture.
Behind the scenes, the services stay independent and don’t have to coordinate directly with each other.

**Cosmo Connect takes this one step further**.
From the start, backend teams don’t need to worry about federation or GraphQL correctness.
They just implement simple [gRPC](https://grpc.io) services.
The glass stays GraphQL-shaped for the outside world, while the rooms behind it can speak in gRPC.
For your frontend, it’s still one unified view.
A GraphQL schema contract is still required to connect them into the supergraph, but backend teams only need to implement gRPC services instead of maintaining GraphQL servers.


## API Stitching vs GraphQL Federation

Traditionally, you have **two options**.
The first is what most people call [stitching](https://the-guild.dev/graphql/stitching).
Each backend service gets its own endpoint—users, billing, inventory—and if those need to interoperate, it’s on the services themselves to coordinate.
The second option is federation, which is what Cosmo provides.
Here, the router can fetch data from multiple services, join them using entity keys, and present a unified API without those services even knowing about each other.

**Federation is powerful, but it comes with a catch**: it only exists for GraphQL.
That forces every team to adopt GraphQL, whether it fits or not.
It means learning the quirks of recursion depth, query planning, APQ, and N+1 problems.
It means building or adopting tools like data loaders and persisted queries.
For some engineers, that’s fine. For many, it’s a wall to adoption.

This is where Cosmo Connect comes in.

## From GraphQL to RPC
Cosmo Connect lets you keep the benefits of federation while exposing a simpler model to your backend services.
On the frontend, clients still see a flexible GraphQL API.
But behind the router, those requests get mapped to plain RPC calls like `QueryProjects`, `LookupEmployeeById`, or `MutationUpdateProjectStatus`.

This matters for two reasons.
First, gRPC semantics are simple: **request** and **response**.
Every major language has gRPC tooling, often with code generation and type safety baked in.
Second, teams don’t need to think in GraphQL terms when they don’t want to.
The router handles the mapping.
Developers define the GraphQL schema, let the router generate the protobuf definitions, and then implement the RPC endpoints, while federation stitches them together.

The result is a system where backend teams can work in the languages and patterns they know best, while frontend teams still enjoy a unified graph.


## Router Plugins vs gRPC Services
Cosmo Connect introduces two paths for extending the supergraph: plugins and gRPC services.

[Router Plugins](https://cosmo-docs.wundergraph.com/connect/plugins) run as separate local processes managed by the router, published through the Cosmo registry, and deployed automatically alongside the router.
They’re perfect for lightweight integrations if you can budget a little extra CPU or RAM in the router’s environment.
For example, wrapping Stripe or Slack becomes a single-cycle task: define a schema, write a resolver or two, and publish.
No separate CI/CD pipelines or deployments are required; you just publish through the Cosmo registry.

[gRPC Services](https://cosmo-docs.wundergraph.com/connect/grpc-services), on the other hand, live outside the router.
They’re ideal for teams running at scale or in strict environments.
You control the deployment, scaling, and versioning.
You can put them behind your own load balancers, run them serverless, or manage them in Kubernetes.
The trade-off is more work on your side, but this comes with more control.

Think of it as a spectrum: **plugins optimize for iteration speed**, latency, and simplicity, **services for control and scalability**.


## Why Cosmo Connect Uses gRPC First
We chose gRPC first for a few reasons.
Its binary wire format **avoids the overhead of JSON**, which can make a huge difference at high throughput.
It also avoids GraphQL’s heavy parsing steps—AST normalization, query validation, execution planning—that sit on the hot path of every request.
The router already performs these steps for the GraphQL request, so avoiding doing them again at the subgraph can result in real performance gains with no downsides.

Equally important is **ecosystem coverage**.
GraphQL servers are solid in a few languages, like Go and TypeScript, but support is thin elsewhere.
By contrast, gRPC has strong tooling almost everywhere: Rust, Java, Python, and even more obscure systems languages.
If you want federation without being locked to JavaScript or Go, gRPC is a natural fit.

That’s why entire industries already use it.
Games like Counter-Strike and Dota 2 rely on gRPC for hundreds of messages per second.
Using GraphQL would be absurd. Cosmo Connect opens that same efficiency to federated systems.


## Cosmo Connect for Greenfield and Legacy Services
Despite the name, Connect isn’t just about bridging legacy APIs.
It’s also a strong option for new services.
A gRPC service contract is simple to reason about and **doesn’t require your engineers to become GraphQL experts**.
For small, focused APIs with only a handful of RPC calls to manage identity or groups, it’s ergonomic and fast to implement.

That said, GraphQL still has advantages for some backends, especially when field selection can reduce database load.
For example, on a `Product` type, simple fields like name, price, or image might be cheap to fetch, while something like “customers also bought” could require heavier joins or external lookups. With GraphQL, the frontend can choose only the fields it needs, avoiding unnecessary queries or expensive computations.

If you’re building something complex like a primary data store where that kind of field-level control directly impacts performance, a native GraphQL subgraph may still be worth the overhead.
The extra work of query planning, data loaders, and resolver tuning pays off when it prevents expensive operations from running needlessly.

But for many services, particularly those that just wrap external APIs without any opportunity for smart data loading, Connect eliminates the need for that overhead entirely.
One customer we spoke with found that about half of the endpoints they moved from their monolith to microservices were just thin wrappers over external services.
With Connect, those could have been left as gRPC services instead of rebuilt as GraphQL subgraphs, freeing the team to spend their effort on the backends where GraphQL’s features actually matter.

[**Ready to get started? Read the docs**](https://cosmo-docs.wundergraph.com/connect/overview).

## Lowering the Barrier to Federation
For some teams, the biggest barrier to federation has always been GraphQL itself.
They want the single API surface and the clean contracts, but they don’t want to retrain their whole org around GraphQL semantics.
**Connect lowers that barrier**.

Today, you still need to write a GraphQL schema to define how your gRPC service integrates into the supergraph.
But the service implementation itself doesn’t need GraphQL libraries; it only needs to expose the RPC methods defined in the generated Protobuf service.
That’s often enough to make federation approachable for teams who had ruled it out.

It’s not about replacing GraphQL everywhere.
It’s about letting teams choose the right tool for each service while still delivering a unified graph to the outside world.

## Final Thoughts
**Cosmo Connect makes federation accessible beyond GraphQL**.
It gives developers a choice: use plugins for quick integrations, or services for full control.
Build in any language with mature gRPC tooling.
Wrap existing APIs without rewriting them into GraphQL.
Scale without introducing the complexity of a service mesh.

For developers who already know GraphQL inside and out, Connect may not replace your existing approach.
But for the many teams who want federation without the GraphQL learning curve, or for those who just want to cut their migration workload in half, it’s a strong alternative.

In short, Connect brings the benefits of federation to more teams, more languages, and more use cases. 


## Try It Yourself
[Deploy Your First gRPC Service](https://cosmo-docs.wundergraph.com/tutorial/grpc-service-quickstart).

[Deploy Your First Router Plugin](https://cosmo-docs.wundergraph.com/tutorial/using-grpc-plugins).


---

{% faq /%}

---