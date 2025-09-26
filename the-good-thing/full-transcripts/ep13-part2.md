00:32:23:10 - 00:32:56:17
type: podcast-chunk
Jens
I mean, I'm now, a few more than I don't know how many years, ten, 12, whatever. I guess doing
doing software and, I learned a, I learned coding in the pre vibe coding era. Yeah, it's I don't
know how you did it thing. Yeah. And we, we had to learn the, the, the fundamentals. And you
know, the funny thing is just, just today I had maybe maybe he's listening, but I, I for me this is
funny.
00:32:56:24 - 00:33:06:23
Jens
clone something.
So one of my colleagues, he said like, hey, I'm currently in the hospital and I want to I want to
00:33:07:10 - 00:33:11:04
Stefan
Can. Right. Because of GitHub. Oh, he can't clone it cause in the hospital.
00:33:11:04 - 00:33:27:10
Jens
Right. So he wants to clone the repo, and he was like, yeah, I get this timeout error. SSH is not
working. And you know, like so you're you're also like a vibe coder. So ssh it's not working.
What's the problem. What is the hospital doing then?
00:33:27:12 - 00:33:38:28
Stefan
I think they're blocking from GitHub because I know in hospitals you can't like bring down repos
for protection from the hospitals. Am I right there?
00:33:39:00 - 00:33:40:18
Jens
Kinda like they don't want to.
00:33:40:18 - 00:33:44:07
Stefan
They don't want you to bring down some malicious repo into. They won't in there.
00:33:44:12 - 00:33:47:20
Jens
What is what is port 22?
00:33:48:20 - 00:33:52:08
Stefan
I don't know if it's like a port like computer.
00:33:52:10 - 00:34:25:20
Jens
It's it's the SSH port. Okay, so the hospital is for whatever reason, they are they are just
allowing, like port 80, probably. Maybe not even 80, but 443. So, TLS and they obviously block
for 22 because I don't know, maybe it's, it's malicious or whatever. And yeah. So he cannot
clone repositories and because his git is using SSH.
00:34:25:21 - 00:34:30:17
Jens
So how could you how could you solve the problem.
00:34:30:19 - 00:34:33:22
Stefan
Can you use a different port.
00:34:33:25 - 00:35:09:24
Jens
That's. Yeah. So you could use git over http. For example https them and that should be port
443. That should work. Or you could you could create a proxy proxy. SSH. Over, over. Over TLS
that that could also be a possibility. But yeah, it's it's just, you know, and these are the
fundamental, like a vibe coder would be like, oh, I don't know, like my internet working or
whatever, but yeah, it's it's,
00:35:09:27 - 00:35:16:18
Stefan
No, it's true. Like, you know, the ports like that in a vibe coder wouldnt be able to know exactly
what to do. That's interesting.
00:35:16:20 - 00:35:39:10
Jens
But, you know, you're in a hospital and you get the timeout when doing ssh. It it's kind of very
obvious that it must be something with, with ports or a firewall or something. And now you need
to see, okay, which, which ports are open and how can I can I tell my client to use another port
or whatever.
00:35:39:10 - 00:35:41:15
Jens
Like how how can. Yeah.
00:35:41:18 - 00:35:47:21
Stefan
different port?
It's kind of funny though. I wonder, did he manage to fix it though once you told them to use a
00:35:47:23 - 00:35:53:06
Jens
I don't know, he he he said he try some stuff.
00:35:53:08 - 00:36:09:05
Stefan
no. But you got a good point there and then I mean yeah we're opening it up into a huge space
like the S in MCP stands for security. I see it's going to get it's going to get interesting these next
couple months these next couple of years. I'm excited for that. And then let's transition to the
next topic though.
00:36:09:05 - 00:36:14:05
Stefan
behind.
So this one we kind of wanted to show a demo, which I really like one sec. There's someone
00:36:14:05 - 00:36:17:14
Jens
Me.
00:36:17:16 - 00:36:26:02
Stefan
Sofia just snuck in to grab something and I didn't hear until she was like literally right behind me,
it scared the hell out of me. I was like, well.
00:36:26:04 - 00:36:30:12
Jens
But your your your, virtual background, it it covered it well.
00:36:30:14 - 00:36:35:21
Stefan
Oh, okay. Cool. Yeah. I was literally like. Like I could have touched her. It was so weird.
00:36:35:27 - 00:36:37:18
Jens
We saw. We saw nothing.
00:36:37:21 - 00:36:54:12
Stefan
Okay, cool, cool, cool. But, All right, let's shift into the next topic. I want to talk because we're at
the halfway mark. Let's show off what we were talking about today with MCP and with Cosmo,
and let's just kind of go through it, and we can just kind of explain it to me. You can explain to
me, we can explain it to the audience, and we'll go right into it.
00:36:54:14 - 00:36:56:22
Stefan
Let me know if you want me to share the screen.
Yeah, you can. By the way, today I have to to cut at, at the hour. So we only have 15 minutes
00:36:56:24 - 00:37:05:12
Jens
left.
00:37:05:14 - 00:37:11:12
Stefan
Oh my God. All right. Sorry, guys. It was my fault I started late. It doesn't matter, though. All
right, quick speed run. Let's go. Cosmo.
00:37:11:12 - 00:37:24:05
Jens
Excuse me. I kept prompting you like, hey, we need to start. Okay, let me get this as far as I can
because my screen is left. Okay. You can see him, right?
00:37:24:08 - 00:37:26:24
Stefan
Wait. These docs are already live.
00:37:26:27 - 00:37:32:26
Jens
Yeah, yeah. What? Okay, go. Good. What do you mean?
00:37:32:29 - 00:37:39:16
Stefan
sick.
I thought we were just. I didn't even know that these were live on the website already. This is
00:37:39:18 - 00:37:41:27
Jens
Well, what do you think we're doing?
00:37:42:00 - 00:37:50:24
Stefan
No, I just saw it this morning, and then I find out that the docs, like, 30 minutes later, are already
up on the website. I mean, just shows you how fast we ship it. Go ahead. We got 15 minutes.
00:37:50:27 - 00:38:14:00
Jens
Okay, so let's assume we have cursor installed. I first want to go a little bit through the through
the docs and then we can we can talk a bit about the the implementation details. But one thing I
want to to say about MCP is so they're there there was a debate, a while ago on, on LinkedIn,
on, on.
00:38:14:27 - 00:38:43:23
Jens
Should you just you build an MCP server and wrap your existing APIs, or should you augment
your APIs and build something on top? And so what I tried to do is I wasn't like, okay, let's let's
slap MCP on top of Cosmo. That was not my intention. My intention was more like, let let's let's
look at some workflows and let's try to mcp them.
00:38:44:00 - 00:39:05:26
Jens
Let's try to really enhance them with MCP. And I give you like, okay, this is let's get started. Like
super simple. So setting the context doesn't matter. Schema exploration. This is like a super
simple, case. But here, you see. Okay, we have a prompt. We say we have our super graph. We
have our namespace. Oh.
00:39:05:26 - 00:39:29:02
Jens
By the way, on setting it up. So just for completeness, you, you create this thing and in your
cursor you need an API key. You get this from our studio and then you, you set this up like npx,
wgc, mcp and that's it. That that's all you need to do for for setting it up. Okay. First prompt
schema exploration.
00:39:29:04 - 00:39:33:12
Jens
Very simple. One. So let me go to cursor. Do you see that.
00:39:33:15 - 00:39:38:17
Stefan
Yeah it's here okay. And what repo do you have up. You just have the, the Cosmo mono repo.
00:39:39:04 - 00:39:41:02
Jens
One second.
00:39:41:04 - 00:39:42:29
Stefan
You see it on the left here, Cosmo and then router.
00:39:42:29 - 00:39:58:15
Jens
Okay, cool. Yeah. Just need to close some stuff here. Okay, so we have our first prompt. So we
need to tell our tools what what a super graph to use, what namespace. And then show me the
core features of the super graph.
00:39:58:17 - 00:40:01:12
Stefan
And you do this in the config file, right.
00:40:01:15 - 00:40:31:05
Jens
Yeah. The the config file doesn't really matter at this point. It's more like yeah okay. So you see
MCP wants to call a tool. It wants to get my graph from default okay. We run it. You see here
schema is coming back and it wants to get the subgraphs okay. It wants to get the subgraphs as
well. And even the router config.
00:40:31:07 - 00:40:40:23
Stefan
This is so cool. It's like a what I see is like a human. Okay, let me grab the subgraphs, let me
grab more of the subgraphs. Let me grab the router. I want to understand everything. That's
sick.
00:40:40:25 - 00:41:28:02
Jens
Okay. So now you see the architecture. We have a family service availability mood hobbies the
entity model. So we have the employee type, and we have some features with authentication,
we can find employees products, teammates, mutations, subscriptions, advanced features, file
uploads. So it's a pretty comprehensive summary of what's our API can do. And this is all
coming from fetching the super graph, fetching the subgraphs and our, router configuration,
from the super graph.
00:41:28:02 - 00:41:42:07
Jens
It. And now we, we know everything about this thing. Maybe we can ask a follow up question.
For example. Show me the, schema of the, employee type.
00:41:42:09 - 00:41:52:07
Stefan
I have a question of could you ask it, can you visualize for like, visualize this for me? Like I
shows you a picture or a visualization of the of the architecture.
00:41:52:10 - 00:41:54:20
Jens
For or.
00:41:54:20 - 00:41:57:23
Stefan
Would we have to build that MCP component?
00:41:58:06 - 00:42:08:29
Jens
Good question. So here's our, our, employee type. Yeah. We now understand the schema. You
said visualize the architecture.
00:42:09:01 - 00:42:23:29
Stefan
Yeah. Like I want to see what the federated architecture looks like. So, like, if I'm a new
developer and we're using GraphQL and we have a super graph, I'd be like, hey, can you
visualize this for me? So I can see how each components work together?
00:42:24:01 - 00:42:25:27
Jens
I have no clue.
00:42:25:29 - 00:42:33:09
Stefan
Yeah, I was about to say for the audience and everybody watching, we haven't tried this before.
Okay, so you can't, but why can't you visual.
00:42:35:07 - 00:43:17:06
Jens
That's not too bad. So what do we have here? Graph TD client router, router subgraph, then
subgraphs. Oh, this is wait, this is a, a mermaid diagram, right? interesting. So we could take
this and put it into some mermaid drawing tool. And it could actually, this is interesting. You
know, you have family. It's a subgraph.
00:43:17:09 - 00:43:38:28
Jens
And it shows us that it has details and pets and, availability has this available. So it actually
shows us what is coming from where, which is it's pretty interesting. So it figured out all this
information and can, can present it. So yeah, very useful. But this was just the first prompt okay.
So yeah sorry.
00:43:38:28 - 00:43:39:24
Stefan
I'm getting excited.
00:43:39:24 - 00:43:54:14
Jens
Like like it's crazy okay. So here's here's another thing that's so I call it the dream query
workflow. And I think this is for me this is really cool thing.
00:43:54:16 - 00:43:59:11
Stefan
So in the dream query that comes from, Yelp, right.
00:43:59:13 - 00:44:03:17
Jens
Yes. So I, I borrowed it from Yelp.
00:44:03:19 - 00:44:10:18
Stefan
to give this back?
By the way. You know, if you borrow something, you have to give it back. So how are you going
00:44:10:20 - 00:44:14:24
Jens
I give them credit. Okay. Here we go.
00:44:14:26 - 00:44:15:07
Stefan
Okay.
00:44:15:07 - 00:44:45:27
Jens
So let's say, we have here we have this employees. This will always fail on the first run because
we have a weird serverless architecture okay. So we have ID details. Forename, surname,
format run. Okay. So you see, we have this. So now I give you a simple example. So let's put
age here, to get the age of everybody.
00:44:45:29 - 00:44:50:06
Jens
Yeah. So it's not working. Why is it not working.
00:44:50:08 - 00:44:51:27
Stefan
It's not in the schema.
00:44:51:29 - 00:44:59:23
Jens
It's not in the schema, okay. So we do this. We copy this, we go. That's the.
00:44:59:23 - 00:45:02:28
Stefan
Dream. That's the dream. Query you want is in front end.
00:45:03:00 - 00:45:05:04
Jens
This is my dream query. Yeah.
00:45:05:07 - 00:45:11:15
Stefan
As a front end developer, that's the information I want to go and get and display to the client
okay okay.
00:45:11:17 - 00:45:39:16
Jens
So we put our dream query, and we say super graph blah blah blah. So this and then we say.
Start the dream query work flow for the following query.
00:45:39:18 - 00:45:46:10
Jens
No way.
00:45:46:13 - 00:45:59:22
Jens
Do you see how hard I'm working? I'm I'm I'm I'm I'm I'm an architect. Like, I'm very busy stefan.
I'm I'm fetching the super graph.
00:45:59:24 - 00:46:05:24
Stefan
This feels like you ever see, Iron Man where he's like, come on, come on, Jarvis, wake up.
Wake up of the Jarvis.
00:46:05:26 - 00:46:15:00
Jens
Yeah, it's literally what it is. Okay, so, we we verify.
00:46:15:02 - 00:46:18:16
Stefan
That's another MCP tool, so you verify it against the in-memory schema. Okay.
Yeah, I, I you see I, I this workflow, it tells AI, it gives AI instructions on how to follow this,
00:46:18:16 - 00:46:30:27
Jens
through.
00:46:30:29 - 00:46:52:06
Stefan
And there's a very cool tool by the way. And what I'm envisioning is so we've had to build these
MCP tools, but in the next iteration of Cosmo, in the next iteration, everything we build, we'll just
have a marketplace of, hey, take this down, do that. Hey, do this. Just basically all these MCP
tools that you could grab and use for yourself as well as create your own.
00:46:52:12 - 00:46:56:28
Stefan
It's pretty amazing.
00:46:57:00 - 00:47:03:12
Stefan
Okay, so now you're fetching the subgraphs.
00:47:03:15 - 00:47:16:15
Stefan
You know that. It's so cool though. And it's also learning for the person to see how it would like
go through and solve the problem. It's very cool.
00:47:16:17 - 00:47:24:19
Stefan
Okay, so now it's calling the schema change proposal workflow. Very cool. And I know what
that's going to fit into eventually, but I'm not going to say it on the podcast.
00:47:24:21 - 00:47:27:19
Jens
00:47:27:21 - 00:47:37:09
Stefan
Very cool, very cool. Okay. Let's prepare the schema change. This is crazy.
00:47:37:12 - 00:48:08:19
Jens
You know? And here's the thing. Like the the cool thing is not like I haven't invented the llm, but
what I just did here in this call, for example. So we made a proposal to prompting. And now what
the alarm did is we're actually making a verification. That's the change we want to do. It's
actually compatible. And I can show you something.
00:48:09:03 - 00:48:33:16
Jens
So it wants to, verify this again. Okay. And, needs to do that. Okay. Remote schema. That won't
work. But I show you something. If we go to our studio, you see here, we want it to do h, right?
We wanted to add this.
00:48:33:18 - 00:48:36:29
Jens
Look at what it did.
00:48:37:01 - 00:48:40:27
Stefan
Yeah. It did what? That's insane. Oh, yeah. Oh, my God.
00:48:40:27 - 00:49:01:00
Jens
AI, the llm added the field h to the employee type in the family service I think is it family service?
Here. Family. Yes. And now we can see the schema. The schema is here.
00:49:01:00 - 00:49:03:15
Stefan
Employee ID is age.
00:49:03:18 - 00:49:42:16
Jens
It has details and age. So just by prompting, we have you did a proposal to add the age to the
employee type and I don't know what this is. I think it's very powerful because we just went from
from a query, from our dream query to how we could turn that into and, you know, like, this is not
even, like, don't think too much about this, like advertising, in terms of, hey, Cosmo is cool, blah,
blah, blah.
00:49:42:20 - 00:50:04:01
Jens
It's not about that's not why I'm showing it. I'm showing it more like, think about your existing
tools. And if you expose the right things to MCP, this is what is possible. This is where you can
where you can go. And then I can show you another example where you can see.
00:50:04:02 - 00:50:07:22
Stefan
If you query now for age, it'll pop up right on the playground.
00:50:07:23 - 00:50:10:19
Jens
No, no, we haven't changed the schema okay.
00:50:10:22 - 00:50:12:15
Stefan
But we just made a proposal on a change.
00:50:12:15 - 00:50:16:28
Jens
Yeah, exactly. Yeah, we just checked, how could it be possible, etc..
00:50:17:01 - 00:50:35:07
Stefan
Insane. And what's cool though, I'm a front end developer and I do the dream query workflow. In
the old days I'd have to go and tell my backend developers, hey, can we add this field to this
type? So that way that I can query from the front end. Now they can just do it with MCP and it
gets checked with Cosmo and then they can approve it, basically providing governance on top.
00:50:35:12 - 00:50:36:25
Stefan
It's sick.
00:50:36:27 - 00:51:10:01
Jens
But and here's the thing. And this is I think it's so important for everybody to understand like the
impact of of MCP. But, here are all the tools we have available list subgraphs, get subgraphs,
introspect subgraph, subgraph, verify schema changes so that the AI can iterate. And we can
we can run these checks. Then for the super graph list Supergraph fetch super graph fetch
super graph router config fetch super graph subgraphs, and then for schema evolution.
00:51:10:21 - 00:51:38:05
Jens
The schema change proposal workflow. Actually, it's not really doing anything. All it does is it. It
prints out a playbook for the AI. What to do and which tools to use to go to a proposal. And then
the stream query, workflow which is essentially also just text that tells the LLM what to do. And
then very powerful verify query against remote schema, verify query against in-memory
schema.
00:51:38:12 - 00:51:59:23
Jens
This is kind of like what kicks the workflow off. Because in the beginning you have a query. It's
not working. So you verify that. And this is what I think people need to understand with MCP,
you need to build workflows where AI can iterate so it can start with something, it can try
something and then you tell it, okay, try a schema design.
00:51:59:23 - 00:52:19:11
Jens
But run this check workflow to verify your work, and then it runs the check workflow to check. It
will run our composition library behind the scenes and other checks, and it will tell you what is
wrong. And then you can iterate based on this information. And yeah, this makes this workflow
happen. Change log. Another one.
00:52:19:11 - 00:52:45:18
Jens
And this is also something I wanted to show you. Verify router config and cosmos router config
reference. So this is essentially we have embedded the Json schema specification for our router
config into this tool. Yes. We also have documentation search but. By embedding the Json
schema, we can we can do a really cool thing. So I show you something.
00:52:45:18 - 00:53:02:17
Jens
So here is my config. You see very simple config okay. Yep. lets do something. So, yeah. Tell
me what you want to enable on your custom router because you're, you're not an expert. You
are, you are a good guinea pig.
00:53:02:20 - 00:53:09:08
Stefan
Yeah. This is not bad. So, like, maybe like OTEL. I want to, because that work.
00:53:09:10 - 00:53:28:21
Jens
Okay. So, hub me to enable OTEL metrics and tracing. In my COSMO router.
00:53:28:24 - 00:53:38:06
Stefan
And one step further. So if I wanted to pipe this information of otel metrics and tracing from the
Cosmo router to Data dog, could I also ask it? And it would tell me like how I would do that.
00:53:38:09 - 00:54:22:24
Jens
But I don't know. Depends on the model. Let's let's go step by step. So enable otel metrics and
tracing into the router. And then we say my config is this. And then we say oops new. Okay.
Config. Look into the Cosmo router reference and the docs to find information. And then we say
make sure to verify the correctness of the config.
00:54:22:26 - 00:54:51:12
Jens
So you see it's a little bit of prompting. But at the same time, I don't need to look into the docs
how to, how to enable OTEL. I just do this little bit of prompting and let's see, what do we get.
So first of all, it wants to look into the customer router config reference. So this loads the Json
schema of our config into the context.
00:54:51:13 - 00:54:51:27
Stefan
Searches the.
00:54:51:27 - 00:55:16:07
Jens
Docs. Now it searches also the docs to get some more info, and it seems like it already has an
idea of how to do it. So that's pretty good. So it adds telemetry here. I don't know if it's right. Like
I'm not an expert in this part, but it will verify that the configuration is correct.
00:55:16:09 - 00:55:20:21
Stefan
It does look right, doc, because when you see the tracing you see the sampling rate metrics.
00:55:20:21 - 00:55:30:09
Jens
Yeah it could be. It could be. So it wants to verify the router config.
00:55:30:11 - 00:56:01:13
Jens
Okay. It it seems right. And this is something you can trust. Because yeah because we have a
Json schema validation that ensures that everything here is correct. And this follows the Json
schema spec. So this is not validated by an LLM. It's validated by my code. And now one one
thing you mentioned is let's see where's our exporter.
00:56:01:19 - 00:56:23:06
Jens
Here. This is our exporter. Right. Okay. Yeah. Change this blah blah blah. Okay. Can you export
the OTEL, tracing to data dog? Dog?
00:56:23:08 - 00:56:31:10
Jens
It could be hallucinating. Now, I'm not sure how it will solve this problem.
00:56:33:26 - 00:56:39:13
Stefan
early.
By the way, after the example, you do have to jump. So we will have to cut the podcast a little
00:56:41:01 - 00:57:05:10
Jens
Okay. We can go very little for, over. It's fine. So what did it do. It edit data dog metadata. And
here it says data dog agent OTLP. So now it, this is cool. It wants to run verify, verify. Yeah. And
so now it's verified.
00:57:05:10 - 00:57:06:21
Stefan
That it's good.
00:57:06:23 - 00:57:40:28
Jens
It seems like this is okay. And it also give me some information about, headers like the API key
and this, so this this, might be very interesting, useful overall. I think this is pretty cool. Just to
give you like another example. So let's say you want to enable WebSocket support. Can you
also enable web socket support for subscriptions.
00:57:41:01 - 00:57:49:08
Stefan
So you just extending the route or just without even looking at the docs, you've added old style
instrumentation, you've added Datadog integration and now you're enabling WebSockets.
00:57:49:08 - 00:58:21:24
Jens
Yeah. You're like okay, I want to enable WebSockets apart. And because we already have so
certain information in, in the context, like our Json, Json schema for the, for the config. So I
know this is right, I think it's right. It looks very right. Like we support the absent protocol, we can
forward headers, authentication from initial payload.
00:58:21:27 - 00:58:46:18
Jens
This all looks good. It now wants to verify again. And, Yeah, it's valid. And sig. Well, it's I find so
powerful about this is you now no longer need to be an expert. Plus, you can you don't need to
go through the docs. You stay in your IDE and you're like, hey, this is my router config.
00:58:46:18 - 00:59:01:07
Jens
I want to do a certain thing. How can I do it? And then it searches through the docs and
everything. So yeah, that's, that's, what we have so far. With MCP, well done.
00:59:01:07 - 00:59:09:03
Stefan
And in the workflow. Two, you never left the IDE once. You just implemented three pieces of
functionality without ever leaving that.
00:59:09:05 - 00:59:30:00
Jens
But also, if you think about it, when we when we did, the, the, schema proposal, we could
actually see what our, the results of our work, we could see it in the studio and we can then
visualize the changes and, and everything. Like, you remember how I, we found, the, the
different everything where the field added.
00:59:30:02 - 01:00:07:20
Jens
But yeah, overall, I think one observation from my side is previously, you would always build
user interfaces to interact with the system, especially in the dev tools space. This has shifted.
We're now using things like, CLIs and terraforming and other methods of interacting with the
system. And I think MCP is is a new way where you now have your IDE and you just prompt
from your IDE and now it can it can do these powerful workflows.
01:00:07:20 - 01:00:47:27
Jens
And essentially your IDE is now like, like, Copilot, the workflow manager and, and you're, you're
more high level. And beyond that, what I find interesting is your IDE can now interact with
cosmos Schema Registry, and it can do the same thing with other tools. And I think it's it's now
the time for dev tool makers to, to think about okay, how can we how can we elevate the
workflows of our users, the developers, and how can we help them automate tasks and work
better?
01:00:47:27 - 01:00:52:00
Jens
And, I think this is a very interesting space.
01:00:52:02 - 01:00:58:21
Stefan
Incredible. We do have to cut it now. We actually hit the full hour begins. What's the good thing?
01:00:58:24 - 01:01:04:29
Jens
Where are we back next week? Because there is this thing called Easter.
01:01:05:02 - 01:01:08:01
Stefan
I'm off on Monday for Easter.
01:01:08:04 - 01:01:09:09
Jens
I,
01:01:09:11 - 01:01:12:08
Stefan
Yeah, that's what I celebrate at the 21st.
01:01:12:10 - 01:01:12:24
Jens
But we'll see.
01:01:13:01 - 01:01:21:25
Stefan
I'll post an update on LinkedIn if you're off on Friday. We'll then do another episode the week
after, but we'll keep you guys updated. The good thing is MCp is now available in one graph.
Cosmo.
01:01:21:27 - 01:01:24:03
Jens
Yes. Try it out. Give us feedback.
01:01:24:05 - 01:01:25:25
Stefan
Okay. Awesome. Thanks everybody.
01:01:25:25 - 01:01:29:08
Jens
See you. MCP.
01:01:29:08 - 01:01:31:01
Stefan
Jarvis. Jarvis, get to work.