---
title: Strategic Technical Decisions and the SDK-to-Cosmo Pivot
slug: ep10-01-technical-pivot-to-cosmo
series: The Good Thing
episode: 10
chunk: 1
participants:
  - Stefan
  - Björn
  - Dustin
  - Jens
segment: Introduction and technical strategy
timecode: 00:00:04:07 – 00:09:15:16
start_time: 00:00:04:07
end_time: 00:09:15:16
speakers:
  - Stefan
  - Björn
  - Dustin
  - Jens
topics:
  - In-person 10th episode celebration
  - Co-founder introductions and roles
  - Open source architecture decisions
  - Amsterdam retreat and Cosmo pivot
  - Mono repo development approach
  - Connect Buff and protobuf tooling
tags:
  - open-source
topic_tags:
  - open-source
entities:
  - WunderGraph
  - Cosmo
  - Amsterdam
  - Connect Buff
  - Protobuf
  - T-Online
mentions:
  - first in-person episode
  - Bretten working retreat
  - makeshift microphone setup
  - Amsterdam pivot decision
  - open source commitment
  - mono repo efficiency
  - protobuf contract generation
summary: Stefan introduces a special 10th episode recorded in-person with all co-founders
  in Bretten. Dustin explains the technical decisions that shaped WunderGraph, including
  the commitment to open source and mono repo architecture. They discuss the pivotal
  Amsterdam retreat where they decided to go all-in on Cosmo and how protobuf tooling
  enabled rapid development across multiple languages.
