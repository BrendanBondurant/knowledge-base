---
title: Dream Query Workflow
slug: ep13-11-dream-query-workflow
series: The Good Thing
episode: 13
chunk: 11
participants:
  - Stefan
  - Jens
segment: Schema Evolution and Visualization Demo
timecode: 00:41:28 – 00:45:02
start_time: 00:41:28
end_time: 00:45:02
speakers:
  - Stefan
  - Jens
topics:
  - Employee type schema exploration
  - Architecture visualization with Mermaid diagrams
  - Dream query workflow concept (from Yelp)
  - Live schema modification attempt
  - Serverless architecture challenges
tags:
  - dream-query
  - schema-visualization
  - mermaid-diagrams
  - yelp-concept
  - schema-evolution
  - serverless-architecture
  - employee-type
entities:
  - Employee type
  - Mermaid
  - Yelp
  - GraphQL
  - Super graph
  - Subgraphs
  - Family service
  - Availability service
mentions:
  - employee schema details
  - federated architecture visualization
  - Mermaid diagram generation
  - family and availability subgraphs
  - dream query workflow from Yelp
  - age field addition attempt
  - serverless cold start issues
  - schema field missing error
summary: |
  Jens demonstrates schema exploration by showing the employee type details and successfully generates a Mermaid diagram visualizing the federated architecture. He introduces the "dream query workflow" concept borrowed from Yelp, attempting to add an age field to demonstrate schema evolution, but encounters issues due to the field not existing in the current schema.
---

00:41:28:02 - 00:41:42:07
Jens
It. And now we, we know everything about this thing. Maybe we can ask a follow up question.
For example. Show me the, schema of the, employee type.
00:41:42:09 - 00:41:52:07
Stefan
I have a question of could you ask it, can you visualize for like, visualize this for me? Like I
shows you a picture or a visualization of the of the architecture.
00:41:52:10 - 00:41:54:20
Jens
For or.
00:41:54:20 - 00:41:57:23
Stefan
Would we have to build that MCP component?
00:41:58:06 - 00:42:08:29
Jens
Good question. So here's our, our, employee type. Yeah. We now understand the schema. You
said visualize the architecture.
00:42:09:01 - 00:42:23:29
Stefan
Yeah. Like I want to see what the federated architecture looks like. So, like, if I'm a new
developer and we're using GraphQL and we have a super graph, I'd be like, hey, can you
visualize this for me? So I can see how each components work together?
00:42:24:01 - 00:42:25:27
Jens
I have no clue.
00:42:25:29 - 00:42:33:09
Stefan
Yeah, I was about to say for the audience and everybody watching, we haven't tried this before.
Okay, so you can't, but why can't you visual.
00:42:35:07 - 00:43:17:06
Jens
That's not too bad. So what do we have here? Graph TD client router, router subgraph, then
subgraphs. Oh, this is wait, this is a, a mermaid diagram, right? interesting. So we could take
this and put it into some mermaid drawing tool. And it could actually, this is interesting. You
know, you have family. It's a subgraph.
00:43:17:09 - 00:43:38:28
Jens
And it shows us that it has details and pets and, availability has this available. So it actually
shows us what is coming from where, which is it's pretty interesting. So it figured out all this
information and can, can present it. So yeah, very useful. But this was just the first prompt okay.
So yeah sorry.
00:43:38:28 - 00:43:39:24
Stefan
I'm getting excited.
00:43:39:24 - 00:43:54:14
Jens
Like like it's crazy okay. So here's here's another thing that's so I call it the dream query
workflow. And I think this is for me this is really cool thing.
00:43:54:16 - 00:43:59:11
Stefan
So in the dream query that comes from, Yelp, right.
00:43:59:13 - 00:44:03:17
Jens
Yes. So I, I borrowed it from Yelp.
00:44:03:19 - 00:44:10:18
Stefan
to give this back?
By the way. You know, if you borrow something, you have to give it back. So how are you going
00:44:10:20 - 00:44:14:24
Jens
I give them credit. Okay. Here we go.
00:44:14:26 - 00:44:15:07
Stefan
Okay.
00:44:15:07 - 00:44:45:27
Jens
So let's say, we have here we have this employees. This will always fail on the first run because
we have a weird serverless architecture okay. So we have ID details. Forename, surname,
format run. Okay. So you see, we have this. So now I give you a simple example. So let's put
age here, to get the age of everybody.
00:44:45:29 - 00:44:50:06
Jens
Yeah. So it's not working. Why is it not working.
00:44:50:08 - 00:44:51:27
Stefan
It's not in the schema.
00:44:51:29 - 00:44:59:23
Jens
It's not in the schema, okay. So we do this. We copy this, we go. That's the.
00:44:59:23 - 00:45:02:28
Stefan
Dream. That's the dream. Query you want is in front end.