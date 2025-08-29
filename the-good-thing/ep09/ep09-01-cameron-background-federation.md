---
title: Cameron's Background and Federation Experience
slug: ep09-01-cameron-background-federation
series: The Good Thing
episode: 9
chunk: 1
participants:
  - Jens
  - Cameron
segment: Introduction and guest background
timecode: 00:00:00:00 – 00:04:16:28
start_time: 00:00:00:00
end_time: 00:04:16:28
speakers:
  - Jens
  - Cameron
topics:
  - Cameron’s Background
  - AI Engineering Focus
  - Federation Experience
  - Cosmo Adoption
tags:
  - graphql-federation
  - cosmo
  - microservices
  - ai
  - api-design
  - federation
  - go
  - graphql
  - mcp
  - rest
  - rust
  - startup
  - typescript
topic_tags:
  - graphql-federation
  - cosmo
  - microservices
entities:
  - Cameron
  - WunderGraph
  - Cosmo
  - GraphQL Federation
  - Stefan Avram
  - Jens Neuse
mentions:
  - Stefan traveling to Germany
  - Cameron joining WunderGraph with AI focus
  - TypeScript rewrite discussion
  - 13 federated microservices
  - frontend API dependency
summary: Jens introduces Cameron, a new senior software engineer at WunderGraph who
  previously worked as CISO at a WunderGraph customer. Cameron shares his background
  in AI-powered tooling and his experience using GraphQL Federation with 13 microservices
  at his previous company, discussing how it simplified both frontend and backend
  development.
---
Episode 9
00:00:00:00 - 00:00:48:09
Jens
And we are live and back with the good thing. I'm your host today, Jens. You can already see we
don't have Stefan today because, last minute he figured out that, he's he's actually on an
airplane. I think he's currently about, to board because he is coming over to, to Germany. We
meet, we meet next week, and so, yeah, he's currently traveling.
00:00:48:11 - 00:00:57:09
Jens
But we found a very interesting, co-host for me today. Welcome, Cameron. Hi.
00:00:57:11 - 00:01:00:06
Cameron
Hey Jens. Thanks for having me.
00:01:00:09 - 00:01:27:03
Jens
Cool. Yeah. Cameron Cameron just recently joined WunderGraph. He's a senior software
engineer. He joined us with the focus on on AI. And, we have a couple of topics. Today we want
to talk a little bit about, what's happened with, the TypeScript, rewrite, which seemed to be, not
happening in rust.
00:01:27:06 - 00:01:48:02
Jens
And, yeah, probably the biggest question they have to ask, ask themselves is, Yeah. Why why
did they, had they written it in rust? That would have invited a bunch of questions, but no. Okay.
So that's one topic we talk about. I'm curious about your your opinion. We haven't spoken about
that yet. And then let me see.
00:01:48:04 - 00:02:21:13
Jens
I have this this, list. So other topics, we want to talk about vibe coding or, in general, like coding
with agents. Very interesting topic. We want to talk about MCP. I'm very interested in the topic. I
think, Cameron knows a little bit more about it. Yeah. And first of all, we would like to, to get to
know a little bit about you, how you joined, WunderGraph what you did prior to to WunderGraph.
00:02:21:13 - 00:02:25:20
Jens
So, yeah. Maybe give us a little bit of an intro.
00:02:25:23 - 00:02:51:00
Cameron
For sure. So I've been a software engineer for the last, so I'm ten years working specifically with
startups to help build artificial intelligence powered tooling. I have also worked with different
organizations to empower them to do cool things with their data. Right before joining
WunderGraph, I was the chief information security officer, actually at a customer of
WunderGraph.
00:02:51:02 - 00:03:03:27
Cameron
And, you know, I really enjoyed working with the team. And when that ended, I decided that it
would be awesome to come work with the WunderGraph team. So here I am.
00:03:03:27 - 00:03:11:07
Jens
Great, And at the company were you you worked before, you were using GraphQL Federation?
00:03:11:10 - 00:03:29:25
Cameron
We were. Yes, we had 13 different microservices, that were all federated together through
Cosmo. And our entire front end leveraged that API. We didn't have any kind of other APIs that
we used. So everything was done through GraphQL Federation.
00:03:29:28 - 00:03:42:02
Jens
Okay. And like, in general, what what's your what's your take? What's your opinion on on
GraphQL Federation from from a user slash consumer point of view?
00:03:42:04 - 00:04:16:28
Cameron
Yeah. I think it makes things really simple for both the frontend engineers and also for backend
engineers. I think it's something that empowers the engineer to focus on the product and the
focus on building cool tools, as opposed to having to worry about how to, you know, stitch
together data, how to, you know, I need to get one field that say, like the orders or billing service
has on to the user that comes from the account service, so that the front end doesn't have to
make 100 API calls.