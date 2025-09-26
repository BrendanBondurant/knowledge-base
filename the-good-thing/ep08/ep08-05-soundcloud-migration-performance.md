---
type: podcast-chunk
title: SoundCloud Migration Performance and Architecture Benefits
slug: ep08-05-soundcloud-migration-performance
series: The Good Thing
episode: 8
chunk: 5
segment: Technical details of SoundCloud's migration and performance gains
timecode: 00:36:18:11 – 00:42:02:16
start_time: 00:36:18:11
end_time: 00:42:02:16
speakers:
  - Stefan
  - Jens
topics:
  - Node.js to Go Migration
  - Performance Gains
  - Cost Reduction
  - Query Planning Improvements
tags:
  - federation
  - graphql-federation
  - ai
  - benchmarking
  - cache-warming
  - cosmo
  - cosmo-router
  - database
  - go
  - graphql
  - kubernetes
  - query-planning
  - startup
  - query-optimization
entities:
  - SoundCloud
  - Node.js
  - Golang
  - Kubernetes
  - AWS Fargate
  - Cosmo
  - Stefan Avram
  - Jens Neuse
summary: |
  Technical deep-dive into SoundCloud's migration from Node.js to Golang-based routing, achieving 86% infrastructure cost reduction and 45% latency improvement. Jens explains the architectural advantages of multi-threaded processing, linear CPU scaling, and the collaborative analytics bridge built to support migration from Node.js gateways to Cosmo.
---

00:36:18:11 - 00:36:39:25
Stefan
But this was a really exciting use case that we had with SoundCloud. Also, the graphic is my
favorite, but basically the Tldr is they cut the, infrastructure cost by 86% and when we estimated
it with them, this was about $265,000 in annual savings on AWS Fargate. And then with Cosmos
and Cosmos Studio, they were able to increase or improve the query latency by 45%.
00:36:39:27 - 00:36:56:07
Stefan
So there was performance improvements all across the board. Do you have any thoughts on
that? What was what like you worked very closely with the tech side. I worked mostly on the
procurement side, but tell us a little bit on the insides of like what we did with SoundCloud, why
it was so exciting as well as I mean, the partnership with them was just fantastic.
00:36:56:10 - 00:37:46:09
Jens
Yeah. So first of all, the the engineering team of SoundCloud is really smart and it's it's a lot of
fun working together with them. They, they have a lot of scale. And for, for someone like us
creating a router and this whole infrastructure, it's always super useful to have very tech savvy
people on on the other side of the table because they bring the scale, they bring the use cases
and, the operational complexity, and we bring the, the, the tech, we bring the solution, and
together we get insights into, okay, well, what happens if you throw billions of requests at
Cosmo router?
00:37:46:12 - 00:38:22:11
Jens
What are the pitfalls? What what can go wrong and how can we improve the product. So we
always love these kind of relationships because they are definitely a power user. And they they
help us to to make it better. And then at the same time, so they, migrated from a Node.js based
gateway and as we all might know, Node.js being single threaded and just by the nature of the
architecture has some limitations in terms of how it can handle, throughput and, and other
aspects.
00:38:22:14 - 00:38:55:28
Jens
And we know that, quite a lot of people in the market are still on Node.js based, GraphQL
federation gateways. So, what you can expect by migrating to, a Golang based router with
query planned caches and many other improvements, it's, first of all, you get a lot more bang for
the buck. So we get more throughput, out of a single, out of a single instance.
00:38:56:01 - 00:39:38:01
Jens
Deployments are much easier because our router is, it's working multi multi-threaded. So it's it's,
it linearly scales with the number of CPUs. So, we, we did some, some, benchmarking with, with
customers where we found that, if you, doubled the number of CPUs, you double the, the
amount of throughput you get. And so that means you don't have to deploy, hundreds of single
CPU pods on your Kubernetes, but you can actually deploy instances with 4 or 8 CPUs.
00:39:38:01 - 00:40:13:24
Jens
So it's, it's, less complex to handle. And then the architecture is just faster and more efficient.
So, so that means we get more requests per, per watt per per per power. So that means overall
you can deploy much less instances in case of SoundCloud, 86% savings. And then on top of
that, because the component, the router is more efficient.
00:40:13:26 - 00:40:56:02
Jens
We also, decrease latency. So the single request, we're serving it faster. And now SoundClouds
bottleneck is the subgraph. So the service behind the router. And and that's something we see
quite often. We had another customer who did a POC. And as part of the POC, they they did
heavy benchmarking. And if you set up or if you give Cosmo enough resources, then you are
actually measuring your subgraphs because Cosmo is faster than your subgraphs, because we
have so heavily optimized it and, yeah.
00:40:56:02 - 00:41:30:22
Jens
So overall, it's a great relationship with SoundCloud. In the in the beginning, we built, we, we
collaboratively built a library where you can send analytics data from your Node.js based,
GraphQL gateway or Node.js based GraphQL server to Cosmo, which is pretty cool because,
you might have the issue during the migration that you want to use both services for, for a
period of time so that you can serve some traffic here, some there.
00:41:30:25 - 00:41:56:08
Jens
And then when you move to Cosmo, you want to have breaking change detection based on
traffic. So if you if you don't yet run on on Cosmo, you you would lack this kind of data. So we
build a library that can send, analytics data from a Node.js based gateway to Cosmo. And so
you can, you can kind of warm up the analytics database and then make the switch.
00:41:56:08 - 00:42:02:16
Jens
So yeah, that's I think that's, that's, mostly the SoundCloud story.