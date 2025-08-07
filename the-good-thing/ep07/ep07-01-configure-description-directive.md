---
title: Configure Description Directive and Large-Scale Schema Metadata
slug: ep07-01-configure-description-directive
series: The Good Thing
episode: 7
chunk: 1
participants:
  - Jens
  - David
segment: Introduction and Configure Description directive
timecode: 00:00:00:00 – 00:05:06:09
start_time: 00:00:00:00
end_time: 00:05:06:09
speakers:
  - Jens
  - David
topics:
  - Configure Description directive implementation
  - Schema description propagation in federation
  - Customer-driven feature development
  - Large-scale schema metadata challenges
tags:
  - graphql
  - federation
  - directives
  - schema-composition
  - customer-feedback
entities:
  - WunderGraph
  - Cosmo
  - GraphQL
  - Federation
  - Jens Neuse
  - David
  - Stefan Avram
mentions:
  - Stefan's marriage ceremonies
  - customer use case with 80-90+ graphs
  - description propagation algorithm
  - granular control over federation descriptions
  - post-process transformers
summary: |
  Jens introduces episode 7 with David and Sergiy while Stefan is away. David explains the recently implemented Configure Description directive, which gives customers granular control over how schema descriptions propagate in federated graphs, solving challenges for large-scale deployments with 80+ subgraphs.
---
Episode 7
00:00:00:00 - 00:00:54:03
Jens
Hey, everybody. This is the good thing today. We're just a little bit late. As you can see, it's not
Stefan. It's just Jens. I just, brought, David and Sergiy, today to the stream, and, Yeah, Stefan is
currently, doing his, marriage ceremonies. So he's off this week, and, I thought this is a great
opportunity to to bring in some fresh new content to talk about.
00:00:54:05 - 00:01:28:17
Jens
Yeah. GraphQL, query planning, federation composition, all these kind of things. With me today,
I have, David, our chief executive worst engineer. He's one of our masterminds behind, yeah,
GraphQL composition. And I have, Sergiy, who's been working on query planning and, the
GraphQL engine, behind Cosmo for, for quite some while now.
00:01:28:19 - 00:01:37:06
Jens
Yeah. Let's start with David. David, how are you doing today?
00:01:37:08 - 00:01:47:05
David
complain.
I'm very well. Thank you for asking. jens, it's a nice day. It's cold, but it's, it's not raining, so can't
00:01:47:07 - 00:01:52:26
Jens
Well, what what have you recently been working on?
00:01:52:28 - 00:02:17:15
David
A week or two ago, we were working on, configure direct, configure description. That was, a
cool Idea that came from a customer. I think we got we got it to a great place that allows, not
only that customer, but everybody to have granular control over their federation descriptions.
Really happy how it turned out.
00:02:17:17 - 00:02:31:22
David
We have a further ideas how we can add and add more to it, but, yeah, I'm happy with how it
went. And it was it was fun to implement and fun to have that feedback loop directly with the
customer on it.
00:02:31:24 - 00:02:41:12
Jens
Can you give us a little bit of, of background on, on this idea with configure description, like
where, where did this thing come from?
00:02:41:14 - 00:03:11:19
David
Yeah. So this customer, essentially wanted to have granular control over how their descriptions
propagated in the, in the supergraph. So for folks who maybe are not so familiar, you can have
multiple services that have the same instance of a coordinate. So you could have query dot field
in one graph and then query dot field in another graph.
00:03:11:21 - 00:03:34:27
David
And they could each have their own description. And for whatever reason that may be that you
want to have one description in one service, which serves a function for the developers there
tells them information. It's also possible that field has a slightly different role in that graph
compared to another one. And then you have another graph where you have a more of, outward
client facing description that you want to propagate.
00:03:35:00 - 00:04:06:29
David
But, the actual algorithm of how those descriptions get propagated into the federated graph,is to
naive to be able to have that kind of granular control. So this customer essentially, and I believe
they were they had like a Transformer so that they could, do all this with, with a post process or
like a perhaps it was like a middleman process before the composition happened to propagate
what they wanted in there, or they would rely on warnings and errors that things were not lining
up how they should have done.
00:04:07:01 - 00:04:27:14
David
And basically, we tried to streamline that process so that they can just stick a directive in, do
they want the description in the federated graph? Okay, there you go. You don't want it to be in
the federated graph or anywhere that's public. Okay. There you go. You want to override what's
actually in there with something else. So you have one description for your developers who are
working or owning that subgraph.
00:04:27:21 - 00:04:38:28
David
You have a different description for what actually, is propagated. There you go. You can do all
these things. And I believe for the most part, we've solved that issue quite elegantly.
00:04:39:00 - 00:05:06:09
Jens
Yeah. It might sound like like, like a very minor thing. Like if you if you think about composition in
the, in the world of Federation, I think the very last thing would be to, to talk about direct, to talk
about comments or descriptions, but as you, as you scale. I think this was, very interesting to to
see that at, large scale environments.