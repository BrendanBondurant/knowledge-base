---
title: Security Checks and Complexity Scoring
slug: ep14-04-security-checks-and-complexity-scoring
series: The Good Thing
episode: 14
chunk: 4
segment: Schema Safety and Query Plan Analysis
timecode: 00:13:10 – 00:17:11
start_time: 00:13:10
end_time: 00:17:11
speakers:
  - Jens
  - Stefan
  - Dustin
topics:
  - Schema Checks
  - Breaking Change Detection
  - Complexity Scoring
  - Query Plan Analysis
tags:
  - federation
  - mcp
  - ai
  - api-design
  - benchmarking
  - bff-pattern
  - cosmo
  - cosmo-router
  - go
  - graphql
  - graphql-federation
  - open-source
  - query-planning
  - rest
  - startup
entities:
  - Federation
  - Schema usage
  - MCP clients
  - BrowserBase
  - Cosmo router
  - Query plans
  - Serverless router
summary: Stefan and Jens discuss how federation's core strength lies in checks and
  breaking change detection, addressing the 20% of MCP use cases where hallucination
  could cause problems. Jens reveals a new product featuring serverless router batch
  query plan generation with complexity scoring algorithms that can analyze performance
  impacts of schema changes across multiple MCP clients.
---

00:13:10:06 - 00:13:12:26
Dustin
And so schema you.
00:13:12:28 - 00:13:17:12
Jens
Schema usage what. Let's give.
00:13:17:14 - 00:13:18:04
Dustin
You session.
00:13:18:07 - 00:13:19:04
Stefan
Yeah. Yeah. Right.
00:13:19:04 - 00:13:44:06
Jens
Otherwise yeah. You know what who's using what etc.. And then you have breaking change
detection. This is a not I mean the defining thing is an MCP server is really just a BFF. And if you
manually built built this BFF, you don't have a real time map where you know, that's clients, in
this case MCP clients, they talk to your backends.
00:13:44:06 - 00:13:58:07
Jens
You don't know that because there's the MCP in the middle with Federation we have schema
usage. So we know that an MCP client is talking to your subgraphs. We know that. So you
cannot break it.
00:13:58:09 - 00:14:19:23
Stefan
So that part right there though you cannot break it. So the CEO of browser Base, he tweeted the
other day that like MCP is great for 80%, but that 20% where it connects and makes sure that
nothing breaks. That's where it hallucinate. And I was talking to you Jens about this, and we
were talking with one of our customers that the power of federation, if you strip it away is
checks.
00:14:19:28 - 00:14:40:15
Stefan
Is is this going to break a client, is this going to break an API? And what I think is so powerful
behind what we're building is that we give you the power of MCP, we give you the power of AI
and generative AI, but we're also making sure that you're not breaking anything. So we
eliminate that 20% where it could hallucinate, it could break because you're running checks
against the schema.
00:14:40:17 - 00:14:52:05
Stefan
It tells you if it'll break it, and then it will tell you if you are going to break it, what you should do
to not break it. And so that's just my non-technical piece I want to add there. I think it's too too
powerful really.
00:14:52:07 - 00:15:30:28
Jens
But that's one more thing because we're talking about checks and breaking changes and
whatsoever. But we're also building a new product. We're not yet talking about it, but it's going to
be amazing. And so this new product, it it knows about. So cosmos already knows that. But so
we know about all your subgraphs. We know your schema. We know all your clients, including
MCP clients and the, the the one thing that we find super interesting is we have built a
serverless cosmos router that is not serving traffic.
00:15:30:28 - 00:15:55:17
Jens
It can it can batch generate query plans. And we were like, oh interesting. We batch generate
query plans. By the way this is open source. Like everybody can just see this on our repo. We're
not hiding this. So you can batch generate query plans. And if you look into them we have
created a very simple algorithm that that calculates the complexity of a query plan.
00:15:55:19 - 00:16:18:20
Jens
And so we can for example, say if you if you have like a sequence and then in the sequence
you have two fetches, they get a certain score. If you have a parallel node and it has to try to to
child fetches, then the parallel to fetches, they have a lower score. Then a sequence of two to to
fetches.
00:16:18:22 - 00:16:44:14
Jens
Because obviously like the sequence is is slower, it has more of a cost. So we have built this
cost function. And now the, the what that you mentioned checks and breaking like breaking
change. Cool. Yeah it's very important. Like it's the foundation. But what I find also like super
interesting is imagine you are making changes to your schema or you're thinking about making
changes to your schema.
00:16:44:16 - 00:17:11:18
Jens
And now you can see, let's say you have 100 MCP clients that use your schema and you know,
their complexity score and you make changes. You move something around in your in your
architecture and you see that all scores stay. They go up by 20%. So that means you you would
now negatively impact all the clients, all the models because it it's going to take longer.