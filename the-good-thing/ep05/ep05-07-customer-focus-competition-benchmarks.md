---
type: podcast-chunk
title: Customer Focus, Competition, and Benchmarks
slug: ep05-07-customer-focus-competition-benchmarks
series: The Good Thing
episode: 5
chunk: 7
segment: Focusing on customers, handling competition, and the pitfalls of benchmarks
timecode: 00:36:27 - 00:45:06
start_time: 00:36:27
end_time: 00:45:06
speakers:
  - Stefan
  - Jens
topics:
  - Customer Focus
  - Competition
  - Benchmarks
  - Copycat Competitors
  - Product Differentiation
tags:
  - startup
  - ai
  - apollo-graphql
  - benchmarking
  - cosmo-router
  - database
  - founder
  - go
  - graphql
  - postgres
  - rust
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
summary: Stefan and Jens discuss the importance of focusing on customers rather than
  competitors, share stories about copycat competitors and false marketing, and debate
  the value and pitfalls of benchmarks. They reflect on how benchmarks can be manipulated,
  why real-world use cases matter more, and how customer focus drives product improvement.
---

00:36:27:06 - 00:36:51:27
Jens
The router should come with a native solution. So we're now collaborating on the on on how can
we build a native solution instead of just saying yes, build the middleware. And that's that's
simply I think I don't know, it's so simple to move your start up forward. Just just look at what
people are trying to do.

00:36:51:29 - 00:37:13:21
Stefan
Yeah. Talk to users. One thing that you mentioned that was like we don't really focus on
competitors, we focus on the customers. And a cool antidote is from back in the day. There was
a board meeting at Amazon when Jeff Bezos was CEO and, Amazon was profitable the first
year. And then in year 3 or 4, they really took off in the early 2000s like they were crushing it.

00:37:13:24 - 00:37:32:26
Stefan
And so they were having a I think that they even went public. So let's say they were a publicly
traded company and they were so far ahead in the e-commerce space in books that Barnes and
Nobles, which is one of the biggest retailers for books in the United States, they started
launching a online website to sell books, basically what Amazon is doing to compete with them.

00:37:32:29 - 00:37:52:26
Stefan
And a lot of the employees at Amazon got worried. Oh my God, like, oh my God. Barnes and
Nobles has so much distribution. Like we're a startup, how are we going to compete against
Barnes and Nobles? And one of the things that happened was, Jeff Bezos wrote a memo to the
entire company, and he says the way we win against Barnes and Noble is by focusing on the
customer.

00:37:53:02 - 00:38:11:14
Stefan
We don't give any attention to Barnes and Nobles, and we just focus on the customer. And he
kept doing that throughout the years at Amazon. That if you focus on the customers, if you have
the conversations with them, if you don't try to solve the problem, but instead learn exactly what
the problem is, is that this is how you scale your startup.

00:38:11:14 - 00:38:36:03
Stefan
And that's literally the definition of founder mode. He kept it from the beginning, all the way up
until the end. Now it's a little bit tougher, but they're still have that mantra of listen to the
customer. And so this is a great point to talk a little bit about competitors. So yeah. So Jens
have a copycat competitor. Literally if you guys have seen Borat where it's like we implement a
router, they implement a router, we implement this, they implement that.

00:38:36:09 - 00:38:57:15
Stefan
We have customers. They don't have customers. No I'm kidding. But jokes aside, we have a
competitor and they do false marketing. And me and Jens are having a debate about this. And I
want maybe if the audience wants to chime in. But my take on this is if a competitor is doing
false marketing and saying false information about your startup, you should correct it.

00:38:57:18 - 00:39:14:24
Stefan
You should call them out. And then yeah, and you have your opinion on this. You can give it if
you want, but yours is. Don't even give them any attention. But what do you think about that like
and also it's a good transition. There was some drama on Twitter this week where a really big
what series B startup.

00:39:14:27 - 00:39:23:22
Stefan
He started causing drama about a competitor that was doing false marketing. And for me, I don't
think that there's a way to win. What do you think?

00:39:23:24 - 00:39:28:15
Jens
So many topics to unpack. Well, where do we start?

00:39:28:17 - 00:39:33:22
Stefan
Whichever one you want, we can start with founder mode, or you can start back with the
competitors.

