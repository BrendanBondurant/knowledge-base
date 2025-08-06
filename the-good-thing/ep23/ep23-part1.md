Episode 23
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
00:06:53:16 - 00:07:00:12
Jens
It's, it's good for everybody who wants to have, a relational database. Do you see this, though?
00:07:00:14 - 00:07:08:00
Stefan
We've consistently outperformed every Postgres product on the platform, even when giving the
competition 2x the resources.
00:07:08:03 - 00:07:09:25
Stefan
Oh, yeah.
00:07:09:27 - 00:07:37:01
Jens
It's a little bit unfair because, you know, if you go back, there's this blog post about, planet scale
metal and essentially what, what planet scale does is, they figured out a way of running the, the
database, running them with a locally attached, NVMe drive, which it's it's very hard to to beat if
you have a network attached.
00:07:37:01 - 00:07:39:08
Jens
Hard drive.
00:07:39:10 - 00:07:43:27
Stefan
But they're building some hard core engineering like this is some pretty badass. Absolutely.
00:07:44:00 - 00:07:45:08
Stefan
Yeah.
00:07:45:10 - 00:08:05:20
Stefan
Question for you though. What do you think? Like not every company is a YouTube. Not every
company needs that amount of data and sharding. Do you think by being so hardcore that they
cut down on their available market, or do you think that we're now adding Postgres? Basically
they're going to be the database for big companies.
00:08:05:22 - 00:08:08:07
Jens
Can you go to the pricing page?
00:08:08:10 - 00:08:12:28
Stefan
Yeah. One second. Oops. Wrong page.
00:08:13:00 - 00:08:16:15
Stefan
Let's go to pricing okay.
00:08:16:15 - 00:08:23:03
Jens
Let's see where can we start. Let's what's the starting point? 39 bucks.
00:08:23:05 - 00:08:25:09
Stefan
Yeah.
00:08:25:12 - 00:08:27:28
Jens
With a ten gigabyte database.
00:08:28:00 - 00:08:32:26
Stefan
Yeah. I mean, why not?
00:08:32:28 - 00:08:37:09
Jens
I would totally buy it.
00:08:37:11 - 00:08:37:15
Stefan
Too.
00:08:37:18 - 00:08:54:26
Jens
Yeah, 1500 gigabytes. It costs you something. But starting with with 39 bucks. I mean, if you
want to have a reliable database, why not, click, click on metal. This gives us more IOPs. Click
on metal.
00:08:54:28 - 00:09:02:00
Jens
Okay. So if you want to have a super fast database it starts at scroll down.
00:09:02:03 - 00:09:02:18
Stefan
It's actually right.
00:09:02:18 - 00:09:04:10
Stefan
Here, 600 bucks.
00:09:04:13 - 00:09:07:19
Jens
Yeah. But is it the total cost.
00:09:07:22 - 00:09:09:10
Stefan
609. Yeah.
00:09:09:12 - 00:09:37:22
Jens
Okay. Yeah that's the question. So I guess not. This is not for everybody. But if you have, if you
have, a serious thing going, then yeah, you should definitely think about it. I mean, if you, if you
build an app and it's latency sensitive and let's say you have 100 milliseconds latency and let's
say of that 100 milliseconds, 30 milliseconds is, is, database.
00:09:37:22 - 00:09:46:06
Jens
And you can cut it down to five. It could be worth it. If you're in e-commerce something this will
immediately pay back.
00:09:46:08 - 00:09:53:10
Stefan
I mean, check this out. 64 vCPUs. 512gb memory. What is this? GB NVMe?
00:09:53:12 - 00:09:58:00
Jens
That's the, that's the drives, the locally attached drives.
00:09:58:03 - 00:10:06:18
Stefan
And damn, 23,000 a month. And then if you add a little bit more 44, it's kind of cool. You can see
the entire pricing here.
00:10:06:20 - 00:10:10:21
Jens
Yeah. They also don't do weird weird enterprise pricing.
00:10:10:24 - 00:10:14:17
Stefan
So I don't know I, I.
00:10:14:17 - 00:10:25:18
Jens
I think you for 600 bucks you get an insanely fast database. If you have an operation that needs
a fast database, sure. That that can make sense.
00:10:25:21 - 00:10:33:25
Stefan
month.
But look at this. Like if you wanted to shard it, you're looking at work 16 shards, 1 million a
00:10:33:27 - 00:10:35:21
Stefan
I mean. Yeah, okay. You you you.
00:10:35:25 - 00:10:40:27
Jens
You have like, you chose a lot of compute and everything.
00:10:40:29 - 00:10:44:13
Stefan
I mean, it's pretty incredible how they show you everything on here.
00:10:44:15 - 00:10:45:15
Jens
Yeah.
00:10:45:18 - 00:10:53:04
Stefan
But. And then I guess for enterprise, it's if you want to bring your own cloud. So what does that
mean? But you don't use their cloud.
00:10:53:06 - 00:10:58:10
Jens
You, you can you can deploy them into your cloud.
00:10:58:13 - 00:11:06:01
Stefan
This is pretty badass. No, I think what they're building over at planet scale is pretty amazing. I
mean, look at these companies. They got some hype. Yeah. Well, cursor. I gotta.
00:11:06:02 - 00:11:17:08
Jens
Go. Go back to this blog post about Postgres. Here, because I, I figured there's something
interesting search for the term, proprietary.
00:11:17:11 - 00:11:20:06
Stefan
Proprietary.
00:11:20:08 - 00:11:48:23
Jens
Yeah. You see, plants scale for Postgres uses real Postgres running on our proprietary operator,
blah, blah, blah, blah, blah, query buffering and connection pooling via our proprietary proxy
layer PSbouncer. So they have a bunch of proprietary stuff. And I think it's it's pretty smart what
they're doing. Like, Vitess, it's it's open source, but they're their operator.
00:11:48:23 - 00:12:13:23
Jens
It's not open sourced. The PSbouncer is not open source. So there's, there's a moat. And I think
they, they understand the value. And, yeah, I think they are they are doing it. But you know,
other companies like for example, let's say the search Elasticsearch, they have this issue with
licensing and AWS and something and to me it seems like planet scale.
00:12:13:23 - 00:12:37:09
Jens
They figured out a great way where to draw this open source proprietary line like nobody will
complain about, hey, you have this proprietary PSBouncer, people will just want to use it. And I
can I can deploy it in my own account or something. So I don't know a good, good service, good
company. I'm I'm fan honestly.
00:12:37:11 - 00:12:57:15
Stefan
And that's the Jen's recommendation seal. Jacob, we need if you ever seen there's this
YouTuber where like when he approves of a video game, it stamps like a big stamp. So it's like,
Sam's approval. We need one for Jen's, if that. If Yen's approves of a company. stamp? Yeah.
No, I'm. No, I'm honestly in the same way to go ahead.
00:12:57:16 - 00:13:31:26
Jens
Sometimes I see posts from Sam on Twitter and I'm like, I'm not sure if I. If I like this person,
they I don't know, they are. They are special in a way. But at the same time, it seems like they
are doing a lot of stuff. Right? And, I also heard that, someone wrote on, on LinkedIn that if you,
if you join a startup and the CEO is not a little bit intense, then probably it's, it's a it's in the
wrong company.
00:13:31:26 - 00:13:58:01
Jens
And I know for myself, I'm also not an easy person. Like I, I care about stuff, I have opinions
and, I have opinion, experience and, I think if you want to build a successful startup and, and
the CEO is, is not weird in some way or crazy in some way, I don't think it's a, it's a good sign.
00:13:58:01 - 00:14:04:08
Jens
So yeah. Kudos to to Sam. He's he's building something great.
00:14:04:10 - 00:14:13:01
Stefan
I agree I do want to though see if we can find his tweet. But he just kind of roasted old.
00:14:13:08 - 00:14:14:20
Stefan
Where is that?
00:14:14:22 - 00:14:16:09
Jens
He roasts what
00:14:16:12 - 00:14:26:21
Stefan
whatever?
Where he roasts. Basically somebody is like, what's the difference between you and neon or
00:14:26:23 - 00:14:28:03
Stefan
Yeah.
00:14:28:06 - 00:14:48:21
Stefan
I mean, to be honest, though, like, uptime is a pretty tough thing. Like, it's really, really hard. I
mean, have you been seeing what's been happening with, like turso, like for the past couple of
months? They had some pretty bad outages. And then you have somebody like Sam check this
out.
00:14:48:24 - 00:15:13:03
Stefan
To the right it says people ask what's unique about the planet scale postgres product. Here's
one thing. This is a direct dig towards neon. But look at this, 100% uptime. Granted, it is from
April, but still in between April and July 2025, there have been neon outages. So I think also I'm
a fan. You do have to be intense as a founder, but this is pretty badass.
00:15:13:06 - 00:15:17:15
Jens
Do you know how you achieve that? Like, do you know what is behind this?
00:15:17:17 - 00:15:26:21
Stefan
A lot of hard work and dedication and great engineering, but that's all I could say to it. What is
it? Give us a little insight, context.
00:15:26:23 - 00:16:01:24
Jens
So I think what's crazy about this is you cannot achieve, this level of high availability if you are in
a single zone. Because there's always, like, glitches or something. So there's a lot of
engineering behind it. And then, I think platform engineering wise, they are they are pretty
decent. They, they have figured out like, I don't know how they how they are completely
redundant on like so many layers and then they, they obviously work on, on vitess.
00:16:01:24 - 00:16:34:08
Jens
So they, they merge changes, which also means they must have a pretty good workflow
process, whatever for testing, for bringing in changes like I think in general, there must be a very
good engineering culture because if you, if you don't have, like staging environments and
everything and then a lot of redundancy and good process for, for verification, of of code
changes and everything good testing then you would never see those numbers.
00:16:34:10 - 00:16:42:09
Stefan
You know what we should do? Note for Jacob. We should try to get Sam on the podcast and
just talk to him about, like, hard core engineering, like, what are you guys doing over at
planetscale?
00:16:42:09 - 00:16:43:06
Stefan
Yeah, would be.
00:16:43:06 - 00:16:51:22
Jens
Interesting. Like, what's what's behind this, this graph. Like what? How does a company need to
look like from the inside to achieve this?
00:16:51:25 - 00:17:09:13
Stefan
And I think the total headcount for them, I am. I could be wrong if someone could double check
for me, but I think it's like 40 or 50 people or like 40 or 50 engineers at least, which is to achieve
this. It's incredible. So official approval of Jens, stamp I approve. Yeah.
00:17:09:19 - 00:17:24:06
Jens
We we have an emoji in our slack. It's, colon impressed. And then we have a second one. It's
it's colon. Unimpressed. And both are a picture of me and it's the same picture.
00:17:24:09 - 00:17:34:24
Stefan
I mean it tells us the it's the German roots in there, but I love it. Let's get on to a little topic
though. That's not pretty happy. So this is pretty crazy.
00:17:34:24 - 00:17:41:18
Jens
We can also take the happy path first. So we talk about, someone leaving Vercel.
00:17:41:21 - 00:17:56:24
Stefan
Ahh ok. So let me bring up the tweet. Yes. All right. Hold up. But, give us a little bit of context. So
everybody knows this person. Just left vercel. So let me bring up the tweet so we can actually
see it. This is actually.
00:17:56:27 - 00:18:03:29
Jens
Pretty insane I would say he he redefined what, what, developer advocacy means, right.
00:18:04:01 - 00:18:24:26
Stefan
Well, so I had a weird opinion. So in 2021, I met a bunch of developer advocates. And I hated
that whole profession. Like, you just make to do apps, you just make, like, whatever you say. I'm
a developer, developer advocate. I just write blog post. I totally agree, I think Lee Robinson, like
what he did for Vercel, was insane.
00:18:24:28 - 00:18:37:13
Stefan
I think he was one of their most critical components. It's crazy to me that he's leaving, though.
Like, Vercel just did it like a series d. I think I can see them going for an IPO path, but intense.
00:18:37:15 - 00:18:39:02
Stefan
Yeah.
00:18:39:04 - 00:19:09:01
Jens
What do you think? I, I don't know, I have a lot a lot of respect for Lee. I think he, he did great
work. I think he, he helped a lot make Next.js what it is and to until a certain point I slowly start
to see some, some cracks in Next.js like this. There's some, some controversies now, like
Vercel moving back and forth, vercel moving more into AI and other things.
00:19:09:03 - 00:19:45:12
Jens
But overall, I think, yeah, Lee really has shaped what what we know today is like rep dev and
and, developer advocacy. So I think he did a great job, five years with Vercel. So that kind of
indicates, he might be fully vested. Another part is you would typically stay inside a company if
you if you're expecting to get, like, more shares or that you can significantly increase the value
of your shares.
00:19:45:14 - 00:20:08:15
Jens
It seems like this is not the case for for Lee. And maybe there's other opportunities. Maybe in
the in the AI space, I don't know. I could totally see how he's starting tomorrow with anthropic or
whatever. And I, I don't know what. Yeah. It seems like things are going well for him.
Congratulations on on this run.
00:20:08:15 - 00:20:13:09
Jens
I think, he did pretty well. Yeah.
00:20:13:12 - 00:20:18:00
Stefan
Like, does he get to get the stamp? Does he get the stamp of approval?
00:20:18:02 - 00:20:19:18
Jens
Absolutely.
00:20:19:20 - 00:20:20:11
Stefan
Yeah.
00:20:20:13 - 00:20:39:27
Stefan
I also want to go through his blog post. So I think it's got some good stuff into here. For
example, go hard at work and go home. So he talks a little bit here about like, going hard at
vercel and he has pictures. This one is really cool. Everything can be done faster. I really, really,
really like this one.
00:20:40:03 - 00:20:40:21
Stefan
What would you say?
00:20:40:22 - 00:20:43:06
Jens
I think he also has a kid now right?
00:20:43:08 - 00:20:48:20
Stefan
Yeah. He also has a kid.
00:20:48:22 - 00:20:55:13
Stefan
Yeah. This one I like. Everything can be done faster. Scale or die trying.
00:20:55:15 - 00:21:02:03
Stefan
Pretty cool. This is a great one. He's got some good stuff into there.
00:21:02:05 - 00:21:04:01
Stefan
Yeah.
00:21:04:04 - 00:21:16:00
Stefan
Guys, I recommend reading. I will drop it below into the notes. But congratulations Lee. I'm
excited to see where he goes. How much you want to bet he goes to an AI company? Should
we bet?
00:21:16:02 - 00:21:23:06
Jens
It in this climate. So maybe he leaves tech. Maybe he starts a farm.
00:21:23:09 - 00:21:23:25
Stefan
Yeah.
00:21:23:28 - 00:21:26:24
Jens
Or he goes into AI.
00:21:26:27 - 00:21:37:24
Stefan
I think he goes to AI. I think he's going to go to OpenAI anthropic. Maybe. Cursor. He'll probably.
How much do you want to bet? He goes to cursor.
That that's that's a problem with cursor. Like it's not the the most liked company at the moment
00:21:37:26 - 00:21:46:07
Jens
anymore.
00:21:46:08 - 00:21:50:23
Stefan
Good, good. Transition. Good transition. So let's say that we.
00:21:50:27 - 00:21:54:12
Jens
We we didn't plan this transition. It happened.
00:21:54:14 - 00:21:58:05
Stefan
Yeah. We didn't. So yepJens is right. Let me bring up the article by.
00:21:58:05 - 00:22:05:20
Jens
The way Jacob. The the the Good Thing logo sits on top of the Stefan's, name.
00:22:05:22 - 00:22:08:26
Stefan
Well, once I start sharing it, if it goes to normal.
00:22:08:29 - 00:22:12:04
Jens
Then, then it moves to the right. Yeah. That's correct.
00:22:12:07 - 00:22:13:24
Stefan
Oh. There we go.
00:22:13:26 - 00:22:16:11
Jens
See? It's improving.
00:22:16:14 - 00:22:17:27
Stefan
Magic.
00:22:17:29 - 00:22:34:06
Stefan
And get rid of this stupid ad. Okay, so walk me through what happened. You brought it up, I saw
it, I was messing around with cursor this week, but basically, they just kind of change their
pricing and just kind of, like, missed a lot of things up. But I think.
00:22:34:09 - 00:22:35:21
Jens
Not once.
00:22:35:23 - 00:22:39:16
Stefan
Twice walk us through what happened.
00:22:39:18 - 00:23:04:03
Jens
Yeah. There, there's, I think there's a Reddit thread. It describes it best and we have the Reddit
link somewhere and let's go to that. So essentially there, there was like, there was an unlimited
plan or like a pro plan and somehow it wasn't really unlimited. And suddenly it was like 500
requests in a month, and then it was like 200 something requests in a month.
00:23:04:03 - 00:23:29:07
Jens
And then, yeah, they kept changing pricing and everything. And, I think it's it's pretty interesting
because it, it shows two topics or this like two, two threats I would talk about. One threat is, I
had a discussion a while ago with the VC and we were talking about, okay, you're bringing up
something that's. Take a look.
00:23:29:10 - 00:24:01:04
Jens
Cursor. Okay. We missed the mark. Yes, but they they they, they kind of missed it multiple times.
Go to the second post. Second answer maybe. I don't know. Here. Okay. GitHub copilot gives
you 300 sonnet requests for ten bucks. And you have 20 bucks. And then you get something
like 40 requests in five hours or every five hours.
00:24:01:06 - 00:24:26:04
Jens
So there's cracks in the business model and, cursor. They raised a lot of money. And coming
back to the, to the two threats. Yeah. Here, this this is interesting. They had like 225, sonnet
calls and then they, they kept changing it and it, it was a whole mess. And I think what's, what's
interesting to observe here is two things.
00:24:26:04 - 00:25:01:23
Jens
So I had this discussion a while ago with a VC and the VC said, and I think this is also,
something Marc Andreessen said that, bad founders in a good market is still good. And good
founders in a bad market is bad and things like that. Yeah. And my point is, I think what we're
currently seeing is that we have, like, founders with very weird behavior in a good market, and
they keep changing the, the licenses.
00:25:01:29 - 00:25:24:03
Jens
And, it's possible that that they that they really harmed the company with that kind of behavior.
And the second part is, in the in the beginning, there was like a lot of talk about how Curser is
just an AI wrapper and they don't have a moat and so on, so forth. And now it seems like they
are under pressure.
00:25:24:03 - 00:25:52:14
Jens
It seems like they they are not really figuring out the business model. They are. They are
tweaking it. And it. I think there's a lot of evidence that behind the scenes, something is going
really, really badly. And they they tried to figure out how can they make money. And it seems like
it's it's currently tough for them. I know that VCs pump a lot of money into, into, AI coding tools.
00:25:52:16 - 00:26:18:29
Jens
Like, anthropic, for example. My, my big question is what is the real cost of an AI coding tool?
And can we justify, the, the margins and everything, like in the long term will, will it to like first or
will it actually work? Or is the business model so broken that if, if, VC money goes dry then it
doesn't work anymore.
00:26:18:29 - 00:26:24:14
Jens
So I think these are these are big questions, Stefan. What are your thoughts?
00:26:24:17 - 00:26:43:27
Stefan
I'm just like kind of reading these comments, like when you have to give them like benefit of the
doubt, like they're, what, 25, 26, 27 like they're young guys for co-founders. They built this
rocket ship that's actually exploded. And then now, you know, they're trying to figure it out. How
much have they raised? They've raised over like I think a billion something in funding.
00:26:43:29 - 00:27:04:18
Stefan
You know, they're at like 500 million ARR I'm just confused with all with that many people and
success. Why wouldn't you like try to figure out the pricing test the AB, test it, take your time with
it. But three times in the span of a month they messed it up. I don't get it. I don't understand.
00:27:04:20 - 00:27:30:14
Jens
The the other question is the normal playbook would be you raise all that money, you capture
the entire market, and then you figure out the business model and it feels like they are like, I can
only imagine that they must be under extreme pressure to make these changes because, I don't
know, maybe they're losing so much money.
00:27:30:17 - 00:27:50:08
Stefan
You know, it's crazy. I was actually reading a blog post about this. Somebody said that this is the
new age of the tech is not there yet. So what that means is you raise a bunch of money and
your goal is to completely own the market, and then the product and the tech will get there. So
for example, cluley, cursor and icon, have you seen like you.
00:27:50:11 - 00:27:52:24
Jens
And you can close this if we're just talking.
00:27:52:26 - 00:28:15:05
Stefan
Yeah. So icon is this AI video generation for ads. Then you got cluley that cheating tool and then
you got cursor which is we raise a bunch of money, we completely own the market and then the
product and the tech will catch up. But you want to own the market first by being there first and
owning it with the money, which is what cursor could have done.
00:28:15:08 - 00:28:33:01
Stefan
But now, if you're reading the comments, they've already pissed off a lot of people and you have
open router, you have all these open source projects coming out. Now you have claude with the
API keys, everything. They're kind of killing their own market share, which is we've raised the
900 million. Why not just keep going and owning the market?
00:28:33:01 - 00:28:36:18
Stefan
I don't get it. I think you're right on that.
