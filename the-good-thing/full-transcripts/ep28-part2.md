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

00:36:20:14 - 00:36:50:13
Daniel Kocot
It's working good to to really describe capabilities and make them visible. Maybe it's a good idea to use this in the in the API space. Also in regards of this, AI thing that's that's coming up with MCP and A to A, because this will be more related to, to these type of protocols to to understand what, what is really the intent of this endpoint and not not just doing some kind of AI.

00:36:50:15 - 00:37:04:09
Daniel Kocot
It could do this or it could not do this. So, we, we, we use it somehow and maybe we find the right usage for that. So this is this is actually the idea behind this. And as I mentioned, it's at the beginning.

00:37:04:12 - 00:37:04:28
Stefan Avram


00:37:05:01 - 00:37:35:03
Daniel Kocot
So this is, this is something Kim Lane pointed at some post on LinkedIn from me in the, in the past day some, some stuff that has to be defined and so on and so on. This is what is quite interesting that there is a lot of, interest with the people who are really deep into the topic of APIs to, to really make it better for people to understand, because we are still from my opinion, not where we maybe can be to make to make it understandable.

00:37:35:03 - 00:38:01:11
Daniel Kocot
Because for most people, this is this is what we hear in the field is always, yeah, we have a management solution. Problem solved. But, you know it, I know it ,it's not buying something and using something if it is even having, having having your product running somewhere, it will not solve the problem of getting the things right in the end into this.

00:38:01:14 - 00:38:06:25
Daniel Kocot
This is something where we have really to look in and really bring the people to to that level.

00:38:06:25 - 00:38:13:04
Jens Neuse
Actually, by management you mean API management.

00:38:13:06 - 00:38:34:20
Daniel Kocot
It could be also event management or however we call it. So in the end we have to define what an API is. It could be also a GraphQL query or whatever. It's also some kind of interface to to to to see the the relevance. It's it's very for me it's quite hard to use this, this API term.

00:38:34:20 - 00:39:02:28
Daniel Kocot
So, that's why I talk always about interfaces. So it's, it's it's easier. It's not related to this, to this abbreviation of being misunderstood because maybe you meant something totally different by by saying it and it's, it's really in the end. And management is also, a big word. Yeah. Because nobody really defined what management of interfaces really means in the end.

00:39:02:28 - 00:39:12:07
Daniel Kocot
Because there is no clear defining some people think. It's about the lifecycle. Some people think it's about monetizing stuff and so on and so on.

00:39:12:09 - 00:39:29:26
Stefan Avram
But you know what this reminds me of? End. One time we were talking with a customer. We can't we can't say the name, but a very big and important customer in the United States. And we were asking them, what kind of tools are you using? And they said everything. And I was like, what do you mean? You're using everything we have, Kong.

00:39:29:26 - 00:39:50:11
Stefan Avram
We have WSL2   we have  Tyk, we have this, we have that. And I was like, or Jens was like, wait, wait, why do you have four API management tools? They were like, oh, because the first one didn't solve the problem. And I was like, wait, wait, wait, what? And we kept going through it. And every type of API tooling you could talk about, they were using that tool.

00:39:50:16 - 00:40:10:16
Stefan Avram
And then we asked them, what protocols are you guys supporting? Everything we said, like, is it from legacy and you're trying to modernize? No we tried. SOAP some teams build with rest. Some teams have dropped GraphQL. That's why we're talking to you guys now because of this. And it kind of like solves the point where you said in the beginning is that there isn't a tool that can solve this from the very beginning.

00:40:10:16 - 00:40:21:22
Stefan Avram
It was a people problem. And it's just so interesting to hear you say all that, because I have a fire drillgroup one second. But Jens, take over while I do this fire drill.

00:40:21:25 - 00:40:24:21
Jens Neuse
Do you have to do anything?

00:40:24:23 - 00:40:27:02
Stefan Avram
I just have to mute my camera so it doesn't ruin the stream.

00:40:27:02 - 00:40:41:16
Jens Neuse
Okay, okay. That's fine. Yeah. You know, this reminds me of, So. Well, I think for me, one of the coolest learnings is. So we we went through this wave of GraphQL hype, like, we're.

00:40:41:19 - 00:40:43:14
Stefan Avram
We're, we're.

