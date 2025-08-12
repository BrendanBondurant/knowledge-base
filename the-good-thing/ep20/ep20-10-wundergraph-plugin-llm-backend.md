---
title: WunderGraph Plugin System and LLM Backend
slug: ep20-10-wundergraph-plugin-llm-backend
series: The Good Thing
episode: 20
chunk: 10
participants:
  - Stefan
  - Jens
segment: Product Development and Company Updates
timecode: 00:51:10:06 – 01:01:08:19
start_time: 00:51:10:06
end_time: 01:01:08:19
speakers:
  - Stefan
  - Jens
topics:
  - WunderGraph's new plugin system architecture
  - LLM-optimized backend development approach
  - GraphQL vs REST API integration strategies
  - Product development and federation evolution
tags:
  - plugin-system
  - llm
  - graphql
  - rest
  - federation
topic_tags:
  - wundergraph
  - plugin-system
  - llm-optimization
  - backend-development
  - graphql
  - rest
  - federation
entities:
  - WunderGraph
  - Stefan Avram
  - Jens Neuse
  - GraphQL Federation
  - Plugin system
mentions:
  - New plugin architecture
  - LLM-optimized development
  - GraphQL adoption challenges
  - Federation without GraphQL
summary: Introduction of WunderGraph's new plugin system designed for LLM-optimized
  backend development, discussing how it addresses GraphQL adoption challenges while
  maintaining federation benefits through alternative approaches.
---

