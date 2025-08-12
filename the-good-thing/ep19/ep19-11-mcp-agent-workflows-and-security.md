---
title: MCP Agent Workflows and Security
slug: ep19-11-mcp-agent-workflows-and-security
series: The Good Thing
episode: 19
chunk: 11
participants:
  - Stefan
  - Robert Farr
  - Jens
segment: AI Agents and Security
timecode: 00:52:08 – 00:58:01
start_time: 00:52:08
end_time: 00:58:01
speakers:
  - Stefan
  - Robert Farr
  - Jens
topics:
  - Building secure agent tools with MCP
  - Agent session exploration and workflows
  - Production safety considerations for AI
  - Security frameworks for AI agents
tags:
  - mcp
  - ai-agents
topic_tags:
  - mcp
  - ai-agents
entities:
  - Stefan Avram
  - Robert Farr
  - Jens Neuse
  - MCP (Model Context Protocol)
  - AI agents
mentions:
  - MCP security patterns
  - Agent session management
  - Production safety requirements
  - Secure agent tool development
summary: Discussion of building secure AI agent tools using MCP, covering session
  exploration workflows and production safety considerations for deploying AI agents
  in enterprise environments.
---

00:52:08:12 - 00:52:11:26
Stefan
There's a lot to unpack there. Jens. Go ahead.
00:52:11:29 - 00:52:12:05
Robert Farr
I.
00:52:12:05 - 00:52:42:04
Jens
Think one one important point is, and it is often discussed context window with LLMW. There's a
limit. And I think, graph code aligns perfectly with, with, allowing an LLM or, or a developer to, to
clearly articulate how much data do I want to expose. And, how can I limit that if you just, you
know, I, I keep seeing the question, do we need MCP?
00:52:42:04 - 00:53:14:04
Jens
I could just use open API. And then there's tools that eat your open API spec and, immediately
turn it into, into, an MCP server. The problem I see with this approach is it's very imprecise. I
think you need to give an LLM very precise instructions. What it can do with a tool, how it can
use it. And then you want to think carefully about what kind of data do you expose and in, in
which format?
00:53:14:06 - 00:53:52:15
Jens
How much data you want to expose. That's one thing. And then another thing that, I think
enterprises should, should carefully think about is, should we now build specific MCP servers
that talk to our internal infrastructure essentially becoming another layer of BFFS, which we just
tried to get rid of with Federation? Or should we take a step back and think about, okay, is now
the right time to build a supergraph, a data graph, a federated graph?
00:53:52:15 - 00:54:17:04
Jens
However, you want to call it, unify. The APIs behind that graph, bring authentication and
authorization into this graph layer, and then have something on top. And then I think this is
where where the ultimate, power comes for, for an organization is if you build this graph, once.
00:54:17:06 - 00:54:17:12
Robert Farr
On.
00:54:17:12 - 00:54:59:03
Jens
Top of the graph, you can build SDKs, you can have JSON, RPC for humans. You can have you
can have MCP for the LLMs. And if you want to build rich web applications, you can have a
relay client talking directly or an Oracle client or Apollo client talk directly to the GraphQL
endpoint. So I think ultimately, yeah, this supergraph layer, I think it becomes the backbone for,
for like a digital enterprise.
00:54:59:04 - 00:55:01:28
Jens
How do you see it?
00:55:02:01 - 00:55:23:07
Robert Farr
Yeah, it gets like, you know, I, I, I agree, I think that's that's one of my big worries. Right. So I,
you know, I, I, I think I've been on record internally saying like MCP is, the future of APIs. Right.
Because our more or more of our API, as we think about APIs, we're going to target the agent
first, right?
00:55:23:07 - 00:55:56:03
Robert Farr
Like how do we how do we build APIs that an agent can leverage and, and then create value
from. But to that end, that's one of my big concern is like, okay. Yeah. Here's another right. You
know, layer in the stack that people have to then craft an MCP API for every microservice or all
that. The value I see in the GraphQL federation, because a lot of the things that we might get
away with for human developers, right, you can't really get away with for an LLM if you give an
LM raw schema, it does a pretty good job.
00:55:56:05 - 00:56:19:27
Robert Farr
But if you get that well documented schema right, it can do a much better job. You know, the so I
would say it's gonna pivot, right? Pivot us to thinking about APIs as schema first and then
implementation rather than implementation. And then you kind of build your build, you know,
generate your OAS spec after the fact.
00:56:19:29 - 00:56:40:04
Robert Farr
You know, that's one I think one of the key powerful things. And then, you know, having that one
layer where now I can sit there and go say, okay, well, here are one of the things I'm playing
with right now is, you know, locally. I'll turn it on. Right. Let's say, hey, turn on the MCP server,
explore the entire schema, execute anything you think you need to execute.
00:56:40:07 - 00:56:55:21
Robert Farr
Right. And so then I start down the path of trying to mimic an agent I'm trying to build. Right. And
I want to see what it's going to try to query the kind of queries it's going to try to run. And then
ultimately I can capture those queries and bake them and say, okay, here's a first class
operation I want to expose.
00:56:55:24 - 00:57:26:06
Robert Farr
So then when we deploy it, you know, these are the specific operations I'm exposing via MCP.
And it comes a very easy kind of back and forth, experience. And that's not something. Right?
That's not something that you can do with rest. I mean, I can give it a set of Rest APIs, and it will
call them, then to package that up right into a very simple query that I then say here, serve that
as MCP endpoint.
00:57:26:08 - 00:57:50:21
Robert Farr
I don't have another tool like that. So I see that that's where we start making, I would say the
effort. Right. The squeeze, so to speak, of, you know, defining schemas upfront, documenting
them while, you know, working through, you know, implementing certain patterns or enforcing
certain standards, at scale across an entire enterprise.
00:57:50:21 - 00:58:01:16
Robert Farr
Right? Building a single kind of super graph, that all becomes worth it, because now you're able
to easily expose those capabilities to the LLM.