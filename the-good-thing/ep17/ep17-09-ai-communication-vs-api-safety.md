---
title: AI Communication vs API Safety
slug: ep17-09-ai-communication-vs-api-safety
series: The Good Thing
episode: 17
chunk: 9
participants:
- Stefan
- Jens
segment: Scaling AI collaboration and API contract safety
timecode: 00:39:24 – 00:45:01
start_time: 00:39:24
end_time: 00:45:01
speakers:
- Stefan
- Jens
topics:
- Communication as biggest challenge in 1000-dev organizations
- Scalable software building approaches
- Thousands of AI agents collaboration problem
- Layers of agents and control mechanisms
- AI context definition and safety
- API contracts for AI interaction safety
tags:
- ai-collaboration
- organizational-scaling
- communication-challenges
- agent-control
- api-safety
- context-definition
topic_tags:
- ai-collaboration
- organizational-scaling
- communication-challenges
- agent-control
- api-safety
- context-definition
entities:
- Cursor
mentions:
- thousand developer organizations
- scalable software building
- thousands of collaborating agents
- agent controlling agent hierarchy
- cursor instance doing weird tests
- layers of agents problem
- well-defined context requirements
- API contracts for safety
summary: Jens identifies communication as the biggest challenge in large developer
  organizations and questions how thousands of AI agents could meaningfully collaborate.
  He raises concerns about control mechanisms when agents control other agents, using
  Cursor's unpredictable behavior as an example of current AI limitations. He argues
  that while AI is useful for well-defined contexts, defining that context remains
  a human responsibility, suggesting API contracts as a safety mechanism for AI interactions.
---

00:39:24:13 - 00:39:38:17
Jens
Well, what is the biggest problem like from an software engineering perspective from your. Well,
what do you think is the is the hardest problem if you have an org with a thousand devs? What
is what is the number one challenge?
00:39:38:20 - 00:39:39:23
Stefan
Communication.
00:39:39:26 - 00:40:39:26
Jens
Yes. So it's all about how these people communicate, how they make decisions together, how
they how they shape ideas, how they shape projects, how they prioritize things and, and
ultimately how they make this whole organization scalable in a sense, not scalable from like
building scalable software, but, finding out a scalable approach of building software. So enabling
more, more value and, what I really don't see is like there I have never heard any, any AI
company whatever talking about, how how will how will we have thousands of agents
collaborate in a way that it's any meaningful, that it's that it's helping the, the company to
achieve goals.
00:40:39:26 - 00:41:05:15
Jens
And when I have one single cursor instance and it's doing weird stuff with my tests, what
happens if I have, I don't know, a thousand ones and then layers and layers of of agents and
whatnot. And who controls that They do the right thing. Will this the other agents? Okay. Now
you have an agent controlling an agent, but who controls the agent who controls agents.
00:41:05:15 - 00:41:46:11
Jens
And I don't know, ultimately, yeah, maybe maybe some smart AI people will now laugh at me
and they will. They will be like, oh, Jens is. It's naive, but, I currently live in this naive world
where where I think, AI it's a pretty cool tool to to help us, generate code much faster, for, for for
a context that we have very, very well defined but defining this context, I still think at this
moment it is it is our task as developers to to figure out the.
00:41:46:14 - 00:42:05:06
Stefan
Well said, And I think that like, it's one of our key thesises and you'll see it on a landing page,
everybody says it, but I really like the word that they say is that there is no AI with APIs. And I
think that's super important because how are these, you know, MCPs or these agents, how are
they talking to each other?
00:42:05:06 - 00:42:20:18
Stefan
Like, how are they making sure that everything is working correctly and how are they
communicating across people? Like, for me, the best example that I've heard, we're writing a
blog post on this is when you go to a restaurant, you look at the menu. That's the front end. The
back end is the kitchen that has the food, the data.
00:42:20:21 - 00:42:40:18
Stefan
And then when you want to get food, you talk to the waiter, you tell him what you want and
somehow the food appears there. That's that communication layer. And it comes from
communicating with him. And that's essentially what APIs are. It's just a communication between
the front and the backend. But with AI, there is no AI without APIs is what Kong says, and I like
it.
00:42:40:20 - 00:43:10:09
Stefan
But where do APIs fit into this equation of agents and MCP? Is there going to need to be APIs?
Can't they just talk to each other as if we just talk to each other? Or is that talking still the API, if
you know what I mean. And I think this is really interesting question for you, because you have a
thesis of where the world is going to be with APIs and AI, and I like it and I fundamentally agree
with it, but where do APIs fit into this AI bubble and wave?
00:43:10:11 - 00:43:40:21
Jens
So let's say. Let's say you have an app and it can send money to someone else. So you want to
send money to Sofia. Okay. You entered the amount a hundred bucks. You intend to send 100
bucks to Sofia, your wife. And what would you do if. If it would send a thousand bucks?
00:43:40:24 - 00:43:57:15
Stefan
Oh, it's to my wife. Luckily. So. It's still to my bank account, so. Yeah. So I wouldn't be too upset.
But let's say it was to. I send it to the wrong Sofia. I sent it to. Okay. Wrong. A friend I send it to a
friend. I'd be a little bit upset. I'd be like, shit. Yeah, okay.
00:43:57:15 - 00:43:59:19
Stefan
Just lost my thousand bucks. So.
00:43:59:21 - 00:44:03:11
Jens
So you want that? Your app is very accurate.
00:44:03:13 - 00:44:04:26
Stefan
Yes. Of course.
00:44:04:28 - 00:44:36:08
Jens
Okay. And if we build the contract between your app and, and, the, the back end of the bank,
and then we have inter banking contracts, we have things like open banking, which is open API
for banking. And all these contracts like, like your app talks to the server, the server talks to
another service, the server talks to another server, some other server talks to a database, etc.,
etc..
00:44:36:10 - 00:45:01:05
Jens
If we have strict contracts like where we say, okay, here's here's our open API spec, here's the
JSON schema, you have to send money in a specific format. And if you're done doing it, we give
you a 400 bad request and that's it. So play by the rules. Otherwise it's going to be a foul. All
right. So that is what we're doing today.