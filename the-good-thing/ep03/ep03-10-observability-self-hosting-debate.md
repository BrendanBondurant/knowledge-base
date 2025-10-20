---
type: podcast-chunk
title: Observability and Self-Hosting Debate
slug: ep03-10-observability-self-hosting-debate
series: The Good Thing
episode: 3
chunk: 10
segment: Debate about self-hosting observability and the importance of managed services
timecode: 00:42:32 - 00:47:39
start_time: 00:42:32
end_time: 00:47:39
speakers:
  - Stefan
  - Dustin
topics:
  - Observability
  - Self-Hosting
  - Managed Services
  - Datadog
  - Business vs Technical
tags:
  - observability
  - datadog
  - ai
  - cosmo-router
  - founder
  - go
  - rest
  - startup
  - telemetry
  - typescript
entities:
  - Stefan
  - Dustin
  - Datadog
  - New Relic
  - AWS
summary: Stefan and Dustin debate the merits of self-hosting observability versus
  using managed services like Datadog. They discuss the paradox of self-hosting observability
  when infrastructure goes down and the importance of focusing on business value rather
  than technical coolness.
---

00:42:32:14 - 00:42:41:26
Dustin
Yeah. But also nothing prevents no, nothing. Also, data could go down right then you also are
blind so

00:42:41:29 - 00:42:48:23
Stefan
Yeah, but data going down is like AWS going down. That's a lot of a lot of money on the stock
market. That'll be really upset.

00:42:48:26 - 00:43:11:07
Dustin
That's right. I would also say that, the probability that datadog goes down is, is less than your
own infrastructure. I think at the end it's always a question of, of, of money and, how much you
can spend on such a service and again as again, what I already said on the, on the cloud part,
on the cloud architecture, on the, on the design principles.

00:43:11:10 - 00:43:32:14
Dustin
Mind your own business. And buy buy the service, unless you have very good reason to ship
your own stuff like, if. Yeah, if you're if a data the business is a couple of millions. Maybe it's
time to to move on and, optimize your stack and, yeah.

00:43:32:16 - 00:43:52:19
Stefan
The thing is, the problem I have with that is you don't know you're different because you're a
startup founder. But as an engineer, then, like, somebody actually told me this is that, they work
at, like one of the largest retail companies in the world. And, one of the engineers said, we are
not a tech company.

00:43:52:19 - 00:44:12:00
Stefan
We are a fashion company. And the issue with that is that, engineers like to build cool stuff.
They like telemetry pipelines. They like trying to self-host stuff. They would be super interested
in, you know, setting up, bare metal servers and the racks and everything. And you want to work
at a company where you get to do that type of stuff.

00:44:12:00 - 00:44:29:04
Stefan
And so the issue is engineers want to build cool stuff. They don't really care for the business.
Like, I have a couple friends that work at, like Pinterest, or they work at Walmart and they don't
actually care about Walmart, but they care about the tech, the stuff that goes into power that
they build cool stuff, and it's really cool.

00:44:29:04 - 00:44:51:21
Stefan
And same thing with Pinterest. Like they don't even have a Pinterest, but they the stuff that
takes to power Pinterest is interesting for them. What do you think on that? Like it took you a
little bit of time. We've seen it with all technical folks on the team that they went from a pure
engineer mindset to a business mindset like, let's get the job done because the customer
matters not, hey, this is the coolest solution.

00:44:51:21 - 00:44:58:03
Stefan
Let's build this because it's super cool. And then the customer comes second.

00:44:58:06 - 00:45:01:18
Dustin
Great question.

00:45:01:20 - 00:45:02:24
Stefan
I know it's tough because.

00:45:02:24 - 00:45:26:09
Dustin
Like, I mean, as an engineer, you always you love to experiment. You love to innovate, but you
also need to yeah, you need to compare with the reality. Like how if you if you build this, if you're
building a business, I think there are a lot more things you need. You have to worry about than,
than the about your foundation.

00:45:26:09 - 00:45:48:24
Dustin
So you need to build, you need to you need to build the right foundation. But nothing prevents
you from experimenting and innovating. So, I think you can you can still you can still do great
stuff and you can still bring in doing interesting stuff. For example at wundergraph. But, yeah.

00:45:48:27 - 00:46:12:00
Stefan
You need both. I think you need, like, I think this is a great career advice. Like, if you're early in
your career or you're a senior engineer or principal engineer at that point, you're not hired
because you like cool tech and you can build cool POCs. You're hired to make direct business
impact. And if you put on your business hat and think, okay, I'm going to build something, but
how is it going to generate more business?

00:46:12:00 - 00:46:31:18
Stefan
You can rise up the ranks pretty quickly. And for example, I have a friend, he works, I think it's
meta or it's Microsoft. He's a like, distinguished principal engineer. He makes like over two, 3
million a year, like he makes crazy money as an engineer. And people are always blown away
like, oh my God, this engineer, like, he makes 2 or $3 million a year.

00:46:31:18 - 00:46:55:27
Stefan
And it's like, you don't understand that the initiatives that he leads, they're not fun, they're not
cool tech, they're not crazy. They're very boring, but they drive significant revenue to the
company. And when he fixes a problem, it's a problem that's costing them millions of dollars.
And he does it only in a way that it brings impact. And so but Dustin I agree with you, 90%
needs to go towards business impact.

00:46:55:27 - 00:47:13:16
Stefan
But if you just focus on the business, some of the best stuff is just made by experimenting. You
know, like we tried out the AWS Lambda router, we experimented with all sorts of stuff at wunder
graph, and it actually led to some stuff that's actually used by our customers today. Yeah.

00:47:13:18 - 00:47:15:10
Stefan
Yeah. It is an interesting thing.

00:47:15:12 - 00:47:39:16
Dustin
It's it's always a matter of calculating risk and benefits. Like if there is a benefit of of of going this
approach huge, then we can think about to, to invest in it. But I don't want to write my own
JavaScript framework just for the sake of, of having fun and use it in my application, like, yeah. 