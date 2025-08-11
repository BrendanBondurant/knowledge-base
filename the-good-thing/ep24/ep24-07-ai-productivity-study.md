
---
title: AI Productivity Study Critique and Sample Size Issues
slug: ep24-07-ai-productivity-study
series: The Good Thing
episode: 24
chunk: 7
participants:
  - Stefan
  - Jens
segment: AI Productivity Research Analysis
timecode: 00:33:06:08 – 00:40:14:14
start_time: 00:33:06:08
end_time: 00:40:14:14
speakers:
  - Stefan
  - Jens
topics:
  - AI slowing developer workflows study
  - Sample size critique (16 developers)
  - Scientific methodology and peer review
  - Selection bias in research
  - Media headline-driven narratives
  - Psychology research standards
tags:
  - ai-productivity
  - research-methodology
  - sample-size
  - selection-bias
  - peer-review
  - media-criticism
  - psychology
entities:
  - Stefan Avram
  - Jens Neuse
  - Jacob
  - Nithin
  - TechCrunch
  - Time Magazine
  - Hacker News
  - Cursor
  - Lovable
  - Google
mentions:
  - 19% developer slowdown claim
  - 16 developer sample size
  - early 2025 AI study
  - experienced open source developers
  - 22K stars repositories
  - 1 million lines of code
  - selection bias explanation
  - statistical tools for data validation
  - scientific journal review process
  - headline vs actual science
  - Google outage trolling incident
summary: |
  Stefan and Jens critically analyze a study claiming AI tools slow developers by 19%, focusing on the problematically small sample size of 16 developers. Jens applies his psychology background to explain selection bias, proper statistical validation, and peer review standards. They critique media outlets for prioritizing clickbait headlines over scientific rigor.
---

