---
title: Fly.io, Platform Building, Reliability, and Support
slug: ep04-08-flyio-platform-reliability-support
series: The Good Thing
episode: 4
chunk: 08
participants:
  - Stefan
  - Jens
segment: Experiences with Fly.io, building on platforms, reliability issues, and support
  challenges
timecode: 00:22:00:14 - 00:25:32:21
start_time: 00:22:00:14
end_time: 00:25:32:21
speakers:
  - Stefan
  - Jens
topics:
  - Fly.io
  - Platform building
  - Reliability
  - Support
  - Product focus
  - Vendor relationships
  - API integration
  - Customer support
tags:
  - startup
  - founder
topic_tags:
  - startup
  - founder
entities:
  - Stefan
  - Jens
  - Fly.io
  - Apollo
  - Calendly
mentions:
  - fly machines
  - firecracker
  - CI workflows
  - support tiers
  - API spec
summary: Stefan and Jens discuss their experiences building on Fly.io, the promise
  and challenges of the platform, reliability issues, and the lack of support. They
  compare Fly.io to other vendors and reflect on the importance of listening to customers
  and providing robust support.
---

00:22:00:14 - 00:22:17:24
Jens
It but it can also go the other way around. So sometimes you meet startup founders who clearly
they clearly mess up. They are disconnected from reality. Should we talk about fly?

00:22:17:27 - 00:23:00:18
Stefan
We can talk about fly. We can talk about Apollo. You can talk about Calendly. I mean, it's all
these great companies and they just don't listen. Let's do it. I like it because it bothers me,
especially as a startup founder. But what are your thoughts on fly?

00:23:00:18 - 00:23:01:27
Jens
Or.

00:23:01:29 - 00:23:23:21
Jens
GCP, they have something to to deploy apps and in a simple way like Fargate or something. But
it's always like all these services, they were kind of slow, and it was really hard to like, I, I quickly
want to build and deploy a container in Frankfurt and another one in the US and another one in
London, and fly allowed me to do this.

00:23:23:21 - 00:24:15:02
Jens
And I thought, that's that's revolutionary. But, they did something that that I thought it's, it's even
it goes beyond that. They created something. It's called fly machines. And I think it's it's such a
brilliant idea. So they take the, they take the, the firecracker API, which is AWS has, built this as
far as I know, it's like an, an abstraction on top of, Linux that gives you like a very simple API to,
to deploy, like containerized workflows on, on hardware, very lightweight, thin wrapper startup
time is extremely fast.

00:24:15:04 - 00:24:41:03
Jens
And this would allow you to put like a go application or a node application like into Frankfurt.
And when a request comes in, because this is such a lightweight, virtual machine, engine, within
a couple milliseconds, it can, it can start this container started up and you can you can build
your business on top and what this allow or what this could allow you to do.

00:24:41:03 - 00:25:05:21
Jens
For example, we tried using this in, in our previous, endeavor with, with Wunder Graph Cloud.
We built a builder service with this. So what this does is we, we took this fly machines API and
we, we put on top, like, CI frameworks so that you can use fly machines to run CI within our
service.

00:25:05:21 - 00:25:32:21
Jens
It it was really cool. Like you, you trigger the CI on when you make a git commit. We start up the
fly machine. We run your work, your workflow. It's all like isolated. Like really cool tech. And
there were just huge problems. We, we had in executing this and it started with. So one of the
biggest issues was, reliability.