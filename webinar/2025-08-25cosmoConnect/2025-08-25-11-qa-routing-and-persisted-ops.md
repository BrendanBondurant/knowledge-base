---
type: webinar-chunk
title: Q&A Part 2: Routing Flow and Persisted Operations
slug: 2025-08-25-11-qa-routing-and-persisted-ops
series: WunderGraph Webinars
date: 2025-08-25
speakers:
  - Jens Neuse
episode: null
chunk: 11
segment: Q&A Routing
timecode: 00:50:32 – 00:57:04
start_time: 00:50:32
end_time: 00:57:04
topics:
  - Q&A
  - Routing
  - Persisted Operations
tags:
  - routing
  - graphql
  - ops
entities:
  - Cosmo Router
summary: |
  This Q&A dives into how routing works with plugins, persisted operations, and strategies for exposing minimal GraphQL complexity to clients.
canonical_url: https://your-site/webinars/cosmo-connect-aug25
---

00:50:32:10 - 00:50:39:19
Dustin
Maybe Ludwig can you elaborate? What what is happening inside the router before it makes the
request?
00:50:39:21 - 00:51:00:02
Ludwig
Yeah. So basically we're calling the router with gRPC. We're calling the router with the GraphQL
request, and it goes through our, for our engine logic. So we're going through the whole logic
that we had in place before the whole, GraphQL logic that is doing the planning, normalization
and so on, so forth.
00:51:00:04 - 00:51:19:17
Ludwig
And in the end, we're providing, a GraphQL request to, to, one part of the engine that is taking
this request and converting it in place into a gRPC. Invocation. And this invocation will then be
sent to the subgraph.
00:51:19:19 - 00:51:21:10
Dustin
This is binary, right? This is not.
00:51:21:11 - 00:51:23:00
Ludwig
A binary protocol. Yeah.
00:51:23:02 - 00:51:28:22
Dustin
Yeah.
00:51:28:24 - 00:51:31:08
Jesse
Jacob, I don't know how to allow.
00:51:31:08 - 00:51:38:22
Jens
So we we have Sanath us here also as, as a panelist. So if you if you want to just step in.
00:51:38:24 - 00:52:01:19
Attendee
This is my audio. We're just making sure. Yeah. We hear you. Perfect. Sorry. The question was
phrased. Maybe not so. Well, typically, like you guys have highlighted, the struggle has really
been like, not everyone at the companies that is comfortable GraphQL or something to that end.
So, it sounds like at least from integrating service side, you guys have kind of the not so that
technically a team could not be aware, and we can just build a like a connection piece for them.
00:52:01:19 - 00:52:17:17
Attendee
And I guess a question is that operations has also been helpful for hiding it from the client where
like they say, what they want, we build them the operation and they query the operation without
knowing that much about GraphQL. I guess I'm asking if that stays in this version because.
00:52:17:19 - 00:52:18:10
Jens
Ecosystem.
00:52:18:11 - 00:52:21:00
Attendee
Persisted Operations. Yes yes yes.
00:52:21:02 - 00:52:54:07
Jesse
Yeah. So of course persisted operations are a way to kind of limit what the front end is able to
request from the backend. And that can limit complexity in terms of crazy, weird queries,
destroying your subgraphs with performance or whatever else. But what we've done with gRPC
is actually a bit step, step further than that. And for every GraphQL query that you might be able
to send to the router, for requested persisted operation or not, it gets broken down into a series
of RPCs which are very clean cut, just boxed.
00:52:54:09 - 00:53:08:24
Jesse
Requests for data like you might have a lookup product by ID or get user by name. It works with
entity calls, mutations, queries, all of the different kinds of operations you'd have in GraphQL.
00:53:09:05 - 00:53:33:23
Jens
Thank you to and to to to clarify one thing. So on the backend side, you could kind of say that if
you have one person who knows how Federation works. And by the way, we're currently
building a product that kind of makes it less relevant for everybody to know, how Federation
works. So but but let's talk about that at another time.
00:53:34:00 - 00:54:00:11
Jens
But let's say you have one person they can create perfectly valid, federation. GraphQL SDL, you
run the compiler, it gives you a proto definition. And now the, the backend developer, they can
really focus on. Yeah. Just implementing the, the proto. And, you don't have to, to think too
much about, GraphQL or Federation at all.
00:54:00:13 - 00:54:26:02
Jens
For, for like queries or mutations, you have like, like a root resolver, it will be prefixed with like
query or mutation. But that's, that's the, the only thing that kind of hints that GraphQL is
somehow connected to this thing for everything that is like an entity call, we name these RPC
methods, lookup whatever by whatever, like lookup the thing by the keys.
00:54:26:04 - 00:54:48:21
Jens
That's, that's the message. And then we, we send you a batch of of entity keys, like user IDs or
whatever. And you give us back users. So it's just you, you just implement a loader function
essentially. And then to your point, it's kind of funny that that you're even using Federation when
the backend devs don't want to do GraphQL.
00:54:48:21 - 00:55:09:15
Jens
And the front end guys also don't want to do GraphQL. So why why this whole thing? But I know
why. Because the entity layer is powerful. Just one thing for the future. So the first step, like I
said in the beginning, we're building a puzzle and one piece at a time. And we we we want to do
it properly.
00:55:09:17 - 00:55:38:07
Jens
The first piece, cosmo connect, is towards the backend. What we will do in the future is we will
also work on the frontend side of of the router, like there's very interesting aspects to cover. One
part is the the concept of MCP, like, LLMs. That's a very interesting API consumer. And we, we
want to make it super simple for LLMs to connect to your entity layer.
00:55:38:07 - 00:56:06:01
Jens
So to leverage the entity layer that we have built, that is one part. And the other part is exactly
what you just ask about is we have API consumers that, really like to use a GraphQL layer, for
example, with persisted operations, persistent queries. These are people who love relay or urkel
or Apollo client. And that's one way to consume the graph.
00:56:06:03 - 00:56:29:01
Jens
But another way to consume the graph is to, for example, create a collection of GraphQL
queries and turn that into an SDK, because maybe you have external partners and they they
just want to have an SDK. They, they are not interested in your, in the fact that you're using
GraphQL behind the scenes or something like that. So that's another way of exposing it.
00:56:29:01 - 00:57:04:08
Jens
And I think it would cover your, your use case. And then another, another use case is, especially
for those who built public APIs. They might want to build Rest APIs and, internally, they it's
possible that they have hundreds of subgraphs or subsystems and they want to leverage
federation or like I like to say, an entity layer to bring it all together, maybe use cosmo connect to
connect to all your systems, Kafka or whatever, but then put a Rest API on top.