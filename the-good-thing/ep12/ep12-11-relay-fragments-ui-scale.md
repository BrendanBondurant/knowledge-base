---
type: podcast-chunk
title: Relay Fragments and UI Architecture at Scale
slug: ep12-11-relay-fragments-ui-scale
series: The Good Thing
episode: 12
chunk: 11
segment: Relay Benefits and Frontend Architecture
timecode: 00:38:22:29 – 00:42:26:21
start_time: 00:38:22:29
end_time: 00:42:26:21
speakers:
  - Stefan
  - Jens
topics:
  - JWT Validation
  - Relay Fragments
  - Component Data Requirements
  - UI Architecture at Scale
tags:
  - federation
  - graphql-federation
  - ai
  - authentication
  - authorization
  - cosmo
  - cosmo-router
  - go
  - graphql
  - open-source
  - rust
entities:
  - Relay
  - Facebook
  - React
  - Next.js
  - GraphQL
  - Stefan Avram
  - Jens Neuse
summary: Discussion of JWT validation for secure entity requests and Relay's fragment-based
  architecture. Jens explains how Relay enables component-specific data requirements
  through fragments, while Stefan questions what makes Relay special compared to other
  frontend frameworks and why it's not more widely adopted despite being open source
  from Facebook.
---

00:38:22:29 - 00:38:55:05
Jens
We would assume this combination of type name and keys exist. Or at least we need to validate
that it exists. Yeah. So the router kind of needs to trust the client that this combination of type
name and keys that we actually have it or so it, it can kind of be an attack because keys are
kind of like an internal concept and you don't want clients to guess.
00:38:55:07 - 00:39:18:01
Jens
And so if you if you don't have this JWT, clients can just send whatever combination of, of, of
entity keys and then they can figure out like if the server always says no doesn't exist. No no no
no no no no. And then eventually they say, oh yes, this exists. Then it means the client can
guess entities. And I don't think we want clients to guess entities.
00:39:18:09 - 00:39:45:21
Jens
So we give the client the JWT. We sign it. So the first thing that happens, if we make such a,
such a, relay node, signed relay, request, we verify the JWT so we know okay, we the router like
ourselves, we created this JWT because we can validate the signature. So that means first of
all, we can trust that we should process this request.
00:39:45:24 - 00:40:20:11
Jens
That's good. It's not authentication at this point it's a JWT. But we're not doing authentication.
That's the authentication already happened okay. So we now know that we can trust this combo
of type name and keys. And so we have translated the we have translated the the node relay
node request into an entity type name in keys. And we know what, what fields, the user, wants
to have and now we can, we can make our entity calls and fetch it.
00:40:20:13 - 00:40:40:00
Jens
And so yeah then then cosmo router could support natively support relay I think that would be
super dope. If anybody likes this idea then then, I don't know, give it a thumbs up or react
whatever. Comment like and subscribe.
00:40:40:03 - 00:40:45:18
Stefan
You're getting a few streamers. No it makes sense in. I mean, there's a lot to unpack there, but
okay.
00:40:45:18 - 00:40:49:23
Jens
No, no, you explain like, can you actually listen, explain to me.
00:40:49:25 - 00:41:07:11
Stefan
No. Not explaining relay to you. I'm thinking most people say about relay. Is that the fact that
you have to use relay, it is one of the best clients to use though, on the front end. If you're
working with GraphQL. But no. Well, what was that tweet that went viral of yours that you can't
have a discussion about Federation if you're not a federation about it?
00:41:07:13 - 00:41:11:22
Stefan
Not yeah, yeah. You can't talk about GraphQL if you don't mention relay, right?
00:41:11:24 - 00:41:37:26
Jens
Yeah. But yeah, honestly, I think a lot of people who like GraphQL know they are. They are not
like I like or a lot of people who really like to use GraphQL. I think, they are not just like, hey, I
really like to use GraphQL, but more like, I, I really love relay and because of that I'm using
GraphQL.
00:41:37:28 - 00:41:55:24
Stefan
But what makes relay so special? Like, abstract, like the abstract, the way the GraphQL, like,
okay, like there's a bunch of front end clients out there, react, Next.js and then there's relay.
What makes relay so special? What makes it so good and why aren't more people using it?
Also, relay is open source from Facebook, right?
00:41:55:26 - 00:41:56:18
Jens
Yeah.
00:41:56:21 - 00:41:57:06
Stefan
Okay.
00:41:57:09 - 00:42:26:21
Jens
It's it's just the way it works. So you know, let's say you have a UI component that shows you
the feed with not so much detail. So you create a fragment that defines what fields you need to
have this overview. Okay. Okay. All right. So you have this fragment for this component. Then
you have like let's say you have a feed detail page.