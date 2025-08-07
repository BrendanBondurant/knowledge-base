---
title: LLM Consumers and Schema-First APIs
slug: ep19-08-llm-consumers-and-schema-first-apis
series: The Good Thing
episode: 19
chunk: 8
participants:
  - Stefan
  - Robert Farr
  - Jens
segment: AI and API Design
timecode: 00:37:10 – 00:42:11
start_time: 00:37:10
end_time: 00:42:11
speakers:
  - Stefan
  - Robert Farr
  - Jens
topics:
  - AI and LLMs as new API consumers
  - Schema-first approach value proposition
  - GraphQL's metadata and introspection advantages
  - API design for AI integration
tags:
  - llm
  - ai
  - schema-first
  - graphql
  - metadata
  - introspection
  - api-consumers
entities:
  - Robert Farr
  - Stefan Avram
  - Jens Neuse
  - GraphQL
  - AI/LLM systems
mentions:
  - AI as API consumer paradigm
  - Schema-first design benefits
  - GraphQL introspection capabilities
  - Metadata-driven integration
summary: |
  Discussion of how AI and LLMs represent a new class of API consumers, highlighting the value of schema-first approaches and GraphQL's metadata advantages for AI integration.
---

00:37:10:22 - 00:37:38:22
Robert Farr
But, it is it is a disrupting factor in terms of now there's a new consumer. Right. And so there is
an opportunity to say, is there a better way for us to expose our APIs than, you know,
handwritten REST, individual, you know, resources or just kind of a pragmatic approach?
There? Can we create a more structured way to provide information so, you know, things like
GraphQL schema was built in day one, right.
00:37:38:22 - 00:38:07:06
Robert Farr
It's schema first approach. I always said REST in Http were kind of schema last, right? So you
know, documenting your API, the contracts, OS, all those things kind of came after the fact
rather than upfront. And there's a lot of power in having that schema because it provides
metadata and information i.e., you know, I'll say the metadata, right, necessary for something to
understand what it is and then how to leverage it.
00:38:07:08 - 00:38:17:13
Robert Farr
So that's that for me is kind of a, that's going to create a pivot point in the industry. It'll be
interesting to see where it lands. You know, over time.
00:38:17:15 - 00:38:23:19
Stefan
Well said there's a lot of interesting points there. Yeah. And you want to dive deeper into those
before we segue into the next one.
00:38:23:21 - 00:38:24:28
Robert Farr
00:38:25:00 - 00:38:49:13
Jens
One, one, one thing I want to say about, Federation is and then that is something it took me a
long while to, to really see that and understand the value in it. If you think about a graph as a
whole and like you said, everybody somehow has a graph of data. The question is how is it
represented?
00:38:49:15 - 00:39:17:02
Jens
And if you have a federated graph and you take a query, what we have built is we have built, a
serverless query planner so that for every query, we can show you how the query plan looks like
and we can analyze all of your query plans so we can build complexity scores for all query
plans. We can, figure out how many fetches are they making?
00:39:17:04 - 00:39:57:12
Jens
And we can, from that, we can create kind of like, Gaussian function, where we see the
distribution of query complexities. And this is something where I think things get extremely
interesting at scale, because if you look at the distribution of query complexities of a large
organization, you can understand, the data access patterns, and you can evolve the graph in a
way, and you can move ownership of, of fields like from one subgraph to another to better
satisfy the majority of your queries.
00:39:57:12 - 00:40:22:09
Jens
So to to better align the graph for its actual usage, because, you know, day one, everybody's in
a good mood. You start with three subgraphs or whatever, and you think you have you have cut
them in the, in the right pieces and then your API consumers come in on day three and they are
like, okay, this is the way we want to access data.
00:40:22:09 - 00:40:47:23
Jens
And then you, you realize maybe you have like a majority of of consumers, they have a query
complexity of ten. And then you have a few consumers, they have a complexity of 30. And
you're wondering what's going on. Why are they behaving differently. What what is our graph
not designed for that. And for me this was an eye opening.
00:40:47:23 - 00:41:15:04
Jens
So we we we had this idea of let's just build it. We didn't know where this is going. We we were
just curious about, okay, how would it look like. And I think the, interesting observation we made
is if you don't have such a graph, if you have Rest APIs, if you have gRPC, if you have just any,
any, API landscape, you will never be able to understand.
00:41:15:07 - 00:41:45:20
Jens
And this is something that were, were I think the there's the power of declarative because if
something is declarative like a graph and you have a query and you have a compiler in the
middle, the compiler can give you statistics and it can tell you how, how are we constructing?
query. And then I think this is really the superpower of having a graph versus Rest APIs.
00:41:45:22 - 00:42:11:22
Robert Farr
Yeah. No, I agree. And it's interesting I always say, right, like new ideas are old ideas. So if you
really, you know, peel the layers back, right? Think about, what databases, what relational
databases did for the industry when they came around. Right. Moving from flat files to now, this
relational model. But if you think about a database, right, you have schema, you have query,
right?