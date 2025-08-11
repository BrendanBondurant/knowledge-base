
---
title: APIs as Plumbing and MCP Dependence
slug: ep25-09-apis-as-plumbing-and-mcp-dependence
series: The Good Thing
episode: 25
chunk: 9
participants:
  - Stefan Avram
  - Jens Neuse
  - Kevin Swiber
segment: APIs as Infrastructure and MCP Reality
timecode: 00:35:12:21 – 00:39:30:26
start_time: 00:35:12:21
end_time: 00:39:30:26
speakers:
  - Stefan
  - Kevin
  - Jens
topics:
  - APIs as digital plumbing analogy
  - Bachelor party HVAC conference story
  - API ubiquity in digital systems
  - MCP and API relationship misconceptions
  - Distributed systems and API inevitability
tags:
  - api-plumbing-analogy
  - digital-infrastructure
  - mcp-apis
  - distributed-systems
  - client-server-model
  - api-proliferation
entities:
  - HVAC and plumbing convention
  - Bachelor party
  - graphql
  - MCP (Model Context Protocol)
  - Client-server architecture
  - Network infrastructure
  - Digital systems
mentions:
  - Physical building plumbing parallel
  - Every digital system has plumbing
  - GraphQL still being an API
  - MCP servers becoming API consumers
  - Network distribution necessitating APIs
  - Connected cloud world reality
  - API proliferation management need
summary: |
  Stefan shares a humorous story about attending an HVAC convention during a bachelor party, leading to the realization that APIs are like digital plumbing - every system has them. Kevin reinforces this, explaining how even attempts to escape APIs (like GraphQL or MCP) ultimately create more APIs. He emphasizes that distributed systems over networks inevitably become APIs, and the solution isn't avoiding APIs but better managing their proliferation in our connected world.
---

00:35:12:21 - 00:35:19:14
Stefan
That one’s curious, but I'm not going to ask you that one. I’ll ask you offline.
00:35:19:16 - 00:35:50:04
Stefan
That's awesome. But, let's kind of acknowledge, some of the topics that we had planned, which
is, again, Jens this all the time, I think you also say, and I also wholeheartedly agree on this, it's
APIs all the way down. APIs quietly power everything. And one of the things I realized, the
space that we're in, I was once I had a bachelor party, and in the hotel there was an Hvac and
plumbing convention, and there was people going crazy about the type of, like, angles on the
plumbing, the type of material used in the pipes and everything.
00:35:50:06 - 00:36:04:18
Stefan
And I kind of realized, like the API space is the plumbing space, like we're the weird people that
get excited about what type of piping we use, how we connect different systems together. So I'm
like looking at this conference and I'm walking around and I'm looking at all these booths and
everything, and I'm like, oh, this is true.
00:36:04:18 - 00:36:21:20
Stefan
If you think about it. Like every physical building in the world has plumbing, every digital system
in the world has plumbing. And so one of the things we all agree on, I think, Kevin, I'd love your
take on this is I mean, APIs, power, everything. It's APIs all the way down. Would you agree with
that? What's your take on that.
00:36:21:22 - 00:36:40:24
Kevin
Yeah. So first off, let me just get this straight. You're at a bachelor party. And instead of spending
time at the bachelor party, you decide to go to an HVAC and plumbing convention that happens
to be in the same venue and think about APIs. That's that's it sounds like a pretty wild bachelor
party.
00:36:40:26 - 00:36:41:21
Jens
If I'm.
00:36:41:21 - 00:36:55:01
Stefan
Honest, though, I was at the bar, I saw all these people. They were getting super excited. So I
got a couple of drinks into me and I went into the conference and it was a little bit more fun like
that. But yes, yes, you got that right, I did okay. APIs are always on the top of my mind.
00:36:55:04 - 00:37:20:28
Kevin
No. It sounds like something that would happen to me too, but like at then suddenly I was
looking at, you know, plumbing, like, how did how did that happen? But, yeah, I mean, I think
it's, it's, you know, I as much as we've tried to, steer away from, from APIs and I think even in
the GraphQL space, it was almost like, oh, you know, to hell with APIs.
00:37:21:01 - 00:37:40:22
Kevin
I'm going to go use GraphQL. And I think for a lot of the those people, it took a while to realize,
like, oh, this is still an API. Like, I still I still have to worry about the network. I still have to, you
know, maybe the tools are really great for me. Client side. But there's still, like, a whole network
here that I've got to think about, right?
00:37:40:24 - 00:38:10:12
Kevin
So, yeah, we just we can't escape it. Right? Like, client server is a really good model. And to do
client server, there are a few different patterns. But they all end up looking like APIs. No matter
how you slice it. So, so, yeah, I think, you know, when we, we look at kind of AI and, MCP now
there are like a group of people who are saying like, oh, I don't need my API anymore.
00:38:10:12 - 00:38:41:02
Kevin
I can just make an MCP server. But then, you know, what happens is you want to centralize this
functionality somewhere. You want to provide this functionality to multiple consumers. You know,
you've got natural seams. Where you need to scale separately. And so you're looking at, you
know, having a distributed model of some sort. And when you have a distributed model and it's
going over the network, suddenly you're building an API that your MCP server is a consumer of.
00:38:41:04 - 00:39:02:25
Kevin
Right? And it's just, every time we say, like we're trying to, to get out of doing APIs, we end up
just creating more APIs. And, and so, like, you know, I don't I don't think that's, that's going
away. And I think, you know, some people are, I think they're experiencing the pain of having so
many APIs.
00:39:03:01 - 00:39:30:23
Kevin
And so they're like, no more APIs, you know, like, let's just stop. Stop doing it. I don't think they
can right. I think, like, APIs are here to stay. They're going to keep proliferating. And so doing a
better job managing that proliferation, is, you know, is probably the way to go there. But yeah, I
think, you know, as AI, we're we're never going to get rid of APIs because we live in a connected
world.