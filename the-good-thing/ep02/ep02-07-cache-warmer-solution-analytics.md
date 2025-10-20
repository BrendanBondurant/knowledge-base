---
type: podcast-chunk
title: Cache Warmer Solution and Analytics Implementation
slug: ep02-07-cache-warmer-solution-analytics
series: The Good Thing
episode: 2
chunk: 7
segment: Cache Warming Implementation
timecode: 00:25:15 – 00:29:35
start_time: 00:25:15
end_time: 00:29:35
speakers:
  - Stefan
  - Jens
topics:
  - Cache Warmer Implementation
  - Analytics Data
  - Query Plan Pre-Computation
  - CDN Integration
tags:
  - cache-warming
  - query-planning
  - cdn
  - ai
  - benchmarking
  - composition
  - cosmo-router
  - federation
  - go
  - graphql
  - graphql-federation
  - startup
  - persisted-operations
entities:
  - WunderGraph
  - GraphQL Federation
  - CDN
  - Analytics Data
  - Query Planning Cache
summary: Jens explains their cache warmer solution that analyzes 30 days of analytics
  data to identify the most expensive queries and pre-compute their query plans. The
  system stores this data on a CDN and loads it when routers start up, ensuring they're
  immediately capable of serving queries without delays. He discusses the limitations
  of federation complexity and how this solution addresses the fundamental challenge
  of query planning performance.
---

00:25:15:16 - 00:25:41:09

Jens

This means the customer has to wait 10s. So they, they after clicking this ad, it costs you so

much money, it you might not like the product because it's so slow. Which means before we

actually take the router live, we should warm up the cache. So we should somehow have a

mechanism to fill the cache without the customer waiting for the request to come to the router.

00:25:41:09 - 00:26:09:12

Jens

So how can we do it? We built something for this. It's called cache warmer. And what we do is

every day we look into the, the analytics data of the last 30 days, and we calculate a top end list

of queries of how long it took them. It took the router to plan. So at the top of the list there will be

the query with the 10s.

00:26:09:12 - 00:26:35:08

Jens

And then there's a query with nine seconds. And then there's a whole bunch of queries with like

maybe 50 milliseconds or something. And then does queries in the nanoseconds. Okay. So you

create this list, we put it on a CDN. And now what we do is when the router starts up, we load

this list from the CDN, we precompute the query plans, we put them into the cache.

00:26:35:11 - 00:27:04:28

Jens

And then we take the router live, which means it takes a little bit longer until we we can get this

router live. But at the same time, the router is immediately capable of serving queries from the

query planning cache. So all we do is execute. So there is no additional latency. And you might

be thinking, okay, sounds very smart, cool solution, but why the heck does it take 10s to plan?

00:27:05:01 - 00:27:58:26

Jens

And, the the real reality is you can create like your, your, your subgraph or your super graph

composition in any possible level of complexity. And it's, it's a simple function of, of mathematics

that, if you have a very small query and a small schema, it takes nanoseconds. And as you as

you grow over time and you create like crazy complex queries, it can take a few seconds and, it

just, it just, I would say, there was the company who initially started to create, GraphQL

Federation, and they added a bunch of directives that do very cool things, like, provides

directives and external directives.

00:27:58:28 - 00:28:31:18

Jens

And there's also very cool concepts like interface objects. And I'm not even able to explain them

in detail. And all these directives together. Someone has invented them and at the time where

they invented them, the they thought it solves the problem. It solves a problem. Like, not not,

diminishing that, but as you scale your graph, you can run into situations where it's very, very

hard for your query planner to figure out how can I load this particular field?

00:28:31:20 - 00:28:53:09

Jens

Because it might be in one graph, it might be in another graph. But actually here's an abstract

type and it could be in 20 graphs. And so you have to compute every possible way this field

could be loaded. And the unfortunate reality is this computation. It's a CPU bound task. We we

cannot just like speed it up in some magical way.

00:28:53:09 - 00:29:21:09

Jens

We need to compute that. And then this. Yeah, this is a limitation of of federation. And the

solution to this problem is if you know ahead of time that you have, very complex query on your

landing page, then you should have something like, like a cache warmer. And we also have a

process, with persistent operations where, when you deploy your front end application, you can

actually register all operations.

00:29:21:09 - 00:29:35:13

Jens

So you can tell our backend, hey, I'm, I'm building an app and it has this query. It needs to be

warmed up. So you can you can tell us ahead of time and then, you will never have a, a

customer waiting for that query.

00:29:35:15 - 00:30:01:03

Stefan

First of all, I think that explanation was absolutely brilliant. And one of the coolest things that I

absolutely love about, you know, working with such technical folks like yourself and building this

company is that we get to see deep into consumer facing applications, and we get to see what

actually happens behind the scenes. And from let let's abstract a little bit away from the tech,

from the business side. 