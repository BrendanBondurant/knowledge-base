---
title: Schema Quality and REST API Abstraction Leakage
slug: ep08-07-schema-quality-and-abstractions
series: The Good Thing
episode: 8
chunk: 7
participants:
  - Stefan
  - Jens
segment: Schema design philosophy and subgraph quality focus
timecode: 00:49:03:07 – 00:54:23:05
start_time: 00:49:03:07
end_time: 00:54:23:05
speakers:
  - Stefan
  - Jens
topics:
  - Schema quality as primary concern
  - Subgraph implementation verification
  - Type safety and developer experience improvements
  - REST API abstraction leakage into GraphQL schemas
  - Federation directive complexity (@provides, @requires)
tags:
  - federation
  - graphql-federation
  - ai
  - schema-design
  - type-safety
  - subgraph-quality
  - developer-experience
  - abstraction-leakage
  - federation-directives
entities:
  - graphql
  - Federation
  - SAP
  - SOAP APIs
  - REST APIs
  - Stefan Avram
  - Jens Neuse
mentions:
  - @provides and @requires directive challenges
  - subgraph schema verification
  - modernization efforts
  - legacy SOAP/REST integration
  - schema structure dictation by REST APIs
  - GraphQL compatibility concerns
summary: |
  Deep dive into schema quality concerns and the philosophical tension between REST connector convenience and GraphQL best practices. Jens argues that REST APIs can leak their abstractions into GraphQL schemas, potentially compromising schema design quality, while emphasizing the importance of well-designed schemas over convenient integration shortcuts.
---

00:49:03:07 - 00:49:43:10
Jens
Yes, you need to solve authentication and yeah, so, I don't know, I, I would love if we could
move a little bit slower and, but yeah, it is what it is. And, and the harsh reality unfortunately, is I
think we, we will end up supporting it anyways because at some point people want to migrate to
cosmo and they say, yeah, but we use these directives and yeah, until then, maybe we figure
out a better way to, to do, to do REST with GraphQL.
00:49:43:10 - 00:49:50:11
Jens
But so far, yeah. The other aspect. Sorry for my real quick.
00:49:50:11 - 00:50:08:03
Stefan
Real quick Jens, And before we jump in there, we have a decent amount of viewers. Guys stick
around till the end because, we have a cool, I guess, a surprise or it's a bundle of knowledge
that you don't want to miss and you definitely want to get access to so Jens continue your rant.
But please stick around till the very end.
00:50:08:09 - 00:50:25:24
Stefan
We're going longer for just ten minutes and five minutes, we're going to announce something
really cool that we spent a lot of time working on. Honestly, my fault because Jens told me about
it three months ago and it took forever. But I'll expand on that a little bit less. But Jens continue
on the REST connector. So I understand the technical application to implement.
00:50:25:29 - 00:50:32:12
Stefan
I don't know the work, but you know, the word I'm trying to say, but I understand that part. But
continue on the REST connectors.
00:50:32:14 - 00:51:06:27
Jens
Yeah. So I understand the desire. But at the business side, I can also talk to all our customers
and it doesn't seem to be the biggest problem to write the subgraph. There are many other
problems like security. What? I hear people talk a lot about is Things like the @provides
directive and @requires directive and like these directives in general.
00:51:06:27 - 00:51:41:02
Jens
And how can we properly map dependencies between fields and how can we achieve better
type safety in subgraphs, and how can we achieve that? If a subgraph says they implement a
schema, how do you actually verify that they really implement that schema? So these kind of
things so the quality of subgraphs, the quality, the type safety, the developer experience of
creating subgraphs.
00:51:41:04 - 00:52:09:24
Jens
Yeah. We we think there's a, there's a, there's a huge gap. And I think if we, if we make building
subgraphs better and easier and more type safe and all these kind of things, then there is the
question of is REST connector? Is it really the biggest problem or. Yeah. So but this is this is our
focus, this is our understanding of the of the market.
00:52:09:24 - 00:52:16:24
Jens
And yeah, future will will will tell us if, if we're right or wrong or whatever.
00:52:16:26 - 00:52:44:22
Stefan
Yeah, TBD. We'll figure it out. It's I haven't been hearing it from our customers. But then again
let's see. Let's see where the market pulls us. I do know that one of the biggest use cases for
GraphQL federation is modernization efforts. It's companies that have grown super fast. They
have a lot of tech that or that. They're just significant behemoths like SAP or large big
companies, and they want to modernize their stack and they have a bunch of legacy old Soap
or REST APIs.
00:52:44:22 - 00:53:03:04
Stefan
I can see the use case there, but like you said, I think the approach is a little rushed. I think it
needs to slow down a little bit, use these behemoths as a way to kind of move towards that. But
I have the same thoughts with that. And then guys, since we are almost at time definite. Yes.
00:53:03:07 - 00:53:04:24
Jens
Just one thought.
00:53:04:26 - 00:53:10:05
Stefan
Yes. Continue. That on the REST connectors though.
00:53:10:07 - 00:53:14:20
Jens
Yeah. Like but it's, it's the last the last puzzle.
00:53:14:22 - 00:53:17:06
Stefan
What is it?
00:53:17:08 - 00:53:54:17
Jens
From conversations with, I would say our biggest customers and users, I would say the, the big
thing I learned is the most important thing is the schema. The most important thing is to have a
good and well-designed schema. If we are building our schema in a way that wants to just
connect REST APIs, there's a likelihood that we are leaking the REST API abstractions into our
schema, because the REST APIs might dictate structure.
00:53:54:17 - 00:54:23:05
Jens
They might dictate behavior that we actually don't like in in the GraphQL world. Or maybe it's not
really compatible with GraphQL. So yeah. Our we're what we're what we're aiming for is to help
customers build great schema and to build a great API. And, this might be conflicting with
connectors. So that's my my last thoughts on the topic.