---
type: podcast-chunk
title: AI-Assisted Plugin Development
slug: ep27-13-ai-assisted-plugin-development
series: The Good Thing
episode: 27
chunk: 13
segment: AI-assisted workflows for REST and gRPC plugin automation
timecode: 00:54:02 – 00:59:06
start_time: 00:54:02
end_time: 00:59:06
speakers:
  - Jens
  - Dustin
  - Jesse
topics:
  - AI-Assisted Development
  - Plugin Automation
  - REST Integration
tags:
  - ai
  - plugin-architecture
  - grpc
  - rest
entities:
  - Cursor
  - WunderGraph
summary: Jens and Stefan discuss AI-assisted development using Cursor, explaining automation for REST integration and how gRPC plugins simplify complex workflows.
---
00:54:02:25 - 00:54:14:29
Jens
I think I feel much better if we don't have our own storage. Like let people from Cloudflare store
the stuff they they can figure this out.
00:54:15:01 - 00:54:17:24
Jesse
I meant using, like, GHCR or if you're,
00:54:17:27 - 00:54:49:04
Jens
Oh, yeah, I see. Okay. Well, one one last topic for for Dustin cursor. And then, to close it up, I'm,
I will do one round of what? What are you proud of? Like something you have built the last
couple of months can be Cosmo connect related. Can be anything like something you're you're
really proud of, where you say, okay, this is I built something cool before we come to that, which
will conclude our our end of this, session today.
00:54:49:04 - 00:55:17:11
Jens
We started a bit late, and we we we just drag it a little bit, but, one last topic. Dustin. Cursor. We
all we're all lazy. Developers are lazy. Nobody wants to write code that's, like someone said, at
some point, a human shouldn't do what a machine could do. And, writing glue code to to
connect to a REST API.
00:55:17:11 - 00:55:51:04
Jens
That's, that's maybe a case where, where AI could, could do some stuff. But, one of my early
experiments showed it's actually not so easy to connect or to, to implement, an Apollo
Federation subgraph with LLMs or cursor or claude code. And you have invested a little bit into,
into Cosmo Connect and it it actually works with LLMs or like how does it look like.
00:55:51:07 - 00:56:21:11
Dustin
So so right now when we, like we in the first iteration of Cosmo Connect, we, we relied heavily
on convention like we have different directories where we put the binary where you have to put
the graphql schema file in it, but you have where we store the generated files from the graph, go
to proto conversion. And this struct allowed us to define like a cursor or windsurf or claude
template that that is able to instruct how to actually operate a plugin.
00:56:21:13 - 00:56:49:09
Dustin
That means how to build it, how to generate it, how to test it. And if you if you're doing some
clever prompt engineering inside, it, it is possible to instruct a claude, claude for instance, or
cursor to, to implement an open API specification. And this workflow works pretty well. And in
this way you can actually integrate, bridge REST APIs very easily in almost no time.
00:56:49:11 - 00:57:20:16
Dustin
However, this always comes with limitations. So you also need to be able to solve use cases
like. where you have an open API specwith thousands of endpoints. Right. And this will,
obviously overwhelm, the LLM, to do things right. And for this purposes, we also have a different
product in the pipeline that allows you to to split those, graph those gRPC endpoints in, in
several, I would say, pieces so that multiple agents can run on these things in parallel.
00:57:20:18 - 00:57:39:01
Dustin
And it's not yet part of Cosmo Connect. But we are very, we are aware of that. The limitation I
would describe that the user need to solve your on your own and yeah, exciting stuff. And we,
we also, I hope also have a, good thing about that as well.
00:57:39:03 - 00:57:48:05
Jens
So we're, we're, we're looking into bringing API integration and getting that on, on autopilot.
00:57:48:08 - 00:57:57:28
Dustin
Exactly. So that someone can easily. Yeah, easily bridge an existing rest API within a day,
including tests, everything.
00:57:58:00 - 00:58:15:25
Jesse
I think one of the understated benefits of using gRPC for having your a your AI assistant write
things is that it's very easy to tell when a gRPC API is behaving within spec. It's not so easy with
a GraphQL API. If you developed your own GraphQL server from scratch, and you wanted to
make sure it was working correctly.
00:58:15:25 - 00:58:38:03
Jesse
You have to kind of try everything. This underneath this, underneath this, like, ABC, all these,
like, nested queries. You do, things that return arrays or, all these different ways of creating the
same data in order to make sure that it's doing the right thing with gRPC, there are RPCs and
they have an input type and a return type.
00:58:38:05 - 00:58:47:01
Jesse
And if they act within that spec in the kind in one test, they will do it in any circumstance and
more or less.
00:58:47:04 - 00:59:06:07
Dustin
And when we convert like GraphQL to protobuf, we also we change the GraphQL descriptions.
That means this is this will also serve as additional context to LLMs to understand the full, full
context of of your of your domain.
