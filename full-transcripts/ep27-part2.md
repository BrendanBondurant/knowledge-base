00:38:48:16 - 00:39:13:16
Jesse
It might go down once in a while. And you can use your own Prometheus metrics.
Opentelemetry. You can do BGP whatever you want. Because it is a completely separate
process run underneath your, DNS, your service mesh, whatever you'd like, and the router just
contacts it via however you would normally want to network your services together.
00:39:13:18 - 00:39:37:26
Jesse
And that gives you total control over the deployment, the versioning, the packaging. And that's
really going to be best either if you have something complex that needs its own resources or
access to, what are they called, an AWS, like a virtual private network or something like that?
AWS has a fancy word for it. Like if you need access to rds or something that could be a good
option.
00:39:37:28 - 00:39:40:02
Jesse
But you get all this control.
00:39:40:05 - 00:40:11:12
Jens
Yeah. Got it. So we have, like the lightweight option, the plugin. I think that's that's a pretty good
option if, if the plugin just talks to another API, like it will just be IO it, it cannot use a lot of CPU
and memory, so it's fine. Just run it as a, as a plugin. That that would also be like our, our I
would say alternative to, to Apollo connectors.
00:40:11:12 - 00:40:37:16
Jens
Yeah. Connect it. It's always a problem. Is it Cosmo connectors or Cosmo Connect. And is it
Apollo connectors or I sometimes stumble okay. So we have plugins, lightweight. Just IO talk to
something. If you do some more heavyweight stuff than dedicated gRPC. Okay, we got that.
And.
00:40:37:16 - 00:41:03:06
Dustin
Okay, maybe maybe another maybe just another two points. I see I also very huge benefit in
like, local development if you just want to try something out, but also for preview, preview,
subgraph changes. So you can also create like in cosmo we have all cosmo feature flag. You
could also deploy console connect plugin and deploy that as a feature flag.
00:41:03:06 - 00:41:13:08
Dustin
And that means, you don't have to deploy another router to, to, preview your changes on, on a
QA system.
00:41:13:10 - 00:41:14:12
Jens
Okay. That's also, if.
00:41:14:12 - 00:41:35:17
Ludwig
You're starting also, if you're working on a plugin, you can just, add another main file and
converge a plugin into a service like reuse the exact same code that you have been using for
your plugin. Just have another main file that stores plugin as a grpc service and just deployed
somewhere. So you have a plugin and and a service.
00:41:35:20 - 00:42:01:03
Jesse
Yeah, that's that's really important when we talk about these two separate ways of deploying it,
the only real difference is just how the service is initialized. All of the resolvers and the whole
like gRPC innards are identical for both implementation methods. It's just whether you use our
helper to run it on the socket using HashiCorps go plugin, or whether you launch a bog standard
Http2, gRPC server over the network.
00:42:01:06 - 00:42:23:27
Jens
Yeah, but that does one thing that that Dustin mentioned. That's an interesting point. We we
have never made it like a very big thing, but imagine we have a staging environment and we
have a new use case. We want to build a new feature. We currently don't have a lot of
resources to implement it. What we could actually do is we create a feature flag.
00:42:23:27 - 00:42:49:27
Jens
So Cosmo has a thing called graph feature flags. It creates a copy of your graph and you can
replace subgraphs in it. So what we could actually do is we create a feature flag. And under the
feature flag we we just create a plugin that adds our functionality. We say, hey cursor, implement
me this plugin with some mock data, whatever.
00:42:49:29 - 00:43:10:18
Jens
And instead of deploying a service which could be like a heavyweight operation, we need ops
and whatever. Let's say ops is not here. We we could just say, oh to to this feature flag, just
deploy a plugin with some mock data and that's it. And now we have something running in
staging. So that's I really like that.
00:43:10:24 - 00:43:45:01
Jens
And then to your other point, Dustin, because this is, this is one of my main criticisms of, of
Apollo connectors, you know, Apollo connectors, you have a subgraph schema. You put some
weird directives on it, like @REST, whatever. And you, you kind of map your, your GraphQL to
REST or Http, and, the typical approach to debug problems is and and this by the way, you like
sometimes Apollo goes like, oh, it's declarative.
00:43:45:01 - 00:44:08:25
Jens
This is so amazing. And I'm like, no, declarative is really not amazing. Because the biggest
problem with declarative is you have this spec that you give the router, and now you send a
request and you open the playground and you look into the playground, what the router does.
And if the router is not doing what you hope it should be doing, what are you going to do?
00:44:08:28 - 00:44:28:20
Jens
Like how will anybody tell you what in your mess of directives you have created is wrong? You
did. I don't know. I think it's very hard to debug versus Dustin. How do I debug a plugin?
00:44:28:23 - 00:44:48:14
Dustin
Yeah, it's I mean, it's it's just, as a service. I mean, it's just a process. And you can, depending
on what programing language you have implemented, the plugin, you can just open, your
golang IDE, your VS code IDE and attach to the process. And because there's nothing special
in it, you can make a query from the playground.
00:44:48:16 - 00:44:54:26
Dustin
When it will hits to the plugin service, you will. Yeah. Debug is usually.
00:44:54:28 - 00:45:25:25
Jens
So the plugin like we, we don't distinguish between subgraph and then gRPC like it's just the
gRPC method methods. You use VSCode, and delve, and you connect to the process and you
look what's going on and that's pretty easy and to, to, to do and also other things if we're already
talking about like comparison for example, with, with Apollo connectors.
00:45:25:27 - 00:45:51:22
Jens
A lot of let's say we want to integrate an external API stripe, whatever, some API from AWS,
they all have SDKs, and SDKs, good SDKs. they do more than just calling the rest API. They
can help you with authentication signatures, whatever. Like if you want to talk to things in AWS,
you have to sign requests.
00:45:51:22 - 00:46:21:09
Jens
And there's like different requirements. You like if we're talking about like real production grade
stuff, you have to stick a lot more things into connect directives then just talking to a REST API.
In reality, like in AWS SDK, it does a lot of things for you and it can be very helpful. So with with
Cosmo Connect, you, you can just import those SDK and do whatever you need.
00:46:21:11 - 00:46:37:23
Dustin
I also think there's an architectural break. Do you really want to give your schema designers that
responsibility of integrating APIs? I think yeah, I think not.
00:46:37:25 - 00:47:10:12
Jens
No, not not even that. But my my personal pet peeve is if you. So when you design a schema
like for example, you create an open API spec. Ideally you really just define the spec or the
GraphQL schema. You just say, here is the schema. I make this an entity. And the the that was
always my idea of, of APIs is the the spec of the API should should define the contract and and
hide from me the implementation.
00:47:10:19 - 00:47:42:25
Jens
Like I don't want to leak the implementation into the contract. So and this is one of my worries
with with Apollo connectors, if you combine schema and directives to connect to REST APIs into
one thing, it it is possible that you design the GraphQL schema after your REST API because
you have this natural tendency of I mean, you have the both on the same page, so why not use
the GraphQL and follow more of the REST?
00:47:42:25 - 00:48:06:27
Jens
Because that's what you connect. And then you have to do mappings and things. And so this is
one thing. And another problem I have with these directives is I think they are very verbose. And
if you look at the schema it is not super clear what is the schema. So you have schema and you
have connectors and it's a it's a mix.
00:48:06:27 - 00:48:09:02
Jens
And I think it's much easier if we just have.
00:48:09:04 - 00:48:10:08
Dustin
Our.
00:48:10:10 - 00:48:11:29
Jens
Schema and whatnot.
00:48:12:01 - 00:48:23:10
Dustin
I mean this is a great discussion I think for a separate, good thing. But also like I also want
someone to highlight, like how do you do error handling? Right. Like it's another beast.
00:48:23:12 - 00:48:46:12
Jens
Yeah. You know, like, I it's you're triggering me. But I wrote, like, posting on all of this might, but
this is also from one of my blog posts. When, when you, when you integrate with, with, with a
well-designed REST API with a good open API spec, a good Rest API, sometimes they return
unions.
00:48:46:12 - 00:49:12:13
Jens
So there's like the one off directive or any of, and then they can have discriminator fields or
maybe a header to discriminate. And then you can also have status codes as discriminator so
that means you have like three possible options that distinguish what is actually coming back.
And then now here's my question. Let's say you have a Rest API and it returns five possible
things.
00:49:12:16 - 00:49:31:22
Jens
Do you really want to create like, like a union in your GraphQL schema that can represent the
five possible things and then map them? Or do you just want to say, oh, in my GraphQL
schema, I don't care about all these errors. They mean nothing to my front end. I hide them
completely away. Let's just focus on our use case here.
00:49:31:22 - 00:49:56:07
Jens
And if something goes wrong, we just say it goes wrong like it's broken. Like, do I need to
expose a rate limiting error from stripe to my front end? Where are the front end guy? What do I
do with, stripe rate limiting error? Like the. It doesn't matter for this here, Jesse. Any you feel
you need to say something?
00:49:56:10 - 00:50:16:11
Jesse
Yeah. If we take all this, kind of negativity about how you can use a DSL in your, in your schema
to describe an external API and you kind of just completely flip it to how we approached it. We
have a full programing language to handle all of these transformations. And, different error paths
you might want to handle.
00:50:16:11 - 00:50:36:04
Jesse
You can do anything you'd like with the response from the API you're wrapping, whether it's,
iterative transformations or, completely changing the shape. You can even join different things
together. Like, let's say you have a Rest API that has posts and authors and GraphQL expects
those two things to be in the same type. You can just merge them.
00:50:36:07 - 00:50:47:12
Jesse
It's not, mental gymnastics to figure out how to represent your business use case in some
limited language. It's, just programing.
00:50:47:14 - 00:50:58:17
Dustin
It needs some. I would argue that, hey, I can just do it in my schema and I don't have to do
anything. I mean, with plugins, you can also just, build your plugin and deploy it with the router.
00:50:58:19 - 00:51:00:12
Jesse
Yeah.
00:51:00:14 - 00:51:17:15
Jens
Which is a good, segue, plugins router. So I have my plugin. It's, probably like a go binary. How
do I get it to the router?
00:51:17:17 - 00:51:40:18
Jesse
Well, if you're using the if you're not using Cosmo Cloud, like, if you're self-hosting, you can
directly include the plugins code in the file system next to the router. You can do this via a PVC
in Kubernetes, or you can include it directly in the image. You can use sef, whatever, just put it
there in the file system.
00:51:40:20 - 00:52:17:08
Jesse
However, if you are using our cloud product, you're able to use the publish and pull workflow
that's built into WGC, which uses Docker to package up your plugin into, uses the Docker
builder to package your plugin up into an OCI image and ship it off to our registry, which can
then be pulled down by the router alongside your updated, execution config that includes the
new version of the plugin, and it's schema, and the router can automatically, unpack that image
into a working directory and run it, as it would a local plugin.
00:52:17:11 - 00:52:26:00
Jens
So you're abusing, OCI storage to, to upload plugins and download them?
00:52:26:03 - 00:52:54:20
Jesse
I wouldn't say I'm abusing it. I would say that we're one of the pioneers in the new space of
using OCI stores as generic artifact stores. There's other projects in this space like, helm uses
OCI specifically not to contain container images. And there's a couple new projects that are
being started up, like generic image registries that don't have any of the Docker Mime types in
them, which are a real detriment to this process.
00:52:54:20 - 00:53:23:11
Jesse
Is having your Mime type stuck as like tar. Docker.image or some other nonsense like that,
because the OCI spec as it exists right now is really derivative of the Docker image spec. But
the whole, the whole, underneath them. What's it called? Cloud Computing Foundation with
Linux Foundation. They're really trying to move it away from that and into just a real nice content
addressable, it has SHA checking all kinds of other nice features that you would want out of an
artifact store.
00:53:23:13 - 00:53:35:29
Dustin
I also have a question to Jesse. I think, or maybe you wanted to ask. I'm not sure, but, we didn't
we didn't build or deploy or maintain our own, Docker registry. Right.
00:53:36:01 - 00:54:02:23
Jesse
We did. It's, it's based on it's based on Cloudflare workers, and it uses R2 as the backing
storage. This allows us to deploy it, in all the regions where our customers are and provide fast
service without depending on an external service like Docker Hub or GHCR. In the future we
might have some sort of option for using your own registry, but that's, on the horizon now.
00:54:02:25 - 00:54:14:29
Jens
I think I feel much better if we don't have our own storage. Like let people from Cloudflare store
the stuff they they can figure this out.
00:54:15:01 - 00:54:17:24
Jesse
I meant using, like, GHCR or if you're,
00:54:17:27 - 00:54:49:04
Jens
Oh, yeah, I see. Okay. Well, one one last topic for for Dustin cursor. And then, to close it up, I'm,
I will do one round of what? What are you proud of? Like something you have built the last
couple of months can be Cosmo connect related. Can be anything like something you're you're
really proud of, where you say, okay, this is I built something cool before we come to that, which
will conclude our our end of this, session today.
00:54:49:04 - 00:55:17:11
Jens
We started a bit late, and we we we just drag it a little bit, but, one last topic. Dustin. Cursor. We
all we're all lazy. Developers are lazy. Nobody wants to write code that's, like someone said, at
some point, a human shouldn't do what a machine could do. And, writing glue code to to
connect to a REST API.
00:55:17:11 - 00:55:51:04
Jens
That's, that's maybe a case where, where AI could, could do some stuff. But, one of my early
experiments showed it's actually not so easy to connect or to, to implement, an Apollo
Federation subgraph with LLMs or cursor or claude code. And you have invested a little bit into,
into Cosmo Connect and it it actually works with LLMs or like how does it look like.
00:55:51:07 - 00:56:21:11
Dustin
So so right now when we, like we in the first iteration of Cosmo Connect, we, we relied heavily
on convention like we have different directories where we put the binary where you have to put
the graphql schema file in it, but you have where we store the generated files from the graph, go
to proto conversion. And this struct allowed us to define like a cursor or windsurf or claude
template that that is able to instruct how to actually operate a plugin.
00:56:21:13 - 00:56:49:09
Dustin
That means how to build it, how to generate it, how to test it. And if you if you're doing some
clever prompt engineering inside, it, it is possible to instruct a claude, claude for instance, or
cursor to, to implement an open API specification. And this workflow works pretty well. And in
this way you can actually integrate, bridge REST APIs very easily in almost no time.
00:56:49:11 - 00:57:20:16
Dustin
However, this always comes with limitations. So you also need to be able to solve use cases
like. where you have an open API specwith thousands of endpoints. Right. And this will,
obviously overwhelm, the LLM, to do things right. And for this purposes, we also have a different
product in the pipeline that allows you to to split those, graph those gRPC endpoints in, in
several, I would say, pieces so that multiple agents can run on these things in parallel.
00:57:20:18 - 00:57:39:01
Dustin
And it's not yet part of Cosmo Connect. But we are very, we are aware of that. The limitation I
would describe that the user need to solve your on your own and yeah, exciting stuff. And we,
we also, I hope also have a, good thing about that as well.
00:57:39:03 - 00:57:48:05
Jens
So we're, we're, we're looking into bringing API integration and getting that on, on autopilot.
00:57:48:08 - 00:57:57:28
Dustin
Exactly. So that someone can easily. Yeah, easily bridge an existing rest API within a day,
including tests, everything.
00:57:58:00 - 00:58:15:25
Jesse
I think one of the understated benefits of using gRPC for having your a your AI assistant write
things is that it's very easy to tell when a gRPC API is behaving within spec. It's not so easy with
a GraphQL API. If you developed your own GraphQL server from scratch, and you wanted to
make sure it was working correctly.
00:58:15:25 - 00:58:38:03
Jesse
You have to kind of try everything. This underneath this, underneath this, like, ABC, all these,
like, nested queries. You do, things that return arrays or, all these different ways of creating the
same data in order to make sure that it's doing the right thing with gRPC, there are RPCs and
they have an input type and a return type.
00:58:38:05 - 00:58:47:01
Jesse
And if they act within that spec in the kind in one test, they will do it in any circumstance and
more or less.
00:58:47:04 - 00:59:06:07
Dustin
And when we convert like GraphQL to protobuf, we also we change the GraphQL descriptions.
That means this is this will also serve as additional context to LLMs to understand the full, full
context of of your of your domain.
00:59:06:10 - 00:59:08:25
Jens
Okay. Awesome stuff.
00:59:08:28 - 00:59:12:19
Dustin
Good that Ludwig is back.
00:59:12:21 - 00:59:33:10
Jens
Then. Then we will do one, one round of something you're proud of. And then if you're, if you're,
if you're, if you think that's funny in the end, you can ask me because I was just moderating all
the time. You can ask me, like, one weird question. If you have a weird question for me, think
about it.
00:59:33:12 - 00:59:47:24
Jens
But starting with Ludwig, anything you're proud of, except like, your amazing teammates and
what we have accomplished. And,
00:59:47:26 - 00:59:49:00
Ludwig
That was actually.
00:59:49:03 - 00:59:52:28
Jens
Sort of of proud of the best CEO, right?
00:59:53:00 - 01:00:23:04
Ludwig
Of course. And then the very best CEO. Yeah. Do you get a raise now? I actually wanted to say
I was super proud of, the whole collaboration. Like, in the beginning, we had a super tight,
schedule when we wanted to have our first version released. I could not have done that alone.
And I got massive support from from Dustin and from Jesse, from other people also involved
that who really helped me with some designing things.
01:00:23:04 - 01:00:43:19
Ludwig
And really, I think the whole this whole project was, is a really fun thing. It makes me wake up in
the morning feel like, yeah, I'm really enjoying what I'm doing. I mean, that's something a lot of
people don't have when they go to work. And like, I was just another workday and I'm working.
I'm like, I'm super excited to see what's coming next.
01:00:43:21 - 01:01:20:09
Jens
Which is a great point. Like if you if you like people like Ludwig, Jesse and Dustin and like,
yeah, you if you can cope with me then then maybe wundergraph is a is a cool place because I
think we have really cool, smart people. It's it's very enjoyable. And then, to work together, we
have super interesting problems like what we just talked about, like, I, I would love to have more
time on on actually hacking on it, but, yeah, I also need to do other things.
01:01:20:12 - 01:01:28:05
Jens
Cool. Thank you, thank you. Ludwig, that was fun. And, Jesse, anything you're you're proud of
or something cool you work on.
01:01:28:07 - 01:01:46:18
Jesse
So one thing that I'm proud of for the team we worked on, on connect is that I have a nice
calendar diagram on my other screen here from five months ago. This was before any code was
written for anything here. And this was Ludwig, and I sitting in a slack huddle trying to figure out
how this is going to work.
01:01:46:20 - 01:02:07:23
Jesse
And if we look at this diagram now and how it actually ended up working, there's like nothing
different. So I think we did actually a really good job of architecting it from day one so that we
weren't, just stepping on our own feet or constantly messing up how we were going to
implement this. We weren't like vibe coding our way through it and constantly having to rewrite
things.
01:02:07:25 - 01:02:18:18
Jesse
I think we did a good job planning and executing, a product that functionally works in production,
and solves the, the use case. It was designed to.
01:02:18:20 - 01:02:49:08
Jens
Respect, like the, the, the in German, the, the the, the biggest level of appreciation. You can get
it. It's, not bad. Like, it's pretty good. Okay, cool. So you see, we, we have, we have good
collaboration. We have, good architects. Dustin. What, what any. Well, what are your highlights
of the last couple of months?
01:02:49:10 - 01:02:50:25
Jens
01:02:50:27 - 01:03:28:15
Dustin
Yeah. I have to repeat, I think, I mean, I think you can you can solve anything. I think tech is not
not not that important, but you need to. You need to have the right people. And I think this is the
most critical one. If you have people who are, curious and have the right attitude and are hungry
and then also can work in a team which is also not given, is then you have everything you need
as a CTO to operate, such an, project and, yeah, I, I tried very hard to, to, to, to, to be part of it.
01:03:28:15 - 01:03:41:14
Dustin
I did some work on the photographic library, but I was more or less like a, like a, like a rubber
duck and an architect on that side. And, yeah, the team did a fantastic job.
01:03:41:16 - 01:03:55:28
Jens
This is what you want to hear from, from a CTO who cares about, the team and and the people.
Cool. Awesome. This was a cool session. Has anybody come up with a weird question?
01:03:56:00 - 01:03:59:27
Jesse
Why did we use gRPC and not Captain Proto?
01:04:00:00 - 01:04:22:12
Jens
Oh, this is this is actually not a super weird question. So if you don't know Captain Proto, I'm
actually a fan of Captain Proto. If you, you should definitely read about Captain Proto, because.
And by the way, this was not like just the. And I didn't set this up like this is, this is free for all.
So, backstory of Captain Proto.
01:04:22:18 - 01:04:39:10
Jens
So, what did I want to say? Yeah. Cloudflare. Cloudflare workers is, using captain proto behind
the scenes. They have something it's called, what was it again? distributed object, like the
what's it called? Something and then.
01:04:39:12 - 01:04:39:28
Jesse
01:04:40:00 - 01:05:12:19
Jens
D1 D1 okay. Yeah. They have this, this cool concept of distributed objects, which are yeah. Like
like singletons and they can move around the globe. And essentially they are kept in proto
objects. And the cool thing, like Captain Proto is like a different, like a different way of thinking
about network programs because instead of instead of, calling a service and it it gives you
something back.
01:05:12:19 - 01:05:41:07
Jens
It's more like you have a distributed object that lives somewhere and you can call functions on it,
and you can also chain function calls. You can say, I don't know. Show me the, the prices of
products. And when you have the prices, then give me, I don't know, the shipping estimate or
something. And you can actually send this in one message as a chain and it will operate on this
distributed object one by one.
01:05:41:07 - 01:06:00:28
Jens
And then it will give you back the response. So you you can send multiple operations to this
object as one request. And then you get back the response. You don't have to go like multiple
roundtrip. So capn proto pretty cool. Why did we not use it? I actually wanted to use it in the
beginning, but I was worried about ecosystem.
01:06:01:00 - 01:06:34:14
Jens
So I thought like if we do like an exotic ecosystem thing, then yeah, maybe we, we end up with,
I don't know, like not many people will adopt it. So I thought, okay, let's go mainstream, let's go
gRPC. And that's that's fine. Good. Then last question from David Stutt. Why did you come into
daily yesterday with a huge cake that you finished by the end of the daily.
01:06:34:16 - 01:06:55:00
Jens
I don't know, like if you have. cake. You want to eat it, right. So why did I come? I come I came
in to the daily because my my mother in law, she's the absolute best. She made cake, and I like
cake, so I, I yeah, I had my cake and eat it too. Exactly. I think that's awesome.
01:06:55:01 - 01:06:56:21
Dustin
Closing words.
01:06:56:23 - 01:07:18:07
Jens
Yes. Okay, so next week our beloved Stefan is back again. But I have to say, this was an
awesome session we had. Very good. I don't know if you see it, but we had very good numbers
in, in viewers and people stayed. So it was interesting. That's a good learning, Jacob. I hope
you can clip some stuff.
01:07:18:07 - 01:07:39:27
Jens
Hopefully we we have some some good rants or whatever. Guys. Ludwig. Jesse, Dustin. Thank
you so much. This was a good session. And Dustin how do I do it again on sec, I Dustin do you
know what the good thing is? Jesse do you know what the good thing is?
01:07:40:03 - 01:07:44:16
Dustin
A podcast that we are online next week.
01:07:44:19 - 01:07:48:12
Jens
Thank you. Ciao Guys. That's it.
01:07:48:14 - 01:07:49:10
Ludwig
See you.
01:07:49:12 - 01:07:49:21
Dustin
Bye