---
title: Infrastructure Reliability and Collaborative Value
slug: ep12-17-infra-reliability-and-value
series: The Good Thing
episode: 12
chunk: 17
participants:
  - Stefan
  - Jens
segment: Reliability and Business Value Discussion
timecode: 01:03:20:20 – 01:08:23:10
start_time: 01:03:20:20
end_time: 01:08:23:10
speakers:
  - Stefan
  - Jens
topics:
  - GCP Kubernetes Reliability
  - Zero Incidents
  - Collaborative Value
  - Federation as Collaboration
tags:
  - zero-incidents
  - ai
  - api-design
  - cosmo
  - federation
  - go
  - graphql
  - graphql-federation
  - kubernetes
  - startup
topic_tags:
  - zero-incidents
  - federation
  - cosmo
entities:
  - GCP
  - Kubernetes
  - Fly.io
  - AWS
  - Azure
  - Linear
  - Cosmo
  - Dustin
  - Stefan Avram
  - Jens Neuse
mentions:
  - Node.js control plane
  - automated cluster management
  - Friday afternoon outages
  - SLA response failures
  - margin compression over time
  - team onboarding value increases
summary: Jens shares WunderGraph's reliability success using GCP Kubernetes with zero
  incidents over years, contrasting with startup infrastructure failures. He advocates
  for collaboration-based business models over compute reselling, using Linear as
  an example of how collaborative tools become more valuable as teams grow, positioning
  Federation as a similar collaborative infrastructure tool.
---

01:03:20:20 - 01:03:23:03
Jens
Like, yeah.
01:03:23:05 - 01:03:24:13
Stefan
It was bad.
01:03:24:15 - 01:03:45:16
Jens
We tried, but like, we we wasted so much time trying fly. Like, just just don't use startups for
compute. It's, it's it's really hard to do to do compute. It's it's so hard. Okay. And real quick.
01:03:45:18 - 01:04:07:16
Stefan
real quick note on that one. These startups move slow or not startups, these companies AWS,
Azure, GCP. But there's a reason that they move so slow. When you're that big and you have
that much reliability, it would be ridiculous to choose anything else other than to go to one which
is Azure, GCP, and Azure. I like how you said maybe Azure.
01:04:07:16 - 01:04:08:09
Stefan
That was kind of funny.
01:04:08:09 - 01:04:41:01
Jens
You know what's crazy? So we have a Node.js component in Cosmo in our cloud. It's called
control plane. Node.js like it's not like Node.js. It's not it doesn't stand for stability or anything or
like best tech or whatever. It's just yeah, okay. Node.JS whatever. And we have this thing now
running for a couple of years, like of course we updat it and it's running on, on, on, Kubernetes
on GCP.
01:04:41:04 - 01:04:45:10
Jens
Do you know the number of incidents.
01:04:45:13 - 01:04:47:06
Stefan
A big fat zero.
01:04:47:08 - 01:04:48:10
Jens
Yes. Yes.
01:04:48:12 - 01:04:49:18
Stefan
Zero incidents. Yeah.
01:04:49:22 - 01:05:21:12
Jens
Like it's it's insanely boring to use Kubernetes on GCP. Insanely. Like we even paid extra money
for like Dustin, our CTO, he he figured out there's like, like a thing and it automates the cluster.
So we're not managing a cluster. And because like, who cares? And so it automatically does
stuff. And we never had an outage, an incident.
01:05:21:12 - 01:05:50:16
Jens
Nothing. It's I don't know, like I'm not I'm not like advocating for, for for GCP or so it's but I can
just say this this stuff just works. It's it's crazy if you want to build a startup and you don't want to
waste your time on on infra, whatever, just use GCP. I'm pretty sure AWS is the same same
game, but this stuff just works.
01:05:50:16 - 01:06:17:19
Jens
If you deploy something on fly, then suddenly on a Friday afternoon your deployment is gone
and you call a number or something because you have an SLA and nobody answers. And if
you're lucky in some forum on Monday, you get an answer and then you just know, okay, like,
let's let's run. I don't know how they how they managed to raise so much money, but yeah.
01:06:17:20 - 01:06:18:25
Jens
Okay. So.
01:06:18:26 - 01:06:20:21
Stefan
I see well said.
01:06:20:23 - 01:06:50:19
Jens
Yeah. So this is the category of we, we buy compute and we resell it more expensive. And to be
honest, I think it's, you know, it's a numbers game, but if given enough time, so given infinite
time, the margin for your for your reselling will go to zero. Yeah. So I don't know, your business
model is designed to fail.
01:06:50:22 - 01:07:08:17
Jens
I don't like it. What I like is collaboration. If you enable, 100 people to build an API together and
they build a workflow that really works for them, that's powerful. Then.
01:07:08:20 - 01:07:22:17
Jens
Imagine linear. So we are using linear. Our team is growing. Every time we add a new member
we onboard them to linear. So what is happening with the value of linear.
01:07:22:17 - 01:07:24:22
Stefan
For us it's going up.
01:07:24:25 - 01:07:57:28
Jens
It's going up. And so that means over time collaborative tools as you add more people become
more valuable. You put in your own tickets, you put in your documentation everything. Yeah.
And so Federation building APIs across teams, collaboration. So on the one hand side you
have, you have infra and you have like schema registry. And we do this for our customers.
01:07:58:00 - 01:08:23:10
Jens
And on the other side of the spectrum, you have, you have collaboration, and and yeah, where
people work together, build subgraphs and everything. We will talk more about this topic in the,
in the future. We, we first need to figure out some, some things. But we're, we're, we're very the
the kitchen is busy I would say yes.