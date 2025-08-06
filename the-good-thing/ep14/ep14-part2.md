00:30:25:05 - 00:30:52:09
Dustin
Rich metadata, which is really important. So I think this is also like a super, super power of
GraphQL. Because we have a unified, super graph schema, you can just add comments to the
type definitions to the root fields, and we will incorporate those information into the JSON
schema definition. Also the tool definition to to give the LLM everything to make the right
decisions.
00:30:52:11 - 00:31:08:10
Stefan
Okay. Yeah. And and then the last one is pretty explanatory. So you can connect with any of the
tools that you guys are using. ChatGPT claude cursor with minimal configuration. Yeah. What
kind of benefits do you want to add to. Kind of just like the benefits of MCP for your GraphQL
API.
00:31:08:12 - 00:31:41:24
Jens
So one topic we talked about on on LinkedIn and other discussions about MCP is, if you simply
expose a GraphQL API or a Rest API or any API or a database through MCP, what is very likely
to happen is that you you give AI a task. You know, let's let's say the LLM model has a tool to
get the whole GraphQL schema and then a tool to make queries and mutations.
00:31:41:27 - 00:32:17:25
Jens
And now you type in the prompt to do something. Will it actually understand to look into the
GraphQL schema to then parse the GraphQL schema, which it can be so large that it actually
goes beyond the context? And then will it be busy figuring out your schema, or will it actually
answer your prompt? And so the the the problem we're we're solving here is if we can persist
some documents or create trusted documents, persisted queries, and limit what we want to
expose.
00:32:17:28 - 00:32:41:11
Jens
First of all, we we make it technically much easier for the model to interact with our with our
tools. And the second thing is, you don't just want to expose GraphQL or Rest APIs through
MCP. You want to carefully think about what are you exposing and what are the workflows you
want to enable the model to do.
00:32:41:11 - 00:33:06:27
Jens
Because a model is not just it's not a human that clicks on the user, that loads the user and then
loads the posts and then adds a comment to the post. A model is an LLM that that does a task.
For example, 111 workflow we have in cosmos, we have a query that's not working and we want
to go through a workflow to change the schema so that the query works.
00:33:06:27 - 00:33:30:16
Jens
We call this the dream query workflow. So that's the workflow of like many many steps that the
model can go through to accomplish the task. So if you model your MCP tools you need to think
about these workflows. These like what what should the model do. And so what you can do with
like exposing operations by writing the query, each query, you can give it like a description.
00:33:30:23 - 00:33:53:24
Jens
And you can also tell the story of okay, here's here's a tool to do this. It gives you an employee.
And then you can also call another tool to do something with the employee. So your your
explaining how the different tools interact. And then that enables the LLM to, to to accomplish
like a real task. So yeah I think that's that's very important.
00:33:53:27 - 00:34:24:11
Jens
The, the other parts I think Dustin mentioned the most important things. One other comment is I
would say, we by by by simplifying the creation of an MCP server to write a GraphQL query, we
we actually give a lot more people access to this capability. You don't need to be a programmer
to write the GraphQL query, because we also offer it in the very near future.
00:34:24:11 - 00:34:58:26
Jens
Tools to create, a GraphQL query with a visual query builder or even prompt to GraphQL query.
So that means in the in the future, there will be a no-code solution or a low-code solution. So
that's everybody with a super graph without technical knowledge can create a secure MCP
server for their particular use case. And so in this sense, we're also democratizing access to
this, to this capability.
00:34:58:28 - 00:35:15:27
Stefan
Yeah. Well Said. So I do want to be conscious of time. So let's scroll down a little bit here and
understand, the available AI tools. And then Dustin, I would love to get into the demo so we
could just kind of speed run through these. But talk to me a little bit about these available AI
tools or the MCP shortcuts as I call them.
00:35:15:27 - 00:35:16:26
Stefan
What do they do?
00:35:16:28 - 00:35:19:24
Dustin
I would say I can, present them in the demo.
00:35:19:26 - 00:35:39:04
Stefan
Oh, okay. Perfect. So, guys, this landing page isn't live yet, but you can see here these are all of
the kind of, AI tools that we have integrated with our MCP. And Dustin will demonstrate it
actually in the demo. So let's switch over to that mode. Give me a second. And give it a sector
render Dustin. Because it would render in 4K.
00:35:39:04 - 00:35:59:03
Stefan
But maybe if you can make it a little bit bigger it would be great. Okay, that might have been too
big, but I think that looks good right there. But feel free to kind of just demo us for it and walk us
through it. And then Jens, just feel free to put questions into there. So that way the audience can
understand exactly what we're doing, but Dustin take it away.
00:35:59:05 - 00:36:29:29
Dustin
Okay, good. So as we discussed, like, the way how to integrate tools or exposing operations to
the MCP protocol is to creating persistent operations, trusted documents. So it is it is up to you
where you want to store them. So in that case, we have defined the storage provider with the id,
MCP, and we choose operations there as the directory to where you could be able to store the
operations and there are a few options you can choose from.
00:36:29:29 - 00:37:00:22
Dustin
You can define on what port the MCP server should be available. It is not possible to define the
path because in the later specification, the, the the protocol recommends to to expose the
endpoints over the MCP / MCP endpoint. And I think this is a good default for the start. You can
you can define the graph name to specify or you give your MCP a, server name as is a suffix.
00:37:00:25 - 00:37:26:24
Dustin
And then the two other, multiple other option, you can expose the full schema to the MCP. But
what we usually do not recommend because, the recommended approach is to expose specific
operations. But this might be useful, useful for exploration or development. Then you can also
enable the executing of, arbitrary operations, which will expose an execute graphql tool.
00:37:26:26 - 00:37:55:19
Dustin
And you can also exclude mutations from your expose trusted documents for safety reasons.
And last but not least, we also expose the router URL because sometimes you might have or I
think often your expose your router are not through localhost but on on on the domain. Yes. So
so that means in that case your, your tooling, you MCP tooling will be aware of where your
router is actually hosted.
00:37:55:22 - 00:38:24:02
Dustin
So it can do real API integration. All right. So this has been already started that let's take a quick
look about the three operations we provide. And operation to to find employees. We have a
search input which accept multiple filters like search filtering by has pets nationality. It also has a
comment, which is pretty important because we will incorporate that into the JSON schema.
00:38:24:02 - 00:38:48:19
Dustin
As discussed before, we will have update update availability to update. Yeah. The the
availability of an employee by ID. And we can also update the moods of an employee. So pretty
pretty funny example. They are coming from our demo and in the OSS repository. You can
essentially try it out yourself. Yeah. So the next step is to start the raw data, which we have
already done.
00:38:48:21 - 00:38:49:25
Jens
One second.
00:38:49:27 - 00:38:51:02
Dustin
Yeah.
00:38:51:04 - 00:38:59:18
Jens
Can you go back to the operations. You can go back to the operation that has this comment.
00:38:59:21 - 00:39:02:09
Jens
Yeah. Here. This is in the schema right.
00:39:02:12 - 00:39:03:15
Dustin
Yes.
00:39:03:18 - 00:39:06:18
Jens
Okay. What are you doing with it.
00:39:06:20 - 00:39:35:00
Dustin
So when we, convert or when we walk through the GraphQL document, we will verify if there are
any comments on these nodes. And when we find them, we will while creating or while walking
over the document we will also create a nested schema. So the document and we will
incorporate this information into the into the field description field okay.
00:39:35:00 - 00:39:45:10
Jens
So this will be in the JSON schema in the OpenAPI spec that we expose through the MCP
introspection endpoint.
00:39:45:12 - 00:39:46:21
Dustin
Exactly.
00:39:46:24 - 00:40:14:05
Jens
Okay. This is super important because you know, everybody is lazy. Everybody is like, oh, like I
don't care. I don't want to document my stuff like code documents itself. No it doesn't. And
here's the thing. If you put good documentation into your into your GraphQL schema, we
automatically stick that into your, into the, into the JSON schema for your MCP server.
00:40:14:07 - 00:40:34:21
Jens
And now AI can can introspect this. And it now can better understand what what is possible. So
by writing good documentation on the schema you allow LLMs to be more precise to better use
your GraphQL API.
00:40:34:24 - 00:41:12:01
Dustin
Yeah 100%. And this one it shows how to how we just add the documentation to the tool
description. So because my operation has used find employee and we have added a comment
here, this will serve as a tool description for the MCP tool. And if you would have here multiple
root fields. What we can do in graph ql, then we would combine this into one big chunk of
description, which then the LLM can use to to get the most of it.
00:41:12:03 - 00:41:13:25
Dustin
Yeah. So we have three operations.
00:41:13:27 - 00:41:26:01
Jens
Sorry, sorry for the interruption. I just I love these little details because it you know for LLMs
context is key. Everything you can tell it.
It will be.
00:41:27:04 - 00:41:30:18
Jens
It will be easier for the model to help you.
00:41:30:20 - 00:41:33:14
Dustin
Exactly.
00:41:33:17 - 00:41:36:15
Stefan
Okay. So continue this is this is pretty sick so far.
00:41:36:18 - 00:41:47:20
Dustin
Yeah. So I we have the operations. We have two demo config. We started the router. Now we
can try to connect it with claude desktop.
00:41:47:22 - 00:41:53:27
Stefan
great.
So give it a sector render distance a little bit blurry for me. And if you could zoom in that'd be
00:41:54:00 - 00:42:14:15
Dustin
Yeah. So, unfortunately, the integration of MCP is, I would say, more developer focused. So
essentially you would need to go to settings, the, developer, then you would need to configure,
your MCP in. Yeah. As a JSON. We will soon publish the documentation around this. It's just
copy paste and then you are good to go.
00:42:14:15 - 00:42:24:21
Dustin
But you also need to restart claude desktop once you have configured your, your, configuration.
Okay. Let's not it's not visible. Right. So,
00:42:24:24 - 00:42:28:06
Stefan
Can you zoom in just a little bit. Make it a little bit bigger.
00:42:28:12 - 00:42:30:09
Dustin
Zooming is not possible here okay.
00:42:30:11 - 00:42:38:06
Stefan
You can make it like the control X like on Mac to make it zoom in. Oh see. Yeah. Ctrl or
command X okay.
00:42:38:09 - 00:42:39:08
Dustin
Awesome.
00:42:39:10 - 00:42:48:11
Stefan
There you go. Look at me. I'm teaching my CTO about some tech stuff. Give it a sector render.
But, Okay, I see the prompt. It looks good.
00:42:48:13 - 00:43:18:15
Dustin
So we have prepared a prompt. The prompt what what what what did we instruct, claude to do?
It should create an next js app that visualize the most important data of our employees and but
also allow us to manage them. So that means based on the expose operations through the
MCP protocl the LLM creative to building a dashboard to main to manage your employees.
00:43:18:18 - 00:43:53:23
Dustin
And there are some important, I would say, prompt instruction. You have to give the LLMS so
that it does not hallucinate, or at least that the that the instructions are clear. It should not use
mock data or fake endpoint. It should not reinvent stuff. It should focus on the integration with
expose a few tools. And yeah, so also important and I wanted to share is one sec there is a tool
called MCP inspector okay.
00:43:53:24 - 00:44:19:18
Dustin
I mean yeah it's allows for for debugging purposes to understand what tools and MCP server
exposes. So before we start, before we run the prompt, I would like to show you what is what
the LLM, will be accessible of. So, it can you see we have exposed three custom operations.
You see here the description that we mentioned.
00:44:19:20 - 00:44:55:08
Dustin
Ignore this. This is just a demo. And here, the what is the update availability operation capable
of. What are the parameters? This is this actually reflects the JSON schema struct. You can
see, for example, my employees this is nested. And but also we also provide an end point that
gives the LLM superpowers to understand how to how to run this operation in, in in a, in a real
world scenario like how does the end point looks like?
00:44:55:10 - 00:45:23:07
Dustin
How how does the HTTP request has to look like in order to make a real and successful request
against the router? So now if we if we now start the the prompt, the LLM has access to all these
tools. And based on our instruction, it will it will make the best decisions. And hopefully we will
create an next js application which we can copy paste into our Cosmos Studio to, to manage
employees.
00:45:23:10 - 00:45:24:06
Stefan
Let's do it.
00:45:24:09 - 00:45:50:18
Dustin
And if you click here again, just a side note, you can also here explore the available tools. And
now let's let's kick it off this can I think this this takes around 30 sec. Maybe if someone has
something to say it's it's the right moment. And here it asks for for permission to get the info of
the operation to understand how to run it.
00:45:50:21 - 00:45:57:24
Dustin
And it would do it for all operation that the LLM thinks it needs access to.
00:45:57:27 - 00:46:10:05
Stefan
So this is pretty incredible. And Dustin, so far you have you tried this with cursor or how come
you prefer claude desktop?
00:46:10:07 - 00:46:26:02
Dustin
I think the, it also works with cursor. But I think for, for demonstration purposes, this, this, this,
this isolated view and the code generation is this, I think it's much more appealing for, for users
here.
00:46:26:04 - 00:46:41:20
Stefan
Yeah. I would say it's a little bit more user friendly. And one of the things me and Jens we're
talking about is like the power of MCP and the power of like just using this and being with the
generator, you still need that developer background and hopefully soon there's a way that we
can kind of go past that.
00:46:41:20 - 00:46:45:27
Stefan
We can just talk to it and build things just like this without having to understand that background.
00:46:45:29 - 00:47:01:08
Dustin
If you if you take a look at the description as a prompt, is really not, if you're if you ignore this
part here, which could be like a base template and only look at this, section. Yeah, there's
nothing technical in it.
00:47:01:10 - 00:47:07:06
Stefan
Yeah. Well, yeah, it's next js and tailwind for styling when you got to know what those two are.
00:47:07:08 - 00:47:48:04
Jens
Yeah, but but you know, one thing I have observed in the MCP community in the last couple of
weeks is that more and more people who are not developers, who are now using cursor to to
build applications and to, to achieve something, to automate something and, yes, you can, you
can make an, an argument and say, okay, there will be security problems and other issues and,
and I'm not trying to argue against that, but what what I'm trying to get at is there's a new
movement of, yeah, like this cursor with LLMs.
00:47:48:04 - 00:48:07:20
Jens
With MCP. More people are now able to, to automate processes to, to build applications and to,
to, to get some or so. Yeah. We need to think about security carefully. But I think in general it's
a, it's an amazing movement.
00:48:07:23 - 00:48:33:03
Dustin
Yes. So with, Claude is done, we can now, if you observe this here, you see, it has actually used
the right end point because this endpoint was exposed through the get operation info endpoint.
It has set the right headers, the right, request, scheme. And yeah, I, because I instructed the
LLM to create a single page and not create multiple components so it's easier to copy.
00:48:33:06 - 00:48:49:02
Dustin
Now I will copy it into our application and let me share the result.
00:48:49:05 - 00:48:55:08
Dustin
One sec.
00:48:55:10 - 00:48:59:02
Dustin
This is by the way, the Cosmo Dashboard. So and so.
00:48:59:02 - 00:48:59:25
Stefan
You're you're.
00:48:59:25 - 00:49:06:16
Jens
You're abusing your local Cosmo dashboard to to bring this in.
00:49:06:18 - 00:49:33:24
Dustin
Ex. Exactly. So now you see it has requested all the data. Those are actually real real requests
against API. And I can make employees happy. Sad. I can make them available. I can filter for
the marriage status and and to prove you that it's actually real data, we can open the GraphQL
endpoint.
00:49:33:27 - 00:49:34:27
Stefan
And query.
00:49:35:00 - 00:49:39:12
Dustin
And clear the data and.
00:49:39:14 - 00:49:41:07
Stefan
This is so sick.
00:49:41:10 - 00:49:43:24
Dustin
And just see Stefan is available.
00:49:43:24 - 00:49:49:02
Jens
Well it's okay now not now. Go to this dashboard and make Stefan unavailable.
00:49:49:05 - 00:49:55:14
Dustin
So let me apply filter Stefan. Let's make it unavailable okay.
00:49:55:14 - 00:49:57:25
Jens
Go to the API.
00:49:57:27 - 00:50:00:09
Dustin
You see.
00:50:00:11 - 00:50:01:17
Stefan
Okay.
00:50:01:19 - 00:50:13:05
Dustin
So it was pretty much a one shot to generate an application to manage your employees. And
now you can think of much more advanced and sophisticated sophisticated examples.
00:50:13:07 - 00:50:14:12
Jens
It's sick.
00:50:14:14 - 00:50:18:28
Stefan
It's insane. Insane.
00:50:19:00 - 00:50:55:00
Jens
It's, Okay. I've seen it the first time, but I think this is very cool. Like, you can very quickly build
those internal apps and you know that the, the, the interesting observation is in the past there
was like, you know, retool and other things and you had to manually connect the data sources
and you had to say, oh, here's my Postgres database, and I want to build this thing and take this
column and take that, and now the new reality is, you have a super graph.
00:50:55:03 - 00:51:25:18
Jens
You, you have this MCP server, you write a prompt and bam dashboards like it's it's
phenomenal. So to wrap this up, if I want to try this okay. Now it's not yet merged, but let's let's
assume you you merge it end of the week. Whereas the documentation where we're kind of
look, you you don't have to show if it's not yet ready, but, I can go to, to Cosmo documentation.
00:51:25:18 - 00:51:27:12
Jens
Right. And then.
00:51:27:12 - 00:51:40:05
Dustin
Yeah, pretty much Cosmo. Cosmo minus docs. And very soon here will be a new section called
MCP gateway. And then we will explain everything, to, to onboard you on this feature.
00:51:40:07 - 00:51:56:23
Stefan
We can even put a banner on the website just to guide people to it because it's so exciting. So
we'll do that on our end. Guys, we are at time, as I mentioned, I hope everyone has a fantastic
Easter weekend. The team will be off tomorrow and then Monday, but if you guys have any
questions, feel free to let us know.
00:51:57:00 - 00:52:12:12
Stefan
For our customers, we are so excited for you guys to try out, this new feature for everybody.
We're excited to it. Let everybody build good APIs. Maybe that'll be our mantra. Let everybody
cook. Everyone should build a good API. And, Jens. What's the good thing?
00:52:12:15 - 00:52:15:12
Jens
The good thing is we're back next week.
00:52:15:15 - 00:52:18:22
Stefan
We're back next week. Thanks, everybody. Bye.
00:52:18:25 - 00:52:20:21
Jens
So.