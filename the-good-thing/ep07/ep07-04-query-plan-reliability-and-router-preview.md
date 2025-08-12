---
title: Query Plan Reliability and Router Headless Mode
slug: ep07-04-query-plan-reliability-and-router-preview
series: The Good Thing
episode: 7
chunk: 4
participants:
- Jens
- Sergiy
- David
segment: Query planner reliability and router preview functionality
timecode: 00:16:19:09 – 00:21:16:06
start_time: 00:16:19:09
end_time: 00:21:16:06
speakers:
- Jens
- Sergiy
- David
topics:
- Query planner reliability safeguards
- Router headless mode implementation
- Query plan regression prevention
- Batch query planning for testing
- Startup moats and velocity advantages
tags:
- query-planning
- startup
topic_tags:
- query-planning
- reliability
- testing
- router-architecture
- startup-moats
entities:
- Cosmo
- WunderGraph
- Jens Neuse
- Sergiy
- David
mentions:
- query plan previews
- execution config from file system
- batch operation planning
- router version comparisons
- 1000+ production queries
- provides and override directives
summary: Discussion of WunderGraph's competitive moats through velocity and reliability
  investments. Jens explains the new router headless mode that enables query plan
  comparison across router versions or schema changes, providing safeguards for large
  deployments with thousands of production queries.
---

00:16:19:09 - 00:16:22:18
David
And, it's one of my favorite things.
00:16:22:20 - 00:16:46:22
Sergiy
Totally agree with. There's like, I worked for quite a long time and never had like to actually
such, such speed train on this, this reaction. It's really reactive. No, not on rocket way, but, yeah,
you know, totally unique way. And, it's, great feeling like you see you have immediate impact
and you.
00:16:46:22 - 00:16:47:24
David
Could.
00:16:47:27 - 00:17:25:29
Sergiy
Bring some something new very fast and you could fix, of course. And in case, there was any
problems and, yeah, everyone is satisfied. Like, we as developers, our customers, as our
customers. Yeah. It's really unique situation, I believe, because, not so many, like, startups or
libraries or whatever have, such a quick feedback like we are open source, but, it also, like, has
a different situation, like, we also have customers and this feedback loop is awesome.
00:17:26:06 - 00:17:47:20
Sergiy
And even, you know, open source contributions, usually they taken just a bit longer to
accomplish something. But yeah, people also love that we, try and thought about fixes that we
respond to and we provide guidance sometimes. And, yeah, it's really unique project to work
with.
00:17:47:22 - 00:18:14:04
Jens
Yeah. I would say like from, from a startup perspective. So this was like the engineering
perspective, but from, from a startup perspective, you know, sometimes, like, for example,
investors, they ask you like, what is the moat of the company? And this is especially an
interesting question when you have a lot of open source code, because now you could say, well,
the the code cannot be the moat, right?
00:18:14:04 - 00:18:40:24
Jens
Because it's open source. Everybody could just take it and run their own router. So like what
what is the product? And the one thing I would say to this discussion is, I think a huge part of the
moat is the velocity, because yes, you can you can run cosmo yourself, everybody it's it's open
source. But, do you have the expertise and the velocity to, to, to quickly change it?
00:18:40:24 - 00:19:27:01
Jens
And I think for, for a startup, one, one of the big parts of a moat is the ability to quickly change
code. And what, what pays into that is maintainability. And for example, one one very big topic
that we're currently heavily investing in is reliability. So we're we're currently building, for
example, one, one tool that can preview query plans, because we, we came to realize that,
when you have very, very big customers with large deployments and you want to you want to
work on the the query planner, or you want to work on composition, or you want to change the
router in some way, like it's software, we want to
00:19:27:01 - 00:19:56:15
Jens
change it, we want to improve it, but you never want to break something. And one super
important piece of that is we want to ensure that query plans don't have regressions. So we, we,
improve query planning or composition in some way. And we want to ensure that it doesn't
break anything. So one thing we are currently, building and we actually as part of that yesterday
we, we released new functionality for the router.
00:19:56:17 - 00:20:19:11
Jens
The router can now run in a headless mode where you can feed it from the file system, a
schema or an execution config, but more or less it's just a schema. And you can feed operations
and then you can, in the, in the batch plan the operations so you can see how will the query
plans look like.
00:20:19:11 - 00:20:41:23
Jens
And can I plan all the queries and then you can you can do this step for different versions of the
router. For example, if you make a new release you can you can test two router versions. Or if
you change a subgraph you can run this process with two configurations. The previous
configuration and now the new configuration with your new subgraph.
00:20:41:25 - 00:21:16:05
Jens
And then we can compare the query plans. And this is like a safeguard to say like okay, we're
we're a big company. We have over 1000 queries in production. We're making a change. Will
the query plans look like we expected? Because let's say you put, an override directive or
provide directive for something, and you guys are the expert experts, like, tell me a little bit
about what what happens if I use directives like, provides external override.