00:40:43:16 - 00:41:11:26
Jens Neuse
We're slowly moving outside or expanding out of the, GraphQL space because we have we have actually learned ourselves that, APIs and GraphQL is, is a lot about people and process. Like for us, it was it took a couple of years, but even as a vendor, you can't just give people a tool. Like. But if you start talking to people like, what are the processes?

00:41:11:26 - 00:41:45:24
Jens Neuse
How do you actually create new APIs and this kind of thing? You kind of explored that the, there are, like you can give people an API gateway, but that's, that's not the solution. And so what what I found super interesting, when, when, when I was right in the middle of this GraphQL wave, like, couple of years ago, there was someone, like an API veteran, and he, he made, like, a, like, funny comment that I at the time, I, I couldn't fully grasp it.

00:41:45:27 - 00:42:09:18
Jens Neuse
Today I look a bit different on it. And he kind of said, if you have a shitty REST API landscape and you put GraphQL on top, like, yeah, now you have a shitty, shitty thing and you have a GraphQL, now you can query, your shitty thing. It's it's still a bad API. Their problem is not solved.

00:42:09:18 - 00:43:04:24
Jens Neuse
We've we've just added one more layer of complexity and and yeah, I, I really like your take that that you, you, you really try to, to help people. Looking at my speaker notes, because we, we always have amazing speaker notes. Jacob prepares, but, we we looked into some of your blog posts, and, if I look at some of the buzzwords that stand out, and also if I reflect on what I see in the in the community, a lot of people talking about MCP and AI and then as they do so and we, we kind of look at APIs, what, what, what everybody keeps talking about is governance and authorization, privacy,

00:43:05:00 - 00:43:31:12
Jens Neuse
these kind of topics. So I'm, I'm curious like from, from your perspective because you know, like everybody tries to do MCP andLLM and whatever and buzzwords and CEOs keep saying we can fire everybody because set alarm will take over the world. Well, we kind of figured out that's not the reality. But, from my perspective, there are a lot of really unsolved problems in the API space.

00:43:31:12 - 00:43:53:21
Jens Neuse
Like, we're we're not doing so great. And but I would love to to hear like your perspective. What are the the real big issues when when you go into into organizations like where where's the majority of of enterprises today and what are the the real big problems?

00:43:53:23 - 00:44:00:25
Daniel Kocot
The real big problems. They all have a gateway.

00:44:00:27 - 00:44:05:01
Stefan Avram
You can clip that clip. That right there.

00:44:05:02 - 00:44:34:24
Daniel Kocot
That's the thing a lot of, a lot of customers we are work with or prospects we talk to have a gateway or they don't have a gateway and have security issues because their APIs are not secure. But what should or should I should I use a gateway when I don't understand that there's a plugin engine into it that needs some kind of knowledge to, to, to move on and so on and so on.

00:44:34:24 - 00:45:03:16
Daniel Kocot
It's really it's really hard because, because the gateway is actually not an architectural tool. It's an infrastructure tool that's that's mostly interesting because we are just talking about the network traffic. We are we are putting through. So, so we removing from we building something by using infrastructure. And this is, this is since years the biggest gap we have there.

00:45:03:18 - 00:45:44:09
Daniel Kocot
And that there is a real misunderstanding. What what is what is actually needed it also what is about governance. Now you can still impress people by presenting linting for me that that shouldn't that shouldn't and use things somebody not should not, should should actually know when there is just a training. This this is for me the basic skill. So everybody should know that there are linters for API descriptions around, so that every API description can be linted, that there is testing, that I can test an API end to end, and so on and so on.

00:45:44:11 - 00:46:09:00
Daniel Kocot
For some people is also still the still mind blowing thing that that's possible. So you can impress people by just having micros running somewhere and in the end it's it's really and we see what happens there. So we are still talking about tooling, but we are not hitting, hitting the screen by saying, okay, how to get to a good API.

00:46:09:02 - 00:46:22:16
Daniel Kocot
Yeah, a lot of people then come up with, yeah, they are these guidelines. We use them, we just copied them. So we we do them. I use the Lando.

00:46:22:18 - 00:46:44:09
Daniel Kocot
Are you are you Google? Are you Microsoft? So get this as an inspiration and learn from others what what they did and build things on their own. So this is this is I think having tooling a lot. So you can you can have a lot of tools for everything. What you want to have. And there is the problem of adaptability.

