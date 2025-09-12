---
title: Technical Challenges in Schema Mapping
slug: ep27-05-technical-challenges-in-schema-mapping
series: The Good Thing
episode: 27
chunk: 5
segment: Type handling, nested lists, nullables, and engine design
timecode: 00:21:23 – 00:27:17
start_time: 00:21:23
end_time: 00:27:17
speakers:
  - Jens
  - Dustin
  - Ludwig
topics:
  - Schema Mapping
  - Type Handling
  - Engine Design
tags:
  - graphql
  - grpc
  - schema-design
  - data-modeling
entities:
  - GraphQL
  - gRPC
  - WunderGraph
summary: Discussion of complex schema mapping challenges, focusing on nested lists, nullable field design, and underlying engine implementation details.
---
00:21:23:03 - 00:21:28:09
Jens
Is it easy? Is is there something that to that you learned in doing this.
00:21:28:12 - 00:21:53:23
Dustin
Ludwig mentioned the mapping file. And one thing I mean, the obvious reason why we, we
choose this approach and why we started, thinking about this, like in proto, the feed order is
significant. It's a binary protocol. So you cannot just move fields around. Otherwise it's no longer
binary compatible. In GraphQL you can move arguments, you can change fields.
00:21:53:23 - 00:22:02:00
Dustin
All the it doesn't matter. That means we have to retain retain this information through the
conversation conversion process and then be stored into the mapping file . So and are.
00:22:02:00 - 00:22:10:08
Ludwig
You mixing up two things right now. We have the mapping file and We have the log file, the log
files for the for the field order and the mapping files just for the naming.
00:22:10:10 - 00:22:11:28
Dustin
Okay.
00:22:12:00 - 00:22:13:05
Jens
Dustin.
00:22:13:07 - 00:22:17:01
Dustin
Because good that you mentioned it.
00:22:17:03 - 00:22:17:14
Jens
Yeah.
00:22:17:16 - 00:22:20:23
Ludwig
I think you can talk about the log file later.
00:22:20:25 - 00:22:48:07
Jens
Okay. Because cosmo is such a big space. Yeah. The there's a lot of moving parts. Yeah, but,
we talk about the, the log file later because, I learned something from Dustin in this, doing this, I,
I didn't know there is a cool keyword in, in, in, in gRPC. It's called reserved.
00:22:48:13 - 00:23:18:01
Jens
I, I didn't know about reserved. And, Dustin pointed me towards it. It's pretty cool. But we talk
about this this later. Ludwig. And anything in your process of, like, taking subgraph requests that
are like, GraphQL over Json, over HTTP, turning that into gRPC, anything that was hard or
something you learned or anything you want to share.
00:23:18:03 - 00:23:57:12
Ludwig
I would say the whole project was a big learning process for me, because when I started with
this project, my my knowledge in our engine repository was quite limited. I've been mostly
working on on Cosmo Router features. The engine part was always like this very complex
planning parts. No one understands. When I started working it, I got a lot of support from,
especially, like from Sergei who, who showed me a lot of things how to use the libraries in
different, different packages that allow me to, traverse, for instance, GraphQL requests,
schemas.
00:23:57:12 - 00:24:25:05
Ludwig
And, what, what kind of metadata we already have available. So, I would say, the first challenge
for me was like getting into, understanding how the engine works internally. So, so I started
writing a visitor. The way that we're doing it, usually in our engine code, is we're writing a lot of
visitors, do, validation, post-processing, post-processing, and so on.
00:24:25:07 - 00:24:48:12
Ludwig
And I started with a simple visitor that would take a simple request, a simple GraphQL request
like, create user or create users where one field without arguments and just convert it into a
very, very simple, gRPC request. And after I was done with that and after I had my initial
moment, my, wow moment, okay.
00:24:48:12 - 00:25:09:09
Ludwig
It works. So I started digging deeper. I started, with, okay, let's start. Let's start with different
data types. We're supporting different data types. And we need to support like scale data types
in GraphQL. We need to support like the base, the base types in, protobuf. They also
sometimes translate differently.
00:25:09:09 - 00:25:33:26
Ludwig
For instance, in GraphQL, we don't have a 64, bit integer. So, we only have 32, 32 bits. But
instead the float in GraphQL is actually a double precision float in, in protobuf. So we would
translate float to double. So so I started digging deeper and deeper and I, I just fell on top of it.
00:25:33:26 - 00:26:08:14
Ludwig
And I always had in mind that I want to build something that kind of keeps it simplicity, while still
having, like, a good, way of using it, like, provides a good developer experience. I wanted to
keep it super simple. Not not making making it super complex with nested messages and, like
very nested complex types. So I wanted to keep it as close as possible to the original design of
the GraphQL schema.
00:26:08:16 - 00:26:38:21
Ludwig
So, yeah. So it was a, gradual process from starting, super, super low and with basic types and
then going over to arguments, then, thinking about Federation directives like, how can I build my
first entity, look up and then at some point we reached a point where we started working with
lists and, I was like, oh my God, this is this is very tricky because in protobuf, for instance, you
can't have lists of lists.
00:26:38:24 - 00:27:03:01
Ludwig
The repeat is only, available for, for a single type. So you can't do repeated repeated type. So
we have to come up with, with the way of translating nested lists into something that, that
protobuf can understand. And also on the engine side, we need to handle different ways of
handling lists because you can have a nullable list, you can have a non nullable list, you can
have a nullable of non nullable lists.
00:27:03:01 - 00:27:17:22
Ludwig
And was kind of interesting. So, so we had to do a lot I had to do a lot of, logic bouncing
between the two. The two designs.
