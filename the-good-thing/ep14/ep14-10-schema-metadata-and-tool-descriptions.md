---
title: Schema Metadata and Tool Descriptions
slug: ep14-10-schema-metadata-and-tool-descriptions
series: The Good Thing
episode: 14
chunk: 10
segment: Documentation Integration and LLM Context Enhancement
timecode: 00:38:24 – 00:43:18
start_time: 00:38:24
end_time: 00:43:18
speakers:
  - Dustin
  - Jens
  - Stefan
topics:
  - Schema Metadata
  - Tool Descriptions
  - Documentation Integration
  - LLM Context Enhancement
tags:
  - graphql
  - mcp
  - ai
  - api-design
  - cosmo-router
  - go
  - llm
  - rest
entities:
  - GraphQL schema
  - JSON schema
  - MCP introspection endpoint
  - Claude Desktop
  - Next.js
  - Employee dashboard
  - OSS repository
summary: Dustin explains how GraphQL schema comments are automatically processed and
  incorporated into JSON schemas for MCP tools, with Jens emphasizing the critical
  importance of good documentation for LLM precision. They demonstrate Claude Desktop
  configuration and introduce a demo where Claude will create a Next.js employee management
  dashboard based on exposed MCP operations.
---

00:38:24:02 - 00:38:48:19
Dustin
As discussed before, we will have update update availability to update. Yeah. The the
availability of an employee by ID. And we can also update the moods of an employee. So pretty
pretty funny example. They are coming from our demo and in the OSS repository. You can
essentially try it out yourself. Yeah. So the next step is to start the raw data, which we have
already done.
00:38:48:21 - 00:38:49:25
Jens
One second.
00:38:49:27 - 00:38:51:02
Dustin
Yeah.
00:38:51:04 - 00:38:59:18
Jens
Can you go back to the operations. You can go back to the operation that has this comment.
00:38:59:21 - 00:39:02:09
Jens
Yeah. Here. This is in the schema right.
00:39:02:12 - 00:39:03:15
Dustin
Yes.
00:39:03:18 - 00:39:06:18
Jens
Okay. What are you doing with it.
00:39:06:20 - 00:39:35:00
Dustin
So when we, convert or when we walk through the GraphQL document, we will verify if there are
any comments on these nodes. And when we find them, we will while creating or while walking
over the document we will also create a nested schema. So the document and we will
incorporate this information into the into the field description field okay.
00:39:35:00 - 00:39:45:10
Jens
So this will be in the JSON schema in the OpenAPI spec that we expose through the MCP
introspection endpoint.
00:39:45:12 - 00:39:46:21
Dustin
Exactly.
00:39:46:24 - 00:40:14:05
Jens
Okay. This is super important because you know, everybody is lazy. Everybody is like, oh, like I
don't care. I don't want to document my stuff like code documents itself. No it doesn't. And
here's the thing. If you put good documentation into your into your GraphQL schema, we
automatically stick that into your, into the, into the JSON schema for your MCP server.
00:40:14:07 - 00:40:34:21
Jens
And now AI can can introspect this. And it now can better understand what what is possible. So
by writing good documentation on the schema you allow LLMs to be more precise to better use
your GraphQL API.
00:40:34:24 - 00:41:12:01
Dustin
Yeah 100%. And this one it shows how to how we just add the documentation to the tool
description. So because my operation has used find employee and we have added a comment
here, this will serve as a tool description for the MCP tool. And if you would have here multiple
root fields. What we can do in graph ql, then we would combine this into one big chunk of
description, which then the LLM can use to to get the most of it.
00:41:12:03 - 00:41:13:25
Dustin
Yeah. So we have three operations.
00:41:13:27 - 00:41:26:01
Jens
Sorry, sorry for the interruption. I just I love these little details because it you know for LLMs
context is key. Everything you can tell it.
It will be.
00:41:27:04 - 00:41:30:18
Jens
It will be easier for the model to help you.
00:41:30:20 - 00:41:33:14
Dustin
Exactly.
00:41:33:17 - 00:41:36:15
Stefan
Okay. So continue this is this is pretty sick so far.
00:41:36:18 - 00:41:47:20
Dustin
Yeah. So I we have the operations. We have two demo config. We started the router. Now we
can try to connect it with claude desktop.
00:41:47:22 - 00:41:53:27
Stefan
great.
So give it a sector render distance a little bit blurry for me. And if you could zoom in that'd be
00:41:54:00 - 00:42:14:15
Dustin
Yeah. So, unfortunately, the integration of MCP is, I would say, more developer focused. So
essentially you would need to go to settings, the, developer, then you would need to configure,
your MCP in. Yeah. As a JSON. We will soon publish the documentation around this. It's just
copy paste and then you are good to go.
00:42:14:15 - 00:42:24:21
Dustin
But you also need to restart claude desktop once you have configured your, your, configuration.
Okay. Let's not it's not visible. Right. So,
00:42:24:24 - 00:42:28:06
Stefan
Can you zoom in just a little bit. Make it a little bit bigger.
00:42:28:12 - 00:42:30:09
Dustin
Zooming is not possible here okay.
00:42:30:11 - 00:42:38:06
Stefan
You can make it like the control X like on Mac to make it zoom in. Oh see. Yeah. Ctrl or
command X okay.
00:42:38:09 - 00:42:39:08
Dustin
Awesome.
00:42:39:10 - 00:42:48:11
Stefan
There you go. Look at me. I'm teaching my CTO about some tech stuff. Give it a sector render.
But, Okay, I see the prompt. It looks good.
00:42:48:13 - 00:43:18:15
Dustin
So we have prepared a prompt. The prompt what what what what did we instruct, claude to do?
It should create an next js app that visualize the most important data of our employees and but
also allow us to manage them. So that means based on the expose operations through the
MCP protocl the LLM creative to building a dashboard to main to manage your employees.