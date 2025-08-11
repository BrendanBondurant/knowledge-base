---
title: Understanding Subgraph Jumps and Graph Traversal
slug: ep07-08-understanding-subgraph-jumps
series: The Good Thing
episode: 7
chunk: 8
participants:
- Jens
- Sergiy
- David
segment: Subgraph jumps and federation graph theory
timecode: 00:38:24:04 – 00:45:32:04
start_time: 00:38:24:04
end_time: 00:45:32:04
speakers:
- Jens
- Sergiy
- David
topics:
- Subgraph jumps as portals between services
- Federation keys and unique identifiers
- Root entry nodes and graph edges
- Microservices architecture and data isolation
- Graph theory vs tree structure in planning
tags:
- federation
- subgraph-jumps
- graph-theory
- microservices
- federation-keys
- entity-resolution
topic_tags:
- federation
- subgraph-jumps
- graph-theory
- microservices
- federation-keys
- entity-resolution
entities:
- GraphQL
- Federation
- Jens Neuse
- Sergiy
- David
mentions:
- science fiction portals metaphor
- user and address service example
- shareable directive
- resolvable false configuration
- composition vs query planning data structures
summary: Jens asks about the "jumps" concept in federation, which Sergiy and David
  explain as edges between subgraphs using federation keys. The discussion covers
  how federation enables microservices architecture, root entry nodes, and the difference
  between composition's full graph perspective and query planning's directed tree
  approach.
---

00:38:24:04 - 00:38:51:28
Jens
Yeah. What one thing that you guys keep talking about, and I keep hearing this, and I kind of
find it funny, is you keep talking about jumps and the. It kind of reminds me of, like, like science
fiction films or something, or a portal where you do, like a jump to something else or can you
explain it with like, well, what is your what is your idea behind jumps?
00:38:51:28 - 00:38:58:04
Jens
And how is that different from how other people think about Federation?
00:38:58:06 - 00:39:26:28
Sergiy
As a consumer federation, you just see a single schema like you file the queries like you have
all data in one. In one place and from outside versus the consumer. You just from, just talking
with one single graphql API, but, underneath you have multiple services and, you could have
subgraphs which have, root queries and which just do not have route queries.
00:39:26:28 - 00:40:02:15
Sergiy
It's, it's they provide some fields to their, like it basically contributes fields to the federated
schema, like whenever you have type user and maybe you have, addresses service which
provides you with an address. And this is like, Federation itself with kind of microservices
architecture. And when you design, designing, federation, schema or federation subgraph, you
typically want to isolate some, some kind of behavior or some kind of information and move it to
its own microservice.
00:40:02:17 - 00:40:33:22
Sergiy
But then, you need to be able to fetch that data and federation, standardize this way. Like during
my tenure, I have, a, I have seen a lot of approaches when you have just one GraphQL schema
from which is front facing and,under it you have a microservices and, this service with,
GraphQL, it's actually in its resolvers.
00:40:33:25 - 00:41:11:13
Sergiy
It's calls your PC. It calls multiple services and gathers this data and federation. And just
another way of, how you could fetch this data between different services. If we will talk about
what jump it is, jump is an event when, you get all the fields from the current subgraph and you
don't have any fields anymore, and you need to, fetch the fields from another subgraph, but
there is a rules for this jumps and that, basically in Federation, we have kind of unique
identifiers.
00:41:11:13 - 00:41:39:02
Sergiy
And, it is called keys. And, keys would consist of one or multiple fields or maybe set of nested
fields. And basically you need to provide this information to the second subgraph. And when,
you know, calculating jumps in composition, there is additional rules apply. So you, not always
will be able to jump to that subgraph.
00:41:39:04 - 00:42:06:15
Sergiy
And, that is why, like a shareable directive exist, because you could share responsibility resolve,
this field between different subgraphs. But then at some, to some degree, you could control like,
do you really want to jump to this subgraph or do you want to jump only from this subgraph?
Like, is it good accept inbound connections or will it be just only outbound jumps?
00:42:06:18 - 00:42:34:15
Sergiy
And, the most easy way to do that is just to use resolvable false, for example. And it make entity
not, not accepting incoming, incoming request just because you have no way to resolve an end
to from the subgraph. But you could easily jump from this subgraph. And, in this case, like you,
anyway, you will have some root query.
00:42:34:17 - 00:43:07:22
Sergiy
And, this root query, it will be just query mutation or subscription. And this means that your
request almost always will start from some particular subgraph, of course, unless you make this
query shareable. But, for sometime, seeing that it's not a good approach to make root query
field to shareable thing like, just splits responsibility between different subgraphs and, yeah, it
could be a bit weird to do that, but yeah, it is possible.
00:43:07:24 - 00:43:29:14
David
Yeah. To to add on what sergiy said like I like to think of this, is that you have an entry node.
Every GraphQL API has an entry node which is going to be your root of root field. So a query a
mutation or a subscription. And in federation your interface layer is your federated graph. But
under the hood that root field belongs somewhere.
00:43:29:14 - 00:43:57:01
David
It's owned by one subgraph or perhaps more than one subgraph. And that's your entry node.
And then you can think of your lateral jumps to other services as being edges, on a graph. So
you have your bespoke and you have a subgraph which is a bespoke graph. But then there are
these edges between different services in the shape of shared root fields, shared fields and
entity jumps.
00:43:57:03 - 00:44:18:01
David
And these are the edges that allow you to go from service to service. Which is all kind of, I
guess, abstracted away the client and the consumer to see this federated graph. But under the
hood, you have all these links in different ways between different, subgraphs. And we can kind
of refer to those as jumps, these edges between the services, the jumps.
00:44:18:08 - 00:44:23:04
David
And they can be entity jumps and they can be shared field jumps.
00:44:23:06 - 00:44:26:08
Jens
That's just one. Sorry. Go ahead. So you.
00:44:27:25 - 00:44:57:27
Sergiy
Just wanted to mention like, David just, described the, one main difference between, like, what,
metadata do we have in composition and what data do we have any query planning like at
composition type. Do you have like a full blown sub, graph? Like you use graph theory to do that
basically. And, you know, all entry points, you know, all all possible connections.
00:44:57:27 - 00:45:22:04
Sergiy
You have all these edges. But, when you do query planning, you basically have a query and it's
already determined, like, what is entry point is and query planning and just use tree structure.
It's not not a graph. It's more like a kind of directed graph, which has layers. And you go layer by
layer and see what is possible.
00:45:22:06 - 00:45:32:04
Sergiy
Like, it's a bit different context of, what data do you need? And what things are you checking