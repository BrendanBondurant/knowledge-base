---
title: API Governance and Hypermedia Challenges
slug: ep19-05-api-governance-and-hypermedia-challenges
series: The Good Thing
episode: 19
chunk: 5
participants:
- Stefan
- Robert Farr
- Jens
segment: API Governance and Standards
timecode: 00:21:20 – 00:27:21
start_time: 00:21:20
end_time: 00:27:21
speakers:
- Stefan
- Robert Farr
- Jens
topics:
- API governance at enterprise scale
- Challenges with API consistency across teams
- Hypermedia approaches and their limitations
- Developer experience considerations
tags:
- api-governance
- hypermedia
- consistency
- developer-experience
- enterprise-scale
- standards
topic_tags:
- api-governance
- hypermedia
- consistency
- developer-experience
- enterprise-scale
- standards
entities:
- Robert Farr
- Stefan Avram
- Jens Neuse
- Procore
mentions:
- Enterprise API governance challenges
- Hypermedia complexity and adoption barriers
- Cross-team API consistency issues
- Developer experience trade-offs
summary: Deep dive into API governance challenges at enterprise scale, exploring the
  difficulties of maintaining consistency across teams, hypermedia approaches, and
  the impact on developer experience.
---

00:21:20:19 - 00:21:43:13
Robert Farr
But also it's hard, right? It's hard to, consistently, you know, approach some of those standards.
In a, in a way that then also is, you know, is it useful to the consumer. Right. What's the impact
on the consumer of those APIs. And so that's the other friction, I think I, you know, really, you
know, comes to mind, right?
00:21:43:13 - 00:22:12:05
Robert Farr
Is I think about contracts, I'm thinking about like, how do we how do we deal with that kind of
governance problem or the, consistency problem at scale. You know, when you start, it's not like
there's one engineer, right? Or one person that goes and defines the API for everything. And
you see this in other industries anywhere where, like, you know, health care, there's HL7,
standards body and there's an immense amount of hours and people that that are involved in
making those standards.
00:22:12:05 - 00:22:41:11
Robert Farr
And it takes a long time to change them. Right. There's a lot of discussion that goes into it. And
then and then it's not necessarily the easiest thing to write, to go, adhere to consistently. And
even, you know, in health care, you know, we always found just because there was HL7, you
would still find differences between providers of that API, whether that was Cerner or, you know,
epic or one of our, kind of competing, health care solutions.
00:22:41:13 - 00:22:46:23
Robert Farr
The same API. They wouldn't quite behave the same.
00:22:46:25 - 00:22:51:09
Robert Farr
So for,
00:22:51:11 - 00:22:56:07
Stefan
I see you thinking Jens he’s thinking. What's the follow up question there?
00:22:56:09 - 00:22:58:14
Jens
I'm processing.
00:22:58:16 - 00:22:59:22
Robert Farr
Yeah, yeah.
00:22:59:24 - 00:23:02:15
Jens
I need to split the tokens, but.
00:23:02:17 - 00:23:04:00
Robert Farr
00:23:04:02 - 00:23:11:04
Jens
What what what do you think is the is the best API style?
00:23:11:06 - 00:23:20:12
Robert Farr
The best API style?
00:23:20:14 - 00:23:31:24
Robert Farr
Well. And, maybe maybe I don't, What do you mean by style? Are you thinking just in terms of,
like, approach to how you.
00:23:31:26 - 00:23:33:09
Jens
RPC style.
00:23:33:12 - 00:23:35:12
Robert Farr
RPC or Rest? Okay, okay.
00:23:35:13 - 00:23:39:01
Stefan
RESTful query Style?
00:23:39:06 - 00:24:13:25
Robert Farr
Yeah. So to be honest, you know, I find RPC to be probably the simplest, most straightforward.
But it also has, right challenges of bloat and maintenance. At times I think that was something
that, you know, rest, Rest style APIs tried to simplify, right? You know, the hope was you have
resources with a few operations and a lot of things you could do, on the other end.
00:24:13:25 - 00:24:37:05
Robert Farr
So that's kind of two ends of the spectrum. You know, the way I think about it, but I find, like, as
a consumer, RPC is a lot easier to, to reason about. Right. Take this action. I understand what
the you know, here's a response that tells me what it did. And if you think about, you know, what
kind of changes, right.
00:24:37:05 - 00:25:01:15
Robert Farr
What kind of changes do we make to state, you know, your basic Crud operations, they're
they're there, but they're really changing information. But the moment that you start getting into
what I'll say are the kind of the, the logical changes of state, you know, statuses and, you know,
you know, maybe, evolving something from published, you know, from draft to published.
00:25:01:17 - 00:25:22:11
Robert Farr
That's where RPC really kicks in, right? And rest, it starts to get kind of, funky or you'll see
people kind of move away from rest and they'll add these, you know, you know, my resource
slash publish, right? Which is not a RESTful API, at least in terms of Http, but becomes more
RPC like, over time.
00:25:22:11 - 00:25:45:19
Robert Farr
I'm, I'm usually and, you know, you know, think about the consumer of the API. Right. And so
sometimes it's a, you know, right. Like the basic Rest stuff is exactly what they need. And
sometimes you need more of that RPC style of API, because at the end of the day, it's your
consumer that kind of drives the contract you really should be providing.
00:25:45:21 - 00:26:11:17
Robert Farr
If you're not satisfying, you know, kind of what they need, then you're really you're just creating
friction, right? You're creating, friction for them. You're creating adoption friction if you're trying
to, you know, create more value, with the service you're building. And so you've got to be
pragmatic. So I guess at the end of the day, I'll say I favor whatever works, but, but I probably
think RPC is a little simpler.
00:26:11:19 - 00:26:16:19
Stefan
What about you Jens what's your favorite API style?
00:26:16:22 - 00:26:18:21
Robert Farr
00:26:18:24 - 00:26:52:10
Jens
So if we go through all of them, I, I personally think hypermedia is the, the smartest style ever
invented, which nobody really understands. So, you know, when I heard the first time about
agents and, and how they or llms how they could use APIs for me, it was immediately clear
hypermedia was built for agents. And do you know how many people use hypermedia for
agents?
00:26:52:10 - 00:27:21:11
Jens
Exactly. Nobody. Because I think nobody ever understood the power of hypermedia, because,
you know, you you go to the landing page of a thing and it returns a hypermedia answer with,
hypertext that tells you this is a shopping cart. Here are things in the shopping cart. If you want
to go to the checkout, send a post, request to the checkout.