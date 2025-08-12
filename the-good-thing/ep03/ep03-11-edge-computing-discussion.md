---
title: Edge Computing Discussion
slug: ep03-11-edge-computing-discussion
series: The Good Thing
episode: 3
chunk: 11
participants:
  - Stefan
  - Dustin
segment: Discussion about edge computing, its use cases, and relevance
timecode: 00:47:39:18 - 00:53:01:17
start_time: 00:47:39:18
end_time: 00:53:01:17
speakers:
  - Stefan
  - Dustin
topics:
  - Edge Computing
  - Latency
  - Performance
  - Use Cases
  - E-commerce
tags:
  - cdn
  - rust
topic_tags:
  - cdn
  - rust
entities:
  - Stefan
  - Dustin
  - Vercel
  - Cloudflare
  - Fastly
  - SQLite
mentions:
  - edge computing
  - latency
  - performance
  - e-commerce
  - streaming
  - SQLite in Rust
summary: Stefan and Dustin discuss edge computing, its benefits for latency and performance,
  and specific use cases like e-commerce where performance directly impacts revenue.
  They also touch on the SQLite rewrite in Rust and the evolution of edge computing
  platforms.
---

00:47:39:18 - 00:47:42:14
Dustin
Go. Yeah.

00:47:42:17 - 00:47:59:01
Stefan
I'd agree. You know what I struggle with? And like, I, I don't think people understand this is that
the biggest thing is not that you can't do it, it's just that you don't even know what you don't
know. Like, oh, I want to build my own content management system. And it's like, people have
been doing this for a while.

00:47:59:01 - 00:48:19:18
Stefan
They made strict decisions because of their learnings. Same thing with building our router or a
GraphQL federation platform like, there's reasons we made these choices because of some of
the mistakes that we made early on. And it's like when you try to build something or self-hosted
something like you don't actually know what you don't know before you even start building
because you haven't been so deep into it.

00:48:19:20 - 00:48:31:17
Dustin
I mean, you can write your own interpretation database. I think you you will learn a lot, but I
don't want to care about the fundamentals when I when I have to build something complex.

00:48:31:19 - 00:48:35:04
Stefan
Yeah, but when do you care about the fundamentals?

00:48:35:06 - 00:48:36:07
Dustin
When?

00:48:36:09 - 00:48:36:18
Stefan
Yeah.

00:48:36:18 - 00:49:01:26
Dustin
When when my, when I mean, I would say every time there must be I think there must be a
good reason why you have to change fundamentals. For example, something doesn't exist yet.
It would enable your use case. You you, Yeah.

00:49:01:28 - 00:49:03:12
Stefan
Like, if it doesn't exist.

00:49:03:15 - 00:49:17:09
Dustin
Yeah, exactly. It doesn't exist. It would be a big differentiator for you on the market. Look at the,
there no reinventing or rewriting SQLite.

00:49:17:12 - 00:49:20:24
Stefan
Why are they doing that?

00:49:20:27 - 00:49:41:21
Dustin
Well, first of all, nobody would ever nobody would ever have done that because nobody
everybody knows that SQLite is super reliable. It is the most used database in the world. And,
now theyre rewriting it in rust. And I think, there want to leverage that on, on on the edge and
Yeah.

00:49:41:28 - 00:49:59:11
Stefan
But the, but this whole thing with the edge. So, there was a GraphQL backend as a service
company that was all on the edge. And then Vercel was like, deploy the edge, but then we're so
kind of like, dropped that initiative, like, like, what is the edge? And like, I'm seeing more and
more people, like, care less about it.

00:49:59:13 - 00:50:03:08
Stefan
If you will.

00:50:03:10 - 00:50:32:08
Dustin
Yeah. It's it's about, being being being local, being, near to to your customers. It's about latency.
It's about, Yeah, I would say performance, but you need to good use case. I mean, you I think
we wouldn't have any benefit from deploying our control plane to the edge. If our existing use
case is.

00:50:32:10 - 00:50:37:13
Dustin
That's already is already more than good enough for the, like.

00:50:37:15 - 00:51:08:10
Stefan
Yeah, I would agree. The only use cases that I can understand is, like. So, for example, like
what some of our e-commerce companies like for them, latency and like the web page being
slow, it actually loses money for them. So they have to be the most performant and it has to be
fast. Because the way you think about it is I'm a user, I go on and I don't know some Sheahan or
some fashion Nova, and if my experience on there isn't good, like I'm adding things to my
shopping cart and when I go to click checkout, it takes like 10s.

00:51:08:12 - 00:51:29:29
Stefan
The likelihood that I leave is extremely high because it's slow and it's not performant. So I can
see for like e-commerce edge being important because you want to be as quickly as possible,
get them from shopping to the counter to pay and then pay. But do you see anywhere else
benefits? Like maybe like streaming? Streaming would be good.

00:51:30:01 - 00:52:00:03
Dustin
Yeah. It really it really depends on the use case. I mean, even if you deploy your application or,
your logic at the edge, your database will probably still, sit somewhere else in your internal
structure. So, that's why fastly Cloudflare trying to build a complete ecosystem around that. You
have a key value store, you have, S3 API, you have not even a database.

00:52:00:05 - 00:52:23:02
Dustin
So then it makes absolutely sense. You can build complete application at the edge. And I mean,
what we, we did already like in Cosmos Cloud is a solid architecture. So we have, we have
implemented, cloud for worker that, is connected with an S3 integration where we upload a
router configurations and make them accessible to, to the customers.

00:52:23:04 - 00:53:01:17
Dustin
So we have we have to develop a small application that is essentially an Http server and has S3
integration, you can call it its database. And why did we do this? Because it's so easy to deploy.
It's we can be sure it's it's it's scalable. It works everywhere. It's, it's cost efficient. And we don't
have to deal with anything like, like deployments, maintenance because it's it's essentially for
us, it's just a script. 