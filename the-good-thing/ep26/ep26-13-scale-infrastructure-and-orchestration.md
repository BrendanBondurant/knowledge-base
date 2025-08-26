---
title: Scale Infrastructure and Orchestration
slug: ep26-13-scale-infrastructure-and-orchestration
series: The Good Thing
episode: 26
chunk: 13
participants:
  - Stefan
  - Jens
  - Sam Lambert
segment: Database Company Passion and Scale Orchestration
timecode: 01:01:10:22 – 01:05:02:25
start_time: 01:01:10:22
end_time: 01:05:02:25
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - Alternative career paths and scale fascination
  - Infrastructure company customer relationships
  - Database complexity vs academic theory
  - 500-node cluster orchestration
  - Real-world scale deployment satisfaction
tags:
  - startup
  - ai
  - database
  - go
  - rest
topic_tags:
  - startup
  - ai
  - database
entities:
  - PlanetScale
  - Amazon
  - WunderGraph
mentions:
  - Working vicariously through customers
  - Products used in physical world
  - Academic vs practical database approaches
  - 500-server cluster single-button deployment
  - Cross-zone orchestration
  - Unison database serving
summary: |
  Discussion of what drives passion for database and infrastructure work, focusing on the satisfaction of seeing massive scale orchestration in action. Sam describes the thrill of watching 500 servers coordinate to serve a single database connection string.
---

01:01:10:22 - 01:01:17:00
Jens
And, what do you use as the, as the virtualization layer on, on behind the scenes?
01:01:17:03 - 01:01:23:11
Sam
What is it that Amazon use? It's the Amazon. What is it they point.
01:01:23:13 - 01:01:24:15
Jens
You mean firecracker.
01:01:24:16 - 01:01:27:07
Sam
Yeah, probably.
01:01:27:10 - 01:01:29:29
Jens
Yeah okay. That's
01:01:30:01 - 01:01:42:28
Sam
We run on we can run on EKS. We run on Google's version too. Yeah, it just fits in. Which was
specific to whichever cloud that we're running in. Basically.
01:01:43:00 - 01:02:06:26
Jens
Okay. If you if you didn't, if you wouldn't be in planet scale today. Would you start another
database company. Would you ever recommend anybody starting a database company? Is it
cool to run a database company, or would you do something else?
01:02:06:28 - 01:02:37:12
Sam
I don't do databases. Yeah, I don't know, I do something, I just like working at scale. You know, if
I didn't have a if I wasn't running a database startup, maybe I'd work at another product
company that has a lot of scale, and that would be fun. I don't know, though, like, there's
something about working at an infrastructure company that has all of these various customers
that I find incredibly fun and interesting, like just seeing what our customers do and doing
something that's so critical to them.
01:02:37:15 - 01:02:56:10
Sam
It's really fun. You live, like, vicariously through your customers. It's like a real kick to like, yeah, I
mean, we just signed up a customer that is a product, the product in the physical world that I
use all the time. And it just it's really fun to know that, like, the things you're doing. Empowered.
Yeah. Yeah. I've had by your product.
01:02:56:10 - 01:03:00:25
Sam
It gets really addictive sending a slack message or, you know, it just feels really fun.
01:03:00:28 - 01:03:12:09
Stefan
I tell that to my wife all the time. Like, we'll be walking by and I'll be like, oh, their website
powered by Wundergraph for, like, this retail store. Like, that stuff is powered by Wunder Graph.
And she's like, do you get discounts? I'm like, well, no, not like that.
01:03:12:09 - 01:03:23:08
Sam
But still yeah yeah yeah yeah. No, it's exactly that. You go, yeah. You drive past a billboard. It
just feels nice. And you became really loyal to your customers that you feel really grateful to
them. It's that it's lovely.
01:03:23:11 - 01:03:28:09
Stefan
I agree. And Jens, I have one question though, so I'll go ahead. We have one more. We have
time for one more. But go ahead.
01:03:28:11 - 01:03:42:28
Jens
Is it about the the scale by itself or the complexity of the problem, or is it really you, you like to
be, to be part of these companies, to be powering them or like what, what what's it's.
01:03:42:28 - 01:04:07:20
Sam
All of those like the complexity comes from scale. But like databases or any tech stuff that's not
at scale, just a real boring to me. Like what's like this is the issue with database world, right?
Like there's the academic end, which they have is obviously have significant contributions, but
you see these like hot new database is or whatever that do all these little like these fun whizzy
features and just can't scale at all.
01:04:07:20 - 01:04:32:29
Sam
It's like, okay, that's that's the boring. But you may join me. We all pretend we're an aircraft. We
sit in a box and go make noise, plane noises. It's like it's actually putting real stuff on the line.
People backing real products, is the bit that's hard. Like there's just. I watched a customer spin
up a cluster the other day that was a single database cluster with about 500 nodes in it.
01:04:33:01 - 01:05:02:25
Sam
Right? So it just they pressed one button and behind the scenes, all of our orchestration starts
in across three zones, hitting Amazon to start spinning up machines and just watching 500
servers orchestrate spin up, get a clean version of our infrastructure report for duty and
immediately act in unison to provide to like serve a database through one connection string.