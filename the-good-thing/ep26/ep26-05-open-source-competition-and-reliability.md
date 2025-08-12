---
title: Open Source Competition and Reliability
slug: ep26-05-open-source-competition-and-reliability
series: The Good Thing
episode: 26
chunk: 5
participants:
  - Stefan
  - Jens
  - Sam Lambert
segment: Open Source Strategy and Competitive Moats
timecode: 00:19:02:26 – 00:24:16:02
start_time: 00:19:02:26
end_time: 00:24:16:02
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - Vitess as open source foundation
  - Amazon/AWS competitive threat
  - Operational expertise vs code access
  - Customer migration case studies
  - Small team achieving high reliability
  - Team composition and expertise
tags:
  - open-source
  - vitess
  - aws-competition
  - operational-expertise
  - reliability
  - team-size
  - maintainership
entities:
  - Vitess
  - Google
  - YouTube
  - Amazon
  - Aurora
  - PlanetScale
mentions:
  - YouTube using Vitess at Google
  - Amazon Limitless reliability issues
  - Public case studies of migrations
  - 55 person team with 100% uptime
  - Principal engineer level talent
  - Four person infrastructure team
summary: |
  Exploration of how PlanetScale navigates open source competition, particularly from AWS, through superior operational expertise rather than proprietary code. Discussion of their small but highly skilled team achieving exceptional reliability with minimal headcount.
---

00:19:02:26 - 00:19:22:22
Sam
Right? Like the physics of how a wing creates lift is like, it's written, it's done. But now the the
operations of making sure there's no single points of failure in that process, and it can continue
and it can do the process over and over again is the bit that's difficult and takes a lot of
knowledge and sedimentary knowledge and layers built up.
00:19:22:22 - 00:19:27:02
Sam
And that's what we have. That makes us pretty different.
00:19:27:04 - 00:19:52:18
Jens
Also one, one, one thing I'm interested in is so planet scale it, at least from the outside, it looks
like you're you're largely basing on top of vitess, which is an open source project. Yep. Like you
said, coming from from Google, Google or my understanding is it was something it was used for,
for YouTube. Right? Yes.
00:19:52:21 - 00:20:00:26
Jens
And so being an open source project and you are a company hosting that open like obviously
you're doing more than just hosting a project you were the.
00:20:00:26 - 00:20:02:16
Sam
We are the Maintainers as well. Yeah.
00:20:02:19 - 00:20:30:03
Jens
Okay. But one of the biggest fears of like startups with open source projects is like, yeah,
Amazon could just take vitess and and hosted like they they can probably do it cheaper. They
have data centers etc., etc.. Like you probably saw like all this back and forth between like, like,
like OpenSearch and Elasticsearch and other database companies.
00:20:30:03 - 00:20:35:03
Jens
Like how, how are you thinking about this, this topic.
00:20:35:05 - 00:20:56:12
Sam
I think that, you know, there's a this is a world where that's true, that can happen. vitess is like
half, half of our offering, right? A lot of the the stuff that makes planet scale really special is not
open source. And vitess is like it's a code base for the engine of our product. And it's incredibly,
incredibly important to us.
00:20:56:14 - 00:21:18:07
Sam
And yes, it would be a big step up, like it would be a big benefit to certain companies to go and
just take that and use it. And there's people that self host vitess at very, very large scale, and it
works for them. It's more like, can they replicate how well we operate databases and they
haven't.
00:21:18:12 - 00:21:40:24
Sam
I mean, we've got multiple public case studies out there of people moving from Aurora or
wherever, and becoming much, much more reliable, on top of our platform, we specialize in
databases, engineers some of our engineers have worked on. But there's no secret, like, they
have a lot of money. They can put a lot of people on these problems.
00:21:40:24 - 00:22:02:25
Sam
But at the end of the day, right, there's expertise. At companies like ours, that far exceeds what
they have, current, current Amazon specifically. And you look at the current tools, they've,
they've, they've built like limitless. We've moved their largest customer over to, to, to us because
it wasn't reliable. I, you know, literally this morning spoke to another limitless customer.
00:22:02:25 - 00:22:21:27
Sam
That's not a very large scale. That's also having problems on these platforms. So them just I'm
sure they've had they've had access to the vitess code base for years. It hasn't really improved
anything they do. They could just take the technology and host it. It's only half the problem for
them. I don't think their problem is writing the code that could look like vitess to go and do the
stuff.
00:22:21:27 - 00:22:35:13
Sam
It's a load of other tail factors that impact whether or not they can hurt your business. But there's
just plus there's also just much more coarse grained, brutal ways Amazon can can hurt you than
just take the code of what you're doing.
00:22:35:15 - 00:22:38:01
Jens
Yeah. What's your current headcount?
00:22:38:03 - 00:22:39:17
Sam
55.
00:22:39:19 - 00:22:58:13
Jens
55. And how does this distribute across like database operators or let's say like infra people or
what do you call it like like platform engineering versus like engineers working on the on the
vitess product or like proprietary products.
00:22:58:15 - 00:23:08:12
Stefan
And Sam real quick 55 with 100% uptime, reliability. That is insane. I mean, that is an insane
stat. Oh yeah. We're deep into this.
00:23:08:14 - 00:23:30:20
Sam
We're very proud of being a small company. We're doing some hiring. We're not going crazy. But
yeah, like this startup, like two other very popular Postgres startups like host hosts have their
engineering teams are three times the size of ours. And we're very proud of having a very small
company and team. These are exceptional people that we have working for us.
00:23:30:20 - 00:23:48:04
Sam
And we know like it's it's a known thing about our culture that we behave that way. Pretty much
every engineer at Planet Scale could be a principal engineer at any other company. We don't
really have any engineering titles that way, or it's just everyone's just an exceptionally good
engineer that's had a long career at scale. And that's how we achieve this.
00:23:48:07 - 00:24:16:02
Sam
And if you build good infrastructure, you shouldn't need to throw tons of headcount. Or
infrastructure team itself is very small. It's like four people. The vitess team is around ten. The
rest break up between what we would call orchestration, which is a large amount of what we do,
which is kind of orchestrating. Database failurover is happening like there's no there's nothing in
terms of how we handle our operations that require human to be around.