---
title: Solving Organizational Problems Beyond GraphQL
slug: ep18-10-solving-org-problems-beyond-graphql
series: The Good Thing
episode: 18
chunk: 10
participants:
- Stefan
- Jens
segment: TAB insights and organizational problem-solving
timecode: 00:58:35:21 – 01:08:29:00
start_time: 00:58:35:21
end_time: 01:08:29:00
speakers:
- Stefan
- Jens
topics:
- Parenting and negotiation parallels with enterprise sales
- TAB findings from Fortune 500 to startups
- Company scale diversity from 50 to 10,000 engineers
- Organizational problems beyond technical solutions
- AI tooling for filtering TAB insights
- Healthcare startup to public company range
- Episode conclusion and format preferences
tags:
- organizational-problems
- tab-insights
- company-scale
- enterprise-diversity
- ai-tooling
- episode-conclusion
topic_tags:
- organizational-problems
- tab-insights
- company-scale
- enterprise-diversity
- ai-tooling
- episode-conclusion
entities:
- Fortune 500 companies
- Healthcare startups
- Public companies
- Europe companies
- Peppa Pig
mentions:
- Serbian culture parenting
- force vs negotiation with kids
- don't negotiate with terrorists meme
- Fortune 500 to healthcare startups
- 50 to 10,000 engineers scale
- AI tooling for filtering
- company name confidentiality
- live vs recorded format preferences
- episode conclusion
summary: The conversation transitions from parenting negotiation tactics to TAB insights,
  with Stefan describing their diverse customer base ranging from 50-engineer startups
  to 10,000+ engineer enterprises across Fortune 500 companies, healthcare startups,
  and European public companies. Jens hints at significant organizational findings
  beyond GraphQL technical solutions, mentioning AI tooling used for filtering insights
  while maintaining confidentiality about specific company details and discoveries.
---