00:46:44:13 - 00:47:16:24
Daniel Kocot
So people have to understand that a situation don't normally fit to their situation. What is what I saw somewhere else. Yeah. At a conference when somebody is presenting like a bang their API management solution by using Akamai and every possible tool in the market available to to to cover this API solution, that might not be the best fit for somebody listening to it, because they do it on different purposes.

00:47:16:24 - 00:47:41:23
Daniel Kocot
They do it because they have to they have regulations, they have to be redundant in geography and so on and so on and so on. But just to understand what is what is actually needed to to provide and maybe just use a proxy for the beginning, not the full blown solution. Yeah. Because you just want routing really understand what is what is really needed.

00:47:41:25 - 00:48:19:17
Daniel Kocot
And then from from that build build the things up and not just and not just say, okay, we start from the highest mountain possible. This makes the buy in into this solution into that solution. Because what what we do now with customers is building platforms. And platforms means to have a lot of tooling underneath the platform layer to really cover all the styles, to really cover all the things needed, but to make it not visible to the users because they get frustrated when they really see what is happening underneath the platform.

00:48:19:19 - 00:48:48:01
Daniel Kocot
And, and this is this is really the thing there to to have too much opportunities in tooling and not understand or have is this this is also one sentence. I always say we need the use cases. What use cases do you want to cover by using this integration style or what are your actual use cases you want to cover where you think an API?

00:48:48:03 - 00:48:51:29
Daniel Kocot
Whether STY could be helpful?

00:48:52:01 - 00:49:15:08
Daniel Kocot
And this is totally interesting. This is total hard for people to get there. But when you go into the business side, it's totally easy because the business tells you what they're actually need. They want to connect with other vendors, or they want to connect with other partners in their system, or they want to get some data from somebody.

00:49:15:08 - 00:49:42:22
Daniel Kocot
And, and enrich it and so on and so on. But when you when you go and onto the technical side, it's for them. Always hard to to say, okay, what are the use cases you want to cover with. With the integration platform you want to build and these, these these are, in my opinion, the, the problems and the challenges we have there to to really go, to really go that way down.

00:49:42:25 - 00:50:16:16
Jens Neuse
It it almost sounds like you present the problem, but you also kind of hint the solution. Get the business people on the same table with the engineers and have the business people explain. Yeah, what what what are the capabilities needed? Not writing endpoints, not writing GraphQL queries, writing down capabilities in plain English in post-its. And then thinking about okay, here are the capabilities we need.

00:50:16:18 - 00:50:35:21
Jens Neuse
How how could we implement that? Is this is this an event driven architecture? Do we need a Rest API for that? Do we need SDK s? This is something we should do with the query language but not be like okay, here's a here's a problem. What kind of GraphQL query will we build for that.

00:50:35:23 - 00:50:59:08
Daniel Kocot
Yeah. Or even just say, okay, we can just, we can just offer REST services. Yeah. This is this is this is the thing. Yeah. That's that's totally to the point to to really make them really make clear that there is conversation needed with within the organization. A lot of people always argue then. Yeah, we are talking with each other.

00:50:59:08 - 00:51:04:00
Daniel Kocot
Yeah. You talking not to the point because you don't want to.

00:51:04:07 - 00:51:12:11
Jens Neuse
Where's where's that gap. Why. Like it's so easy. Why why can't you bring the stakeholders together?

00:51:12:13 - 00:51:13:23
Daniel Kocot
They don't want to.

00:51:13:25 - 00:51:14:28
Stefan Avram


00:51:15:00 - 00:51:38:14
Daniel Kocot
Sometimes or sometimes you don't know who are the real stakeholders. Are you find them over, over time. So you don't know really who are the we? I had a conversation with a customer today where there was a sentence like, we don't have any business people involved in this.

00:51:38:16 - 00:51:41:15
Stefan Avram
Yikes.

00:51:41:17 - 00:51:44:24
Daniel Kocot
It's just it's just backend.

00:51:44:27 - 00:52:01:27
Stefan Avram
One of my concerns there, the that I've kind of seen in the API spaces. And I want to know from your experience if you've also seen this, they know it's a problem. They want to fix it, but they either don't have the time or it's not the very bottom of their To-Do list. Or quite frankly, we've seen it.

00:52:01:27 - 00:52:06:00
Stefan Avram
They just don't care. It doesnt generate business revenue, but they just don't care.

