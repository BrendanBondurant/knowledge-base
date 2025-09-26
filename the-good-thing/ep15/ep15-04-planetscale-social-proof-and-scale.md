---
type: podcast-chunk
title: PlanetScale Bold Claims and Targeted Database Messaging
slug: ep15-04-planetscale-social-proof-and-scale
series: The Good Thing
episode: 15
chunk: 4
segment: PlanetScale Landing Page Analysis
timecode: 00:15:17 – 00:20:38
start_time: 00:15:17
end_time: 00:20:38
speakers:
  - Stefan
  - Jens
topics:
  - PlanetScale Landing Page
  - Bold Performance Claims
  - Technical Audience Targeting
  - Case Study Proof
tags:
  - ai
  - database
  - api-design
  - database
  - benchmarking
  - go
  - mysql
  - startup
  - vitess
entities:
  - PlanetScale
  - eBay
  - Cash App
  - Vitess
  - NVMe
summary: |
  Stefan and Jens analyze PlanetScale's dramatically simplified landing page featuring bold performance claims like "world's fastest database." They discuss the strategic targeting of technical audiences, the effective use of case studies like Cash App, and how the seemingly "ugly" design actually appeals to developers who care more about performance proof than visual polish.
---

00:15:17:22 - 00:15:38:15
Jens
So he's able to talk about like the improvements within eBay, but also the improvements for like
he links that to the customer. And so even if you're a non-technical person, you will read this
and you will see, oh, this makes the sellers thrive. Okay, that must be good. Even if you don't
understand what an API is.
00:15:38:18 - 00:15:54:18
Stefan
Yeah. That's it. So I think the whole quote, by the way, is on the customer's page. I know we we
clicked it, but I totally agree with you. I have some feedback on these, but let's jump away from
ours for now and then we'll get back to roasting it. Let me share one that I think you don't like.
00:15:54:21 - 00:16:20:16
Stefan
but I think is amazing. Okay. Do you think it's a little bit I don't know, you'll see when I, when I
bring it up for the. Here we go. Okay, okay. For those of you that don't know, this is planet scale.
It is the. They used to have a complex data, a complex landing site, and then they completely
stripped it out.
00:16:20:19 - 00:16:28:03
Stefan
I think it's fantastic. But I will let you go first. Jens, what are your initial thoughts on Planet
Scales landing page?
00:16:28:06 - 00:17:01:21
Jens
Okay, let's let's look at the hero. The world's faster and most reliable relational database. It's a
bold statement. Very it's a very bold statement. And then the next thing then there is a blurb. But
somehow, visually, I skip this because in the next blob, in the in the next paragraph, there's a
link and it says our blazing fast NVMe drives unlock unlimited IOPs, blah blah blah.
00:17:01:24 - 00:17:22:18
Jens
Okay, plan and scale managed. Then they link to performance so they are probably able to
prove this. They link to Vitesse and they show our technology powers. Tier zero databases.
Okay, click on tier zero. What is that?
00:17:22:20 - 00:17:29:27
Stefan
Did it change the page? Oh yeah. Yeah. Great. To a freaking case study. Cash app, cash apps.
00:17:30:00 - 00:17:34:28
Jens
That is it. Okay, go. Go back, go back.
00:17:35:01 - 00:18:17:05
Jens
So from the design, you would say, Holy shit, this is ugly, right? But at the same time, who is the
target audience? The target audience is people who want a relational database that speaks
SQL. And it needs to be scalable to the point where nobody else has scale databases will those
will database people will they will they like flashy diagrams or a terminal style website with hard
facts like these people, they, they, you know, they, they look at very yeah.
00:18:17:06 - 00:18:32:16
Jens
Explain query and things. So they look at terminals. I think the only thing to convince them is,
does it, does it scale? And here we have, we have slack and and others and
00:18:32:19 - 00:18:54:25
Stefan
Look at this though, like, like you said, like so database people, I mean, they're all about
sharding, performance, scaling it out. And I know Sam, he has crazy experience. But when you
buy Planet Scale, you're getting technology. And the expertise that ran in scale to YouTube, the
internet's number two site, and the team that scaled GitHub to over 100 million users globally,
that's a very bold statement.
00:18:55:01 - 00:18:56:25
Stefan
That is some big social proof.
00:18:57:00 - 00:19:02:23
Jens
You know, like I have some feedback actually, maybe the like a I guess I like this one.
00:19:02:23 - 00:19:05:15
Stefan
So we'll agree to disagree. It's Sam. Sam.
00:19:05:17 - 00:19:34:08
Jens
No, I'm not disagree I'm not disagree. But my my feedback for Sam is this, I know vitesse. I
understand what it is. It might take a little bit of time until everybody at this page understands
what it that this is. This is vitesse in a very professional way and not everybody knows that
vitesse was actually built by YouTube to sustain the scale of YouTube.
00:19:34:14 - 00:19:54:01
Jens
So what I would make more like I think I would build a, like a, like a bigger hero. And I would say
something like, everybody can now use the database that was able to sustain YouTube scale.
00:19:54:03 - 00:19:58:23
Stefan
What about this? And you see the change page. So he has it on a separate one.
00:19:59:00 - 00:19:59:18
Jens
Yeah.
00:19:59:21 - 00:20:08:17
Stefan
you like, you know.
Honestly that's cool by the way that you said it though, without, you know, your stuff Jens. But
00:20:08:20 - 00:20:38:25
Jens
YouTube, YouTube took MySQL and they built this sharding layer on top of MySQL because
MySQL eventually you have too much data. So you need to split your data into, into shards. And
essentially like we test it is an orchestration layer to, to to shard your MySQL database. It has
some trade offs, like you cannot do all, all operations, that you would do with a normal, relational
database.