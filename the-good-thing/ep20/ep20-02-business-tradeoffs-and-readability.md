---
title: Business Tradeoffs and Readability
slug: ep20-02-business-tradeoffs-and-readability
series: The Good Thing
episode: 20
chunk: 2
segment: Language Choice and Business Impact
timecode: 00:06:28 – 00:12:00
start_time: 00:06:28
end_time: 00:12:00
speakers:
  - Stefan
  - Jens
topics:
  - Business Tradeoffs
  - Code Readability
  - Team Productivity
  - Language Ecosystem
tags:
  - ai
  - cosmo-router
  - typescript
  - cosmo
  - go
  - llm
  - rest
  - rust
  - startup
  - telemetry
entities:
  - Stefan Avram
  - Jens Neuse
  - Programming languages
summary: Deep dive into the business considerations behind programming language choice,
  focusing on readability, maintainability, team productivity, and the broader implications
  for hiring and ecosystem support.
---

00:06:28 - 00:06:44
Stefan
That's fair. This one. I like what he said, but I think this kind of goes in what you've said though,
you need rust more than ever in the LLM generated code era. The worst part? I wouldn't say the
worst part, but these. You can easily write code that looks correct and does not function properly
due to some pretty severe design flaws in that language.
00:06:45 - 00:07:00
Stefan
If rust code compiles, it's generally going to do exactly what you intended to do. If rust code
compiles, you're able to get to that part, especially in a world where you're generates downright
stupid to use golang. I don't know. It came a little bit aggressive. I mean, you could tell because
he has a crab there and he says, I love rust.
00:07:00 - 00:07:03
Stefan
But what are your take on this comment?
00:07:03 - 00:07:30
Jens
Yeah. also interesting. So, I wrote rust in the past, and I can write rust that compiles. And the
problem is, the first problem I ran into when I was learning rust is, I needed to properly use the
async keyword. And I also had to run my own scheduler, and I was using it in the, in the wrong
way.
00:07:30 - 00:07:57
Jens
So for for some reason, I, I'm not sure why I did it wrong. It wasn't intuitive to me, but, I
somehow created like a whole scheduler for each async operation, and then I didn't have like a
shared context. It was a very weird situation. The problem is, it compiled. So it was working. But
I had to to talk to a rust expert to have me, to have explained to me how to actually use a
scheduler.
00:07:57 - 00:08:31
Jens
So if rust compiles, it could also mean I'm getting something wrong. And then there's another
thing, that I think a lot of people get wrong about. Go it Go has some primitives like, channels
and the go keyword to start the goroutine. And the reality is, most of the time you write code that
doesn't use these features because most, most, developers who need channels or goroutines,
they are actually library creators.
00:08:31 - 00:08:57
Jens
And if you create a library like us, like, we have, the engine of our, of our cosmo router, we don't
use LLM coding heavily in that space. It's too complicated for LLMS. And it's also too
dangerous. So, yeah, that's that's I don't know if you have anything to add.
00:08:57 - 00:09:12
Stefan
Not really. This guy came up pretty. aggresive. Rust skin or rust, a cane or whatever. All I see
here is skills issues. Your inability to understand rust as lead you do an incredibly ignorant write up.
00:09:12 - 00:09:40
Jens
So but okay it's super important to to set the ego to the side and think in and think in in a
business context, if you say this is a skill issue, you're essentially messaging that your your
opinion is you are smart, you can write rust. I cannot write rust. I'm an idiot. So that is what
you're saying. And this is not working in a in a business context.
00:09:40 - 00:10:10
Jens
What you need to think about in a business context is what kind of human resources do I have
available on the market? Who can I hire, and what will it cost me to get talent to build my
software? And then also the cost of maintaining software. And if rust developers are, more
expensive, and if for my use case, go would be enough or TypeScript.
00:10:11 - 00:10:13
Jens
It's not just skill.
00:10:13 - 00:10:30
Stefan
Jacob. We're going to have to clip that because I think that's the nicest. Like way to kind of
frame it. Like rust is a great language, but if you're looking at it from a business point of view
and you're a startup and your resources are limited, what language are you going to choose and
why? I mean, rust developers are expensive.
00:10:31 - 00:10:41
Stefan
It's also harder to learn. The barrier to entry is harder. If you start hiring junior developers,
they're going to have to learn rust. It'll be harder for them to debug. I mean very well said Jens.
00:10:41 - 00:10:42
Jens
Can I add one thing?
00:10:42 - 00:10:44
Stefan
Yeah.
00:10:44 - 00:10:59
Jens
Imagine you do a fun little weekend on the new book ring Nordschleife. I'm, you know, I'm I'm,
I'm a little bit of a petrolhead. Right. And so I.
00:10:59 - 00:11:02
Stefan
Was, I think I was like, wait, what is that?
00:11:02 - 00:11:04
Jens
Okay. You know, the Nordschleife, right?
00:11:04 - 00:11:08
Stefan
I think we went to it, didn't we, when we were in Germany.
00:11:08 - 00:11:10
Jens
No, that was Hockenheimring.
00:11:10 - 00:11:12
Stefan
Okay. But this is still it's just a place where you.
00:11:12 - 00:11:40
Jens
Could okay a race circuit. Yes. Yeah. So let's say you do a little fun weekend on the race circuit
with some friends. Nobody is a professional driver. Should we rent Formula One cars or should
we rent a cheap BMW m3? That is maybe like a race version, it has special race tires and some
some protection, like, like, that it cannot roll.
00:11:40 - 00:11:47
Jens
Or even if it rolls, we don't die. Stuff like, should we take the cheap M3 or the formula one car?
00:11:47 - 00:11:49
Stefan
I mean, the cheap M3.
00:11:49 - 00:12:00
Jens
Yeah. So you choose the appropriate tool. And I think just saying that rust is the all in one