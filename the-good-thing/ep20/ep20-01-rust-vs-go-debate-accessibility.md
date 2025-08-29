---
title: Rust vs Go Debate and Developer Accessibility
slug: ep20-01-rust-vs-go-debate-accessibility
series: The Good Thing
episode: 20
chunk: 1
participants:
  - Stefan
  - Jens
segment: Introduction and Programming Language Debate
timecode: 00:00:21:00 – 00:06:28:24
start_time: 00:00:21:00
end_time: 00:06:28:24
speakers:
  - Stefan
  - Jens
topics:
  - Rust vs Go
  - Developer Accessibility
  - LinkedIn Controversy
  - LLM Code Generation
tags:
  - rust
  - go
  - llm
  - ai
  - api-design
  - benchmarking
  - cosmo-router
  - query-planning
  - rest
  - startup
topic_tags:
  - rust
  - go
  - programming-languages
entities:
  - Stefan Avram
  - Jens Neuse
  - Rust programming language
  - Go programming language
  - LinkedIn
mentions:
  - Jens' LinkedIn post controversy
  - Rust vs Go performance trade-offs
  - Developer experience differences
  - LLM code generation impact
summary: Stefan and Jens discuss the Rust vs Go programming language debate, sparked
  by controversy over Jens' LinkedIn post about language accessibility and the impact
  of LLM-generated code on language choice.
---
Episode 20
00:00:21:00 - 00:00:41:25
Stefan
And we're live. Welcome back, ladies and gentlemen, to another episode of The Good Thing.
Just realized the end. We should probably start this. The good thing at 905. We're 5 or 6
minutes late. Because I feel like consistently, we're always 5 or 6 minutes late. But, guys, thanks
for waiting. Welcome back to another episode. Today we're going to be talking about go versus
rust.
00:00:41:28 - 00:01:00:08
Stefan
How Jens was chased off LinkedIn with pitchforks because of his take on rust versus go. We're
gonna be talking about AI threads. I don't know if you guys saw the news, but Claude is
basically blackmailing engineers and then OpenAI's IPO, which is insane if you think about it.
But, Jens. How are you doing today?
00:01:00:11 - 00:01:06:06
Jens
I'm good. You forgot one topic. I want to talk about the new plugin system we built.
00:01:06:09 - 00:01:10:17
Stefan
And we're going to do a little bit of marketing and talk about the new plugin system. No, no, no,
it's not marketing.
00:01:10:18 - 00:01:15:07
Jens
It's it's, information for developers.
00:01:15:09 - 00:01:34:15
Stefan
Exactly. It's information for developers. But, yeah, I mean, today is going to be a fun episode.
Let's kind of get right into it, which was the rust versus go. So you're probably gonna have more
context on this one, but let me share the linkedin post here. I just realized our content producer
is also there. Hey Jacob.
00:01:34:17 - 00:01:45:00
Stefan
But, this is kind of interesting. I'll read it out loud for the audience, but in the LLM generated
code era. Go wipe the floor with the rust. That's a bold statement, by the way.
00:01:45:00 - 00:01:47:04
Jens
a little bit aggressive, right?
00:01:47:06 - 00:02:06:10
Stefan
A little bit aggressive right away. Go in super fast, compiles super fast and is easy to read. Rust
is extremely fast, can be optimized heavily, takes forever to compile and nobody can read
Arc<Box<Box<dyn Fn() + Send + Sync>>>. I really like rust. Great language for some tasks.
However, most of us write code that doesn't benefit from rust.
00:02:06:10 - 00:02:18:15
Stefan
We need a simple language that can be easily read by average developers, not just the top 5%.
So I don't even think our funding announcement got this many likes. This got a lot of likes, by
the way.
00:02:18:18 - 00:02:19:08
Jens
It also.
00:02:19:08 - 00:02:40:12
Stefan
Got a lot of comments. Let's kind of go through it. Why would you put a box inside of a box? I'm
really interested. Please humor me. I don't even want to read your comment. Where did you put
it? Yeah, that's exactly question, but even it's fun.
00:02:40:15 - 00:02:59:15
Stefan
Oh my God, this is actually kind of great. I believe the opposite. In the llm generated code, error
readability takes a backseat to performance. Really? Opinions are my own I yes, they are your
own. I can tell in that regard. Rust is the winner. If a developer doesn't understand the piece of
code due to complex syntax, they can.
00:02:59:18 - 00:03:03:25
Stefan
There's nobody else. See how kind of dangerous that is?
00:03:03:27 - 00:03:37:28
Jens
It's not realistic. We need to be honest. Okay. So if we read this, I believe the upside in the LLM
generated code era readability takes a backseat on performance. In that regard, rust is the
winner. If a developer doesn't understand a piece of code due to complex syntax, they can
simply ask, okay, I think the the more realistic scenario that's going to happen, is you tell an LLM
to build a backend and it will it will build a backend.
00:03:37:28 - 00:04:07:03
Jens
And then you, you review the code. I think readability will be it will be the number one factor.
And to be honest, if we if we build a backend and it talks to some other system, a backend, an
API, whatever, performance is not going to be that much of importance. And even on the
contrary, I think and this is something I think a lot of people on this thread actually got got
wrong.
00:04:07:03 - 00:04:33:24
Jens
Like I'm. Yeah, because I wrote I like rust. And the thing is, if rust makes sense, I think in this
case I think you would write it by hand because you couldn't trust an LLM because I, I even
think in the, in the LLM era, I think that rust becomes even more important for critical code. But
in this case, you wouldn't write it with an LLM.
00:04:33:24 - 00:05:03:06
Jens
You would hand write it. Let's say you you write the code to, to to, yeah. To handle the software
inside an airplane or something. So let's say you're you're, you're not Boeing. Let's say you're
you're a good airplane company. Then you would use rust or something to write the most,
critical code to handle the steering or, I don't know, the management of the.
00:05:03:09 - 00:05:05:02
Stefan
Yeah. Going up and down.
00:05:05:04 - 00:05:21:05
Jens
Yeah. But, and you wouldn't do it with an LLM versus if we're just generating services, some
backend. I think go has a huge advantage because it's so easy to read, and performance is not
so critical actually.
00:05:21:08 - 00:05:40:07
Stefan
And they're both pretty for performant. Like we always get like comparisons there. Like okay.
Well how do you compare it to rust versus the go router. And what we've learned is like sure rust
can be a little bit faster. It also comes out to how we query plan and our data loader pattern. But
really I mean it's tradeoffs you have to make.
00:05:40:07 - 00:05:49:07
Stefan
Like for me I don't know I think this is funny by the way. Like how do you know if somebody uses
rust though. They'll tell you right here. Yeah.
00:05:49:09 - 00:06:28:24
Jens
But you know, there's another point I want to make. If we use AI to generate backend code, and
I think more and more of us will do it, then I think the the next part you need to think about is,
okay, who can actually do it? And learning Rust is harder than learning Go. So if we want to
have if we're a big enterprise and we want to have human resources to vibe code go versus
write code rust, it will just be easier to get talent to do it with go.