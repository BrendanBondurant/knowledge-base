---
type: podcast-chunk
title: Business-Engineering Gaps and Stakeholder Issues
slug: ep28-07-business-engineering-gaps
series: The Good Thing
episode: 28
chunk: 7
segment: Bridging business-technical divides and identifying missing stakeholders
timecode: 00:44:00 – 00:51:12
start_time: 00:44:00
end_time: 00:51:12
speakers:
  - Jens
  - Stefan
  - Daniel Kocot
topics:
  - Business-Engineering Gaps
  - Missing Stakeholders
  - Prioritization Issues
tags:
  - consulting
  - stakeholder-management
  - api-design
entities:
  - Daniel Kocot
  - WunderGraph
summary: Discussion of disconnects between business and engineering teams, the impact of missing stakeholders, and strategies to improve alignment in API programs.
---
00:44:00:27 - 00:44:05:01
Stefan Avram
You can clip that clip. That right there.

00:44:05:02 - 00:44:34:24
Daniel Kocot
That's the thing a lot of, a lot of customers we are work with or prospects we talk to have a gateway or they don't have a gateway and have security issues because their APIs are not secure. But what should or should I should I use a gateway when I don't understand that there's a plugin engine into it that needs some kind of knowledge to, to, to move on and so on and so on.

00:44:34:24 - 00:45:03:16
Daniel Kocot
It's really it's really hard because, because the gateway is actually not an architectural tool. It's an infrastructure tool that's that's mostly interesting because we are just talking about the network traffic. We are we are putting through. So, so we removing from we building something by using infrastructure. And this is, this is since years the biggest gap we have there.

00:45:03:18 - 00:45:44:09
Daniel Kocot
And that there is a real misunderstanding. What what is what is actually needed it also what is about governance. Now you can still impress people by presenting linting for me that that shouldn't that shouldn't and use things somebody not should not, should should actually know when there is just a training. This this is for me the basic skill. So everybody should know that there are linters for API descriptions around, so that every API description can be linted, that there is testing, that I can test an API end to end, and so on and so on.

00:45:44:11 - 00:46:09:00
Daniel Kocot
For some people is also still the still mind blowing thing that that's possible. So you can impress people by just having micros running somewhere and in the end it's it's really and we see what happens there. So we are still talking about tooling, but we are not hitting, hitting the screen by saying, okay, how to get to a good API.

00:46:09:02 - 00:46:22:16
Daniel Kocot
Yeah, a lot of people then come up with, yeah, they are these guidelines. We use them, we just copied them. So we we do them. I use the Lando.

00:46:22:18 - 00:46:44:09
Daniel Kocot
Are you are you Google? Are you Microsoft? So get this as an inspiration and learn from others what what they did and build things on their own. So this is this is I think having tooling a lot. So you can you can have a lot of tools for everything. What you want to have. And there is the problem of adaptability.

00:46:44:13 - 00:47:16:24
Daniel Kocot
So people have to understand that a situation don't normally fit to their situation. What is what I saw somewhere else. Yeah. At a conference when somebody is presenting like a bang their API management solution by using Akamai and every possible tool in the market available to to to cover this API solution, that might not be the best fit for somebody listening to it, because they do it on different purposes.

00:47:16:24 - 00:47:41:23
Daniel Kocot
They do it because they have to they have regulations, they have to be redundant in geography and so on and so on and so on. But just to understand what is what is actually needed to to provide and maybe just use a proxy for the beginning, not the full blown solution. Yeah. Because you just want routing really understand what is what is really needed.

00:47:41:25 - 00:48:19:17
Daniel Kocot
And then from from that build build the things up and not just and not just say, okay, we start from the highest mountain possible. This makes the buy in into this solution into that solution. Because what what we do now with customers is building platforms. And platforms means to have a lot of tooling underneath the platform layer to really cover all the styles, to really cover all the things needed, but to make it not visible to the users because they get frustrated when they really see what is happening underneath the platform.

00:48:19:19 - 00:48:48:01
Daniel Kocot
And, and this is this is really the thing there to to have too much opportunities in tooling and not understand or have is this this is also one sentence. I always say we need the use cases. What use cases do you want to cover by using this integration style or what are your actual use cases you want to cover where you think an API?

00:48:48:03 - 00:48:51:29
Daniel Kocot
Whether STY could be helpful?

00:48:52:01 - 00:49:15:08
Daniel Kocot
And this is totally interesting. This is total hard for people to get there. But when you go into the business side, it's totally easy because the business tells you what they're actually need. They want to connect with other vendors, or they want to connect with other partners in their system, or they want to get some data from somebody.

00:49:15:08 - 00:49:42:22
Daniel Kocot
And, and enrich it and so on and so on. But when you when you go and onto the technical side, it's for them. Always hard to to say, okay, what are the use cases you want to cover with. With the integration platform you want to build and these, these these are, in my opinion, the, the problems and the challenges we have there to to really go, to really go that way down.

00:49:42:25 - 00:50:16:16
Jens Neuse
It it almost sounds like you present the problem, but you also kind of hint the solution. Get the business people on the same table with the engineers and have the business people explain. Yeah, what what what are the capabilities needed? Not writing endpoints, not writing GraphQL queries, writing down capabilities in plain English in post-its. And then thinking about okay, here are the capabilities we need.

00:50:16:18 - 00:50:35:21
Jens Neuse
How how could we implement that? Is this is this an event driven architecture? Do we need a Rest API for that? Do we need SDK s? This is something we should do with the query language but not be like okay, here's a here's a problem. What kind of GraphQL query will we build for that.

00:50:35:23 - 00:50:59:08
Daniel Kocot
Yeah. Or even just say, okay, we can just, we can just offer REST services. Yeah. This is this is this is the thing. Yeah. That's that's totally to the point to to really make them really make clear that there is conversation needed with within the organization. A lot of people always argue then. Yeah, we are talking with each other.

00:50:59:08 - 00:51:04:00
Daniel Kocot
Yeah. You talking not to the point because you don't want to.

00:51:04:07 - 00:51:12:11
Jens Neuse
Where's where's that gap. Why. Like it's so easy. Why why can't you bring the stakeholders together?

