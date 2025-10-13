---
type: podcast-chunk
title: Entity Layer EDFS and Event-Driven Architecture
slug: ep30-10-entity-layer-edfs-event-driven
series: The Good Thing
episode: 30
chunk: 10
segment: Event-Driven Federation
timecode: 00:26:26 – 00:30:15
start_time: 00:26:26
end_time: 00:30:15
speakers:
  - Jens
topics:
  - Entity Layer Caching
  - EDFS Streaming
  - Event-Driven Architecture
  - Real-Time Federation
tags:
  - cosmo
  - edfs
  - graphql
  - federation
  - kafka
entities:
  - EDFS
  - Entity Layer
  - Event-Driven Architecture
  - Kafka
  - Streaming
summary: Jens elaborates on the entity layer's caching and streaming capabilities through EDFS, linking entities to event-driven architectures for real-time federation updates.
---

00:26:26 - 00:27:07
Jens
Done. Okay, so that's the backend side. So on the backend side why why GraphQL. We we don't need it. But what we need is entities. So again entities. And then on the front end side there's like a big group of people who absolutely fell in love with relay and Fragments. And I belong to that group, big fan like I think like the triple D, like data driven dependencies defining your data requirements per UI component with a fragment, hoisting up the fragments, compiling them into one query per route, etc., etc. I think that's the right approach.

00:27:07 - 00:27:32
Jens
However, not so many people need that, and there are many API consumers who would prefer something different. Like for example, MCP doesn't care about fragments at all. We don't need relay, we just need to have like a query or like maybe we want an SDK. Also doesn't need like SDKs don't benefit from GraphQL. It's just overhead. Just give me an SDK.

00:27:32 - 00:27:58
Jens
So an SDK, ideally it's just kind of like a rest API or at least like JSON RPC. So that means on the left side of the router on the client side we could have GraphQL. We we we we could have MCP, we could have json, RPC or whatever. And on the right side we could have GraphQL. But we could also have gRPC or something.

00:27:58 - 00:28:26
Jens
So that leaves us in the middle with well if we don't always need federation then maybe we need to have a better term for for defining what this middle tier is actually about. And for me it's all about entities. So that's why I call it the entity layer. And from my perspective, the entity layer is extremely powerful. You have objects.

00:28:26 - 00:28:57
Jens
Each object is an entity. If it has a key. This key uniquely defines how we can find in our microservice architecture how we can find this thing. And the router knows what subgraphs to ask to get information about the thing. The router knows that we use the key to go to the subgraph, and the router knows from the subgraph schemas which subgraph has which fields on the entity.

00:28:57 - 00:29:25
Jens
So the entity layer is like a graph of types with unique identifiers. And these unique identifiers. They are absolutely amazing because what they give us is, we can use them as cache keys so we can stick an entity into Redis, and we can get it back from Redis through the name of the type of the entity and the, the, the, the key.

00:29:26 - 00:29:55
Jens
Or we can use EDFS event driven federated subscriptions or how we call it lately, Cosmo streams, where you have a Kafka topic and you get messages and each message contains a type name and, key. So it's actually, it's an entity. And so you have entities, you can access them from subgraphs, you can use them for caching, for cache invalidation.

00:29:55 - 00:30:15
Jens
Or you could even use like, cache, like backend cache filling mechanisms. You could say, oh, if something changes in the back end, you put a message on Kafka. The router reads that resolves the entity from subgraphs and sticks it into Redis. So next time a consumer comes there, they can actually read that right from the cache.
