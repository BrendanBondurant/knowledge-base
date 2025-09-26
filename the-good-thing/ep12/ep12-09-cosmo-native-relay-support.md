---
type: podcast-chunk
title: Cosmo Native Relay Support and Node Interface
slug: ep12-09-cosmo-native-relay-support
series: The Good Thing
episode: 12
chunk: 9
segment: Relay Client Architecture and Implementation
timecode: 00:30:09:24 – 00:34:15:08
start_time: 00:30:09:24
end_time: 00:34:15:08
speakers:
  - Stefan
  - Jens
topics:
  - Relay vs REST/tRPC
  - Fragment Architecture
  - Node Interface
  - Cosmo Relay Support
tags:
  - cosmo-router
  - ai
  - api-design
  - cache-warming
  - cosmo
  - federation
  - go
  - graphql
  - graphql-federation
  - open-source
  - rest
  - rest-apis
  - event-driven-architecture
entities:
  - Relay
  - Isograph
  - Robert Belsky
  - Meta
  - Pinterest
  - Coinbase
  - Cosmo Router
  - Stefan Avram
  - Jens Neuse
summary: Jens explains Relay's power for large-scale frontend applications through
  fragment-based component architecture and normalized caching. He introduces the
  node interface concept for efficient refetching and announces plans for Cosmo Router
  to provide native Relay support, motivated by doing what's right rather than pure
  business value.
---

00:30:09:24 - 00:30:34:04
Jens
But if you have relay the it's it's a completely different role because with relay you define
fragments of what data do I need for which component and like clients like relay for example.
There's also Isograph from from a friend, Robert Belsky at what company is he currently
working at?
00:30:34:06 - 00:30:37:00
Stefan
And so, Robert, was at meta, but now he's at Pinterest.
00:30:37:02 - 00:31:10:03
Jens
Yeah. Okay. And so, yeah, clients like relay or ISO graph, they, they are so powerful in that you,
you get you get, yeah. The way you can build client architecture. I think if you reach a certain
scale of an application. It just becomes un maintainable if you have something like tRPC or Rest
APIs, you're making like too many calls and everything.
00:31:10:09 - 00:31:44:00
Jens
And this is really where, where, where those clients shine. I think that's, that was also a while
ago. There was a big post by what's is the website again? It's it has something to do with crypto.
Coinbase. Yeah I think Coinbase I think they are also using relay. They are. And yeah if you
build a large front end up like something like relay, it's just it's just fantastic to to work with so
much type safety.
00:31:44:03 - 00:32:12:23
Jens
You can easily refetch data and everything. By the way, one one thing I'm, I'm going on a
tangent on my tangent, but, we we are intending to bring native support for Relay to Cosmo
router because I personally like this. There's no value in doing it. Well that's maybe well, it's not
like we're not making money from doing it because it's just open source.
00:32:12:23 - 00:32:41:20
Jens
But you know, sometimes I want to do things because I think they are right. And I'm running a
company. But also, I don't know, I have a feeling for how should things work. And I think, one,
one thing that Federation, or at least our implementation of federation should, should have like
native support is relay. So what we're, you know, in relay you have this node interface.
00:32:41:20 - 00:32:44:16
Jens
Do you know what the node interface is.
00:32:44:16 - 00:32:48:22
Stefan
I don't so feel free to explain it for the audience because they might not as well.
00:32:48:25 - 00:33:16:04
Jens
So if you have a front end and in your front end there's let's say you have like a, like a feed and
you have a feed item and now you have a list of feed item things. And in the front end you have
a normalized cache of feed item things. Awesome. And let's say someone clicks like so. Now
that means we need to we need to refetch the feed item to show the new like or something.
00:33:16:04 - 00:33:43:09
Jens
Right? Yeah. And if you have, if you have a GraphQL API that has an entry point or a Rest API
that gives you like /feed or like the feed field that returns a feed, you have a problem because
you cannot re fetch that one item in the feed. You can just fetch the feed. And so over fetching,
ooh spicy take.
00:33:43:12 - 00:33:44:03
Jens
00:33:44:05 - 00:33:47:06
Stefan
So it is spicy.

00:33:47:08 - 00:34:21:06
Jens
Yeah. Where was it. Relay refetch. Okay. So in relay, that's a pretty cool concept. It's this node
interface and the node interface. It means that, you can send a node ID. So like a unique
identifier of a thing, you can send it to the server. And the server will re fetch the thing. And so
instead of fetching the whole feed you can re fetch the feed item just by giving the server an ID.