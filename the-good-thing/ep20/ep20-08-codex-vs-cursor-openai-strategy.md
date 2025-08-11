---
title: Codex vs Cursor and OpenAI Strategy
slug: ep20-08-codex-vs-cursor-openai-strategy
series: The Good Thing
episode: 20
chunk: 8
participants:
- Stefan
- Jens
segment: AI Development Tools and Platform Strategy
timecode: 00:40:23:25 – 00:47:02:24
start_time: 00:40:23:25
end_time: 00:47:02:24
speakers:
- Stefan
- Jens
topics:
- Codex vs Cursor in AI-powered development
- OpenAI's platform strategy and positioning
- AI development tool competition
- Developer tool market dynamics
tags:
- codex
- cursor
- openai
- platform-strategy
- ai-development-tools
- developer-tools
topic_tags:
- codex
- cursor
- openai
- platform-strategy
- ai-development-tools
- developer-tools
entities:
- OpenAI Codex
- Cursor
- OpenAI
- Stefan Avram
- Jens Neuse
mentions:
- Codex capabilities and limitations
- Cursor's market position
- OpenAI strategic decisions
- Developer tool competition
summary: Comparison of OpenAI's Codex and Cursor as AI development tools, analyzing
  OpenAI's platform strategy and the competitive dynamics in the AI-powered developer
  tool market.
---

00:40:23:25 - 00:40:41:06
Jens
So that means if you compete with OpenAI, on the same capability, first of all, they have more
capital. So they can move faster, hire better talent. They can have the rust developers. You only
have the go developers.
00:40:41:08 - 00:41:09:13
Jens
So they have the borrow checker. You don't have to borrow checker. Okay. So that's number
one. But the second thing is well what what will what will happen is, so you build a product and
you will buy from Google, you will buy Germany two point something. And what's going to
happen is you buy this and you resell the token.
00:41:09:16 - 00:41:40:20
Jens
This will be very expensive for you. At the same time, Sam Altman, he will copy your product
and he will run it on his hardware, which is an extreme amount cheaper than than your solution.
So everybody who built something that has the potential, to, to to be a more profitable business
if ran directly on hardware, you're dead.
00:41:40:23 - 00:42:14:29
Jens
And I can tell you here's my prediction for cursor, because I think cursor is absolutely dead in
the future. So here's what I think. What's going to happen? Cursor has this, cursor. OpenAI has
this new thing. It's called Codex. It changes the workflow. And currently the workflow with cursor
is I have cursor running on my local machine, and I open files and I tell cursor what I want to
change, and then it does, calls to OpenAI or to whatever model, and then it will make changes
to the files.
00:42:14:29 - 00:42:40:15
Jens
And this can take some while. And then after all the changes are done, I can review them, and
then I can re prompt and I can make changes. So on so forth. So it's a direct interaction
between the, the user and the code and the AI. So it's it's very much it's a hands on experience.
But with Codex, which is in the very, very early days, I tried it wasn't super, compelled to be
honest.
00:42:40:15 - 00:43:11:06
Jens
It's not yet great, but the not so important. The point is the experience OpenAI is creating, it's
kind of similar to to, the, the copilot experience from from GitHub. You have a code base. You
write a prompt to change the code base in some way, and then this prompt, you hand it off to AI,
AI will handle it in the background, and then will come back with a pull request or something.
00:43:11:06 - 00:43:30:13
Jens
So it will tell you, hey, I made the changes you wanted. You can now review it. So instead of
having cursor as an IDE in front of you, it's more like you can even think about. Let's say you
have like a linear you create a bunch of tasks, you assign it to an AI, and ten minutes later AI
comes back with the pull request.
00:43:30:13 - 00:44:02:20
Jens
You can review it so it's more hands off and it's more automated. And now here's the interesting
question. Currently cursor works. Works, great. Is is, at an advantage because the models are
so weak and slow and it's expensive. What if we can drive the cost down? What if we can drive
the speed up? What if we can build a framework that allows us to to generate this code much
faster in a more hands off way?
00:44:02:22 - 00:44:27:27
Jens
So we need to build an engine which is Codex. That makes it simpler to write code. Hands off.
And then the following happens. So I think for the next, I don't know, 12 months or whatever, I
think, cursor will be, super successful, throughout. And eventually those hands off coders will
take off. They are they are faster.
00:44:27:27 - 00:44:51:03
Jens
They are getting, more done. I think they can do more complex, things. And you can as a
developer, I think you will get more velocity because you don't have to open cursor. You just say,
here's a bunch of work, and then AI does it. And now now is the problem. Cursor is just buying,
AI from others and reselling it.
00:44:51:06 - 00:45:19:21
Jens
But Codex, it will run on the hardware of open AI so you cannot compete with that. So there's no
way like a startup could compete with this just because, cost and hardware is, inaccessible. So
at that point, I think, OpenAI has won the game. And, to be honest, I would actually invest in the,
like, this is not investment advice, but, if they built that, I would invest in it.
00:45:19:24 - 00:45:40:06
Stefan
No, I think you're spot on. But are you not seeing the similarities, though, with like, the past?
This is basically the cloud 2.0. This is AWS. They own the hardware, they lease it out to you and
they build on top. It's also not a bad thing because the cloud created companies like Vercel,
which have 100 million ARR, and they're literally a wrapper on top of AWS.
00:45:40:06 - 00:46:01:21
Stefan
They just improve the experience. And so you're absolutely right. OpenAI is going to completely
own. And Steve Jobs, he has a good quote. The only way you can completely own is if you own
the software and the hardware. Because if you own the hardware there, your margin is zero.
Nobody can get close to your margin. Nobody can. Same thing with Jeff Bezos where he said,
what is it?
00:46:01:24 - 00:46:09:27
Stefan
Your margin is my opportunity. And he owned the margin with AWS. That's a great take. It's a
great take.
00:46:09:29 - 00:46:32:16
Jens
Yeah I'm not sure. Like on the one hand it's a great opportunity. On the other side, what I don't
like about it is I think this can quickly lead to monopolies. And I'm not sure if it's if it's the right
thing for for humanity. If just like OpenAI and 2 or 3 other big companies have hardware and
own LLM.
00:46:32:19 - 00:47:02:24
Jens
Yeah, I think it will be more favorable if if this was, if more startups could have similar
capabilities. But, yeah, I think what, what will end up happening is that, nobody can compete on,
on that level of automation. just because as a startup, you what you what you won't be able to
do is you cannot raise like, I don't know, 100 billion and build a data center.