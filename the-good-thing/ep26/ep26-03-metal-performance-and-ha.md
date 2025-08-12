---
title: Metal Performance and High Availability
slug: ep26-03-metal-performance-and-ha
series: The Good Thing
episode: 26
chunk: 3
participants:
  - Stefan
  - Jens
  - Sam Lambert
segment: PlanetScale Metal Architecture and Performance
timecode: 00:10:15:23 – 00:15:33:21
start_time: 00:10:15:23
end_time: 00:15:33:21
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - PlanetScale Metal performance advantages
  - Bare metal vs cloud storage architecture
  - High availability without disaggregation
  - NVMe drives and local storage benefits
  - Ephemeral machines and replication strategy
  - Semi-synchronous replication
tags:
entities:
  - PlanetScale
  - AWS
  - Google Cloud
  - Aurora
  - NVMe
mentions:
  - Local NVMe drives inside servers
  - Ephemeral machines in AWS and GCP
  - Network layer latency elimination
  - Three node HA configuration
  - Semi-synchronous replication
  - Proxy buffering during failover
summary: |
  Deep dive into PlanetScale Metal's performance advantages through bare metal infrastructure, local NVMe storage, and their approach to high availability without the latency penalties of disaggregated storage and compute architectures.
---

00:10:15:23 - 00:10:36:03
Sam
A little while after joining. Yeah, we became very successful. I mean, the we went from having
just a tiny, user base to now just a very, very large user base in some of, the largest relational
databases in the world running on the platform, as well as a ton of very large scale kind of
consumer platforms that run on top of us.
00:10:36:03 - 00:10:50:07
Sam
It was really fun to know that, you know, pretty much every working adult in America or, you
know, in the tech industry will interact with products built on top of that scale every single day,
which is really cool, No well said.
00:10:50:12 - 00:10:56:24
Stefan
Jens over to you now on the tech questions. Now we got, we got the background out.
00:10:56:26 - 00:11:25:17
Jens
Okay. Well, one thing I'm interested in and, I'm not a database expert, but a user, but I, I read
about planet scale metal. Yeah. And it's it's very interesting. The graphs you're showing, the
performance and everything, like, in very simple terms, why is planet scale metal so much more
performant than other database solutions?
00:11:25:19 - 00:11:47:29
Sam
So the reason it's more performant is a very simple one. And it's the same thing anyone could
achieve on a local server, you know, a server that they rack themselves is that it just uses, the
NVMe drives that are inside the server, which sounds like when you say it like that, it sounds
silly and, unimpressive. Like obviously you should use the disk inside your server, but in the
cloud that doesn't happen.
00:11:48:01 - 00:12:10:09
Sam
The main reason is really impressive that we do it. The way we do it is because we, we, we're
running those bare metal inside AWS and inside Google by using the machines that they use to
build their services on top of. And and these machines are ephemeral, so the the disks don't
stick around. If you're racking your own servers in a data center, you have rate arrays inside
those servers, and you can go and access them if you really needed to to get access to the
data.
00:12:10:09 - 00:12:32:27
Sam
We can if we provision a server, it's gone forever. If it fails, it's gone forever. So we handle all of
this state, running on ephemeral machines that happen to be extremely fast and much cheaper
than the other hosts that you get inside Amazon. And it means that we get this huge
performance increase, like, you know, Aurora and some of the other databases, they they just
aggregate storage and compute.
00:12:32:27 - 00:12:49:13
Sam
They separate those things, which means they put a network layer, in some form between the
the server process and the disks, which adds a significant amount of latency, to each query. We
don't do that and it makes it a lot faster.
00:12:49:15 - 00:13:12:17
Jens
So if I have, planet scale metal database, it it runs on a computer. The computer has a local
drive that makes it super fast. But what if the computer or the drive fails like my database? Is it
then down, or do you have some sort of like H.A. or. Yeah.
00:13:12:19 - 00:13:32:10
Sam
There is no non ha configuration for this. It's all highly available. By default. You get given three
nodes when you spin up. So you have two replicas in the in the instance that you would if you
say lost a primary node, we very, very quickly detect that failure. We throw that node out we
promote the node that's furthest ahead.
00:13:32:10 - 00:13:58:18
Sam
We have say semi synchronous replication, which means that by the time you write, we know
that the write has left to another machine. We then promote whichever of those machines put
the replicas underneath and then add a replacement node for that, for that primary. And that's all
done very, very quickly. In the time of failure, a proxy will buffer and hold off the queries and wait
for that to happen, and then send them through to the database when it's done.
00:13:58:18 - 00:14:08:25
Sam
So we basically, we handle all of that for you to give you high availability without the kind of
trade offs of disaggregating storage and compute.
00:14:08:28 - 00:14:43:25
Jens
Okay. And then do you, do you have to deal with, with problems like you make a write on like a
master chair and then you, you get you get it back, it's working fine. And then you make a read
request and it wasn't replicated or something or like, you know, there's like different guarantees
you can get from a database or like, is that like, does it behave like a singular Postgres or
MySQL or other differences and guarantees?
00:14:43:25 - 00:14:45:14
Jens
I can go from such a setup.
00:14:45:17 - 00:15:16:19
Sam
Nope. It it does. It works like the storage engine below. It's supposed to work with replication.
That's a core principles. We don't fake out the storage system like, you know, there's other
scaling solutions for these products that basically re-implement a different storage solution
under the hood to allow stronger consistency with significant trade offs there. But, yeah, you if
you read, write to a master and you require the the row on the replica for the same request, if
there's replication delay, it may not be there.
00:15:16:22 - 00:15:33:21
Sam
That's fine. And kind of normal. And that's an edge case to, to deal with any of these types of
systems. It's more like to, to do that kind of guarantee, you then pay a different penalty, which is
a penalty that we don't pay because it doesn't really scale. That's not really what our users are
looking for.