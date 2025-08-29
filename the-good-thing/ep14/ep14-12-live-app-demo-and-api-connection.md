---
title: Live App Demo and API Connection
slug: ep14-12-live-app-demo-and-api-connection
series: The Good Thing
episode: 14
chunk: 12
participants:
  - Stefan
  - Jens
  - Dustin
segment: Real-time Application Testing and Data Validation
timecode: 00:47:01 – 00:50:13
start_time: 00:47:01
end_time: 00:50:13
speakers:
  - Stefan
  - Jens
  - Dustin
topics:
  - Real API Integration
  - Live Demo
  - Data Validation
  - Employee Updates
tags:
  - real-api-integration
  - graphql-validation
  - ai
  - api-design
  - cosmo
  - go
  - graphql
  - llm
  - mcp
topic_tags:
  - real-api-integration
  - graphql-validation
entities:
  - Cursor
  - MCP community
  - Cosmo Dashboard
  - GraphQL endpoint
  - Next.js
  - Tailwind CSS
mentions:
  - non-developers building applications
  - security concerns acknowledgment
  - automation process movement
  - correct endpoint usage
  - right headers and request scheme
  - single page component strategy
  - real-time API requests
  - employee mood and availability updates
  - marriage status filtering
  - Stefan availability status demo
summary: Jens observes a growing movement of non-developers using Cursor and MCP to
  build applications. Dustin demonstrates the generated app running in Cosmo Dashboard
  with real API connections, showing live employee data manipulation including mood
  changes and availability updates, validating the real-time connection through GraphQL
  endpoint queries.
---

00:47:01:10 - 00:47:07:06
Stefan
Yeah. Well, yeah, it's next js and tailwind for styling when you got to know what those two are.
00:47:07:08 - 00:47:48:04
Jens
Yeah, but but you know, one thing I have observed in the MCP community in the last couple of
weeks is that more and more people who are not developers, who are now using cursor to to
build applications and to, to achieve something, to automate something and, yes, you can, you
can make an, an argument and say, okay, there will be security problems and other issues and,
and I'm not trying to argue against that, but what what I'm trying to get at is there's a new
movement of, yeah, like this cursor with LLMs.
00:47:48:04 - 00:48:07:20
Jens
With MCP. More people are now able to, to automate processes to, to build applications and to,
to, to get some or so. Yeah. We need to think about security carefully. But I think in general it's
a, it's an amazing movement.
00:48:07:23 - 00:48:33:03
Dustin
Yes. So with, Claude is done, we can now, if you observe this here, you see, it has actually used
the right end point because this endpoint was exposed through the get operation info endpoint.
It has set the right headers, the right, request, scheme. And yeah, I, because I instructed the
LLM to create a single page and not create multiple components so it's easier to copy.
00:48:33:06 - 00:48:49:02
Dustin
Now I will copy it into our application and let me share the result.
00:48:49:05 - 00:48:55:08
Dustin
One sec.
00:48:55:10 - 00:48:59:02
Dustin
This is by the way, the Cosmo Dashboard. So and so.
00:48:59:02 - 00:48:59:25
Stefan
You're you're.
00:48:59:25 - 00:49:06:16
Jens
You're abusing your local Cosmo dashboard to to bring this in.
00:49:06:18 - 00:49:33:24
Dustin
Ex. Exactly. So now you see it has requested all the data. Those are actually real real requests
against API. And I can make employees happy. Sad. I can make them available. I can filter for
the marriage status and and to prove you that it's actually real data, we can open the GraphQL
endpoint.
00:49:33:27 - 00:49:34:27
Stefan
And query.
00:49:35:00 - 00:49:39:12
Dustin
And clear the data and.
00:49:39:14 - 00:49:41:07
Stefan
This is so sick.
00:49:41:10 - 00:49:43:24
Dustin
And just see Stefan is available.
00:49:43:24 - 00:49:49:02
Jens
Well it's okay now not now. Go to this dashboard and make Stefan unavailable.
00:49:49:05 - 00:49:55:14
Dustin
So let me apply filter Stefan. Let's make it unavailable okay.
00:49:55:14 - 00:49:57:25
Jens
Go to the API.
00:49:57:27 - 00:50:00:09
Dustin
You see.
00:50:00:11 - 00:50:01:17
Stefan
Okay.
00:50:01:19 - 00:50:13:05
Dustin
So it was pretty much a one shot to generate an application to manage your employees. And
now you can think of much more advanced and sophisticated sophisticated examples.