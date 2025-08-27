---
title: Schema Noise and Frontend Friction
slug: ep22-06-schema-noise-and-frontend-friction
series: The Good Thing
episode: 22
chunk: 6
participants:
  - Stefan
  - Jens
segment: GraphQL Developer Experience Issues
timecode: 00:26:23:00 – 00:32:04:00
start_time: 00:26:23:00
end_time: 00:32:04:00
speakers:
  - Stefan
  - Jens
topics:
  - GraphQL Schema Noise
  - Frontend Friction
  - Developer Experience
  - Legacy Integration
tags:
  - federation
  - graphql-federation
  - grpc
  - ai
  - api-design
  - go
  - graphql
  - rest
  - rest-apis
  - rest-connectors
topic_tags:
  - federation
  - graphql-federation
  - grpc
entities:
  - Stefan Avram
  - Jens Neuse
mentions:
  - schema complexity issues
  - frontend development challenges
  - legacy approach problems
summary: Stefan and Jens discuss how complex GraphQL schemas create "noise" that adds
  friction to frontend development. They analyze developer experience challenges and
  explore how schema design decisions impact the practical usability of GraphQL, particularly
  when integrating with legacy systems.
---

00:26:23:16 - 00:26:58:18
Jens
We define the price as an entity. And now we have the connect directive. And with this connect
directive we're essentially coupling the implementation of this entity or the loader of the entity.
We, we couple this to a REST API. And so now if we want to change this REST API to a gRPC
API, or we change it to Soap or I don't know, we make other changes.

00:26:58:21 - 00:27:27:22
Jens
It essentially could mean that we, we, we cannot implement the, the exact same contract
anymore. Like you know currently we get back ID active currency unit amount. And this is this is
mapped in the selection because we get back from the, so we have a mapper function in the, in
the selection in line 11. So there's some level of abstraction.
00:27:27:27 - 00:27:51:29
Jens
But at the end of the day, we, we're kind of really bound to, to two options like either we can
implement this with a connector and, selection function will be enough to map this to the REST
API or at a later stage, we have to implement it with, with GraphQL. And yeah, that might be a
limiting factor.
00:27:52:01 - 00:28:26:18
Jens
If you scroll down to line 25, we see a little bit more. So for example here, you can see that we
load products with http get function from slash products. And then we have a mapper function.
So we have id name and on price we have the id which is default price. And so now just just
imagine that in the future we want to change the rest API.
00:28:26:21 - 00:29:00:09
Jens
And we would not get the price like this. Like it. Or the price ID would come from another place
or whatever. What would we be able to make this change without somehow breaking the
schema in the future? Like, this is such a tight coupling in this case that I. I would be worried
that this we might eventually run into, into issues and at the second time, what I don't like about
it is Stefan.
00:29:00:09 - 00:29:26:24
Jens
You you I know your your like, not the, the deepest federation expert, but, if you look at line 25
and, like, between line 25 and line 39, like how many lines are relevant for the graph, for the
structure of the graph.
00:29:26:26 - 00:29:29:03
Stefan
For the structure of the graph.
00:29:29:05 - 00:29:37:00
Jens
consumer?
Like which lines are relevant that tell us something about what the API's is doing for the
00:29:37:02 - 00:29:43:15
Stefan
One two.
00:29:43:17 - 00:29:45:29
Stefan
3, 4 lines.
00:29:46:06 - 00:29:50:16
Jens
Which which which which three, 3 or 4 lines.
00:29:50:19 - 00:29:57:15
Stefan
So it's a query product, where we're getting it from and what we're getting.
00:29:57:18 - 00:30:22:03
Jens
That's, that's not something we, but that's defined in the product. So really what what what you
need to know as a consumer, it's it's type query and it's products. And that returns a list of
product. But everything from line 27 to line 39. It's just noise. It's this is this is essentially
backend code. Why why is it in the schema.
00:30:22:03 - 00:30:52:26
Jens
Why why do we make it harder? Because, you know, I think what, what we have learned over
the last few years is that graphql. It's it's mainly driven by front end guys. Okay. Yeah. And front
end guys, they are like, hey, I need this query. I need that data. And there might even be in the,
in the, they might even be capable of, of designing a little bit schema or making some changes
to, to the schema contract, but they don't want to worry about.
00:30:52:26 - 00:31:23:05
Jens
Is this coming from a REST API or something? And by mixing connect directives into the
schema here, from my point of view, what we're doing is we're making it harder for frontend
guys to think about, to think about schema and get involved because there's there's so much
noise. So think about the use case where you have, like ten root fields, like not just products,
not just one field, but you have ten.
00:31:23:07 - 00:31:37:07
Jens
So ten times like what do we have like 25 to 39. So ten, ten times. And then then for each call
like 15 lines or something. And it's just so much noise.
00:31:37:09 - 00:31:59:18
Stefan
Question though down here. We have the legacy approach. Let me pull it up. So I said this is
how you used to do it, right? This pattern is cleaner than the legacy approach of creating an
inaccessible entity. True. What does that mean? So prior to the 0.2, you could you could only
add connect to fields and use entity true to resolve.
00:31:59:21 - 00:32:04:22
Stefan
And so what does that mean. Wass connect before or is that just part of the rest connectors?
I'm not sure what this means, by the way.