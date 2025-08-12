---
title: Open Source Support Costs and Enterprise Business Models
slug: ep16-03-open-source-support-and-cost
series: The Good Thing
episode: 16
chunk: 3
participants:
  - Stefan
  - Jens
segment: Open Source Business Model Discussion
timecode: 00:09:15 – 00:14:09
start_time: 00:09:15
end_time: 00:14:09
speakers:
  - Stefan
  - Jens
topics:
  - Developer tools requiring open source approach
  - Nginx enterprise model challenges
  - Tyk API gateway business strategy
  - Open source vs closed source decision criteria
  - Enterprise feature separation strategies
tags:
  - open-source
  - api-gateway
  - ai
  - api-design
  - cosmo
  - database
  - go
  - query-planning
  - rest
  - startup
topic_tags:
  - open-source-business
  - developer-tools
  - nginx
  - tyk
  - enterprise-features
  - api-gateway
entities:
  - Nginx
  - Tyk
  - WunderGraph
mentions:
  - Developer tool companies needing open source
  - Nginx Pro adoption challenges
  - Tyk's core gateway vs management dashboard strategy
  - Open source collaboration invitation
  - Long-term planning requirements for open source
summary: Stefan and Jens discuss how successful developer tool companies often need
  open source strategies to invite collaboration. They analyze different approaches
  like Nginx's failed enterprise model and Tyk's successful separation of open source
  gateway from closed source management features. Jens emphasizes that open source
  decisions require long-term planning and understanding of true costs and implications.
---

00:09:15:13 - 00:09:35:24
Stefan
It's true. So what I'm seeing also what I kind of can imply, like the best developer tool facing
companies, they kind of have to be or at least start in open source, because with development,
you if it's open source, you invite the collaboration. But I feel like if you really, truly want to be a
successful dev tool company.
00:09:35:26 - 00:09:42:05
Stefan
You have to be open source. What do you think about that?
00:09:42:08 - 00:10:11:09
Jens
Yeah, it it depends. And it's hard. For example, we we talked to the investors of, of engine X or
engines or how do you call them enginex. Enginex. Okay. So we talked to them and, and there
was this time where so next open source and then they, they added like, I don't know, engine X
Pro or something with advanced features.
00:10:11:12 - 00:10:45:07
Jens
And nobody wanted to adopt it. But they didn't change the license. They just added another
enterprise tool. Adoption wasn't great, but what it what it did this it created room for alternative
players to create like API gateways that are open source. And for example, one one company I
worked for, before creating wundergraph, is Tyk analogies, who have an API gateway.
00:10:45:09 - 00:11:09:08
Jens
And I think one one decision they made was was very good is they had the open source
gateway, which was just the gateway. But if you wanted to run multiple gateways in a cluster or,
or something like that, then, yeah, you had to had like a dashboard, like a management
component. And this was just closed source from the very beginning.
00:11:09:08 - 00:11:33:21
Jens
There was no discussion around it. And I personally, I have no strong opinion whether a
company should make something closed source or open source. I would rather say, make it
open source if you have a long term plan and understanding of what that means and make it
closed source for the same reasons.
00:11:33:23 - 00:11:48:26
Stefan
It's all said. And what's interesting is I think you're going to laugh at this, but in your mind
actually just in general is I know the answer, but is open source free?
00:11:48:28 - 00:11:51:02
Jens
That's a stupid question.
00:11:51:04 - 00:12:09:02
Stefan
I know it's a stupid question, but we get it very often. Is open source free? I mean, like, the
license is very freeing. I can run it. I don't have to pay you a cent. It's essentially free is what I
hear a lot from I don't know, I wouldn't say the word stupid, but sometimes misguided people.
But why isn't open source not free?
00:12:09:05 - 00:12:13:11
Stefan
Or what are your thoughts there on launch? I'm going to clip that, by the way. That's a stupid.
00:12:13:11 - 00:12:35:05
Jens
Idea. But you know, my my biggest my biggest pet peeve is not not just like it's open source.
Obviously it's not free. It's, I come to that in the moment, but what annoys me the most is people
who think I will support them for free on my open source, because why.
00:12:35:05 - 00:12:40:03
Stefan
a can.
Not? Like I have a big logo, I have a big logo and I work in a big company. I'm going to give you
00:12:40:03 - 00:13:06:25
Jens
I have a full calendar? Like, I'm I'm building a business. Sorry. Like I really have no time for for
you. But, you know, like, I think the most important thing people have to, to understand is open
source is a way of distribute software. You you are allowed to download the software and to
replicate it, whatever the license is.
00:13:06:25 - 00:13:37:01
Jens
And you can do whatever you want with it. And that's it. Exactly. There it ends. Like I owe you
nothing. You owe me nothing. The software is just open. Why is cosmo open and what kind of
interactions do I actually like? There are people who I think who understand open source, and
they come to us and say, hey, we have found a bug in your query planner.
00:13:37:04 - 00:14:09:06
Jens
Here's a replication. In this particular case, it's panics and we think it shouldn't. And then we
collaborate on solving the problem. Or they come in and say, hey, you have this feature. I think
there is a security problem. Here's how you can replicate this. Can we collaborate on on
improving the software? This is why Cosmo is open Source, we we think making it open source
will lead to Cosmo being the best for everybody.