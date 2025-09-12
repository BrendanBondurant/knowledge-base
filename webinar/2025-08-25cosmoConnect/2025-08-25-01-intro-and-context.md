---
type: webinar-chunk
title: Intro and GraphQL Federation Context
slug: 2025-08-25-01-intro-and-context
series: WunderGraph Webinars
date: 2025-08-25
speakers:
  - Jens Neuse
  - Stefan Avram
  - Demo Engineer
episode: null
chunk: 1
segment: Intro and Context
timecode: 00:04:01 – 00:08:58
start_time: 00:04:01
end_time: 00:08:58
topics:
  - GraphQL Federation
  - Webinar Intro
  - Federation Pain Points
tags:
  - graphql
  - federation
  - webinar-intro
entities:
  - WunderGraph
  - Cosmo Connect
  - Apollo Federation
  - GraphQL Federation
summary: |
  The webinar opens with introductions and an outline of the session’s goals. Jens and Stefan frame 
  the motivation behind Cosmo Connect, emphasizing the complexity of current GraphQL Federation 
  approaches and the operational challenges teams face when adopting Apollo Federation. They 
  highlight the shift toward a schema-first model and the need to simplify subgraph development. 
  The team previews a live demo showing how Cosmo Connect and plugins streamline routing, batching, 
  and deployment while reducing GraphQL-specific overhead.
faqs: []
canonical_url: https://your-site/webinars/cosmo-connect-aug25
---

00:04:01:14 - 00:04:32:21
Jens
should go ahead and just start. Okay. Yeah. It's, it's great to do a webinar again. I think it's it's
been a very long time. We we did webinars. I think the last time when we had, the Wunder
Graph SDK.
00:04:32:22 - 00:05:00:07
Jens
That was a time where just, Dustin and I actually were at, the company from the group here. We
didn't have Jacob. We didn't have Jesse and Ludwig. Since then, a lot of things have changed.
We have built, Cosmo. And today we want to talk about, Cosmo Connect. That is like the, the
next piece of the of the puzzle, of the puzzle that we're trying to put together, and,
00:05:00:09 - 00:05:23:00
Jens
Yeah, it's, it's a pleasure to be your host today. My name is. Jens. I'm, the CEO at WunderGraph
and mostly responsible for, product. I'm here joined today by, Dustin Ludwig and Jesse. Dustin,
our CTO. Welcome to the show.
00:05:23:02 - 00:05:25:03
Dustin
Hi. Welcome. Yeah.
00:05:25:05 - 00:05:28:04
Jens
What what's your role in the in the project?
00:05:28:06 - 00:05:45:15
Dustin
I was, I was in charge of of the architecture and also the the project lead. So, I will also be
responsible later to show you a full demonstration of the development flow of how to develop,
Cosmo plugin in in real world. Yeah, that's my part.
00:05:45:17 - 00:05:52:09
Jens
Awesome. Then we have, Jesse from the UK. Hi, Jesse.
00:05:52:11 - 00:05:55:16
Jesse
I'm from Canada. Don't, don't call me from the UK.
00:05:55:18 - 00:05:57:02
Jens
Okay, but you live in the UK.
00:05:57:03 - 00:06:13:05
Jesse
I do. And I worked on a lot of this stuff that you'll find after the demo. Which is with regard to
how this is going to work with the Cosmo Cloud platform, as well as a bit in the early stages of
how this actually really works at a low level with the router and engine.
00:06:13:07 - 00:06:23:21
Jens
Awesome. And, finally we have Ludwig from Berlin. Hi, Ludwig. Hi Jens. What's your role in the
project?
00:06:23:23 - 00:06:47:05
Ludwig
I've been working on on on the engine part. So the part, converts GraphQL requests into gRPC
requests and performs a communication with the new, subgraphs and, in the protocol, and then
converting the responses back to GraphQL responses.
00:06:47:07 - 00:07:16:24
Jens
Okay. Perfect. Great. Yeah. So that that's us then. I want to, welcome everybody to the to the
webinar. Our existing customers, maybe, someone who's, who's, new to the show and,
interested in what Wunder Graph doing. And also, the people from Apollo who signed up with a
fake account. So welcome, everybody.
00:07:17:01 - 00:07:28:10
Jens
To our webinar today. Let me quickly share. We have a little deck, and then we go into the
demo. So.
00:07:28:12 - 00:07:30:04
Jens
Can you properly see this?
00:07:30:06 - 00:07:34:06
Dustin
That was quite funny. Let's see.
00:07:34:08 - 00:07:42:00
Jens
Okay. Do you properly see my screen or what am I sharing? Because I don't see what I'm
sharing its working.
00:07:42:01 - 00:07:43:00
Jesse
Yep.
00:07:43:02 - 00:08:08:14
Jens
Okay, cool. Okay, so that's us. Quick agenda. I want to talk a little bit about, the problem we're
solving with Cosmo Connect. Why? We have actually build it. How does it work? And then, most
time we we actually want to, want to spend in a live demo, show you end to end how everything
works.
00:08:08:16 - 00:08:29:22
Jens
We will have that, with Dustin and, yeah. Then we have time for Q&A. Again, we have Jesse
and Ludwig here. The people who worked hands on on everything. So you can go, super
technical. Any questions? You have, just, pop them up into the into this Q&A thing, and then,
yeah, we will handle it along the way.
00:08:29:22 - 00:08:58:11
Jens
Or maybe later. Cool. All right. So, first of all, it's it's possible that we have some people here
who are not 1,000%, familiar with, GraphQL or Federation. So. So real quick. This webinar, it's
it's kind of targeted towards, the people who, who have at least some familiarity with,
Federation, but on, on a high level.
