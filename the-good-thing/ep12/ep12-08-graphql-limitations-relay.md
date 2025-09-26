---
type: podcast-chunk
title: GraphQL Limitations and Relay-Driven Adoption
slug: ep12-08-graphql-limitations-relay
series: The Good Thing
episode: 12
chunk: 8
segment: GraphQL Constraints and Frontend Focus
timecode: 00:26:19:28 – 00:30:09:24
start_time: 00:26:19:28
end_time: 00:30:09:24
speakers:
  - Stefan
  - Jens
topics:
  - GraphQL Frontend Adoption
  - Apollo Limitations
  - Connector Critique
  - SDK Preference
tags:
  - federation
  - graphql-federation
  - ai
  - api-design
  - apollo-graphql
  - cosmo-router
  - go
  - graphql
  - rest
  - rest-apis
  - rest-connectors
entities:
  - Apollo
  - Relay
  - GraphQL
  - Stefan Avram
  - Jens Neuse
  - Jacob
summary: Jens explains how GraphQL adoption is frontend-driven, typically starting
  with teams wanting Relay, then requiring GraphQL servers and eventually federation.
  He critiques Apollo's stagnation after early success and their connector approach,
  arguing that federation is fundamentally limited by GraphQL since most people prefer
  SDKs over building queries.
---

00:26:19:28 - 00:26:44:26
Jens
You have a great client ecosystem like GraphQL is generally speaking, it's front end driven. Like
most, most people. It's not like anybody in the backend is like, hey, I really want to do
Federation. It's it's more or I really want to build a GraphQL server. It's more like, front end guys
say like, hey, we want to use relay.
00:26:44:29 - 00:27:10:27
Jens
Can somebody make it work? And then okay, people figure out, okay, relay, we need a GraphQL
server. And then they realized, okay, we actually want to build the GraphQL server across
multiple teams. And some teams own some parts of it okay. We do federation. But I don't know.
I think in the meantime.
00:27:11:00 - 00:27:45:16
Jens
Honestly, I think in the beginning Apollo had too much success and it, it kind of killed them
because they absolutely stopped innovating. I think the biggest mistake they made is just, I
don't know, not not not thinking further because, federation is such a powerful concept staying
within the GraphQL realm. Yeah. This is such a big mistake.
00:27:45:18 - 00:28:21:15
Jens
And what they are now doing with connectors. I talked to a lot of experts about connectors and
so I wanted to know what what is the take of, of people like, how do they think about
connectors, what do they see in them? And I asked them in a very unbiased way. I also believe I
write that I will do a write up on this in a while, but currently, I'm doing a write up on another
topic.
00:28:21:18 - 00:28:52:08
Jens
But it's the topic of connectors or the direction they are taking. So their approach is no, how can
we help you to get Rest APIs as quickly as possible and glue them to the graph? Yeah. And
there's also this ongoing process of this working group to rethink federation to be more
GraphQL native.
00:28:52:10 - 00:28:55:22
Stefan
Yeah.
00:28:55:24 - 00:29:22:27
Jens
I think I think both both endeavors are like I think it's good to eventually have a specification for
how GraphQL federation should work. Yeah. And at the same time. I think federation as a
concept is limited by GraphQL. It is a good idea that oh, he finally said it.
00:29:23:00 - 00:29:38:29
Stefan
Yeah. I mean I mean the episode, the episode is called beyond GraphQL. And I'll just say one
more time just just so Jacob can clip it that, yes. Yes. So federation is limited by GraphQL. So
what do you mean by.
00:29:39:01 - 00:30:09:24
Jens
Okay. So we have a router and it speaks. It speaks GraphQL. And I think it's great that it speaks
GraphQL. And it will always speak GraphQL. It's like for for people who use relay it's amazing.
Like graphql is amazing for people who use relay for everybody else, it's just a burden. Because
what most people actually want is an SDK and not building queries like nobody wants to build
queries.