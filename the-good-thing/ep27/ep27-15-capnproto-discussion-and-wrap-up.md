---
title: Cap’n Proto Discussion and Wrap-Up
slug: ep27-15-capnproto-discussion-and-wrap-up
series: The Good Thing
episode: 27
chunk: 15
segment: Technology evaluation and episode conclusion
timecode: 01:03:41 – 01:07:48
start_time: 01:03:41
end_time: 01:07:48
speakers:
  - Jens
  - Stefan
topics:
  - Cap’n Proto
  - Technology Choices
  - Episode Wrap-Up
tags:
  - capnproto
  - tech-evaluation
  - graphql
entities:
  - Cap’n Proto
  - WunderGraph
summary: Closing discussion on evaluating Cap’n Proto, lessons from technology choices, and wrapping up the session with final insights.
---
00:59:06:10 - 00:59:08:25
Jens
Okay. Awesome stuff.
00:59:08:28 - 00:59:12:19
Dustin
Good that Ludwig is back.
00:59:12:21 - 00:59:33:10
Jens
Then. Then we will do one, one round of something you're proud of. And then if you're, if you're,
if you're, if you think that's funny in the end, you can ask me because I was just moderating all
the time. You can ask me, like, one weird question. If you have a weird question for me, think
about it.
00:59:33:12 - 00:59:47:24
Jens
But starting with Ludwig, anything you're proud of, except like, your amazing teammates and
what we have accomplished. And,
00:59:47:26 - 00:59:49:00
Ludwig
That was actually.
00:59:49:03 - 00:59:52:28
Jens
Sort of of proud of the best CEO, right?
00:59:53:00 - 01:00:23:04
Ludwig
Of course. And then the very best CEO. Yeah. Do you get a raise now? I actually wanted to say
I was super proud of, the whole collaboration. Like, in the beginning, we had a super tight,
schedule when we wanted to have our first version released. I could not have done that alone.
And I got massive support from from Dustin and from Jesse, from other people also involved
that who really helped me with some designing things.
01:00:23:04 - 01:00:43:19
Ludwig
And really, I think the whole this whole project was, is a really fun thing. It makes me wake up in
the morning feel like, yeah, I'm really enjoying what I'm doing. I mean, that's something a lot of
people don't have when they go to work. And like, I was just another workday and I'm working.
I'm like, I'm super excited to see what's coming next.
01:00:43:21 - 01:01:20:09
Jens
Which is a great point. Like if you if you like people like Ludwig, Jesse and Dustin and like,
yeah, you if you can cope with me then then maybe wundergraph is a is a cool place because I
think we have really cool, smart people. It's it's very enjoyable. And then, to work together, we
have super interesting problems like what we just talked about, like, I, I would love to have more
time on on actually hacking on it, but, yeah, I also need to do other things.
01:01:20:12 - 01:01:28:05
Jens
Cool. Thank you, thank you. Ludwig, that was fun. And, Jesse, anything you're you're proud of
or something cool you work on.
01:01:28:07 - 01:01:46:18
Jesse
So one thing that I'm proud of for the team we worked on, on connect is that I have a nice
calendar diagram on my other screen here from five months ago. This was before any code was
written for anything here. And this was Ludwig, and I sitting in a slack huddle trying to figure out
how this is going to work.
01:01:46:20 - 01:02:07:23
Jesse
And if we look at this diagram now and how it actually ended up working, there's like nothing
different. So I think we did actually a really good job of architecting it from day one so that we
weren't, just stepping on our own feet or constantly messing up how we were going to
implement this. We weren't like vibe coding our way through it and constantly having to rewrite
things.
01:02:07:25 - 01:02:18:18
Jesse
I think we did a good job planning and executing, a product that functionally works in production,
and solves the, the use case. It was designed to.
01:02:18:20 - 01:02:49:08
Jens
Respect, like the, the, the in German, the, the the, the biggest level of appreciation. You can get
it. It's, not bad. Like, it's pretty good. Okay, cool. So you see, we, we have, we have good
collaboration. We have, good architects. Dustin. What, what any. Well, what are your highlights
of the last couple of months?
01:02:49:10 - 01:02:50:25
Jens
01:02:50:27 - 01:03:28:15
Dustin
Yeah. I have to repeat, I think, I mean, I think you can you can solve anything. I think tech is not
not not that important, but you need to. You need to have the right people. And I think this is the
most critical one. If you have people who are, curious and have the right attitude and are hungry
and then also can work in a team which is also not given, is then you have everything you need
as a CTO to operate, such an, project and, yeah, I, I tried very hard to, to, to, to, to be part of it.
01:03:28:15 - 01:03:41:14
Dustin
I did some work on the photographic library, but I was more or less like a, like a, like a rubber
duck and an architect on that side. And, yeah, the team did a fantastic job.
01:03:41:16 - 01:03:55:28
Jens
This is what you want to hear from, from a CTO who cares about, the team and and the people.
Cool. Awesome. This was a cool session. Has anybody come up with a weird question?
01:03:56:00 - 01:03:59:27
Jesse
Why did we use gRPC and not Captain Proto?
01:04:00:00 - 01:04:22:12
Jens
Oh, this is this is actually not a super weird question. So if you don't know Captain Proto, I'm
actually a fan of Captain Proto. If you, you should definitely read about Captain Proto, because.
And by the way, this was not like just the. And I didn't set this up like this is, this is free for all.
So, backstory of Captain Proto.
01:04:22:18 - 01:04:39:10
Jens
So, what did I want to say? Yeah. Cloudflare. Cloudflare workers is, using captain proto behind
the scenes. They have something it's called, what was it again? distributed object, like the
what's it called? Something and then.
01:04:39:12 - 01:04:39:28
Jesse
01:04:40:00 - 01:05:12:19
Jens
D1 D1 okay. Yeah. They have this, this cool concept of distributed objects, which are yeah. Like
like singletons and they can move around the globe. And essentially they are kept in proto
objects. And the cool thing, like Captain Proto is like a different, like a different way of thinking
about network programs because instead of instead of, calling a service and it it gives you
something back.
01:05:12:19 - 01:05:41:07
Jens
It's more like you have a distributed object that lives somewhere and you can call functions on it,
and you can also chain function calls. You can say, I don't know. Show me the, the prices of
products. And when you have the prices, then give me, I don't know, the shipping estimate or
something. And you can actually send this in one message as a chain and it will operate on this
distributed object one by one.
01:05:41:07 - 01:06:00:28
Jens
And then it will give you back the response. So you you can send multiple operations to this
object as one request. And then you get back the response. You don't have to go like multiple
roundtrip. So capn proto pretty cool. Why did we not use it? I actually wanted to use it in the
beginning, but I was worried about ecosystem.
01:06:01:00 - 01:06:34:14
Jens
So I thought like if we do like an exotic ecosystem thing, then yeah, maybe we, we end up with,
I don't know, like not many people will adopt it. So I thought, okay, let's go mainstream, let's go
gRPC. And that's that's fine. Good. Then last question from David Stutt. Why did you come into
daily yesterday with a huge cake that you finished by the end of the daily.
01:06:34:16 - 01:06:55:00
Jens
I don't know, like if you have. cake. You want to eat it, right. So why did I come? I come I came
in to the daily because my my mother in law, she's the absolute best. She made cake, and I like
cake, so I, I yeah, I had my cake and eat it too. Exactly. I think that's awesome.
01:06:55:01 - 01:06:56:21
Dustin
Closing words.
01:06:56:23 - 01:07:18:07
Jens
Yes. Okay, so next week our beloved Stefan is back again. But I have to say, this was an
awesome session we had. Very good. I don't know if you see it, but we had very good numbers
in, in viewers and people stayed. So it was interesting. That's a good learning, Jacob. I hope
you can clip some stuff.
01:07:18:07 - 01:07:39:27
Jens
Hopefully we we have some some good rants or whatever. Guys. Ludwig. Jesse, Dustin. Thank
you so much. This was a good session. And Dustin how do I do it again on sec, I Dustin do you
know what the good thing is? Jesse do you know what the good thing is?
01:07:40:03 - 01:07:44:16
Dustin
A podcast that we are online next week.
01:07:44:19 - 01:07:48:12
Jens
Thank you. Ciao Guys. That's it.
01:07:48:14 - 01:07:49:10
Ludwig
See you.
01:07:49:12 - 01:07:49:21
Dustin
Bye