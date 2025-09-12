---
title: "Q&A: Plugin Flexibility, TypeScript/Go SDK Support"
start_time: "00:47:27"
end_time: "00:50:32"
tags: [plugins, typescript, go]
---
00:47:27:23 - 00:47:32:17
Jens
But, yeah, I hand it to to Jesse to moderate a bit. The chat.
00:47:32:19 - 00:48:02:01
Jesse
Yeah. For sure. So starting off from, with a question from G. Garnier. Garnier. They ask, can you
add custom code before sending a request? I believe they're referring to wrapping, an Http
subgraph with the gRPC plugin system. And the answer is yes. You can, the code that is inside
of your resolver, whether you call your own database or return mock data or do whatever you're
going to do with the request is totally up to you.
00:48:02:02 - 00:48:19:16
Jesse
You can transform the parameters and then forward them on to an external API like stripe or,
slack, whatever you might want to use. That's not GraphQL native. That's totally up to you. It's
fully, fully functional. Turing complete. Go. You can do whatever you'd like. Oh, but it's your
button.
00:48:19:18 - 00:48:25:03
Jens
It's not just go right. We can do plugins in other languages, right?
00:48:25:05 - 00:48:26:20
Dustin
Typescript.
00:48:26:22 - 00:48:30:10
Jens
TypeScript for sure. That's good.
00:48:30:12 - 00:48:48:18
Jesse
The main supported, happy path for us right now is between go and TypeScript. But, in the
future we will support more languages. And with the gRPC service architecture, you can use
pretty much any, any, framework you'd like. Right now we have some special sauce for plugins
specifically that has not been developed outside of the go.
00:48:48:18 - 00:48:58:00
Jesse
And TypeScript ecosystem right now, but we can that'll be expanded over time, Ludwig can
touch more on that. Maybe.
00:48:58:02 - 00:49:00:18
Ludwig
I didn't get I didn't get to the last part.
00:49:00:18 - 00:49:08:23
Jesse
What is it? The router plugin or our custom library for developing plugins, porting that to other
languages. Then go and TypeScript.
00:49:09:00 - 00:49:13:15
Dustin
Tracing support and, yeah, HTTP support.
00:49:13:17 - 00:49:37:03
Ludwig
We have a little bit of code in place that we can enhance the, fast development experience, by
providing stuff like Opentelemetry integration directly. It's also inside of our, Cosmo GitHub
repository. So it's called router plugin. You can basically use, existing helper functions to, to
bootstrap your plugin.
00:49:37:05 - 00:50:05:14
Dustin
So today if you, if you build a plugin and go, you also get out of the box, telemetry open
telemetry supports, coupled to the router. And also you can, leverage an optimized Http client
for, for, integration work. It's always part of our go SDK. And very soon I think we will have
something equivalent in all the, supported languages.
00:50:05:16 - 00:50:32:08
Jesse
All right. And we have a second question from Sanath. That is not entirely clear to me at the
moment. But from what I can tell, I think you mean that as the GraphQL query being sent over
gRPC. Am I correct? Are you in the. Are you able to reply to the question with some
clarification? Unfortunately, with zoom, I'm not able to both text and answer the question live, so.