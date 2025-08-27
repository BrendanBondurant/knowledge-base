---
title: From Architect to GraphQL Inspiration
slug: ep01-14-from-architect-to-graphql-inspiration
series: The Good Thing
episode: 1
chunk: 14
participants:
  - Jens
  - Stefan
segment: Promotion Networking and Early API Design
timecode: 00:42:46 – 00:46:53
start_time: 00:42:46
end_time: 00:46:53
speakers:
  - Jens
  - Stefan
topics:
  - Rapid Promotion
  - Networking and Appearance
  - Early API Design
  - Discovering GraphQL
  - BFF Pattern
  - Early Federation
tags:
  - graphql
  - api-design
  - bff-pattern
  - ai
  - federation
  - go
  - graphql-federation
  - kubernetes
  - rest
  - rest-apis
topic_tags:
  - graphql
  - api-design
  - federation
entities:
  - Jens Neuse
  - Stefan Avram
  - WunderGraph
  - GraphQL
  - openAPI
  - REST
  - BFF
  - Docker Swarm
  - Kubernetes
  - Imposters Handbook
mentions:
  - engineering lead promotion
  - handmade federation
  - GraphQL in 2015
  - career networking
  - backend for frontend
summary: Jens explains how his confidence and energy landed him an architect role
  and promotion to engineering lead in just a few years, even without senior-level
  experience. He credits networking, dressing professionally, and reading foundational
  books like Imposters Handbook. His interest shifted toward API architecture while
  working on a large news platform where REST endpoints were being updated repeatedly
  to support growing data needs. He discovered GraphQL in its early years and was
  drawn to its simplicity compared to REST. Jens reflects on how their BFF pattern
  functioned like handmade federation before formal GraphQL tooling existed.
---


00:42:46:28 - 00:42:54:25

Jens

And I can, yeah. And and, I felt like I should be an architect.00:42:54:27 - 00:42:56:16

Stefan

So crazy.

00:42:56:18 - 00:43:25:07

Jens

I, I applied for that, and then I, I got hired for, like, 84k or something, and then two years later,

they, they promoted me to to be the, like, the, the engineering lead. So I think with like three,

four years of experience, I was the, the engineering lead of, I think 20 people and not because

I'm like extremely good or something.

00:43:25:10 - 00:43:50:05

Jens

I think I wore the right kind of clothes, you know, I had my suits and everything, and and, yeah, I

think I, I was, I was networking with the right kind of people, you know, a lot of energy. That's

actually, like career advice. A lot of engineers. They are so into their code, which is not helping

their career.

00:43:50:07 - 00:44:12:01

Jens

If you want to make a career, you need to network. You need to you need to dress up. You need

to talk to the right people. And of course, I learned a lot. I read a lot of books like The Imposter. I

mean, if you if you now know my career, it makes sense to have the imposter handbook

because I was the absolute imposter.

00:44:12:04 - 00:44:44:14

Jens

But I, I learned a lot, and, Yeah. And, that that was how I, how I, was the architect. And then

engineering lead and the the the thing that that got me, got me or that I got stuck with this, APIs,

you know, we we had, like, multiple teams, and we were building, like, a news website from data

that was coming from, like, so many systems.

00:44:44:16 - 00:45:17:22

Jens

So how do you bring together all the data from all the systems? And so I was learning about

openAPI and how you can write specifications and, and how you can design Rest APIs. And I

was I was really fascinated by the idea that we can we can really think about design and we can

help teams collaborate to bring data together and that's that's kind of yeah, it it really fascinated

me.

00:45:17:22 - 00:45:43:13

Jens

It was at a time where, where Docker Swarm was new and Docker Swarm was fighting with,

with Kubernetes. And eventually it died kind of. And it was also the time where GraphQL, came

out in, I think, what was it, 2008 or I, I don't remember GraphQL was 2015 15.00:45:43:16 - 00:45:45:17

Stefan

Yeah, yeah. It's not like, yeah.

00:45:45:20 - 00:46:18:16

Jens

Yeah, 2015 makes sense. And yeah, I like GraphQL was really new. Like just one, two, three

years or something. And I, I really like the idea that, that we could use GraphQL on top of all our

data sources, and somehow just write a query and get whatever we need instead of, you know,

each time we we brought on, like a new data source, we had to update our REST API and we

had like a BFF pattern backend for front end.

00:46:18:18 - 00:46:53:15

Jens

And each time we had like a new data thing, whatever we needed, we need to to update this,

this BFF. And we had one BFF across like all all departments and it kind of like was our our

custom handmade federation, if you want to say so. And, yeah, I, I really got interested in the

idea of, of building like a, a GraphQL system or like a system in general, like GraphQL is

