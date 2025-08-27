---
title: Implicit Keys and Leapfrogging in Federation
slug: ep07-11-implicit-keys-and-leapfrogging
series: The Good Thing
episode: 7
chunk: 11
participants:
  - Jens
  - Sergiy
  - David
segment: Federation key management and explicit schema design
timecode: 00:57:00:23 – 01:03:00:00
start_time: 00:57:00:23
end_time: 01:03:00:00
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - Explicit vs Implicit Keys
  - Leapfrogging Between Subgraphs
  - Schema Visibility
  - Interface and Union Handling
tags:
  - implicit-behavior
  - ai
  - composition
  - federation
  - go
  - graphql
  - graphql-federation
  - microservices
  - startup
topic_tags:
  - federation
  - graphql
  - implicit-behavior
entities:
  - GraphQL
  - Federation
  - Lord of the Rings
  - David
  - Sergiy
  - Jens Neuse
mentions:
  - entity key handshakes
  - composition error prevention
  - Lego brick keys concept
  - Middle Earth metaphor
  - 10-20 team coordination challenges
  - interface/union member visibility
  - microservices architecture coordination
summary: David advocates for explicit entity keys to prevent composition errors and
  team confusion. The discussion covers leapfrogging (routing through multiple subgraphs),
  implicit key problems, and Sergiy's concerns about interface/union visibility across
  subgraphs in large organizations with 10-20 teams working on separate services.
---

00:57:00:23 - 00:57:25:09
David
For me, it would just be trying to make everything as explicit as possible we’re of the opinion
that you should, if you have an entity key and you intend to use that to jump to another graph,
you should write that entity key in that subgraph. So you have an entity key on the source. You
have an entity key on the on the target, and you have a handshake.
00:57:25:11 - 00:57:47:12
David
You only need to define the target because as long as you have, you can satisfy that entity key.
You can make that jump that edge between the graph. But well the problem with that is in the
subgraph. So you have a team that owns that subgraph. They might not know that this other
subgraph has a key an entity key that says that it accepts the ID.
00:57:47:16 - 00:58:02:10
David
For example, an ID to be able to jump there and in their graph ID is just a normal field. Perhaps
it's just marked sharable. It doesn't look like it's doing too much. They think, oh, you know,
maybe I can just remove this field because it's not a it. Apparently it's not a key because it's not
defined as a key.
00:58:02:13 - 00:58:19:26
David
I'll just get rid of it and then they get rid of it and then they realize, oh shoot. Like now, that the
composition doesn't work because it says it can't jump to this subgraph. And this was the only
route. So you could have completely avoided that problem if you just made everything explicit,
make your intent explicit in the graph.
00:58:20:01 - 00:58:22:13
David
So for me, it's explicitness.
00:58:22:16 - 00:58:25:24
Jens
It's this what you call an implicit key.
00:58:25:26 - 00:58:46:21
David
Yeah. We call this an implicit key. So you you define a key field that is not a key field in the
subgraph that it's defined. But it's a key field in another subgraph. So there's another subgraph
that has a key directive that references that same field. It's just then in that particular subgraph
that is the source that's making the jump.
00:58:46:25 - 00:58:51:21
David
It is not a key, it's just a key in another graph. And we call that an implicit key.
00:58:51:23 - 00:59:03:02
Jens
And if I'm on the receiving end of the jump and I have this implicit key and I remove it, it's that's
a composition error or what will happen.
00:59:03:04 - 00:59:12:00
Sergiy
jumps.
You can't be at receiving entries implicitly. You need to have explicit key to be able to accept
00:59:12:02 - 00:59:14:20
David
So the target. So when I say target.
00:59:14:22 - 00:59:16:19
Jens
That's what I mean. I mean the target. Yeah.
00:59:16:21 - 00:59:50:02
David
So the target has the key directive. And the key directive has a field set. And the field set
references one or a number of different fields. You cannot remove those fields because then it
doesn't satisfy the fields set define in that graph. What you can do is from the source graph that
doesn't have the key directive, you could just simply remove that and you're at the mercy of the
composition internal satisfiability graph telling you, okay, if you remove this we can no longer
jump from A to B, and that makes such and such a thing impossible.
00:59:50:07 - 01:00:10:18
David
There's a chance that, there's a chance that you don't actually need that jump. But another
consequence is that while you don't need that jump, you might have changed a single A to B
into a bunch of leapfrogging where you have to go from A to C to D to E to F to G, to H, etc. to
get to where you actually want to be, which is, say, subgraph B.
01:00:10:20 - 01:00:13:23
Jens
This is what you guys call Lego brickies.
01:00:13:25 - 01:00:37:16
David
No, this is what we call leapfrogging. We call leapfrogging. Yeah. Leapfrogging is where you
have a middleman or multiple middlemen. I guess middleman is not right. So a middle graph
and where you're visiting that graph just because your root or your destination is one place. But
to get there you have to go down certain roads because there are no other roots to that field.
01:00:37:18 - 01:00:44:07
Jens
And the middle graph, it fits into your your Lord of the rings story because it's it's middle earth.
Oh yeah.
01:00:44:08 - 01:01:07:22
David
Yeah, yeah, yeah, exactly. Yeah, exactly. Yeah, we have, we have all these internal terms like,
like, leapfrogging and Lego brick keys is another thing which I think we've discussed on this
podcast before, I'm not going to go into now, but there are a few things we don't agree with. As
such, I think Sergiy would actually agree with me that we would just prefer things to be much
more explicit.
01:01:07:25 - 01:01:19:07
David
It would prevent a lot of errors on the developer's part and a lot of guesswork on the developer's
part. If the contract and every single subgraph was made explicit.
01:01:19:09 - 01:01:21:09
Sergiy
Yeah.
01:01:21:11 - 01:01:29:13
Jens
Sergiy anything you would change about federation federation directives?
01:01:29:15 - 01:02:00:29
Sergiy
Yeah. Sometimes, more sometimes you just have allowance of some not so clear behavior, like
when you, you basically could have the same field, which, returns interface or union in one
subgraph, and then you have, as a subgraph which just returns one single member of the
interface or a union. And literally, it's not, not do an interface or union in that subgraph.
01:02:00:29 - 01:02:24:04
Sergiy
And you potentially, may even didn't have this definition of the interface union. We just will have
one connected type. And it is also more about, visibility when you just have type you don't know,
like where in, what union or interface it, participate. And it is not from the federated graph level.
And federated graph.
01:02:24:05 - 01:02:59:27
Sergiy
You will see it. Yeah. Right. That I have this type and implement this interface. But it's a
microservice architecture kind right. You have a lot of teams, one of like some of our customers
have like 10 maybe two, 20 teams, which, each works on, separate subgraphs and they have to
coordinate each time, like, the collides with each other, because so yeah, just not that's visible
when you do some changes that you will, affect that as a subgraph.