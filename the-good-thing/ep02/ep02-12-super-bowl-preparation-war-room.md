---
title: Super Bowl Preparation and War Room Setup
slug: ep02-12-super-bowl-preparation-war-room
series: The Good Thing
episode: 2
chunk: 12
segment: Super Bowl Event Preparation
timecode: 00:47:02:28 – 00:51:44:12
start_time: 00:47:02:28
end_time: 00:51:44:12
speakers:
  - Stefan
  - Jens
topics:
  - Super Bowl Preparation
  - War Room Monitoring
  - Cache Warming
  - Performance Reliability
tags:
  - cache-warming
  - observability
  - zero-incidents
  - ai
  - api-design
  - benchmarking
  - composition
  - cosmo
  - database
  - federation
  - go
  - graphql
  - graphql-federation
  - query-planning
  - startup
entities:
  - WunderGraph
  - Super Bowl
  - Cache Warmer
  - Performance Monitoring
  - Customer Support
summary: Stefan and Jens discuss their preparation for a major customer's Super Bowl
  event, including setting up a war room for monitoring and support. They explain
  how the cache warmer feature will help handle traffic spikes and how they'll provide
  real-time support during the event. The conversation covers the importance of being
  prepared for high-traffic events and the value of proactive performance optimization.
---

00:47:02:28 - 00:47:37:18

Jens

So you, we, we, we hope that later on we, we can talk about the, the event and, outcomes and

everything. With permission of the, of the customer and. Yeah, but honestly, I'm not so much

afraid of the event because really, the, I would say the the bulk of the work, it's in the last year,

like, you know, you, you kind of know if your software is working or not and you kind of build this

level of confidence.

00:47:37:18 - 00:48:05:01

Jens

And I would say, like in, in German honesty, in the very early days of, of Cosmo, there were

simply situations where we kind of knew there's queries we cannot really plan. Or even worse,

there are situations where we do not fully understand how federation works. This was like very,

very early days, like over a year ago.

00:48:05:03 - 00:48:37:02

Jens

And over the last year, we, we have, like, specialists working on composition and query

planning, and they have built so much knowledge and so many, I would say, safe gates into, into

our composition and query planning and we, we really have built up confidence. Just to give you

an idea, internally, we have a database of all customer queries, all schemas.

00:48:37:05 - 00:49:07:12

Jens

And whenever we change something like composition or something like that, we have like very

rigorous process where we run through all possible combinations of schemas and queries and

we check are the query plans changing is the behavior changing. And then we verify all of that.

And yeah. You see like reliability, it's a it's a big topic for us, but it can only come from having

enough use cases.

00:49:07:15 - 00:49:56:16

Jens

Unfortunately, there's not yet like a full specification for what federation is. So, the best or the

the closest you can get to a federation specification is to to have as many customers as

possible, take all the use cases and observations and, yeah, I, I would say that's actually I

mentioned earlier there's something it's called Hyrums law and Hyrum's law kind of says that the

specification of of a software, it's, it's not really just the API specifications, but all observable

behaviors from a software are the specification of the software.

00:49:56:16 - 00:50:22:19

Jens

So for example, if you have a software that's super inefficient and it creates a lot of heat on your

CPU, it's possible that someone in Siberia is using your software to heat the room. And if you

now make the room, if you now make the software faster, it means the CPU won't heat up that

much, so they might now freeze.

00:50:22:24 - 00:50:46:08

Jens

So you you didn't change the API, you made it faster. But by making it so much faster, you you

changed one of the outcomes, one of the behaviors of the software. So you need to be careful.

You can't just make something too fast, maybe make it slightly faster or something. So I mean,

this is a ridiculous example, but coming back to Federation.

00:50:46:13 - 00:51:16:25

Jens

Federation is such a complex beast. I would say there's not a single company that knows

federation from, from, or understands it from, from A to Z. And as such, it's very important to

have things like, like benchmarks and audits and collaboration between vendors to to kind of

conclude, what is what is the agreement that the majority of people find in in how federation,

should work.

00:51:16:27 - 00:51:38:29

Jens

And on our end, it means we we have a lot of customers, we have their schemas, we have their

queries. We know what kind of outcome we want when we run the query. So we have all of that

in the in the huge internal database. And every time we change the behavior, we, we check

against that. And that's yeah, that's really helping us to to improve it but not break it.

00:51:38:29 - 00:51:44:12

Jens

And yeah. Now you know a little bit about, our life here. 