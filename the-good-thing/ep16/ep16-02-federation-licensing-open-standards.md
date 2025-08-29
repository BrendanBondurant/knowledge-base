---
title: Federation Licensing Strategy and Open Standards Importance
slug: ep16-02-federation-licensing-open-standards
series: The Good Thing
episode: 16
chunk: 2
participants:
  - Stefan
  - Jens
segment: Licensing Strategy and Enterprise Adoption
timecode: 00:04:30 – 00:09:15
start_time: 00:04:30
end_time: 00:09:15
speakers:
  - Stefan
  - Jens
topics:
  - Federation Strategy
  - Licensing Barriers
  - Enterprise Adoption
  - Open Standards
tags:
  - federation
  - cosmo
  - ai
  - api-design
  - api-gateway
  - apollo-graphql
  - cosmo-router
  - go
  - graphql
  - graphql-federation
  - kubernetes
  - open-source
  - rest
  - rust
  - startup
topic_tags:
  - federation
  - cosmo
entities:
  - Cosmo
  - Federation
  - GraphQL
  - Netflix
  - Apollo
  - FAANG companies
mentions:
  - Ten-year Cosmo adoption vision
  - Large bank and FAANG licensing restrictions
  - Netflix building custom federation gateway
  - Apollo Rust router adoption questions
  - JVM vs Rust technology choices
summary: Jens explains WunderGraph's long-term federation strategy, emphasizing how
  restrictive licensing prevents FAANG companies and large enterprises from adopting
  tools. He uses Netflix's decision to build their own federation gateway instead
  of using Apollo's Rust router as an example of how licensing barriers can force
  companies to create competing solutions rather than contribute to existing standards.
---

00:04:30:14 - 00:05:00:12
Jens
We're betting on federation, the idea of federation. And we, we think it can be it can be loosely
coupled with GraphQL, like GraphQL can be there. But it can be like any federation, like API
federation. But yes, if we're thinking long term, we're like, okay, in ten years from now,
everybody should be using Cosmo. Everybody should be using our federation.
00:05:00:15 - 00:05:34:27
Jens
If we make it somehow hard for companies to adopt it, that's not going to happen. And, from my
previous job, I worked together with very, very large banks, and I worked together with with
other companies where I knew how they, how they work with, with open source, also Faang
companies. And what I learned is if you put certain licenses on your, on your software, then
they, they cannot adopt it, they cannot use it.
00:05:35:00 - 00:06:11:27
Jens
So imagine federation wins in the long term. So that that goes through. But we made some dual
license bullshit or whatever. And so what a Faang company could now do is they could fork
Cosmo or fork Federation, fork Apollo or build their own, for example, Netflix, because of the
behavior of Apollo, has built their own Federation Gateway. And, well, I don't know the the
internals allegedly.
00:06:11:29 - 00:06:33:00
Jens
I cannot speak about the the internals. I can only speak about like, hear say and, you know, but,
Netflix is very big on the, on the Java virtual machine, so, so it made sense for them to, to build
their own gateway. But now you could ask yourself, okay, why didn't they adopt the, the rust
router from Apollo?
00:06:33:00 - 00:07:06:06
Jens
Shouldn't it be the most performant one? Yeah. The the answer is probably somewhere in the
area of. Yeah, maybe they couldn't use rust in the in the company. But you could also ask
yourself, why would Netflix invest their developer time to build their own gateway on top of the
JVM when there's a standard already? And you could also think about, okay, maybe it's it's
actually about the licenses, which is also a likelihood.
00:07:06:09 - 00:07:32:17
Jens
And so to summarize this licensing topic, if we are betting on federation and if we're betting long
term, we don't want companies like Netflix to build their own. And then we have an, an
ecosystem, where everybody has their own thing. But rather we want to be the standard. So I
think the, the only way to get there is by building, by becoming the standard.
00:07:32:17 - 00:07:39:07
Jens
So it, it must be on a liberal license.
00:07:39:09 - 00:08:09:11
Stefan
I agree, but one question that I was thinking about during the podcast is like being the standard.
Okay, so like Epic Games, like Unreal Engine, like if you're an indie developer, that's the
standard. But let's take Salesforce for example. So Salesforce is not open source, but they are
the standard CRM. Do you think it was because of the timing where they just completely just
grew really fast, or their literal Salesforce and getting into companies early on and just growing
or like, how are they the standard, the CRM, but they're proprietary software.
00:08:09:11 - 00:08:17:04
Stefan
What's the balance between being the standard proprietary and being the standard and open
source? Does that make sense?
00:08:17:06 - 00:08:38:03
Jens
I would say one one big difference here is, is, what what kind of solution are we talking about?
For example, Federation. We, we, we have this in the category of, of it's a platform tool. It's a
tool to build a platform like an API gateway, like a proxy like Kubernetes. You I wouldn't compare
us to a Salesforce.
00:08:38:03 - 00:09:05:22
Jens
I would more, compare us to, to like for example, do you think Kubernetes would have been a
success if it was closed source? Kubernetes? You can now, you know, you can now build a
Kubernetes cluster in Azure, GCP, AWS and some smaller players. So there is a standard. How
was it possible the the big players worked together.
00:09:05:22 - 00:09:15:11
Jens
They, they collaborated and they it's a standard. This would have never happened if it wasn't
open source.