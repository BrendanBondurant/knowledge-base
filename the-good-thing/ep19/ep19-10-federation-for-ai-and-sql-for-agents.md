---
title: Federation for AI and SQL for Agents
slug: ep19-10-federation-for-ai-and-sql-for-agents
series: The Good Thing
episode: 19
chunk: 10
participants:
- Stefan
- Robert Farr
- Jens
segment: AI Integration and Federation
timecode: 00:47:02 – 00:52:08
start_time: 00:47:02
end_time: 00:52:08
speakers:
- Stefan
- Robert Farr
- Jens
topics:
- Federation's role in enabling AI systems
- Structured contracts for AI integration
- GraphQL as SQL for AI agents
- AI-driven API consumption patterns
tags:
- federation
- ai
topic_tags:
- federation
- ai
- ai-integration
entities:
- Robert Farr
- Stefan Avram
- Jens Neuse
- GraphQL Federation
- AI agents
mentions:
- Federation enabling AI systems
- Structured contract benefits
- GraphQL as query language for agents
- AI consumption patterns
summary: Exploration of how federation enables AI systems through structured contracts,
  discussing the concept of GraphQL as SQL for AI agents and new patterns of AI-driven
  API consumption.
---

00:47:02:20 - 00:47:04:25
Robert Farr
Yeah.
00:47:04:27 - 00:47:09:07
Jens
You you kind of destroyed it. But,
00:47:09:09 - 00:47:14:28
Stefan
Robert, how what did I destroy my day?
00:47:15:00 - 00:47:16:27
Robert Farr
Yeah. No.
00:47:17:00 - 00:47:26:04
Jens
Robert, I'm curious, how do you see the connection between between Federation and AI?
00:47:26:06 - 00:47:49:19
Robert Farr
Yeah. So, yeah, it's a good topic. Right. AI is this thing that is, I would say just. Yeah. I mean, for
me, it transforms how I work every day. You know, it's just like every tool I use and the new tools
I'm using, everything is driven by AI. And we're, you know, internally. Right?
00:47:49:19 - 00:48:12:06
Robert Farr
We're trying to sit there and say, like, how do we embrace AI? How do we, you know, create an
AI first platform? So I think that's really, you know, I think you mentioned this earlier. Jens. that,
you know, AI and LLM right. I would say there's there's really four pieces for me right now. And,
and we're evolving.
00:48:12:06 - 00:48:31:17
Robert Farr
So this will change. But, you know, you have to have scope, right. So this is often what we call
an agent profiles. Tell me what your purpose is. Right. What what's your what's the bounding
scope? You're trying to get that LLM to focus a little bit. And, you know, the second piece is then
there's, you know, I'd say rules, right?
00:48:31:17 - 00:48:54:11
Robert Farr
I'll say guidelines or rules. So this again, you're trying to provide the LLM, you know, maybe a
decision tree, right? Like, help, help guide it when other things are going on. Then we'll talk
about or I'll talk about the graph, which is really the data. Right. Like it's current state context,
insights, all of those things together, along with the ability to make change.
00:48:54:16 - 00:49:17:07
Robert Farr
And, and then there's a knowledge base behind that. Right. And the knowledge base that
typically comes from our, you know, industry knowledge, our data platform. Right. We we do all
kind of processing and training on the LLMS to make them smarter. Yeah. And but if you don't
have those four components, right, you know, our, our experiences with that today, right.
00:49:17:07 - 00:49:36:06
Robert Farr
We, you know, hallucination happens, right? It it will it'll overachieve or, you know, it'll it'll try to
overachieve and then go off of, kind of off the rails. And you don't really achieve what I call a
valuable result. And I always say it's key, right? Customer value is paramount. And so you
always have to keep that in mind.
00:49:36:09 - 00:50:03:11
Robert Farr
With those interactions. So in that right we're working on the first two right defining agents.
Right. Defining the rules and guidelines and all that stuff. And you know, we're building many
companies have built knowledge bases already to train them. That missing piece is how do you
how do you make that graph accessible. Right. How do you how do you provide it in such a way
that you allow the, LLM to get current state context, right?
00:50:03:16 - 00:50:28:06
Robert Farr
What's actually going on here? You know, what insights do we have to pull from to then frame?
It's it's kind of, you know, decision matrix and the outcome and then ultimately the action it might
try to take, depending on the type of agent you're trying to build that I think is, is is the key
piece. And so that's where, you know, if you think about a developer, right.
00:50:28:08 - 00:50:49:10
Robert Farr
You know, I've, I've, I can go off on a whole theory about, you know, what I've seen in the
industry in terms of like software languages and libraries and all those things. But we have been
catering to human developers for years, right, for decades given. And so it's been this constant
race to create, you know, easier to build with APIs, right?
00:50:49:12 - 00:51:24:12
Robert Farr
ORMs come along instead of SQL. You know, rest really favors, I would say a human developer
more, but just because of the simplicity or RPC the same way. But now we have this, this agent,
right? And it's really good at if you give it a good schema, a good contract, good metadata and
navigating those things, an agent almost does better with SQL, right, than it does an arbitrary
set of of APIs that aren't well connected, right, where you don't really get a sense of the graph.
00:51:24:15 - 00:51:57:18
Robert Farr
And, so that's where I see, you know, GraphQL being kind of that, that potential sweet spot
saying it's almost like SQL for the web, right? If you think about GraphQL, you get to express a
query, a detailed query with what you want. And, you know, the, you know, obviously the graph
kind of navigates you through things, but, but it it provides that powerful access to all of that
data for an LLM and allows it to navigate it.
00:51:57:20 - 00:52:08:09
Robert Farr
That's where I see maybe a, I don't know, I'll say a pivot point of how do we power those LLMs
with that insight? And quickly.