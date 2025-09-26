---
type: podcast-chunk
title: Descriptions, Federation, and RFC Process
slug: ep02-13-descriptions-federation-rfc
series: The Good Thing
episode: 2
chunk: 13
segment: Federation Descriptions and Documentation
timecode: 00:51:44:14 – 00:56:39:05
start_time: 00:51:44:14
end_time: 00:56:39:05
speakers:
  - Stefan
  - Jens
topics:
  - Federation Descriptions
  - RFC Process
  - Public vs Private Documentation
  - Team Collaboration
tags:
  - federation-descriptions
  - ai
  - api-design
  - composition
  - federation
  - go
  - graphql
  - graphql-federation
  - rest
  - startup
entities:
  - WunderGraph
  - GraphQL Federation
  - RFC Process
  - Schema Registry
  - Documentation Standards
summary: Stefan and Jens discuss the challenges of federation descriptions and documentation,
  explaining how teams can conflict when adding descriptions to the same fields. They
  describe their RFC process for solving this problem by introducing a new directive
  that allows teams to specify public vs private descriptions, preventing composition
  errors and enabling better team collaboration.
---

00:51:44:14 - 00:52:03:09

Stefan

Yeah. Well said. So we are nearing the hour, but we do still have two more topics I want to

discuss. So I want to talk a little bit about the conversation that we had with that crazy large

customer that has a first world tech problem. But before we go into that one, let's talk a little bit

about descriptions and federation.

00:52:03:09 - 00:52:16:05

Stefan

Since we're in federation land right now. So this was a topic that came up this week. And I know

you have some thoughts on it, but what are descriptions in Federation. Why are they important

and what are your thoughts on.

00:52:16:07 - 00:52:38:00

Jens

Okay problem. Very simple. So every node in the GraphQL schema you can or I think most you

can puts a description on the node. It means you have a field. The field allows you to query user

info. And you can put the description to say like what is the purpose of this field? And this is very

important.

00:52:38:01 - 00:53:04:00

Jens

Like I mentioned earlier, you need specifications for for users. And code is not self-documenting.

You need to document why this field exists, what is the use case? And, what's important about

that? Now, you have a little problem in Federation that we figured out it it came throug, one of

our biggest customers. You have one team.

00:53:04:02 - 00:53:28:18

Jens

They create an entity, they add a field on the entity. They put a very thorough description on the

field to tell everybody else in the company. What's the purpose off the field? Amazing. Perfect.

That's the way we want to have it. Well documented APIs. Awesome. So we ship this into

production. Then a while later, second team comes along, says, oh, that's an awesome entity.

00:53:28:24 - 00:53:50:03

Jens

We add something, so they create a subgraph, they put something on top and they are like, you

know what? I want to have your field, I can use it as an input because I want to compute

something with your field. So they use the provides directive and, add this other field. They

cannot resolve it. So they put external on it.

00:53:50:05 - 00:54:19:20

Jens

So now we have a second graph that has this field. By the way same problem with shareable.

And essentially you have two graphs. They have the same field. And now both put a description

on it. One team put a description on it to tell the rest of the company, what's the point of this

field? The second team puts a description on the field because they want to have some internal

information, telling the rest of the internal team why they have this field and it's external and

blah, blah, blah.

00:54:19:23 - 00:54:43:18

Jens

So the purpose of a description in a schema can be to communicate something to the rest of the

company, or it can be to communicate something to the team. In both cases, your your tool of

choice is the description. And there's no two descriptions. There's no internal or external

description, all these kind of things, you don't have that.

00:54:43:20 - 00:55:14:14

Jens

So now you have a little bit of of yeah, of a race between, because whoever comes first, they,

they push their description or there's algorithms in other, federation solution that pick the longer

description or. Yeah, like what description should we, should we choose for our federated graph

and for the subgraph. Like what's. Yeah what's the right description.

00:55:14:14 - 00:55:39:16

Jens

And so we were thinking about this problem started an RFC process. How do we do this. Quite

often and we we are getting close to, conclusion. And somehow, we, we think the, the right ways

we introduce a new directive. This directive allows us to say the description we have on this

node. It's public, yes or no.

00:55:39:17 - 00:56:04:01

Jens

So if it's not public, it will not go into the super graph. We we want to keep that to ourselves. If

it's public, it goes into the super graph. And if a second team tries to bring in a description on the

same fields, also make it public, we will have a composition error. So in this case we now have

composition to to prevent this error from happening and not randomly choosing one description.

00:56:04:03 - 00:56:32:10

Jens

And then there's a second thing. We can now put a description on the, on the on the field. And

we can have on this description configuration directive, we can have the second field where we

can define like a custom description and this custom description. We can then publish that into

the super graph. So this allows us to have a private description for the subgraph team a public

description for the super graph.

00:56:32:10 - 00:56:39:05

Jens

And we can decide do we want to have a private or public. And if that's still not enough, we can

even have a custom one. 