---
title: Infrastructure vs Collaboration Value and Pricing Models
slug: ep08-03-infra-vs-collaboration-and-pricing
series: The Good Thing
episode: 8
chunk: 3
participants:
  - Stefan
  - Jens
segment: Business model differentiation and ecosystem strategy
timecode: 00:19:15:04 – 00:27:51:12
start_time: 00:19:15:04
end_time: 00:27:51:12
speakers:
  - Stefan
  - Jens
topics:
  - Infrastructure vs collaboration value propositions
  - SDK vs Cosmo revenue differences
  - Impact radius and multi-team solutions
  - Per-seat vs per-request pricing models
  - Open source ecosystem strategy
tags:
  - federation
  - ai
  - cosmo-router
  - startup
  - api-design
  - api-gateway
  - authentication
  - cache-warming
  - cosmo
  - go
  - graphql
  - graphql-federation
  - open-source
  - query-planning
  - rest
entities:
  - Prisma
  - Vercel
  - Next.js
  - Neon
  - Monday.com
  - Jira
  - Slack
  - Zoom
  - Jeff Bezos
  - Stefan Avram
  - Jens Neuse
mentions:
  - cache warmer Super Bowl traffic
  - breaking change detection
  - schema checks and playground
  - collaborative value add-ons
  - procurement officer insights
  - post-Covid remote collaboration
  - your margin is my opportunity quote
summary: |
  Analysis of why Cosmo generates 100x more revenue than their previous SDK, focusing on impact radius (multi-team vs single-team solutions) and infrastructure vs collaboration value. Discussion covers pricing model insights from procurement officers who prioritize collaboration tools over infrastructure, leading to per-seat pricing strategies for enterprise adoption.
---

00:19:15:04 - 00:19:50:16
Jens
field and if it needs authentication, what scopes are required. So API discovery, sharing APIs,
sharing knowledge. Then we have the playground where you can look into query plans. You can
understand how how would the query planning work then? Other features we have in the studio,
for example, is our cache warmer, where we look into, what what are the what are the queries
you were using for the last month or so?
00:19:50:19 - 00:20:19:00
Jens
And then we build a top list of, of queries. And how long it takes to plan them. So we have that
as an analytics add on. And from this information we create, a top list of first, put this into our
CDN. And when you boot up a router or when the router gets a new config, then we warm up
the caches, reducing, the query planning time for the router.
00:20:19:02 - 00:20:46:01
Jens
This, for example, is a solution. This helped one of our customers go through a Super Bowl
event, where they had, traffic spikes. But thanks to the, to, to thanks to the, to the cache
warmer, they they didn't have query planning spikes because the caches were warm. So these
are like value add ons.
00:20:46:04 - 00:21:15:26
Jens
And it's it's super important that your managed solution has value add ons in the in the collab,
collaborative space, for example, one critical feature of of collaboration is if one subgraph
introduces a change, we will check that this is not breaking any of your clients. So. So that
means by having such a platform, you can now have many teams that make subgraph changes.
00:21:15:26 - 00:21:34:00
Jens
And nobody is breaking, existing functionality. So now more people can be added to creating
services. So that's a big collaborative value add versus one single team builds an API faster
now.
00:21:34:02 - 00:21:58:04
Stefan
Yeah, I think you're spot on with that. Is that a lot of developer tools. What they do is they they
try to solve a problem for an individual developer, but really the power is actually and when you
get it into access to teams and enterprises because they're collaborating across teams as well.
And I think you kind of sum up perfectly of like what the difference was between the SDK as well
as, between Cosmo and then on go.
00:21:58:06 - 00:21:58:19
Stefan
Can I add.
00:21:58:19 - 00:22:01:04
Jens
One, one example?
00:22:01:06 - 00:22:02:02
Stefan
Sure.
00:22:02:04 - 00:22:46:01
Jens
Prisma. So an ORM, I think Prisma for many years is trying to figure out the business model and
if you like, this is not something we make public, but we, we have like, like a product vision
picture, like, like our North Star. How the ecosystem of of WunderGraph should look like in the
future. And one key aspect is open source is good, but it's super important that an open source
component is embedded into a much bigger product vision.
00:22:46:04 - 00:23:16:10
Jens
Where there are other products that have that are in different categories, like collaboration, for
example, with, with, with much bigger enterprise impact. And so yeah, it you need to think like in
an ecosystem. And for example for us, Cosmo, it is it is one step like that's one one piece of the
puzzle or a couple pieces of the puzzle, but there is a lot more around that.
00:23:16:10 - 00:23:42:13
Jens
And then that's in the end, makes the makes this strategy work. But our understanding of the
market is that an API gateway, the goal needs to be to make it virtually free, like our long term
vision for federation routing is to make it more or less free. Like, okay, it will never be free. It has
a cost, and there needs to be a schema registry.
00:23:42:16 - 00:23:57:19
Jens
And there needs to be analytics because otherwise you cannot do breaking change detection.
So there will be some cost. But for for Cosmo, for the router and for analytics like our, our long
term goal is to to actually drive down the cost.
00:23:57:21 - 00:24:17:16
Stefan
Yeah. And I think it's a great model. And I think all successful companies eventually realize this.
But so you mentioned Prisma is maybe not the best example, but what are some companies, in
your opinion that do this really well? For me I think vercel does it great with Next.js, they made
their framework open source or free, but the value really comes from the collaborative platform
of Vercel.
00:24:17:19 - 00:24:25:16
Stefan
Neon also does a good approach on this. What are some good open source companies that
have kind of nailed down this approach that you like?
00:24:25:18 - 00:24:26:08
Jens
Yeah, I.
00:24:26:08 - 00:24:27:02
Stefan
I.
00:24:27:08 - 00:24:58:04
Jens
Like Vercel and I think Vercel also transitioned a bit, you know, if you if you remember like
Vercel two years ago, everybody was like, oh my God, it is so expensive. And the, the, the new
Vercel is implementing new techniques to drive down compute cost and everybody's like super
positive about that. And yeah. And then at the same time you can actually see that it's funny.
00:24:58:04 - 00:25:23:12
Jens
How do you see these parallels. So Vercel is looking at driving down the hosting cost of your
website. And at the same time they built these AI features that allow you to create designs and
other things. And what what is designing? At the end of the day, it's it's collaboration again,
because you have a website and you want to show someone like, hey, here's a new idea.
00:25:23:12 - 00:25:52:18
Jens
So back in, in and in, in collaboration and I think like, you know, in, in, in infra like something like
the router, it's, it's typically like low margin markets because like people have a lot of requests.
And then let's say you have like a social media platform of sorts, that means you have a lot of
free users where you need to make money and then compare that to a collaborative tool like V0.
00:25:52:21 - 00:26:23:17
Jens
You have developers, they are one of your most expensive assets. And you can you can give
them at like enhanced superpowers with AI. And so that is something where you're, you're,
you're happy to pay more because you get more value. But for the router for each request, like
billing per request, at least billing or if you're sole business model is to bill per request.
00:26:23:20 - 00:26:25:11
Jens
It's got to be tough.
00:26:25:14 - 00:26:45:00
Stefan
Agreed. And a little story that I had is I was recently talking to, like a procurement officer helping
them onboard on to Cosmo. And one of the things he said during the procurement is that, hey,
we're not buying like a slack or a zoom or a, what do they use? I think they use Monday.com or
Jira.
00:26:45:02 - 00:27:06:09
Stefan
And if you look at all those tools, what those tools allow is collaboration across the company.
Without zoom, they wouldn't be able to meet with remote workers. Without slack, they wouldn't
be able to communicate. Without JIRA, they wouldn't be able to organize the tasks. And when
you look at that, especially from what we've seen in the market, is that company's biggest
assets are their employees.
00:27:06:11 - 00:27:27:07
Stefan
And then the second biggest assets are the tools that they use to collaborate, especially post-
Covid in a remote environment. And infra is very tricky. You don't want to charge per usage, but
a little secret hack that we've seen is per seat models or collaborative tools. People are like,
yeah, that's fine. As long as we can collaborate and work together, that's totally fine.
00:27:27:07 - 00:27:39:22
Stefan
We'll definitely pay the price on that. And I think it's it's an interesting learning. It took us a while,
but when you look at it in hindsight, me and Jens are like, how could we be so dumb? It makes
total sense. Any final thoughts on that one?
00:27:39:25 - 00:27:48:01
Jens
You have this. You have this quote from I think, Jeff Bezos. Do you remember.
00:27:48:03 - 00:27:51:10
Stefan
Your margin is my opportunity.