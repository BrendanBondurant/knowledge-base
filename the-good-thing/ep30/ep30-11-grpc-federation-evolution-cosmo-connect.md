---
type: podcast-chunk
title: gRPC Federation Evolution with Cosmo Connect
slug: ep30-11-grpc-federation-evolution-cosmo-connect
series: The Good Thing
episode: 30
chunk: 11
segment: gRPC and Federation Evolution
timecode: 00:30:15 – 00:37:47
start_time: 00:30:15
end_time: 00:37:47
speakers:
  - Jens
  - Stefan
topics:
  - gRPC vs GraphQL
  - Federation Evolution
  - Performance Improvements
  - Interoperability
tags:
  - cosmo
  - grpc
  - graphql
  - federation
  - performance
entities:
  - Cosmo Connect
  - gRPC
  - GraphQL
  - Federation
summary: They clarify misconceptions that Cosmo is pivoting to gRPC, explaining that it's an evolution: GraphQL on the frontend, gRPC on the backend, preserving interoperability while improving performance and extensibility.
---

00:30:15 - 00:30:32
Jens
Like you can do like so many, so many things. And then if you build that entity layer, just ask yourself, if I'm not always using, GraphQL to, to access it, maybe. Yeah, maybe we just name it more, more generic. So I call it entity layer.

00:30:32 - 00:30:46
Stefan
No. Well said. And for all the viewers that we have guys, thank you so much for joining us today. We're kind of setting the record straight on wunder graphs direction and federation and where we're going. We just finished talking a little bit about the entity layer and its concept. The Jens is constantly bringing up and it makes sense.

00:30:46 - 00:31:09
Stefan
It's kind of exciting. And and next topic I want to talk about is gRPC. We hear this a lot. And somebody I wonder who said that we're pivoting into gRPC. I don't think that's true. The last time I heard or, you know, in our all hands, I don't think we talked about that. Can you help me understand a little bit?

00:31:09 - 00:31:30
Stefan
Like, why do you feel so strongly that the next generation of federation speaks gRPC? For those that might not be familiar, you might want to take a look at Cosmo Connect. It's a feature that we've released. It's really powerful, and we really believe that the next iteration of Federation speaks gRPC. So again, what do you think about that topic?

00:31:30 - 00:31:40
Jens
So,

00:31:40 - 00:31:45
Stefan
Jacob is going to put the meme here calculating, you know, like the windows the blue thing.

00:31:45 - 00:32:14
Jens
Yep. Okay. Like I said, with the entity layer, you have root fields in the graph and they are kind of like query like search fields. So they can have like search params and then they return a thing. All right. So these root fields you send them to a resolver and that returns a thing in the federated graph this thing is typically an entity.

00:32:14 - 00:32:40
Jens
So that means after the first layer of data fetching, everything else is entity calls. Like so you, you, you say oh I have product. And for this product with ID seven, give me other fields, give me reviews. And I'm not saying that for one product, I'm saying it for 100 products. So we need batching. There. Okay.

00:32:40 - 00:33:09
Jens
So if I want to efficiently batch those requests, why do I need to build a GraphQL server? I, I don't get it. Why why do I need a framework? And the thing is, Apollo created a situation where if you ever want to see any sort of innovation on the federation layer, what you have to do is you have to extend the non-existing spec.

00:33:09 - 00:33:39
Jens
So the by spec I mean you, you, you just document like two lines where you say, oh, here's the new directive. Nobody knows how it works, but here's the directive. Then you implement it in the router and then you implement it in all subgraph frameworks. And that means you have a huge lag. And oftentimes you can see that on the compatibility compatibility side of, of Apollo Federation, it can take years.

00:33:39 - 00:34:06
Jens
And then you still don't have support in all frameworks. So that means Apollo has a monopoly on owning what is possible in the federation layer. And, what we're doing with Cosmo Connect is we move GraphQL into the router, and we move GraphQL at build time to like the composition layer. So you have composition that gives you a schema and and everything.

00:34:06 - 00:34:41
Jens
Then we compile it into gRPC. And because we compile it into gRPC, the dependency on the subgraph layer essentially is just vanilla gRPC. So what that means is if we add a feature to the router, it is available to Python dotnet Java rust, Kotlin. Every language that supports gRPC, it's immediately available. If we can make an improvement, it's immediately available to everybody.

00:34:41 - 00:35:07
Jens
The second part is let's talk about the the request chain. And let's say you, you have a, you have a GraphQL request. It comes from the client to the router. The router parses the query, it normalizes it, it in lines, fields it in lines, fragments. It does all the magic, which is super expensive. So we have a cache for that.

00:35:07 - 00:35:28
Jens
And after all this magic is done we stick that into into. Yeah, into the into the cache. And then we make our subgraph requests. So now we know exactly okay we have a root field. And then we have subfields. So we do like entity calls and whatever. And when we do these entity calls we know we need to do batch calls.

00:35:28 - 00:35:57
Jens
Why should we now take the efficient like all the efficiencies we have in the router to generate text and send. Because GraphQL queries text send that text to the framework. And now the framework, the subgraph framework needs to parse the text needs to analyze it needs to normalize, it needs to validate, it needs to implement data loading to now efficiently resolve that query.

00:35:57 - 00:36:21
Jens
All this stuff already happened in our router and now you have to do it again. Why? All we need to do is we need to call a bunch of, resolver functions. So in terms of efficiency, something that is talked a lot about is how fast can your router be? My question for you is how fast is your subgraph?

00:36:21 - 00:36:47
Jens
Because in our case, most of the time, like in benchmarks, what people do is they use rust as the subgraph framework. But what if you have Node.js or Python or Elixir or something that is not crazy fast in parsing, GraphQL grows, so suddenly the router is good and the backend is actually your, your, your bottleneck. So that's one part of the story.

00:36:47 - 00:36:56
Jens
And to round off this monologue, this is my last point, Stefan.

00:36:56 - 00:36:57
Stefan
For now,

00:36:57 - 00:37:20
Jens
For now, but for now, yes. Cosmos connect is is available in two flavors. One flavor is you deploy the gRPC service as a dedicated service. So it actually is a dedicated service that lives somewhere. And the second shape, you can you can use cosmo connect  You deploy your subgraph as a, as, as a, as a plugin.

00:37:21 - 00:37:47
Jens
So it runs like a co-processor, side by side with the router. And if you run a subgraph as a co-processor, that means it's ultra low latency and it's zero overhead in deployment. So you're not deploying another thing. So now here's the question. So you have Apollo connectors where you put directives on your schema. And then it can do Rest APIs.