00:52:06:02 - 00:52:13:17
Daniel Kocot
Yeah, and the interesting fact is there is no tool to solve this.

00:52:13:19 - 00:52:41:03
Daniel Kocot
Yeah. No tool yet. Yeah. Maybe maybe maybe AI or something related to that has then the the opportunity to solve this by bringing all the informations together and just say, okay, these are the things we need because the business side requested this, this, this, this, this, and then makes it clear for the engineers what to do. Then maybe this will happen somewhere in the future.

00:52:41:03 - 00:52:48:28
Daniel Kocot
But in the end it's, it's, it's the old problem of building software solutions in companies.

00:52:48:28 - 00:52:51:10
Jens Neuse
It's it's requirements engineering. Yeah.

00:52:51:10 - 00:52:54:11
Daniel Kocot
It's okay. Yeah, yeah.

00:52:54:13 - 00:52:59:05
Stefan Avram
Jens you're seeing it. Yeah.

00:52:59:07 - 00:53:29:07
Jens Neuse
No. You know, and this is something we've been thinking a lot about is it. You know, and and I think it's actually we're moving in the direction with this like LLMS can really help there because I think you need a map from people to requirements to capabilities, and you somehow need to wire this up and make it searchable and need to be able to say, you know, also like?

00:53:29:09 - 00:53:56:25
Jens Neuse
Well, one of the things we we see missing in, in a lot of companies is they have APIs, but they don't know why. Nobody knows why this exists because there's no link between my Rest API endpoints and the capabilities that I actually wanted to have, because nobody ever wrote it down. And, so you, you end up with, what people then call like API sprawl or whatever.

00:53:57:02 - 00:54:32:24
Jens Neuse
You have this large landscape of APIs, and nobody knows what it does and why it exists. And a lot of API's are undocumented. And like, if you're extremely lucky, you you find the company where they have put some services into backstage, but then it's not properly documented what what each service does. So yeah, you you have this whole mess and everybody's talking about, you know, I read this a while ago, if we have a service and we don't understand it anymore, why it exists and how it works, then we call it legacy.

00:54:32:27 - 00:54:46:04
Jens Neuse
And if you if you and this is something interesting someone said about vibe coding, if you vibe code a service and you don't know how it works and what it does, then it's actually legacy from the start.

00:54:46:04 - 00:54:49:18
Stefan Avram
legacy.

00:54:49:20 - 00:55:08:16
Jens Neuse
Which is the segue into, into the last topic, we can, we can cover because we're, we're almost at the hour and we want to respect your time, but, with your experience, from your perspective, what's what's changing with AI?

00:55:08:19 - 00:55:35:15
Daniel Kocot
May maybe this this. Yeah. I'm not not what people expect that it helps us to build better APIs because this is a long term process, because the LMMs to learn from good APIs that are in an organization. But maybe the AI can really underline the process you described, actually, to really to really solve, to solve the things that you have.

00:55:35:15 - 00:55:57:18
Daniel Kocot
This demand processes made more clear because it's more searchable and easy to to detect what people really want and not just be placed somewhere in a confluence where nobody really reads it. It's really it's really capable of okay, I can search for it. I can search for the department I'm in. What are the the the capabilities? They want to have this.

00:55:57:18 - 00:56:29:01
Daniel Kocot
You written in human natural language and really clear. Okay. Then you need maybe somebody or the AI to make clear what this capability really means in technology or not, or it's really something it will be a helper. So it will be a helper to, to to really build or establish a good API culture in, in, in the organization environment.

00:56:29:01 - 00:56:49:16
Daniel Kocot
This is what, what I, what I see there. But it's for me it's, it's still in the beginning. And, and just looking at this MCP right now and this hype around this, it's not really reflecting what, what what is what is actually it. Because people are still suffering on the data. Theyre still suffering on the APIs they already have.

00:56:49:16 - 00:57:33:27
Daniel Kocot
So maybe they have a sprawl. So why should they then have an MCP to, to make then, 1000 APIs available by one call or something? I don't know, but in the end it's really about bringing bringing things together. And maybe underlying the development process of APIs to whatever style they are, because this is also something, something mostly important to to really and maybe, maybe be a helper of, deciding what is the best style for this, what what is meant as a capability because the LLM has learned and we don't have to reflect on people who are not with us in the company anymore.

