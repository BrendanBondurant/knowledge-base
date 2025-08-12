---
title: Avoiding BFF Sprawl with Supergraph
slug: ep14-03-avoiding-bff-sprawl-with-supergraph
series: The Good Thing
episode: 14
chunk: 3
participants:
- Stefan
- Jens
- Dustin
segment: BFF vs Federation for MCP Architecture
timecode: 00:09:24 – 00:13:10
start_time: 00:09:24
end_time: 00:13:10
speakers:
- Jens
- Dustin
topics:
- MCP servers as Backend for Frontend (BFF) pattern
- BFF sprawl problems with hundreds of microservices
- Federation vs BFF maintenance challenges
- Models as new API consumers
- Authorization and telemetry duplication issues
tags:
- bff-pattern
- api-consumers
- authorization
- telemetry
topic_tags:
- bff-pattern
- api-consumers
- authorization
- telemetry
entities:
- BFF (Backend for Frontend)
- MCP server
- Microservices
- Media company
- SoundCloud
- Super graph
- Models (AI)
mentions:
- streaming services with hundreds of microservices
- model overwhelm with too many capabilities
- SoundCloud multi-app BFF example
- web, iOS, Android BFFs
- models as new API consumer type
- API sprawl and resource constraints
- authorization/authentication re-implementation
summary: Jens explains how MCP servers essentially become BFFs and warns about BFF
  sprawl when dealing with hundreds of microservices. He argues that models are new
  API consumers requiring specific BFFs, but federation provides a better approach
  by contributing to a shared super graph rather than maintaining separate BFFs for
  each use case, avoiding duplication of authorization and telemetry.
---

00:09:24:03 - 00:09:56:21
Jens
Essentially, this MCP server is now a BFF, and you will very likely want to have one MCP server
per use case because let's say you are a big a big, media company, that offers streaming
services. And let's say you have hundreds of microservices. Do you really want to create one
single MCP server and for, for all use cases and give that to a model, like, first of all, the model
will be overwhelmed by the capabilities.
00:09:56:23 - 00:10:28:12
Jens
You will have problems because these features, they come from over 100 microservices. So
there's a lot of people behind the. Do you really want to bring all of this together in a BFF? It
means that you now have to maintain a BFF across, I don't know, 100 services, potentially
hundreds of people. So you're kind of back to the BFF versus federation problem, where now
the API consumer, it is not the website where it is not one single web front end.
00:10:28:12 - 00:10:51:05
Jens
You know, we have BFFs in the past like SoundCloud, where where you have multiple apps,
you have like web, iOS, Android, etc. for each app, you have a BFF, and now there's a new API
consumer. It's not a website, it's not a browser, it's not, an app. It is a model. And we have
different models and different tasks.
00:10:51:05 - 00:11:35:06
Jens
Models should do. So. Now we need BFFs for these models or we do what Dustin has built
because that means we're not building one BFF per model, per use case. We all contribute to
the super graph and with yeah, a tiny amount of work, we create an MCP server for a very
specific use case. And, and I think that that's ultimately it's, it's the right approach because if
we're not doing it like this, so what is the what are the alternatives if we don't use the approach
by Dustin, we will essentially go back to the BFF pattern.
00:11:35:08 - 00:12:02:07
Jens
And everybody is currently talking about how we have API sprawl and we have too many BFFs
and there's too little resources to maintain the BFFs. So if we don't have the resources to
maintain BFFS for different apps and websites and products, we also don't have the resources
to maintain BFFS for MCP, for for models. So yeah, there needs to be a solution.
00:12:02:10 - 00:12:05:06
Jens
And Dustin.
00:12:05:09 - 00:12:05:27
Dustin
One comment.
00:12:05:27 - 00:12:07:28
Jens
Maybe. Sorry.
00:12:08:01 - 00:12:25:25
Dustin
One comment on the BFF analogy. It's I think also important is that you have to re-implement
everything, authorization, authentication, telemetry, who is doing what. And rather than doing it
twice, why not putting the MCP expose, MCP on the source of truth?
00:12:25:27 - 00:12:52:02
Jens
Yeah. Thank you for the curveball. I actually forgot this, but it's so true. No, no, no, that was
actually one of my bullet points. If you if you have 100 microservices and you build an MCP
server and now in this MCP server, you implement authorization, and then someone else builds
another MCP server for another use case. So now you're building authorization for that twice.
00:12:52:05 - 00:13:10:06
Jens
Yeah. If you have if you build this on top of your super graph and you put authorization into the
super graph, now it's a solved problem for both cases. Plus our router, it already has
authentication authorization. It has analytics. It has all these things.