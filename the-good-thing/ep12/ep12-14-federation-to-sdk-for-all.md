---
title: Federation to SDK Generation for Broader Adoption
slug: ep12-14-federation-to-sdk-for-all
series: The Good Thing
episode: 12
chunk: 14
segment: SDK Generation Strategy
timecode: 00:51:12:00 – 00:54:11:25
start_time: 00:51:12:00
end_time: 00:54:11:25
speakers:
  - Stefan
  - Jens
topics:
  - Federation to SDK
  - Supergraph Schema
  - SDK Generation Patterns
  - JSON Schema Integration
tags:
  - graphql-operations
  - json-schema
  - ai
  - api-design
  - federation
  - go
  - graphql
  - graphql-federation
  - mcp
  - rest
  - rest-apis
  - supergraph
  - schema-ownership
entities:
  - GraphQL
  - OpenAPI
  - SDK
  - MCP
  - JSON Schema
  - Stefan Avram
  - Jens Neuse
summary: Jens proposes expanding federation's reach by generating SDKs from supergraphs,
  moving beyond Relay-only users. He explains how GraphQL operations can become SDK
  functions with JSON schema definitions, similar to the OpenAPI-to-SDK generation
  pattern, creating a uniform platform that opens federation to a much broader developer
  audience.
---

00:51:12:00 - 00:51:40:12
Jens
And I think that's a lot of value because, being able to have a uniform schema with entities,
being able to have clarity what our entities are. So clarity in the domain model and everything
clarity in the, in the descriptions, I think it has a lot of value. But. Theres I think a much bigger
use case.
00:51:40:15 - 00:52:32:17
Jens
And that is okay. You know, all the people who who built SDKs. Yes. Who build Rest APIs for
others to integrate these APIs into the system. Can we create a uniform approach where we
make it super simple to create SDKs from your super graph? Because with that approach, we
could open up federation to not just relay users but to yeah, to, to you know, well, one thing I
kind of realize about the open API community is that a lot of people, they they use open API to
describe Rest APIs, but what API consumers actually want is SDKs.
00:52:32:20 - 00:53:11:07
Jens
So what what we're thinking about is, you know, similar to MCP, if you want, if you want an SDK,
if you want MCP, what really is the difference between because for me, an SDK is generated
code. That's where each does the functions or classes or structs whatever. And I can I can
somehow call a function and it does one thing and then it returns some data.
00:53:11:10 - 00:53:41:25
Jens
So what could we do to turn the super graph into an SDK? We create a collection of GraphQL
operations like MCP. And then we'll because we can describe each operation, we can group
them in folders or whatever and their names. And then each operation, it's, it has an input, Json
schema. It has a response Json schema.
00:53:41:25 - 00:54:11:25
Jens
And then we generate an SDK. And so, so now I think we, we take the concept of federation
and we open it up to, to like, like a whole new surface area and that, that will, that will give so
many people, like something like, like a uniform platform for like, okay, here's our SDK, this is
how we can we can use it.