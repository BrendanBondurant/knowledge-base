---
title: Demo Setup and Persistent Operations
slug: ep14-09-demo-setup-and-persistent-operations
series: The Good Thing
episode: 14
chunk: 9
participants:
  - Stefan
  - Jens
  - Dustin
segment: MCP Configuration and Trusted Document Management
timecode: 00:34:58 – 00:38:24
start_time: 00:34:58
end_time: 00:38:24
speakers:
  - Stefan
  - Dustin
topics:
  - Demo Setup
  - Persistent Operations
  - Trusted Document Storage
  - Safety Controls
tags:
  - trusted-documents
  - mcp
  - ai
  - api-design
  - cosmo-router
  - go
  - graphql
  - rust
topic_tags:
  - demo-setup
  - persistent-operations
  - trusted-documents
entities:
  - MCP server
  - Trusted documents
  - Storage provider
  - Router URL
  - Find employees operation
  - GraphQL mutations
  - JSON schema
mentions:
  - operations directory storage
  - MCP endpoint path defaults
  - graph name suffix configuration
  - full schema exposure options
  - arbitrary operation execution
  - mutation exclusion for safety
  - domain vs localhost hosting
  - search filters for employees
  - comment incorporation into schema
summary: Dustin demonstrates MCP server configuration, showing how to set up storage
  providers for trusted documents, configure ports and endpoints, and manage safety
  options like excluding mutations. He introduces the find employees operation as
  an example, highlighting how comments become part of the JSON schema and how various
  filtering options like nationality and pet ownership can be configured.
---

00:34:58:28 - 00:35:15:27
Stefan
Yeah. Well Said. So I do want to be conscious of time. So let's scroll down a little bit here and
understand, the available AI tools. And then Dustin, I would love to get into the demo so we
could just kind of speed run through these. But talk to me a little bit about these available AI
tools or the MCP shortcuts as I call them.
00:35:15:27 - 00:35:16:26
Stefan
What do they do?
00:35:16:28 - 00:35:19:24
Dustin
I would say I can, present them in the demo.
00:35:19:26 - 00:35:39:04
Stefan
Oh, okay. Perfect. So, guys, this landing page isn't live yet, but you can see here these are all of
the kind of, AI tools that we have integrated with our MCP. And Dustin will demonstrate it
actually in the demo. So let's switch over to that mode. Give me a second. And give it a sector
render Dustin. Because it would render in 4K.
00:35:39:04 - 00:35:59:03
Stefan
But maybe if you can make it a little bit bigger it would be great. Okay, that might have been too
big, but I think that looks good right there. But feel free to kind of just demo us for it and walk us
through it. And then Jens, just feel free to put questions into there. So that way the audience can
understand exactly what we're doing, but Dustin take it away.
00:35:59:05 - 00:36:29:29
Dustin
Okay, good. So as we discussed, like, the way how to integrate tools or exposing operations to
the MCP protocol is to creating persistent operations, trusted documents. So it is it is up to you
where you want to store them. So in that case, we have defined the storage provider with the id,
MCP, and we choose operations there as the directory to where you could be able to store the
operations and there are a few options you can choose from.
00:36:29:29 - 00:37:00:22
Dustin
You can define on what port the MCP server should be available. It is not possible to define the
path because in the later specification, the, the the protocol recommends to to expose the
endpoints over the MCP / MCP endpoint. And I think this is a good default for the start. You can
you can define the graph name to specify or you give your MCP a, server name as is a suffix.
00:37:00:25 - 00:37:26:24
Dustin
And then the two other, multiple other option, you can expose the full schema to the MCP. But
what we usually do not recommend because, the recommended approach is to expose specific
operations. But this might be useful, useful for exploration or development. Then you can also
enable the executing of, arbitrary operations, which will expose an execute graphql tool.
00:37:26:26 - 00:37:55:19
Dustin
And you can also exclude mutations from your expose trusted documents for safety reasons.
And last but not least, we also expose the router URL because sometimes you might have or I
think often your expose your router are not through localhost but on on on the domain. Yes. So
so that means in that case your, your tooling, you MCP tooling will be aware of where your
router is actually hosted.
00:37:55:22 - 00:38:24:02
Dustin
So it can do real API integration. All right. So this has been already started that let's take a quick
look about the three operations we provide. And operation to to find employees. We have a
search input which accept multiple filters like search filtering by has pets nationality. It also has a
comment, which is pretty important because we will incorporate that into the JSON schema.