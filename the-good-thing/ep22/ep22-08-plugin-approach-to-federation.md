---
title: Plugin Approach to Federation
slug: ep22-08-plugin-approach-to-federation
series: The Good Thing
episode: 22
chunk: 8
participants:
  - Stefan
  - Jens
segment: WunderGraph Plugin Architecture
timecode: 00:39:26:00 – 00:46:23:00
start_time: 00:39:26:00
end_time: 00:46:23:00
speakers:
  - Stefan
  - Jens
topics:
  - WunderGraph plugin-based architecture
  - Alternative to Apollo connectors
  - Modular federation design
  - Plugin system benefits
tags:
  - plugin-system
topic_tags:
  - plugin-system
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
  - Apollo
mentions:
  - plugin-based alternatives
  - connector system critique
  - modular approach benefits
  - WunderGraph differentiation
summary: Stefan and Jens discuss WunderGraph's plugin-based approach as an alternative
  to Apollo's connector system. They explore how plugin architecture provides modularity
  and flexibility while addressing some of the complexity issues inherent in traditional
  GraphQL federation implementations.
---


00:39:26:23 - 00:40:01:25
Jens
I don't know, but to me it it seems like yeah, I'm, I'm not sure I like the principles. I like this idea
of the the schema should be abstract. It should be demand oriented. Which which is also
another point. If you if you create your schema and you have all these connect directives in the
schema, what it also means is that the schema automatically kind of aligns with the Rest APIs
that you have behind.
00:40:01:27 - 00:40:36:28
Jens
So that means that, the the way you shape your schema will very much follow the structure of
the Rest APIs, which for me, the question is, wasn't the whole point of GraphQL that we follow
what the what the frontend needs and not what the backend has in the Rest APIs? I think if we
do not have an abstraction layer where we can write custom mapping code, where we can
clearly split between, this is what the consumer side wants.
00:40:36:28 - 00:40:46:07
Jens
This is what the backend side has. I think if we don't have that it it won't work.
00:40:46:09 - 00:41:06:21
Stefan
I mean, there's a lot we can go on. I don't want to do the whole time where we rant about some
of the principles that Apollo has broken. I think it's really interesting just to kind of go back and
see how people change. Overall Jens. If you look at principleed GraphQL, would you agree with
the 1 to 10 principles to this day, even though that some things have changed?
00:41:06:21 - 00:41:13:03
Stefan
Or would you add something else, a different principle from your end?
00:41:13:06 - 00:41:39:09
Jens
So I very much agree with abstract demand oriented schema agile approach. I would probably
rename it a little bit, but I think I understand what they mean, like change your schema all the
time. That's fine. Yeah. Use graph metadata to empower developers. Yes, absolutely. Access
and demand control. I think that's that's also fine structured logging.
00:41:39:09 - 00:42:15:04
Jens
I don't know why. It's why it's really here. Sounds like a filler or something. And, then number ten
separate the GraphQL layer from the service layer. Adopt a layered architecture with graph
functionality broken into a separate tier rather than baked into every service. Which again, I
think it's also, if you click on principle number ten, I think it's also a bit related to what we said
before, because it kind of states that we want to have this separate layer.
00:42:15:11 - 00:42:45:24
Jens
I think it's, it's meant to, to talk about, having this router or something. If we read the last,
paragraph, in some cases, this graph here will talk to the backend services using GraphQL. But
most frequently the backend services are left untouched and continue to be accessed by their
existing APIs such as REST, Soap, gRPC, Swift, or even SQL.
00:42:45:27 - 00:43:23:09
Jens
With the mapping from these APIs to graph objects accomplished by servers that form one part
of the graph tier, which it. In this paragraph, again, they state you should have subgraphs, and
subgraphs should have the logic to map from graph to REST. So gRPC or Swift, which I think
it's is it is the right idea. But I yeah, I'm not sure if they if they still follow this principle by
themselves.
00:43:23:12 - 00:43:27:06
Stefan
Question. What is thrift? I've actually never heard of the thrift.
00:43:27:09 - 00:43:34:20
Jens
Thrift is something similar to to gRPC. It's, it's a binary protocol to talk to services.
00:43:34:23 - 00:43:38:01
Stefan
Is it commonly used?
00:43:38:03 - 00:43:54:21
Jens
Some companies use it, I think, for example, Twitter and others. And I think they, they use that
might also be used by Netflix. I'm not sure. But some, some, some companies do, but it's not
extremely widely used.
00:43:54:23 - 00:44:18:21
Stefan
Okay. Cool. I think that was super comprehensive. And its important to see just kind of how
things change. I also think it's cool when, you know, like a different vendor kind of weighs in on
some of it overall, the principles, good connectors. As you can see, we're not a fan. I actually
was talking with the potential customer this week and, he liked the, the overall promise, which I
also agree with.
00:44:18:24 - 00:44:35:03
Stefan
We have a lot of legacy. We want to transform that into GraphQL. We can't just throw GraphQL
on top of it, but there needs to be an approach that kind of can help us with that. And so the rest
connectors overall idea is kind of smart. But can you just explain just a little bit more why is our
approach different.
00:44:35:05 - 00:44:44:25
Stefan
But try to keep it away from the tech like away from the protobuf, but like, what do we do
differently to help people transform their legacy into the super graph?
00:44:44:28 - 00:45:11:18
Jens
Yeah, I think the first part is, when when we were thinking about implementing, gRPC plugins or
let's just say because gRPC, in this case, it's not so important that, our goal was to implement
Cosmo plugins. So we wanted to find a way where we say, okay, we we want to build, a super
graph because in general, we, we agree super graph has super powers.
00:45:11:20 - 00:45:15:12
Jens
And, so sorry.
00:45:15:15 - 00:45:18:06
Stefan
I said, well, said I, I like the way you put that.
00:45:18:09 - 00:45:44:29
Jens
Yes. So how do we get non GraphQL non federation APIs into the super graph. And for us what
we were thinking about is okay, the abstraction of a subgraph is is very powerful. Like we have
one subgraph. It's a tiny piece of the schema. We have composition that makes sure that this
piece of the schema fits into all other pieces.
00:45:45:01 - 00:46:23:05
Jens
So that's that's one integral part. And then we were thinking, okay, how can we create a
developer experience that first of all, it it keeps federation as simple as it is. It doesn't add any
extra complexity. It will be open to connect to whatever you want. And you don't have to learn
like directives or anything. So we were we were thinking about that and what we, what we came
up with is what if we take a subgraph schema?