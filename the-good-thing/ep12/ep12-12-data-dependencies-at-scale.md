---
title: Data Dependencies and Fragments at Scale
slug: ep12-12-data-dependencies-at-scale
series: The Good Thing
episode: 12
chunk: 12
participants:
- Stefan
- Jens
segment: Fragment Management and Team Coordination
timecode: 00:42:26:26 – 00:47:16:25
start_time: 00:42:26:26
end_time: 00:47:16:25
speakers:
- Stefan
- Jens
topics:
- Fragment hoisting and compilation
- Data dependency changes over time
- tRPC vs GraphQL for large teams
- REST API field management challenges
- Breaking changes and unused fields
- Team-scale frontend development
tags:
- fragment-hoisting
- data-dependencies
- trpc-comparison
- rest-api-challenges
- breaking-changes
- team-scale-development
topic_tags:
- fragment-hoisting
- data-dependencies
- trpc-comparison
- rest-api-challenges
- breaking-changes
- team-scale-development
entities:
- Relay
- tRPC
- GraphQL
- REST
- Meta
- Coinbase
- WunderGraph
- Stefan Avram
- Jens Neuse
mentions:
- relay compiler optimization
- product owner change requests
- lint errors for unused fields
- teams of teams coordination
- REST API field removal challenges
- 100 frontend developers scale
summary: Jens explains how Relay's fragment hoisting enables efficient data dependency
  management at scale, contrasting with tRPC and REST approaches. He describes how
  GraphQL fragments prevent breaking changes when UI requirements change, while REST
  APIs accumulate unused fields over time due to coordination challenges across large
  frontend teams.
---

00:42:26:26 - 00:42:58:21
Jens
So in the field detail page you also define how you how you query the thing and everything. And
you have a fragment for that. And you, you define the fields you need in a detail page. And let's
say in the detail page you need more fields than in the overview because it's more detailed.
Okay, good. So stage one we deploy it and then product owner says detail page I don't like it.
00:42:58:21 - 00:43:28:01
Jens
Please make changes. Please remove something. So you remove a field from the fragment off
the detail page. And by removing it, you then run the relay compiler again. And what the relay
compiler does is it figures out that on each path of the page, you combine all the fragments you
hoist up from the from the child components to the parent.
00:43:28:01 - 00:43:38:19
Jens
You hoist up the data requirements, and you build a unified query for this page to load the page,
efficiently. But you can see this.
00:43:38:21 - 00:43:43:26
Stefan
well with the relay.
By the way, when you said that, you can kind of see the similarities of why GraphQL pairs so
00:43:43:28 - 00:44:17:26
Jens
Yeah. Yeah. Exactly. That's like that's why you need fragments and selection sets and these
things. But now here's the thing. So let's say you have tRPC. So you create a t RPC call that
gives you the feed data. And because you also need the detail page, it loads the feed and also
the detailed page data. So now in your frontend component you remove this this one thing
because the product we want to set, we don't like it.
00:44:17:29 - 00:44:42:28
Jens
Yeah. And so in tRPC you, you would not remove a field from the fragment. But with the right
tooling, if you have a field in the fragment and you're not using it, you get lint errors. So it's like,
hey, why are you fetching something? You don't need it. Yeah okay. Fragments relay compiler. It
figures this out so it tells you hello.
00:44:42:28 - 00:45:01:24
Jens
Remove the field. Then we compile it, we hoist up our data dependencies. And now the field is
actually gone from the page query. If you do the same thing with something like tRPC. Yeah. No
not against trPC. We I think we use it or maybe we don't. But it's a good thing. So don't worry I
think the good thing.
00:45:01:24 - 00:45:29:01
Jens
But yeah. But the point is let's say you are like a big company like meta or what? Coinbase or
whatever. And you have teams of teams, of teams, of people and everybody changes UI
components over time. It means that data dependencies for UI components, they change all the
time. And nobody knows like a complete map of like a complete tree of of everything.
00:45:29:07 - 00:45:54:06
Jens
So you are deep down in the tree, you change that one component, you remove a field or you
add something, and now you need to go through five layers of UI components to manually figure
out, do we really need this field or don't we so and let's say you have a rest API. So what
happens is you make a rest API call in the root of the component tree.
00:45:54:06 - 00:46:19:20
Jens
You load the data for this tree, someone in the child tree in the in the children of this component
tree, they say, we we we need another field. So you go all the way to the root to the rest API.
Someone adds it there. Okay, nice. It's not working. You deploy it. Half a year later, you realize
we change the feature, you remove this field.
00:46:19:23 - 00:46:40:08
Jens
Do you think anybody is going to remove it from the rest API? No, it would be a breaking change
like removing a field from a fragment. It's not a breaking change if nobody is using it, but you
need to know who is using the fields. So you need to hoist up all the fragments and see are we
using it or are we not using it?
00:46:40:10 - 00:47:16:25
Jens
And if you don't have relay you cannot do this. And really, I can only work with a query language
that allows you to have selections on the tree. So yeah, you need GraphQL to do that. And if
you if you have ever tried to build UI at scale or across teams like mock like, oh, we have two
front end developers like WunderGraph, like we don't need relay, but if you build front end with
like 100 people, yeah, you, you, you have different sets of problems.