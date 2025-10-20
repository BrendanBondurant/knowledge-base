---
type: podcast-chunk
title: Open Source Efficiency, Code Quality, and Procurement
slug: ep06-11-open-source-efficiency-code-quality-procurement
series: The Good Thing
episode: 6
chunk: 11
segment: Open source efficiency, code quality, and procurement
timecode: 00:31:41 - 00:36:26
start_time: 00:31:41
end_time: 00:36:26
speakers:
  - Jens
  - Stefan
topics:
  - Open Source Efficiency
  - Code Quality
  - Procurement
  - Sales Strategy
tags:
  - startup
  - federation
  - graphql-federation
  - ai
  - open-source
  - api-design
  - apollo-graphql
  - benchmarking
  - cosmo
  - cosmo-router
  - go
  - graphql
  - rest
  - rest-apis
  - rest-connectors
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
summary: |
  Jens and Stefan discuss the efficiency benefits of open source, the impact on code quality, and how open source can streamline procurement and sales processes for startups.
---

00:31:41:11 - 00:36:26:27
Jens
So you know we're getting a list of producst. And then here inside product you see that inside
the product type we now connect the price. And if you connect these dots you know we now
attach a single field resolver to an entity to to a type that's within a list. And the problem is very
simple like how can you avoid this is what you need to do is if you create like a list of things and
you want to attach something to the list, both resolvers need to be on top of the list, because
what you need to do is you need to fetch the list.

And then for the list you need to fetch the prices. But the problem here is you can see we make
a Post request and the product ID is a single ID. So this endpoint it can only give us pricing for,
for for one product. And and this is the problem and you know like in general my thoughts on
this connect thing is like yes.

Like it it's a quick fix. It can help in situations to quickly get the rest API into your, into your,
GraphQL federation thing. But like, I'm you Stefan. You know, how we built, how we build
cosmo. We our our thinking is never to to go fast or something. It's always to to think about
doing the right thing.

And I mean the, the, the biggest topic if you want to unshare, that's that's fine. But the biggest
topic in GraphQL or one of the big topics, you know, everybody's talking about persisted queries
and then everybody is making jokes about n plus one problems and I don't know why. Why do
we create a new solution that from the very beginning is not thinking about.

n plus one. And, and I think, you know, if you, if you, if you look at this, there's a high likelihood
that your Rest API doesn't have batching. That's no batch endpoint. And so for me, the big
question is, let's say you are like, like, high traffic site. Do you really want to make that?

Let's say you, you load 100 products. Do you want to make 101 API calls? Like, what's the
performance? If your router makes 101 API calls per single request to the router, it means
you're creating a lot of traffic in your infrastructure. Is this really the solution or should you think
about, okay, we have this Rest API.

Maybe on the Rest API we can add another endpoint. We can turn it into a subgraph. And this
subgraph will support batching so that we make two requests for this whole thing. And so like
the pitch of Apollo is you don't pay millions. By the way I don't buy this like this is it's ridiculous.
But they say save millions, save a year of work and you can solve this in two days.

But that's another thing. So you have this connector stuff. It's GraphQL, SDL how do you test it?
And I see it from Apollo in the demos. And by the way this is I'm not ranting against Apollo. I'm
ranting against bad engineering because what I see is so in the demo they create this thing and
then they save and then they open the playground and they click a button and then they see,
okay, now this thing works.

And yes, it works, but no developer ever wants to have a workflow where you write your SDL
and then you open the playground and then you test if it works like what a developer wants is
you write code, you check it into CI, you run tests, and then you can deploy that. So where are
the tests? Where's the test framework?

And I don't know but you need a data loader. You need batching. You need tests. You need
other things. At the end of the day, if you want to do this right, we need to write some code and
we need to have a repository. And yes, maybe it's not going to take two days, but adding this
one endpoint, maybe it takes a few more days, but then it's performant.

It's tested like what happens if the API changes. Yeah. You go to your SDL, you add the field,
you open your playground and then it works right. Like, okay, you check this in. There's no test.
Pull request is open. How do I verify that it works? Should I also run it locally and open my
playground and test how?

Like, I don't know. That's not that. That's not a I don't like it.