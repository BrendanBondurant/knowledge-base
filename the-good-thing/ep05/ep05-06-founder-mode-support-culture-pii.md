---
title: Founder Mode, Support Culture, and PII Handling
slug: ep05-06-founder-mode-support-culture-pii
series: The Good Thing
episode: 5
chunk: 6
participants:
  - Stefan
  - Jens
segment: The scalability of founder mode, support culture, and handling PII in customer
  solutions
timecode: 00:27:37:26 - 00:36:27:03
start_time: 00:27:37:26
end_time: 00:36:27:03
speakers:
  - Stefan
  - Jens
topics:
  - Founder mode
  - Support culture
  - Company values
  - Customer focus
  - PII handling
  - Healthcare use cases
  - Product iteration
  - Team leadership
  - Customer collaboration
  - Native solutions
  - Security
  - HIPAA
  - JWT claims
  - Product responsibility
tags:
  - founder
  - startup
topic_tags:
  - founder-mode
  - customer-support
  - company-culture
  - pii-handling
  - customer-first
  - startup-philosophy
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
  - HIPAA
mentions:
  - founder mode scalability
  - support culture importance
  - PII handling challenges
  - healthcare use cases
  - customer collaboration
  - security compliance
  - JWT claims
  - native solutions
summary: Stefan and Jens discuss the scalability of founder mode, the importance of
  support culture and company values, and share a story about handling PII for a healthcare
  customer. They reflect on how close collaboration with customers leads to better
  native solutions and how security and compliance shape product decisions.
---

00:27:37:26 - 00:28:06:03
Stefan
So Paul Graham wrote this great, essay, and it came from him sitting at a, I guess, like a what is
it called, a fire fireside chat? And he was sitting down with the founder of Airbnb. And it's kind of
like counterintuitive, but it's also startups like startups are very counterintuitive. And so my take
on founder mode is doing what you're doing now with under 15 people.

00:28:06:05 - 00:28:36:22
Stefan
And you still do that when you have 1500 people. And for me, founder mode isn't
micromanagement. It's managing. It isn't over optimizing. It's optimizing. It's being involved in
the nitty gritty. Even when you still have 1500 people. And I think that's a superpower at the
beginning of startups is that, hey, for example, you can talk about today Jens like last week, you
went on a customer call with one of our smallest customers, and you came back with so many
insights of things that we can improve for them, that you definitely see some value for them as
well as for us.

00:28:36:23 - 00:28:49:27
Stefan
And so my definition is founder mode is doing what you're doing at the start of the startup and
also doing the same thing that you're doing when your startup is absolutely massive. What
about you?

00:28:50:00 - 00:29:27:09
Jens
To to pick up your case. I'm just wondering if you have a 1500 people organization, the CEO
should probably somehow be involved in making sure that these 1500 people do something
meaningful. Should they be doing support? I mean, yes, of course it would be super nice to be
hands on and understand the product, but you also at that stage you will also have like product
owners and yeah, I'm not sure how much you want to interfere with with these kind of people,
but yeah.

00:29:27:09 - 00:29:54:12
Jens
And then, you know, then then there's this other thing I wrote about it, like, a few days ago, the
scalability of founder mode and, I mean, for, for, for a very long time, we were a small founding
team. I would say like four founders and, and a handful of of founding engineers, and we, we
kind of expanded founder mode to this whole team.

00:29:54:12 - 00:30:17:08
Jens
And this is. Yeah, until today and even today, I would say, that that we were able to, to infect the
whole team to the to be at least somewhat informed, like I'm not expecting people to work
through the weekend or something. I that that's like, it's still a job. You have a life. It's I respect
that it's fine.

00:30:17:11 - 00:30:32:06
Jens
But yeah, I mean sometimes as a founder you you have to you have to walk the walk and thus
there's no way around. But, yeah, I, I'm, I'm not sure.

00:30:32:08 - 00:30:51:26
Stefan
I think you're right though. So at 1500 like obviously you won't be able to do support like you
won't be able to get in the nitty gritty. And you also want to hire smart people and get out of their
way. But it's what you just said. Like if you walk the walk organically, people are going to see
that and they're going to be like crap, like, look at what Jens is doing and it just motivates them.

