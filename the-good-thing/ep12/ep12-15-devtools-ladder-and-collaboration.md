---
title: Devtools Ladder and Collaboration Strategy
slug: ep12-15-devtools-ladder-and-collaboration
series: The Good Thing
episode: 12
chunk: 15
participants:
- Stefan
- Jens
segment: Devtools Business Model Analysis
timecode: 00:54:11:28 – 00:58:19:17
start_time: 00:54:11:28
end_time: 00:58:19:17
speakers:
- Stefan
- Jens
topics:
- Persisted GraphQL operations via SDK
- Individual to organization adoption ladder
- WunderGraph SDK lessons learned
- Cosmo backwards adoption pattern
- Prisma vs Drizzle competition
- Open source vs commercial monetization
tags:
- open-source
topic_tags:
- devtools-adoption
- sdk-strategy
- adoption-ladder
- cosmo-strategy
- open-source-monetization
- prisma-drizzle
entities:
- WunderGraph SDK
- Cosmo
- Prisma
- Drizzle
- Stefan Avram
- Jens Neuse
mentions:
- persisted GraphQL operations
- three-tier adoption model
- enterprise tooling space
- backwards adoption pattern
- open source ORM challenges
- commercial vs community motivation
summary: Stefan outlines his devtools adoption ladder theory (individual → group →
  organization) and reflects on WunderGraph SDK's failure versus Cosmo's backwards
  adoption success. Jens discusses the challenges of monetizing open source tools
  like Prisma, contrasting community-driven projects like Drizzle with commercial
  ventures and their different sustainability models.
---

00:54:11:28 - 00:54:48:03
Jens
And now you kind of make accessible your super graph to. Yeah, to anybody without
understanding GraphQL because, what this SDK does is it calls persisted GraphQL operations,
one function at a time. And yeah. Yeah. Now anybody can, can use the, the graph and that is,
that is one part where, where I think or where, where, we are currently going because,
00:54:48:05 - 00:54:58:16
Stefan
Well said. But yeah, you went full picture from the very beginning of the podcast all the way to
the very end, including relay it makes sense. But what continue what was the second part? You
said?
00:54:58:18 - 00:55:00:10
Jens
No, you just stop me.
00:55:00:12 - 00:55:26:15
Stefan
Oh, okay. Sorry. I just wanted to call that out the way that we did a full picture. I really like that. I
mean, it makes sense to. And this is how you go beyond GraphQL. But one of the biggest things
I talk with, like other startup founders friends, is that the dev tool space. So technically we're in
the enterprise, tooling space we sell to enterprises, but in the dev tools space, the only way to
make a successful dev tool is if individual developers can use it.
00:55:26:15 - 00:55:36:09
Stefan
And then you have a clear ladder to a group of developers can use it, and then an organization
of developers can use it. That's the only way a dev tool can be successful with the collaboration.
00:55:36:11 - 00:55:38:28
Jens
Where is this definition coming from.
00:55:39:01 - 00:55:55:29
Stefan
That's just my own like razor that I have, is that that's how dev tools are successful, is that an
individual developer can use it, a group of developers can use it, and an organization of
developers can use it. If you can't hit those three and a a lot of companies fall short is and they
have a good tool.
00:55:56:02 - 00:56:12:22
Stefan
We did individual developers used it, but we didn't have teams using it. And this was the
wundergraph SDK. We tried it. It didn't really work out that well. But with Cosmo, what we're
seeing is we're kind of going backwards. We're seeing the organizations of developers can use
Cosmo and that they love it. And it's what you're said.
00:56:12:22 - 00:56:35:14
Stefan
You're expanding beyond Federation, you're expanding beyond GraphQL, and, you know, i like
that. But where do you see Cosmo going in collaboration that organizations, teams, and
eventually the individual developer can use it? You think individual developers will be able to
use it when they're building their projects and things like that, to open up what you said there,
graph or their app to other developers to integrate easily with it.
00:56:35:16 - 00:56:43:21
Stefan
Also, do you like my definition of what I think of dev tooling? Or do you disagree with it?
00:56:43:23 - 00:57:21:13
Jens
I think dev tools is really hard. You build something that's. Let's take the example of Prisma. I
really like Prisma. I would have really hoped for them to be successful. Maybe they are
successful. To me, they don't look successful. Maybe they are, but. So you build it. ORM, in the
hopes that you build a massive group of people around you and you can somehow monetize it.
00:57:21:15 - 00:57:33:29
Jens
Yep. And then comes drizzle and all your dreams fall apart. Okay, but bad joke, but the good.
00:57:34:01 - 00:57:37:08
Stefan
It's true, though, sadly,
00:57:37:10 - 00:58:19:17
Jens
Not okay for real. So you build an open source orm, how do you monetize an orm, because
what you kind of need, like, it's it's, I would say it is our definition, but if a commercial, you know,
I like to, to, to distinguish open source and commercial open source, if someone builds the
drizzle open source to help themselves use drizzle, and they are not building this as a startup,
but more as a means to an end, it can be a successful thing.