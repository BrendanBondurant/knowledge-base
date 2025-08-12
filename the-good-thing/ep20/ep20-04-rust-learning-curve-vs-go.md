---
title: Rust Learning Curve vs Go
slug: ep20-04-rust-learning-curve-vs-go
series: The Good Thing
episode: 20
chunk: 4
participants:
  - Stefan
  - Jens
segment: Language Complexity and Developer Experience
timecode: 00:18:25:15 – 00:23:07:28
start_time: 00:18:25:15
end_time: 00:23:07:28
speakers:
  - Stefan
  - Jens
topics:
  - Rust's steep learning curve and borrow checker
  - Go's flexibility and ease of adoption
  - Developer experience differences
  - Language complexity trade-offs
tags:
  - rust
  - go
topic_tags:
  - rust
  - go
entities:
  - Stefan Avram
  - Jens Neuse
  - Rust programming language
  - Go programming language
mentions:
  - Rust borrow checker challenges
  - Go's simplicity advantages
  - Learning curve implications
  - Developer productivity factors
summary: Comparison of Rust's steep learning curve and borrow checker complexity against
  Go's flexibility and ease of adoption, examining how language complexity affects
  developer experience and productivity.
---
00:18:25:15 - 00:18:47:18
Jens
Problems we have is for example flakiness of tests. But again I'm not sure if if rust would help in
this case because those flaky tests, they typically they, they come from having dependencies
like testing something with Kafka. And in one run Kafka works fine and the timing is okay, and
then it works. In another test, the timing is somehow off.
00:18:47:18 - 00:19:01:20
Jens
You don't get the message at the right moment, or Kafka behaves in a in a weird way. So in this
case, the problem comes more from integrating external systems, which it's kind of independent
of of the, of the language.
00:19:01:23 - 00:19:03:23
Stefan
Yeah, that's a good point.
00:19:03:26 - 00:19:05:26
Jens
I'm not sure.
00:19:05:29 - 00:19:30:04
Stefan
It's a good transition to the next point. So I don't know if you've seen on the news, but I was
actually talking about this with my wife the other day. Let me share my screen, and we could talk
a little bit about this TechCrunch article. Let me know when you can see the screen. But
basically anthropics, new AI model started to blackmail when engineers tried to take it offline.
00:19:30:04 - 00:19:56:03
Stefan
And I want to drop a link later in the comments below. Jacob, make sure you remind me, but it's
this post that David shared with me, which is AI 2027. And I downloaded it onto my Kindle and
before I went on a plane, I read it. It's like about like 50 pages. It takes you an hour to read and
then i don’t know how to explain it, but it was basically just highlighting, like how AI was going to
go across the next couple of years.
00:19:56:05 - 00:20:16:00
Stefan
And one of the things that it was saying is, and you've noticed this and you like, you're the one
that actually taught me this, but when you're writing tests with AI, I writes the tests to just pass
them not to actually replicate or mimic the behavior that you're expecting, but just to pass the
tests. And it's doing that, it can happen.
00:20:16:00 - 00:20:19:09
Jens
It's not necessarily a must, but it can happen.
00:20:19:11 - 00:20:34:11
Stefan
But it happens. And what it's like, I'm slowly realizing, like the other day, is that, oh wait, we got
a comment here. Let's jump back real quick. Rusts biggest problem is barrier to entry for people
who've never used it requires a complete mental model shift. I would agree with that.
00:20:34:14 - 00:21:10:14
Jens
Jens, yes that's probably right. I mean, if you look at it, rust, it has this fantastic concept of, of
the life cycle of, of, of, like, how long does an object live? And, okay, how long does an object
live? And I think what's super interesting about rust is it makes it very explicit handling
ownership of, of objects and everything.
00:21:10:14 - 00:21:39:20
Jens
The, the borrow checker, that, David means. Yes. That's that's correct. And the problem is, when
you use go for many years, you build up that experience. You kind of know implicitly the life
cycle of an object. So you kind of know, okay, I have this object, I have this value. It's accessed
by different goroutines. I need to put a mutex around it or something.
00:21:39:23 - 00:22:08:12
Jens
You know this from experience in rust that that's not even possible to to write code without the
mutex because you, you cannot have a situation where, where two, two threads have
simultaneously access to, to the data. The problem is in go, if you don't see it, you have a data
race. And by the way, it's also not that like, in go, you just have no tools.
00:22:08:12 - 00:22:32:06
Jens
You can do absolutely nothing about it, because we also have a race detector in tests. And it will
also tell you about data races if you use it. Okay. You don't have a borrow checker, but again,
they're like both tools have a have a solution. The problem with rust is the entry bar is is really if
you don't get the borrow checker you're out and in go.
00:22:32:06 - 00:22:58:18
Jens
It's more like, yeah, write some code. And if you write some concurrent code, then eventually
you will run into bugs. But if you write a test with, race detector, then you could actually figure
them out and, Yeah, the the entry bar is, is higher. But in general, I think, what I said is, is, is
kind of correct.
00:22:58:18 - 00:23:07:28
Jens
And I, I'm not even sure how you would solve the problem because the borrow checker, it's
inherent to the language. So yeah. But coming back to your point, Stefan.