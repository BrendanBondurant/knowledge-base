---
title: MCP Gateway and JSON Schema
slug: ep14-05-mcp-gateway-and-json-schema
series: The Good Thing
episode: 14
chunk: 5
participants:
- Stefan
- Jens
- Dustin
segment: MCP Gateway Architecture and Schema Generation
timecode: 00:17:11 – 00:22:00
start_time: 00:17:11
end_time: 00:22:00
speakers:
- Jens
- Stefan
- Dustin
topics:
- Cost transparency in federation architecture
- MCP gateway landing page introduction
- Trusted documents as MCP tools
- Automatic JSON schema inference
- Type-safe LLM tool calling
tags:
- mcp-gateway
- json-schema
- trusted-documents
- type-safety
- cost-transparency
- llm-tools
- protocol-implementation
topic_tags:
- mcp-gateway
- json-schema
- trusted-documents
- type-safety
- cost-transparency
- llm-tools
- protocol-implementation
entities:
- MCP gateway
- Trusted documents
- JSON schema
- GraphQL
- LLM
- Router
- MCP protocol
mentions:
- landing page sneak peek
- MCP protocol implementation in router
- discovery endpoint and metadata
- GraphQL operation to MCP tool conversion
- get product operation example
- input contract definition
- type-safe tool calling
- automatic schema validation
summary: Dustin introduces the MCP gateway, explaining how the router implements MCP
  protocol by converting trusted documents into MCP tools with automatically inferred
  JSON schemas. This enables type-safe LLM interactions where GraphQL operations become
  discoverable tools, with validation ensuring calls comply with the defined contracts.
---

00:17:11:21 - 00:17:38:17
Jens
And this is also where I think Federation or what. Like it's not federation anymore. It's more like
what we're doing with it. It's so powerful to understand who is using what and what is the cost of
using your architecture. Because most of the time, let's say you have your client, you have your
custom built MCP server, you will never understand what is the cost of making of calling a tool.
00:17:38:20 - 00:17:47:11
Jens
And we can make that transparent and we can tell you there's negative impact. So yeah, the
super graph is powerful.
00:17:47:13 - 00:17:53:17
Stefan
I love it.
Let them cook. Let them cook. I really like anybody can make changes. Anyone can run checks.
00:17:53:20 - 00:17:59:04
Jens
We have we have built a landing page I think it's it's not yet live right.
00:17:59:06 - 00:18:02:00
Stefan
No, it's not a little sneak. I we're.
00:18:02:03 - 00:18:03:18
Jens
We're working on it.
00:18:03:20 - 00:18:03:27
Stefan
Okay.
00:18:03:27 - 00:18:04:22
Jens
So so.
00:18:04:22 - 00:18:05:23
Stefan
Today.
00:18:05:26 - 00:18:25:23
Jens
Oh we're we're, we're we're introducing the MCP gateway. And, Dustin built this page, so maybe
you can guide us through. Yeah. Well, what's going on? What are the what are the big concepts,
the big topics. What does everybody need to understand okay.
00:18:25:25 - 00:18:48:26
Dustin
So MCP is a protocol. So that means a server has to implement a protocol. So like so that the
client can speak to to a server. So what we have done in the in other router, we have extend the
capability of implementing a MCP server. And using by using trusted documents, exposing
those operations as MCP tools.
00:18:48:28 - 00:19:20:01
Dustin
And of the nature of an MCP server is it has a discovery endpoint, it has metadata, and it is it
can you provides the the metadata to understand what tools prompts, routes and resources are
available. So what we have built into the into the router and we call it the MCP gateway is a full
integration with MCP protocol over GraphQL.
00:19:20:03 - 00:19:52:15
Dustin
So yeah. So that means we provide tools to discover to discover your graph, grow, a graph to
discover what operation you have, have expose through customer, through trusted documents,
and by connecting all your services. We essentially have we are providing access to your
services through MCP. And if you look at the left side, you get a very, I think, good
understanding of how that will work.
00:19:52:15 - 00:20:24:01
Dustin
You define a graphql operation, let's say a trusted document as a file on the on the file system.
You put that for instance in the operations there. Then we will automatically based on the graph
operation create an MCP tool, export it through MCP protocol. And we also based on your
inputs we infer the right JSON schema so that the end so that the LLM knows how to call that
tool in the type safe way.
00:20:24:03 - 00:21:04:14
Dustin
And we will also leverage this information to validate, once you make a request to the router to
ensure that, this this operation is valid according to according to it generate JSON schema.
Yeah. Schema. So here you see a very simplistic example like someone has exposed a get
product operation. It was exposed to execute operations. Underscore. And then if let's say you
ask for a product price, the llm would be able to figure out that because you have exposed this
method to the LLM, I can call that to get the price.
00:21:04:16 - 00:21:08:07
Stefan
Insane. And you might have.
00:21:08:10 - 00:21:34:11
Jens
Yeah. Just few questions for clarification. You mentioned JSON schema and, like, I know what
you're doing, but maybe we can explain for the for the audience what what is the role of JSON
schema in, in MCP. And what are we doing here to to help people. Yeah. Make it make creating
MCP server is actually easier okay.
00:21:34:11 - 00:22:00:19
Dustin
If you create if you want to expose the MCP tool you need to define the contract. It's called the
input contract. So how what does, an what does an llm has to call the the, the tool in a way that
it's will comply with your contract. So in case of this example here, the LLM has to pass, an
argument, primitive argument of type string.