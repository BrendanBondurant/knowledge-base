---
title: Sergiy's Journey and Evolution of GraphQL Go Tools
slug: ep07-02-sergiy-joins-and-evolves-graphql-tools
series: The Good Thing
episode: 7
chunk: 2
participants:
- Jens
- Sergiy
segment: Sergiy's background and GraphQL Go tools evolution
timecode: 00:05:06:09 – 00:10:23:15
start_time: 00:05:06:09
end_time: 00:10:23:15
speakers:
- Jens
- Sergiy
topics:
- Sergiy's 5-year journey with WunderGraph
- Origins at Tyk Technologies
- GraphQL Go tools development
- Evolution from 10,000-line files to maintainable structure
- GraphQL spec compliance efforts
tags:
- career-journey
- graphql-go-tools
- open-source
- code-organization
- tyk-technologies
topic_tags:
- career-journey
- graphql-go-tools
- open-source
- code-organization
- tyk-technologies
entities:
- Sergiy
- Jens Neuse
- WunderGraph
- Tyk Technologies
- GraphQL Go Tools
- Ukraine
- Germany
- London
mentions:
- first engineer hire
- 14 years of development experience
- splitting large files into manageable modules
- GraphQL reference implementation alignment
- JavaScript GraphQL compliance
summary: Jens and Sergiy discuss their 5-year working relationship, starting at Tyk
  Technologies where Jens created GraphQL Go tools. Sergiy became the first engineer
  hire and evolved the codebase from massive files to a well-structured, GraphQL spec-compliant
  library, now owning 60% of the project.
---

00:05:06:09 - 00:05:42:12
Jens
And then some of our customers have a lot of graphs, like 80, 90, more than 100. And suddenly
things like descriptions become a problem because you want to know, like, what is the, what is
the source of truth and other things. So, yeah, interesting stuff. And it's also, great that we are
in, in a position where we can work directly with, with customers, solve these, these issues, and,
yeah, on the on the second slot, we have, Sergiy with us.
00:05:42:14 - 00:06:10:13
Jens
Sergiy it's great to have you on the, on the podcast. I think we had you on the podcast in the, in
the very beginning of when we started, WunderGraph some some years ago. And, for those
who don't know, Sergiy is our first engineer. I think the first hire. So engineer, number one and,
yeah, maybe you can, you can, walk us a little bit through, like what?
00:06:10:15 - 00:06:22:00
Jens
What is your, what is your journey with me? What is your journey with with, WunderGraph
because actually, we're we're working together for quite some time, right?
00:06:22:03 - 00:06:48:23
Sergiy
Yeah, just about like five years or so. I consider it like, a quite a long time for, for being on the
project and like, a, I have a Guerrero or like, probably 14 years already. And, this is just my last
longing product, which never ends, actually. And, I always have work to do, and it is very
enjoyable.
00:06:48:23 - 00:06:54:17
Sergiy
And, I get a satisfaction from doing this job like, it's it's really cool.
00:06:54:19 - 00:06:55:25
Jens
Yeah.
00:06:55:28 - 00:07:31:15
Jens
I remember so Sergiy and I, we met at Tyk Technologies. It's an and a company, headquartered
in London, I think, with, a remote culture, which allowed, Sergiy from the Ukraine and me from
Germany to actually meet and, they have an open source API gateway, it's written in go and like
many years ago, I think around 2018, I wanted to dive into the world of, of GraphQL and build
some tooling.
00:07:31:15 - 00:07:53:08
Jens
And I saw that there is not so much tooling for GraphQL and go. So I created GraphQL go tools,
and I took it and went to to Tyk and applied there for a job and said, hey guys, you have an API
gateway in go, I have a GraphQL library in go, we should put it into your gateway.
00:07:53:08 - 00:08:15:10
Jens
And then somehow I got the job. I actually created the job. That job didn't exist. And there was
this guy Sergiy in another team. And I think in the beginning, you you you were not immediately
convinced that this is the thing or like, do you remember, like the early days?
00:08:15:12 - 00:08:16:12
Sergiy
Yeah, I do, but.
00:08:18:16 - 00:08:42:14
Sergiy
It is not like that. Basically, it was a funny story because like, I got asked by, my team that like,
do I know GraphQL? I said, of course I know it. I use it on one project, but I just didn't know into
what I am subscribing for and, like what it will be. And then, I started working on a first task, like,
and,
00:08:42:17 - 00:09:10:25
Sergiy
Yeah. Just a whole nother world like this, I think, like brilliant GraphQL spec continuously
digging into it. Yeah. And, one of my comments was that I split a couple of files into plenty of
files, like, Jens has a drawback that, he likes to, bootstrap something very quickly. And, when
the code grows, just the file grows.
00:09:10:27 - 00:09:44:27
Sergiy
And when you have just a single file with 10,000 lines, it's just unmanageable. Yeah. So, yeah,
my, my first job was like, just to split that files into smaller ones and, yeah, five years later, I
could say that, I own like, 60% of the project because, Yeah, I don't share this, currently with
anyone other like and, yeah, I'm very into this project because, yeah, I have written a lot of
things and, we have created a lot of things.
00:09:44:27 - 00:10:23:15
Sergiy
New things, because it's all things, we made like, as much close as possible, to conform with
GraphQL reference, implementation in JavaScript. We align it, most of the validation rules, we
try to be compliant. Of course we are different because we are just not regular old GraphQL
library. Like, it is not like a GraphQL, GraphQL gem, which is the factory standard and, good
development tool, built in GraphQL.