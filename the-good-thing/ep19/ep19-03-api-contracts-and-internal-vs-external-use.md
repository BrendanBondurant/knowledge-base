---
type: podcast-chunk
title: API Contracts and Internal vs External Use
slug: ep19-03-api-contracts-and-internal-vs-external-use
series: The Good Thing
episode: 19
chunk: 3
segment: API Architecture and Design Patterns
timecode: 00:10:10 – 00:15:13
start_time: 00:10:10
end_time: 00:15:13
speakers:
  - Stefan
  - Robert Farr
  - Jens
topics:
  - API Role at Procore
  - Internal vs External APIs
  - API Contracts and Governance
  - System Integration Patterns
tags:
  - api-design
  - contracts
  - governance
  - internal-apis
  - ai
  - go
  - rest
  - startup
  - software-governance
entities:
  - Procore
  - Robert Farr
  - Stefan Avram
  - Jens Neuse
summary: Discussion of API architecture at Procore, focusing on the role of APIs in
  large systems, differences between internal and external API design approaches,
  and the challenges of maintaining contracts in enterprise environments.
---

00:10:10:26 - 00:10:30:01
Stefan
So communication is important. The, the deadlines are important. The grid, you know, you're not
lugging around things, but still, there's a lot of stuff that you have to do with that. And so this is a
good segue into, like your role, at Pro Core. So you're a principal architect. What does that
entail? Like what are you tasked with architecting is it the entire Pro Core platform.
00:10:30:05 - 00:10:33:06
Stefan
What are you kind of specifically focusing on?
00:10:33:09 - 00:10:55:01
Robert Farr
Yeah. So I mean, my, my, so my primary focus of Pro Core is, is really, I would say trying to help
us, become a construction, platform. Right. Or a platform for construction on which to build. And
so that that takes me into a number of areas, right. It takes me in to, kind of our, our
infrastructure.
00:10:55:01 - 00:11:18:08
Robert Farr
Right. How do we think about scaling and building and managing, our customers data? It also
takes me into how we build services. You know, especially with all of the changes. So I'm
always trying to stay just a little bit ahead of the curve or enough ahead of the curve that I can
help guide us to where things are evolving.
00:11:18:10 - 00:11:35:12
Robert Farr
And, you know, we'll talk about AI more, here in a bit, but it's probably the biggest shift in, in
software engineering or in a lot of the industry at this point, at least in my career. You know, 20,
25 plus years. But, so I spent a lot of time there and then.
00:11:35:12 - 00:11:55:09
Robert Farr
And then what's the last part of that is really, you know, what are some of those core services,
the core entities, information architecture that makes us up and those kind of those pieces come
together to really say here in Harare, a platform company, you know, here's how we allow it to
be extended here, how we allow our customers to leverage and then build upon it.
00:11:55:11 - 00:11:59:24
Stefan
What? Well said. And I would sometimes I'll go ahead and
00:11:59:26 - 00:12:00:03
Robert Farr
In,
00:12:00:09 - 00:12:31:22
Jens
In a company like Procore, what role do APIs play and, and how does how does the company
high level think about APIs? Like what? Like if you asked the non-technical people in in
leadership, how do they, do they know APIs? Do they think about APIs who how? Yeah. Just
how do how do different stakeholders inside an organization like, like Procore think about APIs?
00:12:31:24 - 00:12:33:14
Stefan
It's a great question. By the way.
00:12:33:16 - 00:12:54:25
Robert Farr
It's it's a it's a great question. I, I'm going to say it, you know, really depends. And that's, that's
where, you know, when you look at how the software was built, how it's evolved over the years.
You know, we do have a very healthy marketplace and API ecosystem. So you can go to
developers, at procore.com.
00:12:54:27 - 00:13:17:06
Robert Farr
you can see that, so there is a component of Pro Core that's very interested in API contracts,
making sure that we can, you know, enable partner integrations and enable our customers
where they need to be. And then there's the other side where I think, you know, were more the
focus is on the application itself.
00:13:17:07 - 00:13:41:01
Robert Farr
Right? So whether that's, you know, building a particular, you know, web based workflow or a
mobile application where the APIs a lot of times I feel like are a secondary concern. Right. They
become a, a need based on trying to satisfy what you're trying to build or provide from a the
application experience.
00:13:41:03 - 00:14:09:03
Robert Farr
So it's kind of depends. Right? It depends on on where, you know, I guess the, the perspective
or context that somebody was in and how much they worry about APIs. I would say, you know,
those that like when we look at our developer ecosystem, it's much more concerning. I, as a
software architect, I generalize it more and to maybe, you know, I mean, APIs, but ultimately
APIs are contracts.
00:14:09:05 - 00:14:39:22
Robert Farr
And in any large software system, I think contracts are paramount. That is where you get
yourself into trouble, really quickly as you scale. And it's it's not a new idea, right? Like, it's, you
know, loose coupling, high cohesion. Right. Like, these are, these are concepts that have been
around for a long, long time. But they're hard to hard to adhere to at scale, especially when
you're going fast and, but ultimately, it's when you have tight coupling and loose cohesion, right?
00:14:39:22 - 00:14:47:03
Robert Farr
You really start to have to, what we say as tech debt or maintenance burden, that, kicks in as a
result as well.
00:14:47:04 - 00:14:58:05
Jens
So it sounds like you would you would not say procore is an API first company.
00:14:58:07 - 00:15:13:24
Robert Farr
I, I would, I would say no, not yet. And, just because that's where I think, you know, historically,
it's been more solution first and then ecosystem second.