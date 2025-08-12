---
title: Write Optimization and Tradeoffs
slug: ep26-04-write-optimization-and-tradeoffs
series: The Good Thing
episode: 26
chunk: 4
participants:
  - Stefan
  - Jens
  - Sam Lambert
segment: Write-Heavy Workloads and Consistency Tradeoffs
timecode: 00:15:33:24 – 00:19:02:26
start_time: 00:15:33:24
end_time: 00:19:02:26
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - Write-heavy workloads from AI boom
  - Multiple writer nodes for scaling
  - Consistency vs performance tradeoffs
  - Consumer app data patterns
  - Physics constraints in database systems
  - Pragmatic approach to proven architectures
tags:
  - ai
  - database
  - computer-science
  - ai
entities:
  - AI
  - PlanetScale
mentions:
  - Conversations with AI writing to database
  - Consumer apps and data logging
  - Multiple writer nodes when sharding
  - Serialized isolation patterns
  - Physics constraints like latency and speed of light
  - Database papers from the 1960s
summary: |
  Discussion of how PlanetScale handles write-heavy workloads, particularly from AI applications, and the consistency tradeoffs they make for performance. Sam explains their pragmatic approach rooted in fundamental computer science principles rather than attempting to reinvent database architecture.
---

00:15:33:24 - 00:16:12:21
Jens
Okay. So you're at that scale. Your users, they have like database usage patterns, like for
example, like massive writes or something where you you don't immediately read it. Like for
example, I, I saw another, another podcast you did where you were talking about how how
planet scale benefits from, from the AI boom. And so I, I could assume, for example, that you
have, or you could have a customer where, where people have conversations with an AI, and
then you would write the conversation to the database, and that would be like quite write.
00:16:12:21 - 00:16:15:18
Jens
Heavy, but not so many reads in that scenario.
00:16:15:20 - 00:16:33:25
Sam
We do have that. Yes. And we have we do. We're very good at write works, write bound
workloads. We have a lot of very high scale, write bound workloads, whether or not they're AI or
not. They they store a lot of data. You find that in the consumer space, right? Like most
consumer apps. You know, the only thing that makes them specific to you is the data behind it,
right?
00:16:33:25 - 00:17:13:08
Sam
So they log a lot of things, a lot of transactions, transaction volumes, log lists, or just, you know,
data that they're ingesting from other platforms to do training on. That's all stuff that we're very,
very good at. And, you know, having the consistency model we have allows you for a much
higher writes. We also allow you when you shard to have multiple writer nodes, which means
you can actually scale up writes like one way that people give you that kind of consistency is
they do things like serialized isolation or have, single writer threads that mean you kind of
enqueue everything behind, those that kind of, isolation patterns, meaning it's slower,
00:17:13:08 - 00:17:27:15
Sam
but you get that consistency. We don't have that, consistency we have. We go for the
performance. That's different to durability. Your data is always there. We've never lost a
customer's data that, it's just that kind of trade off in terms of the multi-node consistency issue
there.
00:17:27:16 - 00:17:47:04
Stefan
So, when you kind of explain it like this, it's it sounds pretty easy, like you're like the way you
explain in the beginning, like, anybody could have done this, but why is nobody else doing this
the way you explained it? Like it seems like from first principles, like, why did no one else think
of this? But when you guys came along, you guys did like, why is no one else replicating it or
trying to copy it?
00:17:47:06 - 00:18:12:17
Sam
I think they definitely are. Whether or not they're doing it as well. We didn't invent anything like
we we, I said on Twitter a while back that I don't think theres very much IP in the database
world, like we're all looking at papers that are from the 60s. The rules of computers have really
not changed either. Or physics, like the constraints that we're dealing with in most computer
science problems of physics, latency, the speed of light.
00:18:12:19 - 00:18:36:27
Sam
You know, all of these failure rates, all of these various factors, we just provide we apply a very
pragmatic approach to how we deal with these things. And through experience, we've seen the
ways that fail. A lot of databases have a kind of high hopes of reinventing the wheel when it
comes to these kind of architectures, and it just never really works.
00:18:36:28 - 00:19:02:26
Sam
The history of most large scale database applications end up in the same way, looking the same
way in similar ways. And we've provided that in a very generalized manner, which is itself which
is a really hard task. I mean, operations and good operations, it's not about being kind of fancy
and crazy, like you're just not going to you're not going to kind of crack the nut on, like, okay, I
don't have airplane advances in airplanes.