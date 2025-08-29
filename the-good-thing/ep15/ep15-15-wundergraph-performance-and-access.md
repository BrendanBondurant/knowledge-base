---
title: WunderGraph Performance Proof and Missing Customer Success Stories
slug: ep15-15-wundergraph-performance-and-access
series: The Good Thing
episode: 15
chunk: 15
participants:
  - Stefan
  - Jens
segment: WunderGraph Feature Benefits Analysis
timecode: 01:08:14 – 01:13:12
start_time: 01:08:14
end_time: 01:13:12
speakers:
  - Stefan
  - Jens
topics:
  - Schema Checks
  - Feature Flags
  - Customer Success Metrics
  - Performance Proof
tags:
  - schema-checks
  - ai
  - api-design
  - apollo-graphql
  - benchmarking
  - cache-warming
  - cosmo-router
  - federation
  - go
  - graphql
  - graphql-federation
  - rest
  - rest-apis
  - startup
  - telemetry
topic_tags:
  - schema-checks
entities:
  - WunderGraph
mentions:
  - Schema checks reducing QA time by 30%
  - Feature flags enabling 68% QA time reduction
  - Graph pruning and proposal checks
  - Contract testing replacement benefits
  - Customer use case presentation needs
summary: Stefan and Jens discuss WunderGraph's powerful but underrepresented features
  like schema checks and feature flags. They emphasize the need to showcase customer
  success stories, such as 30% QA time reduction through schema checks replacing contract
  testing, rather than just listing technical features without business context and
  quantified benefits.
---

01:08:14:21 - 01:08:38:15
Jens
And so yeah, and also I think our schema checks over time, like we have really we have put a
lot of work into this. We you know, we have graph pruning. We now have checks with proposals
like there are so many things I think we should really revisit this part and talk more about what
feature flags enables our customers to do and what the schema checks do.
01:08:38:15 - 01:08:42:18
Jens
So these are, I think, the the most powerful things here.
01:08:42:20 - 01:08:55:09
Stefan
I would say that I would agree with all that. Like there's not really we're talking about the
customer use cases here. Like, no, you put feature flags in a tiny little box, but it's actually such
a powerful feature. Same thing with all of these. So a lot of work to be done there.
01:08:55:10 - 01:09:03:22
Jens
But but you know, like don't just put features on a landing page like what are you ready to
benefit for the customer?
01:09:03:24 - 01:09:20:16
Stefan
What's the success like, if we were rewriting this, I don't know. On the beach rolled out feature
flags and they saw 68% reduction in QA time because with feature flags like that, that's what I
mean. Like, where is the success with the customer? I agree, something we can take back.
01:09:20:18 - 01:09:47:10
Jens
For example, one thing we saw with schema checks, is one customer was able to schema
checks to reduce QA time by 30% because, previously they had, contract testing for Rest APIs
with schema checks. They could remove that. And now they, faster and more resource efficient
in shipping and shipping the graph and, the APIs.
01:09:47:10 - 01:09:48:18
Jens
So that's really good.
01:09:48:20 - 01:10:07:07
Stefan
I like it. One other thing is, I'm going to jump real quick and come back, but this needs to be on
the landing page. PlanetScale had it. Boom boom boom boom. Small little improvement here.
Tiny little spike and boom. Yes. Fantastic. We need that on the landing page.
01:10:07:07 - 01:10:08:25
Jens
Yes, yes..
01:10:08:27 - 01:10:30:17
Stefan
That's a huge, powerful feature. And the story behind it needs to be there. But yeah, this this
right here, by the way, is kind of an oxymoron. Gain valuable insights into your GraphQL API.
But then we don't show any of the insights. We just say it like, show me the dashboard, show
me the advance request tracing. Show me the valuable insights that I'm going to get through
your product.
01:10:30:17 - 01:10:41:00
Stefan
You know what I mean? Yeah, yeah. Jens don't don't don't be too upset that we're roasting the
landing page. I know you put a lot of work into this, but the only way. Oh, I'm.
01:10:41:00 - 01:10:46:10
Jens
I'm not said it's you're you're absolutely right.
01:10:46:12 - 01:11:04:25
Stefan
Yeah, but what's good is we do this live and then we can actually take it back. So you guys are
going to see the improvements. This by the way I do like okay. So here we have some numbers.
But I think it's the wrong numbers. We're comparing against the Apollo router when actually we
should be talking about the P99 latency that our customers experience.
01:11:04:28 - 01:11:12:15
Stefan
What do you think. Oh also one other point. You're right. Cache warmer is tiny. It's at the very
bottom.
01:11:12:18 - 01:11:39:29
Jens
Yeah. Cache the cache warmer graph needs to be front and center. I think performance in a
router is important. Can we show differently? Yes. Is it the wrong number? Yeah. We could
actually show how it improves the customer. Like just the graph. We just had like P99 query
planning performance with the cache warmer. This is this is the router.
01:11:39:29 - 01:11:40:19
Jens
Yeah.
01:11:40:21 - 01:11:47:22
Stefan
And if we want we can even go the route of like SoundCloud. They had I forgot how many
gateways of.
01:11:47:24 - 01:12:03:21
Jens
Yeah. They, they because it's so efficient they could now run less gateways. So that's another
statement. So first statement is p95 per planning time. Second statement is SoundCloud reduce
gateways because they are so efficient perfect.
01:12:03:23 - 01:12:14:02
Stefan
So we can improve that down here. Three little features one that we don't even officially you can
kind of support and definitely need to fix that.
01:12:14:02 - 01:12:24:27
Jens
TheEDF's why why is it so small? It's it's such a powerful thing with Kafka and NATs and
everything and, yeah, but EDFS should have its own landing page.
01:12:24:29 - 01:12:46:04
Stefan
Yes. And same thing here. Okay, show me the organization. Wide access control. Like, show
me the grouping that Wilson is working on and how granular you can get, like, role based
access control on the namespace level, on the subgraph level, on the federated graph level.
Roll out your super graph to 400 developers across your organization, which, by the way, is a
use case that we have.
01:12:46:04 - 01:12:49:00
Stefan
We need to show that. Yeah.
01:12:49:02 - 01:12:54:08
Jens
Overall, out of ten points, how many points do you give this landing page.
01:12:54:10 - 01:13:12:04
Stefan
For what it was doing when we needed to do what it needed to be done? I give it like a five. It
did a great job. It really did. But I think now we definitely need to improve. Also is it just me. But
does the does the bar lag? Do you see the bar? It just like pauses your your computer.
01:13:12:04 - 01:13:12:20
Jens
It's not fast.