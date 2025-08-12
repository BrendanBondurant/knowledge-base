---
title: Supergraph Unification Strategy and API Evolution
slug: ep11-09-supergraph-unification-strategy
series: The Good Thing
episode: 11
chunk: 9
participants:
  - Stefan
  - Jens
segment: Future of API Unification
timecode: 00:48:14:16 – 00:53:01:04
start_time: 00:48:14:16
end_time: 00:53:01:04
speakers:
  - Stefan
  - Jens
topics:
  - WunderGraph's Conway's Law application
  - API unification through supergraph
  - MCP and SDK integration strategy
  - Moving beyond connector approach
  - GraphQL Gateway evolution
  - Fundamental architecture piece vision
tags:
  - connector-approach
  - ai
  - api-design
  - cosmo
  - go
  - graphql
  - grpc
  - mcp
  - rest
  - rest-apis
  - rest-connectors
  - startup
  - supergraph
topic_tags:
  - connector-approach
entities:
  - WunderGraph
  - GraphQL Gateway
  - Backstage
  - Dustin
  - Stefan Avram
  - Jens Neuse
mentions:
  - one engineering team structure
  - GraphQL Go tools outpost
  - thousand REST APIs problem
  - 2019 GraphQL Gateway
  - directives approach rejection
  - supergraph as fundamental piece
summary: Jens outlines WunderGraph's strategy for API unification through supergraphs,
  explaining how organizations need to move beyond tools like Backstage to handle
  thousands of APIs. He discusses plans to simplify bringing APIs onto supergraphs
  and rejects the connector approach in favor of their own direction, positioning
  supergraphs as fundamental architecture.
---

00:48:14:16 - 00:48:21:04
Stefan
With our organization and our architecture, what's our Conway's Law? How are we as an
organization?
00:48:21:07 - 00:48:35:12
Jens
Great question. How many engineering teams do we have? One How many cosmo
repositories? One kind of right. It's actually not true because.
00:48:35:12 - 00:48:37:07
Stefan
Yeah, we have a little small subteams.
00:48:37:07 - 00:48:44:26
Jens
So we have a small sub team. It's building the engine. Yeah. They have their own repo right.
00:48:44:29 - 00:48:46:11
Stefan
Yeah GraphQL go tools.
00:48:46:14 - 00:48:57:12
Jens
Yeah. And everybody else is working on the same thing. So we have one large team one. And
then we have the little outpost the engine outpost. And it's all a second team kind of.
00:48:57:14 - 00:49:09:07
Stefan
And that's literally it. Yeah. But okay so with Conway's Law does does this only involve
engineering like, well like is marketing and like sales in an organization, are they also affected
by Conway's law or like how does that work.
00:49:09:09 - 00:49:46:22
Jens
Yeah, sure. Like they might have the CMS or other things or whatever. So yeah. But coming
back to your question about the the future of GraphQL, so I think what we currently see is with
MCP, LMS, everything, there's a there's a huge need for organizations to unify all APIs. And if
you have in the past there's tools like backstage or whatever, you can put all your Rest APIs.
00:49:46:24 - 00:50:11:09
Jens
It just doesn't cut it because, now you have a problem if you want to build SDKs on on a
thousand Rest APIs, or if you want to if you want to do MCP on one thousand Rest API, it's very
hard. Much simpler if we can do it on top of one super graph. So for us, next step like super
graph we double down on on the concept.
00:50:11:09 - 00:50:36:21
Jens
Super graph is good. The more APIs you bring onto the super graph, the better. Yep. And then
the super graph should be able to to speak whatever GraphQL is good SDKs on top of the
super graph is good. And then you have you have RPC like SDK is RPC. Essentially we did this
in the past with the SDK.
00:50:36:27 - 00:50:38:08
Stefan
I remember yeah.
00:50:38:11 - 00:51:03:29
Jens
This is something that's coming back and also things like MCP. So it's it's it's obvious that okay,
we unify all our APIs into a super graph. And then we make it simple to put SDK s and MCP on
top. And then everybody can can leverage the super graph. So that gives us a pull on the super
graph. So now everybody will be like oh if you can bring it on the super graph, it gives us super
powers.
00:51:04:01 - 00:51:31:28
Jens
Awesome. So the next step is we need to we need to bring everything on to the super graph. So
we need to make it much, much, much, much more simple. Yeah. To bring stuff onto the super
graph. And we're investing into this topic heavily. And yeah, I think, we, we have, like there's
different takes in the industry how to do it, I think.
00:51:32:01 - 00:52:05:20
Jens
So we have validated our idea with many smart people. And if you, if you not sure if you
remember, but I built something called Graph QL Gateway in 2019, so six years ago, a year.
And it used directives to describe data sources. So, Dustin is a team to you remember how we
how we, how we.
00:52:05:20 - 00:52:33:16
Jens
Yeah. In for my initial version of the graphql gateway, it used directives to describe how the
gateway should talk to data sources. And yeah, I don't think it's the right approach. So you will
you will see from us a different approach, not the not the connector route. We don't believe in
the, in this connector approach. We think we should go another another direction.
00:52:33:18 - 00:53:01:04
Jens
So, yeah, I think the super graph, it will be, a fundamental architecture piece, for, for every
company. And it will be extremely powerful. And I don't see how REST or gRPC or anything else
has, has something has something similar. And you can very easily put on top of a super graph
SDKs and MCP.