---
title: AI Coding Experience and Personal Observations
slug: ep24-08-ai-coding-experience
series: The Good Thing
episode: 24
chunk: 8
participants:
  - Stefan
  - Jens
segment: Personal AI Development Experience
timecode: 00:40:14:14 – 00:46:14:03
start_time: 00:40:14:14
end_time: 00:46:14:03
speakers:
  - Stefan
  - Jens
topics:
  - Personal AI coding tool experiences
  - Cursor effectiveness across languages
  - Claude Coder tool evaluation
  - AI failure with complex codebases
  - Research bias and methodology critique
  - WunderGraph employee survey satire
tags:
  - graphql
  - ai
  - cosmo-router
  - ai
  - api-design
  - cosmo
  - go
  - open-source
  - rest
  - rust
  - startup
  - typescript
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
  - Cursor
  - Claude Coder
  - Opus 4
  - Sonnet 4
  - React
  - TypeScript
  - Go
  - Master Framework
mentions:
  - React frontend development
  - full-stack TypeScript
  - Go language productivity issues
  - Claude Coder workflow
  - AI agent development failure
  - import resolution problems
  - GraphQL Go tools
  - Cosmo Router development
  - existing codebase challenges
  - biased interview methodology
  - group interview bias
  - CEO presence in evaluations
summary: |
  Jens shares detailed personal experiences with AI coding tools, finding Cursor effective for React/TypeScript but problematic for Go development. He describes Claude Coder's impressive workflow but poor code quality for complex projects. The discussion includes a satirical critique of biased research methodologies, comparing proper survey techniques to obviously flawed approaches.
---

00:40:14:14 - 00:40:18:24
Stefan
I don't want to read the article now. I just saw the headline. So I'm actually at fault for that.
00:40:18:27 - 00:40:46:02
Jens
But I can I can give you some some tips from what we have learned in, in, in, that when, when
we studied this, this field, so there's scientific journals and these journals, there are like big
publications in psychology and other fields. And these journals, they review something and they
would never post a study like this with 16 engineers.
00:40:46:02 - 00:41:17:08
Jens
They would they would say, hey, guys, you're the you're not following our guidelines. The the
sample size is way too small. Please. Another approach and, so what you can look for is if you if
you are interested in such research papers, you always want to find them in the big journals
who have, who have reviewed this and posted it themselves, because that gives the, the, the
paper a lot more credibility.
00:41:17:11 - 00:41:18:03
Jens
Yeah.
00:41:18:05 - 00:41:29:08
Stefan
And Nithin actually posted a good question here. So how do you make such studies when some
are better than others are using AI? Nithan, why don't you use AI to write the sentence? It's from
capitalization or nothing.
00:41:29:08 - 00:41:57:07
Jens
But beside my point Nithin, this is the whole point. This is why. Why you want to do such a study
with the thousand developers or like much, much bigger. And then there's also the question like
if you have 16 dev, maybe this study is true for rust backend development or C++, but maybe in
in JavaScript frontend development it would speed you up.
00:41:57:07 - 00:42:19:01
Jens
But we don't know because it's just 16 people. And how much do we know about the people
which like are they working on front and back. And in this case it said they are working on open
source projects, which by the way this this is already selection bias because most developers
do not work on big open source projects.
00:42:19:08 - 00:42:30:26
Jens
Most developers work on super boring enterprise proprietary code bases, with Java or
something or PHP or whatever.
00:42:31:01 - 00:42:33:14
(Mix)
And yeah.
00:42:33:17 - 00:42:38:06
Jens
I don't know. Like, yeah.
00:42:38:08 - 00:42:50:00
Stefan
Well said next topic? Lovable? Or do you have anything else to add to this? Maybe tell the
people one more time that you studied psychology or business psychology? I.
00:42:50:02 - 00:43:19:23
Jens
I, I like this is live so I cannot show certain things with my hands, but, I can just speak from
personal experience. So, I, I tried using cursor for quite a time, so I'm. Or I'm using cursor for
quite a time, and when you do like react front end, it's okay. When you do full stack TypeScript
it's okay.
00:43:19:25 - 00:43:52:25
Jens
I tried using cursor for go. It wasn't very productive. And then I also tried claude code. Pretty
cool tool. I really like it. I think it's it's very smart. And the the way the workflow is, is amazing. I
absolutely love it. The problem I tried claude for building an AI agent with the master framework.
It completely code looked nice, didn't work at all.
00:43:52:27 - 00:43:57:01
(Mix)
Like it? It couldn't. They look for all it.
00:43:57:02 - 00:44:21:08
Jens
It couldn't even figure out imports, like, I don't know. So the, the I was using opus four and then
sonnet four as the model, the code quality, it was just garbage like unusable. So I threw that
away. And I also tried using claude for writing some go code for our GraphQL go tools thats
cosmo router. It also completely failed.
00:44:21:08 - 00:44:52:24
Jens
I didn't really understand the problem or didn't have a good idea of creating the solution, so I
ended up just writing the code by hand. So. But this is n equals one like this is not the case
study or something. It's just my. So so far my personal experience AI is yeah it's okay.
Sometimes it's cool. It can write tests or you can, you can, quickly get something together,
create like an example or something.
00:44:52:24 - 00:45:07:27
Jens
But I don't know, I always get the impression that if you have an existing code base that is
somewhat large, then AI completely fails. But yeah, I don't know.
00:45:08:00 - 00:45:15:16
Stefan
We should write a case study on this, a whole, peer reviewed by me, and it's just based on your
experience.
00:45:15:18 - 00:45:18:29
(Mix)
We should we should do, we should.
00:45:18:29 - 00:45:56:02
Jens
Do a neutral study, and we we will interview all WunderGraph employees what they think about
WunderGraph. And by the way, this there's, this is also you learn it in psychology. For example,
one way to get absolute great results is we we do a group interview. So you should always
interview everybody together should always be public and for example, if you interview people
how they like the CEO of WunderGraph Me, then it's it's best if the CEO is also in the room,
because that will absolutely not bias anybody.
00:45:56:02 - 00:46:14:03
Jens
Nobody will be afraid of of saying their opinion. But honestly, I don't think you have to do it
because everybody loves me. And, I'm, I'm super smart and, every, every evening we, we
dance in a circle and we say, Jens Jens Jens, and,