---
Episode 10
00:00:04:07 - 00:00:11:28
Stefan
Hey, guys. Welcome back to another episode of The Good Thing. My name is Stefan, and today
we have a very special episode because we're actually in person.
00:00:12:00 - 00:00:37:10
Stefan
So you can see here that I'm actually touching my co-founders. We're here for the first time in
Bretten on a working retreat, and for our 10th episode, we thought we would make it special by
having an episode with all of the co-founders. Usually it's mostly me and Jens, but today we've
also brought in Björn and Dustin. We also have this makeshift microphone that Dustin helped
build for us, but I'm going to pass it off to my two co-founders that you've maybe seen Dustin on
the show, but also Bjorn is his first time on the show, so I'd love for you to introduce yourself.
00:00:37:10 - 00:00:39:27
Stefan
Björn. Björn, how are you doing today?
00:00:39:29 - 00:01:02:10
Bjorn
Besides having a cold, which kind of affects my voice, I'm afraid, I'm good. Super excited to be
here again after, you know, being gone for two days to do some other stuff. I'm Björn, the COO
of the company, one of the co-founders, and I do all the stuff behind the scenes. So this is kind
of my perfect opportunity to finally tell you a couple of things, about what's it like to run a remote
first, crazy startup with a lot of crazy guys.
00:01:02:10 - 00:01:03:10
Bjorn
So looking forward to that.
00:01:03:12 - 00:01:08:12
Stefan
I love that I have a mic here so I can talk to you, but Dustin, I.
00:01:08:14 - 00:01:15:08
Dustin
Hope you have seen me already on the episode. So yeah, my name is Dustin. CTO of
WunderGraph. And, yeah.
00:01:15:10 - 00:01:21:06
Stefan
I knew you were going to make that intro. I knew he was going to make that intro. Dustin. We
like to call him The Machine because.
00:01:21:08 - 00:01:22:00
Bjorn
Prince Charming.
00:01:22:00 - 00:01:44:05
Stefan
Prince Charming and the machine. But this episode special because, one, we're in person and
two, we have some really exciting updates coming soon. But what we want to do on today's
episode is just kind of talk a little bit about how we got to this point. So for those of you that don't
know the story, I met Jens online in 2021 or 2022? a long time ago, if you will, right after Covid
and we met online.
00:01:44:11 - 00:02:03:25
Stefan
He knew Bjorn from his working days at T online. And then we met Dustin through open source.
And when you look back at everything that we've achieved, that's amazing. And so for today's
episode, as our 10th anniversary, no, I'm kidding. As our 10th episode, we're going to be talking
about the strategic decisions that shaped WunderGraph. And what's really exciting about this
one is you're going to get a viewpoint from different parts of the company.
00:02:03:25 - 00:02:26:23
Stefan
So what was strategic that shaped us from the customer side, from the business side, from the
product side, as well as for the development side. And so I like to kick this off and start with
Dustin. Dustin, we talk about this a lot, but what are some of the strategic decisions that you
made from the technical side? After our meeting in I think it was Amsterdam, we were on a
working retreat and things weren't looking good for the company, and we decided to go all in on
Cosmo.
00:02:26:23 - 00:02:34:27
Stefan
And to this day, the architectural decisions that we made were paramount to our success. What
were some of the decisions that you made and why?
00:02:34:29 - 00:03:02:17
Dustin
I think the fundamental decision was, first of all, of being fully open source. I think this has
shaped, the past and also the future. Another thing is, we, our architecture, everything, is also
open source and, openly available. And, during building Cosmo Cloud, one of the key principles
was always to focus primarily on our core components.
00:03:02:19 - 00:03:23:15
Dustin
We never try to be an expert in everything, anything else except what we have built in-house.
And I think this gave us that productivity, efficiency on all, on all sides to build Cosmo in a small
team. And coming to this point today where we, yeah.
00:03:23:18 - 00:03:39:28
Stefan
Well said, and we talked about this in the last episode. And Jens, you weren't too happy about
this, but pass the mic to Jens. I want to hear from a product point of view how we got you to to
leave your baby, to leave the SDK, to kill it essentially, and to go all in on Cosmo with us.
00:03:39:28 - 00:03:50:19
Stefan
I remember the first couple of weeks you weren't too happy, but then the gears started turning
and we made some key product decisions. What were some of those key decisions that helped
shape us as a company?
00:03:50:21 - 00:04:15:06
Jens
Yeah. First of all, I would say so it was my idea to create the WunderGraph SDK because prior
to WunderGraph, I worked for, a company called TYK technologies. We built an API gateway,
and I always thought that the workflow is really cumbersome that a developer wants to configure
an API gateway, and we do almost everything in code.
00:04:15:08 - 00:04:39:14
Jens
But when I want to change the configuration of my API gateway, I have to open a dashboard like
a console. I have to make changes, save the the changes they get. Then moved over to
gateway applied and now the gateway has some new functionality. And that felt like from a
workflow perspective, I thought, wouldn't it be much better if we have an SDK?
00:04:39:14 - 00:05:01:28
Jens
We can configure everything in code our all our API dependencies and how the gateway should
behave and how it should bring together the data. So. So that was my idea. I thought, that's a
great product. And what we what we realized is that a lot of developers really like the solution.
And it worked extremely well when you're a single developer.
00:05:01:28 - 00:05:30:11
Jens
But, the, the, the real problem here was, we couldn't sell this because it didn't really have impact
on, on a larger team or at the, at the organization scale. So typically we were talking with single
developers, people who were building like full stack apps. So yeah, it just didn't work. And we,
we had to abandon this idea and and obviously, if you invent something, you're emotionally
attached to it.
00:05:30:13 - 00:05:54:05
Jens
So it's, it's a bit hard to, to let go. So I think for the first 1 or 2 months, I struggled really to, to.
Yeah, come to terms that, this was a good idea. And now we're moving on. And what was really
great during this time is that I don't know that Dustin wasn't that attached because it was not his
idea, but Cosmo was his idea.
00:05:54:07 - 00:06:17:24
Jens
And so he immediately jumped onto this, new topic. And, he bootstrapped Cosmo in no time
and then, Nithin and Suvij, helped him build this. And I have one, one follow up question,
because one thing I have observed from my role is that we we really have, like, the velocity we
have in our stack with Cosmo.
00:06:17:24 - 00:06:43:08
Jens
It's it's incredible how fast we were able to iterate. And maybe you can expand a little bit on what
were architecture and tooling decisions. And then how did you yeah. How did you built up the
Cosmo Mono repo in a way that allowed us to move so fast? Because, like I would say, the
there will be many smart engineers who can build something like Cosmo.
00:06:43:12 - 00:06:51:15
Jens
But what we have created is not just the solution, but rather, a solution where we can iterate
upon, like, very, very fast.
00:06:51:17 - 00:06:53:26
Stefan
Yeah. Well said, I’d love to hear that.
00:06:53:28 - 00:07:18:27
Dustin
Yeah. I mean, it's, I think it's very natural to start off with a mono repo approach. I think, I
wouldn't have said that before, I think, ten years ago, but today everything starts with a mono
repo, and you're going from there. You're trying to extend, the stack, and incorporate more
components, more services. I think if you have to start with such a small team, you're, you're
you're thinking big.
00:07:18:29 - 00:07:47:10
Dustin
You need to come up with a setup which is very efficient, which is easy to maintain from a CI/
CD perspective, but also from a collaboration perspective. So we I research a lot how we could
build, Cosmo. And what I have seen in the ecosystem is that how you can actually generate,
based on proto files, different clients in different languages.
00:07:47:12 - 00:08:14:20
Dustin
And this, ecosystem, tooling, it's called Connect Buff, which allows you to, based on a proto file
definition to generate not just TypeScript Golang clients, but also web clients. So and if we if we
can all together collaborate on the protobuf definition and, yeah, build the API contracts and
make the whole stack working. I think that was, the best experience so far we had.
00:08:14:23 - 00:08:46:12
Dustin
It was very easily easy to, to to add more things to the, to the, to the, to the project. One
example our router is written in go our control plane, which is a schema registry. And and the
API to our studio is written into TypeScript, Node.js. So we were able to, based on the portal
definition, generate a TypeScript client, that interacts with the control plane, which would, which
use query our router communicate with our data collectors, which are written and go.
00:08:46:15 - 00:09:15:16
Dustin
And we were also able to generate go clients based on the protobuf definition. And if you
already recognize that, that means, yeah, we have to touch one API definition file to
communicate and to, yeah, establish contracts across all these components. And this
architecture allowed us to. Yeah. To, to not think about, view models to think about middleware
we could just focus on the implementation.