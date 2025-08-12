---
title: Plugins, Connectors and Apollo Leadership Changes
slug: ep24-04-plugins-apollo-leadership
series: The Good Thing
episode: 24
chunk: 4
participants:
  - Stefan
  - Jens
segment: Future Vision and Apollo Leadership Discussion
timecode: 00:16:25:01 – 00:22:01:03
start_time: 00:16:25:01
end_time: 00:22:01:03
speakers:
  - Stefan
  - Jens
topics:
  - gRPC co-processor plugin system
  - Automated connector generation with LLMs
  - Legacy system integration
  - Apollo leadership transition
  - Matt DeBergalis as new CEO
  - Customer experience improvements
tags:
  - grpc
  - plugin-system
  - llm
  - apollo-graphql
  - plugin-system
  - llm
  - apollo-graphql
  - startup
  - ai
  - api-design
  - cosmo
  - cosmo-router
  - federation
  - go
  - graphql
  - graphql-federation
  - rest
  - rest-apis
  - rest-connectors
entities:
  - WunderGraph
  - Cosmo Router
  - Apollo
  - Matt DeBergalis
  - Geoff Davis
  - REST APIs
  - SOAP APIs
  - CORBA
  - OpenAPI
mentions:
  - co-processor architecture
  - REST/SOAP/XML integration
  - mainframe system connections
  - LLM-generated adapters
  - automated integration tooling
  - Matt as Apollo's face
  - conference leadership presence
  - 18-month CEO mindset
  - competitor relationship strategy
summary: |
  Jens outlines WunderGraph's future vision of using gRPC co-processors and LLM-generated adapters to automatically integrate legacy systems, eliminating manual connector development. Stefan and Jens then discuss Apollo's leadership change with Matt DeBergalis becoming CEO, viewing it as positive while noting it suggests internal challenges.
---

00:16:25:01 - 00:17:03:00
Jens
So that means if you have APIs, that are not federation, you somewhere need to have
something that translates between your REST API, your Soap API, your legacy weird http, API,
XML, like CORBA, whatever mainframe. So you need to have some code somewhere that does
this translation. And the our game plan is that in the future, we think you shouldn't be writing this
and you shouldn't be deploying this somewhere randomly.
00:17:03:02 - 00:17:44:20
Jens
But instead, we we think that we can build, the necessary tooling to take your subgraph
schema, compile it into your gRPC, take your open API spec curl requests, whatever you have,
and we will then leverage, LLMs to generate the adapter in the middle and run it as a co-
processor with, with cosmo browser, which means from a user experience, you can then say,
okay, here's my SDL, here's the service I want to connect and, WunderGraph, please generate
me the, the plugin and boom, integration done.
00:17:44:22 - 00:18:07:15
Jens
I don't need to think about subgraphs. I don't need to understand what entities are. I don't need
to write connect directives or something that might or might not fit my use case. I can just
express like, hey, here's an open API spec, bring me some fields into my graph. Boom! And
that's it. That's the, the the direction we're going.
00:18:07:15 - 00:18:16:22
Jens
we're doing this.
So in the long term, nobody should ever write boring integration code again. That's that's why
00:18:16:24 - 00:18:35:15
Stefan
And I think it's exciting. It's live now. We can definitely start to have see our customers using it.
We already have a couple using it, which is great from your point of view though. We talk a lot
about connectors and we talk a lot about Apollo, but this is a off topic. What do you think of the
new news of their new leadership?
00:18:35:17 - 00:18:52:00
Stefan
Assignment. So for those of you that don't know, Matt DeBergalis as the CTO is now the CEO.
Personally, I think it's a good idea. Yeah. What did you think? I know because you mentioned
Apollo and the ecosystem, so I wanted to bring it up.
00:18:52:02 - 00:19:22:19
Jens
Yeah. Like. If I'm honest, I always felt like Matt is the face of Apollo. I spoke with him, at least on
two occasions in person and often, at the conferences. He was kind of like leading the the the
conversation on the, on the stage and everything. And to me, it always felt like he he's actually
the, the leader from the outside.
00:19:22:19 - 00:19:49:12
Jens
I have never seen Geoff or what kind of function he, he had. So yeah without like I don't know
we, we also try to be you know, I read something somewhere someone said as a, as a CEO of
your startup, you should always try to be the, the CEO, where you want to be in in 18 months.
00:19:49:12 - 00:20:26:21
Jens
So today, be the CEO. That's you think your customers, your partners and everybody else
expects you to be in like, 18 months? And, yeah, I'm not sure if if 18 months future Jens should
roast, competitors. So in that sense, I think it's, it's the right move, to be honest. And at the
same time, it, it shows that not everything is going right behind the scenes because, like, the
must be going on something with the board and then other, things.
00:20:26:21 - 00:20:32:05
Jens
So. Yeah, that's that's my take.
00:20:32:07 - 00:20:44:18
Stefan
18 months Jens would be very proud of that take. No it's very nice, very political. And I think it's
right regarding gRPC plugins and what we're building. Any last minute topics you want to add to
that before we switch topics.
00:20:44:21 - 00:20:52:16
Jens
Yeah. Like you know, you don't always have to be 18 months in future Jens
00:20:52:18 - 00:20:56:23
Stefan
Okay. And I like that better it makes for better content.
00:20:56:25 - 00:21:07:26
Jens
Is it. Yeah. So, we we we sparked a little bit of conversation on, on Twitter. On Twitter. We're not
on Twitter for some reason on LinkedIn.
00:21:07:28 - 00:21:11:06
Stefan
You want me to bring it up?
00:21:11:08 - 00:21:44:22
Jens
Yeah. We can we can take a look because, someone from Uber wrote about the future of
Federation also has to say some things. And there was some conversation and I think it's it's it's
interesting. And we can also speak about what, what we think about this new, this upcoming
spec.
00:21:44:24 - 00:21:49:05
Jens
Are you bringing it up or are you fighting your computer? Mr..
00:21:49:07 - 00:21:56:14
Stefan
It's because every time I type, you always freak out about the typing. So I had to mute myself
while I typed so and so.
00:21:56:16 - 00:22:01:03
Jens
Maybe, maybe we could have Curtis as a as a podcast guest.