---
title: WunderGraph Feature Highlights Missing Business Impact
slug: ep15-14-wundergraph-feature-highlights-missing
series: The Good Thing
episode: 15
chunk: 14
participants:
  - Stefan
  - Jens
segment: WunderGraph Feature Analysis
timecode: 01:04:01 – 01:08:14
start_time: 01:04:01
end_time: 01:08:14
speakers:
  - Stefan
  - Jens
topics:
  - Cosmo as Apollo GraphOS replacement
  - Technical features vs business benefits
  - Schema registry business value unclear
  - Animation and design elements
  - Feature positioning precision
tags:
  - wundergraph
  - cosmo
  - feature-positioning
  - business-benefits
  - schema-registry
entities:
  - WunderGraph
  - Cosmo
  - Apollo GraphOS
mentions:
  - "Built for every use case" bold statement
  - Cosmo as drop-in replacement for Apollo
  - OSA solution bundling everything
  - Animation design appreciation
  - Technical features lacking business context
summary: |
  Stefan and Jens analyze WunderGraph's feature presentation, noting that while the positioning of Cosmo as a drop-in Apollo replacement is precise and hits their target market, the features are too technical without clear business benefits. They acknowledge good design elements but critique the lack of business value explanation for technical features like schema registry.
---

01:04:01:26 - 01:04:08:00
Jens
Is.
01:04:08:03 - 01:04:39:28
Jens
So what this is trying to do is it is it is trying to to pitch a message that we know something about
the future, that we understand the market. And we we want to we want to show our expertise.
And there is a full report and you should get it. And, from the interactions with this button, we
know it works.
01:04:40:00 - 01:05:08:05
Stefan
I would say, overall not bad. Scroll down. Built for every use case. Well, that's a bold statement.
Manage GraphQL at any scale from Monolith of Federation. I do like that. And then here we go
into the four core features for our ICP. So Cosmo is a drop in a replacement to other services
like a Apollo GraphOS, it is the only OSA solution that bundles everything from router to
schema, registry, analytics and tracing, and one package perfect for monolithic or federate.
01:05:08:11 - 01:05:14:03
Stefan
I actually don't mind this. This is actually like if what we're aiming for, it's hitting right on the spot.
01:05:14:04 - 01:05:16:07
Jens
It's it's precise right.
01:05:16:09 - 01:05:20:20
Stefan
Yeah. Exactly. It's precise.
01:05:20:22 - 01:05:42:12
Stefan
I also like this animation. Kind of cool okay. So that's good okay. Nice little pop up. And then you
see, you know, I'm, I'm going to cheat a little bit because we have a designer that I like was
going through this thing and like, these are good. But there are two technical like what does the
schema registry unlock from the business.
01:05:42:14 - 01:05:49:02
Stefan
job.
What does the change log unlock? But I think from what we were aiming to do, it does a good
01:05:49:05 - 01:06:23:03
Jens
Features that enable teams to move fast without breaking things. It's not bad. It's also not. It's
not business focused enough. Schema registry like I don't know what what what does it tell
you? Change lock, synchronize changes. Integrations, feature flags. Schema checks. You know,
like one one thing we should actually do is and we have learned this over time.
01:06:23:05 - 01:06:58:00
Jens
So initially we built feature flags for one customer. They actually they used this before they were
migrating from Apollo. They used Apollo Gateway and they built their own feature flag,
mechanism into the gateway, which was pretty insane because what they did is if you send,
specific header to the gateway, the gateway would, on the fly build a custom, a custom super
graph while the request is in flight.
01:06:58:02 - 01:07:22:23
Jens
Think about it. Compose the custom feature flag subgraph into a schema and then resolve it. So
first of all, that was like super slow. And second, if something goes wrong in this composition,
then it just wouldn't work. And also it would put like crazy, crazy workload on the on the gateway
because the gateway would have to do composition at that point.
01:07:22:25 - 01:07:50:09
Jens
Composition is expensive, like it's a CPU intensive task. It can it can stop the world on the
Node.js gateway for a second or two. Like it's crazy. So we we built a version of feature flags
that works at compile time, and we build it into into Cosmo router. And what we have learned
over time is almost every of our customers is building workflows around feature flags.
01:07:50:09 - 01:08:14:18
Jens
It is such a powerful tool that you can have multiple versions of your graph on one router, and
you can run that under feature flags and we need to make that much more prominent because
it's such a, such a widely used and, broadly adopted feature. And here it is. It's just a little box
and it doesn't really tell you like how strong it is.