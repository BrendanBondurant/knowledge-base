---
title: SoundCloud Case Study and Open Source Moats
slug: ep08-04-soundcloud-case-study
series: The Good Thing
episode: 8
chunk: 4
participants:
- Stefan
- Jens
segment: SoundCloud partnership and competitive advantages
timecode: 00:27:51:12 – 00:36:18:11
start_time: 00:27:51:12
end_time: 00:36:18:11
speakers:
- Stefan
- Jens
topics:
- Jeff Bezos "your margin is my opportunity" principle
- Open source as competitive moat strategy
- SoundCloud engineering partnership
- Customer knowledge transfer and experience
- Multipart file upload customization
tags:
- startup
- open-source
topic_tags:
- soundcloud
- case-study
- competitive-moats
- customer-partnerships
- open-source-strategy
- engineering-collaboration
entities:
- SoundCloud
- Prometheus
- BFF Framework
- Matthew Druker (former CTO)
- Brendan (technical content writer)
- WunderGraph
- Stefan Avram
- Jens Neuse
mentions:
- Prometheus creation by SoundCloud
- BFF framework development
- former CTO podcast appearance
- 86% cost reduction headline
- $265,000 annual AWS Fargate savings
- multipart upload customization
- business goal vs hosting goals
- Suit Supply retail business example
summary: Discussion of competitive advantages through open source and customer partnerships,
  featuring SoundCloud as a premier case study. Stefan highlights SoundCloud's strong
  engineering team and their impressive cost savings, while Jens explains how customer
  knowledge and experience create sustainable moats beyond just software licensing.
---

