---
type: podcast-chunk
title: Cosmo Connect Overview and gRPC Motivation
slug: ep27-02-cosmo-connect-overview
series: The Good Thing
episode: 27
chunk: 2
segment: Introducing Cosmo Connect and gRPC architecture
timecode: 00:06:23 – 00:10:23
start_time: 00:06:23
end_time: 00:10:23
speakers:
  - Jens
  - Dustin
topics:
  - Cosmo Connect
  - gRPC Adoption
  - Architectural Goals
tags:
  - grpc
  - graphql
  - graphql-federation
  - architecture
entities:
  - Cosmo Connect
  - WunderGraph
summary: Jens and Stefan introduce Cosmo Connect, explaining the motivation for adopting gRPC and how it fits into WunderGraph’s architecture strategy.
---
00:06:23:21 - 00:06:54:14
Jens
So that's why we call it wonder. WunderGraph can be anything, but somehow it sounds German
and graph. Is cool. And so anyways, here we are. We launched Cosmo Connect this week. We
had a webinar. It was pretty good. It was, I think, the best webinar we ever did. And it was the
first one. And yeah, maybe we can talk a little bit about what what what is Cosmo Connect and
why we why we built it.
00:06:54:14 - 00:07:15:16
Jens
And, what were the challenges and and, what what what's actually behind the scenes? Like how
how does it even work? And, then Cosmo Connect is actually multiple things you can speak.
instead of speaking to a GraphQL subgraph. You can speak to a gRPC subgraph, it can be a
dedicated service, or it could be a plugin.
00:07:15:21 - 00:07:49:15
Jens
And maybe we also want to talk about what is a plugin and what distinguishes the two. When
would you use a plugin? And how does the plugin even work? Because the code needs to
somehow get to the router. And I think that's a pretty interesting story because, Jesse, having
worked at Fly before, he figured out, a pretty cool, like, pretty cool way of of, putting together the
stuff for a plugin into an OCI thing and then pushing the OCI thing into, into.
00:07:49:20 - 00:08:07:00
Jens
So I don't know, you need to tell us. Okay, where do we start? What is what is cosmo connect
and why did we build it? Please don't everybody speak at the same time? Do I need to point
fingers or who likes the question?
00:08:07:03 - 00:08:28:08
Dustin
No, I like it. I mean, our, initiative, our goal. I mean, we love, many great customers. And what
we have seen as a pattern is people understands the benefits of a super graph. However, not
every team can adopt it because it's it's it's a learning curve to adopt graphql and doing
GraphQL. Right? It's it requires different technology.
00:08:28:08 - 00:08:54:22
Dustin
You need to adopt to a subgraph framework, which also has its its quirks and the biggest factor
is you're probably already have established an ecosystem and a service that you don't want to
change because it's working fine in production. So how can we bring those people into the
super graph so they can benefit from all these, these things like analytics, breaking change
detection, schema collaboration.
00:08:54:25 - 00:09:17:13
Dustin
And then I think the we also got great feedback from, from a customer. And I think one of the
solution was to, to remove GraphQL from the backend side, because people believe and also
understand the benefits of on the consumer side of the front end side. And then it was very, I
would say, a very natural fit to say, why not using gRPC?
00:09:17:15 - 00:09:51:02
Dustin
Because gRPC is is so established in the industry. It's, it's it's known for its, performance type
safety and also easy compatibility with the ecosystem and programing languages. And then we
thought about like, why not creating something that can translate GraphQL to gRPC. Then we
could leverage all the benefits of the gRPC itself. And yeah, it's so that people can purely focus
on business logic on implementation and bring in that way as an existing Rest API.
00:09:51:05 - 00:09:54:18
Dustin
SOAP API into the super graph.
00:09:54:20 - 00:10:23:00
Jens
Yeah. And if I remember correctly, in the beginning we were we were talking a little bit about
what are the possible technologies. And then well one thing I keep seeing is people keep
coming up with, use cases where, where they think WebAssembly would be amazing. And we,
we also had, like in the very beginning, we were talking about like, different approaches, like
how how could you actually do it?
