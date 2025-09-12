00:04:01:14 - 00:04:32:21
Jens
should go ahead and just start. Okay. Yeah. It's, it's great to do a webinar again. I think it's it's
been a very long time. We we did webinars. I think the last time when we had, the Wunder
Graph SDK.
00:04:32:22 - 00:05:00:07
Jens
That was a time where just, Dustin and I actually were at, the company from the group here. We
didn't have Jacob. We didn't have Jesse and Ludwig. Since then, a lot of things have changed.
We have built, Cosmo. And today we want to talk about, Cosmo Connect. That is like the, the
next piece of the of the puzzle, of the puzzle that we're trying to put together, and,
00:05:00:09 - 00:05:23:00
Jens
Yeah, it's, it's a pleasure to be your host today. My name is. Jens. I'm, the CEO at WunderGraph
and mostly responsible for, product. I'm here joined today by, Dustin Ludwig and Jesse. Dustin,
our CTO. Welcome to the show.
00:05:23:02 - 00:05:25:03
Dustin
Hi. Welcome. Yeah.
00:05:25:05 - 00:05:28:04
Jens
What what's your role in the in the project?
00:05:28:06 - 00:05:45:15
Dustin
I was, I was in charge of of the architecture and also the the project lead. So, I will also be
responsible later to show you a full demonstration of the development flow of how to develop,
Cosmo plugin in in real world. Yeah, that's my part.
00:05:45:17 - 00:05:52:09
Jens
Awesome. Then we have, Jesse from the UK. Hi, Jesse.
00:05:52:11 - 00:05:55:16
Jesse
I'm from Canada. Don't, don't call me from the UK.
00:05:55:18 - 00:05:57:02
Jens
Okay, but you live in the UK.
00:05:57:03 - 00:06:13:05
Jesse
I do. And I worked on a lot of this stuff that you'll find after the demo. Which is with regard to
how this is going to work with the Cosmo Cloud platform, as well as a bit in the early stages of
how this actually really works at a low level with the router and engine.
00:06:13:07 - 00:06:23:21
Jens
Awesome. And, finally we have Ludwig from Berlin. Hi, Ludwig. Hi Jens. What's your role in the
project?
00:06:23:23 - 00:06:47:05
Ludwig
I've been working on on on the engine part. So the part, converts GraphQL requests into gRPC
requests and performs a communication with the new, subgraphs and, in the protocol, and then
converting the responses back to GraphQL responses.
00:06:47:07 - 00:07:16:24
Jens
Okay. Perfect. Great. Yeah. So that that's us then. I want to, welcome everybody to the to the
webinar. Our existing customers, maybe, someone who's, who's, new to the show and,
interested in what Wunder Graph doing. And also, the people from Apollo who signed up with a
fake account. So welcome, everybody.
00:07:17:01 - 00:07:28:10
Jens
To our webinar today. Let me quickly share. We have a little deck, and then we go into the
demo. So.
00:07:28:12 - 00:07:30:04
Jens
Can you properly see this?
00:07:30:06 - 00:07:34:06
Dustin
That was quite funny. Let's see.
00:07:34:08 - 00:07:42:00
Jens
Okay. Do you properly see my screen or what am I sharing? Because I don't see what I'm
sharing its working.
00:07:42:01 - 00:07:43:00
Jesse
Yep.
00:07:43:02 - 00:08:08:14
Jens
Okay, cool. Okay, so that's us. Quick agenda. I want to talk a little bit about, the problem we're
solving with Cosmo Connect. Why? We have actually build it. How does it work? And then, most
time we we actually want to, want to spend in a live demo, show you end to end how everything
works.
00:08:08:16 - 00:08:29:22
Jens
We will have that, with Dustin and, yeah. Then we have time for Q&A. Again, we have Jesse
and Ludwig here. The people who worked hands on on everything. So you can go, super
technical. Any questions? You have, just, pop them up into the into this Q&A thing, and then,
yeah, we will handle it along the way.
00:08:29:22 - 00:08:58:11
Jens
Or maybe later. Cool. All right. So, first of all, it's it's possible that we have some people here
who are not 1,000%, familiar with, GraphQL or Federation. So. So real quick. This webinar, it's
it's kind of targeted towards, the people who, who have at least some familiarity with,
Federation, but on, on a high level.
00:08:58:13 - 00:09:30:13
Jens
We have the, the concept of, entities and, we, we kind of, like to say that, the, the key directive
is like, a big enabler, to allow us to build a super graph from multiple, services. And, yeah, we
have seen tremendous success, with companies like, eBay, Paramount, SoundCloud and many
others, who built on top of this, paradigm.
00:09:30:18 - 00:09:57:02
Jens
But what we have also figured out is that there is a couple of, of, problems, with this, with this
architecture. And here, here are some, of of the key issues. Just quick question into into the
round for Dustin or Ludwig or Jessie. From your own perspective, what what have you observed
from talking to customers?
00:09:57:04 - 00:10:06:16
Jens
What what is what is the biggest blocker in adopting federation today?
00:10:06:18 - 00:10:09:14
Jens
Dustin any ideas?
00:10:09:16 - 00:10:16:00
Dustin
So without reading the bullet points, I would say, it's.
00:10:16:02 - 00:10:48:16
Dustin
I think it's super unrealistic to assume that the company that all all departments or all members
of the company, are able to speak GraphQL or and also implement GraphQL on the server side.
So you always have I was a diverse, system. And at some point you also need to bring those,
components into, the super graph or into something that, combines everything together so that
consumption is easier across the company.
00:10:48:18 - 00:11:09:21
Dustin
And this is one of the struggles I have observed, through customers. Everybody understands
and also believes in, in the graph architecture. But this the, the, the, the hurdle to integrate
legacy API's into that system and make it part of a broader ecosystem.
00:11:09:23 - 00:11:36:00
Jens
Yeah. Like yesterday I was on a sales call, with a company with more than 100 subgraphs, and
they have, a large amount of API consumers. If you think about, the front end experience, it
would be extremely hard to build a front end against 100, subsystems, 100 microservices, that
kind of integration, it would be almost impossible.
00:11:36:05 - 00:12:09:07
Jens
That's the problem we solved with Federation. But on the other side, we cannot force everybody
to migrate everything to be a GraphQL subgraph. You have a lot of, legacy APIs, maybe some
some Soap, or maybe you have a mainframe. Maybe you want to integrate a message queue or
a Kafka or anything. And what we also observed is that a lot of our customers, they build
subgraphs as very thin layers around some other system.
00:12:09:09 - 00:12:32:05
Jens
So the front end guys, they really need some extra data. They they like to have that unified API
interface. The, the the one graph. That's a powerful thing. But at the same time, connecting all
these data sources, it's a pain. And you don't want to deploy a subgraph for every little, field,
you add. So that's like too big of the, of the problems.
00:12:32:07 - 00:13:00:05
Jens
Another issue this I have from, from a discussion, with someone working at, like an architect at a
very large, fortune 500 company. Not everybody in the company has the same skill set in
implementing subgraphs, and federation can be quite complex with directives like requires and
others. So how can you help people implement, a service that's actually correct.
00:13:00:07 - 00:13:27:23
Jens
That works how you would expect it and can you, can you build tooling and can you set
guardrails that, that help people? Yeah. Implement subgraphs correctly. Because if you if I have
a subgraph, and I use something like, Apollo Server, maybe not even with TypeScript. I have my
SDL, I have resolvers, and maybe but only maybe this whole thing together is working like I
would expect.
00:13:27:23 - 00:13:53:19
Jens
And then I can have testing and other parts. But this is also something where, we're addressing,
with custom connect, number for this, one, one very big issue is Apollo is the, the main driver in
the, in the Federation ecosystem. And they control a lot of the subgraph frameworks, which it's
it's a good and a bad thing.
00:13:53:19 - 00:14:14:23
Jens
I don't even want to turn this into a rant, but what it absolutely is, if they come up with a new
feature, it can take months or even years until all frameworks really adopt the feature. And so
that means you you have a feature, you implement it in the router, and then all the frameworks
need to adopt it.
00:14:15:03 - 00:14:57:12
Jens
And that's actually, a very long step. And with Cosmo Connect, what we can actually do is we
implement it once in the router and everybody can benefit immediately. And the last part is,
yeah. As I said, Apollo has a lot of control over the ecosystem. They maintain, the, the big
implementations of subgraph frameworks. And what that also means is, if we as wunder graph,
if we think, there should be an amazing feature in, in, in Federation and we implement in our
router, but nobody will ever adopted in the main frameworks for GraphQL subgraphs, we have
no power.
00:14:57:12 - 00:15:30:05
Jens
We have no say by building Cosmo Connect, we can move the responsibility of the subgraph
into the router. Dustin, will talk much more about this. And with that, we're free from this
dependency and we will have a lot more competition. And I think we all agree competition is
good. And, I think we all want more competition in the in the microservice API integration market
because it's good competition, means everybody pushes harder and we build better solutions.
00:15:30:07 - 00:15:48:10
Jens
Okay. So that's the problem. Next, we want to enter Cosmo Connect. The solution. So, Dustin
explain us what actually is Cosmo connect.
00:15:48:12 - 00:16:24:01
Dustin
Okay. A very on a very high level, I would say you can describe the Cosmo Connect as
self-contained. Service it that runs gRPC and, connected to our router. And you still design your
API context through graphql but. The communication protocol is different. So the router will
communicate from the router to the plugin, over a gRPC, which eliminates, parsing of, of
operations twice.
00:16:24:03 - 00:17:10:12
Dustin
It eliminates, performance overheads in subgraph frameworks. It also makes, the
communication much more direct. This is how I would describe, Cosmo Connect. It's and
because of the gRPC implementation, is is free of any, any specific implementation, for instance
graphql, you can do whatever you want in that implementation and science in before said a lot
of companies building a thin layer between services to connect it to the super graph, or they are
connecting to an API, in that word here, you don't you just you really can focus on your
implementation and the rest is handled by the router.
00:17:10:14 - 00:17:34:06
Jens
So on a high level, I send the GraphQL request from my client to the router. The router then
translates it into proto messages, sends them to my gRPC services. They send back proto
messages. The router again translates it back, builds my Json response, and gives me a Json
response that looks as if there was a graphical server.
00:17:34:07 - 00:17:42:16
Dustin
Exactly. That's why we call it sometimes gRPC subgraphs. And yeah, and pretty much.
00:17:42:18 - 00:18:04:15
Jens
And you made a great point about performance because, and I was thinking a very long time
about this, like in the router. And I can tell you, like, we put years of work into making the router
fast because the router it does a lot of work. It it passes the query it it validates it, it normalize it,
it actually normalize it.
00:18:04:15 - 00:18:29:22
Jens
Like I don't know how many times 10 or 15 whatever times because there's a lot of steps to do.
Then we do the query planning and and all these steps. And then we we create text, GraphQL,
queries, encode them as bytes, send them to the subgraph, and the subgraph parses it again
and validates it and looks. Is that a real valid GraphQL query?
00:18:29:22 - 00:18:58:00
Jens
Although it could actually trust our router. But yeah. And it does all this work again. But we
already did the work. And, I think one of the biggest pitys about this traditional Federation
architecture is in the router. We have a super efficient data loader that de duplicates, multiple
requests that want the same data. And we, we have like, data loader batching in the router.
00:18:58:02 - 00:19:23:00
Jens
Then we send the batched request to the subgraph. And now the subgraph has to implement a
data loader again to efficiently load multiple entities. And yeah. By by moving this problem into
the router. You don't have to do that again. We send you a batch request. You give us back a
batch response data loader Not your problem anymore.
00:19:23:02 - 00:19:37:02
Jens
And, yeah, I think that's a great step forward. Cool. Here's how it works. We have two ways,
router, router plugins and gRPC services. What's what's the difference here.
00:19:37:04 - 00:20:00:08
Dustin
So in case of router plugins. So, so under the hood they are more or less the same. Your, your,
you’re starting with the graph, a schema, you're, converted into a protobuf. And then you from
that point on it's just gRPC tooling. You can leverage any language you want. The the difference
between router plugins and GP services is the way how you deploy them.
00:20:00:08 - 00:20:29:03
Dustin
So for for small teams and for local development, you can let the router, supervise, manage the
spawning of these plugins, which, essentially, subprocesses, by the router. And here we also
leverage leveraging a technology also used by millions of, of, deployments of, HashiCorp, for
instance, it's go plugin. Architecture of, of, HashiCorp.
00:20:29:05 - 00:20:52:17
Dustin
And however there is also absolutely the need in order to deploy services standalone for
example, you want to, maintain them, operate them in multiple teams, or you just want to scare
them out for, for efficiency reasons. In that case you would handle a GRPC. service as nothing
more than just a subgraph, with a routing URL and a GraphQL schema.
00:20:52:21 - 00:21:15:20
Dustin
So our in cosmos cloud, our cloud does not doesn't know anything about gRPC because we are
operating on the schema level. And as long as everything is composable and there is a valid
routing URL behind the subgraph, everything works as before. So the frontend knows nothing
about gRPC. The background, the backend can really focus on implementing their business
logic.
00:21:15:22 - 00:21:41:19
Jens
Yeah. And just as a side note, thanks for the explanation. You can actually have gRPC plugins
and gRPC services and Apollo GraphQL subgraphs side by side together. It's for the router. It
doesn't matter. It can speak to all of them together and then combine entities from one and the
other. And you can mix and match.
00:21:41:21 - 00:21:53:14
Dustin
And there's one more point I would highlight in this, jesse should explain that we also have a
very tight integration with Cosmo Cloud when it comes to router plugins deployments. Could
you, could you elaborate on that?
00:21:53:16 - 00:22:22:11
Jesse
Yeah. So when you're using Cosmo and the router and developing plugins with the Cosmo
Cloud product, you don't actually have to handle the deployment of your routers directly into
however you're deploying your router. You can actually publish them directly through our CLI
wgc to the registry for plugins we have set up, and the router is able to pull them down
alongside your configuration for your super graph and run them and reload them alongside your
your main configuration.
00:22:22:13 - 00:22:34:23
Jesse
We can talk about this more later I think, but yeah. In short, there's very good integration with
live deployments and matching up with the exact schema changes in lockstep with the router.
00:22:35:00 - 00:22:47:17
Dustin
That means you can decide if you want to build a huge monolith for simplicity, for for fast
iterations or your, scale them out as individual deployments on your Kubernetes cluster, as
separate pods, etc..
00:22:47:19 - 00:22:50:05
Jesse
Yeah.
00:22:50:07 - 00:23:19:12
Jens
You could even say if you want it with plugins, you can build like a modular monolith, or you
make it a microservice architecture. But, you know, most of the time when we talk about
modular monolith versus microservices, it's actually very hard to turn a modular monolith into
microservices. With Cosmo Connect, you can deploy the services as plugins, and one day you
decide, oh, this one plugin, it's overloading my router.
00:23:19:14 - 00:23:46:02
Jens
I move it into a service and you just deploy it differently and that's it, because plugins are
isolated processes. So yeah, that's just as a side note. Okay, I see where we're we're actually
quite busy with, with the intro. I want to give Dustin as much time for the live demo. Now, that
being said, we have a question already.
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
00:33:04:15 - 00:33:21:08
Dustin
All right okay. So it's resolved. So I think this is kind of a lot of boring. So how can I extend my
schema? So let me go to the schema file here, and let's say it's implement a goodbye, root field.
00:33:21:10 - 00:33:23:17
Jens
You're so creative.
00:33:23:19 - 00:33:44:19
Dustin
I know. So and I would like to make it a little bit more exciting. So what is my next step? After
manipulating the schema, I need to generate it again. I hope that makes sense. And now you
can observe again in the generate folder. Okay. My my contact has extended by query.
Goodbye. And now I want to implement it.
00:33:44:19 - 00:34:10:00
Dustin
And now it's very interesting because we are generating such, a strong tight contract, it we
figured out that it's, I would say it's rematch with LLMs today because it's very simplistic and the
LLM not exactly what, what what needs to do in order to, to fulfill that contract. It becomes a
challenge over time when you have lots of lots of endpoints.
00:34:10:02 - 00:34:39:04
Dustin
But this is also a challenge we will soon address, on, on on Cosmo Cloud and our, future
product. So as an example, let's take these files. To implement my missing methods, this mock
data ends up the tests.
00:34:39:05 - 00:34:45:21
Dustin
This can take, I think, 15 seconds, I hope, I hope it's that's fine for everybody.
00:34:45:23 - 00:34:49:11
Jens
By the way, you're. This is like a cursor IDE, right?
00:34:49:13 - 00:34:50:14
Dustin
Yes.
00:34:50:15 - 00:35:02:22
Jens
Okay. And I have noticed something. There's like a .cursor folder, like, did you create it or did it
come or did this come with, with the plugin generation or rather it's coming from.
00:35:02:24 - 00:35:15:13
Dustin
It comes out of the box when you bootstrap a plugin. It is like, I would say an optimized plan of
how to run commands and execute commands based on the bootstrapped, project structure.
00:35:15:15 - 00:35:31:16
Jens
So this whole plugin architecture, it is designed from the ground up to be to be optimized so that
developers can leverage AI to, to write the glue code.
00:35:31:18 - 00:35:33:22
Dustin
Right.
00:35:33:24 - 00:35:36:12
Jens
And then this is so good.
00:35:36:14 - 00:35:50:18
Jesse
And that's going to be significantly easier than trying to coerce cursor or claude or. Whichever
LLM you choose to write very idiomatic GraphQL code in whatever framework you found is
there. they're all very different. And there's a lot of foot guns.
00:35:50:20 - 00:35:54:12
Dustin
Yeah. Okay.
00:35:54:12 - 00:36:31:12
Jens
So I actually did an experiment like a while ago, I ask, I don't know what what model that was
Gemini 2.0 or I think I also tried it with, with sonnet and I ask it, I ask cursor to implement an
Apollo Federation subgraph with Apollo server and, yeah, what I kind of figured out is that, and I
think we all kind of, conclude that these days, if you give an AI too much, too much room for
interpretation, like implementing a GraphQL server that alone.
00:36:31:12 - 00:37:04:09
Jens
It's a challenge. Figuring out how federation works, you need to have, like, the right tools for
schema validation and everything. So it's it adds to the challenge. And then properly
implementing like, like entity resolvers and all these kind of thing, it adds complexity. And what
we really tried to do with, this, gRPC architecture is we take your, your subgraph SDL, we
compile it into proto, then we have this folder here with cursor rules and everything.
00:37:04:11 - 00:37:39:15
Jens
We also tell cursor like, hey, this is how we write tests. This is we compile everything. So we
really try to to narrow down everything that could add complexity, put AI on the shortest leash
possible to, to limit, like, hallucinations and everything. And so far our, our, results, look very,
very promising because ultimately what we want to achieve here is, you have your subgraph
SDL, you have an open API spec or a.
00:37:39:15 - 00:38:03:08
Jens
SOAPl or whatever, and somehow we need some code in the middle to, to adapt it to, to the
graph. And the end goal is to just say, hey, cursor, here's my RPC, here's my open API, handl
the rest, write the tests, implement the functions, do it right, and then, yeah, that's what Dustin
And the team is trying to achieve.
00:38:03:10 - 00:38:05:20
Dustin
All right. Great. For the,
00:38:05:22 - 00:38:11:15
Jens
Comprehensive, I just try to fill the time until your thing here is done.
00:38:11:17 - 00:38:35:02
Dustin
No. I'm ready, I'm ready. So go ahead. So I just like a simple implementation of a query. Good.
Bye, method and also tests and. Yeah. So let's you also have, like a WGC commands to run
tests in a specific language. And now we can see, okay, test completed successfully. What is
the next step of it. It is again to build it.
00:38:35:04 - 00:38:39:03
Dustin
00:38:39:05 - 00:39:08:18
Dustin
Build it. And then of course also to compose the latest supergraph configuration. And then the
router will pick off, pick up the last execution config to, well, I always mixing up I don't know why,
I always run make, but it's pmpm. Okay. And then you can see here it just picked up, it was
reloaded. If I reload my screen, I should have a good bye here.
00:39:08:20 - 00:39:43:07
Dustin
Good bye. Peter. I don't know anyone called Peter, but it's okay. Good bye. So if we show the
trace again, you know, making calls to three different, subgraphs, two of them are implemented
as gRPC. And it's not super obvious here, but even in HelloWorld examples, we see it
significantly significant, improve in performance. So and this makes this for example here is 0.56
milliseconds.
00:39:43:09 - 00:40:13:18
Dustin
And this is actually making an external call to APIs. But yeah. So even in this simple example
we see like how much we save by moving from http to binary protocol like gRPC. And if I come
to the demo again now I have implemented another gRPC plugin. Next to users, I have
incorporate, also product subgraph, which is the standard or GraphQL server, that compatible
with any frameworks out there.
00:40:13:20 - 00:40:27:04
Dustin
And yeah, I would be interested in what examples and examples. And you would implement
with grpc plugins. Yeah. And I think this is also also the demo. And thanks.
00:40:27:04 - 00:40:52:03
Jens
So thanks. Awesome. Thank you. Thank you Dustin. Great. Great demo. one thing I want to
notice because you were talking about performance, oftentimes we when we when we speak
about performance, we, we like to look at the gateway and the router and which one is faster
and which one is written in go and rust and, everything in rust is always faster and better.
00:40:52:05 - 00:41:20:18
Jens
But one thing we kind of never talk about is the performance of subgraphs. And, quite a while
ago we had, we had a customer, they were using elixir in the backend. And, I have no opinions
about Alex here. Like, a lot of nice people use elixir, but for some reason, the framework wasn't
really extremely performant in parsing GraphQL requests.
00:41:20:18 - 00:41:48:18
Jens
And they had a crazy schema with, with, a lot of, complexity abstract types. So the router would
send huge queries like, I don't know, ten kilobytes of queries, to the, to the subgraphs, which
even let us to actually build like, like a, compression algorithm to compress, duplicate fields, by
moving them into, into fragments.
00:41:48:18 - 00:42:15:22
Jens
We have a blog post about that. Anyways, what I'm trying to say is performance at the router
level is one thing. Performance at the subgraph level is another topic. And if you have, like, not
compiled language, maybe TypeScript or elixir or I don't even know if elixir is compiled, but, let's
say TypeScript, Node.js and the subgraph implementation by itself is not crazy performant.
00:42:15:24 - 00:42:49:06
Jens
If we're replacing at the subgraph level, GraphQL with gRPC, we do less work because parsing,
gRPC binary requests, it is just less work. We don't have to validate so much. We don't have to
parse so much text. It's just simpler and faster and also encoding. So by replacing GraphQL at
the subgraph layer, we we can gain a lot, just by making our subgraphs, faster.
00:42:49:08 - 00:43:21:00
Jens
The router is heavily optimized, like if you use, Apollo router or cosmo router, like, both are
super fast. We invest heavily into making them fast on, on the framework level. Yeah, you could
gain a lot just by using, a different approach. And, oftentimes I would say if, for example, if you
use like Node.js, it's very likely that you have a lot more subgraphs running than routers just
because the, the routers, they are just proxying the requests.
00:43:21:00 - 00:43:45:00
Jens
They don't do like database stuff and everything. So yeah, you you could save a lot of latency,
but also, CPU so that means in the end you save money by replacing, a slow subgraph with a
gRPC subgraph. So that's just, something on the topic of performance. Cool. One thing before
we go. Sorry to it.
00:43:45:02 - 00:44:10:09
Dustin
I actually forgot something. I need to reshare my screen. I promise you in the beginning to show
how easy it is to debug the plugin. So I forgot that thing. So give me, one minute. So here we
are again. So because it's a subprocess spawned by the router, I can also just attach to this
process. So and you can see here now I make a query again.
00:44:10:11 - 00:44:15:12
Dustin
Okay. one sec.
00:44:15:14 - 00:44:18:01
Jens
Did you really want to do this.
00:44:18:03 - 00:44:22:14
Dustin
Yeah I will do it.
00:44:22:16 - 00:44:27:14
Dustin
Okay.
00:44:27:16 - 00:44:31:24
Dustin
So this was right one sec touch.
00:44:32:01 - 00:44:35:11
Jens
Have you attached to the plugin that is currently running with this router?
00:44:35:13 - 00:44:52:18
Dustin
Yes, this is fine. Otherwise it would, indicate a wrong debug breakpoint. But whatever reasons, it
does not work. Oh, sorry. Good bye. Makes sense one sec.
00:44:52:20 - 00:44:55:21
Jens
You you are not querying them, I think. Okay, here we go.
00:44:55:23 - 00:45:12:01
Dustin
It works. So you can fully inspect and everything that was sent by the router to a subgraph. And
it just plain vscode and probably compatible with any IDE out there. Yeah. Thank you.
00:45:12:03 - 00:45:39:24
Jens
Okay, cool. Yeah. Before we go to the Q&A, I want to finish my slides. Am I sharing again? Yes.
Okay, perfect. So, what did I have here? So live demo, then? Documentation. Cosmo docs, if
you want to learn more cosmo docs/connect. Then, deploying your first, router plugin, customer
docs slash tutorial.
00:45:39:24 - 00:46:05:01
Jens
You can also just search for the tutorial, but we have an end to end tutorial where you can go
through or through all the steps, and try it out yourself. And maybe you want to, schedule a live
session. I know the URL says contact sales. But it's it's actually more like, yeah. Just connect
with us, talk to us, and, we can schedule a live session and, talk more about use cases and
everything.
00:46:05:03 - 00:46:29:08
Jens
And then, one more announcement. So, you you might know me from, the Friday sessions,
typically with Stefan, who's currently on, vacation. So this Friday, same time as always, we do
our podcast. We invite Dustin. Jesse and Ludwig. I don't know if Jesse and Ludwig, if you if you
want to come, you can come.
00:46:29:10 - 00:46:58:15
Jens
Yeah. And, again, we will we will talk about, cosmo connect in a little bit more. Relaxed, format.
We have more time. We talk about, like, the, the behind the scenes, how we actually build it,
why we build it, and we can talk much more about, like, log file, and, it's actually not, like, super
trivial to translate, GraphQL to gRPC, because there is some slight differences between the two.
00:46:58:17 - 00:47:01:15
Jens
Ludwig is confirming. So yeah.
00:47:01:18 - 00:47:03:10
Ludwig
Especially this.
00:47:03:12 - 00:47:27:23
Jens
Join us this Friday. It's going to be, amazing. And yeah, that's my slideshow. And then, I know
we have, a couple of questions already. So maybe I don't know, Jesse, you you are hands on
with, with the chat. And we can also look into the answered questions, because maybe we can
just pick it up for the conversation, for the benefit of everybody.
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
00:50:32:10 - 00:50:39:19
Dustin
Maybe Ludwig can you elaborate? What what is happening inside the router before it makes the
request?
00:50:39:21 - 00:51:00:02
Ludwig
Yeah. So basically we're calling the router with gRPC. We're calling the router with the GraphQL
request, and it goes through our, for our engine logic. So we're going through the whole logic
that we had in place before the whole, GraphQL logic that is doing the planning, normalization
and so on, so forth.
00:51:00:04 - 00:51:19:17
Ludwig
And in the end, we're providing, a GraphQL request to, to, one part of the engine that is taking
this request and converting it in place into a gRPC. Invocation. And this invocation will then be
sent to the subgraph.
00:51:19:19 - 00:51:21:10
Dustin
This is binary, right? This is not.
00:51:21:11 - 00:51:23:00
Ludwig
A binary protocol. Yeah.
00:51:23:02 - 00:51:28:22
Dustin
Yeah.
00:51:28:24 - 00:51:31:08
Jesse
Jacob, I don't know how to allow.
00:51:31:08 - 00:51:38:22
Jens
So we we have Sanath us here also as, as a panelist. So if you if you want to just step in.
00:51:38:24 - 00:52:01:19
Attendee
This is my audio. We're just making sure. Yeah. We hear you. Perfect. Sorry. The question was
phrased. Maybe not so. Well, typically, like you guys have highlighted, the struggle has really
been like, not everyone at the companies that is comfortable GraphQL or something to that end.
So, it sounds like at least from integrating service side, you guys have kind of the not so that
technically a team could not be aware, and we can just build a like a connection piece for them.
00:52:01:19 - 00:52:17:17
Attendee
And I guess a question is that operations has also been helpful for hiding it from the client where
like they say, what they want, we build them the operation and they query the operation without
knowing that much about GraphQL. I guess I'm asking if that stays in this version because.
00:52:17:19 - 00:52:18:10
Jens
Ecosystem.
00:52:18:11 - 00:52:21:00
Attendee
Persisted Operations. Yes yes yes.
00:52:21:02 - 00:52:54:07
Jesse
Yeah. So of course persisted operations are a way to kind of limit what the front end is able to
request from the backend. And that can limit complexity in terms of crazy, weird queries,
destroying your subgraphs with performance or whatever else. But what we've done with gRPC
is actually a bit step, step further than that. And for every GraphQL query that you might be able
to send to the router, for requested persisted operation or not, it gets broken down into a series
of RPCs which are very clean cut, just boxed.
00:52:54:09 - 00:53:08:24
Jesse
Requests for data like you might have a lookup product by ID or get user by name. It works with
entity calls, mutations, queries, all of the different kinds of operations you'd have in GraphQL.
00:53:09:05 - 00:53:33:23
Jens
Thank you to and to to to clarify one thing. So on the backend side, you could kind of say that if
you have one person who knows how Federation works. And by the way, we're currently
building a product that kind of makes it less relevant for everybody to know, how Federation
works. So but but let's talk about that at another time.
00:53:34:00 - 00:54:00:11
Jens
But let's say you have one person they can create perfectly valid, federation. GraphQL SDL, you
run the compiler, it gives you a proto definition. And now the, the backend developer, they can
really focus on. Yeah. Just implementing the, the proto. And, you don't have to, to think too
much about, GraphQL or Federation at all.
00:54:00:13 - 00:54:26:02
Jens
For, for like queries or mutations, you have like, like a root resolver, it will be prefixed with like
query or mutation. But that's, that's the, the only thing that kind of hints that GraphQL is
somehow connected to this thing for everything that is like an entity call, we name these RPC
methods, lookup whatever by whatever, like lookup the thing by the keys.
00:54:26:04 - 00:54:48:21
Jens
That's, that's the message. And then we, we send you a batch of of entity keys, like user IDs or
whatever. And you give us back users. So it's just you, you just implement a loader function
essentially. And then to your point, it's kind of funny that that you're even using Federation when
the backend devs don't want to do GraphQL.
00:54:48:21 - 00:55:09:15
Jens
And the front end guys also don't want to do GraphQL. So why why this whole thing? But I know
why. Because the entity layer is powerful. Just one thing for the future. So the first step, like I
said in the beginning, we're building a puzzle and one piece at a time. And we we we want to do
it properly.
00:55:09:17 - 00:55:38:07
Jens
The first piece, cosmo connect, is towards the backend. What we will do in the future is we will
also work on the frontend side of of the router, like there's very interesting aspects to cover. One
part is the the concept of MCP, like, LLMs. That's a very interesting API consumer. And we, we
want to make it super simple for LLMs to connect to your entity layer.
00:55:38:07 - 00:56:06:01
Jens
So to leverage the entity layer that we have built, that is one part. And the other part is exactly
what you just ask about is we have API consumers that, really like to use a GraphQL layer, for
example, with persisted operations, persistent queries. These are people who love relay or urkel
or Apollo client. And that's one way to consume the graph.
00:56:06:03 - 00:56:29:01
Jens
But another way to consume the graph is to, for example, create a collection of GraphQL
queries and turn that into an SDK, because maybe you have external partners and they they
just want to have an SDK. They, they are not interested in your, in the fact that you're using
GraphQL behind the scenes or something like that. So that's another way of exposing it.
00:56:29:01 - 00:57:04:08
Jens
And I think it would cover your, your use case. And then another, another use case is, especially
for those who built public APIs. They might want to build Rest APIs and, internally, they it's
possible that they have hundreds of subgraphs or subsystems and they want to leverage
federation or like I like to say, an entity layer to bring it all together, maybe use cosmo connect to
connect to all your systems, Kafka or whatever, but then put a Rest API on top.
00:57:04:08 - 00:57:24:04
Jens
And so in the in the future, you will see that we're, we're currently focusing on, on the backend
part. And in the future we will focus more on the on the front end part, because we, we think, the
graph is super powerful, but we don't want to force you into into how you consume it or what API
style you're, you're using.
00:57:24:04 - 00:57:27:07
Jens
Just use whatever fits your use case. I.
00:57:27:07 - 00:57:54:05
Dustin
Want to, can I say something? I want to emphasize emphasize one point. I think it's a little bit of
hidden. And Jnes mentioned that already. You can actually build MCP servers as a gRPC plugin
and expose that through, our MCP gateway without dealing with MCP specification at all. I think
this is a very underrated, feature we got for free here.
00:57:54:07 - 00:58:18:15
Dustin
And, you know, it's, it's very powerful. So, you build your plugin, you expose, for instance, on
API endpoints, you design your subgraph schema, you define, define your persistent operation
that you want to make accessible as a tool to your AI tooling. And that's that's pretty much it
without ever getting in touch with MCP. Internals.
00:58:18:17 - 00:58:25:18
Jens
What you say is the cosmo router is can also be used as an MCP server. Right. It can expose
MCP tools.
00:58:25:20 - 00:58:26:18
Dustin
Exactly.
00:58:26:20 - 00:58:51:08
Jens
And cosmo router can run plugins. So you can put stuff in the plugin, create the query. And now
you have an MCP tool right? Yep. Okay. Cool. What other questions do we have?
00:58:51:10 - 00:59:22:24
Jens
I have a question for Jesse. If I build a plugin like what Dustin just did, Dustin did his make
pnpm thing and then he had a binary. So if I'm building my gRPC plugin and I want it to, I have
my my router running in some Kubernetes cluster. How do I get this binary. Which by the way,
probably my my MacBook architecture is the wrong architecture.
00:59:23:01 - 00:59:32:04
Jens
cluster?
How do I get the plugin built in the right way into the, router that's running on my Kubernetes
00:59:32:06 - 00:59:52:04
Jesse
Right. So what we're doing right now with the flow for publishing to Cosmo Cloud and having it
pulled down by the router is what we provide is a Docker file. It's not quite the kind of normal
Dockerfile you would write to package your application into, a Linux container. It, the very last
layer, instead of, like from Debian or whatever.
00:59:52:04 - 01:00:22:02
Jesse
It's from scratch. And that's because we actually just use the image that the Docker file
produces as a container for the working directory of your plugin, including, anything it might
need resources to run. And of course, the binary that is already been compiled for its target
architecture. We do support multi architecture builds just via docker which can use Qemu, or it
can use native cross compilation support in your language which is a big strong point of go and
a couple other modern languages.
01:00:22:02 - 01:00:52:13
Jesse
But if you're using something older like C++ and you're using a compiler that doesn't support
cross compilation on different operating systems, then you can use the native Qemu support in
Docker to do your cross-platform building. And then we publish it up to our OCI registry, which is
backed by Cloudflare, storage R2 to which can then be pulled down by a native OCI client
inside the router and unpacked, sort of the same way that you do inside of a container runtime
to like a var directory.
01:00:52:13 - 01:01:14:04
Jesse
If you might have seen that inside your Docker internals. We do that process, except it's not
being run in a C group or a namespace or anything else container like at the moment it's, purely
just being run as a sibling of the router. The OCI format is just a packaging construct for us. It
doesn't, it doesn't drag in the the container dependency.
01:01:14:06 - 01:01:42:21
Jens
So for dumb people like me, I, I do what Dustin did with his plugin bootstrapping. Then I run a
WGC command and it does some cool magic server S3 things. And then somehow the the
image, the, the plugin gets downloaded by my router and the router schedules, the plugin runs
the process and everything. So I don't really have to do much.
01:01:42:21 - 01:01:53:02
Jens
I just built my plugin and run a WGC command, just like I would publish a subgraph. Somehow it
just does a little bit more of things.
01:01:53:04 - 01:02:11:10
Jesse
Yep. For for sure. From the developer's perspective, this is all completely under the hood. We
provide the Docker file. When you initialize a plugin, we will eventually support more languages.
Then go for that as well. And it's all handled for that. From there, the only thing you need is
Docker support on your building OS.
01:02:11:12 - 01:02:42:16
Jens
Okay, awesome. Well, it's been an amazing hour. Thanks again for all panelists to to join. I think
for the first time we're doing this, this wasn't so bad actually. And that's German translates to it
was pretty good. Thanks for all the attendees. Questions were amazing. We will definitely do
this again. And, just a reminder, this Friday we will have the, the Stefan and Jens good, good
thing session, this time without Stefan.
01:02:42:16 - 01:02:52:04
Jens
And, I hope to see you there and talk a bit more in depth about, customer connect and
everything. So thanks again and have a good one, ciao ciao.
01:02:52:06 - 01:02:52:14
Dustin
Thank you.