00:33:06:08 - 00:33:26:08
Stefan
Oh, what's the saying? No, I'm not going to say it out loud. Bop bop bop bop. I just like, said it
out loud in my head. All right, onto the next topic. This one's interesting. AI might be slowing
down our workflows. Personally, for me, it's speeding me up. So I don't know what this article is
about.
00:33:26:11 - 00:33:48:22
Stefan
I'm able to build things I wasn't able to build before, but, this is one of the articles that we've
already seen. It's measuring the impact of early 2025 AI and the experienced open source
developer productivity. And so it's a great study. I highly recommend that you take a look at it,
because it's really goes into deep of how it's affecting.
00:33:48:22 - 00:34:15:04
Stefan
But long story short, if you were to just kind of look at the time article, it'll show you exactly what
you kind of need to know, which is the tldr. But basically, developers are being slowed down by
19% by using tools like cursor. And the thing is, cursor and other tools are advertising that you
are 20% productive or more productive by using it.
00:34:15:07 - 00:34:23:00
Stefan
Yeah. And I know you have some experience with this. What is your take on this? That AI is
actually slowing developers down.
00:34:23:03 - 00:34:26:08
Jens
Can can you open this article again?
00:34:26:11 - 00:34:29:05
Stefan
Do you want the sciencey you want or do you want the time. So on.
00:34:29:07 - 00:34:30:16
Jens
No science.
00:34:30:18 - 00:34:31:11
(Mix)
Okay.
00:34:31:14 - 00:34:34:15
Stefan
We go for the real stuff.
00:34:34:17 - 00:34:45:18
Jens
Okay. Can you search for the number 16. 16? Okay. Read this sentence.
00:34:45:20 - 00:34:49:18
Stefan
Oh, yikes. That's their sample size.
00:34:49:20 - 00:34:51:08
Jens
Read the sentence.
00:34:51:10 - 00:35:11:19
Stefan
To directly measure the real world impact of AI tools or software development, we recruited 16
experienced developers from large open source repositories leveraging 22 K stars 1 million
lines of code that they've contributed for multiple years. Developers provide a list of real issues
246 that would be valuable to the repository. Bug fixes, features, refactors that would normally
be part of their regular work.
00:35:11:21 - 00:35:20:12
Stefan
Then we randomly assign each issue to either allow or disallow. Use of AI will work on an issue
when AI is allowed. Developers can use any tool. Do I keep reading? Okay.
00:35:20:14 - 00:35:42:21
Jens
It's good. So I know you keep making jokes that ha ha ha. Jens. Studied psychology. It's boring.
Ha ha ha. I know you keep making this kind of jokes, but if you studied psychology, you would
immediately see that and you would be immediately like, okay, this is nonsense.
00:35:42:24 - 00:35:47:12
Stefan
Yeah, it's kind of crazy that they actually publish this. 16 people.
00:35:47:14 - 00:35:58:08
Jens
Like who, who published this, like TechCrunch or somebody like who, who spreads this word
like, I don't know who metr is, but like, who.
00:35:58:10 - 00:35:58:22
(Mix)
Who.
00:35:58:24 - 00:36:00:25
Jens
Who reshared it.
00:36:00:27 - 00:36:05:04
Stefan
It's an organization about like, okay.
00:36:05:06 - 00:36:13:08
Jens
But who knows? I mean, these guys, I don't know who they are. Like, this is just somebody. But
this was in the news, right?
00:36:13:10 - 00:36:28:24
Stefan
Yes. So this is the founder and CEO. She's all about AI. But let me go to the times article
because, this study got published into the times article, which crazy. I didn't actually see that. So
that her sample size was 16 people.
00:36:28:26 - 00:36:53:22
Jens
And I'm really honest. Like this is it's so important if you look at research like this, it is super
important that you that you look at the numbers. And if we're if we're investigating a data set of
16 developers, like we can still look at it and there can be that there can be something in it. It
can be true.
00:36:53:23 - 00:37:27:22
Jens
Like, I'm not saying this is garbage. I'm saying the data set is extremely small. It would have
been so much better if they did this with like a hundred devs over six months or something. 16
devs. It's possible that, for example, there's something in science. We call it selection bias. Just
by picking the one, the wrong group of developers, it can mean that the data set skews in one
direction.
00:37:27:25 - 00:37:56:09
Jens
And, the way you would actually combat against this is, we're now learning something about,
what psychologists actually do. The way you combat is, let's say you have a full data set of 200
developers. You would then pick random sets of 50 and you compare, you compare them
against each other to each other. You have like, there's, like statistics tools for that.
00:37:56:12 - 00:38:24:12
Jens
And this way you can actually see how, how, how uniform is your data set and are there
problems in your data set. Because ideally, if you have 200 devs and you pick randomly 50,
they should always come out at the at the same like they should always tell you like the same
indications like, for example, the main, the main case here, the main message is devs are slow
down 20%.
00:38:24:14 - 00:38:54:21
Jens
So if you randomly pick 50 devs you should always come out at 50. At 20% slower. If this varies
a lot, then it's much worse. Now the problem is, if you just have 16 devvs, you cannot really pick
a slice of that because it's so it's such, such a small amount of developers and, so, yeah, I don't
know how much we should read into that, into that, report.
00:38:54:24 - 00:39:09:08
Stefan
Why don't they have comments like, why aren't people roasting this like, you can't publish
something at the time? They're saying they measure the speed of 16. Developers like that is so
tiny that doesn't tell you anything.
00:39:09:10 - 00:39:13:17
Jens
Yeah. I don't know.
00:39:13:19 - 00:39:37:14
Stefan
And it really comes and draws a conclusion. But I think it's what Jacob said. So if you
remember, every time on Twitter when something like funny happens, like, for example, like, do
you remember when GCP went down and, everybody likes, just got laid off from Google today?
I was in charge of running infrastructure like they always do, like that type of take.
00:39:37:16 - 00:39:58:16
Stefan
And something happened like that with Google and this guy was trolling and all these like pretty
big publications posted it like his thing. He was like young developer fired for accidentally
causing outage at Google, but he was completely trolling. And I think the whole thing right now
with the media is it's what Jacob said, I'm going to bring it back up, which is, oh, on one.
00:39:58:18 - 00:40:14:14
Stefan
But people actually don't care about the results. All they care about is the headline that drives
their narrative. So a lot of people are saying, yeah, AI is good or AI is bad. This one's for the AI
is bad. It's slowing people down. And it's just saying, yep, I care more about the headline then
the actual science, but I actually didn't even read the article.