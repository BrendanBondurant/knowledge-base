---
title: Managed Service Expertise Gap and Customer Support Challenges
slug: ep16-06-managed-service-expertise-gap
series: The Good Thing
episode: 16
chunk: 6
participants:
  - Stefan
  - Jens
segment: Service Delivery and Domain Expertise
timecode: 00:26:16 – 00:31:23
start_time: 00:26:16
end_time: 00:31:23
speakers:
  - Stefan
  - Jens
topics:
  - Code copying limitations and knowledge gaps
  - Customer support and education requirements
  - Domain expertise for effective guidance
  - Business responsibilities with paying customers
  - Implementation decision context understanding
tags:
  - startup
topic_tags:
  - managed-services
  - customer-support
  - domain-expertise
  - business-responsibilities
  - implementation-guidance
entities:
  - Cosmo
mentions:
  - Following commits creates lag
  - Missing decision-making context
  - Trial and error learning curve
  - Customer support obligations
  - Education and guidance requirements
summary: Stefan and Jens explore why simply copying code commits doesn't create a
  viable business, focusing on the knowledge gap problem. They discuss how paying
  customers require support, education, and guidance that demands deep domain expertise
  - knowledge that can't be copied from commits but must be earned through experience,
  trial and error, and understanding the reasoning behind technical decisions.
---

00:26:16:06 - 00:26:33:04
Jens
So now you're lagging behind. Now your counter argument might be but Jens I don't need to
fork it because, I can just copy all your updates. I just follow all your commits. Do you know why
that's not possible?
00:26:33:07 - 00:26:53:05
Stefan
Well, one point before you answer that is also like, even though you copy over the code or you
fork it or whatever, you also don't know why we made certain decisions, why maybe something
is missing or why maybe something is there, and then you also don't even know what you don't
know because of the things that we know.
00:26:53:05 - 00:27:08:07
Stefan
If that makes sense, stick to things that we had to figure out. It did through trial and error and
everything. But to your point with the counter argument, what? Why wouldn't it work? Okay, I
just follow you commit by commit, I'm a little bit lagging behind. Why why why wouldn't it work in
a business model?
00:27:08:10 - 00:27:29:13
Jens
Okay, let's assume you somehow, figure out sales and branding and other things. Maybe you
already have a brand. It's possible. Okay, I have it all, let's say. But let's say you get your first
couple of users. What happens when you have users?
00:27:29:15 - 00:27:31:10
Stefan
Are they paying or they just users?
00:27:31:13 - 00:27:34:02
Jens
They're paying.
00:27:34:05 - 00:27:44:24
Stefan
Well, now we have responsibilities. They were oh. They'll want support. They want education.
They want guidance on how to implement it in the best way possible.
00:27:44:27 - 00:27:52:26
Jens
Let's say they ask for bug fixes or feature requests. So if you just follow our commits.
00:27:52:28 - 00:27:53:13
Stefan
How are you going to do.
00:27:53:13 - 00:27:59:08
Jens
That? We are not aware of the bug fixes your customers need and the features.
00:27:59:11 - 00:28:04:06
Stefan
What's if I just open up the PR? I ask in the discord for the other. I'm just asking you guys.
00:28:04:09 - 00:28:08:16
Jens
I told you before, I'm busy.
00:28:08:19 - 00:28:36:08
Jens
Okay, so you see, you have customers. They want something, so you need to stop maintaining
that. So you, you make commits to to do what they need. You you will quite quickly figure out
that. So you will see that we we are we are not merging this because we're we don't have time
for the frequency of of changes you make.
00:28:36:10 - 00:29:03:05
Jens
And so you add commits. We have commits. Maybe you are able to merge them for a little while
until you come to a point where we just have different opinions. And because we are not
collaborating, we're colliding. And so from, from that point on, the code is more or less
incompatible. So, so you're now forking and the moment you fork, you take full responsibility.
00:29:03:05 - 00:29:42:04
Jens
And here starts the first problem. If you fork Cosmo. We currently have close to 20 developers
working full time on Cosmo. It so like some people, they had a little bit of experience. But now
we have many developers with multiple years of experience working on Cosmo. And I can tell
you from, from the expertise you find in the market, you find people who understand GraphQL,
you find people who understand how to write code and communicate.
00:29:42:07 - 00:30:12:29
Jens
You don't find people who understand, GraphQL federation at the depth where we operate. And
like, there's nobody on the market, these people work at the other federation companies. So
hiring it can take you a year or maybe longer to hire people, to hire the right people and to to get
up to speed, to that. You can actually maintain the, the, the software.
00:30:12:29 - 00:30:19:16
Jens
So that's, that's like a huge problem to solve. In the beginning.
00:30:19:18 - 00:30:39:08
Stefan
Well said, I think people missing most on the domain expertise, like just because you get the
software, you don't have the expertise to run it, especially at scale. And one of the biggest
things is Dustin, our CTO, like, let's say I go and I set it up. I follow you guys with reference
architecture that you guys very nicely put on the documentation page.
00:30:39:08 - 00:30:56:08
Stefan
I fork everything, I copy it perfectly fine, but you also don't have the expertise that Dustin has
and the things that he's done on GCP in Kubernetes to make sure that we run this scale for
customers doing billions of requests per day. I think that's also an important factor, is that
offering this as a managed service is hard.
00:30:56:11 - 00:31:23:22
Stefan
Offering this as a managed service with 99.99% uptime and availability and minimal incidences
of extreme hard. You have to also figure that out. And then the third part, I do want to add this
because I always say this in sales calls is there's probably ten really deep federation and query
planning experts in the world. And I'd say about eight of them work at WunderGraph like the
domain expertise is the biggest part that most people are misunderstanding.