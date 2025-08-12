---
title: Prisma Business Value Issues - Missing Metrics and Messaging Problems
slug: ep15-02-prisma-business-value-issues
series: The Good Thing
episode: 15
chunk: 2
participants:
  - Stefan
  - Jens
segment: Prisma Landing Page Critique
timecode: 00:05:03 – 00:10:19
start_time: 00:05:03
end_time: 00:10:19
speakers:
  - Stefan
  - Jens
topics:
  - Prisma landing page messaging flaws
  - Missing business value metrics
  - Lack of quantifiable improvements
  - Database ORM positioning issues
  - Technical vs business buyer disconnect
tags:
  - database
  - ai
  - api-design
  - benchmarking
  - cache-warming
  - go
  - observability
  - postgres
  - rest
  - rust
  - startup
  - telemetry
topic_tags:
  - database
entities:
  - Prisma
  - Sentry
mentions:
  - Missing KPIs like "40% less bugs"
  - No measurable improvement metrics
  - Over $100M revenue reference for Sentry
  - Developer-first vs business value messaging
  - Database query performance claims
summary: Stefan and Jens critique Prisma's landing page for lacking concrete business
  value metrics and quantifiable improvements. They note that unlike other tools,
  Prisma doesn't provide KPIs or measurable benefits, missing opportunities to show
  value like "40% fewer bugs" or performance improvements that would appeal to business
  decision makers.
---

00:05:03:27 - 00:05:21:09
Stefan
Yeah. We can roast it and and praise it though. So I do love the design. I love the 3D aspect of
it. It does have that playfulness. So thingamajig doohickey whatchamacallit call it, but then it
starts to break. So it gives you the four biggest use cases air monitoring session, gameplay,
code coverage and tracing. And then it starts to go into them.
00:05:21:09 - 00:05:31:18
Stefan
So now I think this is towards the business. Prioritize what matters. Try triage issues based on
impacted customers. That's pretty useful.
00:05:31:21 - 00:05:45:03
Jens
Does sentry have measurable improvements like does it somewhere say like some KPIs? Can
you can you search a bit for like improvements or something?
00:05:45:05 - 00:06:01:01
Stefan
So here's the improvement of critical issues. But like poor performing API calls or data base
query's is too small. Yeah, there's not one that says like right here. Sorry for the developers,
more custom,
00:06:01:04 - 00:06:06:25
Jens
Social proof, social proof, trust compliance updates.
00:06:06:26 - 00:06:08:09
Stefan
Yeah, you're right, it actually doesn’t.
00:06:08:09 - 00:06:20:12
Jens
something.
I think like what's missing is like 40% less bugs or faster improvements or, I don't know,
00:06:20:14 - 00:06:27:02
Stefan
What's crazy though, as they do over 100 million in revenue, I think they're very geared towards
the developer. First.
00:06:27:04 - 00:06:31:27
Jens
Yep. Let let's take a look at Prisma.
00:06:31:29 - 00:06:34:05
Stefan
Oh my god I'm going to roast. I'm going to roast.
00:06:34:08 - 00:06:37:12
Jens
My God.
00:06:37:15 - 00:06:44:28
Stefan
anymore.
I don't know, we should do Prisma because I don't think even I don't know what they do
00:06:45:00 - 00:06:47:08
Stefan
Okay. Once we get them.
00:06:47:10 - 00:06:49:02
Jens
That that's that's an Easter egg.
00:06:49:06 - 00:07:05:29
Stefan
Like okay. So okay. Oh, okay. I'm going to be completely honest with you. So Prisma when I use
it was an ORM. Now they're pivoting from idea to scale. Simplified. What does that even mean.
00:07:06:01 - 00:07:35:19
Jens
Ship production apps at lightning speed and scale to a global audience effortlessly with our next
gen serverless database. You know what? What I think what is the the problem. So from idea to
scale simplified, it means nothing. I don't know like I, I if I read it and I don't know what is the
product and then they say next gen serverless database, I think the hero should be next gen
serverless database.
00:07:35:21 - 00:07:41:03
Jens
But what this but this is the hero, right? The next gen serverless database.
00:07:41:05 - 00:08:02:28
Stefan
Yes. But I feel like they're trying to be like, super base here. They got the green going on now,
right? And it's what is super base from, build in a week ship to millions. Yeah, I don't know, but I
think you're right here. Like, also, if you look up here, Prisma, Postgres is now generally
available. So that's what they're trying to sell.
00:08:02:28 - 00:08:05:02
Stefan
Now this should absolutely be.
00:08:05:04 - 00:08:40:18
Jens
Yeah. The that's there's one problem I have with this whole hero. So for many conversations
and again like our landing page is also bad, but what I heard from many people is that the
landing page, it should have an action. So for example, the hero should say, I don't know, build
apps faster or something. And from idea to scale, simplified.
00:08:40:21 - 00:08:45:11
Jens
It's a bit hard for me to connect this to just the database.
00:08:45:13 - 00:09:03:21
Stefan
What's interesting here, though, is like the single call for action is getting started for free. I don't
know, for me, I'm not sold on that also right here. Like they just have logos going across. But
what I've heard before is like you need to see like what the logos are doing. So trusted by tells
you that they are customers.
00:09:03:23 - 00:09:13:13
Stefan
Used in production by okay, those are my customers or it's used or at least are using it in
production. When you have an empty wall like this, this doesn't tell me anything that's
interesting.
00:09:13:17 - 00:09:39:07
Jens
Okay, scroll a bit because there's good stuff actually. So one one thing I like is how they tell a
story as you scroll. I think this is a very good thing. So, we built something truly unique. First of
all, I think I would not make it about us, so not we I would make it about the user.
00:09:39:07 - 00:09:44:27
Jens
Like you can build something truly unique or. Yeah, yeah.
00:09:45:00 - 00:09:54:24
Stefan
Something unique. Oh, yeah. You're absolutely right. Yes. It's something they you with the
power of Prisma can build something unique. I also agree with you on that.
00:09:54:26 - 00:10:19:21
Jens
Okay, then get a database in an instant. That is. That's good, I understand it. Redefine how your
database works okay. That's about the ORM. We know it and then. But but you know what's
important. Those is a go go back go back. So redefine how your database works on the left
side. They they show me the ORM. Then they have a little label caching.