---
type: podcast-chunk
title: Engineering-Led Support and Early Challenges
slug: ep29-01-intro-and-engineering-led-support
series: The Good Thing
episode: 29
chunk: 1
segment: Engineering-Led Support and Early Challenges
timecode: 00:00:23 – 00:06:05
start_time: 00:00:23
end_time: 00:06:05
speakers:
  - Stefan
  - Jens
  - Viola
topics:
  - Engineering Rotations
  - Early Customer Support
  - Scaling Challenges
tags:
  - startup
  - observability
  - governance
entities:
  - WunderGraph
  - The Good Thing
summary: |
  Viola joins the show to share how customer support began as an engineering-led rotation at WunderGraph. She explains how this model helped early on but became unsustainable as the company scaled, leading to issues with context switching and inconsistent ownership. The group discusses lessons from this phase and why scaling customer success required structural change.
---


00:00:23:12 - 00:00:34:00
Stefan
And we're live. Welcome back, ladies and gentlemen, to another episode of The Good Thing.
I'm joined by always my co-host Jens. And today we have a very special guest. Viola, viola,
welcome to the podcast.

00:00:34:03 - 00:00:35:14
Viola
Thanks for having me.

00:00:35:16 - 00:00:56:07
Stefan
Of course, for those of you that don't know, viola, you're probably not one of our customers. But
for one of you that do. Viola is our amazing customer success manager. Today we're doing
something a little bit different. We're talking about how customer success is actually part of the
product. And so we thought we'd bring viola on and talk a little bit about how we do customer
success over here at Wunder Graph.

00:00:56:10 - 00:01:10:00
Stefan
And just for some context, so viola joined us in 2015. She's currently our only customer success
manager, and she's spearheading 2015. Oh my God, you're right. 2025. Sorry. That was a
Freudian slip by somebody yet.

00:01:10:03 - 00:01:10:12
Jens
Somebody is not yet 10 years old

00:01:10:12 - 00:01:31:07
Stefan
Yeah, so feels like it. I've been around here for so long that I'm just like, oh, my God. So viola
joined us very recently, 2025 as our first CSM hire. She has a background in solutions
engineering and UX research. She was previously at patch. And funny enough, Tyk, for those of
you that know the history of Tyk and Jens is also from Tyk and Jens, worked together with viola
at Tyk.

00:01:31:07 - 00:01:35:13
Stefan
He recommended her so viola that I missed anything on that introduction.

00:01:35:15 - 00:01:44:05
Viola
No, that was great. And yeah, it's been, a few months, but it's been a few intense months, so
yeah, they feel a little bit longer than that.

00:01:44:06 - 00:02:03:10
Stefan
And, and it's, it's actually my high school graduation year, so thank you. The other day I was
watching, like, on TikTok and, somebody made like an old video of, like, high school back in
2015. And they made it look like it was from the 90s. And I was like, Holy shit, am I that old
now? But yeah, I guess it's my ten year reunion in high school.

00:02:03:17 - 00:02:09:04
Jens
David, what makes you think that Stefan is already ten years old?

00:02:09:07 - 00:02:25:21
Stefan
I don't know. That was a good one. I go with David. All right. So cool. Viola, today we're going to
be talking about how we do customer success. One of the things that I'm excited about is
basically kind of the rotation that you've set up, the process that we used to have before and just
your background on that.

00:02:25:24 - 00:02:42:26
Stefan
So to kind of kick things off, one of the questions that I have is how do we currently do Customer
success at wynder Graph, and I want you to kind of explain it for the audience, and then we can
kind of go deeper into it. But as soon as we sign a contract, what do we kind of kick off for our
customers?

00:02:42:28 - 00:02:45:24
Jens
Oh, can I, can I interject because.

00:02:45:27 - 00:02:46:29
Stefan
We go.

00:02:47:01 - 00:02:53:04
Jens
Well, what I would find interesting is so, viola, how long are you with us now?

00:02:53:06 - 00:02:54:21
Viola
I think almost six months. Yeah.

00:02:54:26 - 00:03:12:16
Jens
Six months. Yeah. I would love to hear a little bit. And you can be honest. It's fine. We we we
can, we can live with that. But, you know, before you work with us, we, we kind of did everything
ourselves. And then maybe you can explain a little bit the journey. What did you find when you
joined us?

00:03:12:16 - 00:03:29:25
Jens
And how did you make that whole thing successful and scalable to, to where we are now?
Because I, I would love to hear a little bit the, the story like, well, what did you think in, in like the
first one two weeks and how did you professionalize that.

00:03:29:28 - 00:03:31:13
Stefan
And be honest.

00:03:31:15 - 00:03:59:21
Viola
Always. Yeah. So when I, when I joined, wundergraph, I think I found a team that's, you know,
super passionate. The engineering culture is permeates the company. And so a lot of the
support, a lot of the customer interactions are and some of them still are engineering lead. So
that meant that people that worked on product, would also answer customer queries.

00:03:59:21 - 00:04:31:17
Viola
And it would be an extremely efficient, process for the customers because quite literally, the
people that would build the code were the ones answering any queries, any feature requests,
any bugs. So, you know, that was incredible to see that at such scale. We are we're delivering a
great experience for the customers whilst also innovating. And that is a little bit the beauty and
the pain of start ups when you kind of have to figure things out as you go along.

00:04:31:19 - 00:05:09:05
Viola
You do a lot of things, you know, on your plate and you try to still support customers in a way
that, you would want to be supported because, again, we are delivering software that is utilized
by engineering, like yourselves. But had that had some, drawbacks, which meant that
engineering, engineering that was building product also had to sort of be part of this, support
rotation, which meant, of course they, alternating weeks where they would be on customer calls.

00:05:09:08 - 00:05:30:00
Viola
But it also indicated a lot of context switch. So, you know, having to jump on customer queries,
that would come in and having to always check, this customer channels to see if something new
is popping on. Figuring things out within your rota is also a big, you know, commitment and can
be a stressor for an engineer.

00:05:30:00 - 00:06:05:24
Viola
That's trying to also advance this product work. And so I think we figured out very, you know,
very efficiently that moving forward in this pattern might not be sustainable. It's the growth that
we have experienced. And, the context switch eventually becomes a bit untenable because you
either have to be extremely organized and figure things out very quickly, during your rotation, or
you kind of have to jump back and forth after your rotation to support the next engineer on call,
which can create a bit of a, you know, inefficient pattern.

00:06:05:26 - 00:06:35:21
Viola
And, in the worst case scenario could also mean that, you know, information is repeated, but
also information is missed. In the end overs. So yeah, I saw that, and at the same time, I think I
saw a great opportunity for us to carve out a little bit of that, support function to dedicate
resources that we could absolutely give and, focus on the customer, and eventually rotate out,
periodically.

00:06:35:28 - 00:06:45:22
Viola
But some are more, and it's something I was more sustainable, I think, for, for us as, where we
are as a company does that resonate with you guys?
