---
type: podcast-chunk
title: Introduction and Dustin's Background
slug: ep03-01-intro-dustin-background
series: The Good Thing
episode: 3
chunk: 1
segment: Introduction and Dustin's career background
timecode: 00:00:15 - 00:05:21
start_time: 00:00:15
end_time: 00:05:21
speakers:
  - Stefan
  - Dustin
topics:
  - Role Evolution
  - Technical Founder
  - Startup Lessons
  - AI Impact
tags:
  - graphql
  - open-source
  - ai
  - cache-warming
  - federation
  - founder
  - go
  - graphql-federation
  - monolith
  - rest
  - rust
  - startup
  - typescript
entities:
  - Dustin
  - Stefan
  - Jens
  - WunderGraph
  - High Graph
  - RTL
  - Fastly
summary: Stefan introduces Dustin as the CTO and co-founder of WunderGraph, replacing
  Jens for this episode. Dustin shares his career journey from computer science studies
  to working at High Graph on GraphQL content federation and RTL on GraphQL gateways,
  leading to his role at WunderGraph.
---

Episode 3
00:00:15:27 - 00:00:22:02
Stefan
I was.

00:00:22:05 - 00:00:26:16
Stefan
And. Wait a minute. You're not Jens. Who are you?

00:00:26:19 - 00:00:31:19
Dustin
Hi. Dustin. Go!

00:00:31:22 - 00:00:47:07
Stefan
Everybody, welcome back to another episode of The Good Thing. As you've noticed already,
this is Dustin. This isn't Jens. So, Dustin, who are you? You're kind of. Maybe for the people that
don't know, you maybe get a little quick introduction of yourself. Because I know you very well,
but introduce yourself.

00:00:47:10 - 00:00:58:04
Dustin
Yeah. If you would follow the Covert history of wundergraph, you would already know who I am.
So, But, yeah, my name is Dustin, CTO co-founder of wundergraph. And. Yeah.

00:00:58:06 - 00:00:59:07
Stefan
Yeah. Fantastic.

00:00:59:12 - 00:01:03:06
Dustin
e first time being on the podcast, so.

00:01:03:09 - 00:01:22:05
Stefan
Yeah, it's exciting. So Dustin, thanks for joining us. And as you mentioned, if you follow the
changelog or the commit history on our repo, you'll see Dustin's name pop up a lot. So Dustin is
our CTO and co-founder. He's an absolute beast. We joke around that he's a machine and
yeah, Jens is out this week. So I invited Dustin for his first podcast and all.

00:01:22:05 - 00:01:30:07
Stefan
We're going to do is literally just talk about the technology, talk about Dustin's role here, and just
kind of the things that he's been in charge of. But, yeah. Dustin, thanks for joining me today.

00:01:30:09 - 00:01:32:01
Dustin
Awesome. Thank you.

00:01:32:03 - 00:01:50:10
Stefan
Yeah. So let's kind of just kick it off with a little introduction of yourself. So I know your history,
but I think you have a pretty cool history of companies that you've worked that. So where you
studied, where you started out with, you started off pretty early in the tech journey. And I think
you have like, what is it, ten, 11 years of experience now?

00:01:50:12 - 00:02:15:03
Dustin
Yeah, roughly around that. So, I studied computer science. But very soon I figured out that,
that's not my it's not not my career path. I wanted to to, to do so. I, I spent a lot of time on, on
freelancing, and also educating myself in different technologies. I spent a lot of time in open
source communities.

00:02:15:05 - 00:02:48:21
Dustin
And then I found, my way into, several different companies, for example, high graph, where I
worked at and, high growth as a, like a content management system, which has a focus on
graphql content federation. And I did very, exciting stuff there. We have, implemented, a graphql
proxy written and written in rust that takes care of caching.

00:02:48:23 - 00:03:21:26
Dustin
Which was driven by fastly, the content delivery network deployed on on edge, on the edge. It
was a pretty exciting project, back then. And then I started another career, at RTL, which is, one
of the biggest television companies in Germany and, yeah, the, the, the, they needed, a way to,
to consolidate, to hydrate data sources together.

00:03:21:26 - 00:03:52:18
Dustin
And so the obvious solution was graphql, the didn't invest in graphql federation, back then, but, I
have built with, my, my team, graphql gateway that, aggregated the data, which was more or
less a monolith, graph. And I think, the last I think today they're, they're already, migrating from
the architecture to a federated graph architecture.

00:03:52:21 - 00:03:53:09
Stefan
Which is a very cool.

00:03:53:12 - 00:03:54:29
Dustin
Intense,

00:03:55:01 - 00:04:09:22
Stefan
Yeah. And then so you were working at High Graph and the story of how, Dustin joined us is
actually kind of funny. So you had an open source project which was kind of like, like an OSS
schema registry, right? Like very early on. What was that project?

00:04:09:25 - 00:04:19:00
Dustin
for workers.
I think what you're referring to was, a graphql, cache proxy, for, written in TypeScript for cloud,

00:04:19:02 - 00:04:29:21
Stefan
Yeah, yeah. And, I think you were working on that. And then how did you, like, meet jens? It was
like you guys were working on open source or, like, you start out contributing to a wundergraph.
What was it?

00:04:29:23 - 00:04:57:04
Dustin
Or I think it was on discord. Back then, or. Yeah, I was super. I mean, today you are very busy
as a founder, but back then I was, very active in the community. Also discord. And I don't know
how, but, Jens. Saw what I did in several open source project and wrote me a message, a nice
message like, hey, I'm interested in your stuff.

00:04:57:07 - 00:05:09:24
Dustin
You're doing some stuff with graphql. Yeah. Let's let's talk. Let's. Are you interested in my
startup idea? And, I said, why not?

00:05:09:27 - 00:05:20:01
Stefan
Let's go. That Was three years ago. Yeah, yeah, I remember, and then you joined us. This is
before the original WunderGraph. It wasn't open source. Do you remember? We open sourced it
together?

00:05:20:03 - 00:05:21:21
Dustin
Yeah. 