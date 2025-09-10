---
title: GraphQL to gRPC Schema Translation Workflow
slug: ep27-04-graphql-grpc-schema-translation
series: The Good Thing
episode: 27
chunk: 4
participants:
  - Jens
  - Stefan
segment: Translating schemas and generating dynamic messages
timecode: 00:16:52 – 00:21:23
start_time: 00:16:52
end_time: 00:21:23
speakers:
  - Jens
  - Stefan
topics:
  - GraphQL Schema Translation
  - gRPC Schema Mapping
  - Dynamic Message Generation
tags:
  - graphql
  - grpc
  - schema-translation
topic_tags:
  - graphql
  - grpc
  - schema-translation
entities:
  - GraphQL
  - gRPC
  - WunderGraph
mentions:
  - dynamic message workflow
  - schema conversion challenges
  - automated translation tools
summary: Jens and Stefan break down the workflow for translating GraphQL schemas to gRPC, covering dynamic message generation and challenges in schema mapping.
---
00:16:52:20 - 00:17:28:10
Jens
Okay. Well well said. So cosmo connect. I have, I have a super graph and I have a router and in
this super graph I have one subgraph. I have defined it as, like I have a schema, like, like Apollo
Federation subgraph spec compliant subgraph schema. So that's one thing I have. And then I
have my router and I have my gRPC proto thing.
00:17:28:13 - 00:18:08:00
Jens
So now if I, if I send, a request to the to the router, and we get some data from a GraphQL
subgraph and we get some data from a gRPC subgraph, what what happens? Can I like, how
do you translate between GraphQL and gRPC? Because if I'm like a regular gRPC user, the
way I'm used to to doing gRPC is I have this proto stuff, I run some proto C thing and it
generates code, and then I have a proto, gRPC server.
00:18:08:04 - 00:18:29:00
Jens
But in the case of the router, what does it just said this. We are not recompiling. We're not like
when you change your subgraph, you you don't have to rebuild the router with new proto
definitions. Somehow we're building these messages on the fly. How does it work?
00:18:29:03 - 00:18:58:07
Ludwig
So basically you start off with designing your graphql schema, just the way it's always been
before you think of a schema that not matches your architecture or fits into your existing
architecture. And then after you're done with your with your graphql schema, you can use, our
fancy library proto graphics in combination withour CLI WGC. And you just, you use the schema
as an input and you generate protobuf out of it.
00:18:58:07 - 00:19:23:24
Ludwig
So you get a protobuf schema, and you also get, get a mapping file. So, so basically because
GraphQL and protobuf are quite fundamentally different, there's also like different syntaxes,
different ways of handling types. We use we use our protographic library to, to find the best way
to, to match between the two environments.
00:19:23:26 - 00:19:54:07
Ludwig
So, we're generating a proto schema from, from the graphql schema. The user can then take
the schema and just generate their proto bindings from it. On the other hand, when we're
composing, all our graphs into a route execution config, we're putting together all the information
that are required. So, we're getting the, the graphql schema, which is important for an engine to
understand what types are the, available in my my graphQL sense.
00:19:54:07 - 00:20:26:26
Ludwig
Because I see I'm still talking graphql to my router while I'm talking gRPC to my, to my service.
So my router level I still need to understand GraphQL, but we only need the schema for that.
But on the gRPC level, we just need the, the protobuf schema. And we can compile this
protobuf schema using, library, and convert it into an ast and then and then use all the
information that we can get from it, like the type descriptors and whatever, and build up
dynamic, proto messages.
00:20:27:02 - 00:20:54:22
Ludwig
So, while we're getting GraphQL requests, we can just take this request and convert it into, into
protobuf messages dynamically and then send them over to, to our subgraphs our gRPC
subgraphs. And it using a mapping file will allow us to, to retain the information that we get from,
from the from the original GraphQL schema to the protobuf schema to to get a mapping
between the type and names.
00:20:54:25 - 00:21:23:02
Jens
Okay. So you have a mapping, you have the message descriptors. And there is like a dynamic
library. It allows you to to create those messages on the fly. So you take subgraph requests. You
transform them into into gRPC proto messages sent them, get them back and all without the
compile time step. What what were the, were there any challenges?
