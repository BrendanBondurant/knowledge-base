---
type: podcast-chunk
title: Team Dynamics, Retreat, Cosmo Pivot, First Customers, and Luck
slug: ep06-16-team-dynamics-retreat-cosmo-pivot-customers-luck
series: The Good Thing
episode: 6
chunk: 16
segment: Team dynamics, retreat, Cosmo pivot, first customers, and luck
timecode: 00:55:10 - 01:03:21
start_time: 00:55:10
end_time: 01:03:21
speakers:
  - Jens
  - Stefan
topics:
  - Team Dynamics
  - Retreat
  - Cosmo Pivot
  - First Customers
  - Luck
summary: |
  Jens and Stefan discuss the dynamics of their team, the pivotal retreat that led to the Cosmo pivot, onboarding their first customers, and the role of luck in startup growth and product evolution.
tags:
  - cosmo
  - startup
  - go
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
  - Cosmo
---

00:55:10:15 - 00:55:47:06
Jens
So at least I had, I had to take away and, the, the overnight success from from Wunder Graph, it
came from me having this idea of building, the SDK, WunderGraph SDK when I worked at, tyk
technologies before. I wonder if, tyk Technologies is an API management solution. So, they offer
an API gateway, and I always thought a bit correlated to my, to my rant on this, connector
solution.
00:55:47:08 - 00:56:08:27
Jens
I always thought it's it's kind of stupid that you have a gateway. This gateway is connected to a
dashboard. So if I want to configure something on the gateway, I go to the dashboard. I make
changes in the dashboard in the user interface. And then I click save. And then it pushes this
config to the to the gateway.
00:56:08:27 - 00:56:38:14
Jens
And I thought that's that's a very unnatural workflow for a developer. I would ideally I could just
write code to. Yeah. To configure what the gateway should do. And I commit this code and then
it deploys and I don't need a dashboard I don't want to click buttons. The cool thing is if you put
your config in code, you have a history, you know what changed, etc. and you can propose
changes, you can review it and in a pull request you can test it.
00:56:38:15 - 00:57:03:03
Jens
You know what I just said. So that was the idea of the gateway, of the Wonder Graph SDK. And
yeah, I thought it's right. But, you can do so many mistakes in bringing an idea to market. We
were not successful. I'm honestly, I don't like. It's possible that if you started now, it would work.
00:57:03:03 - 00:57:09:19
Jens
Or maybe if you started it five years ago, it. Whatever. On our timeline, it didn't work.
00:57:09:19 - 00:57:11:22
Stefan
Didn't work.
00:57:11:24 - 00:57:40:07
Jens
But what it allows, allowed us to do is. So we built a GraphQL gateway. Not exactly. For
Federation, but a GraphQL gateway. And we made it open source. And so what happened is a
bunch of people came to us and said words about GraphQL federation. And they were
somehow upset with license changes from Apollo. But we were on our path.
00:57:40:07 - 00:57:58:25
Jens
We were we were not listening so well. We were on our path to the SDK, world. And the SDK
world shouldn't happen. And so there was like a pivotal moment in, in the summer two years
ago.
00:57:58:27 - 00:58:01:14
Stefan
June or July of 2023.
00:58:01:16 - 00:58:27:19
Jens
Yes. There was like a pivotal moment where the team was on a retreat. We sat together, we
figured out we're dead. We're running out of money, and we need to change. We need to pivot
and step back and, yeah. Do you remember? Yeah. Like Stefan opened. Like we will, you know,
we that we had, like a, like a big house.
00:58:27:19 - 00:58:47:14
Jens
Everybody was sitting somewhere. The mood was really bad. And Stefan had his notebook and
we were like, okay, Stefan, go through the, notes with customer calls. Before grain. Let's try to
find the last straw. Right? Yeah. So was cool. You can talk a bit about that situation.
00:58:47:16 - 00:59:04:02
Stefan
Yeah. So currently we use like grain and like circle back to record our customer calls. But before
then before like AI was able to transcribe it we use I use the red notebook I had a red notebook
and every customer call I would talk to the customer with the Jens and I would write down and
yeah, just sense, like we're sitting down.
00:59:04:03 - 00:59:27:18
Stefan
We're like, we're we're just throwing ideas out there. We're like, it's not going to work like
Cosmos Cloud won't work. We would have to get this many users. It's impossible. And, I'm
sitting there and we're going through my notebook and I have a red. The the book is red, and,
everything's written in black ink. And I took a highlighter, and I'm just going through the pages,
and I we did a lot of customer calls, though, in 2023, like before we even launched Cosmo.
00:59:27:20 - 00:59:47:07
Stefan
And I just kept noticing was federation. Federation. And so I'm going through the book and I'm
highlighting federation. I'm like, Jens, I think this is it. Look, they're all talking about federation.
And the three key pain points are I can't self-host my router. It's not open source. And there was
another reason. And yeah, I mean, it was crazy.
00:59:47:07 - 01:00:11:22
Stefan
It was crazy that all these people were telling us what they want. And it was popping up on
every single page. And Jens, explain a little bit, because I think the story is so cool, because
when we came to the retreat, it was great. The mood during the retreat wasn't the best because
we kind of realized we were dying, but when we left, we were like, okay, now I know what to do
and you can explain a little bit because we figured out what we needed to do.
01:00:11:24 - 01:00:14:12
Jens
Well.
01:00:14:14 - 01:00:20:05
Stefan
And David has his thoughts as well about what we were trying to sell.
01:00:20:07 - 01:00:21:21
Jens
Yeah, I think.
01:00:21:23 - 01:00:30:19
Stefan
Wait, one thing, one thing here. Who puts relish on a burger? That's a really weird thing to put
on a burger, David, I'm not a relish guy.
01:00:30:21 - 01:00:35:05
Jens
Continue. Yeah. Like,
01:00:35:07 - 01:00:36:04
Stefan
It's.
01:00:36:07 - 01:01:01:16
Jens
I, I so for me, I remember I had a bit of a hard time of letting go of the SDK. You know, I still
remember the first one two months. Like on the retreat. I was not fully convinced it for me, it was
more like, okay, that's that's our last opportunity. I know we have to do it. I don't like it.
01:01:01:18 - 01:01:29:00
Jens
And I remember for the next two months or so, I, I was really struggling because my, you know,
you're the technical founder, you you had the idea, you raised money. You wanted to prove to
your investor that you're right. And you have to admit that you're not right and you have to admit
to the team. That's the path you you have taken.
01:01:29:03 - 01:02:00:21
Jens
You know, you're you're the leader. You said, we go this way, and now you have to admit it was
a mistake. But I think in the, in the, in the, in the life of a leader, it's important to, to somehow
simply be realistic and say like, hey, what what we're doing, we're, we're, we're building cool
tech, but we're not really targeting a market where, where we can turn this into, into, into a
working company.
01:02:00:21 - 01:02:28:22
Jens
So it was a bit of a of a struggle for me. But the good thing is, yes, we are four co-founders.
Okay. And, one of our co-founders, Dustin, he's a little bit different. Like, you know, everybody's
different. And it's it's it's good to have like, diversity in the founder team. And I'm, in retrospect, I
really appreciate it.
01:02:28:22 - 01:02:55:07
Jens
Like, you know, Stefan, you and me, we have we have different skills. Bjorn, bring something to
the table. But Dustin, he's like, he's for one. He's like an engineer at heart. And also, he's an
amazing team player. So if everything falls apart, he somehow he or he can focus and he wants
to make it work. And he's he's like, I don't know he's carrying you.
01:02:55:07 - 01:03:21:19
Jens
You know, when when it's raining, when everything sucks, he, he keeps going. And the craziest
thing that's happened is like, you know, I was still in my in my shit. My idea sucks depression.
And two weeks after the retreat there was like a post from Dustin like, hey guys, I have prepared
the repository, and he was like, oh yeah, it's it's called Cosmo.