00:51:10:06 - 00:51:27:08
Stefan
Now it's fair point. Some guy, posted today actually on LinkedIn, you'll see it. He was just saying
how important it is to build a brand. And I think he misunderstood. Like there's the brand and
there's the distribution. And like we we can talk about the next episode. I do want to save a little
bit of time. So we're working on something new.
00:51:27:10 - 00:51:50:13
Stefan
It's already kind of out version one. We don't know what we're calling it yet. It's a new product.
It's plug ins, it's connectors, it's connect. We're still working on the name, so if you guys have
any suggestions, that'd be great. But yeah, just tell us a little bit about it. Like and we can talk a
little bit about the problem that we see with the famous word GraphQL and where we're going
with this new product.
00:51:50:13 - 00:52:01:08
Stefan
But tell me a little bit about it. I've not been as close to the team that has been building it, but
what first of all, what's the name for it? And second of all, what problem does it solve?
00:52:01:10 - 00:52:34:00
Jens
So so currently the name is plugins. But I think the name is it's not yet the right name. We're
we're taking it slow. It's not so important to figure out the right name. But at this time, let's, let's
say it's just plugins. Okay. So here's the problem we're solving. I think for us, for our customers,
for hopefully our viewers as well, the value of a super graph is super clear.
00:52:34:03 - 00:52:58:07
Jens
So super graph if you if you know us, we have a single, GraphQL API and it brings together all
your, all your APIs so that, that is, for us, it is proven that it is much better to have a single
monolithic graph than having 1500 rest API points that you somehow stick into backstage.
00:52:58:07 - 00:53:22:06
Jens
And then it's it's very hard to use and it's it's hard to find the right API. And then you have to
manually integrate it. So, you can waste a lot of resources doing that. So the value is clear.
Super graph. Is awesome. The problem is GraphQL. And we we've been talking about this in
the past. We believe federation is a great concept.
00:53:22:06 - 00:53:53:06
Jens
So federation as a as a concept where you just say okay I have a monolithic API and I split it
into multiple parts to make it manageable and to make it scalable across multiple teams. So for
us that is federation. Federation for us. What it's not it's not tied to GraphQL. And we also think
that that potentially one of the biggest adoption hurdles for Federation is GraphQL because you
force everybody to do, GraphQL.
00:53:53:06 - 00:54:21:00
Jens
Well, while, the real value comes from Federation. Okay. So let's talk about the plugin system
we have built because, you know, if you, if you if you know us a little bit, we're extremely
customer focused. We absolutely love to, to pair up with our customers. And we have like,
regular catch ups every, every week, every second week with them.
00:54:21:01 - 00:54:45:28
Jens
And we try to figure out, okay, well what is the well, how can we help you. So federation is great.
GraphQL an adoption hurdle. How can we help our customers to bring all their legacy REST
APIs? Everything that is not yet, a GraphQL subgraph. How can we bring that to the graph so
that they that they can, can leverage it?
00:54:46:00 - 00:55:12:00
Jens
And the architecture or the solution we came up is, it's actually very interesting because I would
say we we this is one of my, blog posts we will publish soon. We accidentally created a backend
framework for LLMs. And so, what we did is we created a workflow where you define, a schema
for, federation subgraph.
00:55:12:02 - 00:55:51:09
Jens
You take the schema, you run it through a compiler, and the compiler turns the GraphQL SDL
into a protobuf definition for a gRPC service. And, essentially what we're doing is we take
GraphQL federation, we take the subgraph out of the subgraph, and we move the subgraph into
the router. So that means from a subgraph perspective, all you have to do is you implement a
gRPC spec and then youre, you're essentially done.
00:55:51:11 - 00:56:16:01
Jens
And now the the last part we had to solve is okay, where do we actually run this. Because it's
more or less like a proxy function. And we, we don't really want to to have you run a separate
service for it. It would just complicate the thing. Imagine you have 1500 REST API endpoints.
Do you want to to run like 500 or something.
00:56:16:03 - 00:56:43:19
Jens
Backends just to proxy. No you probably don't. Okay. So what we figured out is there's, a
solution, from from HashiCorp. It's an open source library. It's called, goplugin. And what it
allows you to do is you have a host process, in our case, the router. You give it the plugins,
which are, they are, compiled, go, go, applications.
00:56:43:19 - 00:57:08:23
Jens
So they are binaries essentially. And the main component, the router, it will have, it will manage
the lifecycle of these plugins. So it will start them and connect to them, etc.. And then what
happens is between the router and the plugin we have a Unix domain socket which we use to
very efficiently talk gRPC, which is also secure.
00:57:08:25 - 00:57:33:01
Jens
And then as a result the workflow we can now do this if we want to add a Rest API or a Soap
API or, an Excel spreadsheet, or it doesn't really matter what, we create a schema and this
schema, we then run through the compiler. Now we have the gRPC plugin interface, the the the
protobuf.
00:57:33:03 - 00:58:20:01
Jens
And we have figured out how to use, cursor to build, certain cursor rules that really constrain
what the llm should do. And with those cursor rules, you can give cursor a single prompt and it
will implement for you a proxy from any JSON, http, API, to your, to your, to the gRPC protocol.
And yeah, what, what the benefit of that is essentially we can we can now drive the cost of
adopting a super graph to, to more or less, zero because it, it costs you a prompt or two, to
migrate an endpoint to, to the super graph.
00:58:20:01 - 00:58:51:17
Jens
And it's, super easy to do. And if you compare it to other solutions, there's for example,
connectors from Apollo. The problem with connectors is it's, it's a declarative way. You have like
directives you put into the schema. And we can like next tine. We can also talk more about that.
But you have these directives. You put them into the schema and then you don't exactly know if,
if if it's right is it working with our approach you can just write tests and you can you can see is it
is it working.
00:58:51:17 - 00:59:21:01
Jens
You can mock the API. And this declarative approach, it simply doesn't align very well with, with
AI because, what we do is you define the contract and you do give a very good prompt to an
llm. What to do. And it really doesn't it, it doesn't depend on what kind of API you have. If your
API supports batching, for example, we one problem we have to solve is the N plus one
problem.
00:59:21:01 - 00:59:42:18
Jens
Like if you have a list of items and for each item you have to fetch another thing. If your rest API
supports batching, that is very possible. The problem will be this it. It won't be following some
specific spec, so you can't just build out-of-the-box features. To support that, you need to
somehow build an adapter.
00:59:42:20 - 01:00:28:28
Jens
And this adapter. Ideally it would look at the open API spec or whatever you have from your
service and then writes code to adapt it. And this is a perfect task for for LLM. And so to tie this
back to like the the wider story, what we've been talking about before, I really believe the, the
future of, of backend development is that we will see more and more backend frameworks that
are designed to, to be used together with LLMs, where the engineer is not just like using
autocompletion or not even using like agent mode or something and cursor, but I think we will in
the future we will see backend frameworks where you can
01:00:28:28 - 01:00:57:06
Jens
you can essentially define your specification. You can then prompt the solution to implement this
new functionality in a certain way using a certain database or something. And then there will be,
a process that generates this, this code. And then yeah, then there's the question, why? Why
even manually write code or why? Why use cursor if you can automate it?
01:00:57:08 - 01:01:05:06
Stefan
in rust, right.
I was going to say is when we tie this all back, this new future, this plugin system, it's all written
01:01:05:08 - 01:01:08:19
Jens
So it's written in go.
01:01:08:22 - 01:01:25:08
Stefan
Just messing around, imagine though, we bring that whole debate and then we go full circle and
then we say this new plugin system, by the way, is written in rust. No, I'm kidding, we only raised
to 7.5, series A, not a 35, so we can't afford the rust developers. Jokes aside, guys, thank you
so much for joining us today.
01:01:25:08 - 01:01:30:25
Stefan
We are at the hour mark, but Jens, what's the good thing?
01:01:30:28 - 01:01:34:01
Jens
Good thing we're back in a week.
01:01:34:03 - 01:01:38:22
Stefan
We're back in a week. Thanks, guys. Have a good one. You sure you don't?