---
title: Chaos Engineering and Kubernetes
slug: ep26-12-chaos-engineering-and-kubernetes
series: The Good Thing
episode: 26
chunk: 12
participants:
  - Stefan
  - Jens
  - Sam Lambert
segment: Reliability Engineering and Infrastructure Architecture
timecode: 00:56:07:17 – 01:01:10:19
start_time: 00:56:07:17
end_time: 01:01:10:19
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - Continuous deployment and bug management
  - Shared nothing architecture benefits
  - 29-day node expiry policy
  - Chaos engineering principles
  - Kubernetes for stateful workloads
  - Virtualization layer choices
tags:
  - kubernetes
entities:
  - PlanetScale
  - Kubernetes
  - Amazon
  - Firecracker
  - EKS
  - Google Cloud
mentions:
  - Progressive rollout and monitoring
  - 29-day maximum node lifetime
  - Constant node failures and repairs
  - Planned and emergency repair systems
  - Kubernetes operator for database state
  - Firecracker virtualization
summary: |
  Deep dive into PlanetScale's reliability engineering practices, including their chaos engineering approach with 29-day node expiry, shared nothing architecture, and their advanced use of Kubernetes for running stateful database workloads at scale.
---

00:56:07:17 - 00:56:37:22
Jens
Yeah. You you have, a pretty decent score in terms of availability of your service. And, like one
thing, I think we we all agree software has bugs. Yeah. And when you change software, you
introduce bugs. You fix some, you add some more. How how how can you actually ensure that
whatever you're deploying, like, you're, you're not breaking your your customers.
00:56:37:22 - 00:56:47:09
Jens
Like what? What is happening like behind the scenes to to be able to continuously contribute to
a database project and not mess it up.
00:56:47:12 - 00:57:07:02
Sam
Yeah. So we're not perfect. We obviously do create bugs and our software has bugs and has
edge cases. I think it all begins with the acknowledgment that those things happen. Right? Like
if you if you're leveraging that, you're going to create bug like the idea that you're going to create
bug free software, you're going to make less availability, right?
00:57:07:05 - 00:57:31:26
Sam
There's a lot of stuff that comes down to our shared nothing architecture, meaning that we have
no single, no true single points of failure in the stack, meaning you can incrementally roll things
out in ways that, get well tested and you can roll things back very, very simply. We obviously
start with a progressive kind of rollout and monitoring of of with that via our tooling that make
that possible.
00:57:31:28 - 00:58:06:07
Sam
And you just have to be very careful. You have to embrace a system that constantly changes.
So we excuse me. No, node of planet scale stays online for more than 29 days. Every single
node expires after 29 days, meaning the whole environment is entirely ephemeral. And it makes
you much like all those little things that churning through connections, churning through state, all
of those things that companies don't do often causes more outages for folks.
00:58:06:10 - 00:58:21:21
Sam
The fact we do it constantly and the system is designed, and when you ship something to
production, you have to account for the fact those things are going to happen. That's the that's
the, the special sauce.
00:58:21:23 - 00:58:38:23
Jens
. So with the with the 29 day expiry on all on all nodes, you, you kind of have Chaos monkey
embedded in the system because it probably means that every day some nodes come, some
go. And it's, it's a continuous every hour spiking of nodes.
00:58:39:00 - 00:59:01:02
Sam
Yeah. We run at such scale that you just we have constant node failures just constantly disks
explode like just constantly. And so it's great. I mean, the way you actually heal the
infrastructure is you kill nodes. We we have a prs and the ers is a planned repair parent shard
and a is is emergency. Those are like the ways you fix most problems.
00:59:01:02 - 00:59:21:16
Sam
If a node's misbehaving rather than like coddling it and trying to figure out just kill it, get rid of it,
look through the logs, isolate and find out what actually truly happened. But the immediate fix is
to kill it and have the cluster resolve back to a healthy state. When you've done that millions
upon millions of times, you get something that's very robust.
00:59:21:23 - 00:59:48:23
Sam
And it's the same with again, back to airplanes, right? They just have done millions and millions
of flight hours on very simple, principles. And the components of the system are very well tested
and stress tested. If you do that, you can you can gain continual leverage. And it's hard to
compete with. It's very hard to start like it's from first principles and build systems like that
without a lot of knowledge and expertise.
00:59:48:26 - 01:00:12:03
Jens
Yeah. But by the way, like when we're talking about, like, killing nodes and starting new nodes
and something well, what's what's the kind of scheduler behind the scenes like one of the most
well-known schedulers for running things is like, for example, Kubernetes. But do you, do you
have some like do you use like an existing product or have you built your own or how do you do
Kubernetes?
01:00:12:03 - 01:00:16:06
Sam
We by far run the most state in the world on Kubernetes.
01:00:16:08 - 01:00:18:08
Jens
Even with your metal machines.
01:00:18:08 - 01:00:19:19
Sam
Yes.
01:00:19:21 - 01:00:22:04
Jens
So on metal you run Kubernetes.
01:00:22:07 - 01:00:42:08
Sam
Its extremely light. They run as pods. Yeah, but an extremely light VM layer on top of the, on top
of the metal. So it's all scheduled and managed through that. So our, our Kubernetes operator is
very advanced. And that's another part of our kind of special sauce that you get when you use
our product.
01:00:42:10 - 01:00:45:11
Stefan
It's funny because I'm talking about you got to meet our CTO.
01:00:45:13 - 01:01:05:29
Sam
Yeah, it's really fun. It's really funny because, we did a survey and like 50% of the people
responding didn't believe you could run state on Kubernetes. And we're over here with
petabytes of state. And is this complete? It's very possible. It's hard. It's not easy to do. But you
get these all these benefits. So yeah, we use Kubernetes and, and our Kubernetes, right.
01:01:06:01 - 01:01:10:19
Sam
We're very cloud native, very, very much in the Cncf ecosystem. There.