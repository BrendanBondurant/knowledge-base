00:36:28:22 - 00:36:56:22
type: podcast-chunk
Jens
Yes, we can do that. But why I mean, we we have an algorithm for this Federation works great.
And yeah, we we now also built very powerful tooling to better understand how your federated
graph looks like. All these kind of things and which which brings me to another interesting topic.
Looking a bit into the into the future.
00:36:56:22 - 00:37:01:24
Jens
But before that, I don't know if you have any questions so far.
00:37:01:26 - 00:37:22:15
Stefan
No, I think it's really useful. And one of the cool things about the series a announcement was,
these reporters took the concept of federation and they put it into, their, their report showed
what they wrote about. And my little sister, she emailed me or not, emailed me. She texted me
and she said, wow. Like, I kind of understand now what you do, which was in Central plumbing.
00:37:22:20 - 00:37:41:26
Stefan
And she's like, okay, now I understand what APIs do and I understand what federating is. It's
really interesting what you guys are doing with the plumbing. That's why I come in. I have on
that. I want to know though, like because I've seen it obviously as a co-founder. I mean, you
don't even talk about GraphQL anymore. You more talk about the organizational pains versus.
00:37:41:26 - 00:37:57:04
Stefan
And GraphQL is just a small subset of solving that problem. But talk to me a little bit about like
the roadmap. Like where are we going with this. Where do you see GraphQL fitting in. And
especially with Federation.
00:37:57:07 - 00:38:35:29
Jens
Yeah. So one one super interesting thing that just recently happened is, you know, sometimes
you, you build something like we're, we're currently building a new thing. And this new thing, it's
going to be outside of the typical realm like router and schema registry. And something
interesting happened. You know, sometimes you, you build a new tool and then you kind of
realize, or you, you, you get a new view on the world, and it completely changes how you see
things.
00:38:35:29 - 00:39:03:26
Jens
And so, well, one thing, we did is. So we, we build a bunch of things. I don't want to be, like, too
specific yet, but, what we what we did is, we now have have a tool which allows us to analyze
queries, so we can understand how query plans would look like. So we have turned, by the way,
just it's open source.
00:39:03:27 - 00:39:05:05
Jens
You can you can just you'll.
00:39:05:05 - 00:39:06:00
Stefan
See you can see the.
00:39:06:00 - 00:39:39:06
Jens
Commits. Yeah. No, but, so what we did is, we, we really care about reliability. And one thing to
ensure reliability is, in the, in the future, we we want to improve our, our query planner, bring in
new capabilities. And so we built a CI system that takes all schemas from our customers and all
queries. And it plan all all queries against them.
00:39:39:09 - 00:40:06:23
Jens
So generates a Groupon for every single query we know. And on every pull request where we
change or try to, to, change our router, we run this thing in the back end like it's not on, public
because we don't want to make this data public. So we run all these queries, we generate the
query plans, and if they if there's a diff, we we would flag this.
00:40:06:23 - 00:40:35:22
Jens
And then we have to manually go through the diff and analyze why did the query plan change,
etc., etc.. And so we, we built this and we looked into this and I, you know, sometimes you, you
have data in front of you and you start thinking, you start looking and then a very interesting
process kind of started where, you know, we had discussions in the team and what we kind of
realized this.
00:40:35:22 - 00:40:57:18
Jens
And I think that's a that's a world that opens up that like, nobody ever touched this in the
GraphQL space. So imagine you have a schema and you have a query. No, imagine you have a
schema and you have a thousand queries. And you plan all of the. And now that you have
planned all these queries, you analyze them in whatever way.
00:40:57:18 - 00:41:28:15
Jens
So you you look at the query plans, they are ASTs and you analyze them and you build stats
about what these ASTs do, for example, how many nodes, what kind of nodes, etc., etc.. So you
get statistics about these scores statically. This is static analysis. No, no LLM no magic. It's like
very simple stuff okay. So we have these statistics and now do the following.
00:41:28:17 - 00:41:52:26
Jens
In Federation we have this concept of key. And we have concepts of requires and provides and
blah blah blah. And all these directives, they have influence on what the query planner does,
how it plans something sharable for example. It's another thing override. So all these federation
directives, they they do something with your query plans okay. So imagine this.
00:41:52:28 - 00:42:21:23
Jens
You have a thousand queries and the schema you plan them. And now you have a thousand
ASTs and you analyze them. Then you change one tiny thing in the, in the, in your in your
schema. For example, you change a field or you move a field from one subgraph into another,
or you do like random stuff, whatever. And now you generate these query plans again.
00:42:21:26 - 00:43:02:29
Jens
So they will diff. And now think about it like this. Think about you have these two packs of ASTs
and somehow you're you're able to build, insights or you can build, yeah, you can analyze them
so you can build stats. And now think about doing a lot of changes, random changes, not so
random changes. And you, you, you change the, the a, the schema and you generate the plans
and you build the stats.
00:43:03:01 - 00:43:25:05
Jens
And so you make changes. Just like machine learning. And as you make changes you see the
stats go up or down or they like the let's say you have let's say you have number of nodes in
the, in an AST. And this number, it goes up and down because you need to make more or less
fetches or whatever.
00:43:25:07 - 00:44:08:01
Jens
So you start to change the schema in random ways, and the query plans change. And if you do
this you kind of realize that there's federation, there's microservice architecture, then there's
people. There's, you know, the organization, the people of the organization. And now you start
thinking about. Are we doing microservices right, in the sense that this is the, is the schema or
other schemas we have built?
00:44:08:03 - 00:44:37:08
Jens
Are they good? Yeah. And is there something we can optimize. And then you, you, you kind of
start going down the rabbit hole of, oh, that's, that's a very interesting topic because, we have
never, you know, we have never thought about questioning our architecture. So when I, when I
build microservices in the past, it's like, okay, you build a website, it needs a backend, we build
a monolith.
00:44:37:10 - 00:45:08:01
Jens
We think the monolith is too big. We split it up. Now we have five microservices. Did anybody
ever question if that was a good architecture? And then, you know, so the stuff we're thinking
about is can we, can we build metrics? Can we understand your traffic, your query patterns, the
shape of the organization, the shape of the subgraphs?
00:45:08:03 - 00:45:37:18
Jens
Can we somehow leverage the data to help people improve their architecture? And and I think
this is really just the starting point. And, you know, at this level, it's not about rest. It's not about
MCP, not about SDK. It's it's not about GraphQL, and it's not about Federation. It's about the
question, can we help organizations to, to to kind of wiggle back and forth and try it out?
00:45:37:20 - 00:46:00:09
Jens
What would be the optimal service structure? Which team should take ownership of what. And I
think it's a it's a super interesting topic. And, we're we're starting to do research in this area, and
I, I have no idea where this is leading, but, yeah, I, I think it's super interesting stuff.
00:46:00:11 - 00:46:22:02
Stefan
Well, it is even if you're not, like, super familiar with, like, APIs. I think a big problem companies
have is, is understanding their company, understanding who works on what, who owns what a
lot of companies will do, like a domain driven architecture with websites, with the domain the
team owns that. I think the architecture part is where federation thrives.
00:46:22:02 - 00:46:50:16
Stefan
But for those of you that might not be familiar, there's a really cool mandate by, it's famous, it's
the API mandate from Jeff Bezos. And one of the mandate rules on there was that teams will
communicate with each other only through APIs. And I think that was the first step into this. And
what I understand from this, and Jens, is feel free to correct me if I'm wrong, but Federation can
kind of unlock that mandate even further is that teams can communicate and work together.
00:46:50:22 - 00:47:18:27
Stefan
You can federate across the entire company. You can understand everything within the
company. And I think that's a huge problem that companies have is okay. What team is working
on what what services working on? Is this field still in use on this API, or are we even using this
API? And I think now with LLMS and data, it's what you said I built it, but it was five years too
early and I think right now with AI and LLMS and everything that's coming even further, I think
it's a great time with that.
00:47:19:05 - 00:47:38:21
Stefan
But are you able to share a little bit about like, what we're kind of building where we're
envisioning the space going because we kind of jumped that part, like we went from GraphQL.
This is this interesting sector that we're exploring. But what about the current GraphQL market?
Like what do you think about it and where are we going as a company?
00:47:38:23 - 00:47:42:06
Jens
Yeah. Good question, by the way. You know Conway's Law, right?
00:47:42:09 - 00:47:47:25
Stefan
Yeah. That, I never know what it is, but if someone says and I'm like, yep, that's Conway's Law.
00:47:47:27 - 00:47:49:23
Jens
I think.
00:47:49:25 - 00:47:52:07
Stefan
Something you don't map your organization, right?
00:47:52:09 - 00:48:14:14
Jens
Yeah. But the way information flows inside the organization, it kind of resembles how you build
your architecture. Yeah. So for example, if you have if you build a compiler with two teams, the
compiler is very likely to have two steps.
00:48:14:16 - 00:48:21:04
Stefan
With our organization and our architecture, what's our Conway's Law? How are we as an
organization?
00:48:21:07 - 00:48:35:12
Jens
Great question. How many engineering teams do we have? One How many cosmo
repositories? One kind of right. It's actually not true because.
00:48:35:12 - 00:48:37:07
Stefan
Yeah, we have a little small subteams.
00:48:37:07 - 00:48:44:26
Jens
So we have a small sub team. It's building the engine. Yeah. They have their own repo right.
00:48:44:29 - 00:48:46:11
Stefan
Yeah GraphQL go tools.
00:48:46:14 - 00:48:57:12
Jens
Yeah. And everybody else is working on the same thing. So we have one large team one. And
then we have the little outpost the engine outpost. And it's all a second team kind of.
00:48:57:14 - 00:49:09:07
Stefan
And that's literally it. Yeah. But okay so with Conway's Law does does this only involve
engineering like, well like is marketing and like sales in an organization, are they also affected
by Conway's law or like how does that work.
00:49:09:09 - 00:49:46:22
Jens
Yeah, sure. Like they might have the CMS or other things or whatever. So yeah. But coming
back to your question about the the future of GraphQL, so I think what we currently see is with
MCP, LMS, everything, there's a there's a huge need for organizations to unify all APIs. And if
you have in the past there's tools like backstage or whatever, you can put all your Rest APIs.
00:49:46:24 - 00:50:11:09
Jens
It just doesn't cut it because, now you have a problem if you want to build SDKs on on a
thousand Rest APIs, or if you want to if you want to do MCP on one thousand Rest API, it's very
hard. Much simpler if we can do it on top of one super graph. So for us, next step like super
graph we double down on on the concept.
00:50:11:09 - 00:50:36:21
Jens
Super graph is good. The more APIs you bring onto the super graph, the better. Yep. And then
the super graph should be able to to speak whatever GraphQL is good SDKs on top of the
super graph is good. And then you have you have RPC like SDK is RPC. Essentially we did this
in the past with the SDK.
00:50:36:27 - 00:50:38:08
Stefan
I remember yeah.
00:50:38:11 - 00:51:03:29
Jens
This is something that's coming back and also things like MCP. So it's it's it's obvious that okay,
we unify all our APIs into a super graph. And then we make it simple to put SDK s and MCP on
top. And then everybody can can leverage the super graph. So that gives us a pull on the super
graph. So now everybody will be like oh if you can bring it on the super graph, it gives us super
powers.
00:51:04:01 - 00:51:31:28
Jens
Awesome. So the next step is we need to we need to bring everything on to the super graph. So
we need to make it much, much, much, much more simple. Yeah. To bring stuff onto the super
graph. And we're investing into this topic heavily. And yeah, I think, we, we have, like there's
different takes in the industry how to do it, I think.
00:51:32:01 - 00:52:05:20
Jens
So we have validated our idea with many smart people. And if you, if you not sure if you
remember, but I built something called Graph QL Gateway in 2019, so six years ago, a year.
And it used directives to describe data sources. So, Dustin is a team to you remember how we
how we, how we.
00:52:05:20 - 00:52:33:16
Jens
Yeah. In for my initial version of the graphql gateway, it used directives to describe how the
gateway should talk to data sources. And yeah, I don't think it's the right approach. So you will
you will see from us a different approach, not the not the connector route. We don't believe in
the, in this connector approach. We think we should go another another direction.
00:52:33:18 - 00:53:01:04
Jens
So, yeah, I think the super graph, it will be, a fundamental architecture piece, for, for every
company. And it will be extremely powerful. And I don't see how REST or gRPC or anything else
has, has something has something similar. And you can very easily put on top of a super graph
SDKs and MCP.
00:53:01:11 - 00:53:26:20
Jens
It's not a big deal with something like persistent operations or something. So it's it's not so hard.
And then we cover the main use cases for our apps. We can have queries. So the query
interface and then we need to bring in more data onto the super graph. And, and I think this is
where, where things get super, super interesting.
00:53:26:20 - 00:53:32:00
Jens
And yeah, I think that's that's our focus.
00:53:32:03 - 00:53:41:02
Stefan
You said every company though, do you think every company should use GraphQL and then
follow up. Do you think every company should use GraphQL Federation.
00:53:41:04 - 00:53:44:24
Jens
00:53:45:18 - 00:54:14:01
Jens
I, I don't know if I would build just a GraphQL server today. Yeah, I, I think, I don't know, maybe
maybe not a startup, but, I think if I, if I, if I would build a startup, I would just build an like RPC
or whatever, like super simple. If you are a larger organization, I would think about how can I
have a supergraph just because I think it's a it's a superior pattern.
00:54:14:01 - 00:54:51:00
Jens
Bring all bring all data together, unified. It's so powerful. And it allows us allows you to do so
many, so many powerful things. And and also just, if you can have one unified approach, how
everybody discusses schema like what are the entities in our in our domain. Like for example, I
many years ago I worked with a carmaker in Germany and they had REST APIs and they had, I
don't know, seven or more definitions of what a car is.
00:54:51:00 - 00:55:01:12
Jens
And yeah, that's not really useful. Ideally we can we can have one car definition and we can all
agree on on what the fields should be, etc.. So yeah.
00:55:01:15 - 00:55:20:15
Stefan
It's well said. And it's one of the cool benefits is like our customer roadmap is that sometimes we
tell companies, you know, maybe federation isn't for you. And I think that's really important that a
vendor tells you federation is useful for you, not versus just, hey, this is the ideal solution. It is an
ideal solution for a lot of companies.
00:55:20:17 - 00:55:38:13
Stefan
But for some companies it doesn't make sense. But I think that's well said. And then let's talk a
little bit because we only have five minutes left. I want to talk a little bit about, you know, we got
the, the fundraising is it's exciting, but what kind of key roles are we hiring for for this next
iteration?
00:55:38:13 - 00:55:54:20
Stefan
I think it's really important to understand, especially on the engineering part, what these
engineers will be working on, because there's a lot of cool tech that we're working with. There's
a lot of cool companies that we're working with. But what would people on the engineering team
be working on if they were to join wundergraph?
00:55:54:22 - 00:56:24:05
Jens
Yeah. So you you can build the the foundation of API infrastructure for, for the fortune 500
essentially. I believe everybody will standardize on, on the, on the super graph pattern. And
yeah, like you can be at the forefront of, of helping us, define, how that will, look like in detail. So
that's one part.
00:56:24:08 - 00:56:51:23
Jens
And then if you look inside, we have pretty interesting topics like, you know, you can work a lot
with, with data structures, with AST transformations transform between protocols. You, you learn
a lot about high performance and networking. All this kind of stuff. So I think it's super
interesting. It's a super interesting topic. It's very challenging, to get it right.
00:56:51:23 - 00:57:35:05
Jens
And enterprise integration, like, telemetry, observability, all these kind of things. And then. Yeah,
like things like, graph theory, understanding how, how queries look like, how they plan,
analyzing queries and, and yeah. On the, on the, on the impact side, I think we can really build
tooling to help organizations collaborate better. I think every, every digital business, it relies on
APIs, be it developers who use SDK s or AI using MCP, but below both or underneath both, you
have APIs.
00:57:35:06 - 00:58:10:25
Jens
So, it's very likely you have like a super graph pattern and, and yeah, we can build the, the
architecture for that. And then you can also build if you're, you know, if you go dev, you can work
on, on router engine, things like that. So the API gateway and the GraphQL engine and then if
you're more like, like a full stack dev or front end dev, then we, we are building tools for, for
collaboration, for observability, analytics, like user interfaces that, that help people work together
and, and work on schema and, and all these kind of things.
00:58:10:25 - 00:58:37:01
Jens
So, yeah, I think super interesting challenges. It's not your regular. Oh. I build a backend, I build
a front end. It's it's more like, okay, this is a very novel space. Like, nobody has been here.
There's there's little research. You can rely on this little. Yeah. Little, cursor can do. Like,
sometimes you just have to figure it out yourself and uh, so, yeah, I think, what challenges?
00:58:37:01 - 00:59:00:28
Stefan
We have a lot of them. we’re hiring all across. And then one thing is, the founder of Khan, he
said this, in one of his funding announcements, is that with AI and this what we’ll end on and, so
I would love your thoughts on this. Is. Yeah. You're familiar with the assembly line, right? Like
how they Henry Ford, they would make the cars, you know, it would go down the assembly line
and there'd be a single person, and they would just do that single job.
00:59:00:28 - 00:59:20:07
Stefan
And then before you know it, the car is built by the end of it. And he said, what the internet is, is
people building all these services, but it's going across an assembly line. So a company is like
General Motors and they're building these cars. These cars are their products. And as it goes
down the assembly line, APIs are the parts.
00:59:20:09 - 00:59:40:16
Stefan
The screw this thing here, that thing there, what the person is connecting to that. Would you
agree with that statement? I really like it as an analogy for how APIs work, but where does AI fit
into that? Like how does AI improve building APIs better and faster?
00:59:40:18 - 01:00:12:14
Jens
I'm not sure how does API help building APIs faster? I'm not sure on that, but what what I think
is going to happen at least I or that's my prediction. I'm not sure if it's too early to predict, but if
we can build a super graph and we have MCP and now, tools like cursor, ChatGPT, etc., they
can hook into super graph.
01:00:12:17 - 01:00:26:26
Jens
Yes. I'm, I'm just wondering like I think this this will unlock like a new internet because I think
very soon Web3 we will have.
01:00:26:29 - 01:00:34:19
Stefan
Do you remember Web3? All the crypto bros saying there's a new internet with the blockchain?
Is that what you're referring to, a new internet?
01:00:34:22 - 01:00:40:19
Jens
No, but. So.
01:00:40:22 - 01:01:22:13
Jens
You know, I think companies like, like anthropic and others, I think they are very close to building
agents who can autonomously, do tasks. Yeah. And I think super graph, the super graph pattern
is a perfect foundation to enable MCP to talk to anything in your company. I don't think you want
to build MCP as a translation layer to everything, but if MCP is just a thin layer that speaks
GraphQL, then the super graph becomes an essential part.
01:01:22:16 - 01:01:48:13
Jens
So I think very soon we will have, commodity tools with agents so I can open something like
Excel or like Excel like, like a, like a business user app. And it has agent capabilities. And now I
can give it MCP access. And then I think it can do anything. It can pull data out of our database
like customer records, like anything.
01:01:48:13 - 01:02:15:03
Jens
It can be so powerful. And then I'm just wondering where where like where is this going? It can
accelerate like quite rapidly that that new applications evolve that, that now are built on top of
these layers. And then yeah, I think we're, we're kind of in the, in the, in the shuffle business
because, you know, we're, we're the with the boring pipes and the data needs to come from,
from somewhere.
01:02:15:05 - 01:02:27:18
Jens
And, yeah, I think it's, it's a good spot to be in because, yeah, I think agents, they will they will
really accelerate stuff. And they need data. We do that. So yeah.
01:02:27:20 - 01:02:44:00
Stefan
I'm excited because it's a good spot to and and so we'll end on that because we have actually a
retro after this. And Dustin will be mad if we're late. But end of the episode, we're really excited
about the fundraising round. We're hiring across all fronts. Come help us build the essential
plumbing for basically every company out there.
01:02:44:05 - 01:03:02:20
Stefan
There's a lot of interesting problems you can work on here. You've seen our Conway's Law. It's
two teams, mostly just one big team and one small team working on the the query planning in
the engine. But it's fascinating stuff that they're really doing. We're hiring on all fronts. So keep a
lookout on the website. And Jens, what's the good thing.
01:03:02:22 - 01:03:04:04
Jens
We're back next week.
01:03:04:07 - 01:03:09:10
Stefan
The good thing is we're back next week. Thanks, everybody. Have a good time and have a
great weekend. Bye.