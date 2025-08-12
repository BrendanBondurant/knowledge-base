---
title: Product Philosophy, Structured Opinions, and the Long Game
slug: ep10-09-product-philosophy-and-long-game
series: The Good Thing
episode: 10
chunk: 9
participants:
  - Stefan
  - Björn
  - Dustin
  - Jens
segment: Future vision and product strategy
timecode: 00:55:13:11 – 01:01:55:12
start_time: 00:55:13:11
end_time: 01:01:55:12
speakers:
  - Stefan
  - Björn
  - Dustin
  - Jens
topics:
  - Team growth and personal impact
  - Federation beyond GraphQL
  - AI as newest client type
  - Multi-protocol federation vision
  - Open source commitment
  - GitHub for APIs vision
  - Customer-driven product development
  - Vision validation through enterprise feedback
tags:
  - ai
  - startup
  - api-design
  - cosmo
  - federation
  - go
  - graphql
  - graphql-federation
  - grpc
  - open-source
  - rest
  - rest-apis
topic_tags:
  - federation-evolution
  - ai-integration
  - multi-protocol
  - open-source-commitment
  - github-for-apis
  - customer-validation
entities:
  - WunderGraph
  - Cosmo
  - GraphQL
  - REST
  - gRPC
  - GitHub
  - Apache 2 License
mentions:
  - Frankfurt working space growth
  - AI as new client type
  - federation protocol agnostic
  - search services integration
  - enterprise version rejection
  - 3 million seed funding
  - API collaboration platform
  - customer workflow research
summary: Stefan reflects on the team's growth from internet strangers to a conference
  room full of people. Jens outlines WunderGraph's evolution beyond GraphQL toward
  protocol-agnostic federation, with AI as a key new client type. He reaffirms their
  open source commitment and reveals their "GitHub for APIs" vision, explaining how
  they validate this through customer workflow research rather than direct pitching.
---

00:55:13:11 - 00:55:39:28
Stefan
Yeah, well said, for me what I had, I think they touched on all the points. But I mean, there's so
much I love about WunderGraph, but there's a special feeling when you get together with a
couple guys that you met for the first time on the internet in a small working space in Frankfurt,
and you take it to a point where you know, you have to get a whole conference room to foster
everybody in, and there's all these small little stories.
00:55:39:28 - 00:55:56:01
Stefan
And so what I love is that all these people that are joining our our vision, they have families and
they have their own lives and us wundergraph. What we built. We get to be a small part of their
life a little moment and hopefully it's a really positive moment. So I love that. And what I hate is, I
wish we could do this more often.
00:55:56:01 - 00:56:10:20
Stefan
I wish, I wish we had 100 million in funding so we can do a retreat every month or something
like that. So that's the only thing I hate. But I'm really excited for the journey that we have going
forward. And then to close this out, because we are almost that time, it's interesting to
understand where we're going as a company.
00:56:10:20 - 00:56:30:00
Stefan
So we started off with this interesting pivot, and we've obviously blown past that. We've added
features that only Cosmo has within the stack. We've built amazing relationships with
companies. We have exciting news coming soon, but from a product point of view and also
company point of view and a technical point of view and a customer point of view, where do you
see the future of WunderGraph?
00:56:30:00 - 00:56:45:09
Stefan
And I'll start with you, Jens, because it's interesting. I don't want to take your mojo of what we
talked about, but the money isn't an infrastructure. Where is the future and where do we see
Cosmo evolving into?
00:56:45:12 - 00:57:14:22
Jens
Great question. So I think, first of all, what we start to see in the, in the market and what we,
what we want to support in the future is, we really like the concept of federation federating data,
allowing many, many clients to talk to many, many different data sources. And then it's not just
clients today like the, the, the newest client on the block, it's AI.
00:57:14:24 - 00:57:51:29
Jens
So I think what we see much more in the future is, is AI interacting with, with a, APIs, with data.
And the best way to have AI talk o talk to APIs is by having a schema. And GraphQL is super
great at designing the, the schema. But at the same time, what what we see in the, in the
market and this really influences our, our long term direction, I would say, we very much double
down on the idea of federation, but we are less and less attached to the idea of GraphQL.
00:57:52:02 - 00:58:20:11
Jens
So GraphQL for us, it is one way to federate. But I think in the future we, we will see more ways
of, of federating different data sources. And a federated graph. It doesn't have to speak
GraphQL. It can also speak REST or maybe it speaks, gRPC on the client side, and also on the,
on the backend side, we, we see more and more demand to connect.
00:58:20:13 - 00:58:50:11
Jens
AI to your graph. We see demand to connect search services. REST APIs, Soap. So we're
heavily investing in in ways of, yeah, making the graph more powerful. All of this under the
umbrella of Cosmo, which means open source Apache 2. We're we're, absolutely against any
sort of license change, or we don't want to have an enterprise version.
00:58:50:18 - 00:59:14:11
Jens
We don't like that idea. If you look at our Cosmo Mono repo, it's still the same thing, like in the
beginning. And it's very successful. I think our our cloud has very reasonable pricing for the
value you get. Our customers are happy. We're very happy with this business model. So, to
every to everybody who doesn't believe in open source and having a source for us, it works
really, really great.
00:59:14:11 - 00:59:43:24
Jens
And, like one thing that keeps coming up in sales calls is that that people say, like, hey, we want
to use your, your, cloud service, but we really like that. It's open source. So in case anything
happens, there's, there's insurance. And also we can always look into the, into the code. So
that's kind of like, what, what we have planned with Cosmo and then we're, we're currently
building a completely new product.
00:59:43:27 - 01:00:06:24
Jens
And this product we we don't yet want to share, like, too many details, but, like, information that
is already public is if you look at the announcement from our seed round. Yeah, we said with,
with the 3 million in seed funding, I it's no joke. I actually looked it up the other day, but
somehow, I don't know.
01:00:06:25 - 01:00:36:09
Jens
No, no, nobody seems to to notice or everybody forgets. But we said with the 3 million and seed
funding, we will be building the GitHub for APIs. So we already like our North Star. It was always
to build a platform to to share APIs, to collaborate, to share SDK, a place where there's
documentation, where APIs can be can be easily discovered, and all these kinds of problems in
the in the realm of collaboration.
01:00:36:12 - 01:01:05:22
Jens
And, the thing is, Dustin and I, in the very early days of, WunderGraph, we actually created the
the the solution for this. There's a blog post where we, where we, published something that
allowed you to, to publish, yeah, to publish API dependencies and share them with other people
and, yeah, we we didn't have any, any market reach.
01:01:05:22 - 01:01:27:05
Jens
We, we didn't have the, the media attention that we, we wanted to have. But since then, I would
say everything has changed. And with Cosmo, we have now such a large customer base that,
really allowed us to take, I would say, our vision. But you you can't just have a vision and build it
out and it will work.
01:01:27:05 - 01:01:55:12
Jens
But what you can do is you can have a vision, and then you work with all these enterprises, that
use Cosmo, and you never talk about your vision. You just ask them about their workflows, their
problems, and how are they doing things today. And step by step, we kind of figured out how our
vision actually kind of retrofits the problems that that our, our, customers have.