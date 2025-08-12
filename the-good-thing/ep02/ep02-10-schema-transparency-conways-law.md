---
title: Schema Transparency and Conway's Law
slug: ep02-10-schema-transparency-conways-law
series: The Good Thing
episode: 2
chunk: 10
participants:
  - Stefan
  - Jens
segment: Schema Transparency and Organizational Structure
timecode: 00:39:32:04 – 00:43:16:23
start_time: 00:39:32:04
end_time: 00:43:16:23
speakers:
  - Stefan
  - Jens
topics:
  - Schema transparency benefits
  - Conway's Law in practice
  - Team discovery and collaboration
  - REST API fragmentation
  - Federation organizational advantages
tags:
  - conways-law
topic_tags:
  - conways-law
entities:
  - WunderGraph
  - Conway's Law
  - GraphQL Federation
  - REST APIs
  - Schema Registry
mentions:
  - team discovery
  - API fragmentation
  - organizational structure
  - schema design
  - team collaboration
summary: Jens explains how federation provides schema transparency that helps developers
  discover teams and understand organizational structure. He discusses Conway's Law
  - how organizations design systems that mirror their communication structures -
  and how federation makes this explicit. The conversation covers how REST APIs often
  lead to fragmentation while federation enables better team discovery and collaboration.
---

00:39:32:04 - 00:39:37:11

Stefan

Like I would physically have to go and talk to it. I wouldn't be able to figure it out from the code.

00:39:37:14 - 00:40:12:18

Jens

It really depends. Like there are things like backstage, where where you have like a tool that

really, has an open API spec for every subsystem that that exists. And you can figure out who

are the people behind, but yeah, we, we have seen that very few companies actually use like,

like a registry or thing of that sort with GraphQL federation, you have a schema, it's not optional,

like open API, you can have it. GraphQL.

00:40:12:18 - 00:40:42:09

Jens

GraphQl You must have a schema, otherwise it doesn't work. And so in the in the federated

graph you must have a schema registry. So that means you must have subgraphs. Each

subgraph has a schema. And if you have a schema registry, like, like Cosmo, you also can

associate people and teams with that subgraph. So if you look at the schema, you can

immediately figure out who, the people behind it.

00:40:42:09 - 00:40:49:20

Jens

You can you can talk to them. It's it's very transparent. And it takes very, very low effort to, to

figure all these things.

00:40:49:23 - 00:41:13:27

Stefan

And for the non-technical audience, the schema is just simply like a blueprint of that service.

And so basically what you're saying is, let's say that this rest, landscape, we might use

something like backstage, but it's optional. We might not do it. Maybe we're growing so fast we

might not do it. But with GraphQL Federation, you cannot have it without a schema, which is a

blueprint of how that service works.

00:41:14:00 - 00:41:35:20

Stefan

And with GraphQL, Federation enforces that strictness. So theoretically, in a GraphQL

federation landscape, I have a visual graph of how the company kind of works in a more or less

sense. And so I can go and I can make changes. And I can also kind of tangibly see what

services are interacting with others by just simply looking at the schema.

00:41:35:24 - 00:41:38:07

Stefan

Would you say that's correct?

00:41:38:10 - 00:41:44:20

Jens

Yeah, very much. And it's it's also interesting theres what's the name again. This.

00:41:44:22 - 00:41:49:11

Stefan

It's the law right. Yeah. Moore's law I think

00:41:49:14 - 00:42:20:14

Jens

No, that's that's about growth of CPUs. I forgot the name. It's not Hyrum's Law, but that's the

law. Maybe the audience knows that's a law. It's not really a law, but the Conway's law.

Conway's law. Yeah. So good. Conway's law. So the architecture that software engineers built, it

kind of replicates the communication. Our, the communication paths of the organization.

00:42:20:16 - 00:42:50:01

Jens

So if you have three teams in your organization, it's very possible that you have three

subgraphs in your federated graph, which is a pretty good feature, because if you if you happen

to be a front end dev and you use an entity on the user service, all you need to do is figure out

who are the the people, behind the user service.

00:42:50:03 - 00:43:16:23

Jens

And it's kind of like the, the subgraph architecture you have. It's it's somehow like sometimes a

team has more than one service, but somehow the subgraph architecture, it also kind of reflects

the, the team structure of the, of the company. So it's it's it's yeah, it's it's a pretty cool feature.

And just a question, Stefan. So I know you used to be a developer in the past. 