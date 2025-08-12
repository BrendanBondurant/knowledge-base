---
title: MCP Through GraphQL Collections and Access Control
slug: ep12-06-mcp-through-graphql-collections
series: The Good Thing
episode: 12
chunk: 6
participants:
- Stefan
- Jens
segment: MCP Implementation Strategy
timecode: 00:18:23:27 – 00:22:42:22
start_time: 00:18:23:27
end_time: 00:22:42:22
speakers:
- Stefan
- Jens
topics:
- MCP as GraphQL query collections
- Fine-grained access control for AI
- No-code MCP interface creation
- Cosmo router proxy capabilities
- Unified API approach benefits
tags:
- cosmo-router
topic_tags:
- cosmo-router
entities:
- GraphQL
- MCP
- Cosmo Router
- JSON Schema
- Stefan Avram
- Jens Neuse
mentions:
- GraphQL queries as MCP functions
- JSON schema transformation
- mutation control and observability
- no-code query collection creation
- API gateway limitations
- federation investment strategy
summary: Jens explains WunderGraph's approach to implementing MCP through GraphQL
  query collections, providing fine-grained access control and observability. He describes
  creating no-code MCP interfaces where backend developers build subgraphs and create
  query collections that become MCP instances with built-in protection and analytics.
---

00:18:23:27 - 00:18:52:18
Jens
If we build a super graph, we have a single approach. We have a framework of how to how to
bring all our services together. And second, if we have this, we can now create an MCP
interface on top, which is what we are currently doing. So we're currently working on this topic,
where you say, okay, MCP, what is MCP really?
00:18:52:20 - 00:19:30:08
Jens
You have a function or multiple functions. They have a description. They have an input and an
output and input and output is described as Json schema. So actually for me MCP is a
collection of GraphQL queries. Because a GraphQL query can have a description. GraphQL
gives you back Json, the input can be Json, and I can. I can transform the AST of a GraphQL
query in a way that I get the Json schema for the input, I get the Json schema for the output.
00:19:30:10 - 00:20:04:12
Jens
So if I have federation and the super graph and I have AI, I create a collection of GraphQL
queries. And now I can. With this collection, I can give MCp fine grained access to my super
graph. And this MCP, it will go through a proxy. This proxy it can live in the in the Cosmo router.
And this proxy can ensure that let's say a client is allowed to do mutations or not.
00:20:04:15 - 00:20:32:20
Jens
It's we can control what kind of operations it makes. Cosmo router already has observability. So
we know what an agent is doing. And so yeah, now now we have a very good approach to, to
create MCPs and where I think where the real benefit is of course, you can do it without
federation, without the graph and everything, but the real benefit is all backend devs.
00:20:32:20 - 00:21:05:03
Jens
We just tell them build subgraphs and then if you want to create, an MCP interface, you just
create a collection of queries. And this collection, you I don't know, you somehow persist. It's
stored. And now you have an MCP instance. And so we can almost build a no code, low code
way of. Yeah, just open the browser, create a collection of queries.
00:21:05:03 - 00:21:35:17
Jens
And now you have an MCP interface. And it's protected. We have analytics for it. We can see
exactly what kind of calls is AI making. Maybe AI is doing the wrong calls. So, yeah, I think
that's, that's a great match. Can you do it differently. Yeah. Of course. But I think what, what we
kind of need to figure out is so our approach obviously we have, we have huge investments in
federation.
00:21:35:17 - 00:22:12:01
Jens
So we will continue that and our approach and and like what I just said, like take it with the grain
of salt, of course, because, yeah. But even if you're not using our approach, you somehow need
to figure out, okay, I need to take rest. Soap, Postgres, whatever external services, I somehow
need to unify it to put an umbrella on top json, rpc for MCP, I need to add protection.
00:22:12:06 - 00:22:42:22
Jens
Rate. Limiting security authorization and observability. So you have to do it anyways. Yeah. And
that was the question. This so many of these parts like API gateways can do it like. But what API
gateways don't do is they don't unify all the stuff into MCP. And I think creating an MCP by
writing GraphQL queries that's pretty easy.