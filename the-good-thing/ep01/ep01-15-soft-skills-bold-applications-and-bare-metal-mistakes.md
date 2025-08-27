---
title: Soft Skills Bold Applications and Bare Metal Mistakes
slug: ep01-15-soft-skills-bold-applications-and-bare-metal-mistakes
series: The Good Thing
episode: 1
chunk: 15
participants:
  - Jens
  - Stefan
segment: Career Moves and Build Versus Buy Lessons
timecode: 00:46:53 – 00:49:40
start_time: 00:46:53
end_time: 00:49:40
speakers:
  - Jens
  - Stefan
topics:
  - Soft Skills
  - Bold Career Moves
  - Startup Politics
  - Engineering Credibility
  - Build vs Buy Lessons
  - Meeting Cofounder
tags:
  - graphql
  - ai
  - api-design
  - benchmarking
  - federation
  - founder
  - go
  - graphql-federation
  - startup
topic_tags:
  - graphql
  - api-design
  - federation
  - startup
entities:
  - Jens Neuse
  - Stefan Avram
  - WunderGraph
  - AWS
  - Tonline
  - GraphQL
  - Federation
mentions:
  - soft skills in tech
  - overconfidence in senior hires
  - bare metal infra vs cloud
  - bold career moves
  - politics in engineering promotions
  - build versus buy mindset
summary: Jens shares how his desire to unify APIs and help teams collaborate led him
  deeper into architecture and GraphQL. Stefan reinforces that his boldness in applying
  for jobs above his experience level paid off, thanks in part to soft skills, networking,
  and confidence. They discuss how career progression in engineering often depends
  on more than just technical ability. Jens reflects on his early rejection of AWS
  at Tonline in favor of bare metal infrastructure. This experience shaped his current
  thinking on when to build versus when to buy, especially when helping developers
  avoid the trap of overengineering cool systems.
---


00:46:53:15 - 00:47:10:10

Jens

I like the idea of bringing together APIs and and helping multiple teams collaborate on on. Yeah,

getting APIs and data together. And that's that's how I got into all of this. What we're now doing.

00:47:10:12 - 00:47:30:29

Stefan

I think there's a lot to unpack there, especially for people early in their career, is don't apply for

the job that you're qualified for, apply for the job you want, like you went from being a junior dev

to you're like, definitely very bold. I'm going to apply for the senior role. But then you even saw

an architect role with only like 2 or 3 years of experience and you somehow got it.

00:47:30:29 - 00:47:54:21

Stefan

And I think you gave a really good piece of advice there is that so many developers and I've

seen this like with my friends, they're, they're amazing programmers, but what they really lack

on are the soft skills. And especially in a corporate environment, it is a ladder. And the only way

you can go up the ladder is by going around people being a joy to work with, networking, being

able to kind of present yourself in a way that's beneficial for the company.

00:47:54:23 - 00:48:12:09

Stefan

There's a lot of politics involved. There's a lot of sus choices you make. For example, hiring a

junior developer as a architect. But Jens, and you actually ended up, you know, doing a good

job at that role. And, correct me if I'm wrong, but that's also where you met be our COO and co-

founder, correct?00:48:12:12 - 00:48:14:21

Jens

Yes. So that's actually right.

00:48:14:24 - 00:48:38:04

Stefan

And there's actually a super funny story, which, I want to share is that Jens and I a lot in our

sales calls, we fight with, build versus buy. We get Jens in the past, we get a very smart senior

who thinks he knows everything. That thinks he can build himself a whole Federation test suite.

And I don't blame him because somebody told me this is that it's cool to build Federation tools.

00:48:38:04 - 00:48:59:03

Stefan

It's cool to build high performance gateways. It's cool. And when you work at a big company that

does photos or something that like, is built for consumers, the developers don't care about that.

They want to build cool stuff and Jens, at the time of T online, I think this is so funny, is that

AWS was kind of up and coming and you were like, no AWS.

00:48:59:03 - 00:49:11:15

Stefan

So we're going to do it on bare metal, right? Walk us through that decision and what you learn

from there that that now you use in your build versus buy, use cases when we use developers.

00:49:11:17 - 00:49:40:22

Jens

We, we actually made two absolute terrible decisions. So one one decision was so we we the

historically the company had a data center like for whatever reason, like not not an entire data

center. But I think we had like, 20 or something racks in the data center where we had like very