00:57:34:01 - 00:57:40:16
Daniel Kocot
We can really reflect on what what is what is there. For a long time, actually.

00:57:40:18 - 00:58:09:08
Jens Neuse
Well, one workflow I really like about tools like Claude Code, for example, is planning mode. And and I can definitely think of in the, in the broader scope of, of thinking about capabilities and all this kind of stuff. I think, LLMS can be an excellent copilot in helping people be really crisp in what they need, and it can help you with, with prompting and summarizing.

00:58:09:08 - 00:58:32:04
Jens Neuse
And hey, is this really what you want? And it can give you like a playbook to come to good requirements. And then then it can help people summarize requirements. You can have like, like a, like a vector search where you can search across all requirements and find similar requirements. And then you can you can see, oh, someone wants to build something.

00:58:32:04 - 00:58:42:05
Jens Neuse
But actually last year someone else wanted to have a similar capability. Maybe we can bring the people to the same table. Asked what they are trying to do.

00:58:42:08 - 00:59:04:28
Daniel Kocot
Yeah, this this this, this is this is really the things to to to really make, make it worth to use AI and not just for the purpose again of technology or somebody told you or you saw something. It's really about, okay, this is this is bringing value because as you mentioned, I can really search and see. Oh, somebody else had the idea, which is actually totally simple.

00:59:04:28 - 00:59:29:04
Daniel Kocot
To have an idea board or capability board to just say, but even this is what I see hard for people to understand that there are so many easy ways to really to really solve the problems we have. Because having an, having some kind of a board is just like having, a GitHub repository with some kind of issue tracker and just say, okay, I want to have this.

00:59:29:06 - 00:59:57:14
Daniel Kocot
And then somebody can step in and say, okay, somebody already requested, I want to have it too. So it's sometimes so simple, but it's not done or adopted for process in, in in building these things. Because everything that we do relies on integration in the end. And for me it sometimes it sometimes looks like that there's a split between integration and API.

00:59:57:17 - 01:00:18:13
Daniel Kocot
So API is something mystique, quite popular, but in the end it delivers integration. But but people always don't use this term because it's not so fancy, so shiny in the in that place. So this is what what I see actually there.

01:00:18:16 - 01:00:19:18
Stefan Avram
Jens.

01:00:19:20 - 01:00:21:19
Jens Neuse
Again okay. Last question.

01:00:21:21 - 01:00:39:00
Stefan Avram
I was going to say one more before David's question. Daniel, what's the craziest thing or craziest thing you've heard when you went in to talk with the customer, whether it's like, oh, we don't do this or that or whatever, but like, what's, a story that stays at the top of your head like, wow, this company is crazy.

01:00:39:02 - 01:00:40:19
Stefan Avram
Do you have one like that?

01:00:40:22 - 01:00:51:22
Daniel Kocot
Yeah, I have one like that. There was an API built with R, I don't I don't say anymore.

01:00:51:24 - 01:00:56:13
Stefan Avram
Like, like, as in, I feel like I used R, in college. Just kind of like. Yeah.

01:00:56:17 - 01:01:04:10
Daniel Kocot
Use it for statistics and. Yeah. Yeah. And there, there are some, there are some libraries where you can build APIs on.

01:01:04:13 - 01:01:10:07
Stefan Avram
And this was like a big company. Like legitimate company. Yeah. Yeah, yeah. Okay. Pretty good.

01:01:10:09 - 01:01:18:05
Daniel Kocot
And, and the last thing is this it's the most used API there. Okay.

01:01:18:08 - 01:01:20:03
Jens Neuse
So it seems to be valuable.

01:01:20:05 - 01:01:22:10
Stefan Avram
Yeah.

01:01:22:13 - 01:01:23:25
Stefan Avram
But I like but.

01:01:23:28 - 01:01:30:00
Daniel Kocot
It's crazy from the perspective of. So you can use every framework to build APIs.

01:01:30:02 - 01:01:31:25
Stefan Avram
Yeah.

01:01:31:27 - 01:02:04:01
Jens Neuse
But by the way you mentioned one, one thing like this, this whole, focus on technology. And I think and you mentioned the, the bank at the conference and how other people tried to copy that. I think this is unfortunately one of the big reasons why why the, why the GraphQL ecosystem got such a big hit? Because I think a lot of people applied GraphQL when they didn't need it.

