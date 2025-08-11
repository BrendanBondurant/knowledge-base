---
title: Apollo Principles and Small Startup Hacks
slug: ep22-03-apollo-principles-and-small-startup-hacks
series: The Good Thing
episode: 22
chunk: 3
participants:
- Stefan
- Jens
segment: David vs Goliath Strategy and Apollo Analysis
timecode: 00:11:01:10 – 00:16:05:00
start_time: 00:11:01:10
end_time: 00:16:05:00
speakers:
- Stefan
- Jens
topics:
- Small startup competitive advantages
- Apollo GraphQL principles document
- Big brother vs little brother dynamics
- Principled GraphQL framework analysis
tags:
- small-startup-strategy
- apollo-principles
- competitive-dynamics
- david-goliath
- principled-graphql
topic_tags:
- small-startup-strategy
- apollo-principles
- competitive-dynamics
- david-goliath
- principled-graphql
entities:
- Stefan Avram
- Jens Neuse
- Apollo
- Supabase
- Google
- Jeff (Apollo CEO)
- Matt (Apollo CTO)
- WunderGraph
mentions:
- small startup advantages
- big brother little brother analogy
- Supabase vs Google example
- Principled GraphQL document
- Apollo CEO and CTO authorship
- competitive positioning tactics
summary: Stefan explains the "little brother advantage" where small startups can aggressively
  challenge larger competitors without retaliation, using Supabase's bold marketing
  against Google as an example. They transition to analyzing Apollo's "Principled
  GraphQL" document written by the CEO and CTO, examining how established companies
  codify best practices and the implications for smaller competitors like WunderGraph.
---

00:11:01:10 - 00:11:21:15
Stefan
I don't think it can ever be boring. It's kind of fun, but. I mean, it's start ups. What's funny about a
startup? I'll give you guys a little hack when you're the the smaller one. You can do whatever
you want, because you can. It's like a big brother, you know, you can annoy your big brother,
your big brother, and your mom's like, okay, whatever.
00:11:21:15 - 00:11:37:06
Stefan
But as soon as the big brother punches down on you because you're small, everyone's like,
whoa, man. Whoa, what are you doing? So as long as we're the little brother, we can keep
doing this. And it's true. Like when, do you remember when Super Base was messing with
Google? It was like, good evening, sir, I'm from India.
00:11:37:06 - 00:12:07:16
Stefan
And how can we develop AI and robotics? Great. I was definitely not sure on that one, but we
can try to touch it. But today, today, what we're going to be going over is just the principles that
Apollo kind of published. Jens Walk me through this. Hold up. Let's start right here. This is
called principaled GraphQL. When did they build this by the way this was a while ago so written
by Jeff and Matt.
00:12:07:16 - 00:12:11:22
Stefan
So this is the CEO and the CTO.
00:12:11:24 - 00:12:24:13
Stefan
And to be honest this is a great idea. What they've written now. But Jens, you've probably read
this a couple more times more than I have. What what was the point of this?
00:12:24:16 - 00:12:49:09
Jens
So I think this is but by the way, can you take a note? I need to take a note. So, because we, we
need to rant more about Apollo. Strategy question mark. Okay. I wrote down strategy question
mark, because,
00:12:49:12 - 00:12:50:14
Stefan
I.
00:12:50:16 - 00:13:25:06
Jens
Yeah, I just remind me of strategy question mark. All right. So principled GraphQL I think in
general principled GraphQL. It's it's a fantastic idea. From the, from the two founders of, of
Apollo, essentially. And, I think this exists for many years and more or less, Matt and Jeff, they,
they created like ten principles to, to somehow.
00:13:25:08 - 00:13:34:14
Jens
Yeah, create like, like a strategy or to, to have, like, I don't know how you call this. Is it like a
memorandum or what kind of title would you give it but just.
00:13:34:14 - 00:13:36:29
Stefan
Say like, manifesto. Like.
00:13:37:01 - 00:14:07:29
Jens
Yeah, like a like a manifesto. Like, okay, follow these ten rules, guidelines, whatever. And then
you will have, you will do GraphQL the right way. That's, that's more or less it. And I think it
came at a time where Apollo was very much like leading, the, leading the space, like here. What
they say, like, over 90% of GraphQL implementations use their, their software.
00:14:08:06 - 00:14:33:00
Jens
By the way, this is actually like these days. It might even be true, but it's only true because
Apollo server and client and probably like almost everybody is using that. But I think the more
important question is like what what federation stack are people actually using? And like they
like this said, this is it's inspired by the 12 factor.
00:14:33:03 - 00:14:35:13
Jens
Do you know 12 factor?
00:14:35:15 - 00:14:38:29
Stefan
No, I just changed the screen. Can you see? Okay. Perfect.
00:14:38:29 - 00:15:10:12
Jens
So yeah, we said so when when I was younger 12 factor. It was like 1212 rules that that gave
you like a pretty good structure on how should you build microservices like, you know, how you
handle dependencies, how you do configuration and everything. And, yeah, it was like some
years ago. This was pretty decent. And I think, Matt and Jeff just they wanted to do a similar
thing for, for GraphQL.
00:15:10:12 - 00:15:13:10
Jens
So that makes sense. It makes sense.
00:15:13:13 - 00:15:33:07
Stefan
And so I like what you said though. So 90% of GraphQL implementations. You know, it's funny
though since 2015 I graduated high school in 2015. Yeah it is. They have been around for a
while. And so they have these. Let's go through the ten principles and then let's dive into the
one that you said that they're breaking, which is interesting.
00:15:33:09 - 00:15:41:10
Stefan
But let's start with one graph. So one graph your company should have one unified graph
instead of multiple graphs created by each team.
00:15:41:12 - 00:16:05:27
Jens
Yeah, that's that's, that's a funny one because, well, one thing that stands out immediately, by
the way, you can you can stay on the on the overview. I think that's easier for us to, to go
through. But if you stay on the overview, the first two points, one graph and federated
implementation as a company that's that, yeah.