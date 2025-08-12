---
title: Working Group Doubts and Federation Spec Concerns
slug: ep24-05-working-group-doubts
series: The Good Thing
episode: 24
chunk: 5
participants:
  - Stefan
  - Jens
segment: GraphQL Working Group Critique
timecode: 00:22:01:06 – 00:28:16:05
start_time: 00:22:01:06
end_time: 00:28:16:05
speakers:
  - Stefan
  - Jens
topics:
  - Curtis from Uber's federation blog post
  - GraphQL Foundation working group analysis
  - Hot Chocolate (ChilliCream) dominance in spec development
  - Federation spec collaboration concerns
  - Market adoption and Gartner hype cycle positioning
  - Alternative approaches to federation
tags:
  - federation
  - graphql-federation
  - grpc
  - graphql
  - graphql
  - startup
  - startup
entities:
  - Curtis (Uber)
  - GraphQL Foundation
  - ChilliCream
  - Hot Chocolate
  - Michael Staib
  - Pascal Senn
  - Switzerland
  - LinkedIn
  - Twitter
  - GitHub
mentions:
  - Curtis's federation blog post
  - collaborative effort claims
  - GitHub contribution analysis
  - Michael Staib and Pascal contributions
  - Swiss developers leading spec
  - trough of disillusionment
  - market impact considerations
  - thinking outside the box
  - removing GraphQL dependency
summary: |
  Stefan and Jens discuss Curtis from Uber's federation blog post and critique the GraphQL Foundation's working group. Jens reveals that despite claims of collaboration, the federation spec is primarily written by two developers from ChilliCream (Hot Chocolate), questioning whether reinventing federation is the right approach given its position in Gartner's trough of disillusionment.
---

00:22:01:06 - 00:22:05:29
Stefan
Yeah. No, we definitely should. So. Okay, I found the post. Give me a second, guys.
00:22:06:01 - 00:22:11:05
Jens
David, we're not ignoring the chat. We're just ignoring you.
00:22:11:07 - 00:22:18:29
Stefan
Yeah, there's a big difference. Yes. My keyboard. Yeah. Which is funny because I actually got a
keyboard that's not supposed to.
00:22:18:29 - 00:22:20:25
Jens
Do you have a mechanical keyboard?
00:22:20:28 - 00:22:24:07
Stefan
No, I have the Logitech one. Like it's supposed to be quiet, which I like.
00:22:24:07 - 00:22:27:12
Jens
Like I have this guy here. Do you see that?
00:22:27:14 - 00:22:32:09
Stefan
Oh, you have the, the the the when, the apple one.
00:22:32:12 - 00:22:34:01
Jens
Yeah, the little one.
00:22:34:04 - 00:22:49:15
Stefan
Okay, so this is the post. Curtis is a senior staff engineer. Uber. He's been talking about
GraphQL federation, and he wrote a really great blog post. Jens. Do you want me to jump into
the blog post? So we can kind of skim it? Or do you want to just give us like a high level
overview? And then we'll get to the comment?
00:22:49:17 - 00:23:11:05
Jens
I mean, it's it's complimentary to, to, what we say. You can post it on the, on the chat if you want.
And there's one comment, from someone from the, from the, GraphQL working group. Where
was it again? Is it still the.
00:23:11:07 - 00:23:12:14
(Mix)
I don't see it anymore.
00:23:12:17 - 00:23:20:23
Jens
You clicked most relevant. Is there also another way most recent.
00:23:20:25 - 00:23:27:20
(Mix)
Oh. Wow. Was it removed?
00:23:27:22 - 00:23:29:27
Stefan
Can you check on your side?
00:23:30:00 - 00:23:37:24
Jens
Yes.
00:23:37:26 - 00:23:40:22
Jens
I can still see it.
00:23:40:24 - 00:23:47:07
Stefan
Maybe I'm blocked. Did he block me?
00:23:47:10 - 00:23:54:21
Jens
I send you the link. On slack. DM. That would be so funny.
00:23:54:23 - 00:24:00:04
(Mix)
But, Oh, the.
00:24:00:07 - 00:24:02:23
Stefan
No, I don't see it. I think I'm blocked.
00:24:02:25 - 00:24:10:28
(Mix)
Shit. Why? Why are you such a dick? I don't know, I guess he blocked.
00:24:10:28 - 00:24:42:12
Jens
interesting. Okay. All right. Share your screen. Can you share it in chat? Wow. It's, it's actually
not so important, but I think that the gist is that so there is a working group from the GraphQL
foundation, and it's, it's, on its way to create a new Federation spec and, or. Yeah, it wants to
create the Federation spec under the GraphQL Foundation.
00:24:42:12 - 00:25:26:17
Jens
And it, it I think it's it's really like from a technical perspective, I see a lot of very smart aspects.
Like there's like they really try to solve hard problems. And I think from a technical point of view,
I think it's, it's it's a good idea and it makes sense. What I want to say from another perspective
is, I remember like, I don't know, some months, a year or whatever ago, I remember how
various vendors, were on stage together and they had discussions and they were very loud
about like, how this is a collaborative effort and how, also Apollo is, is working with this, this
group and helping and everything.
00:25:26:20 - 00:25:55:00
Jens
But what I figured out recently is I looked into this, the spec working group, and if you go to the
GitHub page and if you check the the contributions, if you're honest, this spec is written by chili
cream, and primarily Michael Staib and Pascal. I forgot the last name, but Pascal, something
two guys from, I think, Switzerland.
00:25:55:03 - 00:26:28:26
Jens
They are primarily writing the spec, and there might be other people joining meetings, but it
appears to me that the major work is being done by chili cream. So I'm not exactly sure how this
is a super collaborative effort or like it appears that theres just like one company pushing
behind. And like I said earlier with, what we're doing with with gRPC, our personal take is that
I'm not sure if we now like, Reinvent Federation.
00:26:28:26 - 00:26:57:10
Jens
I'm not sure how that will absolutely transform. Like, the market. If you look at the Gartner hype
cycle, for example, you can see that, like, GraphQL federation. It's not like on the, on the
trajectory to the, to the moon or something. It's it's somewhere close to the, to the, what's it
called? The the trough of disillusionment.
00:26:57:12 - 00:27:02:24
Stefan
Well, it actually started from up here, and then it just moved slightly down, but it's still in the
trough of disillusionment.
00:27:02:27 - 00:27:18:13
Jens
Yeah. And like I said earlier, there's on the technical side, there's good ideas there. But just on,
on, like what do you say like on the, on the market impact side.
00:27:18:16 - 00:27:20:22
(Mix)
Is it really is.
00:27:20:22 - 00:27:53:00
Jens
It really the right thing to, to now like put all this work into or. I don't know, maybe the real
challenge is somewhere else. Maybe the, the real problems are that it's maybe too hard or the
wrong approach. Or maybe we need to think outside the box and I would, I would argue like
thinking outside the box is we just remove GraphQL because maybe also one of the problems of
federation is that it's called GraphQL federation.
00:27:53:07 - 00:28:16:05
Jens
Maybe it should just be called federation. And we're maybe we're too tied to federation. And
then I'm also wondering like is it I don't know, do you have to solve every problem with GraphQL
or maybe there's like other specs or other ways where where it could just make the problem
simpler. So yeah.