---
title: LLM Code Quality and Productivity
slug: ep23-07-llm-code-quality-and-productivity
series: The Good Thing
episode: 23
chunk: 7
participants:
  - Stefan
  - Jens
segment: AI Code Quality Assessment
timecode: 00:39:06:00 – 00:45:01:00
start_time: 00:39:06:00
end_time: 00:45:01:00
speakers:
  - Stefan
  - Jens
topics:
  - 50% AI code claims analysis
  - Software liability concerns
  - AI-generated code quality
  - Development productivity metrics
tags:
  - ai-generated-code
topic_tags:
  - ai-generated-code
entities:
  - Stefan Avram
  - Jens Neuse
mentions:
  - 50% AI code statistics
  - liability concerns
  - code quality assessment
  - productivity claims
summary: Stefan and Jens analyze claims about 50% AI-generated code in software projects,
  discussing the implications for software liability and questioning the accuracy
  of productivity metrics while examining code quality concerns.
---
00:39:06:00 - 00:39:08:17
Jens
But my, my current observation is that.
00:39:08:19 - 00:39:09:15
Stefan
00:39:09:18 - 00:39:37:22
Jens
LLMs help good developers to get more stuff done. So my current take is, developers are not
going anywhere. Like I see it in our company and I have some observations with tools like
cursor. Yeah, exactly. Jacob. Thank you. GitHub CEO says the smartest companies will hire
more software engineers, not less, as AI develops. So that's what he's saying.
00:39:37:24 - 00:39:39:10
Jens
My observation.
00:39:39:12 - 00:39:41:02
Stefan
Currently is.
00:39:41:04 - 00:40:03:21
Jens
That LLMs are cool and they help you write code. A lot of code. But you still need very good
developers. You you still need, senior devs. You still need people who guide the LLM to do the
right thing. Like, it's so easy to to generate a garbage code with an LLM that looks right, but it's
wrong.
00:40:03:23 - 00:40:22:23
Jens
And one other topic I wanted to to bring up you know, you keep seeing this post that like, just
like two days ago, I saw that, someone posted somewhere that, Google is now or at Google,
there is now more than 50% of the code is written by LLM.
00:40:22:24 - 00:40:25:07
Stefan
That was Salesforce. That was Salesforce.
00:40:25:09 - 00:40:35:12
Jens
Okay. So yeah, I was okay. Well, what's your take on on this post? Because I, I think I will have
a different one. I have, yeah.
00:40:35:14 - 00:40:55:05
Stefan
Okay. So my take is Salesforce is pushing there like AI, CRM called Agent Force. And I think if
you say it again, so 50% of all the code at Salesforce is being written by AI. I think it just means
that they're 50% faster because the developers are using AI, not the AI is writing the code and
it's adding to it.
00:40:55:05 - 00:41:06:21
Stefan
But I think he's trying to say is that developers are more productive, but he's spinning it that I've
replaced 50% of my workforce with AI. That's my take on it. Are you on the same one or not?
00:41:06:24 - 00:41:44:29
Jens
Okay. My take is that that it's complete nonsense. Like I'm not dismissing what you said, but. So
here's my take. Let's say your company writes 100 lines of code per day in total. And if we now
say that we, we write, 50% of the code with AI, with LLMs, you would assume that tomorrow
when this is right that we would now write 50 lines of code with AI and 50 lines of code with
humans.
00:41:45:01 - 00:41:47:09
Jens
That's what you would assume, right?
00:41:47:12 - 00:41:48:13
Stefan
Yeah.
00:41:48:16 - 00:42:24:15
Jens
But my observation is completely different. My observation is that LLMs have a tendency to just
write a lot of code. They don't reuse code in smart ways. They don't understand the entirety of
your code base. So my assumption is that yesterday the humans wrote 100 lines of code. Then
they discovered that they can now use AI, and suddenly they are writing like 200 lines of code in
a day.
00:42:24:18 - 00:42:53:02
Jens
The problem is, it doesn't mean that these new 100 lines of code are equally good or even
better. It's just we are now writing more code, and I'm telling you, experienced developers know
this. Every line of code is a liability. Like, ideally, you could be a billionaire with zero lines of code
because if you have code, you have to test it, you have to maintain the technical debt, blah blah,
blah, blah, blah.
00:42:53:07 - 00:43:21:20
Jens
So actually, I think and then I'm very curious to see this, but I would like to know like from
companies if you're using, if everybody's now using cursor, it's the amount of code that you
write. Is it, is it growing faster. So does it mean you're now writing more code, more verbose
code or something? Because that means you're essentially the liability grows faster.
00:43:21:20 - 00:43:50:10
Jens
So this take of 50% of the code, we're now writing it with LLMs. I'm I'm curious in a sense that's
like, first of all, how do you measure that? And and second, I'm not sure if it's a totally positive
trend, to be honest. And I can also speak from my personal experience. We have different code
bases. Recently I wrote some code in our in our GraphQL engine, our GraphQL engine.
00:43:50:10 - 00:44:16:13
Jens
It's so complicated that I don't I don't use cursor to write code in it because it doesn't make
sense. It doesn't it doesn't get what we're doing there. So I'm just writing it by hand. And then we
have a CLI and I added a new command and the code, the existing code didn't really I don't
know, it it didn't feel like this is the most amazing code.
00:44:16:15 - 00:44:43:20
Jens
So I was like, okay, whatever, I just use cursor for that and it generates and generates and blah,
blah, blah. And, yeah, it's it's quite verbose, but my, my, my real question is like is the code that
is written by AI like, is it really like more valuable or, you know, better questions I would ask is if
you use a LLMs to write code, is it more reliable?
00:44:43:23 - 00:45:01:06
Jens
Is the code faster? Are we are we shipping faster? Are we saving time? And you also have to
offset this against the the cost for the for the LLM. So I think it's more than just saying we're now
writing 50% of our code with AI.