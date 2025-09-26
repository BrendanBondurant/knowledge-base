---
type: podcast-chunk
title: Monoliths vs Microservices in Practice
slug: ep17-03-monoliths-vs-microservices-in-practice
series: The Good Thing
episode: 17
chunk: 3
segment: Practical comparison of monolith vs microservice architectures
timecode: 00:10:29 – 00:15:20
start_time: 00:10:29
end_time: 00:15:20
speakers:
  - Stefan
  - Jens
topics:
  - Microservices
  - Monolith
  - Problem-Solving
  - RPC Contracts
tags:
  - microservices
  - monolith
  - ai
  - cosmo
  - federation
  - go
  - graphql
  - graphql-federation
  - kubernetes
  - rest
  - startup
  - typescript
entities:
  - Ruby on Rails
  - GitHub
  - Cosmo
  - WunderGraph
  - buf connect
summary: Jens critiques the trend of small teams adopting microservices prematurely,
  arguing that monoliths like GitHub's Rails implementation have better scaling stories
  than complex microservice architectures. He advocates for boring, problem-focused
  solutions, using WunderGraph's Cosmo as an example of a successful single backend
  with RPC contracts that serves multiple clients without unnecessary architectural
  complexity.
---

00:10:29:05 - 00:11:01:07
Jens
And this is something I think a lot of people, they, they got tricked a little bit into, into following
microservice patterns or trying to adopt modern patterns. For example, I would say one, one of
the biggest anti-patterns you can establish in, in, in service architecture is you have one single
team and you're, oh, you're thinking and let's say you were five developers and you're thinking,
microservices seems modern.
00:11:01:09 - 00:11:30:23
Jens
Let's build a microservice architecture and split out certain functionality into a separate service,
because we want to make it scalable or something. And yeah, I mean, there's many stories of
companies that have used something like Ruby on Rails, for example, GitHub. And they scaled
very, very, very well. So there's a lot of these stories where people will be like, oh yeah, we have
a monolith.
00:11:30:23 - 00:12:02:24
Jens
It's scaled to a certain degree, like now we have some problems, but it it scaled really well for
us. There's very few stories of companies that say, oh, our company completely messed up.
Like, we, we went bankrupt because of our monolith. I have never heard such a story, but there
will be many stories where people say, well, we we we messed it up with complexity and now
our microservices architecture is too hard.
00:12:02:26 - 00:12:29:13
Jens
Because the point is, if you are a single team, five devs, why do you need to split anything into
another service? Why can't you just focus on solving the problem? And solving the problem
typically means just create a boring monolith, solve the problem, move forward. For example, in
in in our architecture we have Cosmo, we have one backend.
00:12:29:13 - 00:12:55:12
Jens
It's called control plane. And it's one backend and it's it's okay. We have like an RPC contract,
this RPC contract, it's it's we use buf connect to implement this. And it can be called from our
front end. And it can be called from the CLI. And that's okay. We can generate clients and go in
TypeScript and we call it a day and that's it.
00:12:55:14 - 00:13:09:19
Stefan
Question though. Have you ever worked or seen a company that started with the microservice
architecture and it was success was successful? Or maybe we read about a blog where they
from the beginning, they started with the microservice architecture and it was successful.
00:13:09:21 - 00:13:15:25
Jens
So I did that in the past, and the project was killed.
00:13:15:27 - 00:13:35:24
Stefan
So I don't know if you would say that was a success, but I mean, it's interesting, like I hear it all
the time, we'll talk with people and they're like, oh, we're we're preparing for scale. And it's like,
why don't you hit scale first and then deal with the problems that come from it?
00:13:35:26 - 00:14:25:04
Jens
I mean, I can speak for myself, if you are, I don't know if every engineer has this journey. But for
me, I made a I mean, you you know me quite well over the years, and I made a huge journey
from being obsessed about tech to. So that was my past. And now being obsessed about
solving problems and figuring out how, how much deeper can we go in the problem space and
what else can we do for for customers and, I kind of transitioned from thinking so much about
tech and more thinking about what can we enable, what what can we achieve together with our
with our customers?
00:14:25:06 - 00:14:51:25
Jens
Nowadays I find it more interesting to, to building like a great product and to solving the hard
problems for our customers. Not so much. How do we do it? Like which tech? But yeah, I guess
like a big problem some developers have like me in the past is we read these blog posts from
Netflix and whatnot, and then we're like, oh, I also want to be like an engineer from Netflix.
00:14:51:28 - 00:15:20:23
Jens
I also want to use Kubernetes. I also want to use go and microservices, and I want to use
GraphQL and Federation and Relay. And yeah, I, I don't know, maybe it's a little bit of, of resumé
driven development. Maybe it's a little bit about about hype. Maybe it's anxiety. Like you need to
stay up to date with the stack or something.