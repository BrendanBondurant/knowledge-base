---
title: Open Source Collaboration and Safety
slug: ep26-11-open-source-collaboration-and-safety
series: The Good Thing
episode: 26
chunk: 11
participants:
  - Stefan
  - Jens
  - Sam Lambert
segment: Open Source Maintenance and Community Collaboration
timecode: 00:51:13:19 – 00:56:07:15
start_time: 00:51:13:19
end_time: 00:56:07:15
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - Open source licensing philosophy
  - Internal forks vs upstream contributions
  - Vitess maintainership responsibilities
  - Community contributions from major companies
  - Collaboration without contracts
  - Large scale open source project governance
tags:
  - ai
  - postgres
  - open-source
  - open-source
  - database
  - go
  - mysql
  - vitess
entities:
  - Vitess
  - PlanetScale
  - Slack
  - HubSpot
  - Etsy
  - Uber
  - MIT
  - GPL
mentions:
  - Open source as human achievement
  - Internal Vitess and MySQL forks
  - Platform-specific modifications
  - Uber's significant contributions
  - Consultation on large changes
  - Postgres and Mongo compatibility discussions
summary: |
  Discussion of open source philosophy and the responsibilities of maintaining large-scale projects like Vitess. Covers how PlanetScale manages internal forks while contributing upstream, and their approach to community collaboration with companies like Uber, Slack, and others.
---

00:51:13:19 - 00:51:36:29
Sam
If you're going to use the glow and the incredible branding of what is the most in one of the most
amazing human achievements, which is the open source, like you think the open source
community is just a phenomenal human achievement to be able to, like, bask in the glory of that
and use open source in terms of your branding and furthering your company.
00:51:37:01 - 00:52:01:08
Sam
But holding back the actual license from being an open source license, I think is very wrong. So
yeah, I don't really have a Beef for the specific, like there's some licenses that are just more.
The GPL is annoyingly like niche and well, has like niche ramifications that GitHub would always
just suggest people use their MIT license because it's the most simple and most open.
00:52:01:10 - 00:52:10:23
Sam
But yeah, it's no no specific license problems. It's more like the approaches people take by
taking these non open source licenses and claiming to be open source. I think it's very cheeky.
00:52:10:25 - 00:52:19:28
Jens
Do you have like like a fork of like an internal fork of of vitess or is it just you use the open
source. We test. That's what you deploy.
00:52:20:01 - 00:52:40:22
Sam
We do have an internal fork and it's really for simplicity. Right. Like rather than there's no we're
not trying to do like a kind of premium thing where you, there's like a ton of features hidden.
There's some stuff that's platform specific to us, which we don't even want to bend the, vitess
project out of shape too much to be specific to planet scale.
00:52:40:22 - 00:53:01:15
Sam
So we run our forecast selves to kind of address some of those things. Same with our MySQL
fork. It's open, but you know, it's not like we push it out there for people to go and like run it
themselves. It just has the things we need to go and do our platform. But yeah, we run a fork.
We do, but not it's not the kind of like, oh, here's like a super pared down thing in terms of
vitess.
00:53:01:15 - 00:53:17:12
Sam
It's, it's it's more like fit and functionality to work well with our platform. And that's things we just
we wouldn't put into the test anyway. The everything we can upstream into vitess. We absolutely
do. And a lot of things just start with the test code base and get pulled into our fork.
00:53:17:15 - 00:53:28:03
Jens
Is there a possibility that that someone could prevent you from from merging something into the
into the public? vitess repo.
00:53:28:06 - 00:53:32:09
Sam
If we didn't have control of the maintainer ship, then yeah. Yes.
00:53:32:12 - 00:53:33:18
Jens
You have you have control.
00:53:33:23 - 00:53:39:13
Sam
Yes. We are the maintainers. The project. Yes. Or like nearly all the maintainers work for us is.
00:53:39:19 - 00:53:54:05
Jens
way.
But by the way, by by the I read something about the C, Cncf and maybe I misunderstood it, but
is it not like you need to have, like other companies who also contributed and in a meaningful
00:53:54:08 - 00:54:15:13
Sam
And we do slack, HubSpot, Etsy, they, they all contribute, it's great that Uber have put a lot of
contributions into vitess lately. It's fantastic. We we absolutely do. We have we're very happy
with, that's what makes it great. Right. Like that was what makes it generalizable. You know, it
means we can we get to listen and deal with the concerns that they have.
00:54:15:13 - 00:54:46:18
Jens
It's fantastic when when someone from Uber wants to, wants to merge something upstream,
and you would have to spend a significant time to, to plan the feature, to review, to collaborate,
etc., etc. is that is that's all something like I would get from you for free or do I need to have a
contract with you? Or would you just spend time with me or or how are you handling these kind
of relationships?
00:54:46:20 - 00:55:04:22
Sam
Yeah, you don't need to have a contract. Basically. Yeah. Like we we recommend if you're going
to send a very large change to vitess that you consult us first on the approach. Like there's
some people that say, like people are generally fairly sensible. They'll like hit us up and say, you
know, we we're thinking vitess should do this.
00:55:04:24 - 00:55:22:10
Sam
And we'll tell them if we disagree, like if someone shows up and say, we think we should change
vitess to be a Postgres compatible or Mongo compatible, we would say we disagree and we
wouldn't accept patches that do that. Right. On the other hand, if someone says we want to take
this approach to do this thing, can you kind of guide us towards it?
00:55:22:10 - 00:55:41:14
Sam
We'll say, yeah, absolutely. It's valuable. Or sometimes people show up with a bunch of
functionality and we need to go back and forth a bit to kind of help them. Maybe they've missed
certain ways of doing things that are already there that, you know, can just be tidied up, or we
need to tidy up this implementation. And they haven't thought about a downstream effect that
would affect a load of other people.
00:55:41:16 - 00:55:57:29
Sam
They may not have thought about the elegant upgrade path or whatever. Right. Like we help
them think through those things, but that's part of the burden of running a really big open source
project that has so many large companies that depend on it. You just have to kind of do that to
keep the project healthy. Again, that's another hard dynamic for companies, right?
00:55:57:29 - 00:56:07:15
Sam
this magnitude.
They it's this in or out thing. You have to take it super seriously. When you maintain projects of