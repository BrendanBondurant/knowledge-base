---
title: ClickHouse Self-Hosting Discussion
slug: ep03-08-clickhouse-self-hosting-discussion
series: The Good Thing
episode: 3
chunk: 08
participants:
- Stefan
- Dustin
segment: Discussion about ClickHouse requirements and self-hosting considerations
timecode: 00:32:26:15 - 00:37:00:14
start_time: 00:32:26:15
end_time: 00:37:00:14
speakers:
- Stefan
- Dustin
topics:
- ClickHouse
- Self-Hosting
- Managed Services
- Infrastructure
tags:
- clickhouse
- self-hosting
- managed-services
- infrastructure
- cosmo
topic_tags:
- clickhouse
- self-hosting
- managed-services
- infrastructure
- cosmo
entities:
- Stefan
- Dustin
- Cosmo
- ClickHouse
- PostgreSQL
- GCP
mentions:
- ClickHouse
- PostgreSQL
- managed services
- self-hosting
- analytics
- schema registry
summary: Stefan and Dustin discuss the common question about whether ClickHouse is
  required for self-hosting Cosmo. They explain that while technically possible with
  PostgreSQL, ClickHouse is needed for analytics workloads and they prefer using managed
  services rather than being experts in everything except their own product.
---

00:32:26:15 - 00:32:45:14
Stefan
No, it's super interesting. And people are always saying this in discord. They're asking, hey, like,
I want to spin up, Cosmo. I want to self-host it, but I don't have any clickhouse experience. Do I
need to click House? And we always tell them, yes. It's like the central source of truth. You need
to clickhouse and like.

00:32:45:17 - 00:32:51:15
Stefan
Any thoughts on that dustin? It's it's a funny question we get all the time.

00:32:51:18 - 00:33:17:00
Dustin
I would say it's still a good question. There might be users out there that that don't need that
scalability that clickhouse can provide. And there would might be sufficient with Postgres, but
that wouldn't that would require a lot of. Yeah, implementation on all sides to also support
different databases and yeah, on our current router

00:33:17:00 - 00:33:42:25
Dustin
That's not, that's not worth it. But yeah, overall you need some database. That that is, is suitable
for analytics, workloads to process. The opentelemetry data that is emitted by the router and
also the schema usage data. If you don't want analytics and only you want to use a schema
registry, that's.

00:33:42:27 - 00:33:46:14
Dustin
Yeah. I'm not sure. Who's doing that?

00:33:46:16 - 00:34:07:10
Stefan
Technically, it's possible. It doesn't make sense for us because we are ingesting large scale
data. So for us, that's the reason why we built that. We built it with scale in mind. I mean, it
makes sense. I mean, yeah, like, maybe someday in the future, there's like a Cosmo light where
it's like a smaller version of Cosmo with just a schema registry in the router and like a Postgres
database.

00:34:07:10 - 00:34:27:09
Stefan
But for now, there isn't. And so to answer the question, like, yeah, if you're going to self-hosted
Cosmo, you will need to use clickhouse. But I like what Dustin said. Like when you're building a
platform that uses other people's technologies or other technologies, frameworks, concepts, it's
better not to be an expert in them. Like we're not authentication experts.

00:34:27:09 - 00:34:40:16
Stefan
We use key cloak and then we use cloud IAM, which is a managed service of Google because
you know, you don't want to be an expert. We don't want to roll our own auth. What we want to
do is provide the most value we can for our customers. And the same thing with clickhouse we
use manage clickhouse, right?

00:34:40:16 - 00:34:50:27
Stefan
We don't tell folks like us exactly. Everything is just kind of manage, right? We use GCP, their
Kubernetes offering. Do we self host anything?

00:34:51:00 - 00:35:24:03
Dustin
Except from our company, our own components we have developed no know at least we, we
you know, we try our best not to doing it. It's also, for example, valid for, our Kubernetes cluster,
we use GCP, autopilot. So we don't have to worry about autoscaling. We use GCP as a
complete observability platform for, to ensure uptime, to, to implement proper, alerting and,
yeah, analytics.

00:35:24:05 - 00:35:34:22
Stefan
Yeah. And why did we decide or why did you decide to go with GCP over AWS? When we first
started out with Cosmo?

00:35:34:24 - 00:36:13:12
Dustin
That's a good question. I, I had, experience with GCP already. I knew, about the autopilot,
offering and, I did a quick POC and GCP and the whole the whole user experience was much
better than on AWS. And, yeah, yeah, I think your point. Yeah, you could have built the same on,
on on, AWS or on Azure, but, none of these providers as far I as far I remember, do not offer, a
similar service to, to autopilot.

00:36:13:15 - 00:36:36:21
Dustin
You can, you can, you can implement it. For example, AWS has karpenter, which is like a,
Kubernetes controller that does auto scaling for you. But yeah, again, I don't want to
experiment. I just want to buy something and solve the problem. So throw throw money, throw
money at it and.

00:36:36:24 - 00:37:00:14
Stefan
Yeah, I mean, that's what you're supposed to do with VC funding. I mean, no jokes aside, I think
this is what like. This is what I struggle with a lot. So I have a lot of good technical folks like
friends. And this is the first mistake we made. Wunder graph is we built a super technically
super cool product, like with firecracker, the CI CD pipeline that we set up the GitHub actions. 