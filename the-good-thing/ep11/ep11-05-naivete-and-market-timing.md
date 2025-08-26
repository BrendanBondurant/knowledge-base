---
title: Naivety Benefits and Market Timing Challenges
slug: ep11-05-naivete-and-market-timing
series: The Good Thing
episode: 11
chunk: 5
participants:
  - Stefan
  - Jens
segment: Product Timing and GraphQL Market Evolution
timecode: 00:24:36:08 – 00:30:13:19
start_time: 00:24:36:08
end_time: 00:30:13:19
speakers:
  - Stefan
  - Jens
topics:
  - First-time founder naivety benefits
  - Building right product at wrong time
  - Being 5 years ahead of market
  - GraphQL ecosystem evolution
  - WunderGraph origins and Apollo Summit
  - Market timing challenges
  - MCP explanation
tags:
  - startup
  - mcp
  - ai
  - api-design
  - apollo-graphql
  - federation
  - founder
  - go
  - graphql
  - graphql-federation
  - llm
  - rest
topic_tags:
  - startup
  - mcp
  - graphql
entities:
  - WunderGraph
  - Apollo
  - GraphQL Summit
  - Tyk
  - Eric Wilde
  - INNOQ
  - Stefan Avram
  - Jens Neuse
mentions:
  - GraphQL Summit 2019
  - 5 years ahead of market
  - Apollo conference inspiration
  - MCP model context protocol
  - JSON RPC explanation
summary: Discussion of how first-time founder naivety enables building products, with
  Jens reflecting on building the right thing at the wrong time and being 5 years
  ahead of market. Stefan recounts WunderGraph's origins from Jens attending GraphQL
  Summit 2019, and they explain MCP (Model Context Protocol) as an API wrapper for
  LLMs.
---

00:24:36:08 - 00:25:03:13
Jens
So they just do it. Yeah. It that that's that's a that's a huge advantage. Also I don't know, but in
the beginning we built the wrong thing. We didn't know it was wrong. We just built the wrong
thing because we thought, that's right. We figured it out. But then later on we we figured out that
actually we always built the right thing, but at the wrong time.
00:25:03:16 - 00:25:27:00
Jens
So, I don't know. In the end, this is something that one one of my friends keeps telling me, hey,
Jens, you need to be careful with the products you're building. You're always, like, five years
ahead. And it's a it's such a difficult thing if you if you think you understand the market and then
you I don't know, I, I cannot sit still.
00:25:27:00 - 00:25:52:27
Jens
I always want to make something, something better. You know, I talk to customers and I'm like,
okay, this, this, this should be better. It should be different. But if you do it for a while, you kind of
accept that you have like a long term roadmap, you have a short term roadmap. And you you
kind of need to align and you somehow need to synchronize with the, with the, with the vibe of
the market.
00:25:53:00 - 00:26:09:01
Jens
So you can you can have ideas, about the, about what you, what you want to build and
everything. And, you need to sometimes you need to wait for the market to make the right move,
and, yeah.
00:26:09:01 - 00:26:30:22
Stefan
So I think, yeah, I think it's a great transition. One of the things I really want to talk about today
is like, okay, we got the funding. That's great, but what are we actually using it for? So you can
say all the generic stuff. We're going to hire people. We're going to expand this. But from the
product point of view I want to go into GraphQL like it's interesting and I'll be fully transparent.
00:26:30:22 - 00:26:41:08
Stefan
So we started Jens originally started wundergraph in 2020, and this was after he went to, I think.
Was it Apollo's conference? The original Apollo conference. He went to.
00:26:41:11 - 00:26:45:03
Jens
GraphQL summit in, I think 2019.
00:26:45:05 - 00:27:02:03
Stefan
So you went there and you had this idea of like this universal data layer you were still working
at, Tyk at the time, you really enjoyed it. And GraphQL was hot. Like, it was really hot. I
remember like even being like graduating from college, like this was something that they were
putting to the curriculum. And 2020, you started wundergraph, in 2022
00:27:02:03 - 00:27:22:07
Stefan
We raised the funds. We started working together, I mean, year 2021. But we've gone through
this crazy thing where at one time there were so many GraphQL companies, there were stepset
and there was a delay. There was, the guild, there was all these companies, and they were well-
funded. Fast forward to now, there's really just us and Apollo.
00:27:22:09 - 00:27:41:19
Stefan
But what happened with GraphQL like. And I'm going to play devil's advocate and you I'm going
to play the people on Reddit and Twitter and you tell me what you see because when I see
GraphQL, I actually don't see what they say on Reddit. In Twitter. Oh, GraphQL is dead.
Instead, I see, wow, GraphQL is growing. All these huge companies are using it.
00:27:41:23 - 00:27:56:28
Stefan
They're all going towards Federation. But I want you to play that part. But from a product point
of view, with the funding, where do you see GraphQL? Where do you see this market? And like
where do you think it's going? Especially in the next couple of years withAI.
00:27:57:00 - 00:27:59:21
Stefan
I know a lot to unpack.
00:27:59:23 - 00:28:22:29
Jens
Okay. I don't want to start with GraphQL, by the way. This is not staged. We're just yeah, I, I'm
not prepared. But if we zoom out a little bit and I this morning I had, I had a cool conversation
with, Eric Wilde from I think, you know, or, INNOQ or something. He he's an API expert, like.
00:28:23:02 - 00:28:30:29
Stefan
Eric Wilde from. He works,. Yeah, yeah, yeah. Okay.
00:28:31:00 - 00:28:49:06
Jens
He's like a API catalyst, But he goes into companies and he consults and helps people with API
strategy, governance, everything. Okay. So we had a conversation and it it started with MCP of
course. Yes MCP sure. Model context protocol.
00:28:49:08 - 00:28:55:00
Stefan
real quick, can you explain MCP like for maybe those don't really understand it.
00:28:55:03 - 00:29:09:16
Jens
Yeah. So, I have an API for you. So, so, so that LLMS can talk to APIs. I put an API around the
API so LLM can talk to the API.
00:29:09:18 - 00:29:13:21
Stefan
Okay. Well, problem does that solve. So what does that actually do?
00:29:13:24 - 00:29:46:13
Jens
Yeah, that's that's weird. So we have APIs in the world like REST, GraphQL, whatever.
Somehow people were like, okay, LLM could talk to them, but that would be too simple. So we,
we we we now say let's click create kind of like something that is similar to open API, which talks
over Json RPC, and it defines functions that LLM could call and we call it MCP.
00:29:46:15 - 00:30:13:19
Jens
So it's kind of like okay we we define RPC with Json RPC and we create open API. And now
LLM can talk to the thing and yeah. So so that's MCP. This is where this discussion started
okay. So yeah, we were we were talking about this topic and what we came down to is this kind
of like it's it's interesting.