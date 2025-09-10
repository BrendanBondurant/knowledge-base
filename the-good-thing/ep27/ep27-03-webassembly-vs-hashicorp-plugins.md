---
title: WebAssembly vs HashiCorp Plugins
slug: ep27-03-webassembly-vs-hashicorp-plugins
series: The Good Thing
episode: 27
chunk: 3
participants:
  - Jens
  - Stefan
segment: Comparing plugin frameworks and deployment models
timecode: 00:10:23 – 00:16:52
start_time: 00:10:23
end_time: 00:16:52
speakers:
  - Jens
  - Stefan
topics:
  - WebAssembly
  - HashiCorp Plugins
  - Deployment Architecture
tags:
  - wasm
  - hashicorp
  - plugin-architecture
  - deployment
topic_tags:
  - wasm
  - hashicorp
  - plugin-architecture
  - deployment
entities:
  - HashiCorp
  - WunderGraph
mentions:
  - wasm tradeoffs
  - plugin runtime decisions
  - deployment considerations
summary: A deep dive into why WunderGraph evaluated WebAssembly versus HashiCorp plugins, focusing on runtime tradeoffs and deployment complexity.
---
00:10:23:03 - 00:10:55:17
Jens
One, one idea was also WebAssembly. But we, we didn't go for, for WebAssembly. Like, well,
let's and I ask everybody in the right, like, what's your take on like will WebAssembly ever be
like like the standard in extending something like a router or like why why did we go for, for
gRPC and and in general how you think about like, extending like a binary with custom
customer stuff.
00:10:55:19 - 00:11:25:04
Jesse
I can talk about this a little bit. I think that WebAssembly is great. And using things like shared
objects and DLLs is great, like the new go plug in system that's like officially a part of the
toolchain. However, one of the main goals of Cosmo Connect was to take the onus of the
complexity of importing graphical frameworks and all this subgraph nonsense and just make it
easy to do what you've always been doing, which is import protobuf Proto C Protoc gen
gRPCco.
00:11:25:04 - 00:11:49:15
Jesse
All these packages that everyone's used to and be able to federate those into the super graph.
And if we bring all the complexity of developing WebAssembly programs into that to replace it, I
don't think we've made much of a stride at all. There's issues with concurrency and language
support and all kinds of little gotchas with WebAssembly right now, especially if you're not using
a web browser as your runtime.
00:11:49:17 - 00:11:53:09
Dustin
So and you would also need to add your own SDK, right?
00:11:53:12 - 00:12:18:12
Jesse
Yeah, you absolutely would, because there's pretty much nothing available in WebAssembly.
There's no standard library. So you would have to provide all your own bindings to the
WebAssembly engine. It just a whole lot of extra new, like it's all greenfield for anyone
developing these things. And as opposed to gRPC, they have to learn this whole new
technology and how to work with it.
00:12:18:14 - 00:12:20:29
Jesse
And some languages, it's even outright broken.
00:12:21:01 - 00:13:03:14
Jens
So whenever someone comes up with like WebAssembly, like being a go dev, like, I think we all
tried WebAssembly, probably. And if you try out using WebAssembly and you're using a
garbage collected language and you know a little bit about architecture of programing language
and stuff like that, the first thing you kind of stumble into is, okay, if I want to get some
information into a WebAssembly thing and then call a function and get some other stuff outside
of the WebAssembly thing, what I have to do is I because very simply, the way it works, it
doesn't give you like garbage collection or something.
00:13:03:18 - 00:13:28:29
Jens
You have to allocate space space somehow get something in like copy it into the thing, into the
runtime, and then do something and copy some results into some other space and then get it
out. And I was always like, I don't know, I, you know, one thing I really like about go is and then
you can, you can, have opinions on, on rust and non garbage collected languages.
00:13:28:29 - 00:13:52:06
Jens
But what I really like about garbage collected languages is, I create an object and I do
something with it, and when it goes out of scope, then that's fine. And I don't have to think about
memory management and stuff because lots of other problems to solve. with WebAssembly You
have to think about this somehow, because you can't just randomly allocate stuff and not care
about things.
00:13:52:06 - 00:14:13:06
Jens
So, and I had discussions with the Dustin initially I wanted to go for WebAssembly, and he
quickly came up with alternative ideas. Maybe you want to to share some of your thoughts and
how we ended up using what we're now using, which is a pretty cool library from HashiCorp. I
think.
00:14:13:08 - 00:14:38:20
Dustin
Yeah, I think, I think Jesse, summarizes pretty well why we why choosing webassembly wouldn't
have been a good idea in in that, case. Then we explored like, for instance, like go also has a
capability to, to produce plugins, but those plugins only work, I think, on Linux. Right. And those
are like compiled. I think,
00:14:38:22 - 00:14:56:29
Jens
Libraries. go plugins are horrible. Like, yeah. One of the biggest problems is you must use the
exact same package versions of every dependency in the main binary and the plugin and yeah,
that's not fun.
00:14:57:01 - 00:15:21:15
Dustin
Yeah. So, so, first of all, we talked about WebAssembly and then we, then we I mean, the, the
whole, the whole initiative was driven by the idea that people doesn't need to recompile the
router. That was one of the design goals. So then WebAssembly, we figured out then for
obvious reasons, we didn't do this. Then we thought about like an and co processing model
where the router can spawn processes.
00:15:21:18 - 00:15:47:09
Dustin
Then we checked I think go plugins, which is obviously not a good choice. But then if you
research a little bit about go plugins, you will always find the HashiCorp library as the first,
search result. And because its so widely adopted also in HashiCorp vault and an all I mean a lot
of many HashiCorp product which which are serving millions of users per day.
00:15:47:12 - 00:16:11:03
Dustin
For us it was a good signal like it's production grade and it would give us all of these benefits we
are looking for, for, for instance, like, one of the goals of, of the, of plug of the plugin architecture
is also that we want to bring that aha effect. I mean aha effect immediately to a customer so
they can build things without redeploying services.
00:16:11:03 - 00:16:35:15
Dustin
It everything should be self-contained in the router. On the other hand, we also didn't want to
destroy the, the capability of deploying, deploying these services independently for, for high,
high traffic scenarios. So I think that was the perfect match because at the end is it's just a
gRPC service. And in case of a plugins, it is it has a different, transport.
00:16:35:17 - 00:16:52:18
Dustin
And in case of, gRPC services, it's, it's really handled as a separate, subgraph. So, yeah. Then
that was I would say the, the decent decision metrics in that at the time.

