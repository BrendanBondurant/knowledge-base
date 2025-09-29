---
type: blog
title: 'I was wrong about GraphQL'
slug: 2024-12-03-i-was-wrong-about-graphql
series: WunderGraph Blog
date: 2024-12-03
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Evolution
  - API Architecture
  - Federation
  - Developer Experience
tags:
  - graphql
  - federation
  - api-design
  - developer-velocity
  - microservices
entities:
  - GraphQL
  - Apollo Federation
  - WunderGraph
  - tRPC
  - Relay
  - JSON-RPC
  - REST
  - gRPC
  - WebSockets
  - Server-Sent Events
  - Persisted Queries
  - Schema Stitching
  - Composite Schemas
  - Cosmo Router
  - Cosmo Connect
summary: |
  After 6 years building GraphQL tools, Jens revisits past opinions to reflect on how experience has reshaped his views on APIs, federation, and tooling. Covers the evolution from monoliths to Federation, the shift from frontend-driven to enterprise adoption, and why GraphQL's true value lies in enabling organizational collaboration rather than technical performance.
faqs:
  - question: "Why did Jens change his mind about exposing GraphQL over the internet?"
    answer: "Initially against exposing GraphQL directly, he realized JSON-RPC layers added unnecessary complexity. The GraphQL ecosystem's adoption of Persisted Queries solved security concerns while maintaining compatibility with existing tools and libraries."
  - question: "What is Jens' current view on GraphQL's primary value?"
    answer: "GraphQL has evolved from a frontend technology to an enabler for Federation, solving organizational problems at enterprise scale. Companies adopt GraphQL for Federation benefits, not for GraphQL itself."
  - question: "Why does Jens now prefer Federation over monolithic GraphQL?"
    answer: "Monolithic GraphQL APIs are dead because they don't justify their complexity over alternatives like tRPC. Federation solves organizational problems by enabling multiple teams to collaborate on a unified API across services."
canonical_url: https://wundergraph.com/blog/six-year-graphql-recap
---
I've been building GraphQL tools and writing about the technology since 2018.
Over the years, I've shared my thoughts on various aspects of GraphQL.
From best practices to controversial opinions—I've covered a lot of ground.

In this post, I'd like to revisit some of my old opinions and reassess them using the knowledge and experience I have today.
A lot has changed in the GraphQL ecosystem: use cases have evolved,
and it's much clearer now what works and what doesn't.

{% quote author="Jens Neuse" %}
Build on top of an existing ecosystem rather than try to replace it.
{% /quote %}

You'll notice that there's an overarching theme that I believe is universal to technology in general and not just GraphQL.
There's an ideal way to solve a problem, and then there's the practical way that actually gets adopted by the majority.
Sometimes, the two align; but often they don't.

As such, my main takeaway from this exercise is that innovation is not about finding the perfect solution to a problem.
It's about finding a solution that works well enough for a large enough group of people
while also being easy to adopt and maintain.

With that in mind, let's dive into what I've said and thought in the past to see what still holds up today.

## GraphQL is not meant to be exposed over the Internet

In 2020, I wrote:

> In essence, almost nobody should expose GraphQL directly over the internet.
> As GraphQL is primarily used for internal applications, we should put a JSON-RPC layer in front of it.
> This layer can easily be generated from GraphQL operation files as we can generate a JSON Schema for both the variable
> input definitions and the response types.

In the beginning of my GraphQL journey, I was very much against exposing GraphQL APIs directly over the internet.
I was very much in favor of hiding GraphQL behind a JSON-RPC layer to make the API more secure and more performant.
Consequently, I've built a solution to solve this problem and advocated for it in my writing.

I thought this was really smart.
Having a JSON Schema for every operation would allow us to easily generate clients, forms, and documentation.

However, as time went on, I realized that this approach is not as practical as I initially thought.
Most companies had adopted existing GraphQL tools and libraries, which rely on the GraphQL schema.
Adding this additional JSON-RPC layer introduces complexity and unnecessary overhead.

In addition, the security concerns I had about exposing GraphQL directly can also be solved in a way that's more aligned
with the GraphQL ecosystem.
Under the name of "Persisted Queries", "Persisted Operations", or "Trusted Documents", the GraphQL community has widely
adopted a pattern where clients can register GraphQL Documents with a server, allowing them to send a hash of the
document instead of the full query.

Persisted Queries, while being much less capable than JSON-RPC in combination with JSON Schema,
are compatible with the existing GraphQL ecosystem of clients, servers, and tools.

What I've learned from this is that it's much easier to enhance existing tools and patterns than to introduce new ones.
Build on top of an existing ecosystem rather than try to replace it.

