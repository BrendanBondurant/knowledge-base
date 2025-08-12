---
title: Building Employee App with MCP
slug: ep14-11-building-employee-app-with-mcp
series: The Good Thing
episode: 14
chunk: 11
participants:
- Stefan
- Jens
- Dustin
segment: Live App Generation with MCP Integration
timecode: 00:43:18 – 00:47:01
start_time: 00:43:18
end_time: 00:47:01
speakers:
- Dustin
- Stefan
topics:
- Prompt engineering to prevent LLM hallucination
- MCP Inspector tool for debugging
- Real-time Next.js app generation
- Tool permission management
- Non-technical prompt requirements
tags:
- mcp
- ai
- cosmo-router
topic_tags:
- mcp
- ai
- cosmo-router
entities:
- MCP Inspector
- Next.js
- Claude Desktop
- Cursor
- Cosmo Studio
- LLM
mentions:
- anti-hallucination prompt instructions
- no mock data or fake endpoints
- focus on exposed tool integration
- JSON schema structure reflection
- HTTP request endpoint details
- 30-second generation time
- tool exploration interface
- developer background requirements
- Tailwind CSS styling
summary: Dustin demonstrates the complete MCP workflow, using MCP Inspector to show
  available tools and their JSON schema structures. He runs a carefully crafted prompt
  that prevents hallucination by instructing the LLM to avoid mock data and focus
  on real tool integration, successfully generating a Next.js employee management
  app in about 30 seconds.
---

00:43:18:18 - 00:43:53:23
Dustin
And there are some important, I would say, prompt instruction. You have to give the LLMS so
that it does not hallucinate, or at least that the that the instructions are clear. It should not use
mock data or fake endpoint. It should not reinvent stuff. It should focus on the integration with
expose a few tools. And yeah, so also important and I wanted to share is one sec there is a tool
called MCP inspector okay.
00:43:53:24 - 00:44:19:18
Dustin
I mean yeah it's allows for for debugging purposes to understand what tools and MCP server
exposes. So before we start, before we run the prompt, I would like to show you what is what
the LLM, will be accessible of. So, it can you see we have exposed three custom operations.
You see here the description that we mentioned.
00:44:19:20 - 00:44:55:08
Dustin
Ignore this. This is just a demo. And here, the what is the update availability operation capable
of. What are the parameters? This is this actually reflects the JSON schema struct. You can
see, for example, my employees this is nested. And but also we also provide an end point that
gives the LLM superpowers to understand how to how to run this operation in, in in a, in a real
world scenario like how does the end point looks like?
00:44:55:10 - 00:45:23:07
Dustin
How how does the HTTP request has to look like in order to make a real and successful request
against the router? So now if we if we now start the the prompt, the LLM has access to all these
tools. And based on our instruction, it will it will make the best decisions. And hopefully we will
create an next js application which we can copy paste into our Cosmos Studio to, to manage
employees.
00:45:23:10 - 00:45:24:06
Stefan
Let's do it.
00:45:24:09 - 00:45:50:18
Dustin
And if you click here again, just a side note, you can also here explore the available tools. And
now let's let's kick it off this can I think this this takes around 30 sec. Maybe if someone has
something to say it's it's the right moment. And here it asks for for permission to get the info of
the operation to understand how to run it.
00:45:50:21 - 00:45:57:24
Dustin
And it would do it for all operation that the LLM thinks it needs access to.
00:45:57:27 - 00:46:10:05
Stefan
So this is pretty incredible. And Dustin, so far you have you tried this with cursor or how come
you prefer claude desktop?
00:46:10:07 - 00:46:26:02
Dustin
I think the, it also works with cursor. But I think for, for demonstration purposes, this, this, this,
this isolated view and the code generation is this, I think it's much more appealing for, for users
here.
00:46:26:04 - 00:46:41:20
Stefan
Yeah. I would say it's a little bit more user friendly. And one of the things me and Jens we're
talking about is like the power of MCP and the power of like just using this and being with the
generator, you still need that developer background and hopefully soon there's a way that we
can kind of go past that.
00:46:41:20 - 00:46:45:27
Stefan
We can just talk to it and build things just like this without having to understand that background.
00:46:45:29 - 00:47:01:08
Dustin
If you if you take a look at the description as a prompt, is really not, if you're if you ignore this
part here, which could be like a base template and only look at this, section. Yeah, there's
nothing technical in it.