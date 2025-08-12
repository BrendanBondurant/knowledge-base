---
title: Architecture Insights and Conway's Law
slug: ep11-08-architecture-insights-conways-law
series: The Good Thing
episode: 11
chunk: 8
participants:
- Stefan
- Jens
segment: Microservices Architecture Analysis
timecode: 00:43:03:01 – 00:48:14:14
start_time: 00:43:03:01
end_time: 00:48:14:14
speakers:
- Stefan
- Jens
topics:
- Machine learning approach to schema optimization
- Conway's Law in practice
- Microservices architecture evaluation
- Organization structure and service design
- Jeff Bezos API mandate
- Team communication through APIs
tags:
- conways-law
- microservices-architecture
topic_tags:
- conways-law
- microservices-architecture
entities:
- Conway's Law
- Jeff Bezos
- Amazon
- Stefan Avram
- Jens Neuse
mentions:
- machine learning schema optimization
- questioning architecture decisions
- team ownership of domains
- API communication mandate
- compiler team example
summary: Discussion of using machine learning approaches to optimize microservices
  architecture through schema analysis. Jens explores how Conway's Law affects system
  design, while Stefan explains Jeff Bezos' API mandate requiring teams to communicate
  only through APIs, and how federation can enhance this approach.
---

00:43:03:01 - 00:43:25:05
Jens
And so you make changes. Just like machine learning. And as you make changes you see the
stats go up or down or they like the let's say you have let's say you have number of nodes in
the, in an AST. And this number, it goes up and down because you need to make more or less
fetches or whatever.
00:43:25:07 - 00:44:08:01
Jens
So you start to change the schema in random ways, and the query plans change. And if you do
this you kind of realize that there's federation, there's microservice architecture, then there's
people. There's, you know, the organization, the people of the organization. And now you start
thinking about. Are we doing microservices right, in the sense that this is the, is the schema or
other schemas we have built?
00:44:08:03 - 00:44:37:08
Jens
Are they good? Yeah. And is there something we can optimize. And then you, you, you kind of
start going down the rabbit hole of, oh, that's, that's a very interesting topic because, we have
never, you know, we have never thought about questioning our architecture. So when I, when I
build microservices in the past, it's like, okay, you build a website, it needs a backend, we build
a monolith.
00:44:37:10 - 00:45:08:01
Jens
We think the monolith is too big. We split it up. Now we have five microservices. Did anybody
ever question if that was a good architecture? And then, you know, so the stuff we're thinking
about is can we, can we build metrics? Can we understand your traffic, your query patterns, the
shape of the organization, the shape of the subgraphs?
00:45:08:03 - 00:45:37:18
Jens
Can we somehow leverage the data to help people improve their architecture? And and I think
this is really just the starting point. And, you know, at this level, it's not about rest. It's not about
MCP, not about SDK. It's it's not about GraphQL, and it's not about Federation. It's about the
question, can we help organizations to, to to kind of wiggle back and forth and try it out?
00:45:37:20 - 00:46:00:09
Jens
What would be the optimal service structure? Which team should take ownership of what. And I
think it's a it's a super interesting topic. And, we're we're starting to do research in this area, and
I, I have no idea where this is leading, but, yeah, I, I think it's super interesting stuff.
00:46:00:11 - 00:46:22:02
Stefan
Well, it is even if you're not, like, super familiar with, like, APIs. I think a big problem companies
have is, is understanding their company, understanding who works on what, who owns what a
lot of companies will do, like a domain driven architecture with websites, with the domain the
team owns that. I think the architecture part is where federation thrives.
00:46:22:02 - 00:46:50:16
Stefan
But for those of you that might not be familiar, there's a really cool mandate by, it's famous, it's
the API mandate from Jeff Bezos. And one of the mandate rules on there was that teams will
communicate with each other only through APIs. And I think that was the first step into this. And
what I understand from this, and Jens, is feel free to correct me if I'm wrong, but Federation can
kind of unlock that mandate even further is that teams can communicate and work together.
00:46:50:22 - 00:47:18:27
Stefan
You can federate across the entire company. You can understand everything within the
company. And I think that's a huge problem that companies have is okay. What team is working
on what what services working on? Is this field still in use on this API, or are we even using this
API? And I think now with LLMS and data, it's what you said I built it, but it was five years too
early and I think right now with AI and LLMS and everything that's coming even further, I think
it's a great time with that.
00:47:19:05 - 00:47:38:21
Stefan
But are you able to share a little bit about like, what we're kind of building where we're
envisioning the space going because we kind of jumped that part, like we went from GraphQL.
This is this interesting sector that we're exploring. But what about the current GraphQL market?
Like what do you think about it and where are we going as a company?
00:47:38:23 - 00:47:42:06
Jens
Yeah. Good question, by the way. You know Conway's Law, right?
00:47:42:09 - 00:47:47:25
Stefan
Yeah. That, I never know what it is, but if someone says and I'm like, yep, that's Conway's Law.
00:47:47:27 - 00:47:49:23
Jens
I think.
00:47:49:25 - 00:47:52:07
Stefan
Something you don't map your organization, right?
00:47:52:09 - 00:48:14:14
Jens
Yeah. But the way information flows inside the organization, it kind of resembles how you build
your architecture. Yeah. So for example, if you have if you build a compiler with two teams, the
compiler is very likely to have two steps.