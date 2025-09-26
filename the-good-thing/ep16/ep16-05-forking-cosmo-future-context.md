---
type: podcast-chunk
title: Forking Cosmo Challenges - Future Context and Business Complexity
slug: ep16-05-forking-cosmo-future-context
series: The Good Thing
episode: 16
chunk: 5
segment: Business Forking Strategy Analysis
timecode: 00:21:10 – 00:26:16
start_time: 00:21:10
end_time: 00:26:16
speakers:
  - Stefan
  - Jens
topics:
  - Code Forking
  - Business Strategy
  - Open Source Maintenance
  - Competitive Differentiation
tags:
  - open-source
  - ai
  - composition
  - cosmo
  - cosmo-router
  - go
  - graphql
  - startup
entities:
  - Cosmo
  - GraphQL Go Tools
summary: Jens transitions from discussing PR maintenance to the central question of
  business competition through code forking. Drawing on seven years of maintaining
  GraphQL Go Tools, he sets up a framework for analyzing what it takes to successfully
  clone their business beyond just copying code, introducing the concept that building
  a successful business requires covering multiple categories beyond just the technical
  implementation.
---

00:21:10:15 - 00:21:45:00
Jens
And maybe you didn't do that in your PR and now we're in the situation where you want this PR
merged and we're thinking, actually it's not really our priority. We also think it's just 60% right?
There needs to be like work on it. But even just spending time helping you to get the PR right
means we're now spending time and like frankelly, just said in the in the chat, yeah, it's one of
the most nuanced and challenging responsibilities to maintainer has.
00:21:45:00 - 00:22:13:01
Jens
Truly. Absolutely. And the point is, I, forgive my German for for saying these things in such a
direct way, but, it is it is hard to maintain software, especially open source, if you do this over
many years, like I'm now maintaining open source from like, open source. But I have one
project, the engine of Cosmo, the Cosmo router.
00:22:13:01 - 00:22:36:01
Jens
It's called GraphQL Go Tools, and I'm now one of the maintainers. I created this in 2018. So you
can you can look at your calendar. That's more than seven years now. So we're maintaining that
over such a long period of time. And, I'm, I'm more and more in a passive role in maintaining
that. But over the years I have learned a lot about maintaining open source.
00:22:36:01 - 00:23:14:14
Jens
And, yeah, in, in, in many ways it is complicated. It is hard. But Stefan, today we we want to talk
a little bit about what would happen if someone stole our code. Well, it's not exactly stealing
because it's open source. So what if someone took our codes and cloned our business? And I
was thinking about how can we approach this topic, and, I, I yeah, a little bit about that.
00:23:14:16 - 00:23:42:21
Jens
And I think we can, we can look a little bit into what are the different aspects of, of topics you
have to cover. And then we go through them like, like one by one. So if you would build so let's
say you could just okay you can do the let's say you copy our Cosmo code if what other aspects
if we're thinking in categories, what other categories do we have to cover to build a successful
business.
00:23:42:21 - 00:23:46:20
Jens
So so what other things need to be there?
00:23:46:23 - 00:23:58:20
Stefan
Are you talking more general or just like more technical? Like so for example, like with the
technical, they would have to understand composition for the general, they would have to have
like brand awareness or are we talking about both?
00:23:58:23 - 00:24:24:03
Jens
Yeah. A bit of both. So if we stay high level so the first thing or let's just build some categories.
So I would say one, one big category is engineering. We can we can split it a little bit. We can
also say you have to do like maintenance and development on the, on on Cosmo, but also
platform engineering because you need to to run our cloud.
00:24:24:06 - 00:24:28:04
Jens
What other categories can you think of?
00:24:28:06 - 00:24:36:25
Stefan
I would say branding. So like customer success, customer use cases that you have just those
from around customers and a brand around wundergraph.
00:24:36:25 - 00:24:55:13
Jens
The brand is a good topic. Because by copying the code, you are not copying the brand. So you
have to build a brand. What about other topics? Go to market sales.
00:24:55:15 - 00:25:00:28
Stefan
Domain expertise. Technical ability. What else?
00:25:01:00 - 00:25:02:18
Jens
Hiring.
00:25:02:21 - 00:25:18:16
Stefan
Hiring, procurement. You'd have to learn procurement you have to learn sales. You would have
to learn how to operate a company. Oh, security. Like, Cosmo is, soc2. Like, type two. So you
have to do compliance, security.
00:25:18:16 - 00:25:45:03
Jens
So, so you need to build the, the the processes to be compliant, right? Yes. So we have to build
a framework, okay. That, that that can take up a significant amount of time. But okay. If we dive
a little bit into this topic. So I would say the the first problem you run into is so let's say you copy
the code you want to you'll want to run it.
00:25:45:05 - 00:26:16:06
Jens
The first problem is you don't have the expertise. Why we build things. You can see what we
have built. You can see like a snapshot, like, okay, here is Cosmo. You don't know why we have
build things this way, and you don't know what we had in mind for the future. You just have a
snapshot and so the moment you kind of fork it or whatever, then you, you kind of have the
snapshot.