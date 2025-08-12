---
title: MCP Demo - Schema Exploration
slug: ep13-10-mcp-demo-schema-exploration
series: The Good Thing
episode: 13
chunk: 10
participants:
  - Stefan
  - Jens
segment: Live MCP Integration Demo with Cosmo
timecode: 00:36:09 – 00:41:28
start_time: 00:36:09
end_time: 00:41:28
speakers:
  - Stefan
  - Jens
topics:
  - Live MCP demo with Cosmo
  - Schema exploration workflow
  - MCP-enhanced development workflows
  - Prompt-driven API exploration
  - Super graph architecture analysis
tags:
  - schema-exploration
topic_tags:
  - schema-exploration
entities:
  - Cosmo
  - MCP
  - Cursor
  - Super graph
  - wgc (WunderGraph CLI)
  - Studio
  - Subgraphs
  - Router config
mentions:
  - live documentation release
  - npx wgc mcp setup
  - API key configuration
  - schema and subgraph fetching
  - employee service architecture
  - family, availability, mood services
  - authentication and mutations
  - file upload capabilities
summary: Jens demonstrates live MCP integration with Cosmo, showing how to set up
  and use prompt-driven schema exploration. The demo reveals how MCP tools can automatically
  fetch super graph schemas, subgraphs, and router configurations to provide comprehensive
  API architecture summaries through natural language prompts.
---

00:36:09:05 - 00:36:14:05
Stefan
behind.
So this one we kind of wanted to show a demo, which I really like one sec. There's someone
00:36:14:05 - 00:36:17:14
Jens
Me.
00:36:17:16 - 00:36:26:02
Stefan
Sofia just snuck in to grab something and I didn't hear until she was like literally right behind me,
it scared the hell out of me. I was like, well.
00:36:26:04 - 00:36:30:12
Jens
But your your your, virtual background, it it covered it well.
00:36:30:14 - 00:36:35:21
Stefan
Oh, okay. Cool. Yeah. I was literally like. Like I could have touched her. It was so weird.
00:36:35:27 - 00:36:37:18
Jens
We saw. We saw nothing.
00:36:37:21 - 00:36:54:12
Stefan
Okay, cool, cool, cool. But, All right, let's shift into the next topic. I want to talk because we're at
the halfway mark. Let's show off what we were talking about today with MCP and with Cosmo,
and let's just kind of go through it, and we can just kind of explain it to me. You can explain to
me, we can explain it to the audience, and we'll go right into it.
00:36:54:14 - 00:36:56:22
Stefan
Let me know if you want me to share the screen.
Yeah, you can. By the way, today I have to to cut at, at the hour. So we only have 15 minutes
00:36:56:24 - 00:37:05:12
Jens
left.
00:37:05:14 - 00:37:11:12
Stefan
Oh my God. All right. Sorry, guys. It was my fault I started late. It doesn't matter, though. All
right, quick speed run. Let's go. Cosmo.
00:37:11:12 - 00:37:24:05
Jens
Excuse me. I kept prompting you like, hey, we need to start. Okay, let me get this as far as I can
because my screen is left. Okay. You can see him, right?
00:37:24:08 - 00:37:26:24
Stefan
Wait. These docs are already live.
00:37:26:27 - 00:37:32:26
Jens
Yeah, yeah. What? Okay, go. Good. What do you mean?
00:37:32:29 - 00:37:39:16
Stefan
sick.
I thought we were just. I didn't even know that these were live on the website already. This is
00:37:39:18 - 00:37:41:27
Jens
Well, what do you think we're doing?
00:37:42:00 - 00:37:50:24
Stefan
No, I just saw it this morning, and then I find out that the docs, like, 30 minutes later, are already
up on the website. I mean, just shows you how fast we ship it. Go ahead. We got 15 minutes.
00:37:50:27 - 00:38:14:00
Jens
Okay, so let's assume we have cursor installed. I first want to go a little bit through the through
the docs and then we can we can talk a bit about the the implementation details. But one thing I
want to to say about MCP is so they're there there was a debate, a while ago on, on LinkedIn,
on, on.
00:38:14:27 - 00:38:43:23
Jens
Should you just you build an MCP server and wrap your existing APIs, or should you augment
your APIs and build something on top? And so what I tried to do is I wasn't like, okay, let's let's
slap MCP on top of Cosmo. That was not my intention. My intention was more like, let let's let's
look at some workflows and let's try to mcp them.
00:38:44:00 - 00:39:05:26
Jens
Let's try to really enhance them with MCP. And I give you like, okay, this is let's get started. Like
super simple. So setting the context doesn't matter. Schema exploration. This is like a super
simple, case. But here, you see. Okay, we have a prompt. We say we have our super graph. We
have our namespace. Oh.
00:39:05:26 - 00:39:29:02
Jens
By the way, on setting it up. So just for completeness, you, you create this thing and in your
cursor you need an API key. You get this from our studio and then you, you set this up like npx,
wgc, mcp and that's it. That that's all you need to do for for setting it up. Okay. First prompt
schema exploration.
00:39:29:04 - 00:39:33:12
Jens
Very simple. One. So let me go to cursor. Do you see that.
00:39:33:15 - 00:39:38:17
Stefan
Yeah it's here okay. And what repo do you have up. You just have the, the Cosmo mono repo.
00:39:39:04 - 00:39:41:02
Jens
One second.
00:39:41:04 - 00:39:42:29
Stefan
You see it on the left here, Cosmo and then router.
00:39:42:29 - 00:39:58:15
Jens
Okay, cool. Yeah. Just need to close some stuff here. Okay, so we have our first prompt. So we
need to tell our tools what what a super graph to use, what namespace. And then show me the
core features of the super graph.
00:39:58:17 - 00:40:01:12
Stefan
And you do this in the config file, right.
00:40:01:15 - 00:40:31:05
Jens
Yeah. The the config file doesn't really matter at this point. It's more like yeah okay. So you see
MCP wants to call a tool. It wants to get my graph from default okay. We run it. You see here
schema is coming back and it wants to get the subgraphs okay. It wants to get the subgraphs as
well. And even the router config.
00:40:31:07 - 00:40:40:23
Stefan
This is so cool. It's like a what I see is like a human. Okay, let me grab the subgraphs, let me
grab more of the subgraphs. Let me grab the router. I want to understand everything. That's
sick.
00:40:40:25 - 00:41:28:02
Jens
Okay. So now you see the architecture. We have a family service availability mood hobbies the
entity model. So we have the employee type, and we have some features with authentication,
we can find employees products, teammates, mutations, subscriptions, advanced features, file
uploads. So it's a pretty comprehensive summary of what's our API can do. And this is all
coming from fetching the super graph, fetching the subgraphs and our, router configuration,
from the super graph.