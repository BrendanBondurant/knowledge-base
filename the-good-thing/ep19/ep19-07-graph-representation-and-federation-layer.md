---
title: Graph Representation and Federation Layer
slug: ep19-07-graph-representation-and-federation-layer
series: The Good Thing
episode: 19
chunk: 7
participants:
  - Stefan
  - Robert Farr
  - Jens
segment: Graph Architecture and Federation
timecode: 00:32:32 – 00:37:10
start_time: 00:32:32
end_time: 00:37:10
speakers:
  - Stefan
  - Robert Farr
  - Jens
topics:
  - Distinction between graphs and GraphQL
  - Hypermedia as graph interface pattern
  - Procore's internal federation implementation journey
  - Graph representation strategies
tags:
  - graphs
  - graphql
  - hypermedia
  - federation
  - architecture
  - procore
entities:
  - Robert Farr
  - Stefan Avram
  - Jens Neuse
  - Procore
  - GraphQL
mentions:
  - Graph vs GraphQL conceptual differences
  - Hypermedia interface patterns
  - Internal federation experiences
  - Graph representation challenges
summary: |
  Exploration of graph representations beyond GraphQL, discussing hypermedia as a graph interface and Robert's insights from Procore's internal federation implementation journey.
---

00:32:32:19 - 00:33:00:20
Robert Farr
Yeah. So I might my might be a little bit more nuanced. And I would actually argue that, most
companies want a graph. Now, I'll be very, very careful here to say I'm going to separate
GraphQL from graph. Think of graph in terms of the data. And this is one of the reasons why I
think about our information architecture at Pro Core so much.
00:33:00:22 - 00:33:24:28
Robert Farr
Fundamentally, you want to understand all the connections of the data, be able to navigate
through them. So you want a graph, and if you think about hypermedia, one of the intents of
hypermedia was I always thought about hypermedia as a way to expose that graph to a
consumer. Right. Because your you hit a URL, but then you also get linkages to all of these
other things from that point.
00:33:25:00 - 00:33:54:12
Robert Farr
So hypermedia, was a way to expose a graph and you know, exposing a graph can be difficult.
So it and again, it requires your consumer to really need it. Or or you know, gain advantage of it.
So what I, I know we went down the hypermedia route at, at Cerner for a while, and, you know,
what we found is just it was a lot of work and there wasn't really, you know, for the squeeze, the
juice wasn't that good.
00:33:54:15 - 00:34:20:22
Robert Farr
In terms of our, our consumers using it. So, you know, fast forward, you know, when I, when I
start looking at, you know, like the evolution of backends. Right? So we, we moved from
monoliths to, we swung the pendulum towards microservices, everything. We created new
problems. Right. Because now, I always say there's a federation layer somewhere, right?
00:34:20:22 - 00:34:50:25
Robert Farr
There's a layer within your, within your software stack where you're trying to pull things together
into a unified single thing. Right? Sometimes that's your public API surface. Microservices
moved that out of the database, right? Effectively. And they moved it into this hypermedia layer.
And, you know, what I've seen done in the past is, you know, one one approach to that is you
have an internal API surface.
00:34:50:27 - 00:35:17:19
Robert Farr
A lot of times that's gRPC, or maybe it's, it's, you know, Http, and then you have an external API
surface. And and behind that external API is, you know, some stateless, piece of software that's
then making other API calls, on your behalf. And it's all, you know, hand handwritten, right hand
constructed. And, you know, that's one way to try to create that separation.
00:35:17:19 - 00:35:43:25
Robert Farr
And GraphQL Federation, I think, builds that in, which is one of the really intriguing things about
it. But it's been interesting, right? Like as you look at the industry and I, you know, I've said if if
GraphQL and GraphQL Federation were there the day that, you know, REST came about, then
it probably wins right, because there was a, there was a pivot point in the industry there.
00:35:44:03 - 00:36:10:17
Robert Farr
But REST was there. And so they kind of took the day. And so now, you know what I've seen,
with GraphQL specifically, kind of with hypermedia is this challenge of who are the consumers,
right. And again, today or up to this point, our consumers have been developers, right, web
developers, internal or external developers. And so now you're you're, you know, these
changes, right?
00:36:10:17 - 00:36:48:27
Robert Farr
They're changing those patterns. One thing has kind of won, but now we, we AI enters the
picture. Right. And this is the for me, this is a game changer because it, you have an opportunity
right to now say, well, what's the best API that I can provide to an agent? You know, kind of like,
you know, so they're, you know, now we're kind of back to, like, well, hey, wait, GraphQL
Federation or hypermedia, something that's going to allow me to express the graph of the
underlying data graph that we have to that LLM.
00:36:48:29 - 00:37:10:19
Robert Farr
And then now, right now, we can start to, pull something together that's really useful for, you
know, customers of that, that functionality. So I think that's, you know, we're we're in this window
right now of, of, I would say exploration with AI. Right? Were we're not I wouldn't say we're to
the point of where we're really exploiting it yet.