00:27:51:12 - 00:28:26:10
Jens
Yes. Like and I think in infra, if someone creates a proprietary product with a high margin that is
billing per traffic, then you can, you can, you can set a counter and someone will build an open
source alternative. And they they will create an alternative model where self-hosting works in
some way or where they, incentives better align for people with, with high traffic.
00:28:26:10 - 00:28:46:19
Jens
And, yeah, which is one of the reasons we said like or, you know, I still remember like one and a
half year or. No, I think it's now two and a half years ago, I was on vacation and I was, you
know, every time I go on vacation, I'm thinking outside the business.
00:28:46:22 - 00:28:47:07
Stefan
And, and.
00:28:47:07 - 00:29:15:07
Jens
I, I came back and I told Stefan, no, I, I actually went on a call, like, I called you guys because I
was like, calling my co-founders and said, guys, we will make Cosmo open source 100%. And
we were debating like, you can't do this. Like we're giving away everything and so on and so
forth. But I was like, you know, I, I don't want to build this whole platform and router and
everything.
00:29:15:07 - 00:29:43:24
Jens
And then someone comes around the corner and says, open source. So, you know, we say
open source alternative to Apollo Router. And then we make the control plane closed source.
And then the next guy comes around and says open source alternative to cosmo control plane.
And I'm like, no, I don't want this to be happen. Like, I, I want everybody to to use it like, like
they want.
00:29:43:24 - 00:30:14:15
Jens
And I think our cloud service needs to be much more powerful and it needs to give much more
value than just Docker compose up. And, you know, like the these days, if you look at our cloud
stack, there's clickhouse, that's database migrations. We now have our telemetry pipeline
hosted in multiple regions. It's highly available. We have the CDN hosts highly available in those
operations.
00:30:14:18 - 00:30:41:03
Jens
We have internally. We now use Kafka to ensure that we have high throughput processing of the
telemetry pipeline with back pressure and all these kind of things. It's such a complex stack. For,
for most customers, it's it's just so much easier to. Yeah, talk to us. We we figure out, pricing
strategy that that works for everybody.
00:30:41:03 - 00:31:24:12
Jens
And, yeah, that's so we're we're not just running Cosmo. We're, we're doing more. And it's a
complex second. The question if you're if you really want to self host is do you want to, to own
all these components or do you want to use them. But that's one thing because it's open source,
it kind of establishes a level of trust, because even if we in the future, driven by VCs or
whatever, even if we decide to change course, which I, I don't intend to do because we have, a
different strategy that goes beyond Cosmo.
00:31:24:12 - 00:31:57:10
Jens
But, even if we would, you can self host Cosmo. And I think also, if you could self host
something, it somehow sets, threshold of how hard can you squeeze a customer? And I think
this aligns our values better with the customer values. Like, you know, if you if you can, if you
can self host something for, I don't know, let's say, let's say 1 million per year and we're charging
you 50 million.
00:31:57:12 - 00:32:12:01
Jens
Something is wrong. Completely wrong. And and by making it open source, we, we kind of set
the threshold to ourselves of, of playing fair. And to be honest, I think that's that's good.
00:32:12:03 - 00:32:31:04
Stefan
Yeah. And I think those are I mean, I agree with all of those. And I think the benefit of open
source is definitely on the procurement side. But also, I had the conversation with my mom, like
I first I had to explain to her what Cosmo does using the waiter example. And then, once they
got that, they were like, well, how can you sell something that's basically free?
00:32:31:06 - 00:32:50:15
Stefan
And I was like, mom, like, the mode isn't actually in the software, it's in the knowledge and the
experience of running it, but also the knowledge and experience that we bring from all of our
customers. And what I love the most about our customers is they love what they do. And we get
to work with some amazing, talented engineers, but they're also open to meeting with other
customers.
00:32:50:15 - 00:33:08:22
Stefan
So when we have a customer that's using EDFS or subscriptions, we can take that knowledge,
take it to another organization, and then they become successful subscription. And that's only
possible. I really think it's only possible through open source. And this past week we announced
a really cool customer, which I want to dive into this topic a little bit.
00:33:08:22 - 00:33:14:14
Stefan
So, I'll actually bring up let me share my screen so people can see the blog post.
00:33:14:21 - 00:33:18:23
Jens
Okay. Can I add one one thing to this mote, right.
00:33:18:27 - 00:33:21:15
Stefan
Yes, yes. Before I share, go ahead.
00:33:21:18 - 00:33:53:27
Jens
So this week a customer came to us and said we're using, we're using your. So our router has a
feature to upload files using multipart. Yeah. And they were not exactly implementing the spec.
They wanted to send the requests slightly differently. And they said we don't have the resources
to to change all our clients. Can you add a feature flag or can you somehow help us how to how
to accomplish that?
00:33:54:00 - 00:34:19:06
Jens
And here's the thing. People have business goals, like your business goal is not to host Cosmo.
Your business goal is to find a partner that helps you get this thing working. So. So ultimately,
there are there are a lot of people you don't really have to convince them to to use the service or
partner up with us because they, they are busy and they, they want help.
00:34:19:06 - 00:34:25:04
Jens
So yeah, we're, we're we're not so worried about making something opensource.
00:34:25:06 - 00:34:41:19
Stefan
If you remember the guy from suit supply when we first started talking to them. So they were
evaluating Cosmo, but then they ended up not even going to GraphQL. But we were talking with
this guy and he goes, I'm not in the technology business. I'm in the retail business. He's like, I
just buy software to get the job done.
00:34:41:21 - 00:34:58:13
Stefan
And I remember that always stuck with me because some people are in the technology
business like us, other people are in whatever business that they're in. But if it solves a
business goal, are you really in the business of hosting, building your own gateways? It's cool.
It's great, and if that's something you want to do, you should really consider applying to
WunderGraph, because that's what we do.
00:34:58:15 - 00:35:12:27
Stefan
But if you're at a bigger company and they're making you build gateways, there's a lot that you
don't even know that you don't know. And there's a lot of use cases and edge cases you haven't
even thought of yet. But if that does interest you, we are hiring across the board. So take a look
at some of our open job sites.
00:35:12:27 - 00:35:34:04
Stefan
But yeah. So Jens with that in mind, I wanted to transition into this amazing graphic that we
have. So this was written by Brendan, our technical content writer, and I am this is probably one
of the customers that I'm the most excited about. So SoundCloud. We've been working with
them for how many months now? 4 or 5 months?
00:35:34:06 - 00:35:35:00
Jens
Yep.
00:35:35:03 - 00:35:55:29
Stefan
I'd say so. And for those of you that aren't familiar with, with SoundCloud, SoundCloud is a very
strong engineering team, extremely strong. They're the creators of Prometheus, they're the
creators of the BFF framework, and they've kind of migrated over to GraphQL Federation, and
we work very closely with their team. Their former CTO, Matthew Druker. He will be joining us
on the podcast in a couple of weeks.
00:35:55:29 - 00:36:18:11
Stefan
So it'll be great to have some questions beforehand about what it's like to be a CTO. He's been
a CTO at multiple companies, and he's also, he was the CTO at, SoundCloud. But Jens, this
was super exciting from a tech point of view. I mean, the headline is a banger. They cut their
computing costs by 86%, walked me through a little bit from the beginning and, you know, keep
the details high level.