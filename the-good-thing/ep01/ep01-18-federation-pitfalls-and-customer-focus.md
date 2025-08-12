---
title: Federation Pitfalls and Customer Focus
slug: ep01-18-federation-pitfalls-and-customer-focus
series: The Good Thing
episode: 1
chunk: 18
participants:
  - Jens
  - Stefan
segment: Lessons from Building Cosmo and Avoiding Rewrites
timecode: 00:57:05 – 01:00:23
start_time: 00:57:05
end_time: 01:00:23
speakers:
  - Jens
  - Stefan
topics:
  - Build versus buy mistakes from inexperience
  - Federation platform complexity misunderstood
  - Cosmo as an evolving system with real depth
  - Danger of building feature by feature rewrites
  - Lightweight replacements that spiral into bad clones
  - Vendor trust and relying on infrastructure partners
  - Prioritizing customer value over internal engineering
tags:
  - graphql
  - api-design
topic_tags:
  - graphql
  - api-design
entities:
  - Jens Neuse
  - Stefan Avram
  - WunderGraph
  - Cosmo
  - Federation
  - Linear
mentions:
  - federation trap of rebuilding
  - customer focus over internal systems
  - vendor partnerships
  - schema registry and router minimalism
  - garbage rewrites of complete platforms
summary: Jens explains how many engineers reject vendor solutions like Cosmo because
  they seem too big or complex at first glance. But over time, as business requirements
  pile up, teams realize they are slowly recreating every feature they once thought
  they did not need. He emphasizes that federation systems like Cosmo reflect deep
  lessons gained over years of experience, and trying to replace them with a lightweight
  version typically results in failure. Instead of rebuilding, teams should partner
  with vendors and focus on what matters. For developers, that means prioritizing
  the customer over the thrill of internal systems work.
---




00:57:05:08 - 00:57:38:07

Jens

These were things that we we saw like, that's cool. We want to do this. And, and I think like

often times build versus buy is completely misled by inexperience. And I think it's so important to

get either you have this experience in-house or you get an external consultant who has built a

content management system or like, you know, if we if we make it specific in terms of federation.

00:57:38:09 - 00:58:18:26

Jens

So, we are we are a very big team working on, on Cosmo for more than a year now. I think how

long is it? Yeah, more than a year, a year and a half or something. And, our backlog is full. So

many things we can improve upon. But we have also built this huge knowledge base and

internal understanding of what is federation, how does it work and what's other things, are there

to come in the future and the, you know, the, the typical pitfall you run into is you're like, oh, I

look at Cosmo, it does too many things.

00:58:18:28 - 00:58:52:29

Jens

It's too big. I don't want this kind of big thing. This should be very lightweight. I, I just need a

router and a schema registry. That's what you think on day one. And then like, couple weekslater, you're like, okay, but we need this one extra thing, and then a week later we need this

other extra thing. And then over the course of a year, you build the, the, the absolute worst copy

of Cosmo, and you don't end up with, with the better or bigger or anything.

00:58:52:29 - 00:59:17:11

Jens

It's it's just garbage. Because the problem is you can't just look at something like, I don't know,

big content management system. And you're like, oh, it's too complex. It does too many things. I

don't like it. We build the simpler one. This is never going to happen because then two weeks

later, business side comes product manager. We need this one other thing.

00:59:17:11 - 00:59:43:21

Jens

And then then you add that and then you add more. And over time you realize, okay, our

architecture doesn't support that. If you're a vendor and you sell a federation platform, yes, of

course you need to have the expertise. You should be building that thing. But on our end, we're

relying on other partners. We have tools like like Linear.

00:59:43:22 - 01:00:05:11

Jens

We we have a partner, for infrastructure, for hosting. And there's. We don't do bare metal. We

have someone who who does that for us, who abstracts it away. And, really the most important

thing for a developer. Focus on your customer.

01:00:05:13 - 01:00:23:07

Stefan

I think that's huge. And, I just want to re-emphasize that that if you're in your career early, kind of

get away from the code. And I had this experience at my last job, so, they, they were asking me

to do these tickets, and I was just wondering, like, who actually asked for these? And I asked if I

