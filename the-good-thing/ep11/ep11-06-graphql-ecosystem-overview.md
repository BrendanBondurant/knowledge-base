---
title: GraphQL Ecosystem Overview and API Categories
slug: ep11-06-graphql-ecosystem-overview
series: The Good Thing
episode: 11
chunk: 6
participants:
  - Stefan
  - Jens
segment: API Ecosystem Analysis
timecode: 00:30:13:19 – 00:36:28:19
start_time: 00:30:13:19
end_time: 00:36:28:19
speakers:
  - Stefan
  - Jens
topics:
  - Three API categories: SDKs, MCP, GraphQL
  - SDK generation from OpenAPI
  - GraphQL federation vs query interface
  - Microservices architecture scaling
  - Federation vs custom BFF layers
  - gRPC consumption challenges
tags:
  - api-ecosystem
  - graphql-federation
  - microservices
  - openapi
  - grpc
  - bff-pattern
  - ai
  - api-design
  - federation
  - go
  - graphql
  - llm
  - mcp
  - monolith
  - rest
  - rest-apis
  - startup
topic_tags:
  - graphql
  - federation
  - api-design
entities:
  - Eric Wilde
  - INNOQ
  - OpenAPI
  - GraphQL
  - gRPC
  - News Corp
  - Stefan Avram
  - Jens Neuse
mentions:
  - Eric Wilde API consultation
  - SDK vs MCP vs GraphQL categories
  - Federation algorithm invention
  - REST API middleware layers
  - 20 teams 30 subgraphs example
summary: 'Jens outlines three API ecosystem categories: SDKs for humans, MCP for LLMs,
  and GraphQL for diverse applications. He explains how most people use GraphQL for
  federation rather than query interface, discussing the challenges of scaling microservices
  without federation and the complexity of custom federation solutions.'
---

00:30:13:19 - 00:30:39:18
Jens
But in the, in the API ecosystem, I would say there's three ways of, of using and interacting with
this APIs. So you have open API which allows you to describe your Rest API. And kind of people
figured out that nobody likes to directly use open API. So what people did is they built like there
is many startups now doing it.
00:30:39:18 - 00:31:12:03
Jens
They generate SDKs from open API specifications because people like to have classes or
structs or whatever to call APIs. Okay, so the way humans use APIs is through SDKs. If you
take an open API spec and you annotate it a little bit more with other stuff, you could turn that
into MCP and you obviously you have to talk over over Json RPC.
00:31:12:06 - 00:31:51:27
Jens
So that means you have two categories. You have one category, where we're doing APIs for
humans with SDK s. Then we're doing APIs for, for LLMs and we do it with MCP. And then we
have APIs for a diverse set of, of applications. And we're doing it with GraphQL. So we have a
query interface. And the funny part is how eric wilde was like he wasn't mentioning GraphQL,
but he started with like, yeah, if you don't care about Http and you just want to call classes, then
use SDK s.
00:31:51:29 - 00:32:20:27
Jens
If you don't care about Http, and you're an AI use MCP. And then I was like, yeah, and if you
don't care about Http and you want to have a query interface then GraphQL okay. So I would
describe the current state of the API ecosystem is we have these three categories. We have
SDKs, we have MCP and we have query interface query interface GraphQL.
00:32:20:27 - 00:32:52:17
Jens
It means we have we have a GraphQL API. And we have many clients and they many web
clients, no mobile clients. And they use this API in different ways. So instead of creating one
backend for front end per front end app, you, we have GraphQL. Okay. Now every frontend can
create this thing. And then there's this other, the other side where I think the whole REST
ecosystem, they kind of have it wrong.
00:32:52:19 - 00:33:16:04
Jens
Most people these days use GraphQL not because they want to have the query interface. That's
a cool benefit, but actually because they they want to have the federation. So they they
distribute the implementation of the API across multiple services, which can be which can be
distributed across different teams. And so.
00:33:16:07 - 00:33:17:07
Stefan
Question. Yeah.
00:33:17:10 - 00:33:18:03
Jens
Yeah.
00:33:18:05 - 00:33:31:17
Stefan
Do you think everyone that's using GraphQL will eventually go into Federation. Is that what
you're trying to say there. Like the real benefit is federation. What do you mean by that.
00:33:31:19 - 00:33:34:14
Jens
So.
00:33:34:16 - 00:34:03:00
Jens
You know, a long time ago I stopped pitching, I stopped pitching GraphQL. Yeah. Because.
Yeah, you can, you can, like, I still think it's it's the best way to have multiple apps with different
requirements. And it's, it's great that you have queries and fragments and it makes a lot of
sense. But I, I kind of cool down a bit on, on being like too enthusiastic.
00:34:03:00 - 00:34:33:03
Jens
about GraphQL on the front end side. That being said, on the back end side with Federation, I
think as a, as a lot of larger organization, you, you have to think about, how do you build your
microservice architecture or do you build a microservice architecture at all? But I mean, if you
want to to scale an engineering team, you it's typically very hard to have just one single
monolith.
00:34:33:06 - 00:34:51:09
Jens
And so, yeah, maybe you want to have one service per team, or at least, I don't know, one, 2 or
3 like a handful of services per team, but one service per team could, could be good. And so
let's say you have 20 teams, so you could have 20 subgraphs or more. Maybe you have a few
more.
00:34:51:09 - 00:35:26:14
Jens
Let's say, you are 20 teams and you have 30 subgraphs. If you don't have this federation thing,
what you will have is you have this gRPC thing. So each team has, I don't know, five gRPC
services. So you have 100 gRPC services and gRPC. It's not easy to consume from from the
web. It's not easy to consume from mobile apps, which also means you don't want to consume
100 gRPC services from mobile and web.
00:35:26:17 - 00:35:55:24
Jens
It's it's a complicated architecture. So what can you do? You can build Rest APIs on top BFF
style, or you can build, a unified graph on top. And this is where Federation comes into play. And
now you have to ask yourself the question, like the question I ask myself many years ago, and
when I was working for a big News Corp, do we invent our own federation algorithm?
00:35:55:26 - 00:36:28:19
Jens
Do we do we touch our Rest API middleware layer all the time? When we change
microservices, or can we rely on the framework that federates? And so I don't know these days
why why would you invent your own federation like and up that you know federation can mean
that I updat a microservice gRPC. And then I go to another repository with the Rest APIs, and I
update the client and add the fields to the REST API and so on, so forth.