01:02:04:04 - 01:02:27:19
Jens Neuse
And, they later on figured out it's it's not solving my problem. And, and a lot of people, I think it's kind of unfair. A lot of people are, are upset with GraphQL. I think they they never really understood it or they, they didn't need it or, and, there are very good use cases for, for graphql.

01:02:27:20 - 01:02:35:16
Jens Neuse
It's a great technology. But I think in the in the early days it was completely overused.

01:02:35:19 - 01:02:40:10
Daniel Kocot
Yeah. It was, it was there, it was like, as always it was like a hype.

01:02:40:13 - 01:02:42:16
Stefan Avram
Yeah. It's the same with it.

01:02:42:21 - 01:03:12:28
Daniel Kocot
It's the same with rest. There's still this just it's just I wouldn't say hype phase because it's so easy to build Rest APIs full stop. And, when you have a hype, it's the same with with with these event based stuff. There was there was a really big hype. There's still a hype because everybody wants to be event driven, still, even if they don't know what it really means in the end to be event driven or whatever impacts you have there.

01:03:12:28 - 01:03:31:11
Daniel Kocot
So there's always this this relation to technology, but it's not how do I solve the challenges, the capabilities of the business or of my business to really bring value to my company?

01:03:31:14 - 01:03:34:26
Jens Neuse
It's still this, you know, these days it's MCP.

01:03:34:28 - 01:03:58:06
Daniel Kocot
Yeah, it's it's the next the next wave. Actually we don't know. It will be a to a or something or another crazy framework coming up. And being the solver of every problem existing. So there's always and there's always this, this kind of cycle.

01:03:58:08 - 01:04:26:22
Jens Neuse
Yeah. That the the story behind MCP is so weird because if you look into it, some people build tools, IDEs to, to code. And they needed the way to bring in information into the context so they built a solution to attach context to tools. And then they were like, this is we could actually make it open source.

01:04:26:22 - 01:04:56:04
Jens Neuse
And we could we could allow other people to extend the context through, HTTP or RPC. And then they kind of wrote out the, the, the protocol and, and now suddenly and this is something I kind of feel like, you know, now, now that I went through this GraphQL hype, I now kind of see that everybody is now trying to use this MCP solution and figure out what kind of problems could be solved.

01:04:56:06 - 01:05:23:29
Jens Neuse
But nobody like in our customer base, it's very rarely that people are like, we really, really need MCP. It's more like some developers. They are like, MCP could be cool. But if you look from the business side, like the business people, nobody is really asking for for MCP, it's it's they they have different problems and yeah, yeah, it currently really feels like solution looking for problem.

01:05:24:01 - 01:05:31:29
Daniel Kocot
Yeah. It's always you need a solution to solve the problem. But you but you don't have a methodology to, to to really solve the problem that behind.

01:05:31:29 - 01:05:53:27
Jens Neuse
So I think in the end we will figure out like there will be some problems that MCP is amazing at solving. But I think we will we will first burn a couple of billions in VC funding for things that absolutely make no sense. And then at some point, like I think like LLMs in general, they have great applicability.

01:05:53:27 - 01:06:12:04
Jens Neuse
Like there are super cool use cases like summarizing and all kind of workflows and reading stuff and also helping and then writing like LLMs are cool. But yeah, for for MCP, I think we're, we're extremely hard. And in searching for problems.

01:06:12:06 - 01:06:17:11
Stefan Avram
That's where. And then then yeah I know we are a little bit over, but do you have time for one more question from the audience?

01:06:17:14 - 01:06:19:23
Daniel Kocot
One more question then I have to leave.

01:06:19:25 - 01:06:38:17
Stefan Avram
Okay. Last question. So this one comes from David. He's on our team. Interesting. He never says the word real talk, but let's let's read the question anyways. Daniel. Real talk. Can you see in the next six months or year, a booming business for consultancies, fixing the mess that AI and Vibe Coding are creating today? It's a great question.

01:06:38:17 - 01:06:42:09
Stefan Avram
Real talk.

01:06:42:11 - 01:06:45:16
Daniel Kocot
Short answer no.

01:06:45:19 - 01:06:54:13
Stefan Avram
Interesting. If you're able to expand and then we'll let you go. If not we can save it for another episode another time.

