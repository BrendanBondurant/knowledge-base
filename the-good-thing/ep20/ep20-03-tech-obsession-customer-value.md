---
title: Tech Obsession vs Customer Value
slug: ep20-03-tech-obsession-customer-value
series: The Good Thing
episode: 20
chunk: 3
segment: Technology Philosophy and Customer Focus
timecode: 00:12:00 – 00:18:25
start_time: 00:12:00
end_time: 00:18:25
speakers:
  - Stefan
  - Jens
topics:
  - Tech Obsession
  - Customer Value
  - Software Complexity
  - Pragmatic Development
tags:
  - startup
  - ai
  - apollo-graphql
  - cosmo
  - cosmo-router
  - founder
  - go
  - graphql
  - observability
  - rest
  - rust
  - telemetry
  - typescript
entities:
  - Stefan Avram
  - Jens Neuse
summary: Discussion of the tension between technology obsession and customer value
  delivery, exploring how software complexity affects business impact and the importance
  of balancing technical excellence with pragmatic, customer-focused approaches.
---

00:12:00 - 00:12:21
Stefan
It's a misguided take. And I mean, it's interesting to be honest. I've seen Jens blow up on
Twitter. Twitter is very easy to get bait. I was a little surprised. I mean, LinkedIn, I've never seen
a blow up like this, but overall there are some like more interesting points. And to here I think
you got how many comments that it got like 70 something comments.
00:12:21 - 00:12:40
Stefan
Yeah. And what's what's good about this is that it encourages debate. But one of the things I
wanted to highlight is that and we've seen this and I've been seeing this a lot, which is let's
switch back to this view. Why are people so obsessed with the tech like we can talk about said
competitor who's obsessed with the tech?
00:12:40 - 00:12:58
Stefan
And it's like, I understand coming from a developer mindset, and one of the things I've seen with
the Jens over the years is he's become less focused or cares about the tech, and just more
about the business value and what the customer solves. Then at the end of the day, rust is just
a tool in your box to solve a problem for ideally a customer.
00:12:58 - 00:13:16
Stefan
Is it the right tool? Maybe, but it's what Jens said. Are you going with the M3 or are you going
with the formula one car? It completely depends on your use case, but I don't know. So many
startup founders, especially technical ones. I see them too obsessed with the tech and then the
actual best founders that I've met who don't care about the tech.
00:13:16 - 00:13:22
Stefan
They care more about the impact that they're making for their customers. That's interesting.
What are your thoughts?
00:13:22 - 00:13:56
Jens
Yeah. In 2018, I started writing GraphQL go tools, a library to build GraphQL gateways and
proxies. And I was absolutely obsessed about GraphQL and everything. And, I wanted to solve
everything with it. These days, I would say I'm, I'm, I'm leaning more and more. I, I wouldn't
agree to what you said when you mentioned, I don't care about tech anymore.
00:13:56 - 00:14:22
Jens
I would say I still like it's not just tech for me, but I find much more enjoyment in in working
together with customers and figuring out how can we how can we help them better. And most of
the time it it's not so important what we use behind the scenes TypeScript, react, go whatever
rust they they don't care.
00:14:23 - 00:14:47
Jens
They care about, the job that needs to be done and, yeah, but if you if you think about the
customer and you go backwards from the problem to the solution and you think about, you
know, if you if you maintain software for a couple of years, you kind of realize that, every feature
you put into that, nobody really benefits from.
00:14:47 - 00:15:20
Jens
But some people use and complain about, it's, it's it has a cost. So yeah, you you need to be
super careful in every feature. You accept you support. It's kind of like you put it in the in the
back. You have to shoulder it over many years. You have to maintain it and it can become a
burden. And so, in terms of the, the talent and everything, yeah, ideally it's easy for you to
attract, the right talent to get people to, to use your software.
00:15:20 - 00:15:48
Jens
And to give you an example. Why why I think go is an excellent fit for us. We we, so Cosmo
router, we have a couple of, of things that are super important for the enterprise. One is, support
for Prometheus, and the other one is support for Opentelemetry, for observability. And, both are
implemented in go have excellent support in go.
00:15:48 - 00:15:55
Jens
And so for us, it's actually the the best ecosystem to to be in that this is written in go.
00:15:55 - 00:16:15
Stefan
No thats well said. one question. Or do you think it's also a moat to make your software
complex. So for example, building it in rust so that it's harder for competitors to replicate, or
having these highly paid specialists that can only work on it. Is it also a moat, or could it be a
moat?
00:16:15 - 00:16:42
Jens
It, I'm not sure. It depends. So one thing I know is, if you look at, if we look at, for example, in
our market, Apollo, there was, so Apollo is written in, Apollo Gateway, it was written in Node.js,
TypeScript or, I think, JavaScript, not even TypeScript. Then they rewrote it in rust.
00:16:42 - 00:17:10
Jens
It took them very, very long. Yeah. And, now they have the, the migration complete. So I think
that that's fine. And the Guild tried to, to rewrite or to, to write like a gateway in, in rust. And they
abandoned the project. And I think that's because it was too complex for some reason or
something. So, that I think that's that's an interesting observation.
00:17:10 - 00:17:15
Jens
I'm not sure if it was correlated to the, to the language or, or something.
00:17:15 - 00:17:39
Stefan
But, yeah. Yeah, that's what I'm wondering. Like, for example, like, the engineers at OpenAI or
whatever, like some of the stuff that they're working on, it's pretty complex to think that they're
using rust. And I wonder if it's like you making your software complex on purpose. It has a trade
off like one. It's harder for you to understand, but it's also harder for your competitors to
understand and to replicate.
00:17:39 - 00:17:43
Stefan
So I'm wondering if complexity can also be a moat, its interesting.
00:17:44 - 00:18:25
Jens
I think you want to have your software easy to change. Yeah. So yeah, that could be a pro for
for rust because the rust compiler, it's it's definitely pretty helpful. But yeah, a moat based on
complexity. So we know ourselves. One one of our biggest burdens is, to, to test customer
router testing is, is one of the most important things to ensure that we're, we're not breaking
anything testing in go is is is quite good.