---
type: webinar-chunk
title: Debugging and Developer Experience
slug: 2025-08-25-08-debugging-and-devx
series: WunderGraph Webinars
date: 2025-08-25
speakers:
  - Demo Engineer
episode: null
chunk: 8
segment: Debugging and DevX
timecode: 00:43:21 – 00:45:12
start_time: 00:43:21
end_time: 00:45:12
topics:
  - Debugging
  - Developer Experience
tags:
  - debugging
  - developer-experience
entities:
  - Cosmo Connect
summary: |
  This segment demonstrates attaching a debugger to live plugins, streamlining developer workflows and testing.
---

00:43:21:00 - 00:43:45:00
Jens
They don't do like database stuff and everything. So yeah, you you could save a lot of latency,
but also, CPU so that means in the end you save money by replacing, a slow subgraph with a
gRPC subgraph. So that's just, something on the topic of performance. Cool. One thing before
we go. Sorry to it.
00:43:45:02 - 00:44:10:09
Dustin
I actually forgot something. I need to reshare my screen. I promise you in the beginning to show
how easy it is to debug the plugin. So I forgot that thing. So give me, one minute. So here we
are again. So because it's a subprocess spawned by the router, I can also just attach to this
process. So and you can see here now I make a query again.
00:44:10:11 - 00:44:15:12
Dustin
Okay. one sec.
00:44:15:14 - 00:44:18:01
Jens
Did you really want to do this.
00:44:18:03 - 00:44:22:14
Dustin
Yeah I will do it.
00:44:22:16 - 00:44:27:14
Dustin
Okay.
00:44:27:16 - 00:44:31:24
Dustin
So this was right one sec touch.
00:44:32:01 - 00:44:35:11
Jens
Have you attached to the plugin that is currently running with this router?
00:44:35:13 - 00:44:52:18
Dustin
Yes, this is fine. Otherwise it would, indicate a wrong debug breakpoint. But whatever reasons, it
does not work. Oh, sorry. Good bye. Makes sense one sec.
00:44:52:20 - 00:44:55:21
Jens
You you are not querying them, I think. Okay, here we go.
00:44:55:23 - 00:45:12:01
Dustin
It works. So you can fully inspect and everything that was sent by the router to a subgraph. And
it just plain vscode and probably compatible with any IDE out there. Yeah. Thank you.