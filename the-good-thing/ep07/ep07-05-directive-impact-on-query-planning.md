---
title: Federation Directives Impact on Query Planning
slug: ep07-05-directive-impact-on-query-planning
series: The Good Thing
episode: 7
chunk: 5
participants:
  - Jens
  - Sergiy
  - David
segment: Federation directives and query plan optimization
timecode: 00:21:16:06 – 00:27:03:05
start_time: 00:21:16:06
end_time: 00:27:03:05
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - Federation directive behavior in query planning
  - @provides directive as optimization strategy
  - @requires directive and field dependencies
  - @override directive and field resolution changes
  - Query plan visualization and human readability
tags:
  - federation
  - graphql-directives
  - query-optimization
  - provides-directive
  - requires-directive
  - override-directive
entities:
  - GraphQL
  - Federation
  - Apollo
  - Sergiy
  - David
  - Jens Neuse
mentions:
  - Apollo query plan visualization
  - parallel vs sequential fetching
  - field resolution location changes
  - subgraph dependencies
  - optional optimization patterns
summary: |
  Sergiy explains how federation directives like @provides, @requires, and @override directly influence query planning behavior. The discussion covers optimization strategies, field resolution location changes, and the complexity of managing dependencies between subgraphs in federated architectures.
---

00:21:16:06 - 00:21:23:08
Jens
Like what? What can it potentially do with query plans?
00:21:23:11 - 00:21:53:23
Sergiy
Yeah. Like query plans itself. It's, rather big topic. And it's, yeah. Well, one of the good things
and, I'm glad that we were all inspired by Apple in that way. Like, it's a visualization of query
plans, like human readable version of query plan. It's very good to understand what's happening
like and what what fetches, you are doing in what way you fetch in like, in parallel or in
sequential way.
00:21:53:25 - 00:22:21:12
Sergiy
And, by using federation directive, by the Federation nature, all these directives there define the
behavior of the, how you resolve data. And by using overrides, you can basically change in the
place of a field where field be resolved. And it has a direct influence and query plan because
you, constantly will move the place from where these, fields, would be resolved.
00:22:21:14 - 00:22:44:15
Sergiy
But when you use that, you have to consider that, this field, it could be used in some required
directive and some other subgraph, and it's required by the subgraph, for example. So you
move it to another subgraph and basically you have another chanin of request because you
need to fetch this field from totally other place. But, it will be required only when you query
fields.
00:22:44:15 - 00:23:09:28
Sergiy
This has this requires configuration. And at the same time when you, for example, just put
requires it will mean that always when you when you request this field, you will have to request
some consumption from other subgraph. And requires. Doesn't make a lot of sense when you
do have full data locally in a subgraph and in binary to we just reflected that there will be no
outside features.
00:23:09:28 - 00:23:36:13
Sergiy
You have all data just right here. And at the same time you have provides directive, provides
directive, source purpose of like optimizations. It very chain. And it is actually rather hard to,
make it usable and to place it, exactly where you need it. Most of the cases, you just would see
that. Okay. I always need this field.
00:23:36:16 - 00:24:18:19
Sergiy
And why not to make it provided like usually I need to fetch it from the other subgraph. But
maybe my system has access to this field. So I'm placing my provides directive. And basically
we will be fetching this field on this given parts and, and like, fro from the root query parts or
from some relative parts to the entity, we will be fetching this field, like from this place now
because, it is available, but not all people know that basically, provides, is an optional
optimization and, there could be very rare situation when actually you have a provided node.
00:24:18:21 - 00:24:44:24
Sergiy
But you want to fetch it from that, subgraph where it was provided because it's not beneficial to
do your fetch to this subgraph, because basically all the, all your other fields, come into another
subgraph and this, another subgraph also have this, field, and you just don't want to fetch the
fields from two places. You just will do one, one single fetch.
00:24:44:27 - 00:25:04:03
Sergiy
Yeah. This is like from my point of view. But, also like you, you're working with, composed graph,
like federated graph. And it also has an additional meaning, not only for the execution, but, I
think David could add more on top of that.
00:25:04:05 - 00:25:35:03
Jens
I have one, one question. If we take one step back. So there's various terms. So we have
federation, then we have something that a lot of people, they talk about composition. Then we
have super graphs. And we have in in in Cosmo we have something we call execution config.
And how do you. Yeah. And another term we use is query planning.
00:25:35:03 - 00:26:02:03
Jens
And then we have query execution. So maybe I don't know David Sergiy maybe you can you
can explain a little bit the the ecosystem and how it all plays together. Because from
conversations with you two,, one thing I learned is that actually query planning and composition,
they are kind of married together or they are somehow, somehow like they are two but one.
00:26:02:03 - 00:26:15:28
Jens
that.
But yeah, maybe, maybe you can explain a little bit the the relationship between you two, like
how you work together and what it means for, for composition query planning, execution, all of
00:26:16:00 - 00:26:20:07
David
So, sorry Sergiy.
00:26:20:10 - 00:26:28:27
Sergiy
just a joke?
Yeah, just wanted to say, when you see how illusion is built, it's not an illusion anymore. but is
00:26:28:29 - 00:27:03:05
David
So. So how it works. How Apollo, how it works with Apollo is that composition runs and you get
a supergraph schema. And within that supergraph schema, you have all the encodings for
where a type comes from, which subgraph it comes from, other parts like overrides and external
and inaccessible and all these sort of things are all encoded within directives within the
GraphQL schema itself.