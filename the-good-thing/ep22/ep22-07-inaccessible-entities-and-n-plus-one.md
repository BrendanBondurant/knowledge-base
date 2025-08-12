---
title: Inaccessible Entities and N+1 Problems
slug: ep22-07-inaccessible-entities-and-n-plus-one
series: The Good Thing
episode: 22
chunk: 7
participants:
- Stefan
- Jens
segment: GraphQL Performance Issues
timecode: 00:32:04:00 – 00:39:26:00
start_time: 00:32:04:00
end_time: 00:39:26:00
speakers:
- Stefan
- Jens
topics:
- GraphQL entity accessibility
- N+1 query performance problems
- Federation implementation issues
- Query optimization challenges
tags:
- federation
- graphql-federation
- grpc
topic_tags:
- federation
- graphql-federation
- grpc
entities:
- Stefan Avram
- Jens Neuse
mentions:
- entity accessibility problems
- N+1 query patterns
- implementation challenges
- performance optimization
summary: Stefan and Jens explore GraphQL federation's entity accessibility issues
  and the persistent N+1 query problems that plague federated systems. They discuss
  performance optimization challenges and implementation issues that arise when scaling
  GraphQL federation architectures.
---


00:32:04:23 - 00:32:38:23
Jens
I think that that was the previous approach with, with connectors. So they, they probably they
probably change something already in the, in the spec. Yeah. That that is okay. That is an
interest. Another one interesting problem. Can you scroll back up again. Okay. So here that that
yes. So what's interesting is can you scroll a little bit up.
00:32:38:25 - 00:33:10:16
Jens
Yes. Okay. So here we have price. Yeah. The the interesting bit is you have the, because this is
something I also figured out about, after digging a little bit into, into connect directive and
entities. So one problem you have is if you define the subgraph with the line seven type price,
this is you define an entity so another subgraph can jump to this subgraph.
00:33:10:16 - 00:33:43:23
Jens
And grab the price entity with the id field and then add other fields like active currency, unit
amount, etc.. Okay, so the problem is for this to work you need to add a root resolver to. To jump
to this, you need to have an entity resolver to jump to the subgraph. So if you scroll up a little bit
down okay, to this legacy approach thing, scroll more.
00:33:43:25 - 00:34:11:09
Jens
Yes. You see here this this is you need to have a query, the query field, it takes an ID and it
returns the price. And they have set entity to true. And and this is something it already smells
because. But on the one side, no, you know, I say smells because it's, it's like a cold smell.
00:34:11:09 - 00:34:44:12
Jens
Okay. Yeah, yeah. So my point is this. You have this price field, it's gets an ID, it returns a price
because you need to somewhere define an entity resolver that gives you the price for an ID, so
that this can behave like an entity. But at the same time, you don't want to expose this field to
the clients, because this should be an entity resolver like an entity resolver, something that's
internal to the graph, not public.
00:34:44:14 - 00:35:13:12
Jens
So to to not make it public, they said, okay, let's put inaccessible on this field because
inaccessible it creates fields that are in the schema. They are accessible to the router but not
accessible to the client. So this field price that gives you price for ID it's not in the client schema.
You cannot see it. It doesn't exist for you, but it exists in the graph because you need to have it
as an entity resolver.
00:35:13:19 - 00:35:37:12
Jens
And there lies another problem. So now you're a frontend guy. You look at the schema, you see
price by ID and you're like, why is it not in my schema? And it's because it's an entity resolver.
So we're we're mixing the concepts here and we're just making things like more harder. And
then Stefan, there's one more thing I guess you do.
00:35:37:15 - 00:35:40:12
Stefan
It I don't I don't see.
00:35:40:15 - 00:35:43:05
Jens
You want to come up with something.
00:35:43:07 - 00:35:43:12
Stefan
But.
00:35:43:12 - 00:35:44:24
Jens
That's another one.
00:35:44:26 - 00:35:49:06
Stefan
The let's do the third one and then I'll ask my question. I'll keep in the back. Okay.
00:35:49:08 - 00:35:54:27
Jens
Do you see the big problem in line number nine?
00:35:54:29 - 00:35:58:15
Stefan
Price IDs. Idea price? No, I don't what is it?
00:35:58:22 - 00:36:10:04
Jens
Okay. The problem could also be seen in line number 12.
00:36:10:06 - 00:36:11:26
Stefan
I don't see. What is it?
00:36:11:29 - 00:36:18:03
Jens
Okay. What was one of my most successful conference talks.
00:36:18:06 - 00:36:20:20
Stefan
About the data loader pattern 3.0.
00:36:20:22 - 00:36:26:13
Jens
The data loader pattern. What problem does the data load? Pattern solve?
00:36:26:15 - 00:36:32:21
Stefan
You're asking the wrong guy. Reverse question Jens. What problem is the data loader pattern
solved?
00:36:32:23 - 00:36:40:12
Jens
It solves the n plus one problem. Do you know anything about graph Ql?
00:36:40:15 - 00:36:42:12
Stefan
I know how to sell it.
00:36:42:15 - 00:37:12:19
Jens
Okay, today I'm asking you like random dude, youre a developer. No, no, no, I'm just kidding. I'm
just making fun. Okay, so here's here's the big deal. When well, when the router wants to give
you active currency and unit amount for a price entity, it doesn't do that for a single entity. It can
do it for one, but also for a hundred price entities.
00:37:12:21 - 00:37:38:21
Jens
So that means we need to where we might be sending a huge batch of requests to the
subgraph to figure this out. And then we we, get back the information. The problem here is we
have this in line number 12. We have this Http endpoint. It's slash prices. And then slash RX id
which, which injects the ID from the price here.
00:37:38:23 - 00:38:22:07
Jens
So that means if we fetch this field, this entity 100 times we will make 100 rest API calls. And
this will not be batched or anything. No data loader. So that's a huge n plus one problem. And
this comes from having this connect directive in this shape. If, if you, you know, if you did this
with, with Cosmo, gRPC plugins, we generate a, we generate an RPC function that takes a list
of ID arguments, and it returns a list of prices.
00:38:22:07 - 00:38:25:27
Jens
And then the batch problem is solved.
00:38:25:29 - 00:38:48:18
Stefan
But again, why would they do this then? Like, I don't understand it. It's full of problems. Why?
And we see this all the time that the team over at Apollo is quite smart. But I'm a little bit
confused about this. Like if it's full and it goes back on the old principles, why would they
implement something like.
00:38:48:20 - 00:39:26:23
Jens
Okay, why why do you do this? I think you, you go for this approach. If you're absolutely
desperate to quickly get people who have REST APIs into the graph or maybe you have
customers who who don't really get enough value out of the graph. And your last straw is to, to
to not have to implement subgraphs. And then you can you can just continue writing your REST
APIs.