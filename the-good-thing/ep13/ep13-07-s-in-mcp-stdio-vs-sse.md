---
title: The S in MCP - STDIO vs SSE Security
slug: ep13-07-s-in-mcp-stdio-vs-sse
series: The Good Thing
episode: 13
chunk: 7
participants:
  - Stefan
  - Jens
segment: MCP Security Considerations and Implementation Models
timecode: 00:23:06 – 00:29:20
start_time: 00:23:06
end_time: 00:29:20
speakers:
  - Stefan
  - Jens
topics:
  - MCP security concerns viral Hacker News post
  - Standard input/output vs SSE implementation models
  - CLI security posture analysis
  - Network vulnerability risks with SSE servers
  - Local machine attack vectors
tags:
  - mcp
  - websocket
  - mcp
  - stdio-implementation
  - sse-vulnerabilities
  - hacker-news
  - cli-security
  - network-attacks
  - local-vulnerabilities
entities:
  - MCP
  - Hacker News
  - Medium
  - Cosmo CLI
  - wgc
  - SSE (Server-Sent Events)
  - Claude Desktop
  - Cursor
mentions:
  - viral Hacker News security post
  - "S in MCP stands for security" title
  - JSON RPC over standard IO
  - 0.0.0.0 listening risks
  - WhatsApp MCP server example
  - npm repository attack vectors
  - file system read/write access
summary: |
  Stefan and Jens discuss a viral Hacker News post about MCP security concerns. Jens explains two MCP implementation models: standard input/output (safer, like CLI tools) and SSE servers (more vulnerable). He details security risks of SSE implementations, including network exposure and local machine attacks through npm packages or malicious websites.
---

00:23:06:18 - 00:23:10:13
Jens
Okay. What next? Security.
00:23:10:15 - 00:23:31:19
Stefan
Yeah. Let's talk about this. So this week there was a I'll actually bring it up a hacker News post,
which was the S and MCP stands for security. But actually let me jump into the post. And he
posted it on medium and it went pretty viral on Hacker News. It was on the top page. But yeah,
The S in MCP stands for security.
00:23:31:19 - 00:23:47:29
Stefan
I didn't actually read the post begins. Walk us through what was happening with the post. And
then kind of like the discussion that was happening in Hacker News, as well as obviously the the
oxymoron, the S in MC stands for security. Like what do they mean by that?
00:23:49:11 - 00:23:56:23
Jens
time, but, yeah.
I think the first thing, by the way, I'm not sure how much value we get from just showing it all the
00:23:56:27 - 00:24:00:00
Stefan
I'll jump up. Yeah, I'll jump out. Don't worry.
00:24:00:15 - 00:24:24:22
Jens
So I think the first thing we need to talk about with MCP is there's two models how you can run
an MCP server. So one way is you have an MCP server that runs over, standard input output.
And then there's a second way how an MCP server could run, over SSE. So it actually exposes
a server.
00:24:24:22 - 00:24:52:00
Jens
And now this server is, is subject to whatever you sent there. And whatever people do with it.
And so we have to distinguish these two cases. To give you an example. In our case, we added
sorry, we added an MCP server, to the Cosmo CLI. wgc, And this MCP server, it actually only
supports standard input output.
00:24:52:02 - 00:25:20:13
Jens
So that means you stop the server and then to have it do something, you need to send a Json
RPC message into the standard input, and you get a response via standard output. What this
means in terms of security is I can have a CLI like wGC. It accepts parameters and it returns
data to standard output.
00:25:20:15 - 00:25:52:19
Jens
We're now doing the same thing with MCP, except we're doing it over the MCP protocol. So in
terms of security it runs in the context of the user. And every like if you have permissions to do
things then the MCP CLI has permissions to do things. So it it's exactly the same context. But
we're not exposing a server of sorts or we're not like there's no port open or whatever.
00:25:52:22 - 00:26:29:15
Jens
So in terms of security, it's as secure or insecure as running any other CLI on your computer. So
it's it's not really changing anything to be honest. It's, it's just, we're giving a more descriptive
way or we have a more descriptive way of communicating over a standard input output. So that
is one way of using MCP. And then there's another way of using MCP, which by the way, it's not
yet so widely adopted.
00:26:29:17 - 00:27:16:11
Jens
For example cursor or claude desktop. I'm not sure on cursor actually but cloud desktop we
know it currently doesn't support SSE. Yeah. SsE if you don't know, it's just, like a, a little bit like,
a little bit more fancy way of doing http, with, some, some quirks. You can stream a response,
but other than that, it's, it's actually more or less just Http, and so the problem with this is let's
say you start an MCP server and it, it, let's say it can read and write, write, read and write in
your file system.
00:27:16:14 - 00:28:01:27
Jens
And you start the server with SSE enabled. Yeah. So what now can happen is all, all sorts of
super dangerous things because I can create a website and this website, well, that there might
be content policies, but let's say I can create apps or stuff that runs on your local machine like
an npm repository. And when you run an npm library, I can build something into it that searches
all parts on the local computer and tries to figure out if there is an MCP server listening, and if
there's an MCP server, I can introspect it and figure out what kind of tools does it give me.
00:28:01:29 - 00:28:32:10
Jens
And if there's an MCP server that allows me to read and write in the file system. Yeah. It means
I can now read your files and I can manipulate your computer. So if I have write access to your
computer, I could write a script that runs every time the computer starts and it does whatever I
want. So I now have kind of free access to your computer, and these are super dangerous
things.
00:28:32:10 - 00:28:57:14
Jens
So, yeah, I, I think that, you know, that there's people who build, for example, MCP servers for
WhatsApp, and you can build like MCP servers for whatever. And if you open them up, even on
the local local machine, it's it is one thing. And now you're vulnerable to all sorts of attacks on
your local machine, but maybe you're you're even, doing other mistakes.
00:28:57:14 - 00:29:20:29
Jens
Let's say you create an MCP server, you listen on, 0.0.0.0. So you listen on all parts, let's say
somehow your computer is accessible through the network, even if it's just a local network. It
now means all devices on your local network can find your MCP server. And by finding your
MCP server, they can now read your WhatsApp messages.