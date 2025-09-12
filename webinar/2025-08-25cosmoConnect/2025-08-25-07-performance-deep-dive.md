---
title: "Performance Deep Dive: gRPC vs GraphQL Subgraphs, Cost Savings"
start_time: "00:40:13"
end_time: "00:43:21"
tags: [performance, grpc, federation]
---

00:40:13:20 - 00:40:27:04
Dustin
And yeah, I would be interested in what examples and examples. And you would implement
with grpc plugins. Yeah. And I think this is also also the demo. And thanks.
00:40:27:04 - 00:40:52:03
Jens
So thanks. Awesome. Thank you. Thank you Dustin. Great. Great demo. one thing I want to
notice because you were talking about performance, oftentimes we when we when we speak
about performance, we, we like to look at the gateway and the router and which one is faster
and which one is written in go and rust and, everything in rust is always faster and better.
00:40:52:05 - 00:41:20:18
Jens
But one thing we kind of never talk about is the performance of subgraphs. And, quite a while
ago we had, we had a customer, they were using elixir in the backend. And, I have no opinions
about Alex here. Like, a lot of nice people use elixir, but for some reason, the framework wasn't
really extremely performant in parsing GraphQL requests.
00:41:20:18 - 00:41:48:18
Jens
And they had a crazy schema with, with, a lot of, complexity abstract types. So the router would
send huge queries like, I don't know, ten kilobytes of queries, to the, to the subgraphs, which
even let us to actually build like, like a, compression algorithm to compress, duplicate fields, by
moving them into, into fragments.
00:41:48:18 - 00:42:15:22
Jens
We have a blog post about that. Anyways, what I'm trying to say is performance at the router
level is one thing. Performance at the subgraph level is another topic. And if you have, like, not
compiled language, maybe TypeScript or elixir or I don't even know if elixir is compiled, but, let's
say TypeScript, Node.js and the subgraph implementation by itself is not crazy performant.
00:42:15:24 - 00:42:49:06
Jens
If we're replacing at the subgraph level, GraphQL with gRPC, we do less work because parsing,
gRPC binary requests, it is just less work. We don't have to validate so much. We don't have to
parse so much text. It's just simpler and faster and also encoding. So by replacing GraphQL at
the subgraph layer, we we can gain a lot, just by making our subgraphs, faster.
00:42:49:08 - 00:43:21:00
Jens
The router is heavily optimized, like if you use, Apollo router or cosmo router, like, both are
super fast. We invest heavily into making them fast on, on the framework level. Yeah, you could
gain a lot just by using, a different approach. And, oftentimes I would say if, for example, if you
use like Node.js, it's very likely that you have a lot more subgraphs running than routers just
because the, the routers, they are just proxying the requests.