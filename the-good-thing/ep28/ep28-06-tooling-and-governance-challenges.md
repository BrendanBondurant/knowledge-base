---
title: Tooling and Governance Challenges
slug: ep28-06-tooling-and-governance-challenges
series: The Good Thing
episode: 28
chunk: 6
segment: Misconceptions about tools, API governance hurdles, and platform complexity
timecode: 00:36:20 – 00:44:00
start_time: 00:36:20
end_time: 00:44:00
speakers:
  - Jens
  - Stefan
  - Daniel Kocot
topics:
  - API Tooling
  - Governance Challenges
  - Platform Complexity
tags:
  - api-governance
  - tooling
  - consulting
entities:
  - Daniel Kocot
  - WunderGraph
summary: Daniel discusses common misconceptions around API tooling, highlights governance challenges, and explores the complexity of enterprise API platforms.
---
00:36:20:14 - 00:36:50:13
Daniel Kocot
It's working good to to really describe capabilities and make them visible. Maybe it's a good idea to use this in the in the API space. Also in regards of this, AI thing that's that's coming up with MCP and A to A, because this will be more related to, to these type of protocols to to understand what, what is really the intent of this endpoint and not not just doing some kind of AI.

00:36:50:15 - 00:37:04:09
Daniel Kocot
It could do this or it could not do this. So, we, we, we use it somehow and maybe we find the right usage for that. So this is this is actually the idea behind this. And as I mentioned, it's at the beginning.

00:37:04:12 - 00:37:04:28
Stefan Avram


00:37:05:01 - 00:37:35:03
Daniel Kocot
So this is, this is something Kim Lane pointed at some post on LinkedIn from me in the, in the past day some, some stuff that has to be defined and so on and so on. This is what is quite interesting that there is a lot of, interest with the people who are really deep into the topic of APIs to, to really make it better for people to understand, because we are still from my opinion, not where we maybe can be to make to make it understandable.

00:37:35:03 - 00:38:01:11
Daniel Kocot
Because for most people, this is this is what we hear in the field is always, yeah, we have a management solution. Problem solved. But, you know it, I know it ,it's not buying something and using something if it is even having, having having your product running somewhere, it will not solve the problem of getting the things right in the end into this.

00:38:01:14 - 00:38:06:25
Daniel Kocot
This is something where we have really to look in and really bring the people to to that level.

00:38:06:25 - 00:38:13:04
Jens Neuse
Actually, by management you mean API management.

00:38:13:06 - 00:38:34:20
Daniel Kocot
It could be also event management or however we call it. So in the end we have to define what an API is. It could be also a GraphQL query or whatever. It's also some kind of interface to to to to see the the relevance. It's it's very for me it's quite hard to use this, this API term.

00:38:34:20 - 00:39:02:28
Daniel Kocot
So, that's why I talk always about interfaces. So it's, it's it's easier. It's not related to this, to this abbreviation of being misunderstood because maybe you meant something totally different by by saying it and it's, it's really in the end. And management is also, a big word. Yeah. Because nobody really defined what management of interfaces really means in the end.

00:39:02:28 - 00:39:12:07
Daniel Kocot
Because there is no clear defining some people think. It's about the lifecycle. Some people think it's about monetizing stuff and so on and so on.

00:39:12:09 - 00:39:29:26
Stefan Avram
But you know what this reminds me of? End. One time we were talking with a customer. We can't we can't say the name, but a very big and important customer in the United States. And we were asking them, what kind of tools are you using? And they said everything. And I was like, what do you mean? You're using everything we have, Kong.

00:39:29:26 - 00:39:50:11
Stefan Avram
We have WSL2   we have  Tyk, we have this, we have that. And I was like, or Jens was like, wait, wait, why do you have four API management tools? They were like, oh, because the first one didn't solve the problem. And I was like, wait, wait, wait, what? And we kept going through it. And every type of API tooling you could talk about, they were using that tool.

00:39:50:16 - 00:40:10:16
Stefan Avram
And then we asked them, what protocols are you guys supporting? Everything we said, like, is it from legacy and you're trying to modernize? No we tried. SOAP some teams build with rest. Some teams have dropped GraphQL. That's why we're talking to you guys now because of this. And it kind of like solves the point where you said in the beginning is that there isn't a tool that can solve this from the very beginning.

00:40:10:16 - 00:40:21:22
Stefan Avram
It was a people problem. And it's just so interesting to hear you say all that, because I have a fire drillgroup one second. But Jens, take over while I do this fire drill.

00:40:21:25 - 00:40:24:21
Jens Neuse
Do you have to do anything?

00:40:24:23 - 00:40:27:02
Stefan Avram
I just have to mute my camera so it doesn't ruin the stream.

00:40:27:02 - 00:40:41:16
Jens Neuse
Okay, okay. That's fine. Yeah. You know, this reminds me of, So. Well, I think for me, one of the coolest learnings is. So we we went through this wave of GraphQL hype, like, we're.

00:40:41:19 - 00:40:43:14
Stefan Avram
We're, we're.

00:40:43:16 - 00:41:11:26
Jens Neuse
We're slowly moving outside or expanding out of the, GraphQL space because we have we have actually learned ourselves that, APIs and GraphQL is, is a lot about people and process. Like for us, it was it took a couple of years, but even as a vendor, you can't just give people a tool. Like. But if you start talking to people like, what are the processes?

00:41:11:26 - 00:41:45:24
Jens Neuse
How do you actually create new APIs and this kind of thing? You kind of explored that the, there are, like you can give people an API gateway, but that's, that's not the solution. And so what what I found super interesting, when, when, when I was right in the middle of this GraphQL wave, like, couple of years ago, there was someone, like an API veteran, and he, he made, like, a, like, funny comment that I at the time, I, I couldn't fully grasp it.

00:41:45:27 - 00:42:09:18
Jens Neuse
Today I look a bit different on it. And he kind of said, if you have a shitty REST API landscape and you put GraphQL on top, like, yeah, now you have a shitty, shitty thing and you have a GraphQL, now you can query, your shitty thing. It's it's still a bad API. Their problem is not solved.

00:42:09:18 - 00:43:04:24
Jens Neuse
We've we've just added one more layer of complexity and and yeah, I, I really like your take that that you, you, you really try to, to help people. Looking at my speaker notes, because we, we always have amazing speaker notes. Jacob prepares, but, we we looked into some of your blog posts, and, if I look at some of the buzzwords that stand out, and also if I reflect on what I see in the in the community, a lot of people talking about MCP and AI and then as they do so and we, we kind of look at APIs, what, what, what everybody keeps talking about is governance and authorization, privacy,

00:43:05:00 - 00:43:31:12
Jens Neuse
these kind of topics. So I'm, I'm curious like from, from your perspective because you know, like everybody tries to do MCP andLLM and whatever and buzzwords and CEOs keep saying we can fire everybody because set alarm will take over the world. Well, we kind of figured out that's not the reality. But, from my perspective, there are a lot of really unsolved problems in the API space.

00:43:31:12 - 00:43:53:21
Jens Neuse
Like, we're we're not doing so great. And but I would love to to hear like your perspective. What are the the real big issues when when you go into into organizations like where where's the majority of of enterprises today and what are the the real big problems?

00:43:53:23 - 00:44:00:25
Daniel Kocot
The real big problems. They all have a gateway.

