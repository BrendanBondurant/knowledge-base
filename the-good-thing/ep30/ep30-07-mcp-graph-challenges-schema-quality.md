---
type: podcast-chunk
title: MCP Graph Challenges and Schema Quality
slug: ep30-07-mcp-graph-challenges-schema-quality
series: The Good Thing
episode: 30
chunk: 7
segment: MCP Technical Challenges
timecode: 00:17:42 – 00:20:25
start_time: 00:17:42
end_time: 00:20:25
speakers:
  - Jens
topics:
  - MCP with Large Graphs
  - Schema Documentation
  - Query Generation
  - Schema Governance
tags:
  - ai
  - graphql
  - mcp
  - schema-governance
  - federation
entities:
  - MCP
  - GraphQL
  - Schema Documentation
  - Query Generation
summary: Jens explores how MCP interacts with large graphs, schema documentation quality, and query generation. He stresses schema clarity and governance as prerequisites for meaningful AI automation.
---

00:17:42 - 00:18:16
Jens
And this is a very big problem, because if you if you have a huge graph with thousands of types or hundreds or thousands of types, the next big challenge will be how can I choose? Or how can I create a tool from that graph that really solves my problem? And if you dive into that space, I, I've seen demos from other vendors, and what they do is they take the schema, they give it to cursor, and then they ask cursor to create, to create a query.

00:18:16 - 00:18:44
Jens
And so we investigated this. We, we tried these kind of things out. The performance is really, really bad. And the and the accuracy and often times the problems come from surprise bad documentation. So if you have a GraphQL schema and the the types are not well documented, the entities are not well documented. The fields don't have meaningful documentation.

00:18:44 - 00:19:07
Jens
Imagine the following scenario. Let's say you have the GitHub schema and you, you remove all, all kinds of all, all descriptions, everything. It's just the schema, just types and fields. And let's say you come to the documentation of GitHub and you are not an API expert. You're not a GraphQL expert. You don't know so much about GitHub in general.

00:19:07 - 00:19:40
Jens
And you're like, you know what? I'm I'm interested. I want to see, all my repositories and the amount of stars I have or something. And now let's imagine on the semantic level that there is no end point to give you the amount of stars or maybe GitHub uses different language for that. So you can't just take the entirety of the GitHub steam schema, dump it into into an LLM, and ask the LLM to build a query.

00:19:40 - 00:20:01
Jens
By the way, LLMs cannot guarantee you like that the query will be will be valid, so they have to somehow iterate and validate. And you don't want to pollute the entire schema. You need to figure out what what parts of the schema are relevant for this use case. And sometimes the user doesn't really understand the language of the schema.

00:20:01 - 00:20:25
Jens
So you need to have like a translation layer so that that whole problem of of how can I help someone understand? Because if you want to build a query, it's ultimately about understanding the graph. And so we're currently investing into how can we make it easier for people to, to understand the graph and then take the requirements and turn that into, into, into valid queries.
