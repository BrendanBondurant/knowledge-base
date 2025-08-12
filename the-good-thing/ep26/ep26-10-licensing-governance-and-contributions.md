---
title: Licensing Governance and Contributions
slug: ep26-10-licensing-governance-and-contributions
series: The Good Thing
episode: 26
chunk: 10
participants:
  - Stefan
  - Jens
  - Sam Lambert
segment: Open Source Governance and Licensing Philosophy
timecode: 00:45:00:07 – 00:51:13:17
start_time: 00:45:00:07
end_time: 00:51:13:17
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - Company culture and performance management
  - CEO coding involvement
  - CNCF and Vitess relationship
  - Open source licensing philosophy
  - BSL vs true open source licenses
  - Apache 2.0 vs other licensing models
tags:
  - ai
  - open-source
  - websocket
  - open-source
  - benchmarking
  - database
  - go
  - mysql
  - rest
  - startup
  - vitess
entities:
  - PlanetScale
  - CNCF
  - Vitess
  - Apache
  - BSL
  - MongoDB
  - Amazon
mentions:
  - No passengers company value
  - Expert-led leadership principle
  - CEO coding but not in critical path
  - CNCF governance benefits
  - BSL pretending to be open source
  - Apache 2.0 licensing preference
summary: |
  Deep dive into PlanetScale's company values including "no passengers" and expert-led leadership. Discussion of open source licensing philosophy, criticizing BSL licenses that claim to be open source, and explaining their relationship with CNCF governance.
---

00:45:00:07 - 00:45:22:01
Sam
You need to do the performance reviews, the people management and all that stuff. But if you
have a small team of very good people, and fit the culture around that, you can. You can build a
company that people like working out. Like if you work with other smart people that you find
challenging, and then you learn and you grow, it becomes very addictive to go and do that and
have influence.
00:45:22:01 - 00:45:52:08
Sam
And that's the kind of feedback we get from from folks. We do miss the mark sometimes. You
don't hire people, great people every time. And that's why we have one of our values is no
passengers, meaning we don't really tolerate people not kind of being here and working hard
and being present and doing good work. And you have to kind of clean up those types of issues
and let people go and if you're fair about how you do that, then it kind of works.
00:45:52:10 - 00:46:12:15
Sam
Another one is experts, leading experts, which is we believe that everyone should be an expert
in the field, that there are and should be. You want to work for a boss that you aren't, you know
that you respect as an expert. So we have we don't have non-technical managers and things
like that's just silly things like that.
00:46:12:18 - 00:46:15:12
Jens
Are you still writing code?
00:46:15:14 - 00:46:41:22
Sam
I do, but not really anything that goes into the critical path in production, because if I would not
be able to make myself available to, like, be on call to kind of remediate those things. Plus, I'm
probably the worst engineer at the company now. So that's not, it's not a anything anyone's
caught. No one's missing me writing code, but I've done a few, you know, small features or
integrations or add ons for our ecosystem and things like that.
00:46:41:23 - 00:46:45:07
Sam
I'll fuck around with.
00:46:45:09 - 00:46:55:24
Jens
Yeah. Like people are also sometimes annoyed when when I write some code or they joke
about it and, yeah, it's similar. It's fun.
00:46:55:24 - 00:47:16:09
Sam
Like we've had some like niche MySQL issues that, you know, I've been able to, like solve or
just remembered some similar things in the past. And it's always kind of funny when it's me that
remembers that or whatever. But yeah, not a whole load.
00:47:16:12 - 00:47:28:01
Jens
The thing I love the most is, when I get impatient, I vibe code something and then I go to the
guys and then they are super annoyed because they have to get to production ready.
00:47:28:04 - 00:47:47:08
Sam
What's the best way to do it? Right? It's like have come up with something that people sort of
dislike, and then they'll go and tidy up and fix it. One thing I do, do is I have access. The
customers, our customers give me access to their planet scale orgs, and I'll often work with
them as a user and so help them out a bit.
00:47:47:11 - 00:48:02:22
Sam
I like joke. It's like the the most premium tier of support that we have, which is like, I'll go and
mess around with their stuff. And it's a really nice way of seeing from their side how interacting
with the product is and seeing the any pain that we put them through.
00:48:02:24 - 00:48:03:29
Jens
Yeah.
00:48:04:01 - 00:48:05:26
Stefan
That's awesome.
That's that's a good one. Another question I have is, so, vitess open source. It's, Cncf project,
00:48:05:29 - 00:48:16:10
Jens
right?
00:48:16:13 - 00:48:17:23
Sam
Yes.
00:48:17:25 - 00:48:34:27
Jens
And like a while ago there was like in the situation between Cncf and, the guys behind NATs and
a, what's the company called? Something with s.
00:48:34:29 - 00:48:43:18
Sam
Oh, I vaguely recall this. Yeah, I know I didn't pay much attention. Yeah, there was some drama,
I think. No, I can't remember.
00:48:43:18 - 00:49:08:06
Jens
Yeah. So they, they, they, they somehow they wanted to pull out the, the, the project out of the
Cncf and get more control over it. I don't even want to talk about that, but what I'm interested in
this. What's your relationship with, with the Cncf and, Well, is it good that vitess is a Cncf project
or is it neutral or.
00:49:08:07 - 00:49:10:15
Jens
I don't know, is it anything.
00:49:10:17 - 00:49:30:03
Sam
I think it's a good thing. I believe in open source. I believe if you're going to be open source, you
should be you should be really open source. You know, like there's types of licensing that I don't
like. When they pretend they're open source, when they're not or whatever. But there's also
licensing that I think is great and defends companies against companies like Amazon.
00:49:30:03 - 00:49:49:23
Sam
And yeah, like there would be a downside if Amazon just stole our tech and went and started
using it. Right. And that was not a good thing. But that's kind of what you throw into when you
do open source. And I think it's good to have these foundations in these bodies that protect
open source and allow some purity to these projects.
00:49:49:25 - 00:50:06:23
Sam
There is downsides generally from the model, but they're not specific to Cncf at all. And they're
a great crew. Chris and the team over there are just fantastic. And they do something that's very
difficult to do and wrangle a lot of the complexities that come with open source. And so, yeah, I
don't see it really as a downside.
00:50:06:23 - 00:50:12:23
Sam
I think it's the goods that keeps us honest. As an open source company.
00:50:12:26 - 00:50:28:09
Stefan
And what are some open source licenses that you don't like? So like for us, just for context,
we're licensed under Apache 2.0. Some of our competitors do BSL. I think BSL was created
because of Mongo right Amazon went and took it. Yeah okay. So what are some licenses that
you like or and don't like.
00:50:28:12 - 00:50:48:13
Sam
There's lot like I guess I should have I but I don't dislike the license I dislike the pretense. Right.
So yeah BSL for example. Right. It's not an open source license. It is officially not recognized as
an open source license. But there's companies that will do BSL and refer to themselves as open
source. And I don't like that.
00:50:48:15 - 00:51:13:17
Sam
Like your code is open. That's fine. But you can't I mean, you've blocked any contributors to that
going and starting a rival company to you that's not open source. That is not how that works.
And so I don't like the kind of layering on top of, you know, I think if there's a lot of people that
have one way relationships with open source and it's very take, take, take, and I don't like that.