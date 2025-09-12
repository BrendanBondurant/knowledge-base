---
type: webinar-chunk
title: Cosmo Connect Overview and Design Goals
slug: 2025-08-25-03-cosmo-connect-overview
series: WunderGraph Webinars
date: 2025-08-25
speakers:
  - Jens Neuse
episode: null
chunk: 3
segment: Cosmo Connect Overview
timecode: 00:15:30 – 00:19:23
start_time: 00:15:30
end_time: 00:19:23
topics:
  - Cosmo Connect
  - Federation
  - gRPC
tags:
  - grpc
  - federation
  - cosmo-connect
entities:
  - Cosmo Connect
  - Cosmo Router
summary: |
  Jens introduces Cosmo Connect’s gRPC-first model, explaining how it eliminates redundant parsing, improves batching, and simplifies federation workflows. This section positions Connect as a pragmatic alternative to GraphQL-only subgraphs.
---


00:15:30:07 - 00:15:48:10
Jens
Okay. So that's the problem. Next, we want to enter Cosmo Connect. The solution. So, Dustin
explain us what actually is Cosmo connect.
00:15:48:12 - 00:16:24:01
Dustin
Okay. A very on a very high level, I would say you can describe the Cosmo Connect as
self-contained. Service it that runs gRPC and, connected to our router. And you still design your
API context through graphql but. The communication protocol is different. So the router will
communicate from the router to the plugin, over a gRPC, which eliminates, parsing of, of
operations twice.
00:16:24:03 - 00:17:10:12
Dustin
It eliminates, performance overheads in subgraph frameworks. It also makes, the
communication much more direct. This is how I would describe, Cosmo Connect. It's and
because of the gRPC implementation, is is free of any, any specific implementation, for instance
graphql, you can do whatever you want in that implementation and science in before said a lot
of companies building a thin layer between services to connect it to the super graph, or they are
connecting to an API, in that word here, you don't you just you really can focus on your
implementation and the rest is handled by the router.
00:17:10:14 - 00:17:34:06
Jens
So on a high level, I send the GraphQL request from my client to the router. The router then
translates it into proto messages, sends them to my gRPC services. They send back proto
messages. The router again translates it back, builds my Json response, and gives me a Json
response that looks as if there was a graphical server.
00:17:34:07 - 00:17:42:16
Dustin
Exactly. That's why we call it sometimes gRPC subgraphs. And yeah, and pretty much.
00:17:42:18 - 00:18:04:15
Jens
And you made a great point about performance because, and I was thinking a very long time
about this, like in the router. And I can tell you, like, we put years of work into making the router
fast because the router it does a lot of work. It it passes the query it it validates it, it normalize it,
it actually normalize it.
00:18:04:15 - 00:18:29:22
Jens
Like I don't know how many times 10 or 15 whatever times because there's a lot of steps to do.
Then we do the query planning and and all these steps. And then we we create text, GraphQL,
queries, encode them as bytes, send them to the subgraph, and the subgraph parses it again
and validates it and looks. Is that a real valid GraphQL query?
00:18:29:22 - 00:18:58:00
Jens
Although it could actually trust our router. But yeah. And it does all this work again. But we
already did the work. And, I think one of the biggest pitys about this traditional Federation
architecture is in the router. We have a super efficient data loader that de duplicates, multiple
requests that want the same data. And we, we have like, data loader batching in the router.
00:18:58:02 - 00:19:23:00
Jens
Then we send the batched request to the subgraph. And now the subgraph has to implement a
data loader again to efficiently load multiple entities. And yeah. By by moving this problem into
the router. You don't have to do that again. We send you a batch request. You give us back a
batch response data loader Not your problem anymore.