---
title: Pricing and Proprietary Architecture
slug: ep23-02-pricing-and-proprietary-architecture
series: The Good Thing
episode: 23
chunk: 2
participants:
- Stefan
- Jens
segment: PlanetScale Business Model Analysis
timecode: 00:06:53:16 – 00:13:31:00
start_time: 00:06:53:16
end_time: 00:13:31:00
speakers:
- Stefan
- Jens
topics:
- PlanetScale pricing strategy
- Proprietary vs open source architecture
- NVMe storage technology
- Database hosting business models
tags:
- planetscale-pricing
- proprietary-architecture
- nvme-storage
- database-hosting
- business-models
topic_tags:
- planetscale-pricing
- proprietary-architecture
- nvme-storage
- database-hosting
- business-models
entities:
- PlanetScale
- Stefan Avram
- Jens Neuse
- NVMe
mentions:
- pricing model analysis
- proprietary technology benefits
- NVMe storage advantages
- competitive positioning
summary: Stefan and Jens analyze PlanetScale's pricing strategy and proprietary architecture
  decisions, discussing the benefits of NVMe storage technology and how proprietary
  solutions can create competitive advantages in the database hosting market.
---

00:06:53:16 - 00:07:00:12
Jens
It's, it's good for everybody who wants to have, a relational database. Do you see this, though?
00:07:00:14 - 00:07:08:00
Stefan
We've consistently outperformed every Postgres product on the platform, even when giving the
competition 2x the resources.
00:07:08:03 - 00:07:09:25
Stefan
Oh, yeah.
00:07:09:27 - 00:07:37:01
Jens
It's a little bit unfair because, you know, if you go back, there's this blog post about, planet scale
metal and essentially what, what planet scale does is, they figured out a way of running the, the
database, running them with a locally attached, NVMe drive, which it's it's very hard to to beat if
you have a network attached.
00:07:37:01 - 00:07:39:08
Jens
Hard drive.
00:07:39:10 - 00:07:43:27
Stefan
But they're building some hard core engineering like this is some pretty badass. Absolutely.
00:07:44:00 - 00:07:45:08
Stefan
Yeah.
00:07:45:10 - 00:08:05:20
Stefan
Question for you though. What do you think? Like not every company is a YouTube. Not every
company needs that amount of data and sharding. Do you think by being so hardcore that they
cut down on their available market, or do you think that we're now adding Postgres? Basically
they're going to be the database for big companies.
00:08:05:22 - 00:08:08:07
Jens
Can you go to the pricing page?
00:08:08:10 - 00:08:12:28
Stefan
Yeah. One second. Oops. Wrong page.
00:08:13:00 - 00:08:16:15
Stefan
Let's go to pricing okay.
00:08:16:15 - 00:08:23:03
Jens
Let's see where can we start. Let's what's the starting point? 39 bucks.
00:08:23:05 - 00:08:25:09
Stefan
Yeah.
00:08:25:12 - 00:08:27:28
Jens
With a ten gigabyte database.
00:08:28:00 - 00:08:32:26
Stefan
Yeah. I mean, why not?
00:08:32:28 - 00:08:37:09
Jens
I would totally buy it.
00:08:37:11 - 00:08:37:15
Stefan
Too.
00:08:37:18 - 00:08:54:26
Jens
Yeah, 1500 gigabytes. It costs you something. But starting with with 39 bucks. I mean, if you
want to have a reliable database, why not, click, click on metal. This gives us more IOPs. Click
on metal.
00:08:54:28 - 00:09:02:00
Jens
Okay. So if you want to have a super fast database it starts at scroll down.
00:09:02:03 - 00:09:02:18
Stefan
It's actually right.
00:09:02:18 - 00:09:04:10
Stefan
Here, 600 bucks.
00:09:04:13 - 00:09:07:19
Jens
Yeah. But is it the total cost.
00:09:07:22 - 00:09:09:10
Stefan
609. Yeah.
00:09:09:12 - 00:09:37:22
Jens
Okay. Yeah that's the question. So I guess not. This is not for everybody. But if you have, if you
have, a serious thing going, then yeah, you should definitely think about it. I mean, if you, if you
build an app and it's latency sensitive and let's say you have 100 milliseconds latency and let's
say of that 100 milliseconds, 30 milliseconds is, is, database.
00:09:37:22 - 00:09:46:06
Jens
And you can cut it down to five. It could be worth it. If you're in e-commerce something this will
immediately pay back.
00:09:46:08 - 00:09:53:10
Stefan
I mean, check this out. 64 vCPUs. 512gb memory. What is this? GB NVMe?
00:09:53:12 - 00:09:58:00
Jens
That's the, that's the drives, the locally attached drives.
00:09:58:03 - 00:10:06:18
Stefan
And damn, 23,000 a month. And then if you add a little bit more 44, it's kind of cool. You can see
the entire pricing here.
00:10:06:20 - 00:10:10:21
Jens
Yeah. They also don't do weird weird enterprise pricing.
00:10:10:24 - 00:10:14:17
Stefan
So I don't know I, I.
00:10:14:17 - 00:10:25:18
Jens
I think you for 600 bucks you get an insanely fast database. If you have an operation that needs
a fast database, sure. That that can make sense.
00:10:25:21 - 00:10:33:25
Stefan
month.
But look at this. Like if you wanted to shard it, you're looking at work 16 shards, 1 million a
00:10:33:27 - 00:10:35:21
Stefan
I mean. Yeah, okay. You you you.
00:10:35:25 - 00:10:40:27
Jens
You have like, you chose a lot of compute and everything.
00:10:40:29 - 00:10:44:13
Stefan
I mean, it's pretty incredible how they show you everything on here.
00:10:44:15 - 00:10:45:15
Jens
Yeah.
00:10:45:18 - 00:10:53:04
Stefan
But. And then I guess for enterprise, it's if you want to bring your own cloud. So what does that
mean? But you don't use their cloud.
00:10:53:06 - 00:10:58:10
Jens
You, you can you can deploy them into your cloud.
00:10:58:13 - 00:11:06:01
Stefan
This is pretty badass. No, I think what they're building over at planet scale is pretty amazing. I
mean, look at these companies. They got some hype. Yeah. Well, cursor. I gotta.
00:11:06:02 - 00:11:17:08
Jens
Go. Go back to this blog post about Postgres. Here, because I, I figured there's something
interesting search for the term, proprietary.
00:11:17:11 - 00:11:20:06
Stefan
Proprietary.
00:11:20:08 - 00:11:48:23
Jens
Yeah. You see, plants scale for Postgres uses real Postgres running on our proprietary operator,
blah, blah, blah, blah, blah, query buffering and connection pooling via our proprietary proxy
layer PSbouncer. So they have a bunch of proprietary stuff. And I think it's it's pretty smart what
they're doing. Like, Vitess, it's it's open source, but they're their operator.
00:11:48:23 - 00:12:13:23
Jens
It's not open sourced. The PSbouncer is not open source. So there's, there's a moat. And I think
they, they understand the value. And, yeah, I think they are they are doing it. But you know,
other companies like for example, let's say the search Elasticsearch, they have this issue with
licensing and AWS and something and to me it seems like planet scale.
00:12:13:23 - 00:12:37:09
Jens
They figured out a great way where to draw this open source proprietary line like nobody will
complain about, hey, you have this proprietary PSBouncer, people will just want to use it. And I
can I can deploy it in my own account or something. So I don't know a good, good service, good
company. I'm I'm fan honestly.
00:12:37:11 - 00:12:57:15
Stefan
And that's the Jen's recommendation seal. Jacob, we need if you ever seen there's this
YouTuber where like when he approves of a video game, it stamps like a big stamp. So it's like,
Sam's approval. We need one for Jen's, if that. If Yen's approves of a company. stamp? Yeah.
No, I'm. No, I'm honestly in the same way to go ahead.
00:12:57:16 - 00:13:31:26
Jens
Sometimes I see posts from Sam on Twitter and I'm like, I'm not sure if I. If I like this person,
they I don't know, they are. They are special in a way. But at the same time, it seems like they
are doing a lot of stuff. Right? And, I also heard that, someone wrote on, on LinkedIn that if you,
if you join a startup and the CEO is not a little bit intense, then probably it's, it's a it's in the
wrong company.