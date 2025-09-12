---
title: Using Vectors and Embeddings to Map Queries to Schema Slices
slug: ep09-06-vectors-embeddings-query-mapping
series: The Good Thing
episode: 9
chunk: 6
segment: Vector databases and embeddings
timecode: 00:21:04:01 – 00:25:32:08
start_time: 00:21:04:01
end_time: 00:25:32:08
speakers:
  - Jens
  - Cameron
topics:
  - Root Type Slicing
  - Vector Databases
  - Embeddings Models
  - Query Mapping
tags:
  - graphql
  - ai
  - cosmo
  - benchmarking
  - database
  - federation
  - go
  - graphql-federation
entities:
  - GraphQL
  - Vector Database
  - Embeddings Model
  - Gemini
  - Claude
  - ChatGPT
summary: Cameron explains the technical approach of using vector databases and embeddings
  to map natural language queries to relevant schema slices. He details how root types
  are grouped and how semantic similarity through vector distances helps identify
  the most relevant schema portions, improving both accuracy and performance.
---

00:21:04:01 - 00:21:14:15
Jens
When when you say, yeah, I think you mentioned root types or something, right. Well, what is
the root type.
00:21:14:18 - 00:21:38:20
Cameron
A root type is, is basically what anything that is returned by an operation. So like if you have
create user and it returns a user and then you have get user and it returns a user, one slice
schema would have a query with get user and the mutation and type would have the operation
of create user.
00:21:38:22 - 00:21:48:05
Cameron
And so it's just that very base root type that is defined as a return type on the mutation or on the
query types or the subscription type.
00:21:48:08 - 00:21:56:15
Jens
So so you mean like the the fields on the root operation types like query, mutation, subscription.
00:21:56:17 - 00:21:58:15
Cameron
Yep. Exactly.
00:21:58:17 - 00:22:06:22
Jens
Okay. And so you take you take a root field or you take all of the root fields. And what are you
doing with each of them.
00:22:06:25 - 00:22:42:06
Cameron
Basically I'm grouping them by their return type. So I create like sub graphs of just only one
return type. So only have the user type or only of the search result type. And that allows me to
significantly reduce the size of the schemas and also reduce the context like not the context
size, but reduce the amount of information that I'm passing in because I'm only passing in one,
like there's only one real return type that's possible.
00:22:42:09 - 00:23:18:21
Cameron
And then I enable the model to use tools to actually find other types as well. So like for example,
you might in the GitHub schema, you might ask for the number of stars on the WunderGraph or
the WunderGraph Cosmo repository. And you might ask for the current user's username. And so
what it would do is you would return in the initial run, it would actually show, it would give the
repository and it potentially would return, for a secondary subgraph or for the secondary sliced
graph of the user, slice.
00:23:18:23 - 00:23:38:16
Cameron
However, even if it doesn't, the model actually has access through tools to enable it to re query
and re look up for different root types so that it can still access the data from other root types
and answer complex queries.
00:23:38:19 - 00:23:55:00
Jens
Okay. Got it. And one one other part you mentioned earlier is I think you you mentioned the term
vector. How how do vectors play into this whole exercise?
00:23:55:02 - 00:24:22:09
Cameron
Yeah for sure. So, we are using a vector database to do this, however, the way that, you know,
really in, in natural language processing works is that, I mean, really any artificial intelligence is
that you calculate, you turn everything into a vector. And specifically with natural language
processing, the placement of the vector is determinant of the similarity of words.
00:24:22:12 - 00:24:46:07
Cameron
So like, a user and human aren't the same thing, but they would be pretty close to each other. In
terms of where they are in the vector graphs. So you would be able to, to search for a user and
the distance would be filtered down by how far apart that vector between a user and a human is.
00:24:46:14 - 00:24:53:29
Cameron
And that's based off of the embeddings model that you use to actually generate those vectors.
00:24:54:01 - 00:24:57:10
Jens
Well what what is an embeddings model.
00:24:57:12 - 00:25:32:08
Cameron
The embeddings model is basically it's the tokenization model. So it's actually how the vectors
are calculated and it's trained on and it's trained on all of the data that goes into training
something like Gemini or Claude or, ChatGPT. So it, it holds where those, items live. So it like,
you know, like going back to the human and user, it the embeddings model would actually be
the one that would calculate and learn that human and use are near each other and close to
each other.