---
title: API Safety, Cosmo, and the Waiter Analogy
slug: ep17-10-api-safety-cosmo-and-the-waiter-analogy
series: The Good Thing
episode: 17
chunk: 10
participants:
  - Stefan
  - Jens
segment: API contracts as AI safety mechanisms
timecode: 00:45:01 – 00:50:19
start_time: 00:45:01
end_time: 00:50:19
speakers:
  - Stefan
  - Jens
topics:
  - Schema Validation
  - API Safety
  - Waiter Analogy
  - Cosmo Integration
tags:
  - schema-validation
  - ai
  - api-design
  - cosmo
  - founder
  - go
  - graphql
  - llm
  - mcp
  - rest
  - startup
topic_tags:
  - schema-validation
entities:
  - LLMs
  - Sofia
  - API contracts
mentions:
  - sending 100 bucks to Sofia
  - raw text communication problems
  - tokenization process
  - different model training data
  - temperature creativity settings
  - hallucinations risk
  - waiter restaurant analogy
  - schema validation importance
summary: Jens explains why raw text communication between LLMs is dangerous, using
  an example of accidentally sending money to Sofia due to tokenization differences
  and temperature settings causing hallucinations. He advocates for API contracts
  as safety mechanisms, using a waiter restaurant analogy to illustrate how structured
  schemas provide validation and type safety that prevent AI systems from executing
  unintended actions.
---

00:45:01:06 - 00:45:06:24
Jens
Now no you're saying can't we just replace all of this with LLMs and stuff.
00:45:06:27 - 00:45:11:18
Stefan
And I'm already seeing where you're going. I like it.
00:45:11:21 - 00:45:44:24
Jens
No. But so you're you're front end LLM. It it sends text to the next server and this text could
contain. Please send 100 bucks to Sofia. And then the server goes like, okay, I'm sending 100
bucks to, to Sofia, and maybe that's even right. And then you have like multiple other agents
and they all collaborate and they all have text as the, as the communication method.
00:45:44:26 - 00:46:11:04
Jens
And the problem with, with this kind of style of communication is if you just use raw text, the way
LLMs work is you, you tokenize the input. So you take the, the bytes or whatever you, you cut
them into smaller pieces. And then the, the LLM tries to make sense of what these pieces mean.
We call them tokens.
00:46:11:06 - 00:46:33:04
Jens
Okay. You have these tokens blah blah blah. And now in each server you have like different
models. They might have trained on different data and maybe they slightly send different
messages. And if we're super lucky, they all do like the right thing. But then there's also, for
example, a thing an LLMs we call it temperature.
00:46:33:07 - 00:46:58:03
Jens
So temperature it it can it can allow an alarm to have some sense of creativity, some sense of
randomness, so that it's not always writing like the same boring stuff. But if you ask an LLM to
write like a story, then you can increase the temperature and it will be more creative and
something. But this creativity, it can lead to to hallucinations.
00:46:58:03 - 00:47:20:09
Jens
So it it might somehow get something into the context window and then it starts, I don't know, it
starts rambling or whatever. So do we want to build a world that works like 60% of the time, or
what's it do?
00:47:20:10 - 00:47:23:03
Stefan
What's your quote though? Your quote? It works. What?
00:47:23:05 - 00:47:54:13
Jens
It works 60% of the time. All the time. No, I mean, you know, but, I think this, this world is, is not
gonna work. We need to have safeguards. And, you know, let's say you have, like, an MCP tool
and your kitchen gives you an MCP server and your waiter. It's an LLM. And so what what kind
of needs to happen is you speak to the LLM, you tell them, here's what I want to eat.
00:47:54:13 - 00:48:27:00
Jens
Like I want to have pizza, margarita and one beer. And then the LLM could, could, could come
back to you and say, Stefan, do you really intend to, to, eat pizza? Pizza margherita and one
beer. Is that what you wish? And then you say, yes, that's exactly what I want. So now the LLM.
It can now do an MCP call for you, and it will say, hey, I on your behalf, I would like to make an
MCP call to the to the kitchen to bring the order.
00:48:27:02 - 00:48:50:06
Jens
Here's what I would send. And now in cursor. If you look at this MCP tool you will actually see it
will construct a JSON message to called the MCP tool. Because MCP uses JSON schema to
define like what is the input? You can verify it. And now you see that we we gave the LLM like a
very strict contract.
00:48:50:06 - 00:49:19:01
Jens
How to talk to the MCP server. And so I think LLM is pretty cool if we put it on top of APIs. And if
you look between the lines like, what is MCP, then okay, it's it's APIs again. And at the core of
everything we need APIs. We need strict contracts. Otherwise, banking wouldn't work like
nothing would work.
00:49:19:04 - 00:49:37:05
Stefan
I think it's a fantastic example. I'm going to have Jacob clip that because I love the waiter
example when I'm talking to non-technical people. But when people ask why do you need? AI
with APIs? It's simply because of banking. Like you say, 100. It accidentally sends 100,000 and
it's because I hallucinated the temperature was a little bit up.
00:49:37:07 - 00:49:57:19
Stefan
And what APIs are providing to this world are the safeguards. And I think that's what the kong
founder means is there is no AI without APIs because APIs provide the safeguards around that.
I like that, I really like that. And we are all about to be at time. We are going to end the episode a
little bit early, because we do have a couple customer calls to get into.
00:49:57:21 - 00:50:19:22
Stefan
But Jens. So one last question before we jump into that is where do you see the future of AI?
But like with APIs? And how does Cosmo tie into that? Because we're working on some exciting
products, and I would love to just have a little bit of time of you talking about it, because I think
what we're building is really powerful because what AI allows is productivity.