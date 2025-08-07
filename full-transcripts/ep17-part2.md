00:30:57:28 - 00:31:43:24
Jens
And then I make a coffee or something and five, ten minutes later I get a well researched paper.
I can, I can review it, and I'm not even considering using that for my RFC. It's more like, okay,
now I have this in my brain, this this dump. I and I will sleep over it. And now I have some some
fresh ideas, and it's as if I had a conversation with a senior developer who read all our all these
seven documents, and they gave me some thoughts and now I can I'm one step further and if
you're not using these kind of tools, if you're not trying out how Cursor could help you.
00:31:43:24 - 00:32:15:19
Jens
And I'm not saying like, you know, LLMs generate tokens, okay? Like it's not intelligence. It's not
smart in any way. But, I think we as developers, we have to to reimagine our job because we're
not code writers. We are problem solvers. And for me, describing a prompt and working with
ChatGPT Deep Research to figure out how to solve a problem for me that is engineering.
00:32:15:21 - 00:32:50:12
Jens
So my job hasn't really hasn't really changed. It's it's just I'm now doing it at another level. And
I'm honest with you, in the beginning, it's kind of fun to write code and to see how it compiles
and runs. But after several years, I'm I'm still very interested in solving problems, but I'm I'm not
going crazy about typing words to make it like it's not so important for me to type every single
character, if you know what I mean.
00:32:50:14 - 00:33:11:00
Stefan
I think you're spot on, and I really like that example. And one of the things I'm noticing is like, do
you remember, like when Amazon was being built or just the internet and people were like, oh,
the internet's just a fad, and it's just something that's going to go away. And what I'm sometimes
hearing, which is crazy from people, is like, oh, AI this just bubble, it's going to burst.
00:33:11:00 - 00:33:30:27
Stefan
It's not really that useful or whatever. And the thing is, is, Shopify and now Duolingo and I'm
telling you, all these other public company CEOs are going to start doing the exact same thing,
which is the API or like the API mandate, but the AI mandate you have to incorporate or at least
be using AI into your tooling because it's what you said.
00:33:30:27 - 00:33:56:01
Stefan
It's just a tool, but it's an extremely powerful tool. And I do think it's a red flag as a technologist,
not to use AI, because as a technologist and a problem solver, your goal is to use the best and
most available tools at your disposal to solve that problem. And it's what you said. Like you
could have spent ten hours, 15 hours doing deep research, reading all those things and
everything, but instead you prompted it.
00:33:56:02 - 00:34:19:27
Stefan
You spent ten minutes describing exactly what you want. You press enter, and you went. While it
was compiling and building and getting all that information. You went and you made yourself a
coffee, and you might not be at step ten where you're finished, but you're at step five, and you
did that in ten minutes. And I think AI it's such a powerful tool for that, that when we hear in the
interviews like, oh, I used AI, it actually makes me happy because it's like, okay, you're using
tools at your disposal.
00:34:20:00 - 00:34:44:14
Stefan
And one example I'll draw back to is when I was doing my computer science degree. Every
exam was, open book and open computer, for this one teacher. And this teacher said, this is
what he said. He's like, I don't understand professors that don't let you use your computer or
your book. Because in the real world, when you're an engineer, you're going to have Google
open, you're going to have everything open.
00:34:44:14 - 00:34:58:01
Stefan
So that way you can solve all these problems and you should use every tool at your disposal.
So it doesn't make sense for me to create this environment in this classroom where that's not
the truth, but it's going to be hard problems, and you're going to have to be able to use the
internet. But I agree with you 100%.
00:34:58:06 - 00:35:20:09
Stefan
But you go back to the question like I'm also with you. I think AI is going to empower developers.
I not yet. I don't see a world where software is just being built by AI, but could it happen? Do you
think sometime in the future that, you know, just things are being built with AI and that there's no
like the way I envision is, have you ever seen Iron Man?
00:35:20:12 - 00:35:30:22
Stefan
What was the name of that AI villain that he created? There was a whole, Marvel Avengers on. I
think it was the second one.
00:35:30:25 - 00:35:35:05
Jens
So I know Jarvis, but that's not what you're looking for, right?
00:35:35:07 - 00:35:52:16
Stefan
No, Jarvis is the good one. Which which could be amazing. But there was the one that was so
smart and so sentinel that it ended up being bad, and it hated Tony Stark and I forgot the name
of it. I'll post that later in the comments. But with AI, do you ever see a future where, like, it's
kind of like its own thing?
00:35:52:16 - 00:36:03:10
Stefan
It solves problems and it works and it just does its own thing without humans like we've built it.
And at this point, sustainable.
00:36:03:12 - 00:36:34:29
Jens
So theres probably people smarter than me. And they have more knowledge about what's
what's going on in the AI market. But from, from my perspective, where we currently are at is,
we have agents like LLMS, we we prompt them something. We can give them tools, for
example through MCP. And then they can do like more complex tasks and yeah, the the results
are, are okay, like some tasks they are really good at.
00:36:35:02 - 00:37:03:03
Jens
And now there's like a new protocol, agent to agent. So instead of one agent doing like a super
complex task where it would get stuck, we divide the task into smaller pieces. And then agents
can, can essentially call tools. And these tools are other agents. So now we have agents
collaborating with agents on like more complex problems.
00:37:03:06 - 00:37:31:00
Jens
I, I don't think this is intelligence. It's still LLMS. It's still each agent does a task and it can predict
something, like then the next token and it can I mean, you can train these models further and
further. It will not be intelligence, but it will be extremely capable. We can automate it and it will
be able to do things that today humans do.
00:37:31:07 - 00:38:02:06
Jens
It will look very intelligent, although it's not. And so coming to your question Will, will that's AI will
replace how we do software or something. I'm not sure in the in the current form, I think what is
what is currently missing is like motivation, like, what you don't see in LLMs is they are not really
motivated in doing anything.
00:38:02:09 - 00:38:39:23
Jens
For example, when I did some, some experiments with, with cursor, like one, one workflow that
is quite, quite useful when you work with LLMs is you write a test and you ask cursor to make
the test go pass. And the stupid thing is that cursor doesn't really care if your code is right and it
it doesn't know exactly what, what does it mean that code is right, or it also doesn't care about
your business, or that this is scalable or whatever.
00:38:39:23 - 00:39:24:07
Jens
It's just make it. Yeah. You you asked to make the test pass. So what can happen quite likely is
that the implementation looks at the test and it's it somehow implements the logic in a way that,
yeah, it makes the test pass. But this is not good architecture or something. And now you have,
you have a bigger problem in, in large organizations I would say because imagine you have a
big org, you have a thousand developers, and they all work, work on, on several projects and
they all want to achieve something.
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
00:45:01:06 - 00:45:06:24
Jens
Now no you're saying can't we just replace all of this with LLMs and stuff.
00:45:06:27 - 00:45:11:18
Stefan
And I'm already seeing where you're going. I like it.
00:45:11:21 - 00:45:44:24
Jens
No. But so you're you're front end LLM. It it sends text to the next server and this text could
contain. Please send 100 bucks to Sofia. And then the server goes like, okay, I'm sending 100
bucks to, to Sofia, and maybe that's even right. And then you have like multiple other agents
and they all collaborate and they all have text as the, as the communication method.
00:45:44:26 - 00:46:11:04
Jens
And the problem with, with this kind of style of communication is if you just use raw text, the way
LLMs work is you, you tokenize the input. So you take the, the bytes or whatever you, you cut
them into smaller pieces. And then the, the LLM tries to make sense of what these pieces mean.
We call them tokens.
00:46:11:06 - 00:46:33:04
Jens
Okay. You have these tokens blah blah blah. And now in each server you have like different
models. They might have trained on different data and maybe they slightly send different
messages. And if we're super lucky, they all do like the right thing. But then there's also, for
example, a thing an LLMs we call it temperature.
00:46:33:07 - 00:46:58:03
Jens
So temperature it it can it can allow an alarm to have some sense of creativity, some sense of
randomness, so that it's not always writing like the same boring stuff. But if you ask an LLM to
write like a story, then you can increase the temperature and it will be more creative and
something. But this creativity, it can lead to to hallucinations.
00:46:58:03 - 00:47:20:09
Jens
So it it might somehow get something into the context window and then it starts, I don't know, it
starts rambling or whatever. So do we want to build a world that works like 60% of the time, or
what's it do?
00:47:20:10 - 00:47:23:03
Stefan
What's your quote though? Your quote? It works. What?
00:47:23:05 - 00:47:54:13
Jens
It works 60% of the time. All the time. No, I mean, you know, but, I think this, this world is, is not
gonna work. We need to have safeguards. And, you know, let's say you have, like, an MCP tool
and your kitchen gives you an MCP server and your waiter. It's an LLM. And so what what kind
of needs to happen is you speak to the LLM, you tell them, here's what I want to eat.
00:47:54:13 - 00:48:27:00
Jens
Like I want to have pizza, margarita and one beer. And then the LLM could, could, could come
back to you and say, Stefan, do you really intend to, to, eat pizza? Pizza margherita and one
beer. Is that what you wish? And then you say, yes, that's exactly what I want. So now the LLM.
It can now do an MCP call for you, and it will say, hey, I on your behalf, I would like to make an
MCP call to the to the kitchen to bring the order.
00:48:27:02 - 00:48:50:06
Jens
Here's what I would send. And now in cursor. If you look at this MCP tool you will actually see it
will construct a JSON message to called the MCP tool. Because MCP uses JSON schema to
define like what is the input? You can verify it. And now you see that we we gave the LLM like a
very strict contract.
00:48:50:06 - 00:49:19:01
Jens
How to talk to the MCP server. And so I think LLM is pretty cool if we put it on top of APIs. And if
you look between the lines like, what is MCP, then okay, it's it's APIs again. And at the core of
everything we need APIs. We need strict contracts. Otherwise, banking wouldn't work like
nothing would work.
00:49:19:04 - 00:49:37:05
Stefan
I think it's a fantastic example. I'm going to have Jacob clip that because I love the waiter
example when I'm talking to non-technical people. But when people ask why do you need? AI
with APIs? It's simply because of banking. Like you say, 100. It accidentally sends 100,000 and
it's because I hallucinated the temperature was a little bit up.
00:49:37:07 - 00:49:57:19
Stefan
And what APIs are providing to this world are the safeguards. And I think that's what the kong
founder means is there is no AI without APIs because APIs provide the safeguards around that.
I like that, I really like that. And we are all about to be at time. We are going to end the episode a
little bit early, because we do have a couple customer calls to get into.
00:49:57:21 - 00:50:19:22
Stefan
But Jens. So one last question before we jump into that is where do you see the future of AI?
But like with APIs? And how does Cosmo tie into that? Because we're working on some exciting
products, and I would love to just have a little bit of time of you talking about it, because I think
what we're building is really powerful because what AI allows is productivity.
00:50:19:24 - 00:50:37:11
Stefan
It doesn't really allow collaboration. What APIs provide is the safeguards. And what we're
building is at the intersection of collaboration, productivity, and safeguards. But can you talk a
little bit about where you see AI and Cosmo, and APIs?
00:50:37:14 - 00:51:10:08
Jens
So what we're currently seeing is big companies adopting tools like Cursor and changing the
way they create software. So it's now like senior architects or senior engineers who can who
now focus on developing the right prompts and everything. And they are migrating legacy
service into the world of federation at lightning speed. So it's, it's a very interesting observation.
00:51:10:08 - 00:51:35:13
Jens
It was never cheaper to migrate legacy and modernize it and consolidate services. And, one we
we just talked with, with one such company, we we joined one of their guild meetings. So they
have like a GraphQL guild that meets every Friday there. There's not just one guild in the
because.
00:51:35:15 - 00:51:37:26
Stefan
That's what I'm saying. It's a community. It's a community.
00:51:37:26 - 00:52:08:12
Jens
Yes. So they had this, this, this, guild meeting and one developer showed an example where
they have a single query. And this query loads data from like seven, seven, subgraphs. And
before they had this, this, implementation, the front end would have made like 20 calls to
various services to get the same data. Now it's one query.
00:52:08:12 - 00:52:42:24
Jens
So massive, massive improvement and so where I'm seeing the or where are we going like with,
with WunderGraph and what we're doing is so I think the trend we're seeing is companies adopt
AI and LLM and they will they will increase the speed and velocity and productivity of their
developers. If you do that, you need some sort of orchestration layer and operating system.
00:52:42:27 - 00:53:14:00
Jens
You need a place where the thousand developers can efficiently collaborate on what they are
now building at lightning speed. So now everybody's running faster. Everybody can build and
modernize is faster. They have more output, more velocity. But all of this energy, where is it
going if you don't have a means to organize it, to have people collaborate, work together?
00:53:14:03 - 00:53:49:27
Jens
And the foundation of, let's say you have a thousand devs and everybody builds services, what
is the foundation of of bringing it all together, making it re usable for everybody else? You need
to to encapsulate your business, your business logic as a service, expose it as a strict contract.
We now know why we just discussed this problem. So you need a strict contract and you need
to be able to share it with the rest of the company or even like partners, external, internal,
whatever.
00:53:50:00 - 00:54:21:06
Jens
So you need a platform where you can you can get like a bird's eye view on where are we
currently at with our APIs. Then you can search and leverage AI capabilities to immediately to
quickly understand what is the current API landscape doing. Can it solve my problem? So it's it's
a it's a question of exploration, of understanding APIs, of finding APIs that solve your problem.
00:54:21:09 - 00:54:53:27
Jens
So that is one big part. So bird's eye view exploration. And then if it it's not able to solve your
problem then you want to be able to find like the right stakeholders, the right people, the right
code owners. You want to collaborate with them on design. And once you have figured out the
good design for your new functionality, once you have figured out like the right place, where to
put it, you want to immediately go back to your your vibe coding whatever cursor.
00:54:54:00 - 00:55:25:22
Jens
Now you can code that publish, bring it into your API architecture. Sure, make it accessible to
everybody else, make it searchable, make it findable, reusable, etc. we don't want duplication in
this world. Yeah. And then we we essentially built like I would say like, like an operating system
or yeah, a principled approach so that you can really leverage the power of AI in terms of
development.
00:55:25:24 - 00:56:04:28
Jens
And we give you like the missing piece in terms of collaboration, so that it's not all just this. You
know, spinning the tires and creating lots of smoke, but actually bringing the horsepower on, on
the, on the road and enabling, this, this collaboration. And I think this is going to be like a, yeah,
a huge productivity boost if we can enable Big orgs to not just, yeah, build services fast, but
actually build services fast that also fit together in the bigger picture.
00:56:05:00 - 00:56:20:22
Stefan
I'm going to close with the comment that I was one of my favorite is from Henry Ford, where
they said if I would have asked them what they would have wanted, they would have said faster
horses. And if you ask companies what they want, they're saying, we want our developers to be
faster. They want this and that. What they actually want is the car, which is Cosmo.
00:56:20:22 - 00:56:38:17
Stefan
The collaboration and everything is we're modernizing everything. They don't actually know
that's what they want. What they see is I just want to move faster and break less, and I want to
modernize my stack. But they're just saying I want faster horses. I think that example is spot on.
I'm excited for what we're building, guys. Let us know below which format that you like better.
00:56:38:17 - 00:56:50:27
Stefan
If you like recorded videos, let us know. We prefer live because it's a little bit more fun for us, but
the good thing is, oh wait, I actually messed that up. Yeah, yeah. Jens what is the good thing?
00:56:50:29 - 00:56:55:23
Jens
The good thing is we're we're we're back live next week. Right?
00:56:55:25 - 00:57:02:07
Stefan
Yeah. We're back live next week. Thanks, guys. I'll see you guys on another episode of The
Good Thing. Thanks again Jens. Great episode.
00:57:02:09 - 00:57:02:19
Jens
See you.