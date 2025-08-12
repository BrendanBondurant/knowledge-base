---
title: Federation Adoption Barriers and Scale Requirements
slug: ep12-13-federation-adoption-barriers
series: The Good Thing
episode: 12
chunk: 13
participants:
  - Stefan
  - Jens
segment: Federation Adoption Analysis
timecode: 00:47:16:25 – 00:51:11:28
start_time: 00:47:16:25
end_time: 00:51:11:28
speakers:
  - Stefan
  - Jens
topics:
  - Limited companies with 100+ frontend developers
  - Federation adoption challenges
  - Small team GraphQL experiences
  - Federation without GraphQL feasibility
  - RPC vs GraphQL complexity
  - Uniform API interface value
tags:
  - federation
  - graphql-federation
  - mcp
  - ai
  - api-design
  - go
  - graphql
  - rest
topic_tags:
  - federation
  - graphql-federation
  - mcp
entities:
  - Meta
  - Coinbase
  - Gartner
  - GraphQL
  - Federation
  - Relay
  - MCP
  - JSON RPC
  - Stefan Avram
  - Jens Neuse
mentions:
  - Twitter GraphQL criticism
  - under-fetching over-fetching problems
  - 1-2 engineer teams
  - Relay complexity concerns
  - MCP preferring RPC
  - domain model clarity
summary: Discussion of why federation adoption remains limited, with Jens arguing
  that few companies actually have 100+ frontend developers working on one frontend.
  Stefan challenges this by noting small teams trying GraphQL and failing, leading
  to the question of whether federation makes sense without GraphQL/Relay, given RPC's
  simplicity compared to GraphQL's complexity.
---

00:47:16:25 - 00:47:24:16
Jens
And this is where, where relay really where relay shines.
00:47:24:19 - 00:47:27:00
Jens
Where this approach relay shines.
00:47:27:00 - 00:47:43:06
Stefan
Oh no. It makes sense. It just makes sense in the name to. I actually never thought about it that
way. And then when you explain it, I can see why it makes so much sense with GraphQL. And it
makes sense when you would use relay. If you have multiple teams that are creating multiple
components, multiple changes, you're a big scale company.
00:47:43:06 - 00:48:07:06
Stefan
Things change. It absolutely makes sense. It's interesting. But okay, so going back so we went
on a tangent as always we went from APIs. We went with the future of federation. Federation is
held back by GraphQL. I can't get that out of my head like what is the next iteration for
Federation? Where where do you see this world going?
00:48:07:06 - 00:48:24:13
Stefan
And I ask this question again, but why aren't more companies adopting federation? Sure, you
have the Gartner metric. People are like, yeah, we're adopting it. But this whole point with
relays, why are more companies at scale using relay? Why aren’t more companies using
federation if it clearly makes sense?
00:48:24:15 - 00:48:37:17
Jens
I think this is it's kind of easy to answer, like how many companies are there where you have a
hundred front end developers or more working on a website.
00:48:37:19 - 00:48:41:11
Stefan
I mean, thousands or hundreds of thousands probably. There's a lot.
00:48:41:13 - 00:48:42:13
Jens
No.
00:48:42:16 - 00:48:43:21
Stefan
You don't think so?
00:48:43:24 - 00:49:00:13
Jens
Like, there's no like, you know, which company has 100 front end developers? Like, I'm not
saying developers, but. Oh, 100 front end developers working on front end on one front end.
00:49:00:16 - 00:49:00:29
Stefan
Yeah.
00:49:01:05 - 00:49:16:26
Jens
Okay. Like yeah. Meta and Coinbase and some others. But ultimately the, the, the surface area
of people like I don't know, you know, and it's about practicality. But.
00:49:16:29 - 00:49:36:09
Stefan
But wait, wait, wait. Because this is the biggest argument that I see a lot on Twitter is that
people adopt federation or they adopt GraphQL, or they adopt relay and they have 1 or 2
engineers. And so what they say is we tried GraphQL. We hated it. And then you ask them,
okay, why do you try GraphQL. Under fetching over fetching problem.
00:49:36:09 - 00:49:50:09
Stefan
Okay. And also we only had a couple developers. Do you think Federation and GraphQL will
ever make sense for these companies that don't have 100 front end developers?
00:49:50:12 - 00:49:53:01
Jens
Yeah. I think we need to change some stuff.
00:49:53:03 - 00:49:58:15
Stefan
And what would we change and why?
00:49:58:17 - 00:50:26:18
Jens
If you if you so I think the first question to ask is does federation makes sense without GraphQL.
So in other words, thus federation makes sense without relay. Oof. And and we just talked about
it I think like again relay is awesome. But it also comes as a cost like relay is not super easy to
understand.
00:50:26:21 - 00:51:11:28
Jens
For a lot of people, I think RPC is easier to understand. Like MCP doesn't want GraphQL, it
wants RPC. Yeah. Json, RPC to be more specific. So how can how can it make sense? And
then is or in other words, does federation make sense without relay. And I think the, the, the
value of federation is we built an API with many teams or we create a uniform API interface
across many teams.