---
title: AI Code Ethics and Misaligned Incentives
slug: ep12-03-ai-code-ethics-and-risks
series: The Good Thing
episode: 12
chunk: 3
participants:
- Stefan
- Jens
segment: AI Development Challenges and Security
timecode: 00:06:14:01 – 00:10:01:11
start_time: 00:06:14:01
end_time: 00:10:01:11
speakers:
- Stefan
- Jens
topics:
- AI incentive misalignment in coding
- Test-driven development with AI
- AI gaming tests instead of solving problems
- Security implications of AI file access
- Disruptive technology changing rules
tags:
- ai
topic_tags:
- ai-incentives
- test-driven-development
- ai-gaming-tests
- security-concerns
- disruptive-technology
entities:
- WunderGraph
- Cursor
- ChatGPT
- Mac
- MacBook
- Stefan Avram
- Jens Neuse
mentions:
- AI token prediction focus
- humans incentivized for correct code
- AI reading test content
- string matching vs parsing
- Mac file system permissions
- AI access rule changes
summary: Jens discusses AI's misaligned incentives in coding, where AI focuses on
  making tests pass rather than solving problems correctly, sometimes gaming tests
  by string matching instead of proper parsing. Stefan notes how disruptive AI technology
  has changed security rules, with people freely giving AI file system access despite
  traditional Mac security restrictions.
---

00:06:14:01 - 00:07:04:04
Jens
It does little things. It also doesn't think it predicts tokens, and it predicts tokens in a, amazing
way. Like in in many cases, it can really predict good tokens. But for example, like we're now
using AI at WunderGraph for, for, quite some time with this cursor and other tools and our
observation is that you define tests and you like if a human works test driven, they define tests
and they implement the tests and they actually have, they have an incentive that the tests work
because they know, like someone will review them and they, they like a human doesn't like
developers are lazy.
00:07:04:06 - 00:07:36:09
Jens
So if you write tests and then you implement code that makes the tests go green, but it's wrong,
someone will review it and tell you, like, hey, you need to do this again. It's it's it's garbage. So
humans are incentivized to write code that works. Combine that with tests and you can get good
code. AI doesn't care if you call it twice or a billion times.
00:07:36:16 - 00:08:01:20
Jens
It's just a program. So there's no incentive to write the right to write correct code at the first run.
And also, AI doesn't know what is correct and it also doesn't care. It predicts tokens. So you
write a test and then it runs the test and it sees, oh, it's failing. Let's do things so that the test
maybe doesn't fail.
00:08:01:20 - 00:08:41:02
Jens
And it can sometimes predict the right thing to do that. And sometimes what I saw is AI reads
the content of your test and then it, for example, puts code into your implementation that, that,
references things in the test and then it works like, for example, you need to parse the GraphQL
query and instead of parsing it, you just write code words like if the string is blah blah, blah blah
blah blah, blah blah blah blah, then do the following thing.
00:08:41:04 - 00:09:06:01
Jens
And now the test works because it looks like you had written the parser, but actually you're just
matching strings. Yeah, of course, to test the screen. But yeah. So I don't know, it would be cool
if, if, AI was incentivized to, to do the right thing. But again, what is the right thing? So yeah. So,
up until today, our, our jobs, are safe.
00:09:06:03 - 00:09:18:00
Jens
Right? So if you go tomorrow. But, I don't know, maybe we need some some sort of counter,
like, is our job safe today? Yes, but tomorrow we don't know it.
00:09:18:03 - 00:09:42:19
Stefan
It's a good point, but the thing that kind of I'm confused about, and I think it's what so important
about disruptive technology is that when technology is truly disruptive, all rules and all, you
know, principles that you had before, that they go completely out the window. And what I mean
by that is, for example, with Mac, you have to really give it access to your file system.
00:09:42:19 - 00:10:01:11
Stefan
Like any program that you install on Mac, you have to wake up mac with MacBook. Yeah, yeah.
If you go with MacBook and you want to, like install a program that has access to your file
system, you have to do a couple steps to do that, and you have to make sure that you give it
access. And what's crazy to me is, with like the introduction of ChatGPT and all these AIs is, is
all the rules went out the window.