## The case against normalized Caching in GraphQL

In 2020, I wrote:

> Normalized caching is a bad idea for GraphQL.
> I argued that it would introduce a second source of truth, and that it would be hard to keep the cache in sync with
> deeply nested relational data.
> I suggested that you should use JSON RPC instead and leverage cache control headers and ETags.

Betting against the existing GraphQL client ecosystem wasn't enough for me.
I also wanted to challenge the idea of sending Queries over HTTP POST requests.
Wouldn't it be much better to use JSON-RPC with HTTP GET requests and leverage cache control headers and ETags?

To be honest, I still think that the GraphQL ecosystem is missing out on a lot of benefits by treating HTTP POST like a
dumb pipe.
But again, a wise friend once told me that I need to pick my battles, and I've come to realize that if people want to
ignore the benefits of HTTP, I don't need to die on that hill.

However, I've also seen more and more GraphQL users adopting APQ (Automatic Persisted Queries) in combination with
Queries over HTTP GET together with cache control headers, cached on the edge, e.g., with Cloudflare Workers.
With that setup, we're staying within the GraphQL ecosystem while also leveraging the benefits of HTTP.

To make this work well, we've introduced a feature in Cosmo Router that automatically calculates the
[most restrictive cache control header](https://cosmo-docs.wundergraph.com/router/proxy-capabilities/adjusting-cache-control#restrictive-cache-control-policy) based on all Subgraph response headers.
This is super important to ensure that we're not caching stale data when we're combining responses from multiple
sources, which naturally leads to different cache control settings.
If one service returns `Cache-Control: max-age=60` and another `Cache-Control: max-age=3600`, we need to make sure that
the cache is invalidated after 60 seconds.
But in reality, it gets much more complex than that with `no-cache`, `private`, etc...

## Why not use GraphQL?

In 2020, I wrote:

> GraphQL is often touted as the future of APIs for its performance, payload efficiency, and developer experience.
> Its true power lies in its ecosystem of tools and community support.
> GraphQL's success parallels Kubernetes where the core language is foundational but gains strength from extensibility
> and tooling.

I don't disagree with this statement, but I've since come to a much stronger view on what GraphQL is and isn't;
where it shines and where it doesn't.

Simply put, you can forget about all the comparisons to REST, gRPC, or whatever.
GraphQL is not about performance; it's not about over-fetching or under-fetching data.

{% quote author="Jens Neuse" %}
I've since come to a much stronger view on what GraphQL is and isn't;
where it shines and where it doesn't.
{% /quote %}

GraphQL has evolved into being the enabler for Federation, which is the ability to implement a Graph(QL) API across
multiple teams and services.
GraphQL Federation is solving an organizational problem—not a technical one.

GraphQL might not be harmful in other contexts... But for me, it's all about Federation.
Federation is becoming the standard for building APIs at enterprise scale, and GraphQL is the underlying technology
that paves the road for those companies.

These days, nobody adopts GraphQL because they want to use GraphQL.
Enterprises adopt GraphQL because they want the benefits of Federation.

## Generated GraphQL APIs: Tight Coupling as a Service

I said the following on generating GraphQL APIs in 2020:

> - works well for small projects and prototyping
> - lacks capabilities to design
> - violates information hiding
> - forces business logic onto API consumers
> - doesn't abstract away storage
> - is hard to evolve because of tight coupling

My opinion on generated GraphQL APIs hasn't changed much,
although I'd say that I'm even more against it now than I was back then.

As I'm focusing more on Federation these days, I have a natural tendency to work with large organizations that have
multiple teams working together on a single unified API.
In this context, schema (design) first approaches are essential to enable teams to collaborate efficiently on decision
making and change management.

API contracts should be driven by the needs of API consumers to help them to get their job done.
In contrast, they should not be dictated by the capabilities and design decisions of the underlying storage system or
database.

## GraphQL Namespacing: Conflict-free merging of any number of APIs

In 2021, I shared the idea of GraphQL Namespacing:

> By prefixing all types and root fields with a namespace, we could merge any number of GraphQL APIs without conflicts.
> This would allow us to build a single GraphQL API from multiple sources.

I had the idea of using GraphQL as an orchestration layer on top of a heterogeneous set of APIs, services, and databases.
They would all be merged into a single GraphQL API, making it easy for a user to query data from multiple sources in a
single request.
If we're combining multiple disparate APIs, it's clear that we needed a way to avoid naming conflicts.
As such, namespacing seemed like a good idea.

As of today, I admit that I mostly retreat from this idea.
If you combine 5 services, and each service has a `User` type, what's the point of a unified graph if the types aren't
merged and are instead kept within a separate namespace?

My current take is that we should establish a layer to map all the different `User` types into a single definition in
the unified graph, leveraging Federation capabilities to join that data across all services.

{% quote author="Jens Neuse" %}
GraphQL Federation is solving an organizational problem—not a technical one.
{% /quote %}

This will result in a much better developer experience with the resulting API while being able to abstract away the
complexity of the underlying services.
We might even be able to change the underlying services—merging them or re-distributing field ownership—all without
altering the API contract.

If we're automatically merging schemas with namespacing, a change in one service will always result in a breaking change
in the unified graph.
With a mapping layer in between, we might be able to absorb such alterations without breaking the contract of the
unified graph.

## API Design Best Practices for long-running Operations: GraphQL vs REST

In 2022, I thought:

> GraphQL is much better suited for long-running operations than REST.
> The reason for this is that GraphQL has better semantics for describing messages of streams.
> REST is better suited for stateless operations.

I still stand by this opinion.
GraphQL is great for describing long-running operations.
You can use Subscriptions to stream data to a client and utilize the `@defer` and `@stream` directives* to turn regular
queries into streams, loading chunks of data as they become available.
All of this is supported by the GraphQL spec: it's type-safe, and clients can easily subscribe to those streams.

That being said, we've learned a lot over the last couple of years about how to implement GraphQL Subscriptions,
especially in distributed systems with multiple services.

One bottleneck we've identified is the use of stateful connections for Subscriptions between clients and backend services.
If we're operating in a Federated environment, meaning that our GraphQL API is composed of multiple services, we'd like
to avoid having stateful connections to the Subgraphs (Microservices).

As it turns out, a simpler approach is to leverage message brokers or streaming platforms, like NATS, Kafka, SQS, or
RabbitMQ, to implement Subscriptions.
This way, we can decouple the client from the backend services and manage the stateful connections in a centralized place.
We call this approach [Event Driven Federated Subscriptions](https://cosmo-docs.wundergraph.com/router/event-driven-federated-subscriptions-edfs) or EDFS for short.

## GraphQL Subscriptions: Why we use SSE/Fetch over Websockets

Another topic I discussed in April 2022 was GraphQL Subscriptions:

> I argued that we should use Server-Sent Events (SSE) and Fetch over Websockets.
> The reason for this is that SSE is a much simpler protocol than Websockets and that it is easier to implement and debug.

I still think that SSE is the easiest and most convenient way to implement GraphQL Subscriptions.
It's a simple protocol that's easy to understand and debug; and it's supported by all modern browsers.

However, many of our existing customers seem to be using Websockets in their Subgraphs as well as in their clients.
My current understanding is that Websockets will still be used over SSE in many cases, which means that GraphQL Gateways
need to support all of these protocols.

Consequently, we've built Cosmo Router to support [Subscription Multiplexing](https://cosmo-docs.wundergraph.com/router/subscriptions) as we call it.
Multiplexing means that clients can connect to the gateway using Websockets, SSE (GraphQL over HTTP spec), or the
Multipart HTTP protocol.
In terms of Subprotocols, the gateway can handle `graphql-ws`, `graphql-transport-ws`, and the `absinthe` legacy
protocol for Websockets.
Internally, the gateway translates all of these protocols into a unified format, which again can be translated into the
Subgraph's native protocols.

As a result, a client can connect to the gateway using Websockets, and the gateway can forward the Subscription to a
Subgraph that only supports SSE or vice versa.

## GraphQL's @defer and @stream Directives are overkill

In February 2023, I served a sizzling side of spice:

> I argued that the `@defer` and `@stream` directives are overkill.
> My point was that we could instead use a Backend For Frontend layer to achieve the same results with less complexity.

This is, once again, a topic where I previously was in favor of a JSON-RPC layer in front of GraphQL.
Aside from the security and performance benefits, I also thought that this layer could implement streaming and deferred
execution in a much simpler way than a GraphQL server could do.

However, this approach comes with a few downsides.
First, you need to implement a custom JavaScript middleware in front of your GraphQL server to handle the streaming and
deferred execution.
This is not ideal, as it means that the frontend developers would have to create and maintain this middleware themselves.
Second, this only really works well if you have full control over how the middleware can fetch data from the backend services.

If you're using a Federated GraphQL API, this middleware would not work as intended as the "client-facing" GraphQL API
of the Federated Graph doesn't have access to the underlying services.
Consequently, the middleware is not able to defer network calls or stream data from the underlying services.

The only solution to handle deferred execution and streaming in a Federated GraphQL API is to use the `@defer` and
`@stream` directives.
This brings us back to the original question of whether these directives are helpful or not.

From discussions with our customers, it's clear that latency of Subgraph responses can vary significantly depending on
the underlying services.
For many use cases, every millisecond counts in the battle to provide the best possible user experience.
Providers of e-commerce platforms, for example, can measure the impact of a 100ms delay in the response time in terms of
lost revenue.
With the help of the `@defer` and `@stream` directives, it's possible to optimize critical rendering paths in a way that
shows the most important data first while the rest of the data is fetched in the background.

## When to use GraphQL vs Federation vs tRPC vs REST vs gRPC vs AsyncAPI vs WebHooks—A 2024 Comparison

In April 2024, I wrote a comparison guide on when to use GraphQL vs other API styles and technologies:

> The gist was that GraphQL is best suited for internal APIs, with Federation being an ideal companion to implement a
> graph across multiple teams.
> REST should be used for public APIs, and tRPC is great when frontend and backend are a single codebase written in
> TypeScript.

As this is an opinion piece, I'd like to share my current thoughts on when to use which technology, which is based on my
personal experience within the WunderGraph team.
However, it's based on discussions with our customers and the broader community.

For me, monolithic GraphQL APIs are dead. No more. Ceased to be. Bereft of li—you get the idea.
They bring not enough advantages over alternatives to justify the complexity they introduce.

{% quote author="Jens Neuse" %}
These days, nobody adopts GraphQL because they want to use GraphQL.
Enterprises adopt GraphQL because they want the benefits of Federation.
{% /quote %}

Internally, we're using tRPC for in a monolithic monorepo setup.
It works great for us and there's no need or benefit to introduce GraphQL.

We're also thinking of exposing a public API for the Cosmo Schema Registry to enable our customers to integrate their own tools with our platform.
For this, we're planning to use REST as it's the most widely adopted standard for public APIs.
To propagate changes or events from the Schema Registry to our customers, we're planning to use WebHooks.

Then there's GraphQL Federation.
Let's be very clear here. Federation is not about GraphQL.
Federation is not solving a technical problem.
Federation is solving an organizational problem.
Federation is about multiple teams collaborating to build, maintain, and evolve a unified API.
This approach has unparalleled benefits in terms of cooperation and change management over any other API style or
technology.
It's currently the best possible way I can imagine to build APIs at enterprise scale.

GraphQL just so happens to be the underlying technology that enables Federation.
These days, companies adopt GraphQL because they want the benefits of Federation—not because they want to use GraphQL.
This is a very important distinction to make.

## Comparisons of GraphQL should mention Relay

In 2023, I tweeted? Xed? the following on X (formerly know as Tw—sorry):

> Every comparison of GraphQL vs whatever that fails to mention Relay is almost always useless.
> Even trpc comparisons completely fail to understand fragments.
> It's very easy to dismiss the complexity of GraphQL when you fail to understand the core value of the Query language.

Similar to the previous point, a lot of people initially adopted GraphQL because of Relay.
Relay, with its powerful features like Fragment support, data masking, pagination, refetching, and more, was the driving
force behind many early adopters of GraphQL.

However, the ecosystem has evolved over the years, and alternatives like tRPC have emerged that make up for a great
developer experience without having to deal with the complexity of GraphQL.
Consequently, monolithic GraphQL APIs are not as popular as they used to be, which means that Relay is less relevant
today than it was in the past.

That being said, if your company has good reasons to adopt GraphQL, e.g., because you're using Federation, Relay is
still one of the best ways to consume the API on the client side.
I also want to mention [Isograph](https://github.com/isographlabs/isograph) here, which is a new project that aims to build on top of the Relay concepts to
further enhance the developer experience.

## Conclusion

In conclusion, I think that GraphQL has shifted over the last couple of years from being a "cool" technology to being
the enabler for solving organizational problems at enterprise scale.

I'm tired of the comparisons to REST, gRPC, or whatever else, which are typically dominated by performance, payload
efficiency, and developer experience.

GraphQL can solve over-fetching, under-fetching, and it can provide a great developer experience with tools like Relay,
but that will not be the main driver for companies to adopt GraphQL.

Companies adopt GraphQL because they want the benefits of Federation; they seek to scale their API development across
multiple teams and services.
Those same companies want to enable collaboration and change management at scale.
GraphQL is the enabler for Federation—and it's doing a great job at that.

*Editor’s Note (2025):
While this post discusses the @defer and @stream directives in the context of GraphQL Federation, please note that these directives are not currently supported in Cosmo.
