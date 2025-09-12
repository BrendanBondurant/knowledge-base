---
type: webinar-chunk
title: Federation Pain Points and Subgraph Complexity
slug: 2025-08-25-02-federation-pain-points
series: WunderGraph Webinars
date: 2025-08-25
speakers:
  - Jens Neuse
  - Stefan Avram
episode: null
chunk: 2
segment: Federation Pain Points
timecode: 00:08:58 – 00:15:30
start_time: 00:08:58
end_time: 00:15:30
topics:
  - Federation Challenges
  - Subgraph Complexity
  - Apollo Federation
tags:
  - federation
  - apollo
  - graphql
entities:
  - Apollo Federation
  - WunderGraph
summary: |
  This segment covers the pitfalls of current federation practices, especially with Apollo Federation. Jens details the overhead of running GraphQL everywhere, the fragility of directives, and the challenge of managing thin subgraph layers at scale.
---

00:08:58:13 - 00:09:30:13
Jens
We have the, the concept of, entities and, we, we kind of, like to say that, the, the key directive
is like, a big enabler, to allow us to build a super graph from multiple, services. And, yeah, we
have seen tremendous success, with companies like, eBay, Paramount, SoundCloud and many
others, who built on top of this, paradigm.
00:09:30:18 - 00:09:57:02
Jens
But what we have also figured out is that there is a couple of, of, problems, with this, with this
architecture. And here, here are some, of of the key issues. Just quick question into into the
round for Dustin or Ludwig or Jessie. From your own perspective, what what have you observed
from talking to customers?
00:09:57:04 - 00:10:06:16
Jens
What what is what is the biggest blocker in adopting federation today?
00:10:06:18 - 00:10:09:14
Jens
Dustin any ideas?
00:10:09:16 - 00:10:16:00
Dustin
So without reading the bullet points, I would say, it's.
00:10:16:02 - 00:10:48:16
Dustin
I think it's super unrealistic to assume that the company that all all departments or all members
of the company, are able to speak GraphQL or and also implement GraphQL on the server side.
So you always have I was a diverse, system. And at some point you also need to bring those,
components into, the super graph or into something that, combines everything together so that
consumption is easier across the company.
00:10:48:18 - 00:11:09:21
Dustin
And this is one of the struggles I have observed, through customers. Everybody understands
and also believes in, in the graph architecture. But this the, the, the, the hurdle to integrate
legacy API's into that system and make it part of a broader ecosystem.
00:11:09:23 - 00:11:36:00
Jens
Yeah. Like yesterday I was on a sales call, with a company with more than 100 subgraphs, and
they have, a large amount of API consumers. If you think about, the front end experience, it
would be extremely hard to build a front end against 100, subsystems, 100 microservices, that
kind of integration, it would be almost impossible.
00:11:36:05 - 00:12:09:07
Jens
That's the problem we solved with Federation. But on the other side, we cannot force everybody
to migrate everything to be a GraphQL subgraph. You have a lot of, legacy APIs, maybe some
some Soap, or maybe you have a mainframe. Maybe you want to integrate a message queue or
a Kafka or anything. And what we also observed is that a lot of our customers, they build
subgraphs as very thin layers around some other system.
00:12:09:09 - 00:12:32:05
Jens
So the front end guys, they really need some extra data. They they like to have that unified API
interface. The, the the one graph. That's a powerful thing. But at the same time, connecting all
these data sources, it's a pain. And you don't want to deploy a subgraph for every little, field,
you add. So that's like too big of the, of the problems.
00:12:32:07 - 00:13:00:05
Jens
Another issue this I have from, from a discussion, with someone working at, like an architect at a
very large, fortune 500 company. Not everybody in the company has the same skill set in
implementing subgraphs, and federation can be quite complex with directives like requires and
others. So how can you help people implement, a service that's actually correct.
00:13:00:07 - 00:13:27:23
Jens
That works how you would expect it and can you, can you build tooling and can you set
guardrails that, that help people? Yeah. Implement subgraphs correctly. Because if you if I have
a subgraph, and I use something like, Apollo Server, maybe not even with TypeScript. I have my
SDL, I have resolvers, and maybe but only maybe this whole thing together is working like I
would expect.
00:13:27:23 - 00:13:53:19
Jens
And then I can have testing and other parts. But this is also something where, we're addressing,
with custom connect, number for this, one, one very big issue is Apollo is the, the main driver in
the, in the Federation ecosystem. And they control a lot of the subgraph frameworks, which it's
it's a good and a bad thing.
00:13:53:19 - 00:14:14:23
Jens
I don't even want to turn this into a rant, but what it absolutely is, if they come up with a new
feature, it can take months or even years until all frameworks really adopt the feature. And so
that means you you have a feature, you implement it in the router, and then all the frameworks
need to adopt it.
00:14:15:03 - 00:14:57:12
Jens
And that's actually, a very long step. And with Cosmo Connect, what we can actually do is we
implement it once in the router and everybody can benefit immediately. And the last part is,
yeah. As I said, Apollo has a lot of control over the ecosystem. They maintain, the, the big
implementations of subgraph frameworks. And what that also means is, if we as wunder graph,
if we think, there should be an amazing feature in, in, in Federation and we implement in our
router, but nobody will ever adopted in the main frameworks for GraphQL subgraphs, we have
no power.
00:14:57:12 - 00:15:30:05
Jens
We have no say by building Cosmo Connect, we can move the responsibility of the subgraph
into the router. Dustin, will talk much more about this. And with that, we're free from this
dependency and we will have a lot more competition. And I think we all agree competition is
good. And, I think we all want more competition in the in the microservice API integration market
because it's good competition, means everybody pushes harder and we build better solutions.