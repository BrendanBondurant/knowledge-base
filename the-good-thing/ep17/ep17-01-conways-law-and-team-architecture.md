---
title: Conway's Law and Team Architecture
slug: ep17-01-conways-law-and-team-architecture
series: The Good Thing
episode: 17
chunk: 1
participants:
  - Stefan
  - Jens
segment: Introduction to Conway's Law
timecode: 00:00:22 – 00:05:10
start_time: 00:00:22
end_time: 00:05:10
speakers:
  - Stefan
  - Jens
topics:
  - Conway's Law
  - Organizational Design
  - Team Architecture
  - Federation Patterns
tags:
  - conways-law
  - federation
  - monolith
  - startup
  - ai
  - api-design
  - go
  - graphql-federation
topic_tags:
  - conways-law
  - organizational-design
  - team-architecture
entities:
  - Conway's Law
  - WunderGraph
  - Stefan Avram
  - Jens Neuse
mentions:
  - recursion learning experience
  - enterprise customers
  - construction company IPO growth
  - monorepo vs distributed teams
  - federation architecture benefits
summary: Stefan introduces Conway's Law through a personal learning analogy with recursion,
  explaining how software structure mirrors organizational structure. He shares observations
  from customer conversations, showing how companies transition from monolith to federated
  architectures as they grow from small teams to large organizations, with a construction
  company example that went from zero to IPO in six years.
---
Episode 17
00:00:22:17 - 00:00:31:05
Stefan
You.
00:00:31:07 - 00:00:51:13
Stefan
And we're back. Welcome back, ladies and gentlemen, to another episode of the. Good Thing.
You might notice I'm not in my usual studio today, and this is actually a recording reason why I'm
actually out this Friday heading to a funeral. So I will be out this Friday. But we wanted to stay
consistent and make sure that you guys get your daily or your weekly viewage of the good thing.
00:00:51:13 - 00:00:55:07
Stefan
Jens, as always, good to see you. How you doing today?
00:00:55:09 - 00:00:57:04
Jens
I'm good.
00:00:57:07 - 00:01:00:24
Stefan
Typical German response. Not bad. I'm good. It's same.
00:01:00:27 - 00:01:03:04
Jens
Every Week.
00:01:03:07 - 00:01:25:03
Stefan
That's awesome. Well, thanks for joining us. Today we're going to be talking about what we call
Conway's law and just kind of going I want to say, like, off script. We don't have a strict agenda
today, but I kind of wanted to talk about organizations, what we're seeing with the rise of AI, just
kind of how companies are adopting AI, where we're going with AI and just kind of like API's and
how it fits into that space.
00:01:25:06 - 00:01:41:22
Stefan
And the first topic I wanted to talk about is, Conway's Law. This is a law that I learned about
when I started at WunderGraph. But it's one of those things and I'll give you like a story is, I'll
forget. Like when I was in college, I didn't understand recursion. I couldn't understand it. I
couldn't, like, figure it out.
00:01:42:00 - 00:01:59:24
Stefan
And for the longest time, like the exam was coming up and I was scared. I was like, I don't
understand recursion. I don't know, understand why anybody would use it. And, this was a
solution to a problem. And what I realized quickly was I couldn't figure it out. There's no way,
there's no way. I spent hours in the lab trying to figure it out.
00:01:59:24 - 00:02:15:08
Stefan
It didn't make sense to me, but when the tests came, they gave me a problem. And I was like,
okay, well, to get to the solution in this problem, which if I go four steps this way and then to the
right, and then just keep kind of doing that, and then it just kind of clicked right there is what I
was doing was recursion.
00:02:15:08 - 00:02:38:03
Stefan
And so because I had an actual problem and I had the solution in my brain or in my toolbox, it
clicked in my head. And what I'm trying to get at is I didn't get Conway's law in the beginning. I
didn't understand it. But now when we work with these enterprises and we talk to them and we
learn about their tech specs and their architectures, and then we actually talk to their teams, I'm
like, holy crap.
00:02:38:03 - 00:02:59:24
Stefan
Like, this is Conway's law at play. And so I want to talk about today of what we have been
seeing with Conway's Law. And this is a very simple paraphrased version of Conway's Law. But
basically, the structure of your software will mirror the structure of the organization that built it,
which I think is super fantastic. And like it's kind of cool how we figured this out, but it totally
makes sense.
00:02:59:25 - 00:03:07:23
Stefan
I'll pause there. Jens, though like, what have you seen lately on Conway's Law? And just I
mean, we talk about it all the time, but why is it important?
00:03:07:25 - 00:03:17:13
Jens
Maybe before we talk about that, I'm curious what what what observations have you made
talking to to to customers.
00:03:17:15 - 00:03:39:25
Stefan
Well it's cool. So like, for example, us, we're a single monolith, one monorepo. And that's how
we work. Everybody works to the same contributing. And then with our customers, what we'll
see is that they'll either be one large team working together with a monolith. And what's quickly
you realize there is they want to take that monolith and they want to break it apart.
00:03:39:27 - 00:04:01:08
Stefan
And the reasoning isn't actually the software, it's what's happening inside the organization.
We're moving too slow. We're stepping on each other's toes. It's just getting too big. We're cut.
We're company. And what you realize quickly with these companies that go from monolith to
federated architecture is that they started off small, which is great, but they grew very fast.
00:04:01:10 - 00:04:17:25
Stefan
For example, we have a construction company that grew from zero to IPO in about six years.
And what they've quickly realized is we've built this huge legacy. We're one big team, but we're
so slow we cannot be slow. And so what we're looking at is a federated architecture to break it
apart. And that's where federation comes in handy.
00:04:18:01 - 00:04:38:06
Stefan
And then we also see is these small distributed teams that kind of started out from the
beginning. It might have been a little bit of a hurdle at first. A lot of times you tell people you're
too small for Federation, but for them it ended up working and they kind of have this modular
type where different teams own different services and they all work together, work together.
00:04:38:08 - 00:04:54:21
Stefan
But it's kind of what we're seeing within the companies is that if you remove the software and
you don't actually talk about the software, just look into the teams and ask them like, okay, how
are you working together with team A, B and C, or are you guys just one team? How do you
push code? How do you collaborate with those teams?
00:04:54:24 - 00:05:10:20
Stefan
And I think that this Conway's Law, it's it's more about the teams than even about the software.
You can always figure out what software they're using or like what architecture that they have by
just talking to them and how they interact with each other. So that's kind of what I've been
seeing. What about you?