00:58:35:21 - 00:58:36:18
Jens
And,
00:58:36:20 - 00:58:40:26
Stefan
My dad, by the way, in Serbian culture, he could beat me if I was bad.
00:58:40:28 - 00:59:06:10
Jens
Currently here, the the culture is you. You you don't use force against kids. Not. Not in words,
not with with your hands, whatever. And so there's this, this typically like a point where you
reach this point and you're like, okay, you if you don't do this, you cannot watch Peppa Pig or
whatever. And then your kid is like, yeah, that's fine, I don't care.
00:59:06:10 - 00:59:26:27
Jens
I don't want to watch it. And you're like, okay, shit. Like, what are we going to do next? And so
so that's what is to say. Like, I, I will, I will have a lot of fun when, when you have your first kids
because you will realize that negotiation with enterprises is so simple.
00:59:27:00 - 00:59:37:18
Stefan
Have you ever seen that meme where, like, this guy, like, was on a negotiation and he goes, we
don't negotiate with terrorists. And just so is that how it is with kids? You just shut the door and
you're just like, go to bed.
00:59:37:20 - 00:59:43:00
Jens
That's the same thing with with kids. Okay, back to your question. And then we end the stream.
00:59:43:02 - 01:00:02:04
Stefan
Yeah. What are some of the biggest findings or from the TAB that you've learned in the first two
weeks? Because I know we've all seen some cool tooling with like AI to kind of filter through it.
But what have you learned from these companies? And just for context, for the viewers, these
are fortune 500 companies. These are emerging healthcare startups.
01:00:02:04 - 01:00:17:23
Stefan
These are some public companies in, Europe. There's companies all over from 50 engineers to
1000 engineers to even more think like 10,000, something crazy like that. But what have you
learned across all these companies?
01:00:17:25 - 01:00:23:21
Jens
Can you give me some some hints? What I'm allowed to say. You could tease.
01:00:23:21 - 01:00:46:19
Stefan
A little bit of what we're building. Don't say any of the company's names. Don't say any of the
companies like, positions. But what are you noticing that companies are doing? Like, they're
they're bringing together a bunch of tools. For what? And and you can hint a little bit on that. You
can hint a little bit on like the biggest problem that companies are doing maybe don't say the
tooling that we're going to go against.
01:00:46:21 - 01:00:59:16
Stefan
But oh, it's interesting that people are using tools in a way that they're not supposed to be used,
you know, but just keep a high level or we can end it right here as like a cliffhanger for the
audience,
01:00:59:18 - 01:01:34:01
Jens
Okay. So if we start with GraphQL Federation, what we're doing is we're building APIs, and then
you have to ask yourself the question, why are people building APIs? They build digital
products. A lot of our customers are B2C. And so you then have to understand what is the
process behind building these products. And we kind of realize that Cosmo is somewhere in this
in this journey.
01:01:34:03 - 01:02:13:02
Jens
It's it's, one I really need to work on this. It's it's it's one part of of of the big puzzle. It's one part
of of the journey. And we we figured out that this whole journey from product idea to product in
production, it's completely disconnected and there's like, so many people involved in. Yeah.
How do we bring this, this idea into the graph and then the graph into the front end applications
or whatever, or we connect it with MCP to AI or this kind of stuff.
01:02:13:05 - 01:02:50:18
Jens
And so there's a lot of people involved and there's a lot of collaboration involved. You have
sometimes you have designers who build UI mocks. Then you have discussions about user
flows. Then you somehow try to connect these flows and, the UI sketches, you try to somehow
connect this to, to API design and then you deploy it and then or well, first maybe you mock it,
then you deploy it and production, blah, blah, blah.
01:02:50:21 - 01:03:24:24
Jens
But what we have kind of figured out that this, this whole journey is completely disconnected.
And yeah, I would say for me the most confusing thing is that and I and like, I don't want to to
boil we can you know the names but oh and how in hell is it possible that the whole competition
is completely ignoring what the market is trying to do, or what what our customers are trying to
do?
01:03:24:27 - 01:03:53:19
Jens
Everybody is is so focused on GraphQL. Everybody's so focused on, I don't know, there's, you
know, there's maybe this is a little bit of a rant, but there's working groups on on how to how to
reinvent federation, how to add new directives for, for federation. And, and I think this is not this
is not the real problem. We don't need another version of Federation.
01:03:53:19 - 01:04:36:02
Jens
We don't need a better version of federation. We need to zoom out. And we need to understand
that federation as it is. It's it's okay. But also REST APIs is okay. But ultimately, this whole
journey, how can we make it easier for people to go from product idea to product reality? And if
you think about this, you kind of realize that, I don't know, but just just building a supergraph and
splitting it up into subgraphs and then using GraphQL in the front end, it's not going to cut it like
this is good, like nothing is wrong with it.
01:04:36:04 - 01:05:00:04
Jens
And I can give you many reasons why why Federation is great and I can give you more reasons
why. I think for a lot of B2C front end driven solutions, I think GraphQL and things like relay is
absolutely fantastic and I definitely recommend it, especially when you have like multiple teams
working on multiple products. Back end, front end.
01:05:00:04 - 01:05:26:22
Jens
So I, I believe like GraphQL Federation is a is a good architecture. It's a good pattern. But we're
not solving we're not solving the whole journey. And this is something that that wundergraph will
focus much more in the future. We want we want to connect the different the different parts of
the journey. And we want to focus on the on the overall journey.
01:05:27:00 - 01:05:56:06
Jens
It doesn't mean that we're de focusing from from Cosmo. Quite the opposite. So we're investing
more and more. We're, we're, making the team bigger and stronger. But, ultimately, I, I, you
know, I think and this is something it's it's for me, it's a personal journey, but over the last couple
of years, I, you know, if you know my past, I started with GraphQL go tools.
01:05:56:06 - 01:06:24:28
Jens
So I, I'm, I'm the engineer here. I'm the technical founder. Stefan is the business guy. I started
with an open source library to build GraphQL gateways because I thought that's an interesting
problem to solve. And over the lead over the last couple of years, I kind of came to the point
that, okay, GraphQL is cool. Federation is cool, but I want to solve I want to solve organizational
problems.
01:06:24:28 - 01:07:01:11
Jens
I want to solve like really high impact problems. And for me, that means I want to help
organizations build products faster. And that really, that really drives me. That drives the whole
company now. And, I think we're we're going in a super interesting, direction because what I,
you know, what I was struggling with in the past is how how can you justify, ACVS and your
contract values of hundreds of thousands or even millions?
01:07:01:14 - 01:07:28:11
Jens
And the point is, you can't just make something proprietary and then say, like, hey, it's hard to do
or it's scarce or whatever, and it's going to cost 500 K. It's it doesn't feel right. So there needs to
be tremendous value. And so, when, when, you know, when, when I was starting with, with
startups, initially I was like, I want to make money.
01:07:28:14 - 01:07:54:01
Jens
And now I'm, I'm, I kind of transitioned into I want to I want to create value. And I think if you
create value, if you if you bring a valuable solution to others, money will follow. But the focus
needs to be on on the value and for for us through the, through our activities with the Technical
Advisory Board, it's very clear where the where the value is.
01:07:54:01 - 01:08:24:24
Jens
And then I can only encourage every founder to step back from your solution, and, talk more
with your customers, dive deeper into what is the real pain. And once you figure out pains, you
try to to find patterns. And once you find patterns, you you build a prototype, you show a
solution, and then you try to get commitment that people are willing to to pay for that.
01:08:24:24 - 01:08:29:00
Jens
And then you might be on to something well said.
01:08:29:00 - 01:08:44:10
Stefan
So I think it's a perfect place to end the podcast. So guys, thank you so much for joining us.
We're really excited about the next couple of episodes coming forward. Next week, we're going
to have a special guest. Actually, somebody who was on our time was building some exciting
stuff at a public company, and he's going to be joining us next week.
01:08:44:10 - 01:09:03:27
Stefan
So tune in for that guest episode. We're going to try having more guests on to the podcast as
well, because finally, our content producer is full time. We've been messing with him this whole
time, but he's finally full time, which is amazing. So expect more content from us. We're really
excited. And, Jens, what's the good thing? We're back next week.
01:09:03:29 - 01:09:12:07
Stefan
The good thing is we're back next week. Only on the N scale support package ends enterprise.
So that's a good one. I'd probably say support package.
01:09:12:10 - 01:09:18:20
Jens
Yeah. I think she's like, secret board member and she.
01:09:18:20 - 01:09:19:23
Stefan
Dictates what happens.
01:09:19:25 - 01:09:23:27
Jens
Tickets. Kids control your life. That's awesome.
01:09:23:28 - 01:09:28:27
Stefan
Well, guys, see you next week. Thanks for joining us. Have a great day or great evening.