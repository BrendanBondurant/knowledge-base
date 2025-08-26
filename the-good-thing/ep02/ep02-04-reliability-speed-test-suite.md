---
title: Reliability vs Speed and Test Suite Optimization
slug: ep02-04-reliability-speed-test-suite
series: The Good Thing
episode: 2
chunk: 4
participants:
  - Stefan
  - Jens
segment: Engineering Reliability and Testing
timecode: 00:12:34:02 – 00:16:37:24
start_time: 00:12:34:02
end_time: 00:16:37:24
speakers:
  - Stefan
  - Jens
topics:
  - Reliability vs speed tradeoffs
  - Test suite optimization
  - End-to-end testing improvements
  - Engineering hiring priorities
  - Go vs full-stack roles
tags:
  - go
  - typescript
  - query-planning
  - cosmo-router
  - ai
  - api-design
  - api-gateway
  - benchmarking
  - composition
  - cosmo
  - database
  - postgres
  - rest
  - startup
  - telemetry
topic_tags:
  - go
  - typescript
  - cosmo-router
entities:
  - WunderGraph
  - Go programming language
  - Node.js
  - TypeScript
  - React
  - PostgreSQL
  - Redis
mentions:
  - test suite performance
  - end-to-end testing
  - router architecture
  - query planning engine
  - gateway functionality
summary: 'Jens discusses the balance between speed and reliability in engineering,
  emphasizing how WunderGraph invests heavily in test suite optimization. He explains
  their approach to hiring engineers, focusing on two main tracks: Go engineers for
  router and query planning, and full-stack engineers for Cosmo. The conversation
  covers the importance of maintaining both fast development cycles and high reliability
  for customers.'
---

00:12:34:02 - 00:12:58:07

Jens

We try to slice it in small portions. Release fast. And and also another big topic, reliability

because you cannot be fast if you're not reliable. One of our biggest toppings is you can, for

example, take a look at our our test suite. It's it's growing so fast. And then just recently we, we

heavily invested into making our tests, much faster.

00:12:58:09 - 00:13:14:07

Jens

And we have an end to end test suite. And for example, one one thing we had like, testing a

cycle of two minutes to run a test, not so bad, but for us, it was too slow. We've now cut it down

to 10s to run our complete end to end test suite. And it's it's just ever growing.

00:13:14:07 - 00:13:49:01

Jens

Because for us, on the one hand side, we want to move like super fast. But with so many

customers, who who rely on the, the correctness of our solution, it's just it's paramount that we

that we really focus on, on releasing something that that absolutely works. And, yeah. So there's

a, there's a thin line between speed and, and, and reliability and, yeah, I think at this point in

time, we're, we're, we're walking, we're walking right in the middle of the street.

00:13:49:04 - 00:14:07:26

Stefan

I would agree. And a quick point there. Jens. So what do you see in the next couple of months.

What key hires are we looking for. So I understand on the marketing side we're looking for a

vice president of marketing of marketing. But on the engineering side, what are we looking for?

What roles and how can people apply and come join this amazing company?

00:14:07:28 - 00:14:34:00

Jens

Yeah, it's it's actually pretty simple. If you look at our code base, we have Cosmo, cosmos is full

stack, Node.js, TypeScript, in the front end we have, react in the backend, Node.js like Postgres

database, Redis, these standard boring things. And then on the, on the router side, our route is

written and go and our query planning engine and everything around that.

00:14:34:00 - 00:14:55:28

Jens

It's also written and go. So there's two very simple opportunities. You can come in as an

engineer focusing on go, or you can be a full stack engineer. Go. Engineer means you you build

your router, you work on things like like telemetry. You can work on the query planner. That's like

kind of like we have two disciplines.

00:14:56:01 - 00:15:22:01

Jens

We we somehow we're mentally split the router into two parts. One part is, more like a gateway.

And the second part is what we call the engine, which actually is the second repository. And in

the engine it's about query planning and execution. And that's kind of algorithmic, like data

structures, graph traversal, AST rewrites, all these kind of things.

00:15:22:03 - 00:15:48:21

Jens

I very much like it. It's it's interesting stuff. And then you have the, the gateway side telemetry

analytics metrics, like all things, gateway, what you would expect from, from an API gateway.

Yeah. And then in Cosmo, Cosmo is the brain of the whole thing. It understands, like, feature

flags and your graphs and composition and everything that that belongs there.

00:15:48:24 - 00:16:14:12

Jens

And, yeah, you have a, a mishmash of some functionality in the backend, then some React and

Tailwind and, in the front end. We want to show the functionality. We built, diagrams to expose,

the metrics and everything. So these are the main opportunities, I would say. And then inside

these two categories, you can also have like two focus points.

00:16:14:12 - 00:16:37:24

Jens

So you can have a focus point. Like you go very deep on the product and or you go a little bit

less on the product side and you go more customer facing because there's always like kind of

like we, we have, we have a long term vision where we want to drive the product and we have

like, like short term goals where we want to enable customers. 