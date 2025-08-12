
---
title: API Governance and Process-First Thinking
slug: ep25-04-api-governance-and-process-first-thinking
series: The Good Thing
episode: 25
chunk: 4
participants:
  - Stefan Avram
  - Jens Neuse
  - Kevin Swiber
segment: Enterprise API Governance Challenges
timecode: 00:14:05:28 – 00:18:28:28
start_time: 00:14:05:28
end_time: 00:18:28:28
speakers:
  - Stefan
  - Jens
  - Kevin
topics:
  - Enterprise API governance needs
  - Process before technology principle
  - Microservice landscape complexity management
  - API sprawl and duplication problems
  - Autonomous teams vs visibility trade-offs
tags:
  - ai
  - microservices
  - rest
  - api-governance
  - process-first
  - microservices-complexity
  - api-sprawl
  - autonomous-teams
  - enterprise-architecture
  - vendor-duplication
entities:
  - Fortune 500 companies
  - Enterprise architects
  - Microservices
  - REST API endpoints
  - Address verification APIs
  - LLM technology
  - Schema governance
mentions:
  - API governance as fundamental problem
  - Hundreds of services management
  - Tens of thousands of REST endpoints
  - People-process-technology priority
  - Seven address verification APIs example
  - Three different vendors for same service
  - Autonomous teams losing visibility
summary: |
  Stefan and Jens discuss how enterprise customers focus on fundamental API governance problems rather than cutting-edge AI. Jens explains the challenge of managing hundreds of microservices with tens of thousands of endpoints. Kevin emphasizes the "people, then process, then technology" principle, sharing examples of API sprawl where companies unknowingly have multiple duplicate services from different vendors due to lack of visibility from autonomous team structures.
---

00:14:05:28 - 00:14:20:22
Stefan
I think you're spot on. Like, I was talking to a couple of my buddies. They work at big enterprises
like fortune 500 companies. I'm like, oh, like, have you heard of cursor? Or they're like, what's
cursor? And I'm like, have you heard a lovable? They're like, what's lovable? And I'm like, have
you heard of ChatGPT? They're like, yeah, we just kind of started using it.
00:14:20:22 - 00:14:37:01
Stefan
And like, these are smart guys. But like, I think what you said is spot on. Like, we're kind of in a
bubble, like our own bubble. We're on the bleeding edge. We see this stuff. We see these crazy
rounds these valuations and everything. But when you back up and you go talk to actual normal
people, nobody actually sees that stuff, which is I think you nailed it on the head.
00:14:37:01 - 00:14:38:06
Stefan
There.
00:14:38:08 - 00:14:48:28
Kevin
Yeah. You know, like, did you see that there's a new dotnet runtime that released, you know, like
that's that's where they are. And we're like, no, actually, I didn't notice that at all. You know.
00:14:49:00 - 00:14:53:06
Stefan
It's so interesting. And then, go ahead. Jens, I think you had a question.
00:14:53:09 - 00:15:21:13
Jens
You know, when when I talk to our bigger customers, like bigger enterprises, and we're talking
to, like, an architect or someone like topics that they are interested in this, like they also look at
AI and things, and they are using Cursor like they are modern, but topics they are interested in
is things like API governance. Like how can we build a robust process to roll out API changes
and not break things?
00:15:21:13 - 00:15:54:21
Jens
And how can we collaborate better? Like very like I sometimes feel like there's so much AI noise
and there's fundamentals in the, in the API space that are not yet solved Well, like for example,
one, one big topic we're, we're working a lot on is how can we help people better collaborate on,
on API design and, how to how to implement APIs and how to structure them and best practices
and blueprints and these kind of things.
00:15:54:23 - 00:16:23:13
Jens
And, I wouldn't exactly say it's like the most exciting topic, but it's a very important problem to
solve. And there's not so great tooling to figure out, okay, if we have a microservice landscape
of of hundreds of services and potentially tens of thousands of of Rest API endpoints, how can
we manage that level of complexity? And you can't just take this whole thing and say like, okay,
here's like an LLM.
00:16:23:13 - 00:16:52:26
Jens
It figures it out. No, that's like, you can't solve every problem with fancy LLM tech. And there's
but from, from a messaging perspective, these are things where I would say the reality check is
schema governance, things like that. This is something enterprise architecture, architects think
about. And then you have this, this whole like, hey, I have five, five cursors running in parallel
and they co generate something.
00:16:52:26 - 00:16:57:23
Jens
And, yeah, for me it's to two realities.
00:16:57:26 - 00:17:21:27
Kevin
Yeah. It's something that, you know, really stuck with me. In my enterprise architecture days, is
this concept of having a priority, people then process, then technology. Right. When we put, like,
the technology first above the rest, we end up in a place like having, a bunch of APIs spread out
everywhere. A bunch of duplication.
00:17:21:27 - 00:17:43:20
Kevin
Nobody knows what the other person is doing. And, you know, we don't even have a good idea
of what APIs are out there, right? I work with tons of companies who are like, yeah, so we went
to this sort of autonomous teams, kind of approach where they got to do the development and
the deployment for themselves. And, you know, that's that's kind of worked out.
00:17:43:23 - 00:18:01:03
Kevin
But now we have no visibility into what any of these teams are doing. And we have seven
address verification APIs, and we're paying vendors on the back end for this. Right. Like we've
got three different vendors for address verification that we have APIs on top of, you know, how
do we how do we get out of this mess?
00:18:01:06 - 00:18:21:07
Kevin
And so it's been it's been interesting to kind of take a step back and, and go to the process and
not just look at, oh, let's do microservices everywhere. Let's have autonomous teams. But like,
let's go back to the process of, how do we actually launch software here? And, you know, how
do we get the most out of the investments we've already made?
00:18:21:09 - 00:18:28:26
Kevin
And how do we get kind of a handle on, on the API sprawl that's happened in our organization,
right?