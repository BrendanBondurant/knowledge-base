---
title: Registry, Access Control, and Business User Interfaces with MCP
slug: ep09-16-mcp-access-and-business-tools
series: The Good Thing
episode: 9
chunk: 16
participants:
  - Jens
  - Cameron
segment: MCP ecosystem and business applications
timecode: 00:58:12:10 – 01:01:20:10
start_time: 00:58:12:10
end_time: 01:01:20:10
speakers:
  - Jens
  - Cameron
topics:
  - AI model access and control limitations
  - MCP registry and discovery systems
  - Authentication and authorization challenges
  - Official validation and security concerns
  - Business user tool integration
  - Multi-service workflow automation
tags:
  - authentication
  - ai
  - api-design
  - authorization
  - go
  - kubernetes
  - mcp
  - rest
  - rust
  - typescript
topic_tags:
  - ai
  - authentication
  - mcp
entities:
  - MCP Hub
  - Docker Registry
  - Banking APIs
  - Bookkeeping Software
mentions:
  - model access limitations
  - MCP registry discovery
  - official connection validation
  - bookkeeper workflow example
  - multi-bank integration
  - business user interfaces
summary: Cameron and Jens discuss the ecosystem challenges around MCP, including registry
  systems, authentication, and security validation. They envision business-focused
  tools that integrate multiple services through MCP, using bookkeeping as an example
  where users could query across banks and financial software through natural language
  interfaces.
---

00:58:12:10 - 00:58:43:10
Cameron
It's still just processing numbers and vectors and weights. It's not you know, the human brain
can conduct the rest of our body. It can tell our arms and our legs and feet to do things. You
know, today, these models don't have that unless we provide them things like tools through
MCP or, you know, tools through the vertex AI SDK or through OpenAI's SDK.
00:58:43:12 - 00:59:05:26
Cameron
That's I think that's one of the big like things that we have to kind of figure out is how do we give
them access? What do we want to do with that access, you know, and should it be done on the
model level, or should it be done or should it be kept at the user level? So I think that there's still
a lot to figure out there.
00:59:05:29 - 00:59:28:25
Jens
Yeah. Interesting. I mean, one way you could, you could actually go with MCPs. You could tell,
let's say you have like an MCP registry where the model can search for MCPs and then figure
out which one to use. Then you have a new problem, authentication authorization. How do you
do that on the B on the behalf of the user.
00:59:28:27 - 00:59:53:25
Jens
And the other problem is, if you let the model run free and select MCPs on its own, you kind of
want to want to regulate that or verify that. Like then we kind of end up with, with a Docker
situation where we need like a public registry, where where people can somehow validate that
an MCP is actually official.
00:59:53:27 - 01:00:28:19
Jens
So now you could say, okay, you can use the MCP hub, but only the, official connections or
whatever, because I think in general it's it's interesting if, if, if every if every company opens up
like an MCP channel and you want to build integrations and work something out across multiple
like even think about your you're like a bookkeeper and you can have an MCP interface with all
the banks you have and with your bookkeeping software and everything.
01:00:28:19 - 01:00:50:13
Jens
And you can then ask a question like, hey, is this where is the money? Is it here? Is there? Give
me the latest transactions can be can be very powerful. And I think we will we will see new kind
of tools pop up that are not geared towards developers but geared towards, yeah, like,
business, business users.
01:00:50:13 - 01:01:20:10
Jens
And I guess the foundation for that is something like MCP. So it's it's interesting. Last topic
before we wrap it up. Microsoft has announced they they are in the making of rewriting
typescript in go and not in rust. Yeah. Well, what are your thoughts on TypeScript in general?
Also in the context of of AI and yeah.