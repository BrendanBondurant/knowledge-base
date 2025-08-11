---
title: Compute vs Collaboration Business Models
slug: ep12-16-compute-vs-collaboration
series: The Good Thing
episode: 12
chunk: 16
participants:
- Stefan
- Jens
segment: Business Model Strategy Discussion
timecode: 00:58:19:19 – 01:03:20:19
start_time: 00:58:19:19
end_time: 01:03:20:19
speakers:
- Stefan
- Jens
topics:
- Compute reselling problems
- Vercel vs AWS wrapper distinction
- Developer purchasing behavior
- Self-hosting preference over markup
- Startup reliability challenges
- Railway and Fly.io experiences
tags:
- compute-reselling
- aws-wrappers
- developer-purchasing
- self-hosting-preference
- startup-reliability
- vercel-strategy
topic_tags:
- compute-reselling
- aws-wrappers
- developer-purchasing
- self-hosting-preference
- startup-reliability
- vercel-strategy
entities:
- Prisma
- Vercel
- AWS
- Railway
- Fly.io
- Flight Control
- Stefan Avram
- Jens Neuse
mentions:
- AWS account developer preference
- 10x markup pricing challenges
- developer time valuation
- startup reliability failures
- 700 years developer experience
- compute provider recommendations
summary: Jens argues against compute-based business models, explaining how startups
  fail when selling marked-up AWS services because developers prefer direct cloud
  provider access. He contrasts Vercel's platform complexity with simple AWS wrappers,
  discusses developer resistance to paying markups, and warns against using startups
  for infrastructure due to reliability issues, citing negative experiences with Fly.io.
---

00:58:19:19 - 00:58:59:08
Jens
Yeah. If you build Prisma with the intention to to make money, I think what you need is
collaboration. Yes. And, by collaboration, what I mean is, you for. Theres two ways you could
sell compute or you could sell collaboration. And I think most startups fail in selling compute,
because you you essentially you are wrapping the service, you are wrapping AWS.
00:58:59:11 - 00:59:27:12
Jens
I would say vercel is not an AWS wrapper because what they have created in the in terms of
complexity of the platform, it goes far beyond wrapping the whole experience from protection
against threats to CDN to like it's not a wrapper, but if you are Prisma and you have.
00:59:27:14 - 00:59:28:13
Stefan
00:59:28:15 - 00:59:34:14
Jens
I don't know what they they they announced something I think some component for
subscriptions or whatever.
00:59:34:14 - 00:59:36:04
Stefan
It's like boost or something. Yeah.
00:59:36:04 - 01:00:08:03
Jens
Yeah, something. Okay. So they take this one thing and they put it on compute somewhere and
they sell it as a service. You have to wundergraph SDK problem again. So our what we pivoted
away is because, developers have a natural tendency to not buy services for singular problems.
Actually developers have a tendency to not buy anything.
01:00:08:05 - 01:00:12:03
Stefan
Clip that. Yes, it's very true. Individual developers. Yes I agree like.
01:00:12:05 - 01:00:45:18
Jens
They what what developers do is they go to their boss and say, hey, can I have an AWS
account? And they get an AWS account and then they gi they, they buy whatever they want. So
so that's the thing. And they buy like a database whatever. And they EC2 and they call it a day.
But if you have your boost thing or whatever you put it on compute, what happens is you buy
compute for $1 and you sell it for three or maybe 5 or 10.
01:00:45:20 - 01:01:06:19
Jens
And people will at some point, maybe they use it, maybe they don't trust you. Even so, it fails at
that stage. But even if it doesn't immediately fail, then people will be like, okay, but it's so
expensive. You're just a wrapper. Like, why am I paying ten bucks if it could cost one, can I not
self-host this thing?
01:01:06:19 - 01:01:35:05
Jens
And then you're like, yeah, but self-hosting is more complex. And they will be like, yeah, I don't
care. Like my time is worthless. I don't value my time. I can I can do everything. And, yeah. So
it's I don't know, it's it's it's not, it's not a world I want to be in. So like, yes, you can somehow
resell compute to, to be honest, like so many startups are just compute resellers like you.
01:01:35:05 - 01:01:43:28
Jens
You are just an AWS reseller with, I don't know, some fancy whatever, but, yeah.
01:01:44:01 - 01:01:56:07
Stefan
You can make good money doing it, you can make good money just being a reseller, and you
can improve the experience a little bit there. Startups that there are whole premises AWS
without the AWS. But you eventually. Yeah. hit that point.
01:01:56:09 - 01:02:03:04
Jens
That's this one company. What was the name again which one they resell AWS actually.
01:02:03:07 - 01:02:04:15
Stefan
01:02:04:17 - 01:02:05:25
Jens
You know what I mean?
01:02:05:28 - 01:02:09:10
Stefan
I'm trying to think of the name they resell like the credits is a flight controller.
01:02:09:10 - 01:02:15:18
Jens
nonono, they they give you a new experience on top of the SSD. No.
01:02:15:20 - 01:02:24:01
Stefan
That's control. That's, there's flight control, there's SSD, there's fly.
01:02:24:03 - 01:02:28:01
Jens
Yeah. Similar. Similar, similar. Okay.
01:02:28:03 - 01:02:37:02
Stefan
I'm really trying to remember is a pump is it up? Remember. But okay. Just saying just a
company that just basically sells you AWS with a better.
01:02:37:05 - 01:02:37:14
Jens
Yeah.
01:02:37:15 - 01:02:43:22
Stefan
Oh oh, oh. It's, Yeah. Railway is a railway. Yes. Okay. Yeah. Yes.
01:02:43:25 - 01:03:20:19
Jens
Yes. You know, in, in in my 700 years of being a developer, I have, I have really learned one
very important thing. You buy databases and compute from AWS, GCP, or maybe Azure, and
you, you you just don't use startups because startups absolutely suck at reliability. And if you
think it cannot get any worse, then try fly.