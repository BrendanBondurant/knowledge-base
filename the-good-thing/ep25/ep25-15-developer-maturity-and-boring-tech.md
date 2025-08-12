
---
title: Developer Maturity and Boring Tech
slug: ep25-15-developer-maturity-and-boring-tech
series: The Good Thing
episode: 25
chunk: 15
participants:
  - Stefan Avram
  - Jens Neuse
  - Kevin Swiber
segment: Technology Pragmatism and Infrastructure Choices
timecode: 01:01:19:16 – 01:05:30:07
start_time: 01:01:19:16
end_time: 01:05:30:07
speakers:
  - Kevin
  - Jens
  - Stefan
topics:
  - Clean code evolution and moderation
  - Pragmatic technology choices requiring experience
  - Young developer enthusiasm vs experienced pragmatism
  - Boring technology preferences for reliability
  - Infrastructure stability over novelty
tags:
  - ai
  - postgres
  - kubernetes
  - clean-code-evolution
  - pragmatic-technology
  - developer-experience
  - boring-tech-preference
  - infrastructure-stability
  - reliability-focus
entities:
  - Clean Code book
  - Digital Ocean
  - Docker
  - Postgres
  - WunderGraph platform
  - Kubernetes
  - Google Cloud Platform (GCP)
  - Render platform
  - Fly.io
mentions:
  - Clean code harmful behavior when taken hardcore
  - Nuanced approach to code quality
  - $5 Digital Ocean droplet enthusiasm
  - Self-hosting database reluctance
  - Two years without infrastructure glitches
  - Vendor reliability concerns
  - Boring Postgres preference
  - Cool vendor deployment disappearances
summary: |
  Kevin emphasizes that effective pragmatism requires experience, using the hammer vs screwdriver analogy. Jens reflects on his evolution from hardcore clean code advocacy to understanding its harmful potential when taken to extremes. He shares how his infrastructure preferences evolved from cheap DIY solutions to boring, reliable choices like GCP Kubernetes, citing two years of glitch-free operation. The discussion highlights how experienced developers prioritize stability over exciting new vendors after experiencing deployment failures and poor support.
---

01:01:19:16 - 01:01:23:18
Kevin
Like it's you're going to have another awakening coming soon.
01:01:23:21 - 01:01:54:15
Jens
Yeah. You know, it's so funny. Like, I had this meme in my head while you were talking and you
didn't mention it already because, you know, I was young and I had no clue I was doing things.
And I was reading, like, clean code. And then I had this phase where everything had to be clean
code. And then you get older and you work on different projects, and you kind of realized that if
you go hardcore, clean code, you're actually harming your company.
01:01:54:15 - 01:02:18:14
Jens
Like it's harmful behavior. Like you don't need to be hardcore, you need to be a little bit or a
nuanced way of clean code. And in the end, if you go to this down, down this hill again, you kind
of realize some aspects of clean code. They are good, but it's not like, I don't know, it's clean.
Clean code is one of the many things that that matter to you.
01:02:18:14 - 01:02:40:10
Jens
And it's yeah, it's I think we often we go through this cycle of we learn something and we're
absolutely crazy about it and then we normalize. And if you if you become like this, like a, a
more experienced developer, you kind of figure out that you're I would say you're also less
excited about new stuff because you already kind of know, like, yeah, okay.
01:02:40:10 - 01:02:56:19
Jens
Like it's LLMs a new thing. But in the end it's also just an LLM. And then like everything else
also matters. So I think we're this is why you why you see like older developers, they, they calm
down a little bit.
01:02:56:22 - 01:02:57:25
Stefan
It depends.
01:02:57:28 - 01:03:28:15
Kevin
Yeah I think to be effectively pragmatic you need experience. Right. Like you need to to know
well, you know, sometimes I need a hammer or sometimes I need a screwdriver. And then
sometimes I got to go, you know, build my own tool to get this done. Right. But, yeah, it's, it's
easier to be more pragmatic when you've got, experience over time and you understand, you
know, what patterns and what solutions work for, what problems.
01:03:28:16 - 01:03:50:04
Jens
You know, this is another thing. When I, when I was like younger, I would I would always go like,
oh, let's buy a $5, droplet on Digital Ocean. It's cheap. And we can, we can with Docker, we can
run Postgres and everything there like it's cheap and everything. And these days I would never
want to run a Postgres database myself.
01:03:50:04 - 01:04:26:15
Jens
Like, never like, can we just buy something and you know, have you ever tried like we have and
you know, there's all these cool vendors that can deploy your stuff like render and whatsoever.
And I'm not talking negative about any of them. Okay. But we have, we have our backend for
our platform. It's, it's on Kubernetes. It's, it's on the most expensive tier of, of GCP Kubernetes
with just some kind of autopilot thing, like it's more expensive, but we have this pod or this stuff
we have this running for, I think more than two years.
01:04:26:17 - 01:04:51:14
Jens
Not a single glitch like nothing to deploy it. It works for two years. Like it's insane. And if you
understand this, you're like, why try out like a cool vendor? I was like, oh, we like, you know, this
is also something like, you know, with with WunderGraph, we built cool new tech, but we, we
tried to build it on the most boring tech we can.
01:04:51:14 - 01:05:30:00
Jens
We can. It's like Kevin said, yeah, the things we want to use are we, we want to like, we don't
want the fancy database. We want the most boring Postgres. And it just like make the problem
go like, and this is, I don't know, if you build for a long enough, you're kind of realizing I just want
the boring stuff because it doesn't break apart and you stop trying out like vendors like fly where
I don't know, suddenly your your deployment disappears and you don't know why and the
support doesn't answer or you're going through those kind of scenarios and then you realize,
you know what?