00:30:51:26 - 00:31:10:19
Stefan
And it's like the the benefit of it is not to be a CEO is to be a leader. And leaders don't tell people
what to do. They show them what to do. And I think that's one key aspect that we have. at
Wunder Graph, is that these founding engineers have, in a way, become founders themselves.
You know, some of our engineers have shifted into parts of one graph, and they founded
something.

00:31:10:19 - 00:31:30:10
Stefan
They founded the composition, they founded the engine, and they own that. And they're the
startup owners of that. And I think the most successful startups are companies that are really,
really good, are actually an umbrella of startups where you just have founders all throughout
them and they own it and they build mini startups. What do you think?

00:31:30:12 - 00:31:56:21
Jens
Yeah, kind of, I was I was just thinking, what what makes us different? And, I would say one
thing that we really live is the way we do support. And, like, nobody pays for a support or
nobody wants to, like, nobody said, yeah, give me, give me the biggest support plan because
everybody just expects good support.

00:31:56:27 - 00:32:31:24
Jens
But one thing I realized over the last couple of months is somehow we have created an industry
in SaaS, where support is typically absolute garbage because everybody tells us our support is
is top notch, like ten out of ten the best. Like they recommend us so much and I don't know, it's
it's just our culture. We we as a company, we we we we do our thing.

00:32:31:26 - 00:32:53:20
Jens
And I think one of our core values is we, we want to do things right. If someone is not able to
use our product the way they they, they want to, if, if that's a problem or a use case, we're not
fully enabling it. It bothers us. And it's, it's like, yeah, we we want to enable it. And obviously we
you you have to prioritize.

00:32:53:20 - 00:33:21:12
Jens
You can't do everything at the same time. But it's I don't know, it's I would say that's a core
value. We really care and we you know, not not not you know, sometimes you, you, you you
you might think about competition and everything. We don't think so much about competition. We're
mainly concerned about, like just today give you an example.

00:33:21:15 - 00:33:51:09
Jens
Customer ask a question. They say can we use cosmo router and add a custom middleware? I
want to manipulate the response that we're sending to the client. So one way you can take this
question is you can say, yeah, we have a custom module system. You can create a middleware
and then you can manipulate, the response. This is one way how you can not now you're out of
support.

00:33:51:09 - 00:34:19:28
Jens
So in my past life I was a consultant and if you're an external consultant, if you get a ticket, your
goal is to write something into the ticket. That's not offending, that's not negatively affecting any
relationship. That's politically correct, but you really want to get it off your table. You want, do
you? You don't want to have open threads and you do.

00:34:19:28 - 00:34:42:22
Jens
So you get the question. You answer the question in some way and you throw the ticket away.
And not my the I don't care. So I didn't do that, but I asked them like, a couple of questions and
then I realized, okay, I want to huddle a with this person. So I huddle with this person.

00:34:42:25 - 00:35:25:00
Jens
Luckily they, they, they are open. We we started the discussion. It's a health care company.
Healthcare companies are super concerned about security and HIPAA. And one aspect of that,
this is personal information. And so what they, what they were looking at this when there is a
problem with a doctor or a patient and they report this problem and the developer wants to
replicate this, they want to they want to mask data because the, the developer shouldn't see,
like the date of birth or something of a patient, like that's the as a healthcare startup of you
cannot do it.

00:35:25:03 - 00:35:58:03
Jens
And his thought was that wouldn't account would provide him a custom module. So we're a
module system so that he can build his customization to handle PII and to mask the data. And
my thought is, or the way I think is, how can wundergraph build a native or offer a native
solution to handle PII? Because I think it's is it is our responsibility as someone who provides a
router.

00:35:58:06 - 00:36:27:03
Jens
Yes, that the router understands that certain fields in your GraphQL schema are PII, and if the
user is a developer and they have a certain JWT with certain claims and scopes, that under
some conditions, because it's the real user, they can see the unmasked data, but if it's
developer they shouldn't see the data. You should mask it. So and I think like PII that's a it's a
problem that's everywhere.