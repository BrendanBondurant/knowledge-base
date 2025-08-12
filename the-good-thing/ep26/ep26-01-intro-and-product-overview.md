---
title: Intro and Product Overview
slug: ep26-01-intro-and-product-overview
series: The Good Thing
episode: 26
chunk: 1
participants:
  - Stefan
  - Jens
  - Sam Lambert
segment: Introduction and PlanetScale Product Overview
timecode: 00:00:22:20 – 00:05:20:08
start_time: 00:00:22:20
end_time: 00:05:20:08
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - PlanetScale introduction and background
  - MySQL vs Postgres hosting
  - Sharded vs unsharded database products
  - Sam Lambert's background at GitHub and Meta
  - Vitess technology explanation
  - Database platform positioning
tags:
  - mysql
  - postgres
  - vitess
  - ai
  - benchmarking
  - database
  - go
  - rest
  - startup
topic_tags:
  - mysql
  - postgres
  - vitess
entities:
  - PlanetScale
  - Sam Lambert
  - GitHub
  - Meta
  - Facebook
  - Vitess
  - MySQL
  - Postgres
  - WunderGraph
mentions:
  - CEO of PlanetScale
  - Years at GitHub and Meta building distributed systems
  - Technical insights and product vision
  - Uptime passion
  - MySQL databases at hyperscale
  - Sharded vs unsharded products
  - Postgres world expansion
summary: Stefan and Jens welcome Sam Lambert, CEO of PlanetScale, to discuss the database
  platform. Sam explains PlanetScale's evolution from MySQL-focused to supporting
  both MySQL and Postgres, covering their sharded and unsharded product offerings
  built on Vitess technology.
---

00:00:22:20 - 00:00:33:03
Stefan
And we're live. Welcome back, ladies and gentlemen, to another episode of The Good Thing.
Today we have a very special guest, which I've been really excited to bring on Sam Lambert
from Planet Scale. Sam, how are you doing today?
00:00:33:06 - 00:00:35:04
Sam
Hey. I'm great, thank you. How are you?
00:00:35:06 - 00:00:44:27
Stefan
Awesome. Doing great. Thank you so much for joining us. We really have a lot of topics we are
going to be discussing today. And for those of the new viewers that are kind of just sinking in,
you guys know Jens. He is my co-host. Yeah, I'm also here.
00:00:44:28 - 00:00:46:06
Jens
Thank you, thank you.
00:00:46:08 - 00:01:03:29
Stefan
Why do we have to intro you? We already know you. But for those of you that don't know Sam,
Sam is the CEO of Planet Scale. And before this, he spent years at GitHub and meta or as
Facebook, where he's been building distributed systems of scales. Some of the things that he's
passionate about is technical insights, strong product vision, strong product leadership and
uptime.
00:01:04:00 - 00:01:08:24
Stefan
You might have seen it on Twitter. He's very passionate about uptime. But Sam, we're so happy
to have you here. How are you doing?
00:01:08:27 - 00:01:13:27
Sam
Thank you. No, I'm really good. Thank you so much for having me on the show.
00:01:14:00 - 00:01:21:29
Stefan
Yeah. We're excited. Did I miss anything in the intro? If you want, feel free to just kind of walk us
through a little bit if I missed anything, but I think I kind of hit some good points there.
00:01:22:01 - 00:01:41:06
Sam
No. Yeah. I think you got I think you got all of it. I can guess I can summarize what plant scale is.
planetscales kind of now the, the database platform we, host MySQL databases at hyperscale
using vitess. Running some of the world's largest consumer products. And now we have, for
vitess as well, which is, well, it's two products, actually, unsharded.
00:01:41:06 - 00:01:46:11
Sam
And sharded vitess products, that we now have out there in the world.
00:01:46:14 - 00:01:50:08
Jens
What's the difference between unsharded and sharded?
00:01:50:11 - 00:02:11:16
Sam
So yeah, actually thats good question. So our current product so the, the product that most
people know and the largest planet scale product is planetscale vitess, which is sharding for
MySQL. That's the product that our largest customers run on. And it doesn't it's always vitess,
right. If you spin up whatever you spin up, you always get a vitess database, whether you're
sharding or not.
00:02:11:19 - 00:02:37:25
Sam
Our new suite of products for the Postgres world was actually split. So they it has an unsharded
product, which is the one that's in private. But, right now it's like a private preview, hosting real
applications for companies. That's. Yeah, like I said, available, but it's pure Postgres hosted on
our operater, with our proxy layer and all the various things that makes planet scale special.
00:02:37:27 - 00:02:59:05
Sam
And then currently now in development and in a phase working with sort of key customer
partners is, our sharded, Postgres product. So the cool thing about that is, you know, because
there's so many people that use Postgres but don't necessarily need sharding, they don't want
to deal with the trade offs that you would get from having a sharding layer in between them and
the database.
00:02:59:05 - 00:03:12:26
Sam
And so we now just provide kind of you directly access or directly through a pooler, to a very
vanilla Postgres, set up. And then the sharding product, we'll put a layer in between that, which
gives you some trade offs, but obviously significantly more scale.
00:03:12:28 - 00:03:24:29
Jens
Yeah. So that means regular Postgres. On planet scale. It's fully hosted by you, but it's like
vanilla Postgres, like, no, no special thing.
00:03:25:01 - 00:03:42:01
Sam
No. I'll proxy the proxy and pooling layer that we have is special and bespoke to us. The
underlying infrastructure that it runs on is also unique. So our operator that allows you to run on
metal nodes, inside AWS and inside GCP, is kind of one of the secret sauce pieces that we
bring to the postgres world.
00:03:42:01 - 00:04:04:01
Sam
And if you look at our launch for the Postgres product, we benchmarked ourself against the sort
of current cohort of, Postgres hosts. And, you know, we can we showed we demonstrated
significantly better performance and throughput. With that, with that product, by giving you
what's kind of good about Postgres, it has some of Postgres downsides. Super.
00:04:04:01 - 00:04:05:21
Sam
That's fine.
00:04:05:23 - 00:04:33:11
Jens
Yeah. For, for for like a very long time when when you were thinking about planet scale, you
were you were immediately thinking, okay, it's it's MySQL. Yeah. MySQL with sharding. But and
then it almost felt like a bit there's like, like a connection of the brand planet scale with MySQL,
almost like you're against Postgres, but it seems like you're absolutely not against Postgres.
00:04:33:11 - 00:04:42:24
Jens
You're, you're, you're, you're kind of rebranding to, okay, planet scale does relational database
at planet scale. Yeah.
00:04:42:27 - 00:05:02:27
Sam
Yeah. Basically. Is that right? Yeah. And definitely not anti Postgres. Very excited by working
with Postgres and the companies that build on Postgres most specifically, I mean, we can dig
into like the core differences that we've already observed between mysql and Postgres, if you, if
you are interested. But yeah, basically we're kind of the database company now, right?
00:05:03:00 - 00:05:20:08
Sam
In fact, shipping Postgres meant that so many more people reached out asking for us to do
other database services. We won't be doing that for a while, maybe one day. But right now we,
we've got a long road ahead in the Postgres world. So we're building building that and enjoying
ourselves so far.