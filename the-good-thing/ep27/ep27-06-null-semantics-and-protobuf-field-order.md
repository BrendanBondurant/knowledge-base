---
title: Null Semantics and Protobuf Field Order
slug: ep27-06-null-semantics-and-protobuf-field-order
series: The Good Thing
episode: 27
chunk: 6
segment: Protobuf mapping challenges and schema alignment
timecode: 00:27:17 – 00:32:43
start_time: 00:27:17
end_time: 00:32:43
speakers:
  - Jens
  - Ludwig
  - Dustin
topics:
  - Protobuf Field Order
  - Null Semantics
  - Mapping Strategies
tags:
  - protobuf
  - schema-translation
  - graphql
  - data-modeling
entities:
  - Protobuf
  - GraphQL
  - WunderGraph
summary: Jens and Stefan dive into Protobuf field order issues, null value handling, and schema translation strategies for compatibility.
---
00:27:17:24 - 00:27:24:03
Jens
And are you following the the semantic non-null discussion in the GraphQL community?
00:27:24:06 - 00:27:26:17
Ludwig
And there's an ongoing discussion.
00:27:26:20 - 00:28:00:03
Jens
Yeah. Like one of the biggest problems we currently have in the GraphQL spaces, if we request
a field, and, and it's nullable. Do we get back nukk? Do we get back nothing. Or an error with
null and does null mean nothing or null or like does null have a meaning or is it an error or null
or we we don't always know.
00:28:00:06 - 00:28:32:11
Jens
But for example, let's say you make a subgraph request and it should return a nullable field like,
I don't know, best friend. And let's say you don't have a best friend because nobody likes you.
So your best friend is null. But it's also possible that, so in that case, the the server, the
subgraph returns null. But what if the server has an error and returns null?
00:28:32:13 - 00:29:02:05
Jens
How do you distinguish? And then. So the stupid thing is we we don't have a way in Json. Like,
you know, sometimes I feel like Json should have like undefined, like, you know, something is.
And then I kind of like this in JavaScript. In JavaScript, you can say something has a value, it's
undefined or it's null, because then you can express that we don't have something with null, like
the value is actually null.
00:29:02:05 - 00:29:27:02
Jens
And with undefined we can say there is nothing. And but that's a different but okay, that's a
different topic. I also want to talk about, the log file with Dustin. And then later on, I want to dive
a little bit into the topic, of, OCI, like Jessie does some, some really cool stuff with, with OCI.
00:29:27:04 - 00:29:48:10
Jens
Just one quick question, Ludwig. Because, this is something I stumbled into a while ago. Are
you supporting BigInt? Because a while ago, I, I realized, BigInt, you cannot represent it in Json
like a number. It's actually in Json. It's a string. Do you. Have you ever thought about BigInt in
the context of your project?
00:29:48:12 - 00:30:20:11
Ludwig
In the context of my project. And, so we only have INTS currently, which are 32 bit integers in, in
protobuf, The idea of how to handle like bigger ints would be to use a float instead. So you can
use a float to, to have a, 64 bit integer if you wanted to. We still have like a floating point
number, but if you, if you just, providing an int, you just get an integer without a floating point if
you pass it properly.
00:30:20:13 - 00:30:33:11
Ludwig
So that is I think that is the idea in, in GraphQL. At least when, when I read through different
posts, people would always recommend to use float instead of an integer.
00:30:33:13 - 00:31:01:17
Jens
Yeah. But by the way, just remember like we have David here. So if you want to trigger David,
someone can just say something wrong about Federation or composition and, just for fun.
Because he wasn't active on the chat for a while, but, okay. Dustin, very early on, I think it was
you who came up with this idea, or we were testing and we were.
00:31:01:23 - 00:31:31:28
Jens
We were trying odd things. And I kind of vaguely remember I was your rubber duck. We were
playing around with Cosmo Connect in the early days, and we. We realized, like, Shit, we we
have a problem. Like, it's it's not gonna work. Like, we quickly found the solution, but there was
a severe problem. Because you can do things in GraphQL schemas that you definitely shouldn't
be doing in gRPC, right?
00:31:32:01 - 00:31:35:13
Jens
Yeah. So. So we learn this is life, right?
00:31:35:13 - 00:32:11:17
Dustin
Otherwise, I would say cut my previous sentence and put it put it into this moment. No. Yeah. I
have to repeat myself like, in, in, in, GraphQL, the order of fields arguments is, is not significant.
So you can play around it doesn't matter for semantics. You can get the same result back.
However in proto the the the field order is significant, that means if you change a field order in
GraphQL, we also need to, be backwards.
00:32:11:17 - 00:32:43:16
Dustin
We need to produce the same, proto structure, in proto. So, and, in order to retain this
information, you need some sort of. Yeah, you need to store that information somewhere. And I
honestly, I don't remember anymore what, what other solution we approach. But, this was, I
would say the yeah. The I mean, if you know, of, npm log files and stuff, that was one of, that
come up in my mind immediately and we've, we've followed this approach.
