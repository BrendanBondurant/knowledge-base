---
title: Federation and Schema Registry
slug: ep22-04-federation-and-schema-registry
series: The Good Thing
episode: 22
chunk: 4
participants:
  - Stefan
  - Jens
segment: Apollo Principles Analysis
timecode: 00:16:05:00 – 00:19:26:27
start_time: 00:16:05:00
end_time: 00:19:26:27
speakers:
  - Stefan
  - Jens
topics:
  - Apollo GraphQL federation principles
  - Schema registry importance
  - Principled GraphQL framework
  - Graph composition strategy
tags:
  - schema-registry
  - principled-graphql
  - ai
  - api-design
  - apollo-graphql
  - composition
  - federation
  - go
  - graphql
  - graphql-federation
  - microservices
  - monolith
  - rest
  - rest-apis
  - rest-connectors
topic_tags:
  - schema-registry
  - principled-graphql
entities:
  - Apollo
  - Stefan Avram
  - Jens Neuse
mentions:
  - federation principles
  - schema registry role
  - graph composition
  - Apollo framework
summary: Stefan and Jens analyze Apollo's federation and schema registry principles
  from their Principled GraphQL document. They discuss the importance of centralized
  schema management and how Apollo's approach to graph composition influences the
  broader GraphQL ecosystem and competitive positioning.
---

00:16:05:28 - 00:16:40:24
Jens
Tries to bring everybody to Federation. That's kind of like, yeah, you, you know more or less
that's that's how you two and the, the, the super interesting bit is with with Apollo connectors,
you might be thinking that somehow they, they are even breaking the second, the second
principle in some way because the federated implementation, it somehow says you should have
subgraphs.
00:16:40:26 - 00:17:12:26
Jens
That's are, that's are, federated or your, your subgraphs, should be or your, your super graph. It
should be split into multiple subgraphs. And what we are now seeing is that, many companies
who have like legacy Rest APIs or whatever, they, they didn't like this abstraction where they
had to run and deploy a subgraph that then connects to the to the microservices, to the, to the
rest APIs or whatever.
00:17:12:28 - 00:17:55:03
Jens
And so, I think Apollo is showing with their connectors approach that the community wants
something different, that the community is actually thinking more like a monolithic approach, like
the community is more, more interested in, yeah, maybe it doesn't have to be like so federated.
Maybe sometimes, but not always. For example, this is also something I learned from Netflix,
like initially, Netflix built multiple subgraph services per team, but they then realized that this is a
little bit too much.
00:17:55:03 - 00:18:23:01
Jens
It's it's too complex. And they are now paddling back in in the direction of like more one
subgraph per team, but with connectors, if you think about it, connectors is is again that you,
you just have the super graph schema with the connectors directives. You directly connect to
Rest APIs. So at the end of the day, you don't really have subgraphs anymore.
00:18:23:01 - 00:18:55:10
Jens
It's it's a monolith now. And the monolith connects to microservices through directives. Which
leads to the question yeah. Why why federation is it is it still is still federation the, the right way
to go, which I also have like opinions on. But that's the first two. So we have one graph. We
have federated implementation by the way I, I still think there's there's a lot of value in federated
implementation.
00:18:55:13 - 00:19:26:24
Jens
The third principle says track the schema in the registry. I think that that is the most simple one.
And it's, it is very, very much proven that we absolutely need a schema registry, but not just to,
to track the, the schema itself, but also the clients and how they use the schema. I think that's is
probably like one of the most, one of the most powerful concepts.