00:39:33:25 - 00:40:21:08
Jens
Okay. Competitors. So, so one, one thing like, I don't know, it's it's like, it's just my playbook.
When I have a much bigger competitor, it's it's okay to say that name. It's okay to sometimes
compare with them. But I also try to be not too impolite. Like, of course there can be some
banter, but no enterprise ever really like WunderGraph when the founders or the people of
WunderGraph shits on Apollo like.

00:40:21:10 - 00:40:54:28
Jens
I don't know, it's you can't it shows. It shows something about you. Like you can compare and
maybe. Yeah, but it's a, it's a gray zone. And then there's another thing. If you have smaller
competitors, people copying you or something. My my simple rule is to to never use the name of
the company and just pretend they're not there, because my, my assumption is why should I use
my audience to give them attention?

00:40:55:00 - 00:41:02:10
Jens
I said? But way,
So I have the my network. I have my audience like they they don't deserve it. Did you hear what

00:41:02:12 - 00:41:06:27
Stefan
I you know who always says that? Like, why should I use my audience to give you attention?

00:41:06:29 - 00:41:07:20
Jens
Nope.

00:41:07:23 - 00:41:10:07
Stefan
Your buddy Theo, he's always saying that.

00:41:10:09 - 00:41:41:19
Jens
Yes. Okay. Yeah. My my my best friend. Theo. I met him in person. It wasn't just a good day,
okay? But. And and then there's this thing about these data base companies. And I think one
thing we need to be super careful about is, benchmarks. So for many years now, I have
benchmarks on my computer to compare all the different graphql gateways, like all of them.

00:41:41:21 - 00:42:11:09
Jens
And I do little tweaks and tests and I, I know a lot about how they behave. And I'm I really love
benchmarking on my own, but I have never committed this anywhere, and I'm not intending to
publish it for a simple reason. Everybody who knows enough about benchmarking also knows
that I can benchmark. I can define the results and benchmark backwards if I want to.

00:42:11:09 - 00:42:41:04
Jens
Everybody can do this and I don't know if you benchmark like a database, and one database
has cold starts and one database doesn't have cold starts, yeah. Well, what are you expecting?
And then I don't know why. Why create this kind of drama? To be honest. Like, we we are. We
are a super boring company. Just deploy a Postgres database.

00:42:41:11 - 00:43:19:17
Jens
No serverless Postgres. Just a boring Postgres on GCP, Azure or AWS. It's always on, it costs a
few bucks, but we have users. Who cares? There's no cold start and I don't need to benchmark
it and I can trust it that it works. And yeah, okay, there's maybe other solutions, but maybe, for
example, this is not advertisement of sorts, but with neon you can have like serverless,
databases and you can have branches and other things.

00:43:19:19 - 00:43:41:26
Jens
And the benefit of a serverless database can be, that you can have many of them and they don't
cost you something when they are asleep. And they they might have a cold start or Prisma or I
don't know, I don't care about databases, but let's say you have a cold start. Use the right tool
for the right job.

00:43:41:26 - 00:44:12:28
Jens
Like if you need 10,000 databases but you rarely use them, maybe that's good. We need one
Postgres and it it should be fast. And we want to have a boring, simple solution. We just use
AWS or GCP like. But the one thing I would really avoid with these benchmarks is, I actually I
tell a trade secret, no.

00:44:12:28 - 00:44:37:13
Jens
Do it. Yeah. The reason I'm not publishing benchmarks where other gateways look bad is, I'm
not giving away my knowledge. Like, if I show you where your gateway is really bad, it means
that I'm pointing you exactly to where you have to improve. Like, I'm not gonna do that. Like.
Yeah. No, I was.

00:44:37:13 - 00:44:38:17
Stefan
Wondering when you were going to say.

00:44:38:17 - 00:45:03:06
Jens
That. So, I don't want others. Like, my product is better, but I don't have to tell you where, like,
you have to figure out on your own and, so, I don't know if someone publishes a benchmark
that's like, please beat these results. Like you urge the competition to act like, why do it? Keep it
to yourself.

00:45:03:06 - 00:45:06:08
Jens
Like, I don't know. It's it's not smart.