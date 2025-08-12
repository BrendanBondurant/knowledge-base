---
title: Hypermedia APIs and LLM Agents
slug: ep02-11-hypermedia-apis-llm-agents
series: The Good Thing
episode: 2
chunk: 11
participants:
  - Stefan
  - Jens
segment: Hypermedia APIs and AI Agents
timecode: 00:43:16:25 – 00:47:02:28
start_time: 00:43:16:25
end_time: 00:47:02:28
speakers:
  - Stefan
  - Jens
topics:
  - Hypermedia APIs and REST
  - LLM agents and API design
  - OpenAPI specifications
  - GraphQL vs hypermedia
  - Future of API design
tags:
  - hypermedia-apis
  - ai-agents
  - rest-apis
  - openapi
  - api-design
topic_tags:
  - hypermedia-apis
  - llm-agents
  - rest-apis
  - openapi
  - api-design
entities:
  - WunderGraph
  - GraphQL Federation
  - REST APIs
  - Hypermedia APIs
  - LLM Agents
mentions:
  - OpenAPI spec
  - hypermedia links
  - self-describing APIs
  - agent collaboration
  - API documentation
summary: Jens discusses hypermedia APIs and their potential resurgence with LLM agents.
  He explains how hypermedia APIs provide self-describing capabilities that are perfect
  for AI agents to navigate, while acknowledging that for human developers, structured
  specifications like OpenAPI or GraphQL schemas are more practical. The conversation
  explores the future of API design in the age of AI agents.
---

00:43:16:25 - 00:43:20:11

Jens

Have you ever created a rest API?

00:43:20:13 - 00:43:30:06

Stefan

believe so.

I did, yeah, from the beginning. Yeah. And I had to, like, did it have an Open API spec? I don't

00:43:30:09 - 00:43:56:08

Jens

Yeah. Most, most APIs in the world are Rest APIs without the spec. And there's also, you know,

there's this debate that, like, I really like the, the ideas behind hypermedia. Hypermedia API is a

pretty cool kind of like self describing you go to the API, it it tells you like, hey, here's some some

information and if you want some other information, here's some links and you can follow them.

00:43:56:08 - 00:44:26:29

Jens

And it's super cool. I just think, it's not really for humans. I think humans, they are much better

off with, with a spec. However, I actually believe that, that there will be like a new summer for

hypermedia APIs in the age of of agents because humans, they. For humans to collaborate, it's

better you have an open API spec or a GraphQL schema for, for LLM agents.

00:44:26:29 - 00:44:50:00

Jens

It's super cool. You you give them a thing like, like a user profile, and you give them a link and

say, if you want to have the comments, here's the links to download the comments. This is

absolutely perfect for an LLM agent because it can just then follow. And if you ask the the agent,

hey, can you give me information about Stefan and all the posts he ever did?

00:44:50:03 - 00:45:12:12

Jens

So you go to Stefan's website, you get the the posts. And then it gives you a link to the to the,

you get the info about Stefan, it gives you a link about his post, and then you can download that.

So yeah, I think hypermedia will be, very interesting to to see the, the effects of, of agents on

hypermedia.

00:45:12:15 - 00:45:35:03

Stefan

Yeah. I think it's super exciting. And I mean, it's just a description you kind of gave us with the

rest with GraphQL Federation I think is fantastic. With that, though, I did want to jump back real

quick to, a CEOs point of view. So we have an amazing customer. They're preparing for a Super

Bowl commercial, their first one, and it's going to be absolutely massive.

00:45:35:03 - 00:46:05:13

Stefan

They have a federated architecture. Cosmos kind of is crucial to them, which is why we've been

working so closely for this preparation. But talk to me like what's going on to your head as you

prepare our startup for an amazing opportunity? What are we going to be doing with this

customer? The war room, if you remember. What kind of preparations are we taking in place, to

prepare for this event and what can people expect will come post not mortem, but like after what

will happen, we write a blog post about it, what we describe it.

00:46:05:18 - 00:46:10:26

Stefan

Talk to me about how you're preparing for our Super Bowl event as well.

00:46:10:28 - 00:46:38:18

Jens

Yeah, so we're planning to have a war room to to support them during the event. But actually

we're or I'm thinking of this war room more like observing because I think all the work it needs to

be done ahead of time. If we have to do something in the war room, it's simply too late. So all

the all the load testing, everything, it happens ahead of time.

00:46:38:18 - 00:47:02:28

Jens

We're we're in very close contact with them, now and, yeah, we're, we're, we're working super

hard to, to gather to, to prepare everything to make sure a cache warming behaves the way we

want. So far, results are looking very good. And yeah, obviously for us, it's a, it's a huge

opportunity to to show the, the scalability of our platform. 