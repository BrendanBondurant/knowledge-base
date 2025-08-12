---
title: Cosmo's Boring Tech Architecture
slug: ep03-06-cosmo-boring-tech-architecture
series: The Good Thing
episode: 3
chunk: 6
participants:
  - Stefan
  - Dustin
segment: Discussion of Cosmo's boring tech architecture and infrastructure choices
timecode: 00:21:40:13 - 00:26:46:23
start_time: 00:21:40:13
end_time: 00:26:46:23
speakers:
  - Stefan
  - Dustin
topics:
  - Cosmo
  - Architecture
  - GCP
  - Kubernetes
  - Boring Tech
tags:
  - cosmo
  - kubernetes
topic_tags:
  - cosmo
  - kubernetes
entities:
  - Stefan
  - Dustin
  - Cosmo
  - GCP
  - AWS
  - ClickHouse
  - Keycloak
  - Cloudflare
mentions:
  - GCP
  - Kubernetes
  - ClickHouse
  - Keycloak
  - Cloudflare Workers
  - managed services
summary: Dustin explains Cosmo's boring tech architecture using GCP, Kubernetes, managed
  ClickHouse, and Cloudflare Workers. They discuss the philosophy of using managed
  services and not being experts in everything except their own product, contrasting
  with their previous Fly.io experience.
---

00:21:40:13 - 00:22:00:20
Stefan
And so with that learning, so we, we, we chose fly for wundergraph cloud. And then when we
started building Cosmo, we pivoted all going and all in on Federation, we built an extremely
reliable piece of software. So what were some of the decisions that you chose? Like what do we
host on what. And we it's boring tech.

00:22:00:20 - 00:22:11:09
Stefan
It's extremely boring. It's not like exciting like fly with firecracker VMs and all this stuff. We chose
boring tech this time. So what do we choose for Cosmo? And like, why do we make those
decisions?

00:22:11:11 - 00:22:31:29
Dustin
Yeah, I think all comes back to the to to to our learnings from wundergraph cloud. We no longer
rely on fancy tech. So right now we use GCP. There are Kubernetes is offering to, to run our
platform, or to run our reference architecture. You also find on Cosmo docs.

00:22:32:02 - 00:22:37:13
Stefan
And yeah, you can actually bring it up when you bring a

00:22:37:15 - 00:23:06:04
Dustin
What else. We also rely on cloud for workers to, to distribute our, routing configs, which, which
are super reliable. Yeah. I think 1 or 1 of the core values of our architecture, but also in general
for smaller startups is mind your own business. So we never try to be an expert in, in any
technology here except our own product.

00:23:06:07 - 00:23:30:08
Dustin
So for clickhouse for example, we rely on click clickhouse cloud. You don't want to run
clickhouse clusters, at least not at this. At this point, we, we use, managed databases as is,
where we can and this also includes, for example, for key cloak, which you see in in the middle,
which is our identity provider.

00:23:30:15 - 00:23:46:12
Dustin
For authentication and federated auth, we also use cloud IAM, which is a managed solution for
for keycloak. And yeah, front end is running on the next.js. So yeah.

00:23:46:15 - 00:24:08:19
Stefan
Yeah, it's very simple, very boring. But I think you have to go through what we did with, like,
relying on a provider. And then imagine telling your customers like, yeah, our service is down,
but there's absolutely nothing we can do about it because our provider is down. And so we
made decisions to go boring with Cosmo. And I think that's like, that's the thing you're paying for
with AWS or GCP.

00:24:08:19 - 00:24:29:09
Stefan
You're not paying for an amazing experience, which is why there's so many companies that
build on top of AWS to make it better. But two things on that is one, when you look at AWS and
you look at how clunky everything is, there's a reason they made those decisions. They've
thought about it extensively, and there's a reason why some things are clunky and it's because
of reliability.

00:24:29:09 - 00:25:02:10
Stefan
They made those decisions because they want to make sure that the platform is reliable, and
it's kind of slow on purpose and which you have companies build on top of that to make it better,
make AWS not a pain. And then the second one is it's such an interesting space because it if
you think about it, I just going to unshare if you think about it, if a company were to come in and
make AWS ten times better, but they also provided the reliability, like, like what I'm trying to say
is like, do you ever think somebody could overtake AWS?

00:25:02:10 - 00:25:20:02
Stefan
Like, I'm like a big guy for like, like David versus Goliath stories like, I like, for example, Deep
Seek can OpenAI. OpenAI is a giant and then Deep Seek destroyed them for a little bit. We
don't know what'll happen in the future, but do you think somebody could ever do that to AWS?

00:25:20:04 - 00:25:30:17
Dustin
I would say for sure. But, even let's say someone is doing that, it needs to be proven. It needs to
be proven for years. And,

00:25:30:19 - 00:25:40:05
Stefan
But how do you do that, like AWS? Like, has the reliability, AWS has the logos and AWS is the
cheapest. Like how do you compete against that?

00:25:40:07 - 00:25:59:03
Dustin
I wouldn't say its the cheapest, but I think there's there's definitely room for competitors on the
market, but yeah, it's tough. It's. Yeah I.

00:25:59:05 - 00:26:17:24
Stefan
I'm telling you, you can't like I'm huge on David versus Goliath stories, but and I hopefully I'm
wrong in my lifetime. But I don't think you can compete against AWS, even me. And Jens say
this all the time, like AWS wins every single time simply because it's AWS. It's too big to fail.

00:26:17:27 - 00:26:44:19
Dustin
Yeah, I think you can build a optimized solution to pull some percentage from the market. But,
when it comes to really reliability infrastructure, and there were and they were the, they become
better and better. It's no longer that shitty UI. It's, I think the last time I checked AWS, it's. Yeah,
it is no longer that bad as it was before.

00:26:44:19 - 00:26:46:23
Dustin
And, 