---
title: Federation as Schema Coordination and Observability via Cosmo
slug: ep09-03-federation-observability-cosmo
series: The Good Thing
episode: 9
chunk: 3
participants:
  - Jens
  - Cameron
segment: Federation benefits and schema registry
timecode: 00:08:36:13 – 00:13:07:13
start_time: 00:08:36:13
end_time: 00:13:07:13
speakers:
  - Jens
  - Cameron
topics:
  - Schema registry and supergraph coordination
  - Client query analytics and monitoring
  - Breaking change prevention
  - QA time savings through contract testing
  - Schema mapping and team coordination
  - Federation flywheel effect
tags:
  - schema-registry
  - observability
  - contract-testing
  - cosmo
topic_tags:
  - schema-registry
  - observability
  - contract-testing
  - cosmo
entities:
  - Cosmo
  - WunderGraph
  - GraphQL Federation
  - Schema Registry
mentions:
  - supergraph and subgraph schemas
  - client query analytics
  - 30% QA time savings
  - WGC check command
  - 20 clients and 2000 queries
  - schema-to-people mapping
summary: Jens explains how federation provides schema coordination through Cosmo's
  registry, which tracks supergraph schemas, subgraphs, and client usage patterns.
  This enables breaking change prevention, team coordination, and significant QA time
  savings. He discusses the federation flywheel effect where more users create more
  use cases, attracting even more users.
---

00:08:36:13 - 00:08:59:22
Jens
But in federation you have your super graph schema, you have your subgraph schemas, and
you have clients using that. And then you have a schema registry like Cosmo. And Cosmo
knows the schema of the supergraph. It knows the schema of the subgraphs. It knows, like your
linting rules and other things, and it knows all clients by name version.
00:08:59:29 - 00:09:20:28
Jens
And what fields they use in what query and when. For example, it knows exactly “oh, we have
these 20 clients and this are the, I don't know, 2000 queries. They, they made, over the last 30
days”. So now if you change a subgraph, first of all, you know who's using you. You can look at
the analytics.
00:09:20:28 - 00:09:40:29
Jens
You know that. So you can talk to the people. And second, if you are on the client team, it's
actually very easy to figure out if you let's say you load an entity and it needs an additional field,
you can actually look at the schema of the super graph. You can figure out where is the stuff in
the super graph coming from, like which subgraph.
00:09:41:02 - 00:10:20:29
Jens
So you can figure out who are the people behind that. Because the schema registry, it's kind of
like a map for you to to map like things in your domain to people. And so you can figure out who
other people you can talk to them. And then in terms of breaking changes, we have one, one,
customer, who reported once they moved the project on to Federation, they saved more than
30% of the time in QA for contract testing because they they just wouldn't have to write the
conflicts anymore because, we have this command WGC check.
00:10:21:01 - 00:10:51:05
Jens
So you run a check when you want to change a subgraph, and then it verifies that you're not
breaking clients. So yeah, overall, you can have, you know, lots of people have opinions on on
GraphQL. It's good, it's bad. It's replacing REST. It's not replacing REST. But at the end of the
day, I would say our opinion that at WunderGraph, we're actually not like GraphQL is the best
thing in the world.
00:10:51:05 - 00:11:21:09
Jens
We're more like federation allows us to have many clients and many backends. And without this
middle layer in between and without the matrix, and we know what is using what and where is
something coming from, and we can prevent breaking. So yeah, like for us, federation solves a
huge problem of scaling clients and backends. And if you if you want to scale a company, it
means you're adding products.
00:11:21:09 - 00:11:31:09
Jens
It means you're adding business logic. So you add backends. So yeah this needs to live
somewhere. So. Yeah. Anything you want to add.
00:11:31:12 - 00:11:43:26
Cameron
Exactly
Now I think you hit the nail right on the head. You know, it, it's just a really great tool, in my
opinion, to empower scale and ease of use and to empower stability.
00:11:43:28 - 00:12:16:10
Jens
Yeah. Which leads to, the next topic. So, like I said, we like federation, but, one, one problem of
federation is, it relies on GraphQL. And not everybody knows GraphQL, like the majority of the
market has not yet adopted federation has not yet adopted GraphQL. So one topic we're
working on is we want to make federation like again.
00:12:16:10 - 00:12:43:16
Jens
Like when when when when we think about what we're doing, we're thinking less about
GraphQL. We're thinking more about federation. Like the problem like we solve the problem. I
just described federation or GraphQL is a detail. So one of the challenges we we find is that, as
you bring federation into a company, more and more people are interested in using it, in
leveraging the graph.
00:12:43:20 - 00:13:07:13
Jens
And obviously your graph, it becomes a more powerful asset for the company if it's more
capable. So there's like, yeah, like a, like a flywheel effect. You have more users, you have more
use cases. It can do and then it attracts more people. So how can we get more people to to
leverage the, the graph, maybe even without understanding GraphQL.