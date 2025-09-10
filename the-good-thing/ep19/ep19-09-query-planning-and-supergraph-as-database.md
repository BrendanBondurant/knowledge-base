---
title: Query Planning and Supergraph as Database
slug: ep19-09-query-planning-and-supergraph-as-database
series: The Good Thing
episode: 19
chunk: 9
segment: Query Planning and Graph Architecture
timecode: 00:42:11 – 00:47:02
start_time: 00:42:11
end_time: 00:47:02
speakers:
  - Stefan
  - Robert Farr
  - Jens
topics:
  - Query Planning Strategies
  - Complexity Scoring
  - Supergraph as Database
  - Federation Optimization
tags:
  - query-planning
  - supergraph
  - federation
  - ai
  - api-design
  - benchmarking
  - cosmo-router
  - database
  - go
  - graphql
  - graphql-federation
  - microservices
  - monolith
  - mysql
  - rest
  - rest-apis
entities:
  - Robert Farr
  - Stefan Avram
  - Jens Neuse
  - GraphQL Federation
summary: Deep dive into query planning mechanics, exploring complexity scoring systems
  and the conceptual analogy of treating a supergraph like a database for optimization
  and federation insights.
---

00:42:11:22 - 00:42:38:13
Robert Farr
Syntax, you have a query planner, you have data storage and, you know, in my in my career,
especially as I entered distributed systems and all those kind of things, right, you move to key
value stores. What what really I was seeing happening is we were decomposing. We were
pulling apart this relational data store that, you know, we had lived on forever and broke it up
into constituent pieces.
00:42:38:15 - 00:43:01:25
Robert Farr
And the real missing piece has been that that query planner, right. The syntax and the query
planner piece. If you think about rest, right, that's that's absence. It's just it's all over the place.
So it'd be like, you know, exposing a database, the raw blocks and indexes and say, go make it
right, go get your data.
00:43:01:27 - 00:43:07:28
Robert Farr
Yeah. Exactly. Yeah. GraphQL Federation is that layer. Yeah. So sorry.
00:43:08:02 - 00:43:43:15
Jens
Sorry for interrupting. You made up a great point. A rest API is a little bit like you can access raw
pages. Right. And it is it is your responsibility to do something meaningful with that versus a, a
super graph where you have the different subgraphs and you have the query planner. And I like
what you said with databases and, and I think these kind of observations that you can see that
you, you have, a few more years of experience, compared to me.
00:43:43:22 - 00:44:16:27
Jens
But one thing I remember when I first learned about how to use MySQL, I was introduced to to
the explain keyword. So you can write a query like, select star from user. But you can also say
explain, select star whatever. And then you do join, join, join, join whatever. And then the query
planner. It will actually show what kind of indices is it using to to join another table.
00:44:16:29 - 00:44:44:24
Jens
How is it accessing this and that and the the what is funny about this? I haven't thought so much
about it. But if you this explain statement how is it joining. Is it using an index. This is exactly
what you see in a query plan from from a Federation router, because the query plan will show
you what kind of keys are we using to jump from one subgraph to another subgraph.
00:44:44:27 - 00:45:16:16
Jens
So yeah, you could say federation is kind of like an evolution where we went from key value
stores to relational databases to to like resource based microservices to like, a graph based
microservice architecture where we can now with, a query planner, understand how we're
accessing data.
00:45:16:18 - 00:45:48:17
Robert Farr
Yeah, yeah, yeah, it is. It's kind of a, I guess, a database for the web. Right. And if, if you wanted
a tongue in cheek, it but but it is, it is literally I think it's that one writes that one layer now where
you pull it all together and you have that ability to create those kind of that insight and those
optimizations, you know, giving, part of your part of your stack now can make decisions on the
most efficient path to get the data.
00:45:48:19 - 00:46:13:06
Robert Farr
And, that just, you know, since since the advent of, of rest and microservices and all that that's
just been absent, and in the industry, because, you know, once you pull, a relational database
apart, right, you pull that apart into multiple microservice and independent databases, you lose a
lot of the value that that monolithic relational database was giving you.
00:46:13:08 - 00:46:31:13
Robert Farr
Or, you know, even if you used a graph database, same kind of thing. Right? If you if you have a
monolithic graph database, well, there's a lot of value you get from being able to navigate using
it, you know, query language, navigating the graph. But if you pull that apart into 100 graph
databases, you lose a lot of that.
00:46:31:15 - 00:46:39:13
Robert Farr
And, I, you know, I look at kind of GraphQL federation. Is this the potential to put that back
together? Yeah.
00:46:39:16 - 00:46:56:01
Stefan
It's well said like one. Just note from my and I like what you said about that with the, like kind of
just going in the past, one thing I've always heard is like, it's never a bad idea. It's just a bad
time. And what you said previously, like, you peel back the onions of the, or the layers of the
onion.
00:46:56:03 - 00:47:02:17
Stefan
It's history again in history tends to repeat itself, which is really, really, really funny. But Jens, I
know you had a thought there. Feel free to add to it.