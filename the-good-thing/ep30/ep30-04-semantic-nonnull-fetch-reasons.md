---
type: podcast-chunk
title: Semantic Non-Null Handling and Fetch Reasons
slug: ep30-04-semantic-nonnull-fetch-reasons
series: The Good Thing
episode: 30
chunk: 4
segment: Cosmo Federation Improvements
timecode: 00:09:31 – 00:11:50
start_time: 00:09:31
end_time: 00:11:50
speakers:
  - Jens
topics:
  - Semantic Non-Null Handling
  - @requiresFetchReasons Directive
  - Safety Improvements
  - Error Handling
tags:
  - graphql
  - federation
  - cosmo
  - compliance
  - graphql-federation
entities:
  - Cosmo
  - @requiresFetchReasons
  - Federation
  - Subgraphs
summary: Jens introduces semantic non-null handling and directives like `@requiresFetchReasons`, highlighting how Cosmo's Federation model improves safety and error handling between subgraphs.
---

00:09:31 - 00:09:58
Jens
So it creates a loophole in your system. There's there's a component of authorization where you think authorization is something that happens between the client and the server in federation, authorization also happens between subgraphs. And it's very important to think about the mechanics and what happens if one subgraph requires a field from another one. So we introduced a new directive.

00:09:58 - 00:10:29
Jens
I think it was something like, fetch reasons or. I don't know, David, you can tell me what's the what's the right name. It's also unorthodox. And if you can enable that, you, you we will essentially tell in metadata. One subgraph, we will we will tell them that, yeah. Require fetch reasons. Thanks, David. So, you if you put that on a field and the field is being requested, we tell the subgraph why we are requesting it.

00:10:29 - 00:10:58
Jens
And so now we're, we're, compliant. Another issue we we found through eBay. EBay is also again requires if you require fields from another subgraph. And that field, that field, doesn't resolve and it returns an error and the field is nullable. We will then render an an entity representation call to that subgraph and send null.

00:10:59 - 00:11:27
Jens
And this is a problem because, yeah, null might not be like a valid key or something. So then the second, subgraph is confused because it requires that field. So if there was an error, we should actually stop or we should think about the meaning of null. And that is another interesting topic. We recently, added support for semantic non null.

00:11:27 - 00:11:50
Jens
There was, like a huge discussion in the GraphQL community, around semantic, non null. And how can you distinguish, nothing. Well, where nothing has a meaning. So absence of a value can have a meaning, or it can mean there is no data or it can mean there was an error. And you need to distinguish all these cases and semantic non null does that.
