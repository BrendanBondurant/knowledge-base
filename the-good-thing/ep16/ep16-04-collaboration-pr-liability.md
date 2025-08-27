---
title: Open Source Community Collaboration and PR Maintenance Challenges
slug: ep16-04-collaboration-pr-liability
series: The Good Thing
episode: 16
chunk: 4
participants:
  - Stefan
  - Jens
segment: Open Source Community Management
timecode: 00:14:09 – 00:21:10
start_time: 00:14:09
end_time: 00:21:10
speakers:
  - Stefan
  - Jens
topics:
  - Open Source Maintenance
  - Community Collaboration
  - Pull Request Challenges
  - Contributor Expectations
tags:
  - federation
  - graphql-federation
  - ai
  - open-source
  - cosmo
  - cosmo-router
  - go
  - graphql
  - rest
  - startup
topic_tags:
  - open-source
  - federation
  - graphql-federation
entities:
  - Discord
  - Cosmo
  - GraphQL Go Tools
mentions:
  - "My time is not free" open source principle
  - Discord as documentation search replacement
  - AI search tool for documentation
  - Seven years maintaining GraphQL Go Tools
  - Frank's comment about maintainer responsibilities
summary: |
  Jens discusses the challenges of open source community management, emphasizing that while code is free, maintainer time is not. He distinguishes between valuable collaboration questions and lazy documentation searches, explaining the burden of maintaining pull requests and external contributions. The discussion covers the demanding nature of long-term open source maintenance spanning over seven years.
---

00:14:09:09 - 00:14:34:07
Jens
What? What is not open source? Is someone coming to us saying, hey, I demand that you teach
me how to use this software. This this has nothing to do with open source. And some people
have a misunderstanding that just because I made it open source, just because it appears to be
free, it doesn't mean that my time is free.
00:14:34:09 - 00:14:58:12
Jens
You need to pay for my time. So if you want to have my time, then I don't know, consult our our
sales team. If you want to have our our hosted service, consult our our, sales team. If you have
a question and you come to the to the discord and you want to collaborate with others, you
know, there's also there's two categories of questions.
00:14:58:18 - 00:15:22:28
Jens
There's one question where where someone asks, for example. And this is something I'm very
happy to do. Someone comes to the discord and ask like, hey, do you have some some ideas?
Or can you share some strategies? How how do I do certain things with Federation? Right? And
I'm happy to share experiences on what we're doing with with other customers and how we're
dealing with this.
00:15:23:01 - 00:15:45:13
Jens
This is something I'm super happy to talk about. Something that people absolutely love to do is
they, they think discord is the search function for our docs. And instead of searching in the docs,
they just ask a question on discord, like, can you not just ask in the docs or like search the docs
we have like AI search on the docs?
00:15:45:13 - 00:16:26:10
Jens
It is very helpful. Super good tool. So and then there's people and this is yeah, I, I, I being
German, I should not directly translated to English, but some one thing I really don't like is
people really and I mean it literally demanding that I do something for them. And this is just not,
not possible. We don't have a business relationship and and even, you know, and this is the
thing, people who pay us, who have an enterprise plan, they are not as demanding as some
people on, on a free discord or something.
00:16:26:10 - 00:16:33:09
Jens
And that's, I don't know, some, I'm not sure what's going on, but yeah, this is something that's
like.
00:16:33:11 - 00:16:51:11
Stefan
There's a meme about that. Like, you have a customer that's paying you five bucks a month,
and they're demanding. They're screaming, they're asking, hey, what's the return policy? Then
you have the customer paying you 5000 a month, and he's just like, yeah, okay, see you next
invoice. And he's totally fine. And it's because there's a different allocation of value there.
00:16:51:13 - 00:17:11:10
Stefan
And then the other point I want to add is, there's a couple points you might have missed. And
the open source is like, we've created something, we've distributed it, we're maintaining it, we're
keeping it in a good state. We're constantly adding features to it all for free, and you have no
interest in contributing to it or in supporting the company financially.
00:17:11:10 - 00:17:28:17
Stefan
But you're demanding for help. Like, come on, man, that's like a clear imbalance is that there's a
little bit of abuse there. And we see it a lot in open source is that somebody will come and they'll
drop their big logo there, say, hey, we're interested in using you guys, but we need this, this and
this. We say, great, let's talk sales.
00:17:28:19 - 00:17:47:24
Stefan
Oh, we don't want to pay anything, okay. Do you want to contribute to it and implement those
features? No, we want you to do it. And it's like, wait, I'm so confused. Like where's the
relationship here doesn't it? It sounds almost like abusive. I'm a little confused. And then the
second part is that people don't understand is, open source is not free because it requires
maintenance.
00:17:47:27 - 00:18:06:21
Stefan
It requires collaboration from other teams. We have to properly make sure that all of our code is
done correctly. We have detailed tests and everything, and it's because there are big companies
relying on this software. And so another issue that I see is, okay, I made a PR, why are you not
merging my PR Jens? I made a PR, I contributed to open source.
00:18:06:24 - 00:18:09:05
Stefan
Why are you not? Why not merging my PR?
00:18:09:08 - 00:18:15:03
Jens
It's not my priority. Not. It's not mine.
00:18:15:06 - 00:18:16:24
Stefan
And so I don't.
00:18:16:24 - 00:18:42:28
Jens
Even mean this in a negative way. It is simply you want to make changes to the software. And I
have customers and I maintain the software on the behalf of my customers. Maybe there's
overlap between your goals and my goals. Maybe there is no overlap. And at the end of the day,
I'm responsible for our resources and our time.
00:18:42:28 - 00:19:09:22
Jens
And yeah, if you find a security bug, it might be our highest priority if you want to add a feature
that you need, but we don't need, and none of our customers needs them. It's. And again, I'm
not saying this in a, in a negative way. Just just think about it. Like if the software was closed
source, then yeah, the collaboration would not be possible.
00:19:09:22 - 00:19:25:26
Jens
And you also need to think about if you create a pull request and you merge it. No. You create a
pull request, we review it, we merge it. Who's liability is the code now?
00:19:25:28 - 00:19:34:29
Stefan
Yeah, I was going to say that like you're taking on risk by taking in the PR and you have to you
we're taking on the liability. It's us. Now if we take in that PR.
00:19:35:02 - 00:20:03:04
Jens
You know, let's think about like let's say you have you have a cosmo router and someone says, I
have an amazing feature and I make a pull request. I add this for free. I even add tests here.
You go. And by adding this code, future refactors of the router are now more complex because
the code base just got more complexity.
00:20:03:07 - 00:20:37:19
Jens
So this is also something sometimes people think if they contribute something, they, they, they
give their time. And we should be just thankful and accept it. And why are we not merging it?
And, so the problem now is if we merge it, it is it is now our burden because we have to
maintain it because let's say we merge your code and we have a customer that now uses this
code.
00:20:37:22 - 00:21:10:12
Jens
So now the customer depends on us of making it right. We cannot do like a sloppy job in
merging it fast or not reviewing it properly. Because if a customer now uses it, it must follow the
same standards. So we need to spend time like is this the right architecture? Is it? And you
know, if we would have built it ourselves, it is quite likely that we we would have gone through
like an RFC process or something where we internally discussed like, here are three
approaches we could take.