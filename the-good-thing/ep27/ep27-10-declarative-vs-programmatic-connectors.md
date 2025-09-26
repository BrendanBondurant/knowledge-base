---
type: podcast-chunk
title: Declarative vs Programmatic Connectors
slug: ep27-10-declarative-vs-programmatic-connectors
series: The Good Thing
episode: 27
chunk: 10
segment: Debugging advantages and SDK-driven integration
timecode: 00:43:10 – 00:48:06
start_time: 00:43:10
end_time: 00:48:06
speakers:
  - Jesse
  - Jens
  - Dustin
topics:
  - Declarative Connectors
  - Programmatic SDK
  - Debugging Advantages
tags:
  - connectors
  - debugging
  - sdk
entities:
  - Cosmo Connect
  - WunderGraph
summary: Jens and Stefan critique declarative connector approaches, highlighting debugging advantages and the flexibility of SDK-based integration workflows.
---
00:38:48:16 - 00:39:13:16
Jesse
It might go down once in a while. And you can use your own Prometheus metrics.
Opentelemetry. You can do BGP whatever you want. Because it is a completely separate
process run underneath your, DNS, your service mesh, whatever you'd like, and the router just
contacts it via however you would normally want to network your services together.
00:39:13:18 - 00:39:37:26
Jesse
And that gives you total control over the deployment, the versioning, the packaging. And that's
really going to be best either if you have something complex that needs its own resources or
access to, what are they called, an AWS, like a virtual private network or something like that?
AWS has a fancy word for it. Like if you need access to rds or something that could be a good
option.
00:39:37:28 - 00:39:40:02
Jesse
But you get all this control.
00:39:40:05 - 00:40:11:12
Jens
Yeah. Got it. So we have, like the lightweight option, the plugin. I think that's that's a pretty good
option if, if the plugin just talks to another API, like it will just be IO it, it cannot use a lot of CPU
and memory, so it's fine. Just run it as a, as a plugin. That that would also be like our, our I
would say alternative to, to Apollo connectors.
00:40:11:12 - 00:40:37:16
Jens
Yeah. Connect it. It's always a problem. Is it Cosmo connectors or Cosmo Connect. And is it
Apollo connectors or I sometimes stumble okay. So we have plugins, lightweight. Just IO talk to
something. If you do some more heavyweight stuff than dedicated gRPC. Okay, we got that.
And.
00:40:37:16 - 00:41:03:06
Dustin
Okay, maybe maybe another maybe just another two points. I see I also very huge benefit in
like, local development if you just want to try something out, but also for preview, preview,
subgraph changes. So you can also create like in cosmo we have all cosmo feature flag. You
could also deploy console connect plugin and deploy that as a feature flag.
00:41:03:06 - 00:41:13:08
Dustin
And that means, you don't have to deploy another router to, to, preview your changes on, on a
QA system.
00:41:13:10 - 00:41:14:12
Jens
Okay. That's also, if.
00:41:14:12 - 00:41:35:17
Ludwig
You're starting also, if you're working on a plugin, you can just, add another main file and
converge a plugin into a service like reuse the exact same code that you have been using for
your plugin. Just have another main file that stores plugin as a grpc service and just deployed
somewhere. So you have a plugin and and a service.
00:41:35:20 - 00:42:01:03
Jesse
Yeah, that's that's really important when we talk about these two separate ways of deploying it,
the only real difference is just how the service is initialized. All of the resolvers and the whole
like gRPC innards are identical for both implementation methods. It's just whether you use our
helper to run it on the socket using HashiCorps go plugin, or whether you launch a bog standard
Http2, gRPC server over the network.
00:42:01:06 - 00:42:23:27
Jens
Yeah, but that does one thing that that Dustin mentioned. That's an interesting point. We we
have never made it like a very big thing, but imagine we have a staging environment and we
have a new use case. We want to build a new feature. We currently don't have a lot of
resources to implement it. What we could actually do is we create a feature flag.
00:42:23:27 - 00:42:49:27
Jens
So Cosmo has a thing called graph feature flags. It creates a copy of your graph and you can
replace subgraphs in it. So what we could actually do is we create a feature flag. And under the
feature flag we we just create a plugin that adds our functionality. We say, hey cursor, implement
me this plugin with some mock data, whatever.
00:42:49:29 - 00:43:10:18
Jens
And instead of deploying a service which could be like a heavyweight operation, we need ops
and whatever. Let's say ops is not here. We we could just say, oh to to this feature flag, just
deploy a plugin with some mock data and that's it. And now we have something running in
staging. So that's I really like that.
00:43:10:24 - 00:43:45:01
Jens
And then to your other point, Dustin, because this is, this is one of my main criticisms of, of
Apollo connectors, you know, Apollo connectors, you have a subgraph schema. You put some
weird directives on it, like @REST, whatever. And you, you kind of map your, your GraphQL to
REST or Http, and, the typical approach to debug problems is and and this by the way, you like
sometimes Apollo goes like, oh, it's declarative.
00:43:45:01 - 00:44:08:25
Jens
This is so amazing. And I'm like, no, declarative is really not amazing. Because the biggest
problem with declarative is you have this spec that you give the router, and now you send a
request and you open the playground and you look into the playground, what the router does.
And if the router is not doing what you hope it should be doing, what are you going to do?
00:44:08:28 - 00:44:28:20
Jens
Like how will anybody tell you what in your mess of directives you have created is wrong? You
did. I don't know. I think it's very hard to debug versus Dustin. How do I debug a plugin?
00:44:28:23 - 00:44:48:14
Dustin
Yeah, it's I mean, it's it's just, as a service. I mean, it's just a process. And you can, depending
on what programing language you have implemented, the plugin, you can just open, your
golang IDE, your VS code IDE and attach to the process. And because there's nothing special
in it, you can make a query from the playground.
00:44:48:16 - 00:44:54:26
Dustin
When it will hits to the plugin service, you will. Yeah. Debug is usually.
00:44:54:28 - 00:45:25:25
Jens
So the plugin like we, we don't distinguish between subgraph and then gRPC like it's just the
gRPC method methods. You use VSCode, and delve, and you connect to the process and you
look what's going on and that's pretty easy and to, to, to do and also other things if we're already
talking about like comparison for example, with, with Apollo connectors.
00:45:25:27 - 00:45:51:22
Jens
A lot of let's say we want to integrate an external API stripe, whatever, some API from AWS,
they all have SDKs, and SDKs, good SDKs. they do more than just calling the rest API. They
can help you with authentication signatures, whatever. Like if you want to talk to things in AWS,
you have to sign requests.
00:45:51:22 - 00:46:21:09
Jens
And there's like different requirements. You like if we're talking about like real production grade
stuff, you have to stick a lot more things into connect directives then just talking to a REST API.
In reality, like in AWS SDK, it does a lot of things for you and it can be very helpful. So with with
Cosmo Connect, you, you can just import those SDK and do whatever you need.
00:46:21:11 - 00:46:37:23
Dustin
I also think there's an architectural break. Do you really want to give your schema designers that
responsibility of integrating APIs? I think yeah, I think not.
00:46:37:25 - 00:47:10:12
Jens
No, not not even that. But my my personal pet peeve is if you. So when you design a schema
like for example, you create an open API spec. Ideally you really just define the spec or the
GraphQL schema. You just say, here is the schema. I make this an entity. And the the that was
always my idea of, of APIs is the the spec of the API should should define the contract and and
hide from me the implementation.
00:47:10:19 - 00:47:42:25
Jens
Like I don't want to leak the implementation into the contract. So and this is one of my worries
with with Apollo connectors, if you combine schema and directives to connect to REST APIs into
one thing, it it is possible that you design the GraphQL schema after your REST API because
you have this natural tendency of I mean, you have the both on the same page, so why not use
the GraphQL and follow more of the REST?
00:47:42:25 - 00:48:06:27
Jens
Because that's what you connect. And then you have to do mappings and things. And so this is
one thing. And another problem I have with these directives is I think they are very verbose. And
if you look at the schema it is not super clear what is the schema. So you have schema and you
have connectors and it's a it's a mix.
