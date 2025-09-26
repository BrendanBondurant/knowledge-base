---
type: podcast-chunk
title: Schema Design Philosophy and Error Handling
slug: ep27-11-schema-design-and-error-handling
series: The Good Thing
episode: 27
chunk: 11
segment: API integration patterns and error strategy
timecode: 00:48:06 – 00:51:17
start_time: 00:48:06
end_time: 00:51:17
speakers:
  - Jens
  - Dustin
  - Jesse
topics:
  - Schema Design
  - API Error Handling
  - Integration Patterns
tags:
  - schema-design
  - error-handling
  - api-integration
  - data-modeling
entities:
  - GraphQL
  - WunderGraph
summary: Conversation about schema design principles, structured error handling, and integration patterns that improve developer experience and system reliability.
---
00:48:06:27 - 00:48:09:02
Jens
And I think it's much easier if we just have.
00:48:09:04 - 00:48:10:08
Dustin
Our.
00:48:10:10 - 00:48:11:29
Jens
Schema and whatnot.
00:48:12:01 - 00:48:23:10
Dustin
I mean this is a great discussion I think for a separate, good thing. But also like I also want
someone to highlight, like how do you do error handling? Right. Like it's another beast.
00:48:23:12 - 00:48:46:12
Jens
Yeah. You know, like, I it's you're triggering me. But I wrote, like, posting on all of this might, but
this is also from one of my blog posts. When, when you, when you integrate with, with, with a
well-designed REST API with a good open API spec, a good Rest API, sometimes they return
unions.
00:48:46:12 - 00:49:12:13
Jens
So there's like the one off directive or any of, and then they can have discriminator fields or
maybe a header to discriminate. And then you can also have status codes as discriminator so
that means you have like three possible options that distinguish what is actually coming back.
And then now here's my question. Let's say you have a Rest API and it returns five possible
things.
00:49:12:16 - 00:49:31:22
Jens
Do you really want to create like, like a union in your GraphQL schema that can represent the
five possible things and then map them? Or do you just want to say, oh, in my GraphQL
schema, I don't care about all these errors. They mean nothing to my front end. I hide them
completely away. Let's just focus on our use case here.
00:49:31:22 - 00:49:56:07
Jens
And if something goes wrong, we just say it goes wrong like it's broken. Like, do I need to
expose a rate limiting error from stripe to my front end? Where are the front end guy? What do I
do with, stripe rate limiting error? Like the. It doesn't matter for this here, Jesse. Any you feel
you need to say something?
00:49:56:10 - 00:50:16:11
Jesse
Yeah. If we take all this, kind of negativity about how you can use a DSL in your, in your schema
to describe an external API and you kind of just completely flip it to how we approached it. We
have a full programing language to handle all of these transformations. And, different error paths
you might want to handle.
00:50:16:11 - 00:50:36:04
Jesse
You can do anything you'd like with the response from the API you're wrapping, whether it's,
iterative transformations or, completely changing the shape. You can even join different things
together. Like, let's say you have a Rest API that has posts and authors and GraphQL expects
those two things to be in the same type. You can just merge them.
00:50:36:07 - 00:50:47:12
Jesse
It's not, mental gymnastics to figure out how to represent your business use case in some
limited language. It's, just programing.
00:50:47:14 - 00:50:58:17
Dustin
It needs some. I would argue that, hey, I can just do it in my schema and I don't have to do
anything. I mean, with plugins, you can also just, build your plugin and deploy it with the router.
00:50:58:19 - 00:51:00:12
Jesse
Yeah.
00:51:00:14 - 00:51:17:15
Jens
Which is a good, segue, plugins router. So I have my plugin. It's, probably like a go binary. How
do I get it to the router?
