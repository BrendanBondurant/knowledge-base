---
title: Startup Credits and Business Focus
slug: ep03-09-startup-credits-business-focus
series: The Good Thing
episode: 3
chunk: 09
participants:
  - Stefan
  - Dustin
segment: Discussion of startup credits and the importance of business focus over technical
  coolness
timecode: 00:37:00:14 - 00:42:32:14
start_time: 00:37:00:14
end_time: 00:42:32:14
speakers:
  - Stefan
  - Dustin
topics:
  - Startup Credits
  - Business Focus
  - Technical vs Business
  - Customer Value
tags:
  - startup
topic_tags:
  - startup-credits
  - business-focus
  - customer-value
  - technical-vs-business
  - vc-funding
entities:
  - Stefan
  - Dustin
  - GCP
  - AWS
  - Railway
  - WunderGraph
mentions:
  - startup credits
  - GCP
  - AWS
  - business focus
  - customer value
  - technical coolness
summary: Dustin mentions GCP startup credits as a motivation for choosing GCP. Stefan
  shares tips about using cloud provider competition to get more credits and discusses
  the importance of focusing on business value and customer problems rather than building
  technically cool solutions.
---

00:37:00:14 - 00:37:19:25
Stefan
We use so much cool tech. It was bleeding edge. It was amazing. But it didn't solve a problem.
It didn't solve the problem pain enough. And then when we pivoted into Cosmo, we started
realizing that the tech is secondary. You want to choose boring, reliable tech that gets the job
done, but you want to focus on solving the problem for the customer, right?

00:37:19:29 - 00:37:38:28
Stefan
Exactly. Yeah. Dustin, you did a quick POC, you tried AWS, you tried GCP. You saw that the
developer experience allowed you to ship faster. It had the autoscaling feature. You thought of
our customer and boom, that's why we implement it. There's no weird like oh like this. It's it's a
better technology. It's now I got the job done and we need to focus on our customers.

00:37:38:28 - 00:37:43:21
Stefan
I like that, so yeah. Don't don't like freaking out.

00:37:43:24 - 00:37:52:03
Dustin
Don't forget, big, big motivation was, Google GCP startup credits.

00:37:52:06 - 00:38:12:19
Stefan
Yeah, I actually forgot about that. So, like, if you're a startup, clouds will give you crazy
discounts. They'll give you like 100,000 in like, credits and, let me actually give you guys a very
good tip, okay? If you're building on any cloud platform, get the credits as soon as the credits
are over, tell them that another competitor is giving you double the credits.

00:38:12:25 - 00:38:32:24
Stefan
If you migrate over and tell them you're going to migrate over, you don't have to actually migrate
over, but they'll come back and they'll give you 50,000 credits or 60,000 credits as long as
you're small enough. Always use the other cloud provider as leverage to get more credits. I it's
somebody told me this, the guy from railway actually he said to use this.

00:38:32:24 - 00:38:50:06
Stefan
And so now every time you know like they come up to us and they're like, hey, like, you guys are
running low on credits or like, yeah, we're looking at jumping to AWS. They're like, wait, no, no,
no, here's 40,000 credits. Please stay. We're like, okay, we'll take it. I think that's kind of like a
funny little hack.

00:38:50:06 - 00:39:09:27
Stefan
It also is like startup mentality. Like, always make sure that you're getting the cheapest, you
know, tools, but that get the job done. And Dustin my next question I want to ask you is, we've
built a lot of cool features into Wunder Graph Cosmo, what was a feature that you were really
proud about or like, really enjoyed building, but also made a big impact with our customers.

00:39:09:27 - 00:39:13:29
Stefan
Like our your favorite feature to Cosmo?

00:39:14:02 - 00:39:18:12
Dustin
My favorite feature?

00:39:18:15 - 00:39:29:09
Stefan
I know there's so many. There's advanced request tracing. There's, I mean, just basically the
analytics view, there's the router, there's studio.

00:39:29:12 - 00:39:54:11
Dustin
I think the most I would say the, the complete, open telemetry integration. So from the router
into Cosmo, setting up the auto collectors, properly setting up click house, steam. I think that
was very interesting. And, it's. Yeah. And it's still not, not done yet. It's, yeah, it's still there's still
a lot of things to do.

00:39:54:13 - 00:39:54:28
Dustin
Okay.

00:39:55:00 - 00:40:18:16
Stefan
And walk me through that. So like, I understand to an extent of like open telemetry, but basically,
a year ago, I mean, our major competitor, they didn't allow you to kind of like, send Otel data to
your own, like Datadog or wherever you wanted to monitor it without an enterprise plan. And we
built that fully into the solution.

00:40:18:16 - 00:40:30:01
Stefan
And so what does that mean? Like otel telemetry that you can export it to Prometheus, to
Datadog, like, kind of explain it to me. And for maybe some of the non-technical folks.

00:40:30:03 - 00:41:10:19
Dustin
Yeah. Opentelemetry is a standard how to collect metrics. Trace suspends events. And they
also now support logs. It is just like a convenient, unified approach to, to instrument your
application. Yeah. For for observability needs and yeah. So before you usually use, custom
integration like Datadog, New Relic, which auto instrumented application through some some
non standardized API you were able to create custom metrics.

00:41:10:22 - 00:41:29:08
Dustin
And now you can just, use an ultra compatible SDK and push the data to a, compatible, auto
collector. And from that point on, you can distribute, or share the data, across multiple platforms.

00:41:29:11 - 00:41:51:28
Stefan
Yeah. And also the interesting is so it's observability, like if you talk to any big company, the first
thing that they'll tell you is, are AWS bills crazy And then they'll say, our data dog bill is crazy.
And so the reason why it's so expensive is like when you're such a big company is observability
is key. Like imagine like having like what would you not do if you didn't have any analytics or
data of like, your platform?

00:41:52:00 - 00:42:17:15
Stefan
And one of the things there's a company that's doing, an open source alternative to Datadog
and their key selling point is that you can self-host it and I always thought that was weird
because I don't think you should self-host observability, because if your infrastructure goes
down, how do you know what happened? If you're self-hosting, your observability?

00:42:17:18 - 00:42:32:12
Stefan
Right. Like like what do you do then. Oh, our infrastructure's down. I can go look at Datadog and
I can understand and look at the tracing, the spans. I can see what services went down. I can
understand it. But if I'm self-hosting, it, in my infrastructure then, like, how do I know what
happened? 