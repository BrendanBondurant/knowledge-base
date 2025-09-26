---
type: podcast-chunk
title: Proto Reserved Keywords and Versioning Strategies
slug: ep27-07-proto-reserved-and-versioning
series: The Good Thing
episode: 27
chunk: 7
segment: Reserved keywords and long-term compatibility design
timecode: 00:32:43 – 00:36:05
start_time: 00:32:43
end_time: 00:36:05
speakers:
  - Dustin
  - Jens
topics:
  - Protobuf Reserved Fields
  - Versioning
  - Compatibility Design
tags:
  - protobuf
  - versioning
  - schema-design
  - data-modeling
entities:
  - Protobuf
  - WunderGraph
summary: The conversation focuses on reserved Protobuf keywords, versioning strategies, and ensuring long-term schema compatibility.
---
00:32:43:16 - 00:33:24:13
Dustin
And so if you compile something from proto to, something from GraphQL to proto, it will not just
create this mapping file Json, but but Ludwig mentioned which contains the type mapping, but
also the you also produce a service proto doc Json file, which has information of, the field order.
And when you, when you change a field in a graphql schema, we also use that you mentioned
the reserved, reserved, directive to, you know, to continuously, make the, proto, message
compatible with your, with your previous changes.
00:33:24:13 - 00:33:27:15
Dustin
If if it's not a breaking change.
00:33:27:18 - 00:33:50:02
Jens
So let's say I create a user type and it has id and name. So then ID in the, in the proto definition
it would be like index one and name is index two. Yeah. So let's say I now remove okay. That
would be a breaking change on, on the, on the GraphQL side. But let's just say we do that.
00:33:50:06 - 00:34:01:24
Jens
index.
So we remove the name field. You would then put the the index two in the proto as the reserved
00:34:01:26 - 00:34:07:02
Dustin
And it would count one level and assign three to the to the new field.
00:34:07:05 - 00:34:19:25
Jens
If we add a new field. So if we then add like I don't know, foobar, it would automatically get the
index three so that we're not mixing up index two and three. Yeah.
00:34:19:27 - 00:34:40:19
Dustin
And the result also supports ranges. So, the protograph library automatically identify if we are
and a like we we made multiple changes over time. So it for for efficiency reason it instead of
having multiple reserve statements it would just use reserve from 2 to 4. For instance. Yeah.
00:34:40:21 - 00:35:08:13
Jens
Okay cool. So we have our query. It goes to the router, the router does magic query running. But
by the way, crew planning, it's a, it's a topic on, on on day one. God, Sergei and I understood
the group planner. Now it's just God.
00:35:08:15 - 00:35:32:01
Jens
No, no. For you, the the funny thing about our query planner is, every time I have to onboard
someone like I. I wrote parts of it, and, I'm, I'm, I'm more guilty of contributing to the to the
execution. But every time I have to onboard someone to our graphqlgo tools, it's it's like, like a
little, like a little birthday party for me.
00:35:32:01 - 00:36:05:06
Jens
Because where I feel like a squirrel, you know, I look into the code base and I find things. I'm
like, oh, interesting. This is how we did it. And, yeah, like the the code base is just so insanely
big. It's it doesn't fit into your head. It also doesn't fit into an llm and llms that's the topic I want to
pick up later because, Dustin did some amazing stuff with, with integrating cursor workflows into
the into this whole plugin architecture.
