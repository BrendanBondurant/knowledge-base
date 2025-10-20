---
type: podcast-chunk
title: How Composition Simplifies Query Planning
slug: ep07-07-composition-simplifies-query-planning
series: The Good Thing
episode: 7
chunk: 7
segment: Composition metadata and query planning optimization
timecode: 00:32:20 – 00:38:24
start_time: 00:32:20
end_time: 00:38:24
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - Composition Metadata
  - Query Planning Optimization
  - TypeScript vs Go
  - Compiler Hints Analogy
tags:
  - composition
  - query-planning
  - metadata
  - typescript
  - ai
  - apollo-graphql
  - benchmarking
  - cosmo
  - cosmo-router
  - federation
  - go
  - graphql
  - graphql-federation
  - startup
  - supergraph
  - composition-algorithms
  - query-optimization
  - persisted-operations
entities:
  - Cosmo
  - Apollo
  - TypeScript
  - Golang
  - WunderGraph
  - Sergiy
  - David
  - Jens Neuse
summary: Sergiy explains how Cosmo's composition precomputes metadata to eliminate
  duplicate work in query planning. The discussion covers architectural decisions
  between TypeScript composition and Golang execution, the benefits of avoiding Apollo's
  supergraph format, and how composition acts like compiler hints for the query planner.
---

00:32:20:18 - 00:32:55:27
Sergiy
The funny part that, we don't even always need to read the subgraph graphql schemas.
Sometimes in the planning we just read the metadata because, yeah, otherwise, anyway, you
will need this information to do something like, for example, you need information like, what is
entity nodes, what is their root query type nodes like, from where you could start the query from
where you can start to query, you need to know, is field external or is this field is provided.
00:32:55:29 - 00:33:26:00
Sergiy
We need to know like, what what keys do I have? Like, and yeah, it is possible to do all that,
when you just loading files, but it will be double work, basically, because we already have done,
every bit of that, almost every bit of that information already was done in the composition. Like
why we would need to replicate it again and, in the, query planning stage.
00:33:26:03 - 00:33:52:15
Sergiy
If we could just use this data. But the important thing, thing, thing here is that, our composition is
built with, TypeScript and execution engine built in in Golang, And, yeah, it will be a huge
investment to build composition in go or to build to, execution in TypeScript. And which do not
have any sense for us right now.
00:33:52:17 - 00:34:18:27
Sergiy
And, TypeScript really allows you to iterate very fast. Like, I had a previous experience of being
a Ruby developer, and, yeah, each time you start a new project, you just bootstrap everything
very fast. And, during, our testing, we always, use JavaScript subgraphs because it is very fast
to build some mocks, to build some subgraphs.
00:34:18:29 - 00:34:42:16
Sergiy
And, yeah, it is convenient way, it is not fast to execute, that in production, but a lot of our
customers are still using it. But, yeah, it works for us. And, there was some questions from some
of the customers. That's why we don't use the same format as, other gateways doing.
00:34:42:18 - 00:35:11:12
Sergiy
But that format is not that useful for us. Like, we, we won't get the same benefits of having this
format because, yeah, we still will need to process it and to create metadata. And it is more
convenient for us to work with, not in interchangeable format, but in case you use our
composition, you just have everything built in, and it works just smooth.
00:35:11:15 - 00:35:13:05
Sergiy
This.
00:35:13:07 - 00:35:41:13
Jens
Yeah, I, I personally like to think about query planning a lot. It's a bit like a compiler. And so what
you're saying it's a bit like composition creates compiler hints. And then the compiler can do less
work. It can be less complex. The compiler can be simpler. Is that fair?
00:35:41:15 - 00:36:00:15
David
And say as much as possible because just because of the nature of composition, you have to
look at a lot of things, to, to be able to know that something can successfully compose. So
you're doing work there, like you have to know what's external. You have to know where fields
live and and how they interact with each other.
00:36:00:18 - 00:36:21:21
David
And the query planner to some extent also needs to know what fields are external. So if I if we
can do that work once in composition, and then basically save that result and pass it to the
query, you're saving that doing that work again, you do the work once and then you share that
work. And then nobody has to do the work again because it's already been done.
00:36:21:23 - 00:36:47:19
David
And we and we basically do that as much as, as much as possible. And, and and like you say,
offer that in terms of how, what's in the, what's in this, JSON what's in this metadata to be able
to for the router to consume that and then eventually by the engine from the router, to produce a
result basically as efficiently as possible with as little work done twice as possible.
00:36:47:21 - 00:37:04:13
Jens
Yeah. So that that kind of means if you have a super graph structure that doesn't contain all this
information, you at some point you probably have this information, but you threw it away. And
now query planning needs to do it again.
00:37:04:15 - 00:37:33:08
Sergiy
Yeah, it basically will sometimes you anyway will need to read or recreate the structure of the
subgraphs like, but when you or when you have just a single schema, you probably will
decompose it again into a single subgraph to see what is actually valuable. The, you will build
this representations of subgraphs, probably in programmatic way.
00:37:33:10 - 00:37:58:18
Sergiy
And, we kind of doing that, but we mostly just, reading this information and yeah, we still have,
subgraph information and, we still have access to the, original subgraph schemas, because
sometimes you need to see, like, how it was, define it. And in this particular subgraph, like
sometimes you do not have a direct match on a field.
00:37:58:20 - 00:38:24:02
Sergiy
Like, for example, you could have interface define it in one subgraph and all the same field, it
will be just, just a, sum of the concrete types of this interfacing on the subgraph. And, it will
work. But, during the planning, you need to say, like, could I just plant this type on this,
subgraph or should I just remove this selection set because it doesn't make any sense?