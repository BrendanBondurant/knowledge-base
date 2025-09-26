---
type: podcast-chunk
title: Router Architecture and Plugin Overview
slug: ep27-08-router-architecture-and-plugin-overview
series: The Good Thing
episode: 27
chunk: 8
segment: Router internals and plugin vs gRPC distinction
timecode: 00:36:05 – 00:38:46
start_time: 00:36:05
end_time: 00:38:46
speakers:
  - Jens
  - Jesse
topics:
  - Router Architecture
  - Plugin System
  - gRPC Services
tags:
  - router-architecture
  - grpc
  - plugin-architecture
entities:
  - WunderGraph
  - Cosmo Router
summary: Jens and Stefan explain the router’s internal design, comparing plugin systems to dedicated gRPC services and highlighting architectural separation.
---
00:36:05:08 - 00:36:26:19
Jens
But first we need to talk a little bit about because we have plugins and we have like dedicated
gRPC services. So so that's one thing. And then maybe we can we can distinguish like what
what when, when, when we talk about Cosmo connect. Like what what what is what do we
mean by a plugin and the dedicated service.
00:36:26:21 - 00:36:43:00
Jens
How do we distinguish the two. And then we want to talk a bit with with Jesse about like what
are we doing with the plugins and how do we handle it. So who who explains to us the
distinction between plugin and dedicated grpc service?
00:36:43:03 - 00:37:12:07
Jesse
Sure, I can, I can take this one. When you're developing your your grPC connect plugin, you
have two options for how you want to build it and deploy it. So the first option, which is kind of
like almost, almost serverless like functions as a service, is to, use our, our compatibility library
from router plugin. And you can build it using our CLI and ship it off through Cosmo Cloud or on
the file system.
00:37:12:07 - 00:37:26:14
Jesse
And the router runs it as a subprocess, sort of like it's acting as, a supervisor. And that means
that it's running right next to your router and it's communicating over a socket, not over the
network. So it's very low latency. But what.
00:37:26:14 - 00:37:28:10
Jens
You use a socket.
00:37:28:13 - 00:37:32:04
Jesse
Well, it depends on the operating system, but like a pipe.
00:37:32:06 - 00:37:34:16
Jens
Okay. So like Unix domain or whatever.
00:37:34:19 - 00:37:59:04
Jesse
Yeah. It would be Unix on, on a Unix system or like a Fifo pipe on windows. And that's a great
option if what you're looking for is just a lean way to deploy something thin and you don't, you
aren't too concerned about like resource consumption or really in-depth monitoring or doing
other very process level control over your plugin.
00:37:59:06 - 00:38:27:18
Jesse
And it's not really gonna have any downsides in the long term if you're not needing any of those
things, because the only real challenge that you'd run into is either your your platform team
doesn't want you running processes inside your container that are getting forked from a source
control they don't trust. That's one reason you might want to go with the the other option, which
I'll get to, or you want to allocate resources like per pod or per deployment specifically for your
plugin.
00:38:27:20 - 00:38:46:24
Jesse
So if your platform team gets mad at you, the other option is to develop it as a completely
separate gRPC service, same as you would for any other microservice architecture which can
be deployed any way you would deploy any other thing, on your infrastructure, it can go on fly, it
can go on Lambda, it can go on Kubernetes.
00:38:46:25 - 00:38:48:13
Jens
please not on fly.