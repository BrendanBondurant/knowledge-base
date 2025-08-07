---
title: AI-Powered Access to Supergraphs Without GraphQL Knowledge
slug: ep09-04-ai-access-graph-non-developers
series: The Good Thing
episode: 9
chunk: 4
participants:
  - Jens
  - Cameron
segment: AI and GraphQL accessibility
timecode: 00:13:07:13 – 00:17:04:24
start_time: 00:13:07:13
end_time: 00:17:04:24
speakers:
  - Jens
  - Cameron
topics:
  - AI-powered GraphQL query generation
  - Natural language to GraphQL translation
  - Business user access to APIs
  - Schema navigation challenges
  - Developer productivity improvements
  - Large schema complexity (GitHub example)
tags:
  - ai-tools
  - query-generation
  - developer-experience
  - schema-complexity
  - business-users
  - accessibility
entities:
  - GitHub
  - GraphQL
  - ChatGPT
  - WunderGraph
mentions:
  - business users querying APIs
  - GitHub schema size (336,000 tokens)
  - schema documentation challenges
  - natural language interface
  - developer schema navigation
summary: |
  Cameron discusses exploring AI-powered tools to make GraphQL supergraphs accessible to non-developers and improve developer productivity. Using GitHub's massive schema as an example, they explain the challenges of navigating large GraphQL schemas and how AI can bridge the gap between natural language requests and GraphQL queries.
---

00:13:07:13 - 00:13:22:13
Jens
And this is something where, where you came, you joined us and we started, exploring, new
ways of, of dealing with, with GraphQL. So maybe, we can expand a bit on that.
00:13:22:15 - 00:13:52:22
Cameron
Yeah. For sure. So one of the things that I've been exploring since I joined the team is how we
can leverage artificial intelligence on top of a super graph or even some subgraphs, to empower
people like business users or, empower front end engineers who’ve never encountered
GraphQL or really anyone to be able to query the graph, to be able to use, to be able to just ask
the graph, hey, how can I find out how many users, are in this organization?
00:13:52:22 - 00:14:17:06
Cameron
Hey, can I get this user's name and it can spit out the query and help them run that query
against the graph. And that's something that personally I feel like will really empower and allow
even people who are super familiar with graphQL that haven't worked with that specific schema
before and might not fully know the schema. It might.
00:14:17:06 - 00:14:29:06
Cameron
It will be a faster way for them to find new queries to figure out the data they need, and to
actually activate and use that data.
00:14:29:09 - 00:14:56:05
Jens
Yeah, this is a good point because, So one use case we give the we give people access to the
API that are not really developers, business people. That is one use case. And they they might
not even know how to write a query for them. It's it's truly helpful because they can have a chat
interface to, to talk to the, the, the API.
00:14:56:07 - 00:15:09:03
Jens
That's helpful. But also for developers. If you look for example, at, let's say you have a schema
like, GitHub, how big is the schema? Do you know that on top of that.
00:15:09:06 - 00:15:13:09
Cameron
It's like 336,000 tokens.
00:15:13:12 - 00:15:15:05
Jens
Okay. So lines of code.
00:15:15:08 - 00:15:24:17
Cameron
And lines of code, I want to say it's like this. I'm not 100% sure. Actually. I think it's like 1500. It's
in the thousands.
00:15:24:19 - 00:15:56:22
Jens
Okay. In the thousands. And like obviously you it's it's impossible to to quickly weed through
that. And so what we could now do is we could go to the GitHub documentation and search and,
and probably they have a good search function like every API should have a good
documentation. But at the end of the day the question is will every company build GitHub level
documentation for every API they, they have?
00:15:56:24 - 00:16:24:12
Jens
We think that's it's kind of hard to, to accomplish. And then there's this other question. If you
have GraphQL schemas with, I don't know how many thousands of, of lines of code, how can
you actually navigate that? But because even if you're a dev, even if you know how to write
GraphQL queries. How do you how do you efficiently navigate, a big, a big GraphQL schema
and understand.
00:16:24:12 - 00:16:56:18
Jens
Okay, how how can it help me? How can it solve my problem? And you could now say, it's it's
easy, simple, simple problem. I just take the schema, I dump it in my file system, and, I just ask
ChatGPT to to look through that, and then we're done. Right? Is it so easy to to do that or what
what what are the challenges working with like
00:16:56:21 - 00:17:04:24
Jens
If we build an application that looks at the GraphQL schema, and then we have a use case and
it should give us a query, well, where's the challenge?