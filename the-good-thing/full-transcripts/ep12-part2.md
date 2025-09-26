00:31:44:03 - 00:32:12:23
type: podcast-chunk
Jens
You can easily refetch data and everything. By the way, one one thing I'm, I'm going on a
tangent on my tangent, but, we we are intending to bring native support for Relay to Cosmo
router because I personally like this. There's no value in doing it. Well that's maybe well, it's not
like we're not making money from doing it because it's just open source.
00:32:12:23 - 00:32:41:20
Jens
But you know, sometimes I want to do things because I think they are right. And I'm running a
company. But also, I don't know, I have a feeling for how should things work. And I think, one,
one thing that Federation, or at least our implementation of federation should, should have like
native support is relay. So what we're, you know, in relay you have this node interface.
00:32:41:20 - 00:32:44:16
Jens
Do you know what the node interface is.
00:32:44:16 - 00:32:48:22
Stefan
I don't so feel free to explain it for the audience because they might not as well.
00:32:48:25 - 00:33:16:04
Jens
So if you have a front end and in your front end there's let's say you have like a, like a feed and
you have a feed item and now you have a list of feed item things. And in the front end you have
a normalized cache of feed item things. Awesome. And let's say someone clicks like so. Now
that means we need to we need to refetch the feed item to show the new like or something.
00:33:16:04 - 00:33:43:09
Jens
Right? Yeah. And if you have, if you have a GraphQL API that has an entry point or a Rest API
that gives you like /feed or like the feed field that returns a feed, you have a problem because
you cannot re fetch that one item in the feed. You can just fetch the feed. And so over fetching,
ooh spicy take.
00:33:43:12 - 00:33:44:03
Jens
00:33:44:05 - 00:33:47:06
Stefan
So it is spicy.
00:33:47:08 - 00:34:21:06
Jens
Yeah. Where was it. Relay refetch. Okay. So in relay, that's a pretty cool concept. It's this node
interface and the node interface. It means that, you can send a node ID. So like a unique
identifier of a thing, you can send it to the server. And the server will re fetch the thing. And so
instead of fetching the whole feed you can re fetch the feed item just by giving the server an ID.
00:34:21:09 - 00:34:22:01
Stefan
Okay.
00:34:22:04 - 00:34:48:26
Jens
Yeah. That's pretty like it's a, it's a great concept and it would be nice if you can just support it in
Federation. But there's a problem because you have entities theres a problem and an
opportunity. So you have entities and you have this node ID. And so if you have a node ID the
problem is you you take the node ID and you figure out what kind of entity is it.
00:34:48:26 - 00:35:13:18
Jens
Because it can be many things like all entities. So it can be whatever. So you figure out okay, it's
a feed item. And once you know it's a feed item, you need to know in which subgraph this entity
lives. So just by sending a node ID to the router, the router doesn't yet know where to get it
because the router like how should you know?
00:35:13:20 - 00:35:40:13
Jens
Like if it was an entity then we know, okay, it's an entity. We know what is the key. So we can
jump to the subgraph and get the entity by the key. So what we need to build is like a
mechanism into the router that understands how to turn a node ID into an entity. And then once
the router has an entity, it can fetch from the right subgraphs to the stuff.
00:35:40:15 - 00:36:06:21
Jens
So somehow, you know, I, I don't know why I somehow call it like, like in each entity, it somehow
has like a home, like it has one subgraph that that is the, the, like the home of an entity that's
like the entry point. Yeah. And so what I'm currently thinking maybe that's naive. Maybe the
people on the stream have a better idea.
00:36:06:23 - 00:36:34:15
Jens
And then you can comment that. But what I'm currently thinking is that we, we somehow take
the GraphQL schema, we annotate it and say this entity should be, should be, a node should it
should be a, it should have implement the node interface. We just annotate it somehow. And
then what is happening is, that it did it.
00:36:34:15 - 00:37:05:25
Jens
Okay. So what we will do is we annotate the entity and each entity, it has this key directive with
fields. Yeah. So my idea is that we create a field, it's called node on this entity. And that's the the
node ID and and the id it will actually be a Json web token. So the JWT can in the Json web
token we put multiple things.
00:37:05:28 - 00:37:33:08
Jens
So first of all we put the we put all the keys of the entity. So if the if the entity let's say the entity
has ID and SKU we put into the JWT, ID and SKU, and then we put into the, into its the, the
subgraph where it's where it's where this is coming from.
00:37:33:10 - 00:37:58:27
Jens
And we sign it because if we sign it, it means or imagine we wouldn't sign it. So a client comes
to the router and sends us a node request. One thing is missing. We need to have a type name.
So we need to have the type name. So feed item the keys and the subgraph where it's coming
from.
00:37:58:29 - 00:38:22:27
Jens
Actually I'm not even sure if we need the subgraph. I think type name and keys should be
enough. And then the the router can, can, figure it out. Okay. So we have this. We sign the JWT
and now the client sends us the request with the JWT y JWT. Imagine the client sends the
request and it gives us type, name and keys.
00:38:22:29 - 00:38:55:05
Jens
We would assume this combination of type name and keys exist. Or at least we need to validate
that it exists. Yeah. So the router kind of needs to trust the client that this combination of type
name and keys that we actually have it or so it, it can kind of be an attack because keys are
kind of like an internal concept and you don't want clients to guess.
00:38:55:07 - 00:39:18:01
Jens
And so if you if you don't have this JWT, clients can just send whatever combination of, of, of
entity keys and then they can figure out like if the server always says no doesn't exist. No no no
no no no no. And then eventually they say, oh yes, this exists. Then it means the client can
guess entities. And I don't think we want clients to guess entities.
00:39:18:09 - 00:39:45:21
Jens
So we give the client the JWT. We sign it. So the first thing that happens, if we make such a,
such a, relay node, signed relay, request, we verify the JWT so we know okay, we the router like
ourselves, we created this JWT because we can validate the signature. So that means first of
all, we can trust that we should process this request.
00:39:45:24 - 00:40:20:11
Jens
That's good. It's not authentication at this point it's a JWT. But we're not doing authentication.
That's the authentication already happened okay. So we now know that we can trust this combo
of type name and keys. And so we have translated the we have translated the the node relay
node request into an entity type name in keys. And we know what, what fields, the user, wants
to have and now we can, we can make our entity calls and fetch it.
00:40:20:13 - 00:40:40:00
Jens
And so yeah then then cosmo router could support natively support relay I think that would be
super dope. If anybody likes this idea then then, I don't know, give it a thumbs up or react
whatever. Comment like and subscribe.
00:40:40:03 - 00:40:45:18
Stefan
You're getting a few streamers. No it makes sense in. I mean, there's a lot to unpack there, but
okay.
00:40:45:18 - 00:40:49:23
Jens
No, no, you explain like, can you actually listen, explain to me.
00:40:49:25 - 00:41:07:11
Stefan
No. Not explaining relay to you. I'm thinking most people say about relay. Is that the fact that
you have to use relay, it is one of the best clients to use though, on the front end. If you're
working with GraphQL. But no. Well, what was that tweet that went viral of yours that you can't
have a discussion about Federation if you're not a federation about it?
00:41:07:13 - 00:41:11:22
Stefan
Not yeah, yeah. You can't talk about GraphQL if you don't mention relay, right?
00:41:11:24 - 00:41:37:26
Jens
Yeah. But yeah, honestly, I think a lot of people who like GraphQL know they are. They are not
like I like or a lot of people who really like to use GraphQL. I think, they are not just like, hey, I
really like to use GraphQL, but more like, I, I really love relay and because of that I'm using
GraphQL.
00:41:37:28 - 00:41:55:24
Stefan
But what makes relay so special? Like, abstract, like the abstract, the way the GraphQL, like,
okay, like there's a bunch of front end clients out there, react, Next.js and then there's relay.
What makes relay so special? What makes it so good and why aren't more people using it?
Also, relay is open source from Facebook, right?
00:41:55:26 - 00:41:56:18
Jens
Yeah.
00:41:56:21 - 00:41:57:06
Stefan
Okay.
00:41:57:09 - 00:42:26:21
Jens
It's it's just the way it works. So you know, let's say you have a UI component that shows you
the feed with not so much detail. So you create a fragment that defines what fields you need to
have this overview. Okay. Okay. All right. So you have this fragment for this component. Then
you have like let's say you have a feed detail page.
00:42:26:26 - 00:42:58:21
Jens
So in the field detail page you also define how you how you query the thing and everything. And
you have a fragment for that. And you, you define the fields you need in a detail page. And let's
say in the detail page you need more fields than in the overview because it's more detailed.
Okay, good. So stage one we deploy it and then product owner says detail page I don't like it.
00:42:58:21 - 00:43:28:01
Jens
Please make changes. Please remove something. So you remove a field from the fragment off
the detail page. And by removing it, you then run the relay compiler again. And what the relay
compiler does is it figures out that on each path of the page, you combine all the fragments you
hoist up from the from the child components to the parent.
00:43:28:01 - 00:43:38:19
Jens
You hoist up the data requirements, and you build a unified query for this page to load the page,
efficiently. But you can see this.
00:43:38:21 - 00:43:43:26
Stefan
well with the relay.
By the way, when you said that, you can kind of see the similarities of why GraphQL pairs so
00:43:43:28 - 00:44:17:26
Jens
Yeah. Yeah. Exactly. That's like that's why you need fragments and selection sets and these
things. But now here's the thing. So let's say you have tRPC. So you create a t RPC call that
gives you the feed data. And because you also need the detail page, it loads the feed and also
the detailed page data. So now in your frontend component you remove this this one thing
because the product we want to set, we don't like it.
00:44:17:29 - 00:44:42:28
Jens
Yeah. And so in tRPC you, you would not remove a field from the fragment. But with the right
tooling, if you have a field in the fragment and you're not using it, you get lint errors. So it's like,
hey, why are you fetching something? You don't need it. Yeah okay. Fragments relay compiler. It
figures this out so it tells you hello.
00:44:42:28 - 00:45:01:24
Jens
Remove the field. Then we compile it, we hoist up our data dependencies. And now the field is
actually gone from the page query. If you do the same thing with something like tRPC. Yeah. No
not against trPC. We I think we use it or maybe we don't. But it's a good thing. So don't worry I
think the good thing.
00:45:01:24 - 00:45:29:01
Jens
But yeah. But the point is let's say you are like a big company like meta or what? Coinbase or
whatever. And you have teams of teams, of teams, of people and everybody changes UI
components over time. It means that data dependencies for UI components, they change all the
time. And nobody knows like a complete map of like a complete tree of of everything.
00:45:29:07 - 00:45:54:06
Jens
So you are deep down in the tree, you change that one component, you remove a field or you
add something, and now you need to go through five layers of UI components to manually figure
out, do we really need this field or don't we so and let's say you have a rest API. So what
happens is you make a rest API call in the root of the component tree.
00:45:54:06 - 00:46:19:20
Jens
You load the data for this tree, someone in the child tree in the in the children of this component
tree, they say, we we we need another field. So you go all the way to the root to the rest API.
Someone adds it there. Okay, nice. It's not working. You deploy it. Half a year later, you realize
we change the feature, you remove this field.
00:46:19:23 - 00:46:40:08
Jens
Do you think anybody is going to remove it from the rest API? No, it would be a breaking change
like removing a field from a fragment. It's not a breaking change if nobody is using it, but you
need to know who is using the fields. So you need to hoist up all the fragments and see are we
using it or are we not using it?
00:46:40:10 - 00:47:16:25
Jens
And if you don't have relay you cannot do this. And really, I can only work with a query language
that allows you to have selections on the tree. So yeah, you need GraphQL to do that. And if
you if you have ever tried to build UI at scale or across teams like mock like, oh, we have two
front end developers like WunderGraph, like we don't need relay, but if you build front end with
like 100 people, yeah, you, you, you have different sets of problems.
00:47:16:25 - 00:47:24:16
Jens
And this is where, where relay really where relay shines.
00:47:24:19 - 00:47:27:00
Jens
Where this approach relay shines.
00:47:27:00 - 00:47:43:06
Stefan
Oh no. It makes sense. It just makes sense in the name to. I actually never thought about it that
way. And then when you explain it, I can see why it makes so much sense with GraphQL. And it
makes sense when you would use relay. If you have multiple teams that are creating multiple
components, multiple changes, you're a big scale company.
00:47:43:06 - 00:48:07:06
Stefan
Things change. It absolutely makes sense. It's interesting. But okay, so going back so we went
on a tangent as always we went from APIs. We went with the future of federation. Federation is
held back by GraphQL. I can't get that out of my head like what is the next iteration for
Federation? Where where do you see this world going?
00:48:07:06 - 00:48:24:13
Stefan
And I ask this question again, but why aren't more companies adopting federation? Sure, you
have the Gartner metric. People are like, yeah, we're adopting it. But this whole point with
relays, why are more companies at scale using relay? Why aren’t more companies using
federation if it clearly makes sense?
00:48:24:15 - 00:48:37:17
Jens
I think this is it's kind of easy to answer, like how many companies are there where you have a
hundred front end developers or more working on a website.
00:48:37:19 - 00:48:41:11
Stefan
I mean, thousands or hundreds of thousands probably. There's a lot.
00:48:41:13 - 00:48:42:13
Jens
No.
00:48:42:16 - 00:48:43:21
Stefan
You don't think so?
00:48:43:24 - 00:49:00:13
Jens
Like, there's no like, you know, which company has 100 front end developers? Like, I'm not
saying developers, but. Oh, 100 front end developers working on front end on one front end.
00:49:00:16 - 00:49:00:29
Stefan
Yeah.
00:49:01:05 - 00:49:16:26
Jens
Okay. Like yeah. Meta and Coinbase and some others. But ultimately the, the, the surface area
of people like I don't know, you know, and it's about practicality. But.
00:49:16:29 - 00:49:36:09
Stefan
But wait, wait, wait. Because this is the biggest argument that I see a lot on Twitter is that
people adopt federation or they adopt GraphQL, or they adopt relay and they have 1 or 2
engineers. And so what they say is we tried GraphQL. We hated it. And then you ask them,
okay, why do you try GraphQL. Under fetching over fetching problem.
00:49:36:09 - 00:49:50:09
Stefan
Okay. And also we only had a couple developers. Do you think Federation and GraphQL will
ever make sense for these companies that don't have 100 front end developers?
00:49:50:12 - 00:49:53:01
Jens
Yeah. I think we need to change some stuff.
00:49:53:03 - 00:49:58:15
Stefan
And what would we change and why?
00:49:58:17 - 00:50:26:18
Jens
If you if you so I think the first question to ask is does federation makes sense without GraphQL.
So in other words, thus federation makes sense without relay. Oof. And and we just talked about
it I think like again relay is awesome. But it also comes as a cost like relay is not super easy to
understand.
00:50:26:21 - 00:51:11:28
Jens
For a lot of people, I think RPC is easier to understand. Like MCP doesn't want GraphQL, it
wants RPC. Yeah. Json, RPC to be more specific. So how can how can it make sense? And
then is or in other words, does federation make sense without relay. And I think the, the, the
value of federation is we built an API with many teams or we create a uniform API interface
across many teams.
00:51:12:00 - 00:51:40:12
Jens
And I think that's a lot of value because, being able to have a uniform schema with entities,
being able to have clarity what our entities are. So clarity in the domain model and everything
clarity in the, in the descriptions, I think it has a lot of value. But. Theres I think a much bigger
use case.
00:51:40:15 - 00:52:32:17
Jens
And that is okay. You know, all the people who who built SDKs. Yes. Who build Rest APIs for
others to integrate these APIs into the system. Can we create a uniform approach where we
make it super simple to create SDKs from your super graph? Because with that approach, we
could open up federation to not just relay users but to yeah, to, to you know, well, one thing I
kind of realize about the open API community is that a lot of people, they they use open API to
describe Rest APIs, but what API consumers actually want is SDKs.
00:52:32:20 - 00:53:11:07
Jens
So what what we're thinking about is, you know, similar to MCP, if you want, if you want an SDK,
if you want MCP, what really is the difference between because for me, an SDK is generated
code. That's where each does the functions or classes or structs whatever. And I can I can
somehow call a function and it does one thing and then it returns some data.
00:53:11:10 - 00:53:41:25
Jens
So what could we do to turn the super graph into an SDK? We create a collection of GraphQL
operations like MCP. And then we'll because we can describe each operation, we can group
them in folders or whatever and their names. And then each operation, it's, it has an input, Json
schema. It has a response Json schema.
00:53:41:25 - 00:54:11:25
Jens
And then we generate an SDK. And so, so now I think we, we take the concept of federation
and we open it up to, to like, like a whole new surface area and that, that will, that will give so
many people, like something like, like a uniform platform for like, okay, here's our SDK, this is
how we can we can use it.
00:54:11:28 - 00:54:48:03
Jens
And now you kind of make accessible your super graph to. Yeah, to anybody without
understanding GraphQL because, what this SDK does is it calls persisted GraphQL operations,
one function at a time. And yeah. Yeah. Now anybody can, can use the, the graph and that is,
that is one part where, where I think or where, where, we are currently going because,
00:54:48:05 - 00:54:58:16
Stefan
Well said. But yeah, you went full picture from the very beginning of the podcast all the way to
the very end, including relay it makes sense. But what continue what was the second part? You
said?
00:54:58:18 - 00:55:00:10
Jens
No, you just stop me.
00:55:00:12 - 00:55:26:15
Stefan
Oh, okay. Sorry. I just wanted to call that out the way that we did a full picture. I really like that. I
mean, it makes sense to. And this is how you go beyond GraphQL. But one of the biggest things
I talk with, like other startup founders friends, is that the dev tool space. So technically we're in
the enterprise, tooling space we sell to enterprises, but in the dev tools space, the only way to
make a successful dev tool is if individual developers can use it.
00:55:26:15 - 00:55:36:09
Stefan
And then you have a clear ladder to a group of developers can use it, and then an organization
of developers can use it. That's the only way a dev tool can be successful with the collaboration.
00:55:36:11 - 00:55:38:28
Jens
Where is this definition coming from.
00:55:39:01 - 00:55:55:29
Stefan
That's just my own like razor that I have, is that that's how dev tools are successful, is that an
individual developer can use it, a group of developers can use it, and an organization of
developers can use it. If you can't hit those three and a a lot of companies fall short is and they
have a good tool.
00:55:56:02 - 00:56:12:22
Stefan
We did individual developers used it, but we didn't have teams using it. And this was the
wundergraph SDK. We tried it. It didn't really work out that well. But with Cosmo, what we're
seeing is we're kind of going backwards. We're seeing the organizations of developers can use
Cosmo and that they love it. And it's what you're said.
00:56:12:22 - 00:56:35:14
Stefan
You're expanding beyond Federation, you're expanding beyond GraphQL, and, you know, i like
that. But where do you see Cosmo going in collaboration that organizations, teams, and
eventually the individual developer can use it? You think individual developers will be able to
use it when they're building their projects and things like that, to open up what you said there,
graph or their app to other developers to integrate easily with it.
00:56:35:16 - 00:56:43:21
Stefan
Also, do you like my definition of what I think of dev tooling? Or do you disagree with it?
00:56:43:23 - 00:57:21:13
Jens
I think dev tools is really hard. You build something that's. Let's take the example of Prisma. I
really like Prisma. I would have really hoped for them to be successful. Maybe they are
successful. To me, they don't look successful. Maybe they are, but. So you build it. ORM, in the
hopes that you build a massive group of people around you and you can somehow monetize it.
00:57:21:15 - 00:57:33:29
Jens
Yep. And then comes drizzle and all your dreams fall apart. Okay, but bad joke, but the good.
00:57:34:01 - 00:57:37:08
Stefan
It's true, though, sadly,
00:57:37:10 - 00:58:19:17
Jens
Not okay for real. So you build an open source orm, how do you monetize an orm, because
what you kind of need, like, it's it's, I would say it is our definition, but if a commercial, you know,
I like to, to, to distinguish open source and commercial open source, if someone builds the
drizzle open source to help themselves use drizzle, and they are not building this as a startup,
but more as a means to an end, it can be a successful thing.
00:58:19:19 - 00:58:59:08
Jens
Yeah. If you build Prisma with the intention to to make money, I think what you need is
collaboration. Yes. And, by collaboration, what I mean is, you for. Theres two ways you could
sell compute or you could sell collaboration. And I think most startups fail in selling compute,
because you you essentially you are wrapping the service, you are wrapping AWS.
00:58:59:11 - 00:59:27:12
Jens
I would say vercel is not an AWS wrapper because what they have created in the in terms of
complexity of the platform, it goes far beyond wrapping the whole experience from protection
against threats to CDN to like it's not a wrapper, but if you are Prisma and you have.
00:59:27:14 - 00:59:28:13
Stefan
00:59:28:15 - 00:59:34:14
Jens
I don't know what they they they announced something I think some component for
subscriptions or whatever.
00:59:34:14 - 00:59:36:04
Stefan
It's like boost or something. Yeah.
00:59:36:04 - 01:00:08:03
Jens
Yeah, something. Okay. So they take this one thing and they put it on compute somewhere and
they sell it as a service. You have to wundergraph SDK problem again. So our what we pivoted
away is because, developers have a natural tendency to not buy services for singular problems.
Actually developers have a tendency to not buy anything.
01:00:08:05 - 01:00:12:03
Stefan
Clip that. Yes, it's very true. Individual developers. Yes I agree like.
01:00:12:05 - 01:00:45:18
Jens
They what what developers do is they go to their boss and say, hey, can I have an AWS
account? And they get an AWS account and then they gi they, they buy whatever they want. So
so that's the thing. And they buy like a database whatever. And they EC2 and they call it a day.
But if you have your boost thing or whatever you put it on compute, what happens is you buy
compute for $1 and you sell it for three or maybe 5 or 10.
01:00:45:20 - 01:01:06:19
Jens
And people will at some point, maybe they use it, maybe they don't trust you. Even so, it fails at
that stage. But even if it doesn't immediately fail, then people will be like, okay, but it's so
expensive. You're just a wrapper. Like, why am I paying ten bucks if it could cost one, can I not
self-host this thing?
01:01:06:19 - 01:01:35:05
Jens
And then you're like, yeah, but self-hosting is more complex. And they will be like, yeah, I don't
care. Like my time is worthless. I don't value my time. I can I can do everything. And, yeah. So
it's I don't know, it's it's it's not, it's not a world I want to be in. So like, yes, you can somehow
resell compute to, to be honest, like so many startups are just compute resellers like you.
01:01:35:05 - 01:01:43:28
Jens
You are just an AWS reseller with, I don't know, some fancy whatever, but, yeah.
01:01:44:01 - 01:01:56:07
Stefan
You can make good money doing it, you can make good money just being a reseller, and you
can improve the experience a little bit there. Startups that there are whole premises AWS
without the AWS. But you eventually. Yeah. hit that point.
01:01:56:09 - 01:02:03:04
Jens
That's this one company. What was the name again which one they resell AWS actually.
01:02:03:07 - 01:02:04:15
Stefan
01:02:04:17 - 01:02:05:25
Jens
You know what I mean?
01:02:05:28 - 01:02:09:10
Stefan
I'm trying to think of the name they resell like the credits is a flight controller.
01:02:09:10 - 01:02:15:18
Jens
nonono, they they give you a new experience on top of the SSD. No.
01:02:15:20 - 01:02:24:01
Stefan
That's control. That's, there's flight control, there's SSD, there's fly.
01:02:24:03 - 01:02:28:01
Jens
Yeah. Similar. Similar, similar. Okay.
01:02:28:03 - 01:02:37:02
Stefan
I'm really trying to remember is a pump is it up? Remember. But okay. Just saying just a
company that just basically sells you AWS with a better.
01:02:37:05 - 01:02:37:14
Jens
Yeah.
01:02:37:15 - 01:02:43:22
Stefan
Oh oh, oh. It's, Yeah. Railway is a railway. Yes. Okay. Yeah. Yes.
01:02:43:25 - 01:03:20:19
Jens
Yes. You know, in, in in my 700 years of being a developer, I have, I have really learned one
very important thing. You buy databases and compute from AWS, GCP, or maybe Azure, and
you, you you just don't use startups because startups absolutely suck at reliability. And if you
think it cannot get any worse, then try fly.
01:03:20:20 - 01:03:23:03
Jens
Like, yeah.
01:03:23:05 - 01:03:24:13
Stefan
It was bad.
01:03:24:15 - 01:03:45:16
Jens
We tried, but like, we we wasted so much time trying fly. Like, just just don't use startups for
compute. It's, it's it's really hard to do to do compute. It's it's so hard. Okay. And real quick.
01:03:45:18 - 01:04:07:16
Stefan
real quick note on that one. These startups move slow or not startups, these companies AWS,
Azure, GCP. But there's a reason that they move so slow. When you're that big and you have
that much reliability, it would be ridiculous to choose anything else other than to go to one which
is Azure, GCP, and Azure. I like how you said maybe Azure.
01:04:07:16 - 01:04:08:09
Stefan
That was kind of funny.
01:04:08:09 - 01:04:41:01
Jens
You know what's crazy? So we have a Node.js component in Cosmo in our cloud. It's called
control plane. Node.js like it's not like Node.js. It's not it doesn't stand for stability or anything or
like best tech or whatever. It's just yeah, okay. Node.JS whatever. And we have this thing now
running for a couple of years, like of course we updat it and it's running on, on, on, Kubernetes
on GCP.
01:04:41:04 - 01:04:45:10
Jens
Do you know the number of incidents.
01:04:45:13 - 01:04:47:06
Stefan
A big fat zero.
01:04:47:08 - 01:04:48:10
Jens
Yes. Yes.
01:04:48:12 - 01:04:49:18
Stefan
Zero incidents. Yeah.
01:04:49:22 - 01:05:21:12
Jens
Like it's it's insanely boring to use Kubernetes on GCP. Insanely. Like we even paid extra money
for like Dustin, our CTO, he he figured out there's like, like a thing and it automates the cluster.
So we're not managing a cluster. And because like, who cares? And so it automatically does
stuff. And we never had an outage, an incident.
01:05:21:12 - 01:05:50:16
Jens
Nothing. It's I don't know, like I'm not I'm not like advocating for, for for GCP or so it's but I can
just say this this stuff just works. It's it's crazy if you want to build a startup and you don't want to
waste your time on on infra, whatever, just use GCP. I'm pretty sure AWS is the same same
game, but this stuff just works.
01:05:50:16 - 01:06:17:19
Jens
If you deploy something on fly, then suddenly on a Friday afternoon your deployment is gone
and you call a number or something because you have an SLA and nobody answers. And if
you're lucky in some forum on Monday, you get an answer and then you just know, okay, like,
let's let's run. I don't know how they how they managed to raise so much money, but yeah.
01:06:17:20 - 01:06:18:25
Jens
Okay. So.
01:06:18:26 - 01:06:20:21
Stefan
I see well said.
01:06:20:23 - 01:06:50:19
Jens
Yeah. So this is the category of we, we buy compute and we resell it more expensive. And to be
honest, I think it's, you know, it's a numbers game, but if given enough time, so given infinite
time, the margin for your for your reselling will go to zero. Yeah. So I don't know, your business
model is designed to fail.
01:06:50:22 - 01:07:08:17
Jens
I don't like it. What I like is collaboration. If you enable, 100 people to build an API together and
they build a workflow that really works for them, that's powerful. Then.
01:07:08:20 - 01:07:22:17
Jens
Imagine linear. So we are using linear. Our team is growing. Every time we add a new member
we onboard them to linear. So what is happening with the value of linear.
01:07:22:17 - 01:07:24:22
Stefan
For us it's going up.
01:07:24:25 - 01:07:57:28
Jens
It's going up. And so that means over time collaborative tools as you add more people become
more valuable. You put in your own tickets, you put in your documentation everything. Yeah.
And so Federation building APIs across teams, collaboration. So on the one hand side you
have, you have infra and you have like schema registry. And we do this for our customers.
01:07:58:00 - 01:08:23:10
Jens
And on the other side of the spectrum, you have, you have collaboration, and and yeah, where
people work together, build subgraphs and everything. We will talk more about this topic in the,
in the future. We, we first need to figure out some, some things. But we're, we're, we're very the
the kitchen is busy I would say yes.
01:08:23:13 - 01:08:42:28
Jens
But on the other hand you can kind of see like I'm not just ranting, but it also guides our own
decisions because, Apollo built a service to host routers for customers. This is ridiculous. Like.
01:08:43:00 - 01:08:43:19
Stefan
why
01:08:43:21 - 01:08:47:07
Jens
I don't know, have they killed it already or is it still alive?
01:08:47:10 - 01:08:53:09
Stefan
It's still a thing. I was talking to somebody the other day about it. Like the whole sit around with
solution and wrapper on a wrapper.
01:08:53:09 - 01:09:28:25
Jens
So, so like given our experience with the SDK and our learnings from like how hard it is to run
to, to run compute at scale, like why do you why on earth like I know they have more than 100
developers, but why on earth do you want to run routers for people? Because what it means is
you have to have people on call like you.
01:09:28:25 - 01:09:47:25
Jens
You have to make sure everything works. If a router doesn't work, it can be your fault. It can be
the customer's fault, I don't know. And then at the end of the day, how are you charging so you
can find some sort of proxy metric, for example, you can invent, I don't know, TPS or whatever.
01:09:47:25 - 01:09:50:19
Stefan
Or something like a graph, some something, your.
01:09:50:19 - 01:10:14:03
Jens
Compute unit, whatever. Yeah. And this is, this is all bullshit because what you're doing is you
you take the compute from AWS and you put something on top, and now I can, I can. So you
put your margin on top and now I can I can draw a line if I put, you know, I can draw a graph.
01:10:14:07 - 01:10:57:25
Jens
And if I, if I put big enough numbers into this graph, I can now calculate if I use the managed
service versus I build a team to run routers. And then you can see the the graphs of the cost.
And you can see exactly at which point you should stop doing stop using such a service. And
and here's a problem, because, in most cases it never makes sense because if you have
subgraphs, it means you have a platform team that operates the infrastructure to run subgraphs.
01:10:57:28 - 01:11:34:24
Jens
So it means the company that uses federation, they already have people on call that the
subgraphs don't break, because if they break, you're offline. So let's say you are, I don't know,
big company Coinbase. If your subgraphs are down, nothing works. So if you now use a
managed router, what happens is if the if the super graph doesn't work in production, two
companies now need to collaborate to fix the problem.
01:11:34:29 - 01:11:53:13
Jens
like.
So you don't just buy a managed router. You also need people on call internally in case of an
incident to figure out why. Is it broken? Is it us? Is it them? Yeah. And you're paying extra for
01:11:53:15 - 01:12:03:04
Stefan
It doesn't make sense. What? It doesn't make sense. Now, I'll leave you in there, but, one sec
my dog is, like, freaking out. But if you guys haven't seen.
01:12:03:07 - 01:12:03:29
Jens
Rent.
01:12:04:01 - 01:12:20:04
Stefan
This is Cosmo's mascot, so this is tricky, but you get out of here. I'm not gonna lie. I think this is
a fantastic episode. So we touched on upon a lot. Next week, we're back, which will be really
exciting. We're going to start bringing more guests onto the show. It's going to be more,
technical focus.
01:12:20:04 - 01:12:32:20
Stefan
We're going to bring experts that have experience running federation at scale or just working at
hyperscaler companies. I have no closing notes, but, what's the good thing?
01:12:32:22 - 01:12:35:28
Jens
The good thing is we are back next week.
01:12:36:00 - 01:12:51:04
Stefan
Awesome. Great episode. Thanks everyone for tuning in. Be a little bit more collaborative
though. Pose some questions. Do you agree with Jens? Do you think that he's crazy? You think
he's off his rocker? Do you think collaboration is a stupid and Compute is where it's at now. Feel
free to post your comments into there. Go ahead.
01:12:51:07 - 01:12:59:26
Jens
If you. If you don't raise your hand, you agree. Yeah. So looks like everybody. That's fair. I think
we're all in agreement.
01:12:59:29 - 01:13:05:25
Stefan
Quiet mouths don't get fed. Thanks, guys. See you guys next week we continue.