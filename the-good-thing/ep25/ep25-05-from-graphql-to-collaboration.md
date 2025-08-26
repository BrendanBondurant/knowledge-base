---
title: From GraphQL to Collaboration
slug: ep25-05-from-graphql-to-collaboration
series: The Good Thing
episode: 25
chunk: 5
participants:
  - Stefan Avram
  - Jens Neuse
  - Kevin Swiber
segment: WunderGraph's Evolution and API Design Process
timecode: 00:18:28:28 – 00:23:20:19
start_time: 00:18:28:28
end_time: 00:23:20:19
speakers:
  - Jens
  - Kevin
topics:
  - WunderGraph's journey from GraphQL to collaboration focus
  - Enterprise sales challenges with developer tools
  - Federation as enterprise entry point
  - Discovery of collaboration as core customer value
  - Miro board API design workflows
tags:
  - federation
  - graphql-federation
  - ai
  - graphql-federation
  - api-design
  - api-gateway
  - benchmarking
  - go
  - graphql
  - rest
  - startup
topic_tags:
  - federation
  - graphql-federation
  - api-design
entities:
  - WunderGraph
  - graphql
  - Federation
  - Enterprise accounts
  - Miro boards
  - Post-it notes
  - API requirements
  - Startup growth
mentions:
  - GraphQL as starting motivation
  - Developer tools vs enterprise sellability
  - Multiple teams collaboration needs
  - Fast-growing startup value creation
  - Screenshot-based API design process
  - Post-it to API translation workflow
  - Process optimization beyond technology
summary: |
  Jens shares WunderGraph's evolution from a GraphQL tool to a collaboration platform. He explains how they discovered that while developers liked their tool, it was hard to sell to enterprises until they pivoted to federation for multi-team collaboration. The real breakthrough came when they realized customers' biggest problem was collaboration itself, not just technology, leading them to discover creative workflows like using Miro boards with screenshots and post-its for API design.
---

00:18:28:28 - 00:18:51:22
Jens
Yeah. You know, this is interesting what you're saying. Because for us, like, we we made and I
would say we we made a super interesting journey on, on like a fast track because when we
started, it was all about, okay, we want to build something cool with GraphQL. That was like our
starting point. And it's a valid starting point.
00:18:51:22 - 00:19:15:17
Jens
Like it's fun. It gives you motivation. And then, we we we iterated on that and we kind of realized
developers like our tool, but it is hard to sell it into enterprise. Like for for enterprise there's no
sellable unit like, they they like it and some people use it but not really enterprise. So we pivoted
into federation and federation.
00:19:15:19 - 00:19:52:19
Jens
Like, you know, you have like multiple GraphQL servers and together they, they federate and
then you have like a unified thing, on, on a high level. And what that allowed us to do is we were
able to get into enterprise accounts where multiple teams wanted to collaborate on creating a
GraphQL API. And then we didn't stop there, but we were curious to figure out, like, you know, if
you if you if you are an ambitious startup, you are you're looking for not just people who like
your tool, but you you really want to make an impact.
00:19:52:19 - 00:20:23:03
Jens
And then like, you know, like on a monetary side, you want a fast growing startup. But how do
you create a fast growing startup? You really must find a lot of value in the market. You must
find value for the customer. So we dig deeper. And if you go beyond GraphQL, if you go beyond
Federation, if you go beyond API gateways, what we kind of realized one of the biggest
problems our, our customers have is, collaboration.
00:20:23:09 - 00:21:01:18
Jens
It's it's working together. It's what you said. It's about people and process. And so, we're we're
kind of expanding beyond just the tech, like, we're we're stepping more and more away from the
tech, and we're trying to help people work together better and collaborate better. And also we
help them to, to take their existing processes and optimize them because we we kind of realized
that, you know, one of the funniest things we realized is when people want to change their, their
APIs, and I explicitly go away from the from the GraphQL language.
00:21:01:18 - 00:21:35:07
Jens
But when they try to change their APIs, we ask a bunch and we realize a lot of our customers,
they use miro boards. They put a screenshot of an application on the Miro board, and then they
put post-its on the screenshot side by side to try to articulate what could be the API
requirements and such. And then they create gigantic Miro boards with lots of screenshots and
post-its all around, and try to figure out what could the API be.
00:21:35:07 - 00:22:07:03
Jens
And then they take these post-its and somehow translate them into other tooling where they
actually create APIs for that. And we kind of realized if we want to, if we want to expand our
scope, if we want to bring more value to them, it's actually not so much about API gateways and
these kind of things and federation. It's more about how can we help the people and, and
optimize the process of designing and working together and, and these kind of topic.
00:22:07:03 - 00:22:25:06
Jens
So that's I don't know, it did it, it it clicked for us. And it, it's, it excites us much more to help the
people get something done than just building like a faster gateway or something. So I don't
know, our our thinking has completely changed. I'm curious, what you think about it?
00:22:25:08 - 00:22:53:21
Kevin
Yeah. It's, you know, I, I, I think being in this business is super interesting. And I particularly like
working for startups. When I went over to postman, my background had always been in sort of
engineering, engineering management. But when I went over to postman, at the time, they had,
a need for people with, like, enterprise experience as they were going to start trying to sell more
to enterprises.
00:22:53:23 - 00:23:20:19
Kevin
And so, you know, where they really needed help on was, in sort of pre-sales and post sales,
technical folks. Right. So I joined as a solutions engineer, and got to work with, with people, with
a bunch of different companies, as they were, you know, having struggles with their API
programs, trying to figure out kind of broadly with their API programs, not necessarily specifically
with postman.