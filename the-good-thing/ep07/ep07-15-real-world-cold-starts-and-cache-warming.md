---
title: Real-World Cold Starts and Intelligent Cache Warming
slug: ep07-15-real-world-cold-starts-and-cache-warming
series: The Good Thing
episode: 7
chunk: 15
participants:
  - Jens
  - Sergiy
  - David
segment: Production benchmarking and cache warming solutions
timecode: 01:20:05:01 – 01:26:02:29
start_time: 01:20:05:01
end_time: 01:26:02:29
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - Configuration bias in benchmarking
  - Production router lifecycle management
  - Config invalidation and cold start problems
  - Heuristic-based cache warming solution
  - Real-world performance vs lab testing
tags:
  - cache-warming
  - ai
  - benchmarking
  - cosmo
  - cosmo-router
  - federation
  - go
  - graphql-federation
  - query-planning
  - rest
  - rust
  - startup
topic_tags:
  - cache-warming
entities:
  - Cosmo Router
  - WunderGraph
  - Node.js
  - K6
  - Jens Neuse
  - David
  - Sergiy
mentions:
  - Node.js single CPU deployment
  - e-commerce website scaling
  - 100,000 concurrent users
  - query planning cache invalidation
  - analytics warehouse integration
  - heuristic query prioritization
  - traffic pattern scaling
summary: Jens explains the inherent bias in benchmarking due to configuration knowledge
  differences and critiques unrealistic lab benchmarks. He details WunderGraph's innovative
  cache warmer solution that uses analytics to pre-warm router caches with the most
  complex queries before accepting traffic, ensuring production performance during
  config changes for large-scale deployments.
---

01:20:05:01 - 01:20:28:10
David
Likewise, I could make it look like I, I pass everything, whereas I'm not passing things up. As
long as you go out of that scope, I'm no longer passing those things. So I would take any
benchmark, any, any audit, anything like that with a grain of salt and do my do your own kind of
research and benchmarking and figure out what what what works for your solution, what works
for your company and whatever else.
01:20:28:13 - 01:20:36:07
David
trust things so far.
I think it's important to know that everybody wants to look good. So, you know, you can only
01:20:36:10 - 01:21:04:16
Jens
Yeah. Well, one comment from my side, I would say, even if there's no ill intent on the side of
someone creating and publishing a benchmark or an audit, I would say there's always bias. Bias
in the sense that I mean, obviously, like, even if we if you said like, okay, everybody wants to
look good, but at the same time, everybody knows the tool best.
01:21:04:16 - 01:21:43:16
Jens
So I know exactly how to configure wunder graph, cosmo router. But another vendor who
doesn't know it and who actually doesn't care to correctly configure it because they want to look
good and they are not deeply interested in in perfectly configuring cosmo router, they will maybe
just use defaults and then deploy the whole thing on the machine that is so big that the defaults
don't make sense, because the defaults are designed for, for a smaller machine or whatever.
01:21:43:16 - 01:22:25:28
Jens
It can be any situation, and this can happen to anybody in any direction like that. There are
other vendors. They have a gateway in written in Node.js. So we know if you want to build
something or if you want to get the best performance out of Node.js, it's probably very likely that
you deploy a large fleet of gateways on ports with one CPU, because there's no big reason to
deploy Node.js on multi CPU machines, or you add like an extra scheduler and then you run
multiple instance, like you can do things like that, but it's it that's complexity.
01:22:26:04 - 01:22:53:26
Jens
So I think that's always this kind of bias that for example, you you like we know how cosmo
router works. We know what kind of caches it has. And we know how to use these caches
efficiently. And so that that's that's one topic. And another topic is I particularly dislike crafted
unrealistic benchmarks. And I explain why.
01:22:53:29 - 01:23:17:26
Jens
So a benchmark you can use k six or whatever and you can design this benchmark how how
you, how you like it. And then typically you can do things like ramp up and then you have like a
bunch of queries and you fire these queries in various ways, and you benchmark the shit out of
the router.
01:23:18:01 - 01:23:51:02
Jens
Okay. So you're hammering the router with traffic, and you get whatever results and you're like,
okay, one benchmark is faster than another, and now you go into production. And in production,
something completely different happens in production. Let's say you are a very big e-commerce
website, and you have billions of requests per day. That means you don't have one router, you
have a hundred routers, maybe a thousand, I don't know, like it.
01:23:51:04 - 01:24:12:00
Jens
It can be many, many routers. And so what is the life cycle of a router? From time to time, you
need to ramp up the number of routers. Then you scale them down because you have changes
in traffic patterns. Like maybe at night there's less traffic a day there's more traffic. So you ramp
up, you ramp down. So you have new instances of the router.
01:24:12:02 - 01:24:49:26
Jens
And then there are situations where someone changes a subgraph. So you publish a new
configuration. So now the router needs to invalidate the configuration. And the thing is in your
benchmark you're assuming that you have one single router and it has a stable config. But that
doesn't really matter so much in reality because in reality, let's say you have 100,000 concurrent
users on your e-commerce website and they are loading the shopping basket or whatever they
want to buy your products, and you invalidate the router config.
01:24:49:28 - 01:25:22:12
Jens
That means we would now have to query plan all queries. On I don't know, 100 routers. So we
would immediately get the spike in, in in CPU and latency because sometimes query planning
can take milliseconds. It can take second sometimes worst case, some queries are very
complex to plan. So what you benchmarked in your lab versus what really matters in reality it
can be different things.
01:25:22:12 - 01:26:02:29
Jens
And this is something it's very hard to, to capture and to to end this real life story. We, we had
this situation with one very big, customer. There's a solution. And I think we're the we're the first
in the market to do this. We built, the cache warmer that is based on heuristics. So we sent
information from the router to our analytics warehouse, and then we we built, like, a top list of
queries that take a long time to plan and or the worst time to plan.