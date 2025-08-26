---
title: AI Collaboration and API Exploration
slug: ep17-11-ai-collaboration-and-api-exploration
series: The Good Thing
episode: 17
chunk: 11
participants:
  - Stefan
  - Jens
segment: AI-powered development and federation acceleration
timecode: 00:50:19 – 00:56:05
start_time: 00:50:19
end_time: 00:56:05
speakers:
  - Stefan
  - Jens
topics:
  - Big companies adopting Cursor for development
  - Senior architects developing prompts
  - Legacy migration to federation acceleration
  - GraphQL guild community meetings
  - Single query replacing 20 API calls
  - AI increasing developer velocity
  - Need for orchestration layer and operating system
tags:
  - ai
  - graphql-guild
  - api-design
  - cosmo
  - federation
  - go
  - graphql
  - graphql-federation
  - llm
  - rest
topic_tags:
  - ai-collaboration
  - cursor-adoption
  - legacy-migration
entities:
  - Cursor
  - WunderGraph
  - GraphQL guild
mentions:
  - collaboration productivity and safeguards intersection
  - senior architects prompt development
  - lightning speed legacy migration
  - Friday GraphQL guild meetings
  - seven subgraphs single query
  - 20 API calls reduction to one
  - AI LLM adoption trend
  - orchestration layer need
summary: Stefan positions their product at the intersection of collaboration, productivity,
  and safeguards while Jens observes big companies using Cursor to accelerate legacy
  migration to federation. He describes a GraphQL guild meeting where one query replaced
  20 API calls across seven subgraphs, illustrating massive improvements. As companies
  adopt AI to increase developer velocity, there's a growing need for orchestration
  layers and operating systems to manage this increased productivity.
---

00:50:19:24 - 00:50:37:11
Stefan
It doesn't really allow collaboration. What APIs provide is the safeguards. And what we're
building is at the intersection of collaboration, productivity, and safeguards. But can you talk a
little bit about where you see AI and Cosmo, and APIs?
00:50:37:14 - 00:51:10:08
Jens
So what we're currently seeing is big companies adopting tools like Cursor and changing the
way they create software. So it's now like senior architects or senior engineers who can who
now focus on developing the right prompts and everything. And they are migrating legacy
service into the world of federation at lightning speed. So it's, it's a very interesting observation.
00:51:10:08 - 00:51:35:13
Jens
It was never cheaper to migrate legacy and modernize it and consolidate services. And, one we
we just talked with, with one such company, we we joined one of their guild meetings. So they
have like a GraphQL guild that meets every Friday there. There's not just one guild in the
because.
00:51:35:15 - 00:51:37:26
Stefan
That's what I'm saying. It's a community. It's a community.
00:51:37:26 - 00:52:08:12
Jens
Yes. So they had this, this, this, guild meeting and one developer showed an example where
they have a single query. And this query loads data from like seven, seven, subgraphs. And
before they had this, this, implementation, the front end would have made like 20 calls to
various services to get the same data. Now it's one query.
00:52:08:12 - 00:52:42:24
Jens
So massive, massive improvement and so where I'm seeing the or where are we going like with,
with WunderGraph and what we're doing is so I think the trend we're seeing is companies adopt
AI and LLM and they will they will increase the speed and velocity and productivity of their
developers. If you do that, you need some sort of orchestration layer and operating system.
00:52:42:27 - 00:53:14:00
Jens
You need a place where the thousand developers can efficiently collaborate on what they are
now building at lightning speed. So now everybody's running faster. Everybody can build and
modernize is faster. They have more output, more velocity. But all of this energy, where is it
going if you don't have a means to organize it, to have people collaborate, work together?
00:53:14:03 - 00:53:49:27
Jens
And the foundation of, let's say you have a thousand devs and everybody builds services, what
is the foundation of of bringing it all together, making it re usable for everybody else? You need
to to encapsulate your business, your business logic as a service, expose it as a strict contract.
We now know why we just discussed this problem. So you need a strict contract and you need
to be able to share it with the rest of the company or even like partners, external, internal,
whatever.
00:53:50:00 - 00:54:21:06
Jens
So you need a platform where you can you can get like a bird's eye view on where are we
currently at with our APIs. Then you can search and leverage AI capabilities to immediately to
quickly understand what is the current API landscape doing. Can it solve my problem? So it's it's
a it's a question of exploration, of understanding APIs, of finding APIs that solve your problem.
00:54:21:09 - 00:54:53:27
Jens
So that is one big part. So bird's eye view exploration. And then if it it's not able to solve your
problem then you want to be able to find like the right stakeholders, the right people, the right
code owners. You want to collaborate with them on design. And once you have figured out the
good design for your new functionality, once you have figured out like the right place, where to
put it, you want to immediately go back to your your vibe coding whatever cursor.
00:54:54:00 - 00:55:25:22
Jens
Now you can code that publish, bring it into your API architecture. Sure, make it accessible to
everybody else, make it searchable, make it findable, reusable, etc. we don't want duplication in
this world. Yeah. And then we we essentially built like I would say like, like an operating system
or yeah, a principled approach so that you can really leverage the power of AI in terms of
development.
00:55:25:24 - 00:56:04:28
Jens
And we give you like the missing piece in terms of collaboration, so that it's not all just this. You
know, spinning the tires and creating lots of smoke, but actually bringing the horsepower on, on
the, on the road and enabling, this, this collaboration. And I think this is going to be like a, yeah,
a huge productivity boost if we can enable Big orgs to not just, yeah, build services fast, but
actually build services fast that also fit together in the bigger picture.