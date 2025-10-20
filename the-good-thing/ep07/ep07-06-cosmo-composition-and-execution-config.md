---
type: podcast-chunk
title: Cosmo's Composition and Execution Config Architecture
slug: ep07-06-cosmo-composition-and-execution-config
series: The Good Thing
episode: 7
chunk: 6
segment: Cosmo vs Apollo architecture comparison
timecode: 00:27:03 – 00:32:20
start_time: 00:27:03
end_time: 00:32:20
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - Cosmo vs Apollo
  - Execution Config
  - Metadata Architecture
  - Resolvability Checks
tags:
  - composition
  - ai
  - apollo-graphql
  - cosmo
  - cosmo-router
  - federation
  - go
  - graphql
  - graphql-federation
  - query-planning
  - supergraph
entities:
  - Cosmo
  - Apollo
  - WunderGraph
  - GraphQL
  - David
  - Sergiy
  - Jens Neuse
summary: David and Sergiy explain Cosmo's architecture differences from Apollo, particularly
  how composition generates metadata in protobuf/JSON format for the router execution
  config. This approach offloads complex validation from query planning to composition
  time, making planning faster and simpler while ensuring query resolvability.
---

00:27:03:08 - 00:27:26:19
David
And so then, I'm not fully aware of the internals, but then the, the, the roots are all the gateway
all the Apollo gateway all then consume that schema and read those encodings from the
directives, and then do that to plan the queries. And whatever and how, WunderGraph does it is
that essentially composition does its thing.
00:27:26:25 - 00:27:50:18
David
And while it is doing its thing, it builds up, a bunch of metadata. And that metadata is then,
translated transposed into some, JSON. Well, first of all It's transposed into, into protobuf and
then into a JSON that, is read by the read by the, consumed by the router to then help with
planning.
00:27:50:21 - 00:28:28:25
David
It's doing very similar stuff to what the Apollo directive encodings are doing, and not exactly the
same, but basically you're trying to provide as much as as much information is necessary to
actually plan the query, from the relevant places in, in that JSON. Just like you're trying to do the
same in, in Apollo with the, the super graph, with the encodings in the directives, so that
essentially you can have a query that or an operation that plans and then, ultimately is executed
and that, JSON is what we call the router execution config.
00:28:28:27 - 00:28:50:14
David
Because we actually have a router config which is actual configuration for the router. But then
there's this other configuration, which is the kind of the read only configuration, that the router
needs to be able to plan. And it was getting a little bit messy with those two terms
interchangeably referred to as the router config. So we have the router execution config the
JSON.
00:28:50:16 - 00:29:09:07
David
And then we have the router config which is the user defined variables and such that they can,
change how the behavior of the router, whereas the read only one is created by composition,
read by the router, and then used during, operation planning. If sergiy wants to add if.
00:29:09:09 - 00:29:47:17
Jens
If I remember correctly, when we started out, our composition was very much the same like
Apollo. So you have subgraphs, you mesh them together. Super graph, super graph in in
GraphQL SDL. And if this is incorrect, just correct me. But so this was when we started out. And
then over time I remember that, you started working more and more closely together, building
ties between composition and query planning, and you started moving some logic into query
planning, into composition.
00:29:47:20 - 00:30:06:14
Jens
And you provide this in this structured way that David just explained to in the config to the, to
the, to the query planner. Can you explain a bit like you could just do it during query planning or
like what? Why are you doing it this way?
00:30:06:17 - 00:30:34:02
Sergiy
But basically we always for building federated graph SDL, a compose schema for a full big
GraphQL schema for subgraphs. This step is still still there. We just, don't have any additional
metadata there, but we always need schema because, like your queries will be distributed
against schema. And actually there was a two versions of this schema because it could be
slightly different.
00:30:37:16 - 00:31:29:19
Sergiy
In our approach, we, we decided that it will be a bit more simpler to offload some job into the
composition just because, composition doing a lot more checks than the planning needs to do.
And, planning is very much simpler. Like, during composition, you have, a full graph of all
possible fields, all possible types, queries, whatever or whatever to be able to display error
messages to understand, like what is possible jumps between subgraphs, what is the relations
between them when you, work with this query planning, you know that, this query is, almost
always possible to plan because we already check it's composition time that, this query
00:31:29:19 - 00:32:20:15
Sergiy
is possible because composition, actually checking that every possible field is possible to
resolve. And this called this, like resolvability check or satisfiability check. Like, in our case we
just name it as a resolvability, but it doesn't matter a lot. What term to use. Yeah. And, s,
composition has this information. Why not to just pass it to the, engine side to the execution
configuration and just make work of the planner and, the in the config much faster and much
more simple, because you could gather a lot of metadata and it will be just there and you could
use it easily.