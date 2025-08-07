---
title: Open Source Enterprise Enablement
slug: ep18-04-open-source-enterprise-enablemen
series: The Good Thing
episode: 18
chunk: 4
participants:
  - Stefan
  - Jens
segment: Open source strategy for enterprise sales
timecode: 00:20:00:08 – 00:26:47:12
start_time: 00:20:00:08
end_time: 00:26:47:12
speakers:
  - Stefan
  - Jens
topics:
  - Product-market fit definition as willingness to pay
  - Technical Advisory Board (TAB) introduction
  - Open source vs closed source enterprise sales
  - Organizational barriers to trying new solutions
  - Healthcare company eight-month blocking example
  - Bank POC limitations with play graphs only
  - Open source enabling engineer evaluation
tags:
  - open-source-strategy
  - enterprise-sales
  - organizational-barriers
  - poc-limitations
  - engineer-evaluation
  - healthcare-company
  - bank-restrictions
entities:
  - TAB (Technical Advisory Board)
  - Healthcare company
  - Cosmo
  - Banks
mentions:
  - product market fit as pain big enough to pay for
  - how to iterate and get to PMF
  - open secret discovery
  - healthcare enterprise call
  - eight months company blocking
  - different vendor market solution
  - large bank POC with play graphs
  - engineer interest vs organizational blocking
summary: |
  Stefan defines product-market fit as solving pain big enough that people pay for it, introducing the TAB concept for iteration guidance. Jens shares insights from healthcare enterprise calls, revealing how organizational barriers prevent engineers from trying solutions for months. He describes an eight-month blocking scenario and bank POCs restricted to play graphs, illustrating how open source enables engineer evaluation when traditional enterprise sales processes create insurmountable barriers.
---

00:20:00:08 - 00:20:10:13
Jens
So you would say product market fit is someone comes to your website and then they click a
button and buy the product.
00:20:10:15 - 00:20:21:27
Stefan
Product market fit is it's very different definitions, but it's you're solving a pain big enough that
people are willing to pay for it. That's my definition of it.
00:20:21:29 - 00:20:45:28
Jens
And today we want to talk a little bit about the TAB because, yeah, I think it's super important to
share some experience and how to actually get there because, you know, a lot of the time you,
you hear people saying like, yeah, you just need to find product market fit, iterate, blah, blah,
blah. But the real question is how do you how do you iterate?
00:20:45:28 - 00:21:11:20
Jens
How do you how do you get there? Before we talk about that, I want to share, like in an open
secret that we figured out because I think it's, it's just, I don't know, I yeah, I want to to, to help
others also also find out something. We had a super interesting call, I think was it yesterday or
the day before, like 1 or 2 days ago?
00:21:11:23 - 00:21:54:20
Jens
We, we had a call with a company, enterprise company in healthcare space. And, what, what we
figured out is, you know, we had discussions before about the topic of open source versus
closed source and things like that. And, what what we learned from the from the market
because it's, it correlates to, to TAB and everything but one, one big thing we learned and we
we we took a bet on this is when you think about enterprise sales, one of the biggest hurdles in
enterprise sales is there are engineers in a big organization.
00:21:54:22 - 00:22:28:23
Jens
They are interested in solving a problem, but they cannot try it out. They cannot learn about
your solution. They cannot get experience because their organization blocks them from trying
something out. So we were talking with them and they were looking into another solution from
another vendor, like different market. They were trying to try. They wanted to try it out and for
more than eight months, their company blocked them from doing anything.
00:22:28:25 - 00:22:59:16
Jens
And we we see this with with other companies as well with banks or something where we're,
we're simply like, yeah, they they want to do something. They want to try something. It's
ridiculous. But we, we, we had a sales conversation with, with a very large bank. And, what they
did is they did a POC with Cosmo, but they couldn't use their own graphs because during a
POC, they can only use like, play graphs.
00:22:59:16 - 00:23:34:22
Jens
So they, they kind of used, like, dummy subgraphs just to get experience with, with the, with the
software. And in both cases, the enabler to even get to the point where we can talk to them,
where they can build the experience with Cosmo, the enabler was open source. And yes, we we
did this in the past or we we did a we made a bet in the past and we were like, open source is
the right way, especially for for infra like we want it to be simple.
00:23:34:22 - 00:24:13:25
Jens
People should be able to try it out. And as it turns out, open source is is such a big enabler, for,
for enterprise sales, because open source means if you are in this healthcare company and you
you don't have to wait like eight months or longer to get, permission to, to to sign up with a
proprietary service, you can just download it, you can Docker run it and I think, you know, one of
the biggest fears of people with open source is, but how will people pay for this?
00:24:13:25 - 00:24:44:15
Jens
Or will they ever pay? And to, to answer the question, or to, to to answer something to, to that
fear. I think there's two components. One component is there will be people who won't pay you
ever. And you just have to accept it because if you make something open source or closed
source, if you make it open source, they will use your solution.
00:24:44:18 - 00:25:08:16
Jens
If you make a closed source, they will use another open source solution. So you can decide if
they should use your solution or something else, but they still won't pay you. And then there's
the question. If you have a managed offering, is there any value in the managed offering? And
for example, in our managed offering, like Cosmo, it's complex.
00:25:08:16 - 00:25:37:17
Jens
You have key cloak, you have Kafka, you have clickhouse you have other components. And for
some people, there's enough value in having this managed. And then what we are also doing is
we have, a line, for example, we say in our cloud version, you, you will not get, like advanced,
role based access control or you will not get things like SSO or skim or you will not get audit
logs or something.
00:25:37:23 - 00:26:05:24
Jens
We think that's like an enterprise feature. So there is like a, like a line and then people can
decide, okay, do I want the managed solution with those extra features, or do I, do I not care?
Another capability we are offering on our cloud is for every customer we have, a schema
registry internally, like a private repository where we, where we store all schemas and all
operations for all customers.
00:26:05:27 - 00:26:30:20
Jens
So before every single release, we're testing automatically against all their schemas that this
new release won't break anything. So we can tell our customers like you can you can safely
upgrade to this version, depending on what kind of company you are, this can be valuable. If
that's not valuable for you, it's it's fine. Like you don't have to buy.
00:26:30:20 - 00:26:47:12
Jens
I.
So, Yeah, just just wanted to, to bring up like the, the topic of, of open source. And I think our
open source is an enabler for, for an enterprise sales funnel. Stefan. Any any comments? Yeah,