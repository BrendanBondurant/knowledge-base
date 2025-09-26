---
type: podcast-chunk
title: Prompt-Driven Router Configuration
slug: ep13-13-prompt-driven-router-config
series: The Good Thing
episode: 13
chunk: 13
segment: AI-Powered Router Configuration and MCP Workflows
timecode: 00:50:04 – 00:54:22
start_time: 00:50:04
end_time: 00:54:22
speakers:
  - Stefan
  - Jens
topics:
  - Router Configuration
  - JSON Schema Validation
  - Composition Checks
  - OTEL and Tracing
tags:
  - router-configuration
  - json-schema
  - composition-checks
  - ai
  - composition
  - cosmo
  - cosmo-router
  - federation
  - go
  - graphql
  - graphql-federation
  - llm
  - mcp
  - supergraph
  - telemetry
  - persisted-operations
entities:
  - MCP tools
  - JSON schema
  - Cosmo router
  - OTEL
  - Datadog
  - Router config
summary: Jens provides an overview of the comprehensive MCP tool ecosystem, explaining
  how AI can iterate through workflows using verification checks and composition validation.
  He demonstrates how JSON schema embedding enables prompt-driven router configuration,
  showing a request to enable OTEL metrics and tracing with potential Datadog integration.
---

00:50:04:02 - 00:50:07:22
Stefan
If you query now for age, it'll pop up right on the playground.
00:50:07:23 - 00:50:10:19
Jens
No, no, we haven't changed the schema okay.
00:50:10:22 - 00:50:12:15
Stefan
But we just made a proposal on a change.
00:50:12:15 - 00:50:16:28
Jens
Yeah, exactly. Yeah, we just checked, how could it be possible, etc..
00:50:17:01 - 00:50:35:07
Stefan
Insane. And what's cool though, I'm a front end developer and I do the dream query workflow. In
the old days I'd have to go and tell my backend developers, hey, can we add this field to this
type? So that way that I can query from the front end. Now they can just do it with MCP and it
gets checked with Cosmo and then they can approve it, basically providing governance on top.
00:50:35:12 - 00:50:36:25
Stefan
It's sick.
00:50:36:27 - 00:51:10:01
Jens
But and here's the thing. And this is I think it's so important for everybody to understand like the
impact of of MCP. But, here are all the tools we have available list subgraphs, get subgraphs,
introspect subgraph, subgraph, verify schema changes so that the AI can iterate. And we can
we can run these checks. Then for the super graph list Supergraph fetch super graph fetch
super graph router config fetch super graph subgraphs, and then for schema evolution.
00:51:10:21 - 00:51:38:05
Jens
The schema change proposal workflow. Actually, it's not really doing anything. All it does is it. It
prints out a playbook for the AI. What to do and which tools to use to go to a proposal. And then
the stream query, workflow which is essentially also just text that tells the LLM what to do. And
then very powerful verify query against remote schema, verify query against in-memory
schema.
00:51:38:12 - 00:51:59:23
Jens
This is kind of like what kicks the workflow off. Because in the beginning you have a query. It's
not working. So you verify that. And this is what I think people need to understand with MCP,
you need to build workflows where AI can iterate so it can start with something, it can try
something and then you tell it, okay, try a schema design.
00:51:59:23 - 00:52:19:11
Jens
But run this check workflow to verify your work, and then it runs the check workflow to check. It
will run our composition library behind the scenes and other checks, and it will tell you what is
wrong. And then you can iterate based on this information. And yeah, this makes this workflow
happen. Change log. Another one.
00:52:19:11 - 00:52:45:18
Jens
And this is also something I wanted to show you. Verify router config and cosmos router config
reference. So this is essentially we have embedded the Json schema specification for our router
config into this tool. Yes. We also have documentation search but. By embedding the Json
schema, we can we can do a really cool thing. So I show you something.
00:52:45:18 - 00:53:02:17
Jens
So here is my config. You see very simple config okay. Yep. lets do something. So, yeah. Tell
me what you want to enable on your custom router because you're, you're not an expert. You
are, you are a good guinea pig.
00:53:02:20 - 00:53:09:08
Stefan
Yeah. This is not bad. So, like, maybe like OTEL. I want to, because that work.
00:53:09:10 - 00:53:28:21
Jens
Okay. So, hub me to enable OTEL metrics and tracing. In my COSMO router.
00:53:28:24 - 00:53:38:06
Stefan
And one step further. So if I wanted to pipe this information of otel metrics and tracing from the
Cosmo router to Data dog, could I also ask it? And it would tell me like how I would do that.
00:53:38:09 - 00:54:22:24
Jens
But I don't know. Depends on the model. Let's let's go step by step. So enable otel metrics and
tracing into the router. And then we say my config is this. And then we say oops new. Okay.
Config. Look into the Cosmo router reference and the docs to find information. And then we say
make sure to verify the correctness of the config.