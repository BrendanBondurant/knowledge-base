---
title: "Demo Part 1: Setup, Router Config, Schema-First Design, Scaffolding First Plugin"
start_time: "00:23:46"
end_time: "00:33:04"
tags: [demo, cosmo-connect, plugins]
---

00:23:46:04 - 00:24:04:14
Jens
Thank you for that. This is, amazing. What we will do is we will keep collecting questions. We
give Dustin the time for the demo. And after the demo, we have, plenty of time left for for Q&A.
So, yeah, with that over to to Dustin for the demo.
00:24:04:16 - 00:24:16:08
Dustin
Awesome. So let's get, let's get our hands dirty. Yeah. So can everybody see my screen? I hope
this is a yes.
00:24:18:06 - 00:24:42:05
Dustin
Good. Awesome, awesome. So this is our, public repository that is accessible. So, feel free to,
to jump on it. After the meeting, we also keep it up to date with all the latest, features. And. And
what is this, demo about is, if you look at this diagram, you can see, like, this demo is like a
reference architecture of a federated architecture.
00:24:42:07 - 00:25:12:10
Dustin
And, Jens mentioned it already. This this reference implementation showcase how you can do
how can you leverage Cosmo plugins in the federate architecture by. But also using your
regular, subgraphs aside. So it, it shows the composability of, of of of technologies, because the
user service is implemented as a grpc plugin and the product subgraph is implemented as a
apollo subgraph.
00:25:12:12 - 00:25:37:22
Dustin
And, for people who are not familiar with cosmo in general, this demonstrates the cosmo router
to always demonstrate our API gateway, which is responsible of, taking, client requests,
GraphQL request, make the right subgraph fetches to the, downstream services, and then
aggregate the data and respond back to the user. So this small out or out outlook about the
architecture here.
00:25:37:24 - 00:26:06:24
Dustin
And the goal of the plug of of the tutorials demonstration is to bootstrap a complete new cosmo
plugin and bring that into the federated graph. And I'm going through the whole development
workflow how to, scaffold the plugin, build it, test it, but also to debug it because I think, I'm also
developer looking, I watched so many, tutorials and it's often of missing the point of how can I
actually debug my code.
00:26:07:01 - 00:26:15:24
Dustin
So and this is also a huge strength of a plugin system. It's not scripting. So it's just code. And
you can leverage the whole IDE tooling for that.
00:26:16:01 - 00:26:31:12
Jens
It's also not some directives that you put in your schema. And then you open the playground
and you can try out what maybe happens. Not exactly. Not trying to look at any other products.
00:26:31:14 - 00:27:00:21
Dustin
Correct. So, let me start the full demo and you can do it yourself if you're fast enough. And this
will, build everything. This is not important yet here. And, let me check. Okay. And so, you see,
just to demonstrate the functionality of the whole demo, let me also show the request trace. You
can see, we have made a call to users, to products.
00:27:00:23 - 00:27:22:15
Dustin
We also have an entity on products. So can we can resolve products from users. This is this is
actually working. So double check the before architecture here. We have the product subgraph
service which resource the products we have implemented. User service already with an
existing plugin. And this actually also it's just a demonstration of I can what I can run whatever
code in my plugin.
00:27:22:20 - 00:27:48:01
Dustin
As I want I can also make API calls. This could be for a stripe slack calls or it's whatever. So this
is working fine. So now let's, let's going into, the real thing and bootstrapping a plugin, I will keep
this process running because, Cosmos Router also supports watch mode. So if, whenever I
recompose my super graph, it will reload, hot reload and serve the latest schema.
00:27:48:03 - 00:28:11:02
Dustin
So now let me create a plugin. Wgc router root. Plugin init for people who don't know. wgc it is
our command line utility to interact with the control plane of cloud. But also for local
development. And here I would create a greeting plugin. It's the name and I would like to put it
into the plugins directory.
00:28:11:02 - 00:28:37:17
Dustin
It is just a convention. And I mentioned conventions. For the first iteration of plugins, we, we
went with a lot of conventions to simplify the bootstrapping, setup for if you look into the
bootstrap plugin, we have readme, it's auto generated. It also explains the structure a little bit.
For instance, Cosmo Connect, still encourages you to do schema first design.
00:28:37:19 - 00:28:57:14
Dustin
For this reason, we have, a schema graphql file into the source directory, which defines the API
context of your supergraph of your subgraph. A plugin. And then depending on your language,
you also have you may not go file or your main test file to, to implement your business logic.
This is like a very simple, example.
00:28:57:14 - 00:29:19:13
Dustin
It's a HelloWorld project. But I would like to also show that this is actually working. So what is
the next step of it? The next step is people again who are not familiar with Cosmo. If you have a
Cosmo router, you can configure the router by specifying the config.Yaml file in the same
directory. And here you can see, I want to enable plugins.
00:29:19:15 - 00:29:41:15
Dustin
I also want to hot reload the config. So the next time when I regenerate the plugin it will also
reload. And you also have very important for local developments because if you don't interact
with the control plane in cloud, you have to compose the whole subgraph locally. So we have a
config file graph.yaml file where I can specify my plugin.
00:29:41:15 - 00:29:52:23
Dustin
And this is also by convention. So here you can see I specify a version a path to my new plugin.
00:29:53:00 - 00:29:57:12
Jens
I think your indentation is not correct.
00:29:57:14 - 00:29:59:02
Dustin
One sec.
00:29:59:04 - 00:30:03:17
Jens
The users plugin is indented differently.
00:30:03:19 - 00:30:15:15
Dustin
No. Okay. It's it should be fine. Okay. So now I can I updated the router config file. Now I also
need to restart the router.
00:30:15:17 - 00:30:18:22
Jens
I thought you have watch.
00:30:18:24 - 00:30:26:06
Dustin
On sick I have watch. But this is a graph yaml file I have. I have no watch on this file.
00:30:26:08 - 00:30:31:21
Jens
The the the failed to set up plugin host.
00:30:31:23 - 00:30:37:03
Dustin
Okay. Makes sense because I didn't build the plugin yet, so I need to you.
00:30:37:05 - 00:30:40:13
Jens
You cannot start the plugin when it doesn't exist.
00:30:40:15 - 00:30:57:01
Dustin
Exactly. So the next step is to generate it. So and let me generate the plugin. Then I will also.
Oh so I'm in the wrong directory one sec.
00:30:57:03 - 00:31:24:06
Dustin
Generate. Here we are. What does generate, it converts the GraphQL schema into a proto file.
This is also visible by inspecting the generated directory. You can see this is actually the proto
file. And then we use standard grpc tooling to generate the steps that you can implement in your
code. And also very important is the order. The field order in proto is significant.
00:31:24:08 - 00:31:44:22
Dustin
However in GraphQL it's not so. And that was like a challenge we had to solve because, we
would lose, we would break the contract from, from proto. And we taken completely care of that
because of you maintain a mapping file. So if I would, change the order of my GraphQL fields,
this order would still be, preserved.
00:31:44:24 - 00:31:50:08
Dustin
And, yeah, those are some, some nifty details here. And.
00:31:50:10 - 00:31:59:12
Jens
Yes. How do you keep engineers busy? You invent new stuff that creates new problems, and
then you have new problems you can solve.
00:31:59:14 - 00:32:00:04
Ludwig
Yeah.
00:32:00:06 - 00:32:34:19
Dustin
So and then, the build process, the build is actually compiling my, my go code into a binary. Put
that into a bin directory. And all this tooling is automatically installed, on your host machine by
just, yeah. Running those commands. And then we also have a bin and then here you can see
this is binary, and then we come back to, this file, this, knows know the location of the new
plugin directory is in plugin scripting, and everything else is by convention, there must be a
binary in bin.
00:32:34:21 - 00:32:43:18
Dustin
works.
There must be a generate folder with the right artifacts, and then I can try it again. I hope it
00:32:43:20 - 00:32:46:17
Ludwig
And we hope for you.
00:32:46:19 - 00:33:04:13
Dustin
say hello Ludwig.
NPM start. All right. So let me run this again. And then I should also have a hello. Yes. And let's