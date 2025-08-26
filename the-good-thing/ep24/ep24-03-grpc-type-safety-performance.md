---
title: gRPC Type Safety and Performance Benefits
slug: ep24-03-grpc-type-safety-performance
series: The Good Thing
episode: 24
chunk: 3
participants:
  - Stefan
  - Jens
segment: gRPC Technical Benefits Deep Dive
timecode: 00:10:10:03 – 00:16:24:29
start_time: 00:10:10:03
end_time: 00:16:24:29
speakers:
  - Stefan
  - Jens
topics:
  - End-to-end type safety with gRPC
  - Performance optimization in subgraphs
  - Eliminating N+1 problems
  - GraphQL parsing overhead removal
  - Apollo ecosystem lock-in concerns
  - Code-first vs schema-first approaches
tags:
  - federation
  - graphql-federation
  - grpc
  - grpc
  - apollo-graphql
  - schema-first
  - ai
  - api-design
  - benchmarking
  - cosmo
  - cosmo-router
  - go
  - graphql
  - startup
  - typescript
topic_tags:
  - grpc
  - type-safety
  - performance
entities:
  - WunderGraph
  - Cosmo Router
  - Apollo
  - TypeScript
  - Go
  - JavaScript
  - Ruby
  - Elixir
  - protobuf
mentions:
  - end-to-end type safety
  - protobuf compilation
  - interface implementation checking
  - code-first frameworks criticism
  - collaborative development workflow
  - batching problem solutions
  - AST parsing overhead
  - 50 millisecond parsing costs
  - Apollo subgraph framework ownership
summary: |
  Jens details the technical benefits of their gRPC approach including guaranteed end-to-end type safety, elimination of N+1 problems through router-level batching, significant performance improvements by removing GraphQL parsing overhead, and reduced dependency on Apollo's ecosystem. He also critiques code-first approaches as less collaborative than schema-first development.
---

00:10:10:03 - 00:10:31:01
Jens
And from our perspective, I think it's, it's the right direction because it achieves multiple things.
So I have a little checklist, which is why I'm looking to the, to the side. So one part is, oh, by the
way, before I go through my checklist, do you have questions?
00:10:31:04 - 00:10:36:23
Stefan
Me? No. One is this released? Can people start using it? Maybe that one.
00:10:36:27 - 00:10:59:08
Jens
It's it's live. Yes. It's live. It's it's in the docs yesterday on LinkedIn, I posted a video about how to
use it, and I gave this to Jacob to post it on YouTube. And, obviously it's not yet on YouTube
because Jacob is super slow, but it will be on YouTube very soon, right? Jacob?
00:10:59:11 - 00:11:06:05
Stefan
continue.
It'll be on YouTube pretty soon. So. Okay, cool. So this is live. People can start using and
00:11:06:08 - 00:11:35:03
Jens
Yeah. So the, the items like why why is this good. So the first part is end to end type safety. So
you have your, you have your, your subgraph SDL, and you compile it to protobuf. And this
protobuf, it will ensure and guarantee type safety. If you use TypeScript for example, we we will
use type checking for all the types.
00:11:35:05 - 00:12:01:26
Jens
With go you can check the interface implementation, everything. So we get much stricter type
safety compared to like there's frameworks that. Yeah, they, they are just not as type safe. And
also, another part, just a side note, just like, one thing we observe a lot in the, in the market is,
and we're actually a little bit confused about it.
00:12:01:28 - 00:12:32:27
Jens
A lot of our customers use code first subgraph frameworks. And, I really don't like this approach
because I think code first is not collaborative. Like, imagine frontend developer comes to you
and says, hey, I have certain requirements. Can you build an API for that? And instead of like
just writing a schema or a scaffolding, a schema for this use case, you now have to write code,
to then generate a schema.
00:12:33:04 - 00:12:57:27
Jens
I personally don't like this workflow, but it's it's another topic code first versus schema first.
Someday we can we can pick it up okay. So that's type safety. The second part is no more N
plus one problem. So what I said earlier with with the batching, normally it's a problem of
GraphQL service in general and with entities.
00:12:57:27 - 00:13:23:22
Jens
It's it's also a big problem. You send entity request to the subgraph and the subgraph has to
handle, to resolve them in batches. So that is something we we have solved because we moved
the sole batching problem to the, to the router. So we always send batched gRPC request to the
to the subgraph. The next part is so that we and by the way this this is not just like an
optimization.
00:13:23:22 - 00:13:46:02
Jens
It's also just less overhead. And we will come to why this is so important at the end. The next
part is performance boost. So one one very big issue with subgraphs and graphql is when you
have a GraphQL server, it needs to parse the text. Then it has an AST, it needs to validate the
AST.
00:13:46:05 - 00:14:10:28
Jens
It needs to execute the AST. This is a very complex operation. And, we can we can solve this
whole problem with, this gRPC approach because we pass the query, validate it, normalize it,
everything once in the router. And then we call your gRPC method methods theres no, no. Yeah.
Like no GraphQL parsing, no validation, nothing.
00:14:10:28 - 00:14:44:04
Jens
It's just calling gRPC method. So it's the overhead on the subgraph is much lower in the world
where you optimize the router, to every degree. I think one one big part that people have
forgotten about is how can we optimize subgraphs. And we had customers they spent
sometimes, like 50 milliseconds in the subgraph for parsing a query because like your elixir
framework or whatever, it's it's not super efficient in parsing a BigQuery with, gRPC, this
problem is gone.
00:14:44:04 - 00:15:15:24
Jens
Okay. Last but not least, the Apollo lock in. So one one big topic in the in the Federation
ecosystem is that even though you could say it's like open and everybody can do whatever they
want, the major subgraph frameworks, they are owned and maintained by Apollo. And, we don't
know what happens to Apollo in the in the future, and how they think about the business model
and everything.
00:15:15:28 - 00:15:41:03
Jens
And currently they have their, their, they kind of own most of the, of the subgraph frameworks.
And, also I would say there's like not that much innovation in making subgraph frameworks
better. Like, in general. And by yeah, by having gRPC between router and subgraph, we can
first of all, we can leverage the gRPC ecosystem.
00:15:41:03 - 00:16:24:29
Jens
And second, if we think there's a useful feature for our customers, we it and it's still vanilla
gRPC. So everybody can now benefit from this feature. So that's that. And then to to just sum it
up or. Yeah. But put like a, like a Tldr why why all of this. So if we have this strong contract and
it's a fast contract, there's a plugin system that allows your cosmo router to run like a gRPC
subgraph as a co-processor.