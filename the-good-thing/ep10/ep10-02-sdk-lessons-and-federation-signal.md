---
title: SDK Lessons, Federation Signals, and the Leap of Faith
slug: ep10-02-sdk-lessons-and-federation-signal
series: The Good Thing
episode: 10
chunk: 2
participants:
  - Stefan
  - Björn
  - Dustin
  - Jens
segment: Product strategy and market signals
timecode: 00:09:15:19 – 00:16:10:04
start_time: 00:09:15:19
end_time: 00:16:10:04
speakers:
  - Stefan
  - Björn
  - Dustin
  - Jens
topics:
  - First paying customer in three weeks
  - SDK limitations for enterprise
  - Customer feedback and market signals
  - SDK to Cosmo technology transfer
  - GraphQL engine architecture
  - Stefan's sales call documentation
tags:
  - startup
  - graphql-engine
  - ai
  - api-design
  - api-gateway
  - apollo-graphql
  - bff-pattern
  - cosmo
  - cosmo-router
  - database
  - federation
  - go
  - graphql
  - graphql-federation
  - microservices
  - monolith
  - open-source
  - rest
  - rest-apis
topic_tags:
  - graphql
  - federation
  - cosmo
entities:
  - WunderGraph SDK
  - Cosmo
  - GraphQL Go Tools
  - Apollo Federation
  - Netherlands Retreat
mentions:
  - three weeks to first customer
  - hair on fire problem analysis
  - federation capabilities request
  - GraphQL go engine reuse
  - Stefan's notebook documentation
  - boring monolith architecture
summary: Stefan discusses the rapid customer acquisition but notes the SDK wasn't
  solving urgent enterprise problems. Björn explains how customer feedback pointing
  toward federation capabilities became a pivotal market signal. Jens details how
  the existing GraphQL go engine was repurposed for Cosmo, and Stefan's meticulous
  sales call documentation helped identify the federation opportunity during their
  Netherlands retreat.
---

00:09:15:19 - 00:09:31:03
Stefan
Yeah. well said. It allowed us to move fast. One note though, while we go over to Björn in three
weeks, we had our first paying customer three weeks. You remember that from idea to to to
MVP. We had our first paying customer in three weeks. But I'd love to hear your thoughts.
00:09:31:03 - 00:09:47:16
Bjorn
Yeah, we'll, touch to touch right on that. Because the, the challenge for us was, it wasn't a hair
on fire problem. What we built with the SDK. So we didn't solve something that was super
urgent and that, you know, enterprise customers would actually go for, even though individual
developers loved it, it's still in and use the SDK.
00:09:47:20 - 00:10:11:18
Bjorn
Yeah. So it's still got its fans. However, we did have the customer feedback that pointed us in
the right direction. I think Jens can say something more about that, which is kind of one of the
the pivotal moments in our brief history. Brief, but Rich, that's it. It is reasonable to be stubborn
about your ideas, but also to be open to, cues from the market, market signals.
00:10:11:18 - 00:10:44:13
Bjorn
And if a couple of customers tell you. If we love what you do. But if you added, you know,
federation like capabilities, we might actually become a customer. That's a very strong indicator.
So I don't want to tak, speak for you. But one thing I wanted to ask you Dustin, is how much of
what we've actually built as part of the SDK helped us build a better Cosmo right from the start,
because the way I understand it is like, it's like almost a V1 we want it's not Cosmo what we
built with the SDK, but we created a lot of the key technologies that Cosmo nowadays is based
upon.
00:10:44:16 - 00:10:55:29
Bjorn
And we were like, able to find out during that first iteration what worked well and what would be
key requirements going forward, and what we would probably try, differently. So first handing it
over to you and then to Jens.
00:10:56:02 - 00:10:58:01
Stefan
Great question.
00:10:58:04 - 00:11:25:27
Dustin
Of the right direction, I think all the efforts we put into the SDK, I think, we were able to leverage
in the go router to I mean, we essentially also build a, an API gateway in, in the SDK. From an
architectural perspective, as Jens describe, is a developer where it was able to declaratively,
programmatically, fully define API dependencies.
00:11:25:27 - 00:11:50:01
Dustin
That could be so REST or even Prisma. But internally we still have maintain the two graph
which leverage GraphQL as a as a meta data as a as a SQL language to to, to, to to combine all
these different endpoints together. And the router today also leverage this library, which we call
the engine the GraphQL go to.
00:11:50:01 - 00:12:08:27
Dustin
It's and yeah. So, the only thing we had to change, the only thing, was the more or less the
head, the engine is still running. And now we focus focusing on schema federation, on GraphQL
federation, and, yeah.
00:12:09:00 - 00:12:09:19
Stefan
Yeah. Well, said.
00:12:09:20 - 00:12:14:11
Dustin
I think Jens can elaborate more on that.
00:12:14:13 - 00:12:49:09
Jens
Yeah. Thank you. I think one one key factor was that from 2018 on when I started building
GraphQL go tools, it always had in mind to federate data sources, not just Apollo Federation, but
simply federate data sources. And it was written in a in a very open way so that you could, you
could implement, any, any sort of adapter for data sources like REST APIs or WebAssembly or
anything, which in the beginning we had many of those.
00:12:49:12 - 00:13:39:29
Jens
And then as you iterate, you clean up your, your technical debt. But we, we supported so our
SDK, it supported like a subset of Apollo Federation V1. Yeah. So it was kind of possible to do
what people asked. But the packaging wasn't right. And it from the workflow, it wasn't Apollo
Federation like. So what we did with cosmo is we essentially we took the engine, threw away
the ugly car we had built around it, built like, yeah, just built a, like a super sports car around it, a
Bugatti, a Bugatti with an extra spoiler and, yeah, we we made the whole thing open source and
and, it worked pretty well.
00:13:40:01 - 00:14:09:17
Jens
Also, I would say some decisions Dustin made were really smart, where you can actually see
the the experience we have in our team. For example, we don't have microservices. It's the
most boring monolith you can build. And nobody cares about splitting services because we're a
simple team. And the other part is we're not even using GraphQL because you should use
GraphQL when it solves a problem for you.
00:14:09:19 - 00:14:36:15
Jens
Which, for example, when you, when you ask us and we discuss this with, with customers, who
needs GraphQL when you have API sprawl. So you have many clients and many backends, and
you have, like many BFFs in the middle. So that problem we can solve and we’re happy to help
you with, but we ourselves, we have one backend, one frontend, a CLI, and a router.
00:14:36:15 - 00:15:01:20
Jens
And so RPC is a it's a very good framework. To address the question from, from Björn. So you
ask, how did we come up with this pivot. And we, we were quite lucky to have Stefan on the
team, who constantly took notes from all our sales calls. I remember how we how we set
together on, retreat in the Netherlands.
00:15:01:23 - 00:15:33:11
Jens
And we were trying to figure out what is, what is the next step. And Stefan looked through his
notebook and he was like, there's a bunch of people who mentioned GraphQL Federation, and,
that that was like our our, I would say our last straw or the direction we, we took at this point
and, giving back the micro to, to Björn, one thing I'm curious about is so you are the COO, so
you operate the company, but you're you're not working on the product.
00:15:33:13 - 00:16:04:26
Jens
You're not working directly with the customers. You help with procurement. But other than that,
the responsibilities of tech and product and sales and everything, this is with all three of us.
From your perspective, how how did it look at this point that essentially like I and the rest of the
team, but primarily I with my idea, we completely messed it up like and how did it look from,
from your perspective?
00:16:04:26 - 00:16:10:04
Jens
How confident were you at this point that we would actually turn it around?