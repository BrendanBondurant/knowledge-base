---
type: podcast-chunk
title: Fly.io Mistake and Reliability Lessons
slug: ep03-05-fly-io-mistake-reliability
series: The Good Thing
episode: 3
chunk: 5
segment: Discussion of the Fly.io mistake and lessons about reliability in cloud infrastructure
timecode: 00:16:34 - 00:21:40
start_time: 00:16:34
end_time: 00:21:40
speakers:
  - Stefan
  - Dustin
topics:
  - Fly.io
  - Cloud Infrastructure
  - Reliability
  - Startup Lessons
  - AWS
tags:
  - startup
  - ai
  - api-design
  - founder
  - go
entities:
  - Stefan
  - Dustin
  - Fly.io
  - AWS
  - Vercel
  - Tercer
  - WunderGraph Cloud
summary: Stefan and Dustin discuss their mistake of choosing Fly.io for WunderGraph
  Cloud, sharing lessons about reliability in cloud infrastructure. They explain why
  they moved away from Fly.io due to support and API stability issues, and discuss
  the broader cloud market dynamics including AWS dominance and the challenges of
  competing with established providers.
---

00:16:34:08 - 00:16:58:00
Stefan
I agree. So I think it's a good transition to kind of like let's get a little bit into the tech. So I want
to talk about a mistake that we made. Pretty early in our journey at Startup Founders. So for
those of you that don't remember, we had Wunder Graph SDK and we decided to create
Wonder Graph Cloud, which were you could think of is Wunder graph was this great framework
for building applications.

00:16:58:02 - 00:17:19:24
Stefan
And we built a cloud on top of that. And one of the key decisions I remember this, where we
were sitting in the room, we said we're going to use fly.io. They're a startup, but we're going to
bet on them. We're not going to do AWS. They have this great firecracker. You can you can talk
a little bit more on that part, but and if you guys saw the news, Tercer is also migrating.

00:17:19:24 - 00:17:40:27
Stefan
Our Tercer is migrating also away from fly io. A lot of people are leaving fly io. But walk me
through, like, kind of like that decision that we made to use fly io and like what we experienced
and then like kind of like as a CTO, like how that affected us, why we moved away and just kind
of like how reliability is, is king in a cloud hosting company, if you will.

00:17:41:00 - 00:17:45:08
Stefan
You know, we'll just talk a little bit about like what with fly.io, what happened with fly.IO?

00:17:45:10 - 00:18:19:05
Dustin
Yeah, I think that's, that's, I would say a funny and a sad story. So if you're building a startup,
you want to be fast, you want to prototype very quickly. You want to figure out if this is a fit. And,
everything that that yeah, that can support you. You will probably also utilize. And for us, fly was
a great candidate of deploying custom, custom, custom CI custom containers worldwide.

00:18:19:07 - 00:18:23:22
Dustin
With little cost. with little steps. Oh.

00:18:23:23 - 00:18:24:26
Stefan
So easy.

00:18:24:28 - 00:18:51:26
Dustin
Yeah. He's the provider I they provide a great API to, I would say an easy, an easy enough API
to, that was worth to explore. And, yeah. And, but the more and more, traction you get, from,
from your product and people beginning to, to rely on you, you also need to be reliable as a
service.

00:18:51:26 - 00:19:18:13
Dustin
And, and then, we figured out that, the yeah, the service that fly provides in terms of support,
even paid support or, API stability. Yeah. They couldn't provide, the right guarantees to us. And
after several incidents, we had to make a cut and, yeah.

00:19:18:16 - 00:19:43:08
Stefan
It's difficult because what fly is building is amazing. Like, if it works like to provide that service as
APIs, though so easy to spin up a container. The firecracker VMs were really cool and they were
really fast. But the reliability part is hard. People don't understand and this actual industry
scares me. So the cloud like just to give you like an understanding of how big the cloud market
is.

00:19:43:08 - 00:20:06:18
Stefan
So, Vercel did 100 million in ARR AWS did like what was it like 100 billion or like some ridiculous
number? And then you have Azure doing like 60 billion ARR. Like they're just doing that in ARR.
So you can imagine how big is the cloud market. And I was talking about this with Dax actually
this week.

00:20:06:20 - 00:20:30:18
Stefan
Any company that builds like on top of the cloud. So meaning like Vercel, you know, they
provide a great front end experience. But it's built on AWS. Eventually they have to become the
same price as AWS because any consumer like us, like you'll get to a point where you're paying
so much just for the experience and you're like, why is there such a margin on top of a cloud?

00:20:30:18 - 00:20:43:00
Stefan
You know what I mean? So like eventually that provider will have to bring their price down to be
equal as AWS, and then they have to provide value on top of that. I don't know, just something
we were talking about. Do you have any thoughts on that?

00:20:43:03 - 00:21:08:28
Dustin
No, I think I think that's right. And the reason why, AWS, is, is the most popular and the first, first
candidate in choosing reliable, reliable infrastructure and. Yeah, as, as I said, like, as a startup.
And you don't you don't have any customers. You have to count any cents. It's you can rely on
fly until you have proven.

00:21:08:28 - 00:21:40:10
Dustin
Proven your point. Your product. But as soon as you get serious, you want to have uptime, you
want to have guarantees. And, I would never choose a fly or any other provider again if I if if my
goal is to to build a reliable foundation for my, for my company. So then I would, I would rather
spend a little bit more money than trying to trying out new things that are unproven. 