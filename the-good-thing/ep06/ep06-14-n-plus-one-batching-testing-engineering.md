---
title: N+1 Problems, Batching, Testing, and Engineering Philosophy
slug: ep06-14-n-plus-one-batching-testing-engineering
series: The Good Thing
episode: 6
chunk: 14
participants:
  - Jens
  - Stefan
segment: N+1 problems, batching, testing, and engineering philosophy
timecode: 00:45:00:15 - 00:50:22:01
start_time: 00:45:00:15
end_time: 00:50:22:01
speakers:
  - Jens
  - Stefan
topics:
  - N+1 Problems
  - Batching
  - Testing
  - Engineering Philosophy
summary: |
  Jens and Stefan discuss the N+1 problem, batching strategies, the importance of testing, and their overall engineering philosophy for building robust products.
tags:
  - graphql
  - startup
  - benchmarking
  - go
topic_tags:
  - graphql
  - startup
  - benchmarking
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
  - graphql
mentions:
  - N+1 problem solutions
  - batching implementation strategies
  - testing methodology importance
  - engineering best practices
  - technical problem solving
  - performance optimization
---

00:45:00:15 - 00:45:26:04
Jens
And here so we have this situation where, you know, we, we, we have one API call this plus one
where we load, products. And then we have n API calls where for each product we make a
second rest API call to fetch the price. And if you go to the next slide.
00:45:26:06 - 00:45:51:28
Jens
Here go to slide three first. So the slide four actually. Okay. The reason why you can so simply
spot this problem is so you see here that we have products and we attach this connect directive
and it returns a list of product. So this is the first hint. And now you go back to slide 3. We.
00:45:52:00 - 00:46:39:11
Jens
So you know we're getting a list of producst. And then here inside product you see that inside
the product type we now connect the price. And if you connect these dots you know we now
attach a single field resolver to an entity to to a type that's within a list. And the problem is very
simple like how can you avoid this is what you need to do is if you create like a list of things and
you want to attach something to the list, both resolvers need to be on top of the list, because
what you need to do is you need to fetch the list.
00:46:39:11 - 00:47:07:13
Jens
And then for the list you need to fetch the prices. But the problem here is you can see we make
a Post request and the product ID is a single ID. So this endpoint it can only give us pricing for,
for for one product. And and this is the problem and you know like in general my thoughts on
this connect thing is like yes.
00:47:07:20 - 00:47:38:00
Jens
Like it it's a quick fix. It can help in situations to quickly get the rest API into your, into your,
GraphQL federation thing. But like, I'm you Stefan. You know, how we built, how we build
cosmo. We our our thinking is never to to go fast or something. It's always to to think about
doing the right thing.
00:47:38:03 - 00:48:05:10
Jens
And I mean the, the, the biggest topic if you want to unshare, that's that's fine. But the biggest
topic in GraphQL or one of the big topics, you know, everybody's talking about persisted queries
and then everybody is making jokes about n plus one problems and I don't know why. Why do
we create a new solution that from the very beginning is not thinking about.
00:48:05:10 - 00:48:32:16
Jens
n plus one. And, and I think, you know, if you, if you, if you look at this, there's a high likelihood
that your Rest API doesn't have batching. That's no batch endpoint. And so for me, the big
question is, let's say you are like, like, high traffic site. Do you really want to make that?
00:48:32:16 - 00:48:57:18
Jens
Let's say you, you load 100 products. Do you want to make 101 API calls? Like, what's the
performance? If your router makes 101 API calls per single request to the router, it means
you're creating a lot of traffic in your infrastructure. Is this really the solution or should you think
about, okay, we have this Rest API.
00:48:57:20 - 00:49:26:19
Jens
Maybe on the Rest API we can add another endpoint. We can turn it into a subgraph. And this
subgraph will support batching so that we make two requests for this whole thing. And so like
the pitch of Apollo is you don't pay millions. By the way I don't buy this like this is it's ridiculous.
But they say save millions, save a year of work and you can solve this in two days.
00:49:26:25 - 00:49:58:17
Jens
But that's another thing. So you have this connector stuff. It's GraphQL, SDL how do you test it?
And I see it from Apollo in the demos. And by the way this is I'm not ranting against Apollo. I'm
ranting against bad engineering because what I see is so in the demo they create this thing and
then they save and then they open the playground and they click a button and then they see,
okay, now this thing works.
00:49:58:17 - 00:50:22:01
Jens
And yes, it works, but no developer ever wants to have a workflow where you write your SDL
and then you open the playground and then you test if it works like what a developer wants is
you write code, you check it into CI, you run tests, and then you can deploy that. So where are
the tests? Where's the test framework?