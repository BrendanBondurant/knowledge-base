---
type: podcast-chunk
title: Micro vs. Macro Benchmarks and Code Optimization
slug: ep05-09-micro-vs-macro-benchmarks-optimization
series: The Good Thing
episode: 5
chunk: 09
segment: The difference between micro and macro benchmarks, and the tradeoffs in code
  optimization
timecode: 00:51:27 - 00:56:04
start_time: 00:51:27
end_time: 00:56:04
speakers:
  - Jens
  - Stefan
topics:
  - Micro Benchmarks
  - Macro Benchmarks
  - Code Optimization
  - Readability vs Speed
  - Developer Experience
tags:
  - micro-benchmarks
  - macro-benchmarks
  - ai
  - benchmarking
  - cache-warming
  - cosmo-router
  - go
  - graphql
  - rest
  - startup
entities:
  - Jens Neuse
  - Stefan Avram
  - WunderGraph
summary: Jens and Stefan discuss the difference between micro and macro benchmarks,
  the dangers of over-optimizing code, and the tradeoffs between readability and speed.
  They share insights on garbage collection, benchmarking tools, and why real-world
  performance matters more than synthetic tests.
---

00:51:27:14 - 00:51:51:03
Jens
You just did a rookie mistake, but you're not a senior developer. It's fine. Like benchmarks are
useful. For example, I can run a local benchmark and I can enable pproff So pproffallows me to
analyze CPU usage and memory usage of the router. So I can enable people, if I can run a
benchmark, and then I can, for example, introspect.

00:51:51:06 - 00:52:10:13
Jens
What what is what is the number of memory allocations. How many objects have been allocated
and where in the code have they been allocated. And so it can help me as a developer to, to
optimize my tool and to also see like is there is the huge changes in behavior. But we have to be
like super careful.

00:52:10:13 - 00:52:39:27
Jens
And this is like one of the I would say big things I learned over the years of maturing as a
developer. There's micro benchmarks and there's macro benchmarks. Micro benchmarks is you
write like a go test and you micro benchmark, assume like a single function, and you then see
the allocations line by line, and you see where you spend CPU time.

00:52:39:27 - 00:53:10:00
Jens
And now you could go and optimize this function. And if you do this, what can happen? And it
will happen. If you're inexperienced you will optimize like so many functions and you will turn
your code into an absolute mess. Because like micro optimizations, the problem is let's say you
have a function and the function creates it allocates memory and that has to be garbage
collected.

00:53:10:06 - 00:53:33:21
Jens
So if you micro benchmark it it looks bad. So you're like okay, now I rewrite this function. I make
the code like typically code can be easy to read or fast. Like the faster you make the code, the
worse it reads. And that's you know, it's like, yeah. Do you want to be like super fast? Okay,
assembler. You want to be like somewhat slower and readable?

00:53:33:21 - 00:53:59:27
Jens
Okay. Go. And you want to be like faster, but use go okay, actually go. And yeah, you can write
super fast Go. And it's going to be more and more ugly, harder to maintain. And then you realize
something. This function in the broader scope, it almost gets never called. And so you micro
optimize something. You made the code harder to maintain.

00:54:00:00 - 00:54:19:26
Jens
But actually in the big in the grand picture, like let's say you micro optimize this and for each
request this function it creates, let's say ten kilobytes of of memory that need to be garbage
collected. And you know, like, oh, that's bad. Let's make it zero like zero garbage collection. Like
we, we build something amazing, okay. You optimize it.

00:54:20:03 - 00:54:44:21
Jens
And then in the big picture, let's say one request, it takes about 100MB of memory. So what is
ten kilobytes? Was it worth wasting your time in this function and then complicating this code.
And that's so yeah. You need to be very careful with micro optimizing stuff. It's sometimes it's
better to do like to do macro optimizing.

00:54:44:25 - 00:55:07:06
Jens
But even with macro optimizing like you're benchmarking the whole world and then you show
like the top ten memory problems. But even then you have this other problem of if you run pprof,
you would never see that when the customer scales up routers, the caches are cold. You don't
see that. You need to think about the architecture.

00:55:07:06 - 00:55:25:02
Jens
So if you want to make something fast, you can just benchmark your way to, you know, it's like A
B testing your way to product market fit. You can benchmark your way to, to to, good
performance. You really need to understand the architecture.

00:55:25:02 - 00:55:44:08
Stefan
And I think it's a good, like the way you explained it. From my point, though, it's not internal, like
we don't release our internal benchmarks, but we use them and we use competitors to make
our product better. But I think marketing benchmarks, I just think it illustrates a position of
weakness. And also you can always tweak them.

00:55:44:08 - 00:56:04:15
Stefan
And so that's my point on that. And then we are almost out of time. So last topic I want to talk
about you brought this one up. So you're going to have to lead it on this one. But Reddit is
always saying GraphQL is dead, GraphQL is dead. Or they're saying REST is REST. And
honestly REST versus GraphQL is a bit outdated, right?