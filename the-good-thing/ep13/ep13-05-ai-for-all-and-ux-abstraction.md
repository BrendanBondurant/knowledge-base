---
title: AI for All and UX Abstraction
slug: ep13-05-ai-for-all-and-ux-abstraction
series: The Good Thing
episode: 13
chunk: 5
participants:
  - Stefan
  - Jens
segment: Universal AI Adoption and User Experience Challenges
timecode: 00:14:46 – 00:19:22
start_time: 00:14:46
end_time: 00:19:22
speakers:
  - Stefan
  - Jens
topics:
  - Universal AI adoption at Shopify (all roles)
  - Small business AI adoption challenges
  - User experience abstraction for non-technical users
  - MCP configuration complexity
  - Cursor's rapid growth (0 to 200M ARR)
tags:
  - mcp
topic_tags:
  - universal-ai-adoption
  - small-business
  - user-experience
  - non-technical-users
  - cursor-growth
  - mcp-configuration
  - accessibility
entities:
  - Shopify
  - Cursor
  - Claude Desktop
  - MCP
  - QuickBooks
  - Dustin
mentions:
  - 1500 Shopify employees
  - HR, operations, legal departments
  - cruise ship analogy for big companies
  - Cursor's 200M ARR in 1.5 years
  - FOMO around AI adoption
  - Stefan's mother's pediatric clinic example
  - JSON configuration complexity
summary: Stefan discusses Shopify's mandate for all 1500+ employees across all departments
  to use AI, comparing large companies to cruise ships that need time to turn. They
  explore challenges of AI adoption for small businesses and non-technical users,
  using examples like Stefan's mother's pediatric clinic and the complexity of MCP
  configuration in Claude Desktop.
---

00:14:46:14 - 00:15:03:26
Stefan
Yeah. And I like what he said. There is like, what would this look like with autonomous AI
agents? We're already part of the team. It's what you said. Like, how can we do more with the
resources that we have? And then if you go a little bit further, this is amazing. Everyone means
everyone. So Shopify isn't just developers.
00:15:03:26 - 00:15:26:29
Stefan
You have a lot of different roles in there. So you have HR, you have operations, you have legal.
And what's amazing is now that everybody within the Shopify company, I think how many
employees they have, 1500 or something like that, is expected to be using AI. And what's great
is when leaders of big companies and we always say big companies like cruise ships, because
a cruise ship needs a couple miles to finally stop and turn.
00:15:27:01 - 00:15:41:29
Stefan
But he's putting this in front of them right now. He's saying, we need to get ahead of the curve.
And I'm going to be honest with you, Jens I think this is just one company that's about to follow
suit. You're going to start seeing every other company doing the exact same thing, and you're
also seeing it with companies like cursor.
00:15:41:29 - 00:15:58:18
Stefan
I mean, they went from 0 to 200 million ARR in like a year and a half. And it's because these
companies are open to adopting AI. Everybody is they're skipping their procurement. They're
jumping through everything to get AI into their company. Because I feel like it's a lot of FOMO. A
lot of companies don't want to get left behind on the on the AI train.
00:15:58:18 - 00:16:01:24
Stefan
What do you think?
00:16:01:26 - 00:16:29:26
Jens
I mean, if Shopify is doing it, it means the the the competition must follow almost. Yeah. I think
we will we will we will all get into this direction. And I think also we, we see it inside our own
company. A lot of people, a lot of our developers are using cursor now. Again, like there's parts
where it doesn't work.
00:16:29:29 - 00:16:50:10
Jens
For example, in our router, it is it is very hard to vibe codes. A query planner for GraphQL
federation. You you cannot easily do it, but, Yeah, for many cases, it's good. Yeah.
00:16:50:10 - 00:16:55:19
Stefan
Well, said and then final thoughts on this, this mandate that he put.
00:16:55:21 - 00:16:58:21
Jens
It to me, it's signaling that.
00:16:58:24 - 00:17:17:08
Stefan
The shift of the tide. But it's what you said. We're so early in on it. Like it's actually quite
amazing. And you said one thing is that people building business apps and I'm going to give you
like a real life example. So my mom, she has a pediatric clinic. She wants to build a dashboard,
let's say pre five years ago she would have to go and hire a developer.
00:17:17:08 - 00:17:35:00
Stefan
He would have to go to QuickBooks or whatever, integrate all that data, and then he would be
able to build a dashboard for her. It's long, it's expensive. It takes time. Now fast forward to
today. She could just talk to cursor or she could just talk to, let's say, claude right there. She
doesn't even have to go into an idea.
00:17:35:00 - 00:17:52:25
Stefan
She could just talk to it. Do you think, though, that, like, they can just prompt it already, but. Or is
it easier for us because we're developers that we kind of know how to talk to systems? Where
do you see the curve of like an average person, let's say a small business owner? How are they
going to interact with AI and like, how are they going to learn?
00:17:52:26 - 00:18:02:00
Stefan
Is it going to be like, you know, like taking classes of how to use the computer? It's like, okay,
this is how you talk to AI. This is the context that you give it. How do you see that going
forward?
00:18:02:27 - 00:18:28:11
Jens
I think it's going to be a bumpy road because we have so much knowledge for us. It's all simple.
But you know the first thing you just said, oh I can just go to QuickBooks and use the API. What
is an API like? Your mother will not understand. So yeah, I think the the first piece of the puzzle
is we need to.
00:18:28:12 - 00:18:54:17
Jens
So MCP is really cool. And I think there's a, there's a chance that we turn MCP into Lego bricks
where you can just say like, okay, MCP, let's say, let's just say it's it's like a little box or a
connector or a cable, and I can somehow plug it into my, into my claude desktop or whatever.
And, we currently see this is not yet the case.
00:18:54:17 - 00:19:21:12
Jens
For example, Dustin just showed showed us how do you enable MCP in Claude desktop? You
need to find the developer settings page. Then you enable MCP and then you open a Json file
where you have to put your cursor config, your, your mcp config. Yeah. I unfortunately that that
is not the experience we can, we can give to non-technical people.