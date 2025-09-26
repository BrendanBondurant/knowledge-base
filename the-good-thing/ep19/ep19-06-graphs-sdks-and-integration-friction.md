---
type: podcast-chunk
title: Graphs, SDKs, and Integration Friction
slug: ep19-06-graphs-sdks-and-integration-friction
series: The Good Thing
episode: 19
chunk: 6
segment: Integration Patterns and Developer Tools
timecode: 00:27:21 – 00:32:32
start_time: 00:27:21
end_time: 00:32:32
speakers:
  - Stefan
  - Robert Farr
  - Jens
topics:
  - SDKs and Integration
  - Webhooks and Real-Time Patterns
  - Graph Representations
  - External Integration Friction
tags:
  - federation
  - grpc
  - mcp
  - ai
  - api-design
  - go
  - graphql-federation
  - rest
  - rest-apis
entities:
  - Robert Farr
  - Stefan Avram
  - Jens Neuse
  - Procore
summary: Discussion of integration patterns including SDKs, webhooks, and graph representations,
  exploring how service fragmentation creates friction for external integrations and
  developer experience.
---

00:27:21:13 - 00:27:22:23
Robert Farr
This this is.
00:27:22:25 - 00:27:47:21
Jens
This is so much smarter than MCP. Are we doing it? No, because I think most people don't
understand the intentions of the web. And, so I, I fully agree with you in the sense that and this
is how my how my thinking has evolved over the years. In the beginning, I was, I was, driven by
excellence.
00:27:47:21 - 00:28:34:09
Jens
I was driven by perfection. And I thought the best solutions are the ones that are perfect from a
technical point of view. And what I have learned is the the reality is the best solutions are the
solutions that work for the people who need them. And what you're saying, I think, I would add
one thing you said, RPC, I agree RPC is great and I would add web webhooks because, if you if
you have an integration with something like GitHub and then something happens, you need to
be notified about that and you want to you want to have notifications that are not tied to an open
connection or something that are super
00:28:34:09 - 00:29:02:17
Jens
simple to implement, and nothing is easier to implement than, than uh web hook. So, so I think,
RPC and webhooks are great. And then another opinion I have and happy to to see if you if you
disagree or have another opinion. But one thing I have observed is a lot of companies try to use,
internally, try to use gRPC and REST.
00:29:02:20 - 00:29:34:21
Jens
And I think it's not working well. And I know I'm biased, but I think internally everybody should
have a graph because, the, the, the for me, the, the big advantage of having a graph is you're
not tying a resource to one service because I think the, the, the absolute worst thing you can do
is you can say we have this core entity in our construction, whatever.
00:29:34:24 - 00:30:03:11
Jens
And it has 50 fields and they all must be implemented by one service. And that's just not going
to fly. Because what what you will run into is you will have you know, in in a domain model, you
always have like certain entities that somehow they are correlated to everything, like a user
object or something. And then everybody comes to this user service and says, guys, we need to
integrate with your user service.
00:30:03:11 - 00:30:26:03
Jens
It needs to give us certain things. And then suddenly user service, 50 fields, 100 fields,
whatever. And every time someone wants to somehow evolve the API, they have to add
something to the service. And this is where, where, Federation would, would simply allow you to
say you can add three fields and you put them into another service.
00:30:26:03 - 00:30:51:20
Jens
And that means you're, you're freeing up this one team to that, that owns this. But on the
surface, I think so internally a graph and then to the outside some sort of webhook system. And
I think to the outside there should be an easy way to create SDKs because that's, that's another,
opinion for me that has evolved.
00:30:51:22 - 00:31:23:27
Jens
When I was like a few years ago and I was observing how everything unfolds, I saw that
somehow REST APIs are winning. And I was wondering, is it like are Rest API is really that
good? And kind of what what what crystallized for me is nobody wants REST APIs because they
are also they typically lead to situations of very tough conversations because it's not entirely
clear how you should structure a URL.
00:31:24:00 - 00:32:12:07
Jens
Do you put the version in the in the URL in the header in whatever, and then you can have so
many debates around whether you should design something like this or that. Super simple,
straightforward solution, just RPC, JSON over Http and then yeah, some sort of RPC contract,
wrap it up with SDKs and make it simple for people to to download an SDK and have like, type
safe integration, which also I think in the, in the age of AI if I want to integrate with Pro Core,
give me an SDK, give me documentation how the SDK works, and I can tell Curser to vibe code
whatever we need because it can just call these
00:32:12:07 - 00:32:32:16
Jens
functions and it's clear what they return. And then I think yeah, for, for, for those reasons. So
yeah, my, my opinion internally you should have a graph. You should have to the outside you
should have a webhook system, JSON, RPC, SDKs. What's your take.