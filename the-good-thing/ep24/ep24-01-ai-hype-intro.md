---
title: AI Hype Introduction and Future Predictions
slug: ep24-01-ai-hype-intro
series: The Good Thing
episode: 24
chunk: 1
participants:
  - Stefan
  - Jens
segment: Episode Introduction and AI Discussion
timecode: 00:00:25:08 – 00:04:05:01
start_time: 00:00:25:08
end_time: 00:04:05:01
speakers:
  - Stefan
  - Jens
topics:
  - Podcast Introduction
  - AI Replacing Developers
  - gRPC for Federation
  - AI Productivity Study
  - Lovable Growth
  - Meta Open Source Shift
tags:
  - ai
  - grpc
  - graphql-federation
  - startup
  - open-source
  - api-design
  - federation
  - go
  - graphql
  - llm
  - rest
  - rust
topic_tags:
  - podcast-intro
  - AI-development
  - developer-productivity
entities:
  - The Good Thing
  - WunderGraph
  - Stefan Avram
  - Jens Neuse
  - Jacob
  - Lovable
  - Meta
  - Crandham
  - GitHub
  - Cursor
mentions:
  - Call of Duty video intro style
  - AI replacing developers
  - prompt engineering
  - Matrix energy provision analogy
  - weekly tech review format
  - Hacker News study
  - 15 million seed funding
  - 200 million Series A
  - 75 million ARR
  - 2 billion valuation
  - China's Deep Seek
summary: Stefan and Jens open episode 24 with playful banter about AI replacing developers
  and the podcast format. They preview the week's tech topics including gRPC for GraphQL
  Federation, an AI productivity study showing developers slowing down 20%, Lovable's
  impressive 200M Series A after 8 months, and Meta potentially moving away from open
  source AI models.
---

00:00:25:08 - 00:00:39:18
Stefan
And we're live. Welcome back, ladies and gentlemen. I always do the same intro I just realized.
Welcome back, ladies and gentlemen, to another episode. I'm going to change that up. If you
guys remember, I used to watch, like, Call of Duty videos growing up. And so I would always be
this guy. He'd be like, yo, yo, yo, it's your boy.
00:00:39:18 - 00:00:41:27
Stefan
I should do that one. Yo, yo, yo, it's your boy.
00:00:42:00 - 00:00:52:15
Jens
down developers.
Stefan. Did you know there's, today we talk about the case study, and it says that, AI, slows
00:00:52:17 - 00:00:53:20
(Mix)
You know, I'm actually kind of.
00:00:53:20 - 00:00:56:11
Jens
Why? Why? That's not a problem for you.
00:00:56:13 - 00:01:00:08
Stefan
Well, let me guess, because I'm not a developer.
00:01:00:10 - 00:01:00:22
(Mix)
Hey, one.
00:01:00:22 - 00:01:09:28
Stefan
Thing I actually built, a little thing over the last week, and I'll share it, but, say what you want. I'm
a prompt engineer. Now. Yes, Dont need to.
00:01:09:28 - 00:01:10:26
(Mix)
But nobody needs.
00:01:10:26 - 00:01:18:08
Stefan
To be a developer anymore, because in a couple of years, it's all going to be gone anyways.
Just going to be people just prompting prompt engineers to the new thing.
00:01:18:10 - 00:01:27:19
Jens
Yeah, we don't need developers anymore. Everything can be generated. Nobody needs to
review it. We can fully trust LLMs. Just throw it in
00:01:27:21 - 00:01:32:17
Stefan
we can just get rid of GitHub too. Like what's the point of GitHub anymore?
00:01:32:24 - 00:01:41:08
Jens
WunderGraph we'll be a one person company and it's just me. I wake up in the morning, I'm
like, okay, let's let's go.
00:01:41:12 - 00:01:48:15
Stefan
AI salespeople just go run. Good morning guys. Three of us stand up with them. And over there.
00:01:48:18 - 00:01:59:28
Jens
And then 100 AI developers and they will know themselves what to build. Actually, they could
they could just fire me. They don't need me. It's just ai all the way.
00:01:59:28 - 00:02:04:05
Stefan
You just. Yeah. You just got to keep them running. And so just make sure they don't get
unplugged.
00:02:04:07 - 00:02:11:17
Jens
AI.
Yeah, it will be matrix again. We will all be just plugged into the system to provide energy to the
00:02:11:20 - 00:02:12:29
(Mix)
Probably.
00:02:13:01 - 00:02:30:00
Stefan
I mean it's what we're going towards. But guys, thanks for joining us. We have a lot of topics
today. Today in our tech review today, it's kind of like a news channel if you think about it. We're
going to be talking about. Yeah, because we're just reporting on like the interesting stuff that
happened over the week.
00:02:30:00 - 00:02:46:17
Stefan
But there's some interesting ones actually on here. Jacob did a great job at picking this topic, so
we'll touch a little bit upon. Why we're bullish on gRPC as the next generation for GraphQL
Federation. This we didn't get to touch last week. So we'll start with that today. Second one I
actually read this study as well.
00:02:46:22 - 00:02:58:10
Stefan
But AI is actually slowing down our workflow. I just noticed Jacob's message. Drop your
questions, comments, or insults in the chat below.
00:02:58:13 - 00:02:59:08
(Mix)
Yeah.
00:02:59:11 - 00:03:03:00
Jens
Starting with insults. It's very important.
00:03:03:02 - 00:03:03:09
(Mix)
Though.
00:03:03:10 - 00:03:29:29
Stefan
I love that one. And then, yeah, I read this, in Hacker News, but it seems that developers are
slowed down by an average of 20%. Using tools like cursor or lovable or things like that. So
we'll touch on that. Speaking of lovable, eight months after their feed, from Crandall, my 15
million, they raise a 200 million series A, they're, at over 75 million ARR only 45 employees.
00:03:30:01 - 00:03:35:09
Stefan
And they're getting closer to that 2 billion valuation. I think they're 1.8. Right. Something like,
00:03:35:12 - 00:03:38:06
Jens
Did Cranham, invest.
00:03:38:08 - 00:03:42:04
Stefan
Cranham led their, seed, 15 million seed.
00:03:42:07 - 00:03:44:13
Jens
We know someone at Cranham.
00:03:44:15 - 00:04:05:01
Stefan
Yeah we do. We do new a couple people at random. And then the last one that we'll touch a
little bit upon, which I'm actually very surprised about, which is meta, may move away from open
source AI models. I don't understand this. I remember in 2003 they said that platform behemoth
will win because it's the open one, but now they seem that they're abandoning that opinion.