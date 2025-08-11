---
title: TypeScript Rewrite in Go and Tradeoffs vs Rust
slug: ep09-17-typescript-go-rewrite-vs-rust
series: The Good Thing
episode: 9
chunk: 17
participants:
- Jens
- Cameron
segment: Microsoft TypeScript rewrite discussion
timecode: 01:01:20:10 – 01:04:23:25
start_time: 01:01:20:10
end_time: 01:04:23:25
speakers:
- Jens
- Cameron
topics:
- Microsoft TypeScript compiler rewrite
- Go vs Rust for compiler development
- Language characteristics and trade-offs
- GitHub's internal Go usage
- Garbage collection in compiler context
- Function-by-function rewrite approach
tags:
- typescript-rewrite
- go-language
- rust-language
- compiler-development
- microsoft
- language-tradeoffs
topic_tags:
- typescript-rewrite
- go-language
- rust-language
- compiler-development
- microsoft
- language-tradeoffs
entities:
- Microsoft
- TypeScript
- Go
- Rust
- GitHub
- C++
- Java
- Python
mentions:
- Microsoft language background
- C/C++/C#/.NET heritage
- Go language characteristics
- compiler rewrite strategies
- GitHub Go usage
- garbage collection benefits
summary: Cameron expresses excitement about Microsoft choosing Go over Rust for the
  TypeScript compiler rewrite, describing Go as combining the best of C++, Java, Python,
  and TypeScript. Jens explains the practical advantages of Go's similarity to C and
  how garbage collection actually benefits compiler development, making function-by-function
  rewriting more straightforward.
---

01:01:20:10 - 01:01:22:26
Jens
What are your thoughts on this rewrite?
01:01:22:28 - 01:01:48:11
Cameron
Yeah. I think it's very interesting. So, I'm a big fan of TypeScript. I use, I've used it frequently for
front end and for some backend stuff. You know, on the, in the AI space, it has its place. It's
being used more and more and supported by more and more groups. I think, you know, it's
great for having just a basic serving engine.
01:01:48:11 - 01:02:17:26
Cameron
So just to be able to, you know, pass three requests back to like the open AI, API or for, you
know, quickly scaffolding those types of things. But it's, you know, for model training. And for,
you know, actually doing any kind of like experimentation around models, I'm going to choose
other languages other than TypeScript. But that being said, I do think it's very interesting that
they chose go.
01:02:17:29 - 01:02:45:09
Cameron
You know, that it was something that I did not necessarily see coming with Microsoft. I, you
know, I you hear constantly about the about compilers being written in rust or C honestly. And to
me, you know, Microsoft, their entire background is in c, C++, C#, you know, .net, all of those
things.
01:02:45:09 - 01:03:15:19
Cameron
So I'm actually pretty pretty shocked and honestly excited that they've decided to go the route of
go because I feel like go is a language. I always, say that it really feels like the best of like C++,
Java, Python and TypeScript all in one. So I feel like it's, it's a language that has a lot of power
and has and has the ability to do more than we typically do with it.
01:03:15:19 - 01:03:27:11
Cameron
So I think it's exciting to see a large compiler for one of the mainstream, languages be rewritten.
In something like Go.
01:03:27:13 - 01:04:23:25
Jens
Sidenote GitHub actually uses go internally to, to, to write some of their, the backend logic. But
aside from that, what I find interesting. So I, look at some of the discussions around this rewrite
and, and yeah, obvious question like why, why not rust and some of the explanations I really, I
watch, an interview and what I really or what resonated a lot is when you have the compiler
written in TypeScript, which is a garbage collected language, and you rewrite it in go, and if you
go like function by function, go is, very similar to, to C, I would say it has structs.