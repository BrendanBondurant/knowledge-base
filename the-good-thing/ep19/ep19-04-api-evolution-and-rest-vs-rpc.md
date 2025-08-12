---
title: API Evolution and REST vs RPC
slug: ep19-04-api-evolution-and-rest-vs-rpc
series: The Good Thing
episode: 19
chunk: 4
participants:
  - Stefan
  - Robert Farr
  - Jens
segment: API Patterns and Evolution Strategies
timecode: 00:15:13 – 00:21:20
start_time: 00:15:13
end_time: 00:21:20
speakers:
  - Stefan
  - Robert Farr
  - Jens
topics:
  - Evolution of Robert's thinking on API design
  - Monolithic database pain points and lessons
  - REST vs RPC architectural trade-offs
  - Practical implementation considerations
tags:
  - rest
topic_tags:
  - rest
entities:
  - Robert Farr
  - Stefan Avram
  - Jens Neuse
  - Procore
mentions:
  - API design evolution over time
  - Monolithic database challenges
  - REST vs RPC decision factors
  - Real-world implementation trade-offs
summary: Robert shares his evolving perspective on API design, discussing lessons
  learned from monolithic database pain points and the practical trade-offs between
  REST and RPC architectural patterns.
---

00:15:13:26 - 00:15:19:04
Jens
When you say not yet, do you think it should?
00:15:19:06 - 00:15:49:20
Robert Farr
Well, I think I think every company so, and, and that's because of what the change, like I would
say, what AI is doing right to how we build software, what software we build. I think it's going to
reinforce that need for solid API contracts. And so you're going to have to, you know, the first
consumer, right, that that we start thinking about in the future is probably an agent, right?
00:15:49:20 - 00:16:11:04
Robert Farr
An AI agent rather than, you know, an external developer rather than an internal developer
trying to build a, you know, either a mobile or web application. That's kind of the opposite of
what it is today, right? Like, or at least it has been where, you know, I think first we think about
our internal developers and then you think about your external developers.
00:16:11:04 - 00:16:34:27
Robert Farr
And this is not uncommon, I would say, at many companies, and, you know, some get it, you
know, some do it the other way. Right? Like it's it's baked into the DNA of the company.
Sometimes that starts from the top down. But but I'll, you know, you'll see one of those two
orientations, and I think that's going to pivot.
00:16:35:00 - 00:16:35:10
Robert Farr
Yeah.
00:16:35:16 - 00:16:38:12
Jens
That's that's that's very interesting.
00:16:38:14 - 00:16:39:16
Robert Farr
00:16:39:18 - 00:17:20:20
Jens
Before we dive deeper into the into the ecosystem of AI, like, I, I'm for me, the foundation of AI is
APIs, AI or LLMs without data is just a cool model that can, yeah, can come up with whatever
token you ask it to come up. But yeah, how much can it do? Well, one great example, for
example, is if you go to chatGPT deep research, I think deep research is a prime example for
how the future looks like.
00:17:20:22 - 00:17:50:25
Jens
And if you can have something like deep research and you can give it MCP access to all of Pro
Core APIs, even if that's just internal, it doesn't even have to be public. That can be just for
people inside Pro Core. This can be, in a crazy interesting use case because it would allow
someone like a business person to ask a very complex question.
00:17:50:28 - 00:18:37:25
Jens
And then the deep research model can go on the journey of, working for ten minutes, crunching
data from various sources and creating a report. And then this business person, they just. And,
the coffee break, and now the report is ready and fresh. And I think that that is where, where the
industry is heading. But before we go deeper into, into AI, one thing I'm curious about is so we
can talk a little bit about your API stack, the API stack you're you're building currently, you're
building something with, with WunderGraph, with Cosmo, which brings us here.
00:18:37:29 - 00:19:01:00
Jens
But I would also love to hear your your journey. How how do you how do you think about APIs
and how has your opinion of APIs changed over the years? Like how how did you end up with
the mindset where you are today? And then how did that change over the last couple of years?
00:19:01:03 - 00:19:10:04
Robert Farr
Yeah, that's a good question. I would say,
00:19:10:06 - 00:19:42:06
Robert Farr
You know, I've had I've had several experiences with monolithic databases, both at, at Cerner
and at Procore. And so, you know, for me, it started at with what you see is it's very easy for
your table schema. Right. In a, in a monolithic scenario to become the API, right, to become the
contract. And so that really impressed upon me early the need for proper, you know, API
encapsulation.
00:19:42:09 - 00:20:05:20
Robert Farr
Because otherwise it's very hard to evolve. Right. Like it, it, one trade off you make when you
define contracts or you define APIs is, is you sign up for, you know, passivity and, you know,
thinking about the impact of API change on your customers or the customers or those APIs. And
so there's there's a higher level of responsibility there.
00:20:05:20 - 00:20:30:09
Robert Farr
You're right. You don't you just can't change it, or break it, willy nilly, so to speak, your internal
details. Right. You have a lot of flexibility to refactor that, to evolve it. Much more so, right, than
your, your external API contracts. So that really kind of I would say set, this set up, the kind of
rule system in my mind of like, okay, let's make sure these are important.
00:20:30:09 - 00:20:57:00
Robert Farr
They, they weren't the extra time to try to make sure your, your you're going to do them right or
doing well. They're they're never. All right. There's something I've learned over the years, so that
that kind of frames that, you know, I think other things, you know, we've seen, you know, just,
you know, the advent of, of REST, right, and REST APIs.
00:20:57:00 - 00:21:20:19
Robert Farr
And what's interesting, I watch that evolution. And there's this tension. Right. I would say in , you
know, when you're trying to define contracts, you're trying to find certain patterns or styles, even
in rest. So, you know, hey, those very few things actually adhere to it. Well, right. Or perfectly.
And that's because there, you know, pragmatism comes in.