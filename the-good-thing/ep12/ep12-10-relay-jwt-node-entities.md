---
title: Relay JWT Node Entities and Secure Federation
slug: ep12-10-relay-jwt-node-entities
series: The Good Thing
episode: 12
chunk: 10
segment: Technical Implementation of Node Interface
timecode: 00:34:21:09 – 00:38:22:27
start_time: 00:34:21:09
end_time: 00:38:22:27
speakers:
  - Stefan
  - Jens
topics:
  - Entity Resolution
  - JWT-Signed Node IDs
  - Router Lookup Mechanism
  - Federation Security
tags:
  - federation
  - graphql-federation
  - ai
  - cosmo
  - cosmo-router
  - go
  - graphql
entities:
  - JWT
  - GraphQL Federation
  - Cosmo Router
  - Stefan Avram
  - Jens Neuse
summary: Jens details the technical implementation of secure entity lookup in federation
  through JWT-signed node IDs. He explains how the router maps node IDs to entities,
  prevents security attacks through JWT signing, and routes requests to the correct
  subgraphs while maintaining the integrity of the federation architecture.
---

00:34:21:09 - 00:34:22:01
Stefan
Okay.
00:34:22:04 - 00:34:48:26
Jens
Yeah. That's pretty like it's a, it's a great concept and it would be nice if you can just support it in
Federation. But there's a problem because you have entities theres a problem and an
opportunity. So you have entities and you have this node ID. And so if you have a node ID the
problem is you you take the node ID and you figure out what kind of entity is it.
00:34:48:26 - 00:35:13:18
Jens
Because it can be many things like all entities. So it can be whatever. So you figure out okay, it's
a feed item. And once you know it's a feed item, you need to know in which subgraph this entity
lives. So just by sending a node ID to the router, the router doesn't yet know where to get it
because the router like how should you know?
00:35:13:20 - 00:35:40:13
Jens
Like if it was an entity then we know, okay, it's an entity. We know what is the key. So we can
jump to the subgraph and get the entity by the key. So what we need to build is like a
mechanism into the router that understands how to turn a node ID into an entity. And then once
the router has an entity, it can fetch from the right subgraphs to the stuff.
00:35:40:15 - 00:36:06:21
Jens
So somehow, you know, I, I don't know why I somehow call it like, like in each entity, it somehow
has like a home, like it has one subgraph that that is the, the, like the home of an entity that's
like the entry point. Yeah. And so what I'm currently thinking maybe that's naive. Maybe the
people on the stream have a better idea.
00:36:06:23 - 00:36:34:15
Jens
And then you can comment that. But what I'm currently thinking is that we, we somehow take
the GraphQL schema, we annotate it and say this entity should be, should be, a node should it
should be a, it should have implement the node interface. We just annotate it somehow. And
then what is happening is, that it did it.
00:36:34:15 - 00:37:05:25
Jens
Okay. So what we will do is we annotate the entity and each entity, it has this key directive with
fields. Yeah. So my idea is that we create a field, it's called node on this entity. And that's the the
node ID and and the id it will actually be a Json web token. So the JWT can in the Json web
token we put multiple things.
00:37:05:28 - 00:37:33:08
Jens
So first of all we put the we put all the keys of the entity. So if the if the entity let's say the entity
has ID and SKU we put into the JWT, ID and SKU, and then we put into the, into its the, the
subgraph where it's where it's where this is coming from.
00:37:33:10 - 00:37:58:27
Jens
And we sign it because if we sign it, it means or imagine we wouldn't sign it. So a client comes
to the router and sends us a node request. One thing is missing. We need to have a type name.
So we need to have the type name. So feed item the keys and the subgraph where it's coming
from.
00:37:58:29 - 00:38:22:27
Jens
Actually I'm not even sure if we need the subgraph. I think type name and keys should be
enough. And then the the router can, can, figure it out. Okay. So we have this. We sign the JWT
and now the client sends us the request with the JWT y JWT. Imagine the client sends the
request and it gives us type, name and keys.