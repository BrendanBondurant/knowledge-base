---
title: Federation Clarity and Composite Schema Working Group
slug: ep07-12-clarity-and-composite-schema-group
series: The Good Thing
episode: 7
chunk: 12
participants:
  - Jens
  - Sergiy
  - David
segment: GraphQL Federation working group participation
timecode: 01:03:00:00 – 01:08:14:07
start_time: 01:03:00:00
end_time: 01:08:14:07
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - GraphQL Composite Schema working group goals
  - Eliminating subgraph library requirements
  - Federation evolution and adoption timeline
  - Subgraph-level schema clarity for developers
  - Federated graph size challenges (100,000+ lines)
tags:
  - composite-schema
  - working-group
  - subgraph-libraries
  - federation-evolution
  - developer-experience
  - schema-size
entities:
  - GraphQL Foundation
  - Composite Schema Working Group
  - Apollo Federation
  - Marc-Andre (Netflix)
  - Sergiy
  - David
  - Jens Neuse
mentions:
  - Netflix Federation feedback
  - 100,000+ line federated schemas
  - subgraph library elimination
  - 2018-2019 Federation origins
  - 6-7 year adoption period
  - regular GraphQL API usage
  - composition validation approach
summary: |
  Discussion of the GraphQL Composite Schema working group's goal to eliminate subgraph libraries by enabling regular GraphQL APIs in federation. Sergiy explains the benefits for developers reading subgraph schemas without needing massive federated graphs, while acknowledging the long adoption timeline similar to GraphQL's own 6-7 year journey.
---

01:03:00:00 - 01:03:24:13
Sergiy
But of course it will get you that composition. But then you need to do change and to check,
compatibility, with just like a typical workflow how you federation. But, yeah, but just believe that
this workflow could be better and, it could bring you add just a bit more information, imagine
your just a new developer and you join in the team.
01:03:24:16 - 01:03:48:27
Sergiy
But by reading just only subgraph schema, you, will see some kind of possible things which, you
could expect to have another subgraphs without need to see into huge federated graph schema
with which could be like, three, 30,000 K of lines. Right. Or I don't know the numbers.
Like.
01:03:49:21 - 01:03:58:01
Sergiy
It has no limit. It just depends on your, on your amount of subgraphs and the amount of types
and fields and so on.
01:03:58:04 - 01:04:06:14
David
That's a baby graph. Sergiy So I think my biggest, the biggest I've seen is over 100,000.
01:04:06:17 - 01:04:41:29
Jens
I think what you what you two are kind of saying it. It's also in the, in, in the same ballpark of of a
tweet I saw a while ago from, from Marc-Andre working at Netflix who like a while ago, he said
something like, it would be nice if if GraphQL Federation had a few less directives and if it was
more, more strict and and I think this is this is overall kind of similar to to what you guys are
saying.
01:04:41:29 - 01:05:13:00
Jens
And, yeah. If you talk a little bit about the, the GraphQL Federation ecosystem. So you guys are
participating in the, GraphQL working group for the, composite schema. That's, living under the
umbrella of the GraphQL Foundation. Maybe you can explain a little bit, what what is the, what
is the goal of this of this, working group?
01:05:13:00 - 01:05:18:10
Jens
And then what are the the participants trying to achieve?
01:05:18:10 - 01:05:23:23
David
Yeah, it's under.
To rule them all. But, yeah, we've.
01:05:23:23 - 01:06:03:00
Sergiy
Been participating for not a long time. We was not there from the beginning. So, we just get into
speed up to get into understand it a bit, but, one, one cool part about it, but, like, the main goal
is that you won't need subgraph libraries anymore of this composition spec, because with the,
Apollo Federation, you basically need to comply with a specific format of, subgraph and specific
behavior, which is also kind of implicit behavior that is getting added into your GraphQL schema
by the subgraph library.
01:06:03:02 - 01:06:45:03
Sergiy
Like, you get some service fields, some internal fields which, are intended to be used not by
user, but by the, Federation getaway. It is possible to use it, manually in case you know what
you are doing, but it is not that friendly. And, yeah, one of the interesting things it's, that really it
should make possible to use more regular GraphQL, APIs by just instructing, the query planner
of how to fetch data, how to set entry points, how to send keys, and, it will allow you to just
bypass subgraph libraries.
01:06:45:05 - 01:07:24:15
Sergiy
Potentially you just will need some kind of validation. Apply it to that. But, even not sure that
subgraphs are typically have, some kind of validation which, different from their regular
GraphQL validation. Usually you just doing that at, composition time with composition checks
and. Yeah, this is cool concept. But, yeah, I just didn't know when it will be adopted because it
has taken a lot of time to adopt graphql across, the tech world.
01:07:24:18 - 01:07:38:00
Sergiy
And, then there was some time like, from 2019 when the Federation righ, David do you recall?
01:07:38:03 - 01:07:41:04
David
Let's, let's say 2018.
01:07:41:06 - 01:08:09:03
Sergiy
Yeah. So like 6 or 7 years ago, it's, it's a period and now now it's adopted. And, yeah, it's
supposed to be an evolution of federation, but, it could take some time to migrate to this
approach. And, yeah, it's quite interesting to participate and to see, what will happened. And it is
the same, the same thing basically, as with our day to day work.
01:08:09:05 - 01:08:14:07
Sergiy
It just interesting to see wasn't the first you could have and how people will use it.