---
title: Customer Patterns and Growth Pain
slug: ep17-02-customer-patterns-and-growth-pain
series: The Good Thing
episode: 17
chunk: 2
participants:
- Stefan
- Jens
segment: Customer patterns and organizational structures
timecode: 00:05:10 – 00:10:29
start_time: 00:05:10
end_time: 00:10:29
speakers:
- Stefan
- Jens
topics:
- Two-team compiler example
- Code proximity and change patterns
- WunderGraph's internal architecture structure
- Customer communication patterns and meeting structures
- API styles influence on Conway's Law
- Workflow alignment with organizational reality
tags:
- startup
topic_tags:
- customer-patterns
- code-organization
- team-communication
- architecture-design
- workflow-optimization
entities:
- Conway's Law
- WunderGraph
- GraphQL Go tools
- Router
- Engine
mentions:
- compiler with two teams example
- code that changes together
- limousine booking service example
- seven different systems complexity
- frontend button change workflow
summary: Jens explains Conway's Law through the classic two-team compiler example
  and discusses how code that changes together should be close together. He examines
  WunderGraph's own architecture showing the split between engine and router teams,
  and explores how customer communication patterns reflect their system architectures,
  questioning whether complex workflows that require changes across multiple systems
  actually support or hinder engineering productivity.
---

00:05:10:23 - 00:05:30:14
Jens
I think when I was first introduced to Conway's Law, there was an like an example. Let's say
you, you have two teams and they, they want to build a compiler. Well, what do you think? How
many steps will the compiler have?
00:05:30:17 - 00:05:34:29
Stefan
How many steps? If it's two teams, how many.
00:05:35:02 - 00:05:36:26
Jens
Get.
00:05:36:28 - 00:05:38:16
Stefan
Ten steps?
00:05:38:19 - 00:06:03:18
Jens
You said the number before. So yes. So and that's that's the interesting part. So at the very
beginning I didn't really understand what is the meaning. You know, I didn't have so much
experience yet and like, okay. Yeah, it's interesting two teams build a compiler, a compiler has
two steps. But but what does it mean?
00:06:03:20 - 00:06:33:28
Jens
And in reality, what I would say one, one pattern I learned in software development is, code that
changes together. It should be very close. And code that, doesn't change together. It should be
like further away. So for example, code that changes together all the time. It could be in a
package. It could also be in a function.
00:06:33:28 - 00:07:03:13
Jens
So the closer the code is together, the easier it is to change it together. For example, if you look
at our architecture, you can kind of see that we have somehow two teams, not one, but the two
we have, we have graphQL Go tools. We have the engine and we have the router. And you can
see there is a clear line between what does the engine do and what does the router do.
00:07:03:13 - 00:07:34:02
Jens
And so some modules you will see or some functionality. We do it in the router, some
functionality. We do it in the in the federation layer. And so yeah you kind of can see how the
way we shaped our organization, the way we kind of even if it wasn't really like a real split, but
somehow it was kind of a split in terms of communication because our engine team, it was
always a little bit like on the side.
00:07:34:05 - 00:08:06:02
Jens
And yeah, I think you can you can see that also in the, in the architectures. And then if, if you
look at our customers, I think one, one very interesting observation is, you can see the structure
of the architecture they built. You can see it in communication patterns. You can see it in, in
which people join on a, on a meeting, how they work together, how they, how they
communicate.
00:08:06:04 - 00:08:31:14
Jens
And, I think it's it's a very interesting problem. And also one observation we made is that
different API styles have an influence on, on how you can deal with Conway's Law. But before
we dive into that, I, I pause and maybe you have some, some other thoughts or, or questions.
00:08:31:16 - 00:08:57:15
Stefan
Well it's interesting. Like you say, it's a problem, and I know it's a problem. We can see it's a
problem with the companies that we work with. But like what what would be a good organization
structure where you wouldn't run into this problem because it just simply mirrors how you guys
communicate. And like, obviously the answer is with APIs and just having a good structure and
being able to communicate across teams with APIs.
00:08:57:15 - 00:09:05:28
Stefan
But have you seen from one of our customers maybe a good structure, that they have an
organizational structure that tends to work for them?
00:09:06:00 - 00:09:33:16
Jens
I wouldn't say per se, Conway's law is a problem. It's is more like, yeah, it, it it's it's more like the
reality. And so the, the question is, does your workflow fit this reality? For example, if you want
to make, let's say you, you build an app where people can, can book like, a limousine service or
something.
00:09:33:18 - 00:09:59:02
Jens
And let's say to add one single button to this front-end application, you have to make changes in
seven different places in seven different systems. And they are all like super complex. And you
have to talk to different people and whatnot. At this point, the question is, have we built a system
that prevents our engineers from making changes?
00:09:59:08 - 00:10:29:03
Jens
Because obviously you want to change your button, but if you have to change multiple systems
that are all over, does this code structure, does it support us in making changes to to this code
base? And, yeah, I think this is this is very tough. And you need, a lot of knowledge and seniority
to, to make changes in such a code base versus.