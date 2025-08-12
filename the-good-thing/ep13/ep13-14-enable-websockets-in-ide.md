---
title: Enable WebSockets in IDE
slug: ep13-14-enable-websockets-in-ide
series: The Good Thing
episode: 13
chunk: 14
participants:
  - Stefan
  - Jens
segment: IDE-Integrated Configuration and Documentation
timecode: 00:54:22 – 00:59:01
start_time: 00:59:01
end_time: 00:59:01
speakers:
  - Stefan
  - Jens
topics:
  - OTEL configuration through prompting
  - JSON schema validation reliability
  - Datadog exporter configuration
  - WebSocket subscription support
  - IDE-integrated documentation workflow
tags:
  - mcp
  - ai
  - cosmo-router
  - api-design
  - authentication
  - cosmo
  - go
  - graphql
  - llm
  - rest
  - rust
  - startup
  - telemetry
  - websocket
topic_tags:
  - mcp
  - ai
  - cosmo-router
entities:
  - OTEL
  - Datadog
  - WebSockets
  - JSON schema
  - Cosmo router
  - IDE
  - Absent protocol
mentions:
  - telemetry configuration
  - sampling rate metrics
  - JSON schema validation trust
  - Datadog agent OTLP
  - API key headers
  - WebSocket protocol support
  - authentication from initial payload
  - staying in IDE workflow
summary: Jens demonstrates configuring OTEL metrics, Datadog integration, and WebSocket
  support entirely through prompts and JSON schema validation. He emphasizes the power
  of staying in the IDE without needing to consult external documentation, as the
  system automatically searches docs and validates configurations against embedded
  JSON schemas.
---

00:54:22:26 - 00:54:51:12
Jens
So you see it's a little bit of prompting. But at the same time, I don't need to look into the docs
how to, how to enable OTEL. I just do this little bit of prompting and let's see, what do we get.
So first of all, it wants to look into the customer router config reference. So this loads the Json
schema of our config into the context.
00:54:51:13 - 00:54:51:27
Stefan
Searches the.
00:54:51:27 - 00:55:16:07
Jens
Docs. Now it searches also the docs to get some more info, and it seems like it already has an
idea of how to do it. So that's pretty good. So it adds telemetry here. I don't know if it's right. Like
I'm not an expert in this part, but it will verify that the configuration is correct.
00:55:16:09 - 00:55:20:21
Stefan
It does look right, doc, because when you see the tracing you see the sampling rate metrics.
00:55:20:21 - 00:55:30:09
Jens
Yeah it could be. It could be. So it wants to verify the router config.
00:55:30:11 - 00:56:01:13
Jens
Okay. It it seems right. And this is something you can trust. Because yeah because we have a
Json schema validation that ensures that everything here is correct. And this follows the Json
schema spec. So this is not validated by an LLM. It's validated by my code. And now one one
thing you mentioned is let's see where's our exporter.
00:56:01:19 - 00:56:23:06
Jens
Here. This is our exporter. Right. Okay. Yeah. Change this blah blah blah. Okay. Can you export
the OTEL, tracing to data dog? Dog?
00:56:23:08 - 00:56:31:10
Jens
It could be hallucinating. Now, I'm not sure how it will solve this problem.
00:56:33:26 - 00:56:39:13
Stefan
early.
By the way, after the example, you do have to jump. So we will have to cut the podcast a little
00:56:41:01 - 00:57:05:10
Jens
Okay. We can go very little for, over. It's fine. So what did it do. It edit data dog metadata. And
here it says data dog agent OTLP. So now it, this is cool. It wants to run verify, verify. Yeah. And
so now it's verified.
00:57:05:10 - 00:57:06:21
Stefan
That it's good.
00:57:06:23 - 00:57:40:28
Jens
It seems like this is okay. And it also give me some information about, headers like the API key
and this, so this this, might be very interesting, useful overall. I think this is pretty cool. Just to
give you like another example. So let's say you want to enable WebSocket support. Can you
also enable web socket support for subscriptions.
00:57:41:01 - 00:57:49:08
Stefan
So you just extending the route or just without even looking at the docs, you've added old style
instrumentation, you've added Datadog integration and now you're enabling WebSockets.
00:57:49:08 - 00:58:21:24
Jens
Yeah. You're like okay, I want to enable WebSockets apart. And because we already have so
certain information in, in the context, like our Json, Json schema for the, for the config. So I
know this is right, I think it's right. It looks very right. Like we support the absent protocol, we can
forward headers, authentication from initial payload.
00:58:21:27 - 00:58:46:18
Jens
This all looks good. It now wants to verify again. And, Yeah, it's valid. And sig. Well, it's I find so
powerful about this is you now no longer need to be an expert. Plus, you can you don't need to
go through the docs. You stay in your IDE and you're like, hey, this is my router config.
00:58:46:18 - 00:59:01:07
Jens
I want to do a certain thing. How can I do it? And then it searches through the docs and
everything. So yeah, that's, that's, what we have so far. With MCP, well done.