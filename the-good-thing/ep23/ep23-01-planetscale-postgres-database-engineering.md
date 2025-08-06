# ep23-01-planetscale-postgres-database-engineering

**Time Range:** 00:00:23 - 00:06:53

**Topic:** PlanetScale’s Postgres announcement and database engineering deep dive

---

00:00:23:21 - 00:00:45:17
Stefan
And we're back. Welcome back, ladies and gentlemen. Back to another episode of The Good
Thing. It's been a while. Sorry, guys. Last three weeks have been absolutely insane. So, 4th of
July, team retreat. And then I think Jens was on vacation and I was sick. So back we got some
amazing topics today. As always, I'm with my co-host Jens
00:00:45:19 - 00:01:05:05
Stefan
How you doing today? I'm okay. Usual is okay, but, yeah. We're back. We got some great topics
today. I'm actually been missing the podcast. You know, there's been some really exciting topics
happening. So we're going to be talking about Cursor. We're going to be talking about what's
been happening with Next.js Lee, Rob leaving, what else? We have a bunch of stuff.
00:01:05:07 - 00:01:27:23
Stefan
Claude code is now available as a VS code extension. Ooh, the next generation of GraphQL
Federation speaks gRPC. That's a big one. And then Planet Scale now supports Postgres Me
and Jens. We're actually chatting about this about how a company we know is getting just
absolutely annihilated now because Sam is just, just he's just a metalhead. Like, I feel like the
developer world of, like, database people.
00:01:27:23 - 00:01:40:11
Stefan
They're like the relation of metal heads. You know, people that like hardcore metal, they like
hardcore headbanging and things like that. So a lot of topics today. Jens which one are you
most excited about? We start with that one.
00:01:40:14 - 00:02:09:15
Jens
Most excited do you remember when when, Planet Scale announced that they do some layoffs
and then they, they wanted to to shrink the company a bit and focus and not go like, like on, on
raising too much money and stuff like that. I was a little bit concerned, but I also had, I always
had a feeling that Sam creates a company that really cares about engineering, and I think it's
paying off.
00:02:09:15 - 00:02:18:11
Jens
they.
Like, I can totally see how how planet scale. Eventually they will completely own database and
00:02:18:13 - 00:02:20:09
Stefan
Yeah, yeah. Do you remember?
00:02:20:10 - 00:02:21:11
Jens
Pretty good.
00:02:21:13 - 00:02:24:22
Stefan
Do you remember what the name of the blog post was?
00:02:24:25 - 00:02:25:27
Jens
Which one?
00:02:26:00 - 00:02:44:12
Stefan
The one that Sam wrote. Like when he had the layoffs. He got a lot of backlash for the blog post
he wrote. And I remember because it was a crazy title, Dont remember. So it was called Planet
Scale Forever. And he made those layoffs so that planet scale would predate him. He wanted it
to go on forever, and he said, these are necessary.
00:02:44:12 - 00:03:09:12
Stefan
We need to cut everything that's not related to our core mission, everything that's not going to
make planet scale stay around forever. And somebody the other day on Twitter, they were like,
how can you talk about a successful startup company? And they posted the LinkedIn insights
and it shows a decline. And Sam replied, an incline of revenue. And he's like, we trimmed what's
not necessary and we're only focusing on what is, but I think it's a good one.
00:03:09:18 - 00:03:17:13
Stefan
into it.
Let's talk a little bit about planet scale. So I'll bring up the tweet and then we can kind of just dive
00:03:17:15 - 00:03:26:26
Jens
planet scale and,
But basically what do I find? I find it's so weird that there's this weird fight going on between
00:03:26:29 - 00:03:31:04
Stefan
Neon, but do you think it's?
00:03:31:06 - 00:03:33:11
Stefan
Do you think it's a fight, though?
00:03:33:13 - 00:03:35:11
Stefan
I, I'm not sure.
00:03:35:17 - 00:03:40:23
Jens
This whole like, hey, show me your availability graph.
00:03:40:25 - 00:03:53:21
Stefan
Yeah, but basically, if you guys haven't seen. So planet Scale now supports Postgres, which is
pretty crazy because Planet Scale is built on what is it? You know, the tech stack, it's something
crazy. And then it supports, I think MySQL, which is it?
00:03:53:23 - 00:04:23:07
Jens
So planet scale, it's built on top of Vitess, which is yeah. Let's just say it's an extension to
MySQL. It was developed by YouTube, and it essentially allows you to to shard, MySQL.
Sharding in very simple terms means you take a table and this table would be too big because
you're YouTube, and you have too much data, like too many videos, too many users.
00:04:23:10 - 00:04:59:28
Jens
So you can you can put an extra column on a table. For example, let's say, country and then
you shard the video table by country. That means you split the table into multiple tables by
country. And this way the shards, they are smaller. And that means you can put more data and
you can scale out because imagine, you are YouTube and you have a table and it's so big that it
doesn't fit on one machine anymore because it's too big for the machine.
00:05:00:00 - 00:05:30:09
Jens
So you need to figure out, okay, how can I somehow scale this database across like multiple
servers? And then there's this concept of, of sharding and, YouTube built vitess and, planet
scale, picked up, vitess and turned it into, into a company. And I think, from the blog post I read,
they are now, working on, on a new algorithm, a new implementation to bring sharding to
Postgres.
00:05:30:11 - 00:05:31:25
Jens
So then.
00:05:31:27 - 00:05:33:15
Stefan
There will be,
00:05:33:18 - 00:05:42:21
Jens
Infinitely scalable Postgres on top of, yeah, planet scale. I think that's that's good stuff.
00:05:42:23 - 00:05:54:02
Stefan
Let me bring up, the blog post, because I think you're right. So sharding isn't a thing you can do
currently in planet scale or in Postgres.
00:05:54:04 - 00:06:13:07
Jens
That there are solutions for sharding with, with Postgres. And there are there are there's some
competition to to do it, but it's not like super widely used. Like if you scroll down a bit, I think
they, they mentioned some providers scroll this page.
00:06:13:09 - 00:06:25:08
Stefan
Yeah. But just real quick. This is badass, the world's fastest Postgres hosting platform. And then
boom, they already announce it with a customer case study. Badass. Yeah.
00:06:25:10 - 00:06:53:16
Jens
Pretty smart. We like that. Yeah. Here you see, there's, Amazon Aurora, alloy DB, neon, super
Base, Heroku, Crunchy data, and Tiger data. So some of them are not doing sharding, but yeah.
Like some some do like, Aurora has some sort of sharding I think alloy DB and yeah, I think it's,
it's pretty interesting. What what planet scale is doing.