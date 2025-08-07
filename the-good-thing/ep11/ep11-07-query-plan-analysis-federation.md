---
title: Query Plan Analysis and Federation Insights
slug: ep11-07-query-plan-analysis-federation
series: The Good Thing
episode: 11
chunk: 7
participants:
  - Stefan
  - Jens
segment: Static Analysis and Future Tooling
timecode: 00:36:28:22 – 00:43:02:29
start_time: 00:36:28:22
end_time: 00:43:02:29
speakers:
  - Stefan
  - Jens
topics:
  - Static query plan analysis
  - CI system for schema testing
  - AST statistics and insights
  - Federation directive impacts
  - Schema change analysis
  - Query planning optimization
tags:
  - query-planning
  - static-analysis
  - federation-analysis
  - ast-statistics
  - ci-testing
  - schema-optimization
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
  - GraphQL
mentions:
  - CI system for schema validation
  - query plan AST analysis
  - federation directives impact
  - schema change testing
  - open source tooling
  - reliability improvements
summary: |
  Jens describes WunderGraph's new static analysis tooling that analyzes query plans for all customer schemas and queries. The system generates AST statistics and can detect how federation directive changes impact query planning, enabling insights into schema optimization and reliability improvements.
---
00:36:28:22 - 00:36:56:22
Jens
Yes, we can do that. But why I mean, we we have an algorithm for this Federation works great.
And yeah, we we now also built very powerful tooling to better understand how your federated
graph looks like. All these kind of things and which which brings me to another interesting topic.
Looking a bit into the into the future.
00:36:56:22 - 00:37:01:24
Jens
But before that, I don't know if you have any questions so far.
00:37:01:26 - 00:37:22:15
Stefan
No, I think it's really useful. And one of the cool things about the series a announcement was,
these reporters took the concept of federation and they put it into, their, their report showed
what they wrote about. And my little sister, she emailed me or not, emailed me. She texted me
and she said, wow. Like, I kind of understand now what you do, which was in Central plumbing.
00:37:22:20 - 00:37:41:26
Stefan
And she's like, okay, now I understand what APIs do and I understand what federating is. It's
really interesting what you guys are doing with the plumbing. That's why I come in. I have on
that. I want to know though, like because I've seen it obviously as a co-founder. I mean, you
don't even talk about GraphQL anymore. You more talk about the organizational pains versus.
00:37:41:26 - 00:37:57:04
Stefan
And GraphQL is just a small subset of solving that problem. But talk to me a little bit about like
the roadmap. Like where are we going with this. Where do you see GraphQL fitting in. And
especially with Federation.
00:37:57:07 - 00:38:35:29
Jens
Yeah. So one one super interesting thing that just recently happened is, you know, sometimes
you, you build something like we're, we're currently building a new thing. And this new thing, it's
going to be outside of the typical realm like router and schema registry. And something
interesting happened. You know, sometimes you, you build a new tool and then you kind of
realize, or you, you, you get a new view on the world, and it completely changes how you see
things.
00:38:35:29 - 00:39:03:26
Jens
And so, well, one thing, we did is. So we, we build a bunch of things. I don't want to be, like, too
specific yet, but, what we what we did is, we now have have a tool which allows us to analyze
queries, so we can understand how query plans would look like. So we have turned, by the way,
just it's open source.
00:39:03:27 - 00:39:05:05
Jens
You can you can just you'll.
00:39:05:05 - 00:39:06:00
Stefan
See you can see the.
00:39:06:00 - 00:39:39:06
Jens
Commits. Yeah. No, but, so what we did is, we, we really care about reliability. And one thing to
ensure reliability is, in the, in the future, we we want to improve our, our query planner, bring in
new capabilities. And so we built a CI system that takes all schemas from our customers and all
queries. And it plan all all queries against them.
00:39:39:09 - 00:40:06:23
Jens
So generates a Groupon for every single query we know. And on every pull request where we
change or try to, to, change our router, we run this thing in the back end like it's not on, public
because we don't want to make this data public. So we run all these queries, we generate the
query plans, and if they if there's a diff, we we would flag this.
00:40:06:23 - 00:40:35:22
Jens
And then we have to manually go through the diff and analyze why did the query plan change,
etc., etc.. And so we, we built this and we looked into this and I, you know, sometimes you, you
have data in front of you and you start thinking, you start looking and then a very interesting
process kind of started where, you know, we had discussions in the team and what we kind of
realized this.
00:40:35:22 - 00:40:57:18
Jens
And I think that's a that's a world that opens up that like, nobody ever touched this in the
GraphQL space. So imagine you have a schema and you have a query. No, imagine you have a
schema and you have a thousand queries. And you plan all of the. And now that you have
planned all these queries, you analyze them in whatever way.
00:40:57:18 - 00:41:28:15
Jens
So you you look at the query plans, they are ASTs and you analyze them and you build stats
about what these ASTs do, for example, how many nodes, what kind of nodes, etc., etc.. So you
get statistics about these scores statically. This is static analysis. No, no LLM no magic. It's like
very simple stuff okay. So we have these statistics and now do the following.
00:41:28:17 - 00:41:52:26
Jens
In Federation we have this concept of key. And we have concepts of requires and provides and
blah blah blah. And all these directives, they have influence on what the query planner does,
how it plans something sharable for example. It's another thing override. So all these federation
directives, they they do something with your query plans okay. So imagine this.
00:41:52:28 - 00:42:21:23
Jens
You have a thousand queries and the schema you plan them. And now you have a thousand
ASTs and you analyze them. Then you change one tiny thing in the, in the, in your in your
schema. For example, you change a field or you move a field from one subgraph into another,
or you do like random stuff, whatever. And now you generate these query plans again.
00:42:21:26 - 00:43:02:29
Jens
So they will diff. And now think about it like this. Think about you have these two packs of ASTs
and somehow you're you're able to build, insights or you can build, yeah, you can analyze them
so you can build stats. And now think about doing a lot of changes, random changes, not so
random changes. And you, you, you change the, the a, the schema and you generate the plans
and you build the stats.