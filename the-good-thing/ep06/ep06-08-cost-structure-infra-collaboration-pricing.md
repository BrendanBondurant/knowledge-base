---
title: Cost Structure, Infra vs. Collaboration, Pricing, and Value Alignment
slug: ep06-08-cost-structure-infra-collaboration-pricing
series: The Good Thing
episode: 6
chunk: 08
participants:
  - Jens
  - Stefan
segment: Cost structure, infrastructure vs. collaboration, pricing, and value alignment

timecode: 00:20:15:18 - 00:23:31:29
start_time: 00:20:15:18
end_time: 00:23:31:29
speakers:
  - Jens
  - Stefan
topics:
  - Cost Structure
  - Pricing Alignment
  - Infra vs Collaboration
  - Customer Value
summary: |
  Jens and Stefan discuss the cost structure of infrastructure and collaboration tools, pricing strategies, and the importance of aligning value with customer needs in the startup landscape.
tags:
  - ai
  - cosmo-router
  - postgres
  - startup
  - api-design
  - cosmo
  - database
  - go
  - llm
  - open-source
  - rust
topic_tags:
  - startup
  - ai
  - cosmo-router
entities:
  - Stefan Avram
  - Jens Neuse
  - IBM
  - Apache
  - Mark Zuckerberg
  - Meta
  - OpenAI
  - Llama
  - Monday.com
  - Miro
  - Postgres
  - S3
mentions:
  - open source history
  - SaaS vs open source cycles
  - infrastructure ownership vs collaboration
  - cost correlation with success
  - data center deployment
  - enterprise licensing models
---

00:20:15:18 - 00:23:31:29
Jens
So if more people use subscriptions, we can find the bugs and we can make it better and we
can make it faster and correct and everything. And so if you put an enterprise license on top of
your infrastructure component, it just means you're now reducing, the possibility that more
people can use it. So less people use it.

Less people tell you about bugs and you're not improving it. And we want to have the best
router. So how do you get the best router. Make it free. Let's everybody use it. And the you know
the the business model is not like selling a license for a router. Because honestly, I don't believe
that anybody wants to pay license fees for a router.

You know, look at engine X. Sorry to go on the on the rant, but look at engine X, engine X, it's at
the very beginning. It was the most amazing thing. Like it powered so many websites. Then they
got investment. And the investors obviously they want to have a return on invest. Like hence the
name investors.

So they created like I don't know, engine X plus or some other weird things. And nobody wants
this. Like I just want to deploy engine X like leave me alone. I don't want extra. I also don't want
license because like, I don't like it. So I don't know. Our our philosophy is just yeah, everybody
just use the router.

If you don't want to buy our cloud it's it's fine. Then we need to think as a company. Why is it not
better? Why are we not providing value. And but that's our problem. That's not your problem. So
yeah, that's my my mini rant. Making ingfa components enterprises.

Stefan
There's a lot to unpack there, if you remember. So I did a conference talk at, API Days Austin,
and it was about the importance of open source. And when I was preparing for that talk, a lot of
the research that I was doing was on the history of open source. And when the first, like,
software was kind of issued, it wasn't like licensed.

It was source code. You would pay for the source code. And then somebody was like, we should
license it out. Like, I will pay you to get the license to get the source code. And then came open
source. And this happened because big enterprises like IBM were like, oh my God, we can
make so much money by putting a license behind our source code and then licensing it out for
companies to use.

And then came the, the Apache web server and came a bunch of other open source tooling, and
it completely destroyed that model. And so we went through this cycle that was like source
code, open source. That's not going to work with the source code anymore. And then we went
back and then we started with SaaS. And if you remember from like 2005 I would say to 2015
like ten years SaaS was dominating.

There was absolutely dominating us. Open source kind of took a step back. And then 2015 to
2020, open source started making a comeback. And what I'm trying to bring home is one, if you
ever want to learn about anything, learn about the history, because you can start to see trends
that happen in the future, because history tends to repeat itself.

It's fantastic. And two, it's happening right now. Mark Zuckerberg released, the their llm model
llama as open source. And what he said is that LLMS need to be open source, and it's not to
compete with open AI. It's not to use it as a marketing funnel. Because fundamentally, if you
want to win in this game, you can't have proprietary stuff on people's data centers.

You can't have proprietary stuff in their infrastructure. They want open source. And what's great
about that is that when open source is used in the correct way, you're not just in one data
center, you're in thousands. You have thousands of use cases, thousands of experiences,
thousands of industries. You're not limiting yourself to one data center with one license.

You're all over. You've created this moat of information, which is absolutely fantastic. And I think
you're absolutely right. And we talk about this a lot. So explain to me, like what you told me all
the time about with like Monday.com, with Miro, with collaboration. And they don't do anything
with infrastructure, but they make $3 billion a year. Where, where is the emphasis in
companies?

Stefan
What do they actually want to solve?

Jens
So the the way we think is there's, there's like two, there's like 2 or 2 ways to, to, to think about,
the, to think about components. So you have one area of components. We, we consider this
infrastructure infrastructure for example. It's a database. It's Postgres. It's it's S3, it's cosmo
router like a router engine X, these kind of components.

And then there's software for collaboration, for example Jira, linear, slack, etc. like, all these
collaboration things like GitHub, there's people, they work together. It can be all sorts of people
like technical, non-technical product owners, etc.. And then on the infra side, you have these
components and that for, for us, the I would say one one, one big observation from the market is
collaborative tools.

People want to use them and they want to collaborate. And infrastructure tools like a router,
people want to own them. They want to have control. It's about trust. It's in our data center, in
our VPN. It's it's in our VPC. It's it's our data. We want to control it. We want to customize it. We
want to own it.

And so, there's also a component to, data volume. So for example in these collaborative tools
like JIRA or linear or whatever, if you have 100 devs working and you have, you have not so
much success yet as a company, you pay for this 100 devs. But if you then build a very
successful product and you scale it out and you're still 100 people, you pay the same amount.

So the cost on collaboration, it doesn't correlate with your success. And then if you look at infra
in the, on the infrastructure side, if you have no users, the cost of your infrastructure is is not
zero, but it's kind of low. Like you need a database, even if it's empty. And if you scale up, if you
are more and more successful, your infrastructure bill, it can skyrocket.

And the big problem here is if you have middlemen in the infrastructure layer, that puts a huge
margin on top of on top of compute. That is that is driving up your cost. And so what we see is
that, like the most expensive asset in your company, it's your it's your people like the, the, the
HR cost.

And because they are so expensive, you want to give them powerful tools for collaboration so
that they as a team can scale and they can work together very well versus on the infrastructure
side, the goal of the company is always to drive down the infra cost. And simply put, it is very
hard to do this. If you have this like these wrappers or however you want to call them.