01:06:54:15 - 01:07:34:10
Daniel Kocot
Because, because the, the boom not ended. So we, we we are still somehow in this business acquirement of using the whole thing. And fun fact it brings value somehow value to the people. So it's really, really something strange because people will not see that there is a problem because they even solved another problem. Not so far. The bad quality of data they already have as a company.

01:07:34:12 - 01:08:06:19
Daniel Kocot
And if they don't see this by using technologies that do stuff with things available, I don't. I don't, I don't see, I don't see, I don't see it because most people are too prominent with it to to really hype, hype to things further. And there there will be some kind of crash maybe next year or the year after when, when initiatives went totally wrong.

01:08:06:21 - 01:08:20:17
Daniel Kocot
But for now, everything is fine. Everybody wants to build agents. Everybody wants to build, their software with vibe coding. And, no big things happened so far.

01:08:20:20 - 01:08:44:27
Jens Neuse
But, you know, I think that's a that's a good reason why it is like that. You can increase your data quality or your API strategy, and that will to some degree improve the business. But what what leaders are currently looking at is, can we quickly spend some money on AI and get fast returns? That is what everybody is now trying to do.

01:08:44:27 - 01:09:11:13
Jens Neuse
And one interesting observation. We see this in our company, but also in research, this whole shebang around AI coding and LLM coding, we kind of figured out and I think more and more people realize as a developer you can use AI to write code. It doesn't necessarily make you faster. It doesn't necessarily increase the quality. It, it, it gives you.

01:09:11:13 - 01:09:43:02
Jens Neuse
It allows you to be a little bit more lazy. But the results are kind of negligible. So you can use cursor. You can also not use it. Vibe coding doesn't work. We have figured this out and what we see in our team. Like for example, David on On the Stream, we did an experiment. We wanted to migrate some very complex code and he tried to use AI, and then he said, yeah, I had to review every little thing because I cannot trust this.

01:09:43:02 - 01:10:01:08
Jens Neuse
So in the end we were asking like, was it really worth it? And he was like, actually, we we could use it. We could also not use it. It's like it's not making us 50% faster. Like the AI boom is not there.

01:10:01:10 - 01:10:28:11
Daniel Kocot
It's in the end it's it's what what what what I always say is you can use it if you are an expert in this, what you want to achieve with AI. So if you know all the things around it and then you can see how this is, this is, this is really, really moving up because there's a lot of trick tricks technology for me involved by using something like ChatGPT and all the other things around.

01:10:28:11 - 01:11:06:17
Daniel Kocot
Because when you ask to to draw a picture with specific libraries and then you say, okay, by using the library, create me and and PNG or, or Jpeg or whatever, it always uses Python in the background. Because it knows Python best. And and this is, this is really something just to see there. So they, they, they actually these these these things don't or the AI doesn't really know all the programing languages.

01:11:06:17 - 01:11:29:25
Daniel Kocot
It's sometimes really thinking about stuff, finding somewhere and just putting the things together. Normally it doesn't, doesn't really work good or not as expected or as as as David said I have to review it. Yeah, I have to review everything I do with this. And even if I want to pimp it up on so on and so on, it will work at some point.

01:11:29:25 - 01:11:52:27
Daniel Kocot
But at another point it will just not work. So it's in the end, it's really something what I say or I see in the API space, nobody is really doing important business stuff with it. So writing open APIs in a in a regulated business context or something like that, when this will happen, we will find out how it really works.

01:11:52:27 - 01:12:04:02
Daniel Kocot
And maybe then there is, the time to fix the mess that happens actually, and say, okay, this is not working, so we should end it. You.

01:12:04:05 - 01:12:18:15
Jens Neuse
Okay, Daniel, that was, a very insightful session today. Thank you for for joining us. Stefan, you know what the good thing is?

01:12:18:18 - 01:12:33:29
Stefan Avram
The good thing is we're back next week. So, guys, thanks so much for joining us today. Daniel. It was a pleasure. We will let you go, but we'll be sending up snippets of this on LinkedIn. Feel free to reshare because this really was an insightful episode and we'll be back next week. Thanks, Daniel. Thank you, thank you.

01:12:33:29 - 01:12:35:00
Daniel Kocot
Bye.

01:12:35:03 - 01:12:36:29
Jens Neuse
Brendan. You can now click the button.