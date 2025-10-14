---
type: podcast-chunk
title: AI and LLM Integration with gRPC Subgraphs
slug: ep30-12-ai-llm-integration-grpc-subgraphs
series: The Good Thing
episode: 30
chunk: 12
segment: AI-Friendly Federation
timecode: 00:37:47 – 00:42:51
start_time: 00:37:47
end_time: 00:42:51
speakers:
  - Jens
topics:
  - gRPC for AI
  - LLM Handler Generation
  - Apollo Connectors Comparison
  - Subgraph Integration
tags:
  - ai
  - grpc
  - cosmo-connect
  - federation
  - graphql
  - llm
entities:
  - Cosmo Connect
  - gRPC
  - LLM
  - Apollo Connectors
  - Subgraphs
summary: Jens explains why gRPC makes Federation AI-friendly: LLMs can easily generate gRPC handlers, unlike Apollo Connectors. Cosmo Connect was intentionally designed for LLM-assisted subgraph integration.
---
00:37:47 - 00:38:15
Jens
So with Cosmo Connect you have a plugin. And this plugin runs with the router. So kind of zero overhead. It's super cheap. And this plugin it's kind of like behaving like a subgraph. Except you don't need to know anything about GraphQL. You don't need to know anything about Federation. There's no keys. There's no directives. It's it's just pure gRPC.

00:38:15 - 00:38:42
Jens
Stefan, question for you. If you have something that is very simple, a very simple interface, and it can contain custom logic and this custom logic, it can contain whatever we want. It is very simple to implement. It is very easy to test. And it's very quickly to, to actually write that just a little bit of code because there's no framework, nothing.

00:38:42 - 00:38:53
Jens
It's really just gRPC. What, what kind of modern cool solution could we hand this to do nice things?

00:38:53 - 00:38:57
Stefan
Sounds like AI maybe an LLM. Cursor.

00:38:58 - 00:39:29
Jens
This and this is intentional. So what we were thinking of at the very beginning is what is the next wave of building graphs, and how can we add more capabilities to our graph and one big blocker we found is everybody has a lot of legacy. They have Rest, API, Soap, APIs, databases, whatever, like just old services. Nobody wants to touch them and somehow we want to onboard them to the graph.

00:39:29 - 00:40:03
Jens
So what we did is we intentionally created Cosmo Connect as a system where the interface is so insanely simple, so dumb. It's just a gRPC proto that an LLM can easily, with a little bit of system prompting and guidance, an LLM can easily implemented if you take an Apollo Federation subgraph. I tried to to implement subgraphs with LLMs.

00:40:03 - 00:40:26
Jens
Yeah. The the results are mixed. Sometimes it works. Most of the time something is wrong. So I have to iterate. So that means me as the driver. I have to understand federation. And I want to create a system where the the driver, the integrator doesn't have to understand federation. So ideally I can just take a schema, run it through a compiler and then ask cursor to to implement that.

00:40:26 - 00:41:00
Jens
And this is how we designed, how we designed Cosmo Connect because with with the approach of what, what what Apollo did with, Apollo connectors. So you have these directives in the schema, and there's very, very few, like in the, in the global, in the global scheme of text available online, like the the amount of GraphQL schemas with Apollo Connect directives is like like zero like it.

00:41:00 - 00:41:26
Jens
You will not find it in the training data. So that means LLMs will never really understand how how Apollo connectors work because it's a custom solution. So the only way you got to an LLM to, to do, to do Apollo connect right. Or Apollo connect to to to to do it right is through system prompting and iteration and other things.

00:41:26 - 00:41:54
Jens
And it's never going to be efficient. So our approach here is with, with Cosmo connect we just have gRPC. So we, we remove GraphQL, we remove entities and everything. We just have a proto and we tell the lamb, hey, here's a protocol. And in this handler we want to make a call to a rest API. Here's the open API spec.

00:41:54 - 00:42:19
Jens
Implement this. So I, I'm saying the future of federation is that you will tell an LLM that you want to add a new capability to the graph. It will decide the graph for you. And the second step is you tell it that here's a proto and there's the rest API. And it will implement that. It will run a test.

00:42:19 - 00:42:51
Jens
It will verify everything. And so the user, the architect, they will be responsible for iterating and designing the schema and telling an LLM to implement it. But and I think like gRPC is, is quite an old technology LLMs know a lot of content about gRPC. They understand how to how to write code for that. And so we, we, we think that is the superior solution.
