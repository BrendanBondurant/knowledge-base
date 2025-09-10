---
title: Apollo Connectors and Broken Abstraction
slug: ep22-05-apollo-connectors-and-broken-abstraction
series: The Good Thing
episode: 22
chunk: 5
segment: Apollo Connector Critique
timecode: 00:19:26:27 – 00:26:23:00
start_time: 00:19:26:27
end_time: 00:26:23:00
speakers:
  - Stefan
  - Jens
topics:
  - Apollo Connectors
  - Broken Abstraction
  - Federation Complexity
  - Architecture Critique
  - apollo-connectors
  - ai
  - apollo-graphql
  - federation
  - go
  - graphql
  - graphql-federation
  - microservices
  - monolith
  - rest
  - rest-connectors
entities:
  - Apollo
  - Stefan Avram
  - Jens Neuse
summary: Jens and Stefan critique Apollo's connector approach, discussing how it breaks
  abstraction layers and creates unnecessary complexity in GraphQL federation. They
  analyze the technical challenges and architectural decisions that impact developer
  experience and system maintainability.
---

00:19:26:27 - 00:19:31:03
Jens
I, I pause here for a second, maybe you have some some remarks.
00:19:31:06 - 00:19:53:26
Stefan
No, it's just interesting. I'm curious to. When this came out, they didn't put a date on this, but I
wonder when they put this. So this is obviously definitely before rest connectors. And so I mean
I would agree with everything that you said here the schema registry being important. But let's
go a little bit further into here. So where is it where they start to contradict themselves is it in
point 4 or 5.
00:19:53:29 - 00:19:59:11
Jens
Click on point for abstract demand oriented schema okay.
00:19:59:12 - 00:20:11:06
Stefan
Okay. Oh it actually goes down okay. So it says the schema should act as an abstraction layer
that provides flexibility to consumers while hiding service implementation details.
00:20:11:09 - 00:20:16:18
Jens
Okay. Can you read like the first two sentences of the, first paragraph?
00:20:16:21 - 00:20:35:24
Stefan
Yeah. So a large part of the value of GraphQL lies in providing an abstraction between services
and consumers. So the schema should not be tightly coupled either to a particular service
implementation or to particular consumers as they exist today. By keeping implementation
details out of the schema, it should be possible to refactor the service to implement the graph.
00:20:35:24 - 00:20:44:25
Stefan
For example, transitioning from monolith to microservices or changing the language in which a
service is implemented without disturbing apps in the field.
00:20:44:28 - 00:20:54:08
Jens
connectors?
Okay, can you open another browser where you just search for an example of Apollo
00:20:54:10 - 00:21:03:22
Stefan
Yeah. One second. Apollo connectors.
00:21:03:25 - 00:21:10:18
Stefan
Here we can just go to their website.
00:21:10:21 - 00:21:28:27
Stefan
I think they have a code example on their website, but kind of weird. Hold up. Okay. Let me
know if this works for you. Let me share my screen. Can you see the code example here?
00:21:29:00 - 00:21:35:15
Jens
Yeah. It's not perfect. Do you have one where you can see it in more clarity?
00:21:35:17 - 00:21:38:25
Stefan
Is this okay?
00:21:38:28 - 00:21:41:23
Jens
No. Can you go to the docs?
00:21:41:25 - 00:21:57:23
Stefan
Yeah. Where are the docs here. Explore pre-built. Where are the, documentation? Okay. Why
use connectors?
00:21:57:25 - 00:22:08:24
Jens
Yeah. Okay. That's a little bit tiny. Do you have, like, a bigger one product? Click on Getting
Started quickstart.
00:22:08:26 - 00:22:11:03
Stefan
Where do you see that?
00:22:11:05 - 00:22:14:06
Jens
Just quickstart. After getting started.
00:22:14:09 - 00:22:17:00
Stefan
Quickstart after getting started. Why don't I see that.
00:22:17:07 - 00:22:22:01
Jens
Left in the menu? You have getting started and then you have quickstart and then.
00:22:22:04 - 00:22:43:07
Stefan
Okay, there we go. Okay, okay. Create a graph, explore example tiny query, adding a new field.
Here we go. Further connectors playground.
00:22:43:09 - 00:22:52:22
Stefan
Come on, give me a good example. Guys.
00:22:52:24 - 00:22:53:27
Stefan
I think we're gonna, you know.
00:22:53:29 - 00:23:10:09
Jens
OpenAI.
Go to pre-built connectors. Pre-built connectors, library, pre-built connectors. Okay, maybe go to
00:23:10:12 - 00:23:14:01
Jens
Is there somewhere the the code for it?
00:23:14:04 - 00:23:19:03
Stefan
Not really.
00:23:19:06 - 00:23:22:15
Stefan
No. It's just a mutation.
00:23:22:17 - 00:23:28:22
Jens
Okay. One sec.
00:23:28:24 - 00:23:46:17
Stefan
One sec. Guys, one thing.
00:23:46:19 - 00:24:03:26
Stefan
Let me look for it too guys. In the meantime, where's everybody calling out? From what we find
this example. Now we can go through it more. But right now, we're discussing some of the
principles that Apollo has broken in their original manifesto. Let me see if I can.
00:24:03:28 - 00:24:15:01
Stefan
You might hear some typing.
00:24:15:03 - 00:24:20:06
Jens
Okay, I think I found something good. I send you the link.
00:24:20:08 - 00:24:25:03
Stefan
Okay. One sec guys.
00:24:25:06 - 00:24:39:14
Stefan
Okay, here we go. Okay. This is a decent example. Give me a sec. Share my screen. We see it.
00:24:39:17 - 00:25:20:01
Jens
Okay, perfect. So let me just reiterate because I have this on this other screen. So a large part
of the value of graphql lies in providing an abstraction between services and consumers. So the
schema should not be tightly coupled either to a particular service implementations or to
particular consumers as they exist today. By keeping implementation details out of the schema,
it should be possible to refactor the services that implement the graph, for example, transitioning
from a monolith to microservices, or changing the language, etc. etc..
00:25:20:03 - 00:25:51:12
Jens
Okay, so if we if we think about the graph as this abstraction layer, this means that the graph on
the one side, it should be oriented towards the, the clients, and it should be abstracted away to
enable many different use cases. And then on the other side, we should be able to move the
implementation from one service to another or rewrite it in a different language and a different
stack, or just completely change.
00:25:51:14 - 00:26:23:16
Jens
Change things. And I, I think that this principle is, is very much, broken, with the with the
connectors approach. So first of all, what, what the principle states is that we should not mix the
schema with implementation details. And if we look at the schema here that we have we have
this type price, then we have the key, which I think is fine.