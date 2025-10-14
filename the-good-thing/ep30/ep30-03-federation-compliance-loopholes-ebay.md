---
type: podcast-chunk
title: Federation Compliance Loopholes Revealed Through eBay
slug: ep30-03-federation-compliance-loopholes-ebay
series: The Good Thing
episode: 30
chunk: 3
segment: Real-World Federation Problems
timecode: 00:07:47 – 00:09:31
start_time: 00:07:47
end_time: 00:09:31
speakers:
  - Jens
topics:
  - Apollo Federation Issues
  - Authorization Loopholes
  - Compliance Risks
  - Subgraph Communication
tags:
  - federation
  - graphql
  - apollo-graphql
  - compliance
  - security
  - open-source
  - cosmo
entities:
  - Apollo Federation
  - eBay
  - Cosmo
  - @requires directive
summary: Jens explains real-world problems in Apollo Federation revealed through eBay collaboration, including authorization loopholes in `@requires` and compliance risks in subgraph communication.
---
00:07:47 - 00:08:32
Jens
Because if you look at what we recently built with, with, eBay, it's actually quite interesting because, thanks to eBay, we can solve problems in Federation that you don't even know exist. And we solve them today, for you to use tomorrow. So to give you one example, eBay has a use case where if you have a very sensitive piece of information in your in your graph for example, when a listing on the eBay page ends or something, because you, you don't want to tell everybody when, when the listing ends because it, it could be used for market manipulation or whatever.

00:08:32 - 00:09:04
Jens
So the problem here is Apollo introduced the requires directive and again like not negative against Apollo. But the point is if you introduce such a directive you need to think about the, the the consequences, the repercussions. And what are the effects of using such a directive? In our case, what we figured out through eBay is when one service has a sensitive field and another service says through.

00:09:04 - 00:09:31
Jens
The requires directive. I want to have that field to resolve another field, unknowing of the other service. Another team now has access to that field. So if you try to follow compliance regulations and one service, is, I would say like audited and is compliant and now another service can just request that field. You might not even be aware of that.
