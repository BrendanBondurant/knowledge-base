00:00:24:17 - 00:00:52:05
Jens
I. Hey, everybody. We're live. Today I do. I have to do the intro because Stefan is not here, and,
I'm not prepared to do it. I'm just winging it. Yeah, it's it's good to be, back on the stream. We
had a webinar this week already with the same round, where? Yeah, we were ten minutes late.
00:00:52:07 - 00:01:21:05
Jens
David, because we we needed some extra time for preparation, the backgrounds and
everything. So. Yeah, but it's good to be live again. Like, you know, typically we it's just me and
a good looking person, Stefan. But because we don't have Stefan today, we need to to mix
together three other good looking people. So, today, here we have, Ludwig.
00:01:21:05 - 00:01:38:14
Jens
Jesse and and Dustin and, Yeah, maybe we can. We can get a little intro. Hi, Ludwig. And,
you're you're working on the, like what? What's what what's what have you been working on for
the last couple of months?
00:01:38:16 - 00:02:03:00
Ludwig
Yeah, I've been working a lot with, making graphql into some kind of reflected gRPC messages.
So I've been working on on the engine part that would translate GraphQL messages into
dynamic protobuf messages and send them over to our gRPC services or plugins. Regarding on
this.
00:02:03:03 - 00:02:22:15
Jens
It's actually an interesting topic, and we will talk about this a little bit later. In the beginning we
thought, oh, it's gonna be easy. We just connect GraphQL to gRPC and then we dig a little bit
into this topic and we we figured out you can't easily translate everything and the messages.
And there are there are some problems.
00:02:22:15 - 00:02:30:16
Jens
But we will we will get to that. Yeah. Also on the stream today. Jesse. Hi, Jesse. How are you?
00:02:30:19 - 00:02:32:15
Jesse
Hello. I'm good.
00:02:32:18 - 00:02:36:12
Jens
What's your what's your contribution to Cosmo Connect?
00:02:36:14 - 00:02:51:27
Jesse
I worked a little bit in the very early stages of how we were going to map, the gRPC data types
to GraphQL ones. And I also worked pretty late in the project on how this integrates with Cosmo
Cloud. And your, very managed system. If you're using.
00:02:51:28 - 00:02:55:26
Jens
You're responsible for the bad naming of proto graphic, right?
00:02:55:28 - 00:02:58:28
Jesse
Yes, yes I am.
00:02:59:01 - 00:03:23:28
Jens
If anybody comes to the Cosmo monorepo and, thinks about who came up with this shitty name,
it was Jesse. But by the way, funny, funny thing, we we also have dustin here. Oh. You change
to cofounder. So you're now also a cofounder? Not just to CTO. That's good, but, Funny story.
So, that's it.
00:03:23:28 - 00:03:44:27
Jens
You're you're intro. How did you come up with the name of Cosmo? Because it's so funny when,
when when we created Cosmo, it was. It was more like. So we were on, on a retreat in
Netherlands, and we had to pivot. So that's like, a long time ago, I think more than two years.
Two and a half years, a bit more or maybe three years, I don't know.
00:03:44:27 - 00:04:10:25
Jens
We're so old now. And two weeks after the retreat, Dustin was like, hey, I have prepared
something. And by the way, it's called Cosmo. And this is so weird that you can talk about this
because at the very beginning I thought, that's a bit stupid. Like, who would call it Cosmo? Like
call it cosmos or something, but for whatever reason, like, Dustin said, it's Cosmo.
00:04:10:25 - 00:04:33:12
Jens
We we we kind of settled on Cosmo and, also funny anecdote. We have one investor.
Sometimes they they, they they help us. They like, we we meet with them and, and and they
spell it in the very they, they always say cosmos and we, we always lose it. It's, it's so weird, but.
Yeah, Dustin
00:04:33:18 - 00:04:41:15
Jens
Great to have you on the on the stream. How did you come up with the name of Cosmo?
00:04:41:18 - 00:05:02:02
Dustin
To be honest, I wouldn't. I wouldn't need to make up no story. But, it it's it's I don't know, it's, You
need to come up with a short name which which sounds appealing to people. You need to do
you need also a free domain, which is very important. But, it's I think it also needs to be a little
bit inspirational.
00:05:02:02 - 00:05:23:20
Dustin
And like, Cosmo is like, it's it's broad. It's it's it can mean anything. But it also does not limit you
in your imagination of what it can be. And it's Cosmo is is is big. It's it's unlimited. And, I think it
would be a great, great term of covering our goals and our, our ambitions.
00:05:23:22 - 00:05:48:25
Jens
Yeah, that that makes sense. Well said. It's also, for example, one of the reasons the company
is called WunderGraph is I, I, I kind of liked, the name of graph. I didn't want to have it GraphQL
and I, I don't know, somehow I wanted to have something German in it because WunderGraph,
it has German roots like Dustin and I and Bjorn.
00:05:48:25 - 00:06:23:21
Jens
We're from Germany with a sprinkle of Stefan from Miami and, yeah, it's, imagine your company
is called something GraphQL. And you kind of realize that you want to enter different markets.
Now. Now you have to tell people why, why why is my MCP server from something GraphQL
company? And I never wanted to have that kind of situation.
00:06:23:21 - 00:06:54:14
Jens
So that's why we call it wonder. WunderGraph can be anything, but somehow it sounds German
and graph. Is cool. And so anyways, here we are. We launched Cosmo Connect this week. We
had a webinar. It was pretty good. It was, I think, the best webinar we ever did. And it was the
first one. And yeah, maybe we can talk a little bit about what what what is Cosmo Connect and
why we why we built it.
00:06:54:14 - 00:07:15:16
Jens
And, what were the challenges and and, what what what's actually behind the scenes? Like how
how does it even work? And, then Cosmo Connect is actually multiple things you can speak.
instead of speaking to a GraphQL subgraph. You can speak to a gRPC subgraph, it can be a
dedicated service, or it could be a plugin.
00:07:15:21 - 00:07:49:15
Jens
And maybe we also want to talk about what is a plugin and what distinguishes the two. When
would you use a plugin? And how does the plugin even work? Because the code needs to
somehow get to the router. And I think that's a pretty interesting story because, Jesse, having
worked at Fly before, he figured out, a pretty cool, like, pretty cool way of of, putting together the
stuff for a plugin into an OCI thing and then pushing the OCI thing into, into.
00:07:49:20 - 00:08:07:00
Jens
So I don't know, you need to tell us. Okay, where do we start? What is what is cosmo connect
and why did we build it? Please don't everybody speak at the same time? Do I need to point
fingers or who likes the question?
00:08:07:03 - 00:08:28:08
Dustin
No, I like it. I mean, our, initiative, our goal. I mean, we love, many great customers. And what
we have seen as a pattern is people understands the benefits of a super graph. However, not
every team can adopt it because it's it's it's a learning curve to adopt graphql and doing
GraphQL. Right? It's it requires different technology.
00:08:28:08 - 00:08:54:22
Dustin
You need to adopt to a subgraph framework, which also has its its quirks and the biggest factor
is you're probably already have established an ecosystem and a service that you don't want to
change because it's working fine in production. So how can we bring those people into the
super graph so they can benefit from all these, these things like analytics, breaking change
detection, schema collaboration.
00:08:54:25 - 00:09:17:13
Dustin
And then I think the we also got great feedback from, from a customer. And I think one of the
solution was to, to remove GraphQL from the backend side, because people believe and also
understand the benefits of on the consumer side of the front end side. And then it was very, I
would say, a very natural fit to say, why not using gRPC?
00:09:17:15 - 00:09:51:02
Dustin
Because gRPC is is so established in the industry. It's, it's it's known for its, performance type
safety and also easy compatibility with the ecosystem and programing languages. And then we
thought about like, why not creating something that can translate GraphQL to gRPC. Then we
could leverage all the benefits of the gRPC itself. And yeah, it's so that people can purely focus
on business logic on implementation and bring in that way as an existing Rest API.
00:09:51:05 - 00:09:54:18
Dustin
SOAP API into the super graph.
00:09:54:20 - 00:10:23:00
Jens
Yeah. And if I remember correctly, in the beginning we were we were talking a little bit about
what are the possible technologies. And then well one thing I keep seeing is people keep
coming up with, use cases where, where they think WebAssembly would be amazing. And we,
we also had, like in the very beginning, we were talking about like, different approaches, like
how how could you actually do it?
00:10:23:03 - 00:10:55:17
Jens
One, one idea was also WebAssembly. But we, we didn't go for, for WebAssembly. Like, well,
let's and I ask everybody in the right, like, what's your take on like will WebAssembly ever be
like like the standard in extending something like a router or like why why did we go for, for
gRPC and and in general how you think about like, extending like a binary with custom
customer stuff.
00:10:55:19 - 00:11:25:04
Jesse
I can talk about this a little bit. I think that WebAssembly is great. And using things like shared
objects and DLLs is great, like the new go plug in system that's like officially a part of the
toolchain. However, one of the main goals of Cosmo Connect was to take the onus of the
complexity of importing graphical frameworks and all this subgraph nonsense and just make it
easy to do what you've always been doing, which is import protobuf Proto C Protoc gen
gRPCco.
00:11:25:04 - 00:11:49:15
Jesse
All these packages that everyone's used to and be able to federate those into the super graph.
And if we bring all the complexity of developing WebAssembly programs into that to replace it, I
don't think we've made much of a stride at all. There's issues with concurrency and language
support and all kinds of little gotchas with WebAssembly right now, especially if you're not using
a web browser as your runtime.
00:11:49:17 - 00:11:53:09
Dustin
So and you would also need to add your own SDK, right?
00:11:53:12 - 00:12:18:12
Jesse
Yeah, you absolutely would, because there's pretty much nothing available in WebAssembly.
There's no standard library. So you would have to provide all your own bindings to the
WebAssembly engine. It just a whole lot of extra new, like it's all greenfield for anyone
developing these things. And as opposed to gRPC, they have to learn this whole new
technology and how to work with it.
00:12:18:14 - 00:12:20:29
Jesse
And some languages, it's even outright broken.
00:12:21:01 - 00:13:03:14
Jens
So whenever someone comes up with like WebAssembly, like being a go dev, like, I think we all
tried WebAssembly, probably. And if you try out using WebAssembly and you're using a
garbage collected language and you know a little bit about architecture of programing language
and stuff like that, the first thing you kind of stumble into is, okay, if I want to get some
information into a WebAssembly thing and then call a function and get some other stuff outside
of the WebAssembly thing, what I have to do is I because very simply, the way it works, it
doesn't give you like garbage collection or something.
00:13:03:18 - 00:13:28:29
Jens
You have to allocate space space somehow get something in like copy it into the thing, into the
runtime, and then do something and copy some results into some other space and then get it
out. And I was always like, I don't know, I, you know, one thing I really like about go is and then
you can, you can, have opinions on, on rust and non garbage collected languages.
00:13:28:29 - 00:13:52:06
Jens
But what I really like about garbage collected languages is, I create an object and I do
something with it, and when it goes out of scope, then that's fine. And I don't have to think about
memory management and stuff because lots of other problems to solve. with WebAssembly You
have to think about this somehow, because you can't just randomly allocate stuff and not care
about things.
00:13:52:06 - 00:14:13:06
Jens
So, and I had discussions with the Dustin initially I wanted to go for WebAssembly, and he
quickly came up with alternative ideas. Maybe you want to to share some of your thoughts and
how we ended up using what we're now using, which is a pretty cool library from HashiCorp. I
think.
00:14:13:08 - 00:14:38:20
Dustin
Yeah, I think, I think Jesse, summarizes pretty well why we why choosing webassembly wouldn't
have been a good idea in in that, case. Then we explored like, for instance, like go also has a
capability to, to produce plugins, but those plugins only work, I think, on Linux. Right. And those
are like compiled. I think,
00:14:38:22 - 00:14:56:29
Jens
Libraries. go plugins are horrible. Like, yeah. One of the biggest problems is you must use the
exact same package versions of every dependency in the main binary and the plugin and yeah,
that's not fun.
00:14:57:01 - 00:15:21:15
Dustin
Yeah. So, so, first of all, we talked about WebAssembly and then we, then we I mean, the, the
whole, the whole initiative was driven by the idea that people doesn't need to recompile the
router. That was one of the design goals. So then WebAssembly, we figured out then for
obvious reasons, we didn't do this. Then we thought about like an and co processing model
where the router can spawn processes.
00:15:21:18 - 00:15:47:09
Dustin
Then we checked I think go plugins, which is obviously not a good choice. But then if you
research a little bit about go plugins, you will always find the HashiCorp library as the first,
search result. And because its so widely adopted also in HashiCorp vault and an all I mean a lot
of many HashiCorp product which which are serving millions of users per day.
00:15:47:12 - 00:16:11:03
Dustin
For us it was a good signal like it's production grade and it would give us all of these benefits we
are looking for, for, for instance, like, one of the goals of, of the, of plug of the plugin architecture
is also that we want to bring that aha effect. I mean aha effect immediately to a customer so
they can build things without redeploying services.
00:16:11:03 - 00:16:35:15
Dustin
It everything should be self-contained in the router. On the other hand, we also didn't want to
destroy the, the capability of deploying, deploying these services independently for, for high,
high traffic scenarios. So I think that was the perfect match because at the end is it's just a
gRPC service. And in case of a plugins, it is it has a different, transport.
00:16:35:17 - 00:16:52:18
Dustin
And in case of, gRPC services, it's, it's really handled as a separate, subgraph. So, yeah. Then
that was I would say the, the decent decision metrics in that at the time.
00:16:52:20 - 00:17:28:10
Jens
Okay. Well well said. So cosmo connect. I have, I have a super graph and I have a router and in
this super graph I have one subgraph. I have defined it as, like I have a schema, like, like Apollo
Federation subgraph spec compliant subgraph schema. So that's one thing I have. And then I
have my router and I have my gRPC proto thing.
00:17:28:13 - 00:18:08:00
Jens
So now if I, if I send, a request to the to the router, and we get some data from a GraphQL
subgraph and we get some data from a gRPC subgraph, what what happens? Can I like, how
do you translate between GraphQL and gRPC? Because if I'm like a regular gRPC user, the
way I'm used to to doing gRPC is I have this proto stuff, I run some proto C thing and it
generates code, and then I have a proto, gRPC server.
00:18:08:04 - 00:18:29:00
Jens
But in the case of the router, what does it just said this. We are not recompiling. We're not like
when you change your subgraph, you you don't have to rebuild the router with new proto
definitions. Somehow we're building these messages on the fly. How does it work?
00:18:29:03 - 00:18:58:07
Ludwig
So basically you start off with designing your graphql schema, just the way it's always been
before you think of a schema that not matches your architecture or fits into your existing
architecture. And then after you're done with your with your graphql schema, you can use, our
fancy library proto graphics in combination withour CLI WGC. And you just, you use the schema
as an input and you generate protobuf out of it.
00:18:58:07 - 00:19:23:24
Ludwig
So you get a protobuf schema, and you also get, get a mapping file. So, so basically because
GraphQL and protobuf are quite fundamentally different, there's also like different syntaxes,
different ways of handling types. We use we use our protographic library to, to find the best way
to, to match between the two environments.
00:19:23:26 - 00:19:54:07
Ludwig
So, we're generating a proto schema from, from the graphql schema. The user can then take
the schema and just generate their proto bindings from it. On the other hand, when we're
composing, all our graphs into a route execution config, we're putting together all the information
that are required. So, we're getting the, the graphql schema, which is important for an engine to
understand what types are the, available in my my graphQL sense.
00:19:54:07 - 00:20:26:26
Ludwig
Because I see I'm still talking graphql to my router while I'm talking gRPC to my, to my service.
So my router level I still need to understand GraphQL, but we only need the schema for that.
But on the gRPC level, we just need the, the protobuf schema. And we can compile this
protobuf schema using, library, and convert it into an ast and then and then use all the
information that we can get from it, like the type descriptors and whatever, and build up
dynamic, proto messages.
00:20:27:02 - 00:20:54:22
Ludwig
So, while we're getting GraphQL requests, we can just take this request and convert it into, into
protobuf messages dynamically and then send them over to, to our subgraphs our gRPC
subgraphs. And it using a mapping file will allow us to, to retain the information that we get from,
from the from the original GraphQL schema to the protobuf schema to to get a mapping
between the type and names.
00:20:54:25 - 00:21:23:02
Jens
Okay. So you have a mapping, you have the message descriptors. And there is like a dynamic
library. It allows you to to create those messages on the fly. So you take subgraph requests. You
transform them into into gRPC proto messages sent them, get them back and all without the
compile time step. What what were the, were there any challenges?
00:21:23:03 - 00:21:28:09
Jens
Is it easy? Is is there something that to that you learned in doing this.
00:21:28:12 - 00:21:53:23
Dustin
Ludwig mentioned the mapping file. And one thing I mean, the obvious reason why we, we
choose this approach and why we started, thinking about this, like in proto, the feed order is
significant. It's a binary protocol. So you cannot just move fields around. Otherwise it's no longer
binary compatible. In GraphQL you can move arguments, you can change fields.
00:21:53:23 - 00:22:02:00
Dustin
All the it doesn't matter. That means we have to retain retain this information through the
conversation conversion process and then be stored into the mapping file . So and are.
00:22:02:00 - 00:22:10:08
Ludwig
You mixing up two things right now. We have the mapping file and We have the log file, the log
files for the for the field order and the mapping files just for the naming.
00:22:10:10 - 00:22:11:28
Dustin
Okay.
00:22:12:00 - 00:22:13:05
Jens
Dustin.
00:22:13:07 - 00:22:17:01
Dustin
Because good that you mentioned it.
00:22:17:03 - 00:22:17:14
Jens
Yeah.
00:22:17:16 - 00:22:20:23
Ludwig
I think you can talk about the log file later.
00:22:20:25 - 00:22:48:07
Jens
Okay. Because cosmo is such a big space. Yeah. The there's a lot of moving parts. Yeah, but,
we talk about the, the log file later because, I learned something from Dustin in this, doing this, I,
I didn't know there is a cool keyword in, in, in, in gRPC. It's called reserved.
00:22:48:13 - 00:23:18:01
Jens
I, I didn't know about reserved. And, Dustin pointed me towards it. It's pretty cool. But we talk
about this this later. Ludwig. And anything in your process of, like, taking subgraph requests that
are like, GraphQL over Json, over HTTP, turning that into gRPC, anything that was hard or
something you learned or anything you want to share.
00:23:18:03 - 00:23:57:12
Ludwig
I would say the whole project was a big learning process for me, because when I started with
this project, my my knowledge in our engine repository was quite limited. I've been mostly
working on on Cosmo Router features. The engine part was always like this very complex
planning parts. No one understands. When I started working it, I got a lot of support from,
especially, like from Sergei who, who showed me a lot of things how to use the libraries in
different, different packages that allow me to, traverse, for instance, GraphQL requests,
schemas.
00:23:57:12 - 00:24:25:05
Ludwig
And, what, what kind of metadata we already have available. So, I would say, the first challenge
for me was like getting into, understanding how the engine works internally. So, so I started
writing a visitor. The way that we're doing it, usually in our engine code, is we're writing a lot of
visitors, do, validation, post-processing, post-processing, and so on.
00:24:25:07 - 00:24:48:12
Ludwig
And I started with a simple visitor that would take a simple request, a simple GraphQL request
like, create user or create users where one field without arguments and just convert it into a
very, very simple, gRPC request. And after I was done with that and after I had my initial
moment, my, wow moment, okay.
00:24:48:12 - 00:25:09:09
Ludwig
It works. So I started digging deeper. I started, with, okay, let's start. Let's start with different
data types. We're supporting different data types. And we need to support like scale data types
in GraphQL. We need to support like the base, the base types in, protobuf. They also
sometimes translate differently.
00:25:09:09 - 00:25:33:26
Ludwig
For instance, in GraphQL, we don't have a 64, bit integer. So, we only have 32, 32 bits. But
instead the float in GraphQL is actually a double precision float in, in protobuf. So we would
translate float to double. So so I started digging deeper and deeper and I, I just fell on top of it.
00:25:33:26 - 00:26:08:14
Ludwig
And I always had in mind that I want to build something that kind of keeps it simplicity, while still
having, like, a good, way of using it, like, provides a good developer experience. I wanted to
keep it super simple. Not not making making it super complex with nested messages and, like
very nested complex types. So I wanted to keep it as close as possible to the original design of
the GraphQL schema.
00:26:08:16 - 00:26:38:21
Ludwig
So, yeah. So it was a, gradual process from starting, super, super low and with basic types and
then going over to arguments, then, thinking about Federation directives like, how can I build my
first entity, look up and then at some point we reached a point where we started working with
lists and, I was like, oh my God, this is this is very tricky because in protobuf, for instance, you
can't have lists of lists.
00:26:38:24 - 00:27:03:01
Ludwig
The repeat is only, available for, for a single type. So you can't do repeated repeated type. So
we have to come up with, with the way of translating nested lists into something that, that
protobuf can understand. And also on the engine side, we need to handle different ways of
handling lists because you can have a nullable list, you can have a non nullable list, you can
have a nullable of non nullable lists.
00:27:03:01 - 00:27:17:22
Ludwig
And was kind of interesting. So, so we had to do a lot I had to do a lot of, logic bouncing
between the two. The two designs.
00:27:17:24 - 00:27:24:03
Jens
And are you following the the semantic non-null discussion in the GraphQL community?
00:27:24:06 - 00:27:26:17
Ludwig
And there's an ongoing discussion.
00:27:26:20 - 00:28:00:03
Jens
Yeah. Like one of the biggest problems we currently have in the GraphQL spaces, if we request
a field, and, and it's nullable. Do we get back nukk? Do we get back nothing. Or an error with
null and does null mean nothing or null or like does null have a meaning or is it an error or null
or we we don't always know.
00:28:00:06 - 00:28:32:11
Jens
But for example, let's say you make a subgraph request and it should return a nullable field like,
I don't know, best friend. And let's say you don't have a best friend because nobody likes you.
So your best friend is null. But it's also possible that, so in that case, the the server, the
subgraph returns null. But what if the server has an error and returns null?
00:28:32:13 - 00:29:02:05
Jens
How do you distinguish? And then. So the stupid thing is we we don't have a way in Json. Like,
you know, sometimes I feel like Json should have like undefined, like, you know, something is.
And then I kind of like this in JavaScript. In JavaScript, you can say something has a value, it's
undefined or it's null, because then you can express that we don't have something with null, like
the value is actually null.
00:29:02:05 - 00:29:27:02
Jens
And with undefined we can say there is nothing. And but that's a different but okay, that's a
different topic. I also want to talk about, the log file with Dustin. And then later on, I want to dive
a little bit into the topic, of, OCI, like Jessie does some, some really cool stuff with, with OCI.
00:29:27:04 - 00:29:48:10
Jens
Just one quick question, Ludwig. Because, this is something I stumbled into a while ago. Are
you supporting BigInt? Because a while ago, I, I realized, BigInt, you cannot represent it in Json
like a number. It's actually in Json. It's a string. Do you. Have you ever thought about BigInt in
the context of your project?
00:29:48:12 - 00:30:20:11
Ludwig
In the context of my project. And, so we only have INTS currently, which are 32 bit integers in, in
protobuf, The idea of how to handle like bigger ints would be to use a float instead. So you can
use a float to, to have a, 64 bit integer if you wanted to. We still have like a floating point
number, but if you, if you just, providing an int, you just get an integer without a floating point if
you pass it properly.
00:30:20:13 - 00:30:33:11
Ludwig
So that is I think that is the idea in, in GraphQL. At least when, when I read through different
posts, people would always recommend to use float instead of an integer.
00:30:33:13 - 00:31:01:17
Jens
Yeah. But by the way, just remember like we have David here. So if you want to trigger David,
someone can just say something wrong about Federation or composition and, just for fun.
Because he wasn't active on the chat for a while, but, okay. Dustin, very early on, I think it was
you who came up with this idea, or we were testing and we were.
00:31:01:23 - 00:31:31:28
Jens
We were trying odd things. And I kind of vaguely remember I was your rubber duck. We were
playing around with Cosmo Connect in the early days, and we. We realized, like, Shit, we we
have a problem. Like, it's it's not gonna work. Like, we quickly found the solution, but there was
a severe problem. Because you can do things in GraphQL schemas that you definitely shouldn't
be doing in gRPC, right?
00:31:32:01 - 00:31:35:13
Jens
Yeah. So. So we learn this is life, right?
00:31:35:13 - 00:32:11:17
Dustin
Otherwise, I would say cut my previous sentence and put it put it into this moment. No. Yeah. I
have to repeat myself like, in, in, in, GraphQL, the order of fields arguments is, is not significant.
So you can play around it doesn't matter for semantics. You can get the same result back.
However in proto the the the field order is significant, that means if you change a field order in
GraphQL, we also need to, be backwards.
00:32:11:17 - 00:32:43:16
Dustin
We need to produce the same, proto structure, in proto. So, and, in order to retain this
information, you need some sort of. Yeah, you need to store that information somewhere. And I
honestly, I don't remember anymore what, what other solution we approach. But, this was, I
would say the yeah. The I mean, if you know, of, npm log files and stuff, that was one of, that
come up in my mind immediately and we've, we've followed this approach.
00:32:43:16 - 00:33:24:13
Dustin
And so if you compile something from proto to, something from GraphQL to proto, it will not just
create this mapping file Json, but but Ludwig mentioned which contains the type mapping, but
also the you also produce a service proto doc Json file, which has information of, the field order.
And when you, when you change a field in a graphql schema, we also use that you mentioned
the reserved, reserved, directive to, you know, to continuously, make the, proto, message
compatible with your, with your previous changes.
00:33:24:13 - 00:33:27:15
Dustin
If if it's not a breaking change.
00:33:27:18 - 00:33:50:02
Jens
So let's say I create a user type and it has id and name. So then ID in the, in the proto definition
it would be like index one and name is index two. Yeah. So let's say I now remove okay. That
would be a breaking change on, on the, on the GraphQL side. But let's just say we do that.
00:33:50:06 - 00:34:01:24
Jens
index.
So we remove the name field. You would then put the the index two in the proto as the reserved
00:34:01:26 - 00:34:07:02
Dustin
And it would count one level and assign three to the to the new field.
00:34:07:05 - 00:34:19:25
Jens
If we add a new field. So if we then add like I don't know, foobar, it would automatically get the
index three so that we're not mixing up index two and three. Yeah.
00:34:19:27 - 00:34:40:19
Dustin
And the result also supports ranges. So, the protograph library automatically identify if we are
and a like we we made multiple changes over time. So it for for efficiency reason it instead of
having multiple reserve statements it would just use reserve from 2 to 4. For instance. Yeah.
00:34:40:21 - 00:35:08:13
Jens
Okay cool. So we have our query. It goes to the router, the router does magic query running. But
by the way, crew planning, it's a, it's a topic on, on on day one. God, Sergei and I understood
the group planner. Now it's just God.
00:35:08:15 - 00:35:32:01
Jens
No, no. For you, the the funny thing about our query planner is, every time I have to onboard
someone like I. I wrote parts of it, and, I'm, I'm, I'm more guilty of contributing to the to the
execution. But every time I have to onboard someone to our graphqlgo tools, it's it's like, like a
little, like a little birthday party for me.
00:35:32:01 - 00:36:05:06
Jens
Because where I feel like a squirrel, you know, I look into the code base and I find things. I'm
like, oh, interesting. This is how we did it. And, yeah, like the the code base is just so insanely
big. It's it doesn't fit into your head. It also doesn't fit into an llm and llms that's the topic I want to
pick up later because, Dustin did some amazing stuff with, with integrating cursor workflows into
the into this whole plugin architecture.
00:36:05:08 - 00:36:26:19
Jens
But first we need to talk a little bit about because we have plugins and we have like dedicated
gRPC services. So so that's one thing. And then maybe we can we can distinguish like what
what when, when, when we talk about Cosmo connect. Like what what what is what do we
mean by a plugin and the dedicated service.
00:36:26:21 - 00:36:43:00
Jens
How do we distinguish the two. And then we want to talk a bit with with Jesse about like what
are we doing with the plugins and how do we handle it. So who who explains to us the
distinction between plugin and dedicated grpc service?
00:36:43:03 - 00:37:12:07
Jesse
Sure, I can, I can take this one. When you're developing your your grPC connect plugin, you
have two options for how you want to build it and deploy it. So the first option, which is kind of
like almost, almost serverless like functions as a service, is to, use our, our compatibility library
from router plugin. And you can build it using our CLI and ship it off through Cosmo Cloud or on
the file system.
00:37:12:07 - 00:37:26:14
Jesse
And the router runs it as a subprocess, sort of like it's acting as, a supervisor. And that means
that it's running right next to your router and it's communicating over a socket, not over the
network. So it's very low latency. But what.
00:37:26:14 - 00:37:28:10
Jens
You use a socket.
00:37:28:13 - 00:37:32:04
Jesse
Well, it depends on the operating system, but like a pipe.
00:37:32:06 - 00:37:34:16
Jens
Okay. So like Unix domain or whatever.
00:37:34:19 - 00:37:59:04
Jesse
Yeah. It would be Unix on, on a Unix system or like a Fifo pipe on windows. And that's a great
option if what you're looking for is just a lean way to deploy something thin and you don't, you
aren't too concerned about like resource consumption or really in-depth monitoring or doing
other very process level control over your plugin.
00:37:59:06 - 00:38:27:18
Jesse
And it's not really gonna have any downsides in the long term if you're not needing any of those
things, because the only real challenge that you'd run into is either your your platform team
doesn't want you running processes inside your container that are getting forked from a source
control they don't trust. That's one reason you might want to go with the the other option, which
I'll get to, or you want to allocate resources like per pod or per deployment specifically for your
plugin.
00:38:27:20 - 00:38:46:24
Jesse
So if your platform team gets mad at you, the other option is to develop it as a completely
separate gRPC service, same as you would for any other microservice architecture which can
be deployed any way you would deploy any other thing, on your infrastructure, it can go on fly, it
can go on Lambda, it can go on Kubernetes.
00:38:46:25 - 00:38:48:13
Jens
please not on fly.