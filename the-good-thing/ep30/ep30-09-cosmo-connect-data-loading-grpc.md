---
type: podcast-chunk
title: Cosmo Connect Data Loading with gRPC
slug: ep30-09-cosmo-connect-data-loading-grpc
series: The Good Thing
episode: 30
chunk: 9
segment: Cosmo Connect Architecture
timecode: 00:23:22 – 00:26:26
start_time: 00:23:22
end_time: 00:26:26
speakers:
  - Jens
topics:
  - Cosmo Connect
  - gRPC Code Generation
  - Data Loading Optimization
  - Backend Performance
tags:
  - cosmo
  - grpc
  - federation
  - graphql
  - go
  - performance
entities:
  - Cosmo Connect
  - gRPC
  - Federation
  - Data Loading
  - Go
summary: He explains how Cosmo Connect replaces GraphQL backends with gRPC-generated code for subgraphs, removing the need for manual data loading and improving backend performance.
---

00:23:22 - 00:23:53
Jens
little bit off. But I talked about this in the past anyways. Key directive, I think it's, it's, it's, it's it's very good because if you think about the key directive. So I keep talking, I would say less about Federation and a little bit more about the entity layer, because I think you can see the entity layer as a, as a construct, as a pattern independent of federation.

00:23:53 - 00:24:25
Jens
Federation. It's kind of like tightly coupled to, to GraphQL. And our, our kind of thinking is that, having a graph is, is, is is really key to creating a good microservice architecture. The big question is, do we need to have GraphQL on the front end, and do we need to have GraphQL on the backend? What are the benefits?

00:24:25 - 00:24:52
Jens
And if you look at I mean you can see what we're doing with with cosmo Connect. And we're replacing GraphQL on the backend side. But I see very little benefits, to be honest, in having GraphQL on the, on the backend. It, it simply means you need GraphQL frameworks that understand these very, very weird root fields like underscore, service and underscore entities.

00:24:52 - 00:25:28
Jens
And then you have this any type and all that stuff like these kind of hacks that allow federation to send batched requests to subgraphs like that. I mean, it's all hacks to make it work, but why? Why hacking when you can have a really good solution? We're currently building, I think the, the best possible, solution that can still be compatible, with the existing Federation stack and that's Cosmo connect, which means on the backend side, we take, we take, a GraphQL schema and subgraph schema.

00:25:28 - 00:25:57
Jens
We compile it into a proto, and then we have, we have a proto that understands data loading. So that means the router by default solves the data loading problem. You never need to think about data loading ever again. You just implement resolvers like RPC calls that, say, hey, give me give me ten products, for these IDs, and then you return ten products and then batching and everything.

00:25:57 - 00:26:26
Jens
It's it's handled. So that means you you never need to do a, a data loader again. Which, by the way, one one of the biggest adoption blockers for, for teams to efficiently build good GraphQL servers, GraphQL backends is data loading. It's always something everybody new to the topic. They need to learn it with Cosmo Connect, write a schema compile it, implement the resulting proto.