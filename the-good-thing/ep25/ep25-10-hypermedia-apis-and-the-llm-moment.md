---
title: Hypermedia APIs and the LLM Moment
slug: ep25-10-hypermedia-apis-and-the-llm-moment
series: The Good Thing
episode: 25
chunk: 10
participants:
  - Stefan Avram
  - Jens Neuse
  - Kevin Swiber
segment: Hypermedia and Siren Introduction
timecode: 00:39:30:26 – 00:44:08:12
start_time: 00:39:30:26
end_time: 00:44:08:12
speakers:
  - Kevin
  - Jens
  - Stefan
topics:
  - Distributed cloud applications and APIs
  - Siren hypermedia type introduction
  - Hypermedia vs HTML comparison
  - LLM and agent API interaction potential
  - MCP UI track and hypermedia patterns
tags:
  - mcp
  - ai
  - rest
  - distributed-cloud
  - siren-hypermedia
  - html-comparison
  - ai-agents
  - mcp-ui-track
  - hypermedia-patterns
  - dynamic-api-interactions
entities:
  - Siren hypermedia type
  - HTML
  - LLMs (Large Language Models)
  - MCP (Model Context Protocol)
  - MCP UI track
  - API agents
  - Hypermedia APIs
mentions:
  - Cloud application distribution
  - Links and forms in API responses
  - Machine-consumable hypermedia
  - Dynamic runtime entity relationships
  - Tool response forms
  - Elicitation and user input
  - Fighting naming conventions
summary: |
  Kevin explains that APIs will persist due to distributed cloud applications requiring network communication. Jens introduces Siren, Kevin's hypermedia type creation, asking for an elevator pitch. Kevin describes hypermedia as APIs with links and forms (like HTML but machine-consumable), noting how LLM interactions are naturally dynamic. He observes hypermedia patterns returning in MCP UI tracks, even without the hypermedia name, showing the concepts' enduring relevance.
---

00:39:30:26 - 00:39:47:00
Kevin
And we, we have our systems living in the cloud now, and, you know, we have, distributed
network of applications that we need to talk to. So it's always going to be APIs.
00:39:47:03 - 00:39:58:10
Jens
You mentioned 1 point. and it it gave me like a curveball. But so you're the creator of siren. We
both know that, Stefan doesn't know what siren is.
00:39:58:13 - 00:40:03:03
Stefan
Yeah, yeah. Well, we're the audience for the audience. Give a give the audience. 30 second
elevator pitch.
00:40:03:03 - 00:40:35:02
Jens
Yeah. You can do that, Kevin. But I kind of thought when when LLMS became more powerful
and when everybody started talking about MCP, I was immediately reminded by, I thought
hypermedia would have been the the right approach to let an and an agent talk to an API. And
then the API tells you what other things you could do and then interact.
00:40:35:02 - 00:40:44:13
Jens
And I thought that's that's the hypermedia moment. And it didn't come like, well, what do you
think about it? And then what is siren again for everybody.
00:40:44:15 - 00:41:14:11
Kevin
So so siren is a hypermedia type. What hypermedia means is, you know, having, basically links
and forms in your API response, so, you know, what you can travel to next, and you know, the
actions that you can take, it's defined, in the response itself, much like HTML, which is a
hypermedia type. So, you know, HTML, you can get links that you can go to the next page, you
can get forms that you can submit.
00:41:14:13 - 00:41:36:05
Kevin
When you talk about a hypermedia API, it's just really presenting that in a way that's, you know,
more easily consumable by a machine. So, you know, when you think of things that are very
dynamic coming from the server side, you know, like, you know, I might not statically know
which entities are related to this entity.
00:41:36:08 - 00:42:13:17
Kevin
Until I do the call at runtime, that's very much where, LLM interactions are today. And I think we
are actually seeing, like, some hypermedia elements, pop into the scene. We probably won't call
it hypermedia anymore. But, you know, the patterns, like we're coming back around to them.
Yeah. With, with MCP, there's this whole MCP, UI, track that's going on right now where they're
talking about how to have like, a tool response come back that essentially has forms in it.
00:42:13:19 - 00:42:33:18
Kevin
So you know what to do next. There's like something called elicitation where you get input from
the user. So like we're we're coming back around to a hypermedia whether we know it or not.
And that's fine. We can take whatever name we want. I've stopped fighting the name thing a
long time ago. You want to call anything?
00:42:33:18 - 00:42:37:20
Kevin
REST. Call it REST. Have fun. Go for it.
00:42:37:23 - 00:43:02:21
Jens
Yeah. No. Like it? It makes sense. And and, Well, one thing I'm curious about, maybe have an
opinion on that, but Will and I think it's actually happening because if you search in Google now
you have the, the I summary and the changes user behavior. That's already proven like there's
statistics that people stop clicking on links.
00:43:02:21 - 00:43:34:06
Jens
And and I have I personally have a feeling that user behavior will change in the sense that we
we open ChatGPT, we ask a question, and maybe it serves the web and does something and
presents us something. And, you now can add your MCP service to, to the chat as well. And, I, I
have a feeling that it's possible that the internet, or at least the internet behavior, it somehow
changes that we're no longer, you know, in the, in the, in the beginning.
00:43:34:06 - 00:43:46:01
Jens
And then you're longer in tech than me, but in the, in the in the early days you had these
registries or what's, what was it called like that were sites that had links like what was the name
directories or something.
00:43:46:04 - 00:43:48:13
Kevin
That link aggregators generic.
00:43:48:13 - 00:44:08:06
Jens
Yeah. So you went to like a page and it has links and everything and you clicked on the links
and then came came Google. Okay. You can search. It takes you to the, to the next pages. And
maybe the next iteration is we're, we're abandoning that as well. And we're just asking
questions. And then we, we we just get the information back.