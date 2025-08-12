---
title: Introduction to MCP and How It Differs from Traditional Tool APIs
slug: ep09-14-introduction-to-mcp
series: The Good Thing
episode: 9
chunk: 14
participants:
- Jens
- Cameron
segment: Model Context Protocol introduction
timecode: 00:50:33:02 – 00:54:05:12
start_time: 00:50:33:02
end_time: 00:54:05:12
speakers:
- Jens
- Cameron
topics:
- Model Context Protocol definition
- Anthropic protocol design
- Client-server architecture
- JSON-RPC communication
- Tool execution differences
- Traditional tool API limitations
tags:
- mcp
topic_tags:
- mcp
- model-context-protocol
- anthropic
- json-rpc
- tool-apis
- protocol-design
entities:
- Model Context Protocol
- Anthropic
- Claude
- OpenAI
- Gemini
- Mixed Role
mentions:
- Claude Desktop implementation
- JSON-RPC communication
- defined protocol standards
- tool execution automation
- function call handling
- prompt iteration cycles
summary: Cameron introduces the Model Context Protocol (MCP) developed by Anthropic,
  explaining how it differs from traditional tool APIs like OpenAI's. He details the
  client-server architecture, JSON-RPC communication, and how MCP automates tool execution,
  eliminating the need for manual function call iteration that exists in other AI
  platforms.
---

00:50:33:02 - 00:50:35:28
Jens
We talked about cursor tools like that.
00:50:37:23 - 00:51:03:02
Jens
Let's talk about MCP. So everybody's talking about MCP. We were talking about okay I can, I
can I can bring files into the context. I can bring websites into the context by writing like add web
into the chat and other things. I can index, websites and documentation. And I can also use this
MCP thing. What?
00:51:03:04 - 00:51:05:04
Jens
What is that?
00:51:05:06 - 00:51:30:13
Cameron
Yeah. So MCP stands for the Model Context Protocol. It was a protocol that was designed by
anthropic. Right now it's being implemented in their claude, models. So with Cloud Desktop or
the cloud API, the super high level basic of what it is is that you have, a client which is the
desktop or is the A is the, SDK.
00:51:30:16 - 00:51:59:24
Cameron
And then you have a server that the model runs. And this the model actually communicates via
JSON, RPC, in order to ask questions. So it's very, very similar to how something like Gemini or
something like OpenAI or Mixed Role actually allows for you to provide it with tools. The big
difference is just that it's, defined protocol.
00:51:59:24 - 00:52:25:17
Cameron
It's a defined method to how to do it remotely without it needing to be, inside, you know, like with
Gemini for example, like it's actually in the stream of the, model execution. So you have to
iterate through the, the response candidates to find the function calls, whereas MCP, the model
will actually take that onus off the user and it will actually call the function.
00:52:25:19 - 00:52:48:13
Cameron
Then the server will return it as opposed to you needing to to act to execute it. Then re prompt
the model again and then run through that whole cycle again. So it's kind of just a way to allow
that communication efficiently and to kind of take the, extrapolate it out some and to set a
defined protocol.
00:52:48:16 - 00:53:27:12
Jens
And so, for those who don't know, in open API, you can define tools and essentially the kind of
the way like it's I find it really interesting how tools is implemented. But you make a request and
as part of the request you also send like which is super expensive, by the way. You send that all
the time, like what tools you have, but so you make a request with the prompt and you also say
like, hello, AI like imagine I had functions like I don't really have functions, but imagine I had and
they can do certain things which I describe here in text.
00:53:27:15 - 00:53:46:04
Jens
So do whatever you want. And if you think one of these functions would be somehow useful to
what you're doing, then tell me to call the function so they send you like a string where they say,
okay, yes. Call the function with the following inputs and you can define the input with the JSON
schema. And so you call the function.
00:53:46:06 - 00:54:05:12
Jens
And then you tell them like okay this is the result of the function call which is like I understand
why the model has to work this way because you can just yeah, it's you can't just have the
model go outside in the world and then call your service because it's, it's it's in the cloud so it
doesn't have access to your, to your computer.