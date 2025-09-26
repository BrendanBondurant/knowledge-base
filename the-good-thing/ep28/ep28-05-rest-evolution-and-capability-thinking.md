---
type: podcast-chunk
title: REST Evolution and Capability Thinking
slug: ep28-05-rest-evolution-and-capability-thinking
series: The Good Thing
episode: 28
chunk: 5
segment: API style evolution, patterns, and capability-based approach
timecode: 00:28:33 – 00:36:20
start_time: 00:28:33
end_time: 00:36:20
speakers:
  - Jens
  - Stefan
  - Daniel Kocot
topics:
  - REST Evolution
  - Capability Thinking
  - Interaction Patterns
tags:
  - rest
  - capability-thinking
  - api-design
entities:
  - REST
  - Daniel Kocot
  - WunderGraph
summary: Daniel explores REST’s evolution, common interaction patterns, and his advocacy for capability-driven API thinking as a way to bridge technical and business language.
---
00:28:33:15 - 00:28:45:03
Stefan Avram
Yeah. thats fair. And I would tend to agree with that. It's good that you guys stay on for the long part of that journey. The ends are funny enough. I knew you were going to bring that up. Really? Yeah that video I know.

00:28:45:05 - 00:29:14:02
Jens Neuse
No not not not in a negative way. I'm just curious about your your your take. I have no strong opinion on the on the craft in general, but. Okay. You mentioned REST is not just an API. Some people would say it's an architectural style or pattern or, how would you say the understanding of APIs and REST over the years has changed?

00:29:14:02 - 00:29:41:20
Jens Neuse
Because we recently had Kevin Swiber on the On the Stream. You probably know Kevin and also the one, one one of the, known names in the, in the API space. And he also kind of, kind of said like, in the past when people said REST, they might meant like hypermedia or something. But today it can be anything, it can be JSON over HTTP.

00:29:41:21 - 00:30:07:08
Jens Neuse
And he also said like, it's it's not so important how we call the things like, because MCP and hypermedia have actually quite a lot in common. And he's like, yeah, like the patterns are all the same. It's just a bit different. And we name things differently today. But but hypermedia was never really gone. It's just yeah, the styles they, they changed.

00:30:07:08 - 00:30:18:01
Jens Neuse
But how do you see the, the evolution of, of API styles and how people perceive REST and stuff like that.

00:30:18:03 - 00:30:36:19
Daniel Kocot
Starting with REST and what, what do we see? So I can I can totally agree with Kevin. It's really about. Yeah, bringing JSON over the wire. Actually this is what we see at customers. This is something. But customers also say to us so we have a slide in our training. It's really a quote from a customer of us.

00:30:36:21 - 00:31:07:08
Daniel Kocot
Yeah, we doing Json over Http. That's, that's, that's the thing there because they were promised something different. Then they did a training with us in regards of REST and open API and and then this, they thought, okay, this was nothing we discussed when we started this initiative. So it was really clear, okay, they're doing the they're doing actually a good thing, but they're doing not what was actually the, the thing they, they wanted to to have because somebody said it to him.

00:31:07:08 - 00:31:31:18
Daniel Kocot
Because when it's coming from management and the management says REST, they don't normally know what, what do we really mean. So that there's hypermedia included and so on and so on. That's why what what we did actually in the, in the past was to setting up so-called interaction patterns, to not talk about technology, to really say, okay, I want to have resources, I want to have hypermedia.

00:31:31:18 - 00:31:59:24
Daniel Kocot
So this is this is one type of pattern there. Then I want to have a tunnel, which is nothing more than doing a gRPC or RPC actually to just say I just call a function that is somewhere else. I don't know where, but it's available. And then you had you have a pattern called query where it's actually clear you want to query something.

00:31:59:26 - 00:32:27:27
Daniel Kocot
Mostly it will be GraphQL or when it's really available and made available with the with the open API 3.2 I think. Yeah, yeah. Then we have something with the with the query work there. So it's, it's it's this part. And then we have the last pattern. It's event based. Because normally when we come to customers it's always they say yeah we read something from the business perspective.

00:32:27:27 - 00:32:50:03
Daniel Kocot
We want to have something like they use on Facebook. I can just query and there comes this graph, blah blah, blah, blah. I saw this, I saw some kind of article about this and we want to have it and was like, okay, they're talking directly about GraphQL, but not really understanding what is the benefit behind it and where it actually should be placed.

00:32:50:05 - 00:33:18:26
Daniel Kocot
And we have the same problems or challenges with yeah. Talking about events because when people not technical related to the stuff talk about. Yeah, we, we use Kafka, it's wrong and the business knows there's Kafka involved. It becomes Kafkaesque in the end. So it's it's really nothing a business person should know that there is a technology in use.

00:33:18:27 - 00:33:43:20
Daniel Kocot
It has to that it has a name that has nothing to do with technology. Actually, they should just know, oh yeah, we doing stuff with events. That's that's all to to really not have this technical discussions around this because of what most people oversee is when we, when we come or talk with customers. Oh yeah, we use open API.

00:33:43:23 - 00:34:04:19
Daniel Kocot
Then it's clear you you want to do REST or Http over the wire. That's that's interesting. Do you do do you use open API with every use case to describe it? Yes. Oh yeah. Then you have always this. That's interesting. So it's also sometimes to really make, make people understand what, what is actually happening behind the scenes.

00:34:04:19 - 00:34:31:00
Daniel Kocot
Because most people don't have this idea that things are connected together. Some people see, okay, it's a it's a description, okay. I can use it for everything I want. And and this is, this is really, really something to look at. That's that's why we did this, just things around to make it really more clear. But with this, it's not really clear also for the business when you when you still talk about this interaction patterns.

00:34:31:02 - 00:34:48:12
Daniel Kocot
That's why I'm actually now looking into this capability, thinking to really take something which is understandable for the business side and not still relates to technology. On, on, on, on the other hand. But this is what what is really needed there.

00:34:48:15 - 00:34:51:17
Jens Neuse
What do you mean by capability thinking?

00:34:51:19 - 00:34:52:27
Stefan Avram


00:34:52:29 - 00:35:26:26
Daniel Kocot
Capability thinking comes out the enterprise architecture context. So you can describe a business needs with capabilities, which makes things more handy, more clear for non-business, for non-technical people to understand what's this little endpoint or this little API or however we call it, really does. And this is this is the idea behind the to to really not say, okay, we have a catalog with a lot of APIs included.

00:35:26:29 - 00:35:52:04
Daniel Kocot
Here's the endpoint slash product. And then you have this standard way of describing the things just saying okay, we have the possibility to list all of our products to really make it clear what what is actually happen happening there. And when you when you put this on on the, on the catalog, it's quite easy for people with semantic search to search for things.

00:35:52:06 - 00:36:20:12
Daniel Kocot
Because when I'm not technical, I can't really understand what is happening there because even in, slash product or product endpoint should not just list the products can be even used for more. So this should be described quite clearly then. So this is this is the idea. So we are just at a at the beginning to just look at it and say, okay, we know this from the enterprise architecture space.

