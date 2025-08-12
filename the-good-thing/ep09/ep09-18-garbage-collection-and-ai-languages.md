---
title: Garbage Collection, Compiler Concerns, and Language Considerations for AI
slug: ep09-18-garbage-collection-and-ai-languages
series: The Good Thing
episode: 9
chunk: 18
participants:
  - Jens
  - Cameron
segment: Programming languages for AI development
timecode: 01:04:23:27 – 01:08:05:29
start_time: 01:04:23:27
end_time: 01:08:05:29
speakers:
  - Jens
  - Cameron
topics:
  - Rust borrow checker complexity
  - AST transformation challenges
  - Garbage collection advantages
  - TypeScript to Go migration
  - AI development language preferences
  - TypeScript compiler integration
  - Kotlin for backend development
tags:
  - ai
  - typescript
  - benchmarking
  - go
  - rust
topic_tags:
  - garbage-collection
  - rust-borrow-checker
  - ast-transformation
  - ai-languages
  - typescript
  - kotlin
  - compiler-feedback
entities:
  - Rust
  - Go
  - TypeScript
  - Kotlin
  - TSC Compiler
mentions:
  - borrow checker lifetime management
  - AST rewriting complexity
  - stop-the-world GC scenarios
  - compiler memory management
  - TypeScript compiler feedback loops
  - backend language preferences
summary: Jens compares language complexity for compiler development, highlighting
  how Rust's borrow checker creates challenges for AST transformations that Go and
  TypeScript avoid. He discusses garbage collection benefits in compiler contexts
  and suggests TypeScript as ideal for AI development due to immediate compiler feedback,
  while noting Kotlin's popularity for backend AI applications.
---

01:04:23:27 - 01:04:59:24
Jens
It has almost no magic. And you can probably if you don't use so much, so much functional
programing, you can probably go quite straight forward from TypeScript to Go versus with rust if
you build parsers and other things, and if you transform ASTs, one thing you have to deal with in
rust is this, this borrow checker, which helps you understand the lifetime of, of values.
01:04:59:26 - 01:05:30:28
Jens
And then you, you, you get into the problem where, okay, let's take an AST and you want to
rewrite it. So how long will that thing live and etc., etc.. So you have a whole bunch of problems
that TypeScript and go they simply don't have, which means just by high level looking at the
code, the go code would be quite similar to to TypeScript versus rust would be more, more
complex, more complicated rust.
01:05:30:28 - 01:05:54:17
Jens
It would probably give you better, better performance out of the box. With go. You can also be
pretty fast, but at the same time there's this tool, um I'm not sure if I remember, but there's,
there's tooling in go already to compile, TypeScript like bundle it. So there's bundlers some,
written in go and they are quite fast.
01:05:54:19 - 01:06:29:17
Jens
So, yeah, I mean go is quite performant. And I think in general, garbage collection can be a
great feature because you don't have to think about memory management at all. And if you, if
you write, you know, if you write a web server, you are somewhat concerned around like things
like garbage collection in the sense that you can have stop the world scenarios where the
garbage collector really blocks your server from doing something.
01:06:29:17 - 01:06:41:22
Jens
So if a new request comes in to the server while the server is GCing, you can have latency
spikes. At the same time, if you build a compiler, that's that's.
01:06:41:27 - 01:07:08:29
Jens
Not Really something you're worried about. You stop the compiler, it does the thing and then it
ends and you just free the memory. So I'm not sure like GC is not a concern. Because you have
so much memory, you probably just run through your work without doing GC at all and then just
throw away the memory. So that might even be, a good scenario so I can kind of understand it.
01:07:08:29 - 01:07:42:13
Jens
I, I was super surprised when I saw it, I, I, I would have never thought that someone would write,
in, in, in go, but at the same time, if you talk about the topic of what are good languages, to, to
write, code in AI and I think for web development, I would always and I'm curious about your
opinion, but I would always choose TypeScript simply because, you let it code something.
01:07:42:13 - 01:08:05:29
Jens
And the first thing you can do is you run the TSC compiler, and whatever comes back, you
throw it back, to the, to the AI to, to correct that. So I think that's, that's, that's one, one pattern.
And then on the backend side, I saw a lot of people who like Kotlin, like when, when it comes to
backend, lots of people like like Kotlin, I haven't used it so much.