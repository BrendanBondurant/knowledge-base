---
title: Explaining MCP with Metaphors
slug: ep14-02-explaining-mcp-with-metaphors
series: The Good Thing
episode: 14
chunk: 2
participants:
  - Stefan
  - Jens
  - Dustin
segment: Explaining MCP with metaphors and federation as a gateway
timecode: 00:05:15 – 00:09:24
start_time: 00:05:15
end_time: 00:09:24
speakers:
  - Stefan
  - Jens
  - Dustin
topics:
  - MCP metaphors and explanations
  - Federation as a gateway
  - Tool descriptions and accessibility
tags:
  - mcp
  - federation
topic_tags:
  - mcp
  - metaphors
  - federation
entities:
  - Stefan Avram
  - Jens Neuse
  - Dustin
  - WunderGraph
  - MCP
mentions:
  - MCP explanations
  - federation metaphors
  - tool accessibility
summary: Stefan and team explain MCP using metaphors and discuss how federation acts as a gateway, making tools more accessible and understandable.
---

00:05:15:24 - 00:05:31:23
Stefan
And and, I was telling my wife about this earlier today, so I was trying to explain to her what
MCP was and let me know what you guys think of her analogy. So she said basically, MCP is
when you take your phone and you plug it in, you plug in the usb-C into your phone and then
you plug it into your laptop.
00:05:31:23 - 00:05:50:11
Stefan
And you remember when that pop up pops up, like give access to this computer. And so then
when you're on the computer, you can access the information that's on your phone. And she's
like, is that what you're doing? You're letting products get access to cosmo. So let's say
someone builds on top of Cosmo, are you giving them access that they can start building from
all that data and stuff like that?
00:05:50:12 - 00:05:51:13
Stefan
What do you do now?
00:05:51:14 - 00:06:16:17
Dustin
Like I would say, it's it's even simpler. Imagine you have a conversation with four people and
each and if a guy represent a system. So with MCP you just bring another person into the
discussion and then you can discuss the things and you can come up with a solution based on
what, what context that can provide to the conversation.
00:06:16:19 - 00:06:20:12
Stefan
I like that, what about Jens?
00:06:20:15 - 00:06:51:03
Jens
I want to take one little step back because, everybody can build an MCP server. Right. And the
MCP, it's a protocol. Now, if you go to, for example, the subreddit slash MCP, like there's so
many MCP server like everybody is building MCP servers. By the way, I have just, used one
really cool one because, I wanted to build a new landing page today, and I thought, okay, I want
to know, does it have a good Lighthouse score?
00:06:51:05 - 00:07:30:21
Jens
So I added a lighthouse MCP server because somebody has built it already. So now my cursor
can change something on the website and then run a lighthouse test without me because I'm
too lazy opening the browser and clicking on lighthouse test so I can I can now do that. So
yeah, like essentially what Dustin said you can now instead of clicking around you can now just
write what you want and and cursor ensures that cursor MCP ensures that cursor or your model
it can now talk to lighthouse score.
00:07:30:21 - 00:07:58:16
Jens
It can talk to Cosmo. It can talk to GitHub. It. Yeah. Yeah. That's so that's right. But one step
back because everybody can build an MCP server. Now there's a new problem. So you you
have this huge opportunity to that's a model can now through MCP talk to anything. The
problem is we have we need to bridge between anything and MCP.
00:07:58:18 - 00:08:21:27
Jens
And so this is the problem Dustin was looking into because we already have a solution to bring
to to turn anything into something very specific and then go from something very specific to
MCP. And so in our case, I mean, you you know, us this anything it is the concept of the super
graph. It's the concept of GraphQL federation.
00:08:21:29 - 00:08:55:24
Jens
If we have a GraphQL federation layer and our router can go from federation to trusted
documents / MCP. So now MCP can actually talk to all the things we have already federated. So
so that means if we if we have this component that goes from federation to MCP, all we have to
do as a company is bring more capabilities to our federated graph, and it becomes available to
to MCP.
00:08:55:24 - 00:09:24:01
Jens
It becomes available to the models. The problem do you want to give everybody access to
everything? Do you want the model to do whatever it wants? Do you somehow want to limit
that? And now you can even ask yourself the question, if you let's say you are not doing
Federation, you just have MCP and you, you manually implement from MCP to anything.