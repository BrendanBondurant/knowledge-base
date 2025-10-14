---
type: podcast-chunk
title: Entity Layer Concept as Federation Core
slug: ep30-08-entity-layer-concept-federation-core
series: The Good Thing
episode: 30
chunk: 8
segment: Entity Layer Architecture
timecode: 00:20:25 – 00:23:22
start_time: 00:20:25
end_time: 00:23:22
speakers:
  - Jens
topics:
  - Entity Layer Concept
  - Data Model Abstraction
  - Caching and Identity Resolution
  - System Integration
tags:
  - graphql
  - federation
  - cosmo
  - microservices
entities:
  - Entity Layer
  - Federation
  - Data Models
  - Caching
  - Identity Resolution
summary: Jens defines the "entity layer" as a core architectural idea beyond Federation—an abstraction that connects data models, caching, and identity resolution across systems.
---

00:20:25 - 00:20:51
Jens
And that's, that's like a very, very big and complex topic. It's also not a pure a pure MCP or graphql or a LLM topic. Like a lot of machine learning and algorithms go into that. And, yeah, it's an interesting topic and I hope kind of what I say, it underscores how much are we we, we thinking about this, this kind of space.

00:20:51 - 00:20:56
Jens
And then by no means we're, we're looking elsewhere.

00:20:56 - 00:20:59
Stefan
Today's show is sponsored by Jens’s monologues.

00:21:00 - 00:21:01
Jens
No kidding. The monologue.

00:21:01 - 00:21:22
Stefan
There. Fantastic. It kind of shows exactly how we feel about this. I'm still a little bit confused. One of the things that we've been talking about, though hard, is the entity layer. People might not be understanding what you mean by it. And again, this is going to trigger another monologue. But it's important. What is the real magic behind this entity layer and how does that feed into our AI strategy.

00:21:22 - 00:21:36
Stefan
How does that feed into the products that we're building, which are coming soon? As you mentioned, you know, we left or we weren't able to join GraphQF conf just because of our roadmap. I mean, things have exploded. We've scaled up the team. Everything is going good from a company point of view. But what is the entity layer like?

00:21:36 - 00:21:40
Stefan
Why is this so special and how does it feed into AI?

00:21:40 - 00:21:48
Jens
Why do you keep hammering against your microphone? Is it me again? No, it's I don't know, your uncle maybe.

00:21:48 - 00:21:50
Stefan
No, it's the stupid chair. I ordered a new one, though.

00:21:50 - 00:21:51
Jens
I don't know if.

00:21:51 - 00:21:53
Stefan
I'm going to step away from them.

00:21:53 - 00:22:03
Jens
But I hear you just said we have an AI strategy. Why? Why are you leaking that? Oops, oops oops. But talk to me about.

00:22:03 - 00:22:04
Stefan
The entity layer.

00:22:04 - 00:22:09
Jens
Can you have a startup these days without an AI strategy?

00:22:09 - 00:22:17
Stefan
No you can't. I mean, you won't get funding and you'll die. Like in this climate. It's a nuclear wasteland. It's all about AI.

00:22:17 - 00:22:25
Jens
Yeah. Okay. Entity layer.

00:22:25 - 00:23:22
Jens
David, asking about innovations. I mean, you're joining our all hands, right? I mean, maybe you should just listen. Kidding. Okay. Entity layer. So, Federation is cool. I truly think like the some some folks at some very smart engineers are, are or have been at Apollo who created the first version of of Federation. And I think one of the coolest concepts they came up with is the key directive which gives us entities, after the key directive, I, I kind of think that Apollo went into a little bit of, of a rush, maybe it came from their early success, but some other directives, they, they feel a little bit rough and a
