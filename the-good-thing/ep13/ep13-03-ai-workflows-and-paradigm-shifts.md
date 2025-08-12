---
title: AI Workflows and Paradigm Shifts
slug: ep13-03-ai-workflows-and-paradigm-shifts
series: The Good Thing
episode: 13
chunk: 3
participants:
  - Stefan
  - Jens
segment: AI Mandate Analysis and Development Paradigm Changes
timecode: 00:07:48 – 00:11:22
start_time: 00:07:48
end_time: 00:11:22
speakers:
  - Stefan
  - Jens
topics:
  - Mandatory AI usage at Shopify
  - Developer requirement to understand LLMs
  - Paradigm shift in software development
  - MCP server demo with Claude Desktop
  - API-first development approach
tags:
  - ai
  - mcp
  - api-design
  - database
  - go
  - llm
topic_tags:
  - ai-mandate
  - paradigm-shift
  - developer-requirements
  - claude-desktop
  - MCP-server
  - api-first
  - workflow-automation
entities:
  - Shopify
  - Claude Desktop
  - Cursor
  - MCP
  - Dustin (CTO)
mentions:
  - fundamental LLM understanding requirement
  - Cursor and Claude Desktop tools
  - employee dashboard demo
  - half-minute development time
  - frontend builds itself concept
  - SAP-style user interfaces
summary: Jens explains that understanding AI/LLMs is now a fundamental requirement
  for developers, regardless of personal preference. He describes a paradigm shift
  where APIs become primary and frontends can be auto-generated, using an example
  of Dustin creating an employee dashboard in 30 seconds via Claude Desktop and MCP.
---

00:07:48:00 - 00:07:57:02
Stefan
So using AI effectively is now a fundamental expectation of everyone at Shopify. What do you
think he means by that?
00:07:58:04 - 00:08:27:13
Jens
So we had we had similar discussions like we we don't have such a mandate, right? Yeah.
We're not big enough. Yeah. We had we had similar discussions. And I think the most important
thing and this is like if you work at Shopify or not, doesn't matter. But I think it is now a
fundamental, requirement for a developer to explore and understand how LLMs work.
00:08:27:16 - 00:08:52:06
Jens
And it's not even about like, liking it or not liking it, but understanding the trade-offs. For
example, and then, and I don't know, I think people who, who don't do it, they are missing out
because, you need to install tools like cursor claude desktop. You need to play with them. You
need to understand how paradigms shift because.
00:08:52:07 - 00:09:22:24
Jens
Yes. So earlier today, we had, we had a demo with our, CTO Dustin, who showed us that he
created an MCP server, from a super graph. And then he, he connected it to Claude Desktop,
wrote a single prompt, and Claude desktop built, an entire dashboard with information about all
employees in half a minute.
00:09:22:26 - 00:09:48:25
Jens
No code was required. And it is not about like you can now say, okay, this is simple, blah, blah,
blah, and you can have opinions, okay? But I think what people need to understand is it's a
paradigm shift there's now something new that it is now possible to to do a certain workflow. It
wasn't possible before and you should be aware of it because you're a software developer.
00:09:48:27 - 00:10:15:29
Jens
You should understand what kind of systems are possible, because I think also one one super
important thing here is, in the past you were always thinking that, okay, we have this this, this
architecture of we build the backend, it has a database, we build a front end, we deploy a front
end, and somebody can then use our front end.
00:10:16:01 - 00:10:54:04
Jens
But with MCP and AI and what's currently happening, you you can actually just build the API
because the front end almost builds itself. Yeah. And yeah, of course like not not every front end
builds itself. Like if you build it like, let's say you build a, I know an app for baseball or whatever.
Like it's not that simple, but there are so many apps where all they need to do is show a bunch
of data, create a table, create a diagram, some forms, whatever, like SAP, style user interfaces.
00:10:54:07 - 00:11:22:06
Jens
And now you don't need to code them anymore. And if you if you if, if the user can now describe
what kind of UI they want and it can be built and all we need is, APIs expose through MCP. I
don't know. It's, it's it's a new paradigm and, like it or not, but be aware of how it works and what
it can do.