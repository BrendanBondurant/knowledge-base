---
title: Federation Audits, Benchmarks, and Ecosystem Bias
slug: ep07-14-audits-benchmarks-and-bias
series: The Good Thing
episode: 7
chunk: 14
participants:
  - Jens
  - Sergiy
  - David
segment: Third-party audits and benchmark reliability
timecode: 01:14:15:10 – 01:20:04:28
start_time: 01:14:15:10
end_time: 01:20:04:28
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - Third-party audit value and limitations
  - Vendor benchmark bias and marketing purposes
  - Federation complexity and edge case discovery
  - Customer-driven importance vs vendor priorities
  - Infinite directive combinations and testing challenges
tags:
  - startup
topic_tags:
  - audits
  - benchmarks
  - vendor-bias
  - federation-complexity
  - customer-experience
  - third-party-evaluation
entities:
  - Federation
  - Apollo
  - WunderGraph
  - Sergiy
  - David
  - Jens Neuse
mentions:
  - third-party audit benefits
  - vendor marketing motivations
  - infinite directive combinations
  - customer experience focus
  - edge case discovery challenges
  - reliable customer solutions
  - downtime prevention
summary: Critical discussion of federation audits and benchmarks, with Sergiy highlighting
  the value of third-party perspectives while David emphasizes that vendor-created
  benchmarks serve marketing purposes. Both agree that the only trustworthy benchmarks
  are ones you create yourself, as federation's complexity creates infinite combinations
  that no single vendor can fully address.
---

01:14:15:10 - 01:14:42:16
Sergiy
Second topic. It was about the audit. Yeah. I know in particular what audit you are talking about,
it is actually interesting. Like I have also my own opinion about that and this opinion not related
to the audit itself. It is kind of like, related to the evolution of, Federation itself.
01:14:42:19 - 01:15:10:28
Sergiy
And, it's everything about the customer experience and customer like way of thinking. Yeah.
Actually, you do not have a lot of directives in Federation, I believe. I'm not sure which could be
safely removed because it's highly adopted right now. But, the important thing is that there is ton
of, combinations. How you could apply them.
01:15:11:00 - 01:15:44:06
Sergiy
And, the more subgraphs you have, the more complicated they are. It is much more or less
predictable. And, it is hard to, to find all these edge cases, but, probably it is more simple when,
you just have a graph and to have some basic set of rules, how you interact with that. But, it is
will be like you just need to implement it right.
01:15:44:08 - 01:16:14:02
Sergiy
In this graph and you may not even know how customers will use your, implementation in which
way they will use it. And, yeah, this is a problematic. So, audits, somehow could also biased, but
they are very useful because in case they are done by a third party company, like, will not
involve it in your approaches, in your relations with customers.
01:16:14:04 - 01:16:43:00
Sergiy
It's actually a very good thing because it just whole lot, different point of view, into this area. And,
it is useful to have different points of view and, it really could show how you could improve and,
you could contribute there and, also improve, other solutions. It's kind of, so some role it is to
have the single spec.
01:16:43:02 - 01:17:05:27
Sergiy
But, until the not all the rules are defined. Each of the parties could, try to show, the bits of, this
rules and, you just at least you have some basics to, to implement something you, try to cover
some basic things and such kind of audits. It could help you.
01:17:05:28 - 01:17:29:28
David
Is that if every now and again we get a question from somebody like in one of our community
places like discord or whatever, and they ask us about, benchmarks. And typically our answer
is, the only benchmark you can trust is your own, when you when when you have vendors
creating benchmarks, you have to ask yourself.
01:17:30:04 - 01:17:53:22
David
And this includes, wundergraph as well is, is, is a vendor going to, deliver something to the
public that makes them look bad? But and the answer is that, obviously, no, you're not going to
do that. So it is a is a benchmark really capturing the reality of all situations when, the real
reason the benchmark is created is for marketing purposes.
01:17:53:24 - 01:18:18:24
David
So you have to you the only the only data you can trust is your own. And that's my first opinion.
And when it comes to things like, audits, again, if, if that's led by a vendor, and the vendor is
deciding what is or isn't important to include in said audit, they've decided what is it, not audit
what is not in the audit.
01:18:18:27 - 01:18:49:22
David
Federation is a topic that is huge and the, the, the combination of directives and different types
of graphs and, different ways to, write schemas and things mean that you have infinite
combinations. And there's not one vendor, Apollo included, anybody who can solve absolutely
every single possible thing because there are endless, endless possibilities and no one can
account for endless possibilities, no matter how good you are.
01:18:49:25 - 01:19:12:24
David
So who decides what is important is, is is one topic. What's important to, one company might
not be important to another company. And what really is important is what, customers want.
And, and every vendor has their own customers, and those customers have issues. And those
issues need to be solved or need to be, the solution needs to be reliable.
01:19:12:27 - 01:19:41:16
David
And those are the real kind of benchmarks. Is that is it working for these customers? Do they
are they able to get the, data reliably and safely? Are they able to prevent downtime and
whatever else? And there's only so much that an audit is a, or any, any benchmark or any audit
is always just, a lens on a small is a small lens that's focusing on, on a small section of the
bigger picture.
01:19:41:19 - 01:20:04:28
David
That's kind of how I see it. I could, like anybody here, could find any number of things wrong
with any of the number of vendors. You you could, you could, you could. I could create
something that makes, you know, company y look terrible because I've written that. So you
make everything that is in this is in this, audit makes that that company fail everything.