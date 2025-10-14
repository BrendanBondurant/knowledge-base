---
type: podcast-chunk
title: Apollo Summit Recap and Analysis
slug: ep30-13-apollo-summit-recap-analysis
series: The Good Thing
episode: 30
chunk: 13
segment: Apollo Summit Discussion
timecode: 00:42:52 – 00:47:23
start_time: 00:42:52
end_time: 00:47:23
speakers:
  - Stefan
  - Jens
topics:
  - Apollo Summit Announcements
  - APM Templates
  - Kubernetes Operators
  - Execution vs Marketing
tags:
  - apollo-graphql
  - graphql
  - federation
  - observability
  - kubernetes
entities:
  - Apollo GraphQL
  - Apollo Summit
  - APM
  - Kubernetes
  - Observability
summary: The hosts react to Apollo Summit announcements. Jens finds most updates incremental, discussing APM templates, Kubernetes operators, and differences in execution versus marketing.
---

00:42:51 - 00:42:52
Jens
Well said, well said

00:42:52 - 00:43:14
Stefan
And one of the other topics I wanted to talk about is it's interesting, Apollo Summit was a couple days ago, and funny enough, we didn't do any pranks this time. I think we should have. But maybe next time, we'll see, even if there is a next time. But Apollo announced some things and. Jens  what is your unfiltered take on what they announce?

00:43:14 - 00:43:27
Stefan
If I'm completely honest with you, I was a little bit underwhelmed and some of their announcements wasn't thoroughly impressed. But from your point of view, what are some of the things that you thought were interesting or did you think anything was interestin From the summit?

00:43:27 - 00:43:31
Jens
There was a blog post, do you have like a link or something?

00:43:31 - 00:43:34
Stefan
Let me get it one sec.

00:43:34 - 00:44:01
Jens
Because like in general, I think, there were some interesting topics. 111 interesting topic. was like templates for, for for observability tooling so that you can easily see or easily set up like new New Relic and Datadog. It's actually a problem that we have as well. We we keep teaching our customers how to do it.

00:44:01 - 00:44:23
Jens
Then they announce, but this is like a small, like, incremental thing. Then they announced, an operator very interesting concept, actually, in the Kubernetes space. It's quite an old concept. I think like five years ago or something, we, we started seeing, operators. Someone sent me something. Right? Did you?

00:44:23 - 00:44:29
Stefan
Yeah, I just sent it to you. So I sent you, everything that they announced in the blog post.

00:44:29 - 00:45:00
Jens
Okay, let me see. So MCP server. Yeah, we have MCP then graph runtime APM templates I think that's a that's a good thing. It, improves the, it improves the developer experience for, for platform teams. Also the operator, that that's also very interesting to to make deployments better. Like operator kind of goes hand in hand with graph artifacts where you publish, you publish an artifact and it contains the schema and everything.

00:45:00 - 00:45:24
Jens
That's super funny because it's actually something we, we also looked into in the past we haven't executed yet. But one thing we we figured out is that some of our customers, when they build the subgraph, they take the schema, stick it into the OCI, into the Docker image, and then when they deploy the service, they kind of use OCI tooling or Docker commands to pull it out again.

00:45:24 - 00:45:57
Jens
So that's that's kind of interesting. We, we will also add something very similar in the future. Yeah. Apollo connectors enhancement. We talked a bit about connectors. Let me see MCP tools. Yeah we, we have MCP for, for quite a long time. I think one of the biggest, differences in, of Apollo and Wunder Graph is they, they do marketing a bit louder, but okay, that's, that's, that's, fine.

00:45:57 - 00:46:24
Jens
And, other than that, you know, when, when when people tell like and I answered, that's in the beginning. But when people say like, oh, wundergraph is, is not bullish on on federation anymore, like who is bullish on federation. And I, I don't see the improvements like what we're building with eBay. And we have more more things to go.

00:46:24 - 00:46:58
Jens
I don't know. There's there's features like defer for example, if you, if you look into into defer like Apollo is really good at marketing things that they have, but they actually don't really have them. Because if you compare the implementation of like, there's this old it's a, it's a Node.js gateway from the guild, which I guess it kind of has like one of the best, implementations of, of federation, actually, or the most complete.

00:46:58 - 00:47:23
Jens
Like it's not like super fast because it's, it's Node.js, but it's quite complete. And if you compare how they do defer versus Apollo router like Apollo router support for the defer, it's like very dumb. And it cannot really split complex queries. It doesn't really defer. But they have it in the, in the marketing. And I think that's like a theme that I see with Apollo.
