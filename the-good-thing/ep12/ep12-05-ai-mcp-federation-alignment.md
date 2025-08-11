---
title: AI, MCP, and Federation Alignment Strategy
slug: ep12-05-ai-mcp-federation-alignment
series: The Good Thing
episode: 12
chunk: 5
participants:
- Stefan
- Jens
segment: Federation and MCP Integration
timecode: 00:14:14:10 – 00:18:23:24
start_time: 00:14:14:10
end_time: 00:18:23:24
speakers:
- Stefan
- Jens
topics:
- Federation and AI alignment
- Supergraph as unified protocol
- MCP challenges with multiple APIs
- API gateway territory for MCP
- Microservices and MCP server scaling
- Authorization and observability concerns
tags:
- federation-ai-alignment
- supergraph-benefits
- mcp-challenges
- api-gateway-patterns
- microservices-scaling
- authorization-concerns
topic_tags:
- federation-ai-alignment
- supergraph-benefits
- mcp-challenges
- api-gateway-patterns
- microservices-scaling
- authorization-concerns
entities:
- Stefan Avram
- Jens Neuse
- JSON Schema
- MCP
mentions:
- politician message delivery joke
- AI struggling with multiple protocols
- SOAP REST OpenAPI Postgres protocols
- uniform interface benefits
- MCP server per team challenges
- AI mutation protection needs
summary: Jens explains how federation aligns with AI needs by providing a unified
  protocol for all APIs, making it easier for AI to work with complex systems. He
  discusses MCP challenges in microservices architectures where every team would need
  MCP servers, leading back to API gateway patterns for authorization, observability,
  and protection against AI going rogue.
---

00:14:14:10 - 00:14:17:29
Stefan
And you can go off the rails for this one. It's okay.
00:14:18:01 - 00:14:31:03
Jens
Yeah. You know, I, I'm sometimes I feel like a politician. I have a message I want to send. You
ask a question I start with, yeah. Thanks for your question and then I send my message.
00:14:31:06 - 00:14:33:02
Stefan
But what's the message you want to send?
00:14:33:04 - 00:15:11:07
Jens
No. Okay. AI and Federation. So obviously obviously I say this so often, I'm not sure can even
be insulting because it's not always obvious. Like, to everybody. Okay, but if you have a super
graph, it means we have all your APIs combined under one protocol. Now with AI, it can be it
can be a challenge for AI to talk to many APIs with many protocols.
00:15:11:10 - 00:15:39:12
Jens
And if you let's say you give AI a task and it needs to talk to ten APIs. And so I think that alone is
a question is a is a challenge. And now imagine AI has to speak ten different protocols like soap
rest open API, Postgres, whatever. I think then then AI will struggle even more.
00:15:39:14 - 00:16:03:24
Jens
And I think it can be much easier for, for AI to do the task. If we had one uniform interface. And
then if we take this a step further, we can say, okay, let's, let's take MCP into consideration. So
model context protocol. So for the for the people who I don't know, I don't even have a good
explanation.
00:16:03:24 - 00:16:30:23
Jens
But for me, MCP is I create a bunch of operations. I create Json schema for them so that AI
knows the input and output, and I add some documentation so that AI can read the description
and notes. Okay, I can call this function and it does some stuff okay. So that's great. So now AI
can use MCP and talk to all my things.
00:16:30:26 - 00:16:58:06
Jens
Now you have a next challenge because it means we will we will actually create an ecosystem
to unify everything to speak MCP. And if you build the microservice architecture we are back in
API gateway territory because do you really want let's say you are you are big like,
00:16:58:08 - 00:17:25:03
Jens
Very big company. And you have hundreds of microservices because you have so many teams.
And these microservices are actually good. So it's it's fine. We're not debating microservices
here. So you have all these services and now AI through MCP should talk to all these services.
Do you want every team to build an MCP server. Which means everybody needs to protect
against AI not doing mutation.
00:17:25:03 - 00:17:54:10
Jens
It's not going rogue. Whatever. You might want to have observability. What about permissions
authorization. So again, like MCP, from my point of view it's just an API user. And for a very long
time, I think many people in this economy and in this API economy, they agree, if you have that
scenario, you should have an API gateway.
00:17:54:12 - 00:18:23:24
Jens
And now you can you can shoehorn this topic and be like, okay, we now create an API gateway
for MCP. But in reality it's just an API gateway and MCP or LLM. It is just an API consumer.
Okay. And so coming back to your question, super graph or Federation and MCP or AI, how
does it fit together.
