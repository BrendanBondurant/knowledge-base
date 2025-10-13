---
type: podcast-chunk
title: AI and MCP Overview in Federation Context
slug: ep30-06-ai-mcp-overview-federation-context
series: The Good Thing
episode: 30
chunk: 6
segment: AI and MCP Introduction
timecode: 00:13:28 – 00:17:42
start_time: 00:13:28
end_time: 00:17:42
speakers:
  - Stefan
  - Jens
topics:
  - MCP Introduction
  - AI in Federation
  - Cosmo MCP Implementation
  - AI Hype vs Architecture
tags:
  - ai
  - mcp
  - graphql
  - federation
  - cosmo
  - startup
entities:
  - MCP
  - Cosmo
  - AI
  - Federation
  - WunderGraph
summary: Stefan introduces MCP and AI as key discussion points. Jens shares the early development of Cosmo's MCP implementation, its real-world use, and his skepticism toward current AI hype without solid architecture.
---

00:13:28 - 00:13:43
Stefan
I think it's a good segue, though. So, we have a very fun hire that's going to be joining us on Monday. And the reason why it's fun is our strategy for 2026 is we're going to be at a lot of events. We're going to be at a lot of meetups. So something to keep in mind as we set those out.

00:13:43 - 00:14:09
Stefan
But mark it and set it up on your calendars once those might go out. But yeah, I think you hit on some couple good points there. But for our product roadmap, one of the things also that we've been hearing about everywhere is MCP MCP MCP AI AI AI. And we released MCP actually before Apollo did we have customers using it and they gave us feedback on it and they love it.

00:14:09 - 00:14:24
Stefan
But what is your take on AI in Federation and how is it going to change things and just your overall take on MCP? I know you sent me an interesting blog post yesterday that I read. So it would be good to kind of reference that one, but talk to me a little bit about our strategy with AI and MCP.

00:14:24 - 00:15:03
Jens
Yeah. So when MCP came out, we were like, okay, let's take a look. Let's build something, let's bring it into the market and see what happens. And as loud as other vendors want to shout, there currently is no interesting business model in the world of MCP and GraphQL. You can have a GraphQL schema and you can put MCP on top, and now you have MCP things and you can you can somehow talk to your graph through persisted operations or something.

00:15:03 - 00:15:30
Jens
And the like LLMs are cool like that. There are some, some use cases that are really, really interesting. And at the same time, if I have a really if my graph isn't designed well and if my, if my Federation doesn't work, then your MCP also doesn't work. And I think the biggest problem for, for MCP, that federation can solve is.

00:15:30 - 00:15:52
Jens
We we can we can help you put all data sources together, have like, a centralized governance and integration layer. And through cosmo connect, we can make it super simple to add not just REST APIs but really anything like, even like we can turn a PDF or an Excel spreadsheet into an API. Like anything can be a subgraph.

00:15:52 - 00:16:21
Jens
Now. And so I think that's that's an important point. Governance and access controls and access policies, that's, that's a very big topic and we're investing into that. But ultimately, I think what the federation can give you is the backbone of MCP. It, it, it can be that integration layer. But like, what can you really do on the, on the MCP side.

00:16:21 - 00:17:12
Jens
Like, yeah, you can put an MCP server on top and now an LLm can can talk to some tools. That's nice, but is it like is it worth like the super big hype. And for us, this is something we were thinking about heavily. And one thing we kind of concluded is, if you have a graph and you have MCP, at what point will MCP stop to be efficient in terms of, you know, imagine you have and there's this case studies and I can if you're interested, you can DM me, I can I can give you some some link to some papers, but, there's case studies about the efficiency of LLMs to choose

00:17:12 - 00:17:42
Jens
models, to, to, to choose tools. And the problem is, if you add too many tools, then stuff gets out of hand and the LLM is less and less efficient in choosing the tool. And so one topic that we are currently investing in is if, if I have a question, if I have a prompt, how can I figure out the, the subset of the graph that is relevant to me?
