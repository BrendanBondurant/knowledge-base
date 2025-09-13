---
type: webinar-chunk
title: Live Demo Part 2: Schema Extension and Testing
slug: 2025-08-25-06-demo-schema-extension
series: WunderGraph Webinars
date: 2025-08-25
speakers:
  - Demo Engineer
episode: null
chunk: 6
segment: Schema Extension
timecode: 00:33:04 – 00:40:13
start_time: 00:33:04
end_time: 00:40:13
topics:
  - Schema
  - Demo
  - Testing
tags:
  - demo
  - schema
  - llm
  - llm-security
  - data-modeling
entities:
  - Cosmo Connect
summary: |
  This demo segment covers adding fields, generating code, leveraging LLM support for plugin implementation, and validating changes through build and test.
---


00:33:04:15 - 00:33:21:08
Dustin
All right okay. So it's resolved. So I think this is kind of a lot of boring. So how can I extend my
schema? So let me go to the schema file here, and let's say it's implement a goodbye, root field.
00:33:21:10 - 00:33:23:17
Jens
You're so creative.
00:33:23:19 - 00:33:44:19
Dustin
I know. So and I would like to make it a little bit more exciting. So what is my next step? After
manipulating the schema, I need to generate it again. I hope that makes sense. And now you
can observe again in the generate folder. Okay. My my contact has extended by query.
Goodbye. And now I want to implement it.
00:33:44:19 - 00:34:10:00
Dustin
And now it's very interesting because we are generating such, a strong tight contract, it we
figured out that it's, I would say it's rematch with LLMs today because it's very simplistic and the
LLM not exactly what, what what needs to do in order to, to fulfill that contract. It becomes a
challenge over time when you have lots of lots of endpoints.
00:34:10:02 - 00:34:39:04
Dustin
But this is also a challenge we will soon address, on, on on Cosmo Cloud and our, future
product. So as an example, let's take these files. To implement my missing methods, this mock
data ends up the tests.
00:34:39:05 - 00:34:45:21
Dustin
This can take, I think, 15 seconds, I hope, I hope it's that's fine for everybody.
00:34:45:23 - 00:34:49:11
Jens
By the way, you're. This is like a cursor IDE, right?
00:34:49:13 - 00:34:50:14
Dustin
Yes.
00:34:50:15 - 00:35:02:22
Jens
Okay. And I have noticed something. There's like a .cursor folder, like, did you create it or did it
come or did this come with, with the plugin generation or rather it's coming from.
00:35:02:24 - 00:35:15:13
Dustin
It comes out of the box when you bootstrap a plugin. It is like, I would say an optimized plan of
how to run commands and execute commands based on the bootstrapped, project structure.
00:35:15:15 - 00:35:31:16
Jens
So this whole plugin architecture, it is designed from the ground up to be to be optimized so that
developers can leverage AI to, to write the glue code.
00:35:31:18 - 00:35:33:22
Dustin
Right.
00:35:33:24 - 00:35:36:12
Jens
And then this is so good.
00:35:36:14 - 00:35:50:18
Jesse
And that's going to be significantly easier than trying to coerce cursor or claude or. Whichever
LLM you choose to write very idiomatic GraphQL code in whatever framework you found is
there. they're all very different. And there's a lot of foot guns.
00:35:50:20 - 00:35:54:12
Dustin
Yeah. Okay.
00:35:54:12 - 00:36:31:12
Jens
So I actually did an experiment like a while ago, I ask, I don't know what what model that was
Gemini 2.0 or I think I also tried it with, with sonnet and I ask it, I ask cursor to implement an
Apollo Federation subgraph with Apollo server and, yeah, what I kind of figured out is that, and I
think we all kind of, conclude that these days, if you give an AI too much, too much room for
interpretation, like implementing a GraphQL server that alone.
00:36:31:12 - 00:37:04:09
Jens
It's a challenge. Figuring out how federation works, you need to have, like, the right tools for
schema validation and everything. So it's it adds to the challenge. And then properly
implementing like, like entity resolvers and all these kind of thing, it adds complexity. And what
we really tried to do with, this, gRPC architecture is we take your, your subgraph SDL, we
compile it into proto, then we have this folder here with cursor rules and everything.
00:37:04:11 - 00:37:39:15
Jens
We also tell cursor like, hey, this is how we write tests. This is we compile everything. So we
really try to to narrow down everything that could add complexity, put AI on the shortest leash
possible to, to limit, like, hallucinations and everything. And so far our, our, results, look very,
very promising because ultimately what we want to achieve here is, you have your subgraph
SDL, you have an open API spec or a.
00:37:39:15 - 00:38:03:08
Jens
SOAPl or whatever, and somehow we need some code in the middle to, to adapt it to, to the
graph. And the end goal is to just say, hey, cursor, here's my RPC, here's my open API, handl
the rest, write the tests, implement the functions, do it right, and then, yeah, that's what Dustin
And the team is trying to achieve.
00:38:03:10 - 00:38:05:20
Dustin
All right. Great. For the,
00:38:05:22 - 00:38:11:15
Jens
Comprehensive, I just try to fill the time until your thing here is done.
00:38:11:17 - 00:38:35:02
Dustin
No. I'm ready, I'm ready. So go ahead. So I just like a simple implementation of a query. Good.
Bye, method and also tests and. Yeah. So let's you also have, like a WGC commands to run
tests in a specific language. And now we can see, okay, test completed successfully. What is
the next step of it. It is again to build it.
00:38:35:04 - 00:38:39:03
Dustin
00:38:39:05 - 00:39:08:18
Dustin
Build it. And then of course also to compose the latest supergraph configuration. And then the
router will pick off, pick up the last execution config to, well, I always mixing up I don't know why,
I always run make, but it's pmpm. Okay. And then you can see here it just picked up, it was
reloaded. If I reload my screen, I should have a good bye here.
00:39:08:20 - 00:39:43:07
Dustin
Good bye. Peter. I don't know anyone called Peter, but it's okay. Good bye. So if we show the
trace again, you know, making calls to three different, subgraphs, two of them are implemented
as gRPC. And it's not super obvious here, but even in HelloWorld examples, we see it
significantly significant, improve in performance. So and this makes this for example here is 0.56
milliseconds.
00:39:43:09 - 00:40:13:18
Dustin
And this is actually making an external call to APIs. But yeah. So even in this simple example
we see like how much we save by moving from http to binary protocol like gRPC. And if I come
to the demo again now I have implemented another gRPC plugin. Next to users, I have
incorporate, also product subgraph, which is the standard or GraphQL server, that compatible
with any frameworks out there.