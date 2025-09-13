---
type: webinar-chunk
title: Plugins vs gRPC Services
slug: 2025-08-25-04-plugins-vs-grpc
series: WunderGraph Webinars
date: 2025-08-25
speakers:
  - Jens Neuse
episode: null
chunk: 4
segment: Plugins vs gRPC
timecode: 00:19:23 – 00:23:46
start_time: 00:19:23
end_time: 00:23:46
topics:
  - Plugins
  - Microservices
  - Deployment
tags:
  - plugins
  - grpc
  - deployment
  - event-driven-architecture
  - data-modeling
entities:
  - Cosmo Router
  - Cosmo Connect
summary: |
  Jens outlines how Cosmo Connect supports both standalone gRPC services and lightweight router plugins. He compares deployment tradeoffs between microservices and modular monolith patterns.
---


00:19:23:02 - 00:19:37:02
Jens
And, yeah, I think that's a great step forward. Cool. Here's how it works. We have two ways,
router, router plugins and gRPC services. What's what's the difference here.
00:19:37:04 - 00:20:00:08
Dustin
So in case of router plugins. So, so under the hood they are more or less the same. Your, your,
you’re starting with the graph, a schema, you're, converted into a protobuf. And then you from
that point on it's just gRPC tooling. You can leverage any language you want. The the difference
between router plugins and GP services is the way how you deploy them.
00:20:00:08 - 00:20:29:03
Dustin
So for for small teams and for local development, you can let the router, supervise, manage the
spawning of these plugins, which, essentially, subprocesses, by the router. And here we also
leverage leveraging a technology also used by millions of, of, deployments of, HashiCorp, for
instance, it's go plugin. Architecture of, of, HashiCorp.
00:20:29:05 - 00:20:52:17
Dustin
And however there is also absolutely the need in order to deploy services standalone for
example, you want to, maintain them, operate them in multiple teams, or you just want to scare
them out for, for efficiency reasons. In that case you would handle a GRPC. service as nothing
more than just a subgraph, with a routing URL and a GraphQL schema.
00:20:52:21 - 00:21:15:20
Dustin
So our in cosmos cloud, our cloud does not doesn't know anything about gRPC because we are
operating on the schema level. And as long as everything is composable and there is a valid
routing URL behind the subgraph, everything works as before. So the frontend knows nothing
about gRPC. The background, the backend can really focus on implementing their business
logic.
00:21:15:22 - 00:21:41:19
Jens
Yeah. And just as a side note, thanks for the explanation. You can actually have gRPC plugins
and gRPC services and Apollo GraphQL subgraphs side by side together. It's for the router. It
doesn't matter. It can speak to all of them together and then combine entities from one and the
other. And you can mix and match.
00:21:41:21 - 00:21:53:14
Dustin
And there's one more point I would highlight in this, jesse should explain that we also have a
very tight integration with Cosmo Cloud when it comes to router plugins deployments. Could
you, could you elaborate on that?
00:21:53:16 - 00:22:22:11
Jesse
Yeah. So when you're using Cosmo and the router and developing plugins with the Cosmo
Cloud product, you don't actually have to handle the deployment of your routers directly into
however you're deploying your router. You can actually publish them directly through our CLI
wgc to the registry for plugins we have set up, and the router is able to pull them down
alongside your configuration for your super graph and run them and reload them alongside your
your main configuration.
00:22:22:13 - 00:22:34:23
Jesse
We can talk about this more later I think, but yeah. In short, there's very good integration with
live deployments and matching up with the exact schema changes in lockstep with the router.
00:22:35:00 - 00:22:47:17
Dustin
That means you can decide if you want to build a huge monolith for simplicity, for for fast
iterations or your, scale them out as individual deployments on your Kubernetes cluster, as
separate pods, etc..
00:22:47:19 - 00:22:50:05
Jesse
Yeah.
00:22:50:07 - 00:23:19:12
Jens
You could even say if you want it with plugins, you can build like a modular monolith, or you
make it a microservice architecture. But, you know, most of the time when we talk about
modular monolith versus microservices, it's actually very hard to turn a modular monolith into
microservices. With Cosmo Connect, you can deploy the services as plugins, and one day you
decide, oh, this one plugin, it's overloading my router.
00:23:19:14 - 00:23:46:02
Jens
I move it into a service and you just deploy it differently and that's it, because plugins are
isolated processes. So yeah, that's just as a side note. Okay, I see where we're we're actually
quite busy with, with the intro. I want to give Dustin as much time for the live demo. Now, that
being said, we have a question already.