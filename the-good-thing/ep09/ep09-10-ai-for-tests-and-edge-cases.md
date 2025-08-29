---
title: Using AI for Test Generation and Second Set of Eyes
slug: ep09-10-ai-for-tests-and-edge-cases
series: The Good Thing
episode: 9
chunk: 10
participants:
  - Jens
  - Cameron
segment: AI testing and validation approaches
timecode: 00:36:35:05 – 00:40:00:11
start_time: 00:36:35:05
end_time: 00:40:00:11
speakers:
  - Jens
  - Cameron
topics:
  - AI Test Generation
  - Reverse Validation
  - Edge Case Discovery
  - Implementation Bias
tags:
  - ai
  - go
  - rust
topic_tags:
  - ai
  - validation
  - edge-cases
entities:
  - Cursor
  - Go
  - JSON
mentions:
  - abstraction layer implementation
  - hard-coded literals vs dynamic code
  - AI as second set of eyes
  - context file selection
  - test case bias prevention
  - edge case generation
summary: Cameron shares his reverse approach to AI-assisted development, using AI
  for test generation and validation rather than primary implementation. They discuss
  how AI can discover edge cases without implementation bias and serve as an unbiased
  second set of eyes, though context management remains important.
---

00:36:35:05 - 00:36:56:01
Jens
And I had like over and over and over I had to force it and tell it like, hey, don't, don't do that. Do
dynamically write code that looks at the AST and that derives this kind of function and that that
was really, really, really tough because, I don't know. It just wants to, to go like the simple route.
00:36:56:05 - 00:36:59:21
Jens
But do you have similar experiences?
00:36:59:23 - 00:37:25:18
Cameron
Oh yeah. There. Very much so. I have, you know, I there was something the other day that I
was working on, where I was working on doing an implementation of, within our, artificial
intelligence work, that of kind of an abstraction layer. And it just kept wanting to over even
override me sometimes, which was a little frustrating.
00:37:25:20 - 00:37:53:13
Cameron
Because it would want to override me to actually put in, like, hard, hard coded, defined literals
as opposed to doing something dynamically and actually extracting it to where it is an
abstraction layer and not just, copy and paste of JSON information into Go, so it. Yeah, that's
why like for me, I really have enjoyed using it to do kind of the opposite of, what Jens has been
using it for.
00:37:53:13 - 00:38:17:28
Cameron
I'm using it to write tests, to validate, the code that I've written or to write help write comments
out to kind of almost using it like my second set of eyes, as opposed to the, as opposed to the
like, you being the human being, the second set of eyes, almost doing it kind of reverse.
00:38:18:00 - 00:38:30:13
Jens
If you have the model writing the tests, which is it? I think it's a good idea. Can you somehow
ensure that it's not looking at your implementation?
00:38:30:16 - 00:38:36:16
Cameron
It probably will look at the implementation, to be honest.
00:38:36:19 - 00:38:37:04
00:38:37:06 - 00:39:12:04
Cameron
I, I yeah, probably I mean, you can, my cursor at least I know you can define what files it uses
and context, but, yeah, my guess is that odds are there is, you know, something that enables
that to look back at the implementation. However, I think that that is somewhere that AI is
hopeful in is that humans might look at that implementation and have a bias towards ensuring
that it works and ensuring the tests pass, whereas AI is not necessarily going to have that bias.
00:39:12:07 - 00:39:31:01
Cameron
Whereas, you know, I've found that. It's more likely to come up with test cases that are failing
even in a state that I would expect, like. I found it comes up with some crazy edge cases
sometimes. Is what I'm getting at there.
00:39:31:04 - 00:39:52:26
Jens
Yeah. You know, I, I was thinking it's a bit like the, like, the pink elephant kind of scenario. If you
tell it, don't look at implementation. Don't go, what will it do? Will it ignore that. Will it think, oh,
you mentioned implementation, but but.
00:39:52:28 - 00:40:00:11
Cameron
You know my guess is it's going to it's, it's going to go after the second one. And I kind of want
to try that now and see what happens.