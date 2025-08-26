---
title: gRPC Federation Future and Apollo Leadership
slug: ep24-02-grpc-federation-future
series: The Good Thing
episode: 24
chunk: 2
participants:
  - Stefan
  - Jens
segment: gRPC Federation Discussion
timecode: 00:04:05:03 – 00:10:10:00
start_time: 00:04:05:03
end_time: 00:10:10:00
speakers:
  - Stefan
  - Jens
topics:
  - gRPC as the future of GraphQL Federation
  - Federation complexity and type safety issues
  - Moving GraphQL layer from subgraph to router
  - Compiler-generated gRPC specs
  - Data loading and batching solutions
  - WunderGraph's approach to Federation
tags:
  - grpc
  - federation
  - graphql-federation
  - grpc
  - graphql-federation
  - data-loading
  - graphql
  - ai
  - apollo-graphql
  - benchmarking
  - cosmo
  - cosmo-router
  - go
  - open-source
  - rest
  - rest-connectors
  - startup
  - typescript
topic_tags:
  - grpc
  - federation
  - graphql-federation
entities:
  - WunderGraph
  - Cosmo Router
  - Apollo Federation
  - GraphQL
  - gRPC
  - Curtis (Uber)
  - LinkedIn
  - YouTube
  - Jacob
mentions:
  - Anchor Man movie references
  - Curtis's LinkedIn post
  - type safety guarantees
  - SDL compilation to protobuf
  - data loader implementation
  - subgraph frameworks
  - batching problem solutions
summary: |
  Stefan and Jens discuss their vision for gRPC as the next generation of GraphQL Federation. Jens explains how moving the GraphQL layer from subgraphs to the router can solve type safety, complexity, and performance issues. They detail their approach of compiling subgraph SDL to gRPC specs and handling data loading at the router level.
---

00:04:05:03 - 00:04:15:26
Stefan
I'm wondering why though. Is it because of China's deep seek? What's making it? Why are they
going back on their open source one And there's going to be a lot of stuff from you on this one.
So it'll be interesting.
00:04:15:28 - 00:04:20:24
Jens
Stefan, how do you call the the guy who who runs a news show?
00:04:20:26 - 00:04:22:13
Stefan
An anchor.
00:04:22:15 - 00:04:28:13
Jens
Are you an anchor now? Anchor. Right. Well, you know the film anchor man, I liked it.
00:04:28:15 - 00:04:29:26
Stefan
Who doesn't know the film?
00:04:29:26 - 00:04:32:24
(Mix)
Anchor man
00:04:32:27 - 00:04:41:24
Stefan
You use that quote all the time. The one with the perfume. What is it? It works. Every time, 60%
of the time or something.
00:04:41:26 - 00:04:43:09
Jens
Yeah. But,
00:04:43:12 - 00:04:54:10
Stefan
And then, what's it called when they get that big fight and Steve Carrol’s like, I kill the man with
the trident, and they're like, yeah, you need to, like, lay low. A couple of days like, that was pretty
crazy.
00:04:54:12 - 00:04:56:10
(Mix)
Do you remember that scene?
00:04:56:12 - 00:04:58:21
Jens
No, no, it was long ago.
00:04:58:24 - 00:05:11:11
Stefan
Okay. We'll have to rewatch it on the next retreat, but let's get back into the topic. So for today
on our news channel okay. Why are we bullish on gRPC as the next generation. It actually
comes. Great timing. Because of the LinkedIn.
00:05:11:11 - 00:05:12:24
(Mix)
That we saw.
00:05:12:27 - 00:05:37:09
Stefan
So, what Curtis posted on LinkedIn and gRPC is the federation, future. Let me bring up just the
blog post because I really like the image. But Jens, let's walk us through this like first of all, your
take on Federation, your take on connectors, which we talk about all the time. But why is gRPC
the future?
00:05:37:12 - 00:06:06:15
Jens
So for quite some time we, we more or less I wouldn't say exactly. We kept it a secret, but it's
more like, like we we we have developed a model of thinking in terms of how we think about
federation. And our our take is that I don't think we need more federation or I don't think we
necessarily need more directives or more complex directives.
00:06:06:18 - 00:06:34:27
Jens
I think what we, what we want to have for federation is actually less and less, especially less
complexity. And, one one of the big issues with Federation is you have many frameworks that
are not 100% type safe. And, and even if they are type safe, like go, then you can have
Federation directive that yeah.
00:06:34:27 - 00:07:02:25
Jens
Like requires or some other cases where it's not 100% accurate that you, you need, you would
need very strong guardrails to ensure that your subgraph implementation is actually correct. But
the majority of subgraph frameworks, they are like JavaScript, TypeScript, Ruby, whatever, they
are much, much less strict. And they, they suffer from this problem even more so.
00:07:02:28 - 00:07:24:25
Jens
That means you have like a subgraph, SDL. It follows the GraphQL Federation spec or Apollo
Federation spec, if you call it the spec. And the big problem is, whatever you do, there's very
little that that will that will enforce that the subgraph implementation is right. Like you can have
the subgraph schema and you have the implementation.
00:07:24:25 - 00:07:50:18
Jens
And if there's a difference between the two, or if the implementation is not accurately following
the the spec, then you you won't notice. And so we have quite a customer base and we know
from experience and from, from customer reports and requests what, what enterprises tell us,
it's a serious problem, especially at scale when there's money on the line.
00:07:50:21 - 00:08:18:03
Jens
Because you have to thoroughly review pull requests to ensure that's what you're shipping is is.
Right. So, we were thinking about this problem, and, what we were thinking about is this. So we
have our client, it speaks GraphQL to the router. And then you have the router. And as of Apollo
spec, it speaks GraphQL to the subgraphs.
00:08:18:06 - 00:08:47:04
Jens
If we could move this whole layer of GraphQL from the subgraph into the router, can we remove
this complete level of complexity? And that was kind of like the the idea we had with, gRPC
Federation. The idea is rather simple. You still write the subgraph SDL like before you define
entities and everything like normal, but then you don't implement a subgraph.
00:08:47:06 - 00:09:13:25
Jens
What you do is you take this file and we have a compiler, and we turn it into a gRPC spec. And
this gRPC spec, it will be generated alongside like a mapping file. And a log file. And we can
then tell Cosmo Router that we have a subgraph schema. But the subgraph is not speaking
GraphQL, it's speaking gRPC.
00:09:13:27 - 00:09:43:27
Jens
And then the, the router will handle, will handle the translation between GraphQL and gRPC.
And what that means is, on a high level, every language that supports gRPC, it can now be
used with this approach. And we made sure that, for example, problems like data loading, that
happen at the GraphQL layer, like for entities, we need to batch load multiple entities.
00:09:44:00 - 00:10:10:00
Jens
We take this problem and we move it into the router. And that means typically you would have to
somehow implement a data loader in your subgraph. With this approach we move the data
loader into the router. So nobody has to implement a data loader anymore. You you just
implement this, this, gRPC thing and then you are done.