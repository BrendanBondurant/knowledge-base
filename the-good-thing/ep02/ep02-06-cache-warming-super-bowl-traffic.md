---
type: podcast-chunk
title: Cache Warming and Super Bowl Traffic Spikes
slug: ep02-06-cache-warming-super-bowl-traffic
series: The Good Thing
episode: 2
chunk: 6
segment: Technical Deep Dive on Cache Warming
timecode: 00:20:13:15 – 00:25:15:13
start_time: 00:20:13:15
end_time: 00:25:15:13
speakers:
  - Stefan
  - Jens
topics:
  - Cache Warming
  - Super Bowl Traffic
  - Query Planning
  - Federation Complexity
tags:
  - cache-warming
  - federation
  - query-planning
  - ai
  - benchmarking
  - composition
  - cosmo-router
  - go
  - graphql
  - graphql-federation
  - microservices
  - startup
  - composition-algorithms
  - persisted-operations
entities:
  - WunderGraph
  - Super Bowl
  - GraphQL Federation
  - Query Planning Cache
  - CDN
summary: 'Stefan and Jens dive deep into a new cache warming feature they built for
  a major customer preparing for a Super Bowl commercial. Jens explains the technical
  challenge: when traffic spikes occur, new routers start with empty caches, causing
  10-second query planning delays. Their solution analyzes 30 days of analytics data
  to pre-compute query plans and warm the cache before routers go live.'
---

00:20:13:15 - 00:20:23:00

Stefan

And we also want to talk a little bit about those preparations. But talk to me a little bit about the

pre warming cache. What exactly is it and why did we build it.

00:20:23:03 - 00:20:25:18

Jens

I can say the event right.

00:20:25:20 - 00:20:34:17

Stefan

Yeah you could say the event but you cannot under any circumstances mention the name of the

customer. Yeah please please we're live and don't do that.

00:20:34:19 - 00:20:56:20

Jens

So imagine you're a company and it uses federation. And you, you run an ad on the Super

Bowl. So you might get a little spike in the traffic, which means I don't know much about Super

Bowl. I guess it's it's kind of big. I don't know how big, but okay, so let's say I'm, I'm.

00:20:56:20 - 00:21:00:09

Stefan

Clipping that, by the way. And for our American audience, I love it.

00:21:00:11 - 00:21:25:10

Jens

So let's say you you you get a little a little spike in your traffic. That means you need to to scale

up your routers. Okay. Let's say you quickly scale up routers to satisfy the demand. What

happens if the querry hits a router and it takes 10s to plan the query.

00:21:25:13 - 00:21:29:18

Stefan

So non-technical question for the non-technical folks. Since this is on LinkedIn.

00:21:29:18 - 00:21:30:29

Jens

Like you.

00:21:31:01 - 00:21:41:02

Stefan

Basically yes. What is what do you mean by like a query. Like what what what's happening. Like

they hit this website and they they send a request in the query in the GraphQL query. Can you

explain that a little bit?

00:21:41:04 - 00:22:07:07

Jens

Okay. So you click on the ad, you go to a website. The website wants to show you some content

okay. This some content. It doesn't come from a single service. It comes from multiple

microservices. And these microservices in our federation land, we call them subgraphs. And we

have something that, it's called federate, Federation. We have something.

00:22:07:07 - 00:22:39:21

Jens

It's called composition. Composition is an algorithm that takes the descriptions of microservices,

meshes them together and creates what we call the super graph, which is a description that

describes how you could get data with the query language called GraphQL from all your

microservices. So instead of the website sending 100 requests to all these microservices, it's

sending a single request to something we call the router, which routes the query to the

subgraph.

00:22:39:24 - 00:23:04:26

Jens

So it sends this query to the router. The router then figures out how to load the data from all the

subgraphs, and then it it, makes a bunch of requests to the subgraphs fetches the data and

gives you the response. This is cool for the frontend engineers because they don't need to know

about 100 microservices. They just know about, the description of this, super graph.

00:23:04:28 - 00:23:35:26

Jens

The problem is, when you send this query the first time a simple query, it takes nanoseconds to

figure out how to get the data because we make one single fetch. But maybe you have like 100

microservice and your schema is a little bit more complex. There can be like abstract types and,

variations of complexity. And it can take a couple of seconds to figure out how to get you the

data for the query.

00:23:35:27 - 00:23:59:20

Jens

Now, a typical website doesn't have one single query. It can actually have 100, 500 a thousand

queries. So we have customers with up to 1000, queries in production or even more so that

means you you get a lot of traffic. You spin up new routers to handle the traffic because you

have autoscaling and all these cool things.

00:23:59:22 - 00:24:20:00

Jens

And now you have this router, and it doesn't know about this query. And it, it needs to plan this

query. So there's a mechanism to speed this up because you definitely don't want to create a

query plan for the same query twice. That would be very expensive. I mean it takes a couple

seconds. But as time.

00:24:20:03 - 00:24:44:26

Jens

So we have something we call it a query plan cache. So we get the query. We have a very

complicated process to create a hash for the query. And this hash it's our, our key in in in the

map map from this hash to query plan. Then we generate the query plan. It can take like worst

case we have one scenario where it takes 10s.

00:24:44:29 - 00:25:15:13

Jens

And yeah. Then we store this and the next time the request hits this router it comes from the

cache. So we we save 10s. Now there's a little problem. Let's say you get this spike in traffic,

and you start the router. That means the cache is empty. So in reality, you're scaling up your

infrastructure and then this new router, it gets hammered with requests and it takes more than

10s to plan this query. 