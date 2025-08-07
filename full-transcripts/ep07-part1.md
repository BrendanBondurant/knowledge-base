Episode 7
00:00:00:00 - 00:00:54:03
Jens
Hey, everybody. This is the good thing today. We're just a little bit late. As you can see, it's not
Stefan. It's just Jens. I just, brought, David and Sergiy, today to the stream, and, Yeah, Stefan is
currently, doing his, marriage ceremonies. So he's off this week, and, I thought this is a great
opportunity to to bring in some fresh new content to talk about.
00:00:54:05 - 00:01:28:17
Jens
Yeah. GraphQL, query planning, federation composition, all these kind of things. With me today,
I have, David, our chief executive worst engineer. He's one of our masterminds behind, yeah,
GraphQL composition. And I have, Sergiy, who's been working on query planning and, the
GraphQL engine, behind Cosmo for, for quite some while now.
00:01:28:19 - 00:01:37:06
Jens
Yeah. Let's start with David. David, how are you doing today?
00:01:37:08 - 00:01:47:05
David
complain.
I'm very well. Thank you for asking. jens, it's a nice day. It's cold, but it's, it's not raining, so can't
00:01:47:07 - 00:01:52:26
Jens
Well, what what have you recently been working on?
00:01:52:28 - 00:02:17:15
David
A week or two ago, we were working on, configure direct, configure description. That was, a
cool Idea that came from a customer. I think we got we got it to a great place that allows, not
only that customer, but everybody to have granular control over their federation descriptions.
Really happy how it turned out.
00:02:17:17 - 00:02:31:22
David
We have a further ideas how we can add and add more to it, but, yeah, I'm happy with how it
went. And it was it was fun to implement and fun to have that feedback loop directly with the
customer on it.
00:02:31:24 - 00:02:41:12
Jens
Can you give us a little bit of, of background on, on this idea with configure description, like
where, where did this thing come from?
00:02:41:14 - 00:03:11:19
David
Yeah. So this customer, essentially wanted to have granular control over how their descriptions
propagated in the, in the supergraph. So for folks who maybe are not so familiar, you can have
multiple services that have the same instance of a coordinate. So you could have query dot field
in one graph and then query dot field in another graph.
00:03:11:21 - 00:03:34:27
David
And they could each have their own description. And for whatever reason that may be that you
want to have one description in one service, which serves a function for the developers there
tells them information. It's also possible that field has a slightly different role in that graph
compared to another one. And then you have another graph where you have a more of, outward
client facing description that you want to propagate.
00:03:35:00 - 00:04:06:29
David
But, the actual algorithm of how those descriptions get propagated into the federated graph,is to
naive to be able to have that kind of granular control. So this customer essentially, and I believe
they were they had like a Transformer so that they could, do all this with, with a post process or
like a perhaps it was like a middleman process before the composition happened to propagate
what they wanted in there, or they would rely on warnings and errors that things were not lining
up how they should have done.
00:04:07:01 - 00:04:27:14
David
And basically, we tried to streamline that process so that they can just stick a directive in, do
they want the description in the federated graph? Okay, there you go. You don't want it to be in
the federated graph or anywhere that's public. Okay. There you go. You want to override what's
actually in there with something else. So you have one description for your developers who are
working or owning that subgraph.
00:04:27:21 - 00:04:38:28
David
You have a different description for what actually, is propagated. There you go. You can do all
these things. And I believe for the most part, we've solved that issue quite elegantly.
00:04:39:00 - 00:05:06:09
Jens
Yeah. It might sound like like, like a very minor thing. Like if you if you think about composition in
the, in the world of Federation, I think the very last thing would be to, to talk about direct, to talk
about comments or descriptions, but as you, as you scale. I think this was, very interesting to to
see that at, large scale environments.
00:05:06:09 - 00:05:42:12
Jens
And then some of our customers have a lot of graphs, like 80, 90, more than 100. And suddenly
things like descriptions become a problem because you want to know, like, what is the, what is
the source of truth and other things. So, yeah, interesting stuff. And it's also, great that we are
in, in a position where we can work directly with, with customers, solve these, these issues, and,
yeah, on the on the second slot, we have, Sergiy with us.
00:05:42:14 - 00:06:10:13
Jens
Sergiy it's great to have you on the, on the podcast. I think we had you on the podcast in the, in
the very beginning of when we started, WunderGraph some some years ago. And, for those
who don't know, Sergiy is our first engineer. I think the first hire. So engineer, number one and,
yeah, maybe you can, you can, walk us a little bit through, like what?
00:06:10:15 - 00:06:22:00
Jens
What is your, what is your journey with me? What is your journey with with, WunderGraph
because actually, we're we're working together for quite some time, right?
00:06:22:03 - 00:06:48:23
Sergiy
Yeah, just about like five years or so. I consider it like, a quite a long time for, for being on the
project and like, a, I have a Guerrero or like, probably 14 years already. And, this is just my last
longing product, which never ends, actually. And, I always have work to do, and it is very
enjoyable.
00:06:48:23 - 00:06:54:17
Sergiy
And, I get a satisfaction from doing this job like, it's it's really cool.
00:06:54:19 - 00:06:55:25
Jens
Yeah.
00:06:55:28 - 00:07:31:15
Jens
I remember so Sergiy and I, we met at Tyk Technologies. It's an and a company, headquartered
in London, I think, with, a remote culture, which allowed, Sergiy from the Ukraine and me from
Germany to actually meet and, they have an open source API gateway, it's written in go and like
many years ago, I think around 2018, I wanted to dive into the world of, of GraphQL and build
some tooling.
00:07:31:15 - 00:07:53:08
Jens
And I saw that there is not so much tooling for GraphQL and go. So I created GraphQL go tools,
and I took it and went to to Tyk and applied there for a job and said, hey guys, you have an API
gateway in go, I have a GraphQL library in go, we should put it into your gateway.
00:07:53:08 - 00:08:15:10
Jens
And then somehow I got the job. I actually created the job. That job didn't exist. And there was
this guy Sergiy in another team. And I think in the beginning, you you you were not immediately
convinced that this is the thing or like, do you remember, like the early days?
00:08:15:12 - 00:08:16:12
Sergiy
Yeah, I do, but.
00:08:18:16 - 00:08:42:14
Sergiy
It is not like that. Basically, it was a funny story because like, I got asked by, my team that like,
do I know GraphQL? I said, of course I know it. I use it on one project, but I just didn't know into
what I am subscribing for and, like what it will be. And then, I started working on a first task, like,
and,
00:08:42:17 - 00:09:10:25
Sergiy
Yeah. Just a whole nother world like this, I think, like brilliant GraphQL spec continuously
digging into it. Yeah. And, one of my comments was that I split a couple of files into plenty of
files, like, Jens has a drawback that, he likes to, bootstrap something very quickly. And, when
the code grows, just the file grows.
00:09:10:27 - 00:09:44:27
Sergiy
And when you have just a single file with 10,000 lines, it's just unmanageable. Yeah. So, yeah,
my, my first job was like, just to split that files into smaller ones and, yeah, five years later, I
could say that, I own like, 60% of the project because, Yeah, I don't share this, currently with
anyone other like and, yeah, I'm very into this project because, yeah, I have written a lot of
things and, we have created a lot of things.
00:09:44:27 - 00:10:23:15
Sergiy
New things, because it's all things, we made like, as much close as possible, to conform with
GraphQL reference, implementation in JavaScript. We align it, most of the validation rules, we
try to be compliant. Of course we are different because we are just not regular old GraphQL
library. Like, it is not like a GraphQL, GraphQL gem, which is the factory standard and, good
development tool, built in GraphQL.
00:10:23:17 - 00:10:49:03
Sergiy
It always was like Samson on top. And, when you work on the actually GraphQL gateway, it's
quite different from the API gateway or just from regular GraphQL server because you have like
so, so many other like complex things and challenges which you need to accomplish and, to
make work. And yeah, it's really, endless thing.
00:10:49:06 - 00:10:58:12
Sergiy
You could improve it more. And we always have new ideas and, yeah, it's quite, quite
challenging and quite interesting job.
00:10:58:15 - 00:11:29:12
Jens
Sergiy and I, we have this, this internal joke that I keep bootstrapping new projects. And
because, I'm usually, I have a lot of meetings and I'm very time constrained, so I'm, I'm typically
in a hurry. So I build something like rather quickly and, I create, like, not files with 10,000 lines,
but I, I, I don't know why I have a tendency to just add more stuff to the file.
00:11:29:14 - 00:11:53:23
Jens
And then after a while, when it turns into a real project, then Sergiy, goes after my code and he
rips it apart into a, well, maintainable structure. So yeah, I'm like the the little speedboat. And
Sergiy is a bit more, I don't know, he he he, he's like a gardener or I don't know, he, he takes
care of the, of the chaos I created.
00:11:53:23 - 00:12:23:06
Jens
So yeah. But yeah, it's it's it's interesting how long we are already together and, one, one other
question I have is like, you know, WunderGraph, GraphQL, Federation. GraphQL go tools, the
library we're working on, this is what we're doing. But the way or the, the constraints we're
operating on, it's still that we're an early stage startup.
00:12:23:09 - 00:12:45:09
Jens
So maybe, question to to David. What what is your experience so far? What what is unique
about working in an early stage startup? What makes it different from from other jobs?
00:12:45:11 - 00:13:12:10
David
Like, I don't I'm not sure that's actually the correct question, because startups can vary quite
considerably. Of like, of course, our startup is, I would say quite fast paced. I mean, a lot of
startups are, but even then, like we release multiple times a day, sometimes we, we releasing
features and fixes and whatever else, all in just a day's work.
00:13:12:12 - 00:13:40:00
David
It's great to be able to get things out to customers quickly as opposed to having, a lot of red tape
and processes that prevent you from shipping things out. And of course, red tape and processes
are there for the protection of the customer. But, when as long as you have a good QA system,
and the tests in place and such, getting things out so that people can actually use them and get
feedback and whatever is really valuable.
00:13:40:03 - 00:14:06:20
David
And the feedback loop as well, is something that. So in my first in my first job, I worked at, a
financial, testing software, testing financial software. So like the customers with, with visa and
Mastercard and things like that, banks and places and, we would often get tickets on we used
Jira then, luckily we don't use Jira now.
00:14:06:23 - 00:14:31:27
David
No shade on Jira, but I don't like Jira, we use linear, and, we would get tickets in and said like,
oh, Mastercard have asked for such and such a thing. But the actual people talking to
Mastercard, were not the engineers, they were, I guess the product owners or perhaps support
teams were talking to those, and then they would have an idea of the what
00:14:32:00 - 00:14:58:19
David
Mastercard wanted or whoever the client was. And then you would kind of implement that
feature request. But, there was one time I remember where I was actually able to ask, this this
company was actually Mastercard. What is it you actually want for this? What do you want to
achieve with this? And what was in the ticket with the specifications were actually a little bit
different to what they actually wanted.
00:14:58:23 - 00:15:13:29
David
They were trying to solve a problem and they thought that we had to solve it one way. There
was a better way to solve it. And if I was able to have that conversation directly with that
customer, it would have saved, I think, a lot of time, and it would have proved for a better
solution. It would have been a tailored solution.
00:15:14:02 - 00:15:36:05
David
And what I really like about it, wundergraph is that we as engineers have a direct line to not only
the engineers at the customers that we provide services for, but their managers and their
product owners. And we directly get all the feedback, all the things that they have to say about
the product, what works well, what could be improved, and what doesn't work, for example.
00:15:36:12 - 00:15:56:10
David
And we can get that feedback feedback loop directly, get the feedback on the code. And it really
drives you when you know what you're building is being used. And you can ask about how
they're finding it or, and what you could do better or like just even the comment that, oh no, this
is working great. Thanks for the quick fix.
00:15:56:12 - 00:16:19:07
David
It really boost morale. I think it's perfect for the engineer involved. It's perfect for the customer
involved. I couldn't imagine if I ever were to have a join a different company for whatever
reason, I couldn't imagine another space where I would not want to have this exact feedback
direct feedback loop with the customer. I think it's completely is absolutely priceless.
00:16:19:09 - 00:16:22:18
David
And, it's one of my favorite things.
00:16:22:20 - 00:16:46:22
Sergiy
Totally agree with. There's like, I worked for quite a long time and never had like to actually
such, such speed train on this, this reaction. It's really reactive. No, not on rocket way, but, yeah,
you know, totally unique way. And, it's, great feeling like you see you have immediate impact
and you.
00:16:46:22 - 00:16:47:24
David
Could.
00:16:47:27 - 00:17:25:29
Sergiy
Bring some something new very fast and you could fix, of course. And in case, there was any
problems and, yeah, everyone is satisfied. Like, we as developers, our customers, as our
customers. Yeah. It's really unique situation, I believe, because, not so many, like, startups or
libraries or whatever have, such a quick feedback like we are open source, but, it also, like, has
a different situation, like, we also have customers and this feedback loop is awesome.
00:17:26:06 - 00:17:47:20
Sergiy
And even, you know, open source contributions, usually they taken just a bit longer to
accomplish something. But yeah, people also love that we, try and thought about fixes that we
respond to and we provide guidance sometimes. And, yeah, it's really unique project to work
with.
00:17:47:22 - 00:18:14:04
Jens
Yeah. I would say like from, from a startup perspective. So this was like the engineering
perspective, but from, from a startup perspective, you know, sometimes, like, for example,
investors, they ask you like, what is the moat of the company? And this is especially an
interesting question when you have a lot of open source code, because now you could say, well,
the the code cannot be the moat, right?
00:18:14:04 - 00:18:40:24
Jens
Because it's open source. Everybody could just take it and run their own router. So like what
what is the product? And the one thing I would say to this discussion is, I think a huge part of the
moat is the velocity, because yes, you can you can run cosmo yourself, everybody it's it's open
source. But, do you have the expertise and the velocity to, to, to quickly change it?
00:18:40:24 - 00:19:27:01
Jens
And I think for, for a startup, one, one of the big parts of a moat is the ability to quickly change
code. And what, what pays into that is maintainability. And for example, one one very big topic
that we're currently heavily investing in is reliability. So we're we're currently building, for
example, one, one tool that can preview query plans, because we, we came to realize that,
when you have very, very big customers with large deployments and you want to you want to
work on the the query planner, or you want to work on composition, or you want to change the
router in some way, like it's software, we want to
00:19:27:01 - 00:19:56:15
Jens
change it, we want to improve it, but you never want to break something. And one super
important piece of that is we want to ensure that query plans don't have regressions. So we, we,
improve query planning or composition in some way. And we want to ensure that it doesn't
break anything. So one thing we are currently, building and we actually as part of that yesterday
we, we released new functionality for the router.
00:19:56:17 - 00:20:19:11
Jens
The router can now run in a headless mode where you can feed it from the file system, a
schema or an execution config, but more or less it's just a schema. And you can feed operations
and then you can, in the, in the batch plan the operations so you can see how will the query
plans look like.
00:20:19:11 - 00:20:41:23
Jens
And can I plan all the queries and then you can you can do this step for different versions of the
router. For example, if you make a new release you can you can test two router versions. Or if
you change a subgraph you can run this process with two configurations. The previous
configuration and now the new configuration with your new subgraph.
00:20:41:25 - 00:21:16:05
Jens
And then we can compare the query plans. And this is like a safeguard to say like okay, we're
we're a big company. We have over 1000 queries in production. We're making a change. Will
the query plans look like we expected? Because let's say you put, an override directive or
provide directive for something, and you guys are the expert experts, like, tell me a little bit
about what what happens if I use directives like, provides external override.
00:21:16:06 - 00:21:23:08
Jens
Like what? What can it potentially do with query plans?
00:21:23:11 - 00:21:53:23
Sergiy
Yeah. Like query plans itself. It's, rather big topic. And it's, yeah. Well, one of the good things
and, I'm glad that we were all inspired by Apple in that way. Like, it's a visualization of query
plans, like human readable version of query plan. It's very good to understand what's happening
like and what what fetches, you are doing in what way you fetch in like, in parallel or in
sequential way.
00:21:53:25 - 00:22:21:12
Sergiy
And, by using federation directive, by the Federation nature, all these directives there define the
behavior of the, how you resolve data. And by using overrides, you can basically change in the
place of a field where field be resolved. And it has a direct influence and query plan because
you, constantly will move the place from where these, fields, would be resolved.
00:22:21:14 - 00:22:44:15
Sergiy
But when you use that, you have to consider that, this field, it could be used in some required
directive and some other subgraph, and it's required by the subgraph, for example. So you
move it to another subgraph and basically you have another chanin of request because you
need to fetch this field from totally other place. But, it will be required only when you query
fields.
00:22:44:15 - 00:23:09:28
Sergiy
This has this requires configuration. And at the same time when you, for example, just put
requires it will mean that always when you when you request this field, you will have to request
some consumption from other subgraph. And requires. Doesn't make a lot of sense when you
do have full data locally in a subgraph and in binary to we just reflected that there will be no
outside features.
00:23:09:28 - 00:23:36:13
Sergiy
You have all data just right here. And at the same time you have provides directive, provides
directive, source purpose of like optimizations. It very chain. And it is actually rather hard to,
make it usable and to place it, exactly where you need it. Most of the cases, you just would see
that. Okay. I always need this field.
00:23:36:16 - 00:24:18:19
Sergiy
And why not to make it provided like usually I need to fetch it from the other subgraph. But
maybe my system has access to this field. So I'm placing my provides directive. And basically
we will be fetching this field on this given parts and, and like, fro from the root query parts or
from some relative parts to the entity, we will be fetching this field, like from this place now
because, it is available, but not all people know that basically, provides, is an optional
optimization and, there could be very rare situation when actually you have a provided node.
00:24:18:21 - 00:24:44:24
Sergiy
But you want to fetch it from that, subgraph where it was provided because it's not beneficial to
do your fetch to this subgraph, because basically all the, all your other fields, come into another
subgraph and this, another subgraph also have this, field, and you just don't want to fetch the
fields from two places. You just will do one, one single fetch.
00:24:44:27 - 00:25:04:03
Sergiy
Yeah. This is like from my point of view. But, also like you, you're working with, composed graph,
like federated graph. And it also has an additional meaning, not only for the execution, but, I
think David could add more on top of that.
00:25:04:05 - 00:25:35:03
Jens
I have one, one question. If we take one step back. So there's various terms. So we have
federation, then we have something that a lot of people, they talk about composition. Then we
have super graphs. And we have in in in Cosmo we have something we call execution config.
And how do you. Yeah. And another term we use is query planning.
00:25:35:03 - 00:26:02:03
Jens
And then we have query execution. So maybe I don't know David Sergiy maybe you can you
can explain a little bit the the ecosystem and how it all plays together. Because from
conversations with you two,, one thing I learned is that actually query planning and composition,
they are kind of married together or they are somehow, somehow like they are two but one.
00:26:02:03 - 00:26:15:28
Jens
that.
But yeah, maybe, maybe you can explain a little bit the the relationship between you two, like
how you work together and what it means for, for composition query planning, execution, all of
00:26:16:00 - 00:26:20:07
David
So, sorry Sergiy.
00:26:20:10 - 00:26:28:27
Sergiy
just a joke?
Yeah, just wanted to say, when you see how illusion is built, it's not an illusion anymore. but is
00:26:28:29 - 00:27:03:05
David
So. So how it works. How Apollo, how it works with Apollo is that composition runs and you get
a supergraph schema. And within that supergraph schema, you have all the encodings for
where a type comes from, which subgraph it comes from, other parts like overrides and external
and inaccessible and all these sort of things are all encoded within directives within the
GraphQL schema itself.
00:27:03:08 - 00:27:26:19
David
And so then, I'm not fully aware of the internals, but then the, the, the roots are all the gateway
all the Apollo gateway all then consume that schema and read those encodings from the
directives, and then do that to plan the queries. And whatever and how, WunderGraph does it is
that essentially composition does its thing.
00:27:26:25 - 00:27:50:18
David
And while it is doing its thing, it builds up, a bunch of metadata. And that metadata is then,
translated transposed into some, JSON. Well, first of all It's transposed into, into protobuf and
then into a JSON that, is read by the read by the, consumed by the router to then help with
planning.
00:27:50:21 - 00:28:28:25
David
It's doing very similar stuff to what the Apollo directive encodings are doing, and not exactly the
same, but basically you're trying to provide as much as as much information is necessary to
actually plan the query, from the relevant places in, in that JSON. Just like you're trying to do the
same in, in Apollo with the, the super graph, with the encodings in the directives, so that
essentially you can have a query that or an operation that plans and then, ultimately is executed
and that, JSON is what we call the router execution config.
00:28:28:27 - 00:28:50:14
David
Because we actually have a router config which is actual configuration for the router. But then
there's this other configuration, which is the kind of the read only configuration, that the router
needs to be able to plan. And it was getting a little bit messy with those two terms
interchangeably referred to as the router config. So we have the router execution config the
JSON.
00:28:50:16 - 00:29:09:07
David
And then we have the router config which is the user defined variables and such that they can,
change how the behavior of the router, whereas the read only one is created by composition,
read by the router, and then used during, operation planning. If sergiy wants to add if.
00:29:09:09 - 00:29:47:17
Jens
If I remember correctly, when we started out, our composition was very much the same like
Apollo. So you have subgraphs, you mesh them together. Super graph, super graph in in
GraphQL SDL. And if this is incorrect, just correct me. But so this was when we started out. And
then over time I remember that, you started working more and more closely together, building
ties between composition and query planning, and you started moving some logic into query
planning, into composition.
00:29:47:20 - 00:30:06:14
Jens
And you provide this in this structured way that David just explained to in the config to the, to
the, to the query planner. Can you explain a bit like you could just do it during query planning or
like what? Why are you doing it this way?
00:30:06:17 - 00:30:34:02
Sergiy
But basically we always for building federated graph SDL, a compose schema for a full big
GraphQL schema for subgraphs. This step is still still there. We just, don't have any additional
metadata there, but we always need schema because, like your queries will be distributed
against schema. And actually there was a two versions of this schema because it could be
slightly different.
00:30:37:16 - 00:31:29:19
Sergiy
In our approach, we, we decided that it will be a bit more simpler to offload some job into the
composition just because, composition doing a lot more checks than the planning needs to do.
And, planning is very much simpler. Like, during composition, you have, a full graph of all
possible fields, all possible types, queries, whatever or whatever to be able to display error
messages to understand, like what is possible jumps between subgraphs, what is the relations
between them when you, work with this query planning, you know that, this query is, almost
always possible to plan because we already check it's composition time that, this query
00:31:29:19 - 00:32:20:15
Sergiy
is possible because composition, actually checking that every possible field is possible to
resolve. And this called this, like resolvability check or satisfiability check. Like, in our case we
just name it as a resolvability, but it doesn't matter a lot. What term to use. Yeah. And, s,
composition has this information. Why not to just pass it to the, engine side to the execution
configuration and just make work of the planner and, the in the config much faster and much
more simple, because you could gather a lot of metadata and it will be just there and you could
use it easily.
00:32:20:18 - 00:32:55:27
Sergiy
The funny part that, we don't even always need to read the subgraph graphql schemas.
Sometimes in the planning we just read the metadata because, yeah, otherwise, anyway, you
will need this information to do something like, for example, you need information like, what is
entity nodes, what is their root query type nodes like, from where you could start the query from
where you can start to query, you need to know, is field external or is this field is provided.
00:32:55:29 - 00:33:26:00
Sergiy
We need to know like, what what keys do I have? Like, and yeah, it is possible to do all that,
when you just loading files, but it will be double work, basically, because we already have done,
every bit of that, almost every bit of that information already was done in the composition. Like
why we would need to replicate it again and, in the, query planning stage.
00:33:26:03 - 00:33:52:15
Sergiy
If we could just use this data. But the important thing, thing, thing here is that, our composition is
built with, TypeScript and execution engine built in in Golang, And, yeah, it will be a huge
investment to build composition in go or to build to, execution in TypeScript. And which do not
have any sense for us right now.
00:33:52:17 - 00:34:18:27
Sergiy
And, TypeScript really allows you to iterate very fast. Like, I had a previous experience of being
a Ruby developer, and, yeah, each time you start a new project, you just bootstrap everything
very fast. And, during, our testing, we always, use JavaScript subgraphs because it is very fast
to build some mocks, to build some subgraphs.
00:34:18:29 - 00:34:42:16
Sergiy
And, yeah, it is convenient way, it is not fast to execute, that in production, but a lot of our
customers are still using it. But, yeah, it works for us. And, there was some questions from some
of the customers. That's why we don't use the same format as, other gateways doing.
00:34:42:18 - 00:35:11:12
Sergiy
But that format is not that useful for us. Like, we, we won't get the same benefits of having this
format because, yeah, we still will need to process it and to create metadata. And it is more
convenient for us to work with, not in interchangeable format, but in case you use our
composition, you just have everything built in, and it works just smooth.
00:35:11:15 - 00:35:13:05
Sergiy
This.
00:35:13:07 - 00:35:41:13
Jens
Yeah, I, I personally like to think about query planning a lot. It's a bit like a compiler. And so what
you're saying it's a bit like composition creates compiler hints. And then the compiler can do less
work. It can be less complex. The compiler can be simpler. Is that fair?
00:35:41:15 - 00:36:00:15
David
And say as much as possible because just because of the nature of composition, you have to
look at a lot of things, to, to be able to know that something can successfully compose. So
you're doing work there, like you have to know what's external. You have to know where fields
live and and how they interact with each other.
00:36:00:18 - 00:36:21:21
David
And the query planner to some extent also needs to know what fields are external. So if I if we
can do that work once in composition, and then basically save that result and pass it to the
query, you're saving that doing that work again, you do the work once and then you share that
work. And then nobody has to do the work again because it's already been done.
00:36:21:23 - 00:36:47:19
David
And we and we basically do that as much as, as much as possible. And, and and like you say,
offer that in terms of how, what's in the, what's in this, JSON what's in this metadata to be able
to for the router to consume that and then eventually by the engine from the router, to produce a
result basically as efficiently as possible with as little work done twice as possible.
00:36:47:21 - 00:37:04:13
Jens
Yeah. So that that kind of means if you have a super graph structure that doesn't contain all this
information, you at some point you probably have this information, but you threw it away. And
now query planning needs to do it again.
00:37:04:15 - 00:37:33:08
Sergiy
Yeah, it basically will sometimes you anyway will need to read or recreate the structure of the
subgraphs like, but when you or when you have just a single schema, you probably will
decompose it again into a single subgraph to see what is actually valuable. The, you will build
this representations of subgraphs, probably in programmatic way.
00:37:33:10 - 00:37:58:18
Sergiy
And, we kind of doing that, but we mostly just, reading this information and yeah, we still have,
subgraph information and, we still have access to the, original subgraph schemas, because
sometimes you need to see, like, how it was, define it. And in this particular subgraph, like
sometimes you do not have a direct match on a field.
00:37:58:20 - 00:38:24:02
Sergiy
Like, for example, you could have interface define it in one subgraph and all the same field, it
will be just, just a, sum of the concrete types of this interfacing on the subgraph. And, it will
work. But, during the planning, you need to say, like, could I just plant this type on this,
subgraph or should I just remove this selection set because it doesn't make any sense?
00:38:24:04 - 00:38:51:28
Jens
Yeah. What one thing that you guys keep talking about, and I keep hearing this, and I kind of
find it funny, is you keep talking about jumps and the. It kind of reminds me of, like, like science
fiction films or something, or a portal where you do, like a jump to something else or can you
explain it with like, well, what is your what is your idea behind jumps?
00:38:51:28 - 00:38:58:04
Jens
And how is that different from how other people think about Federation?
00:38:58:06 - 00:39:26:28
Sergiy
As a consumer federation, you just see a single schema like you file the queries like you have
all data in one. In one place and from outside versus the consumer. You just from, just talking
with one single graphql API, but, underneath you have multiple services and, you could have
subgraphs which have, root queries and which just do not have route queries.
00:39:26:28 - 00:40:02:15
Sergiy
It's, it's they provide some fields to their, like it basically contributes fields to the federated
schema, like whenever you have type user and maybe you have, addresses service which
provides you with an address. And this is like, Federation itself with kind of microservices
architecture. And when you design, designing, federation, schema or federation subgraph, you
typically want to isolate some, some kind of behavior or some kind of information and move it to
its own microservice.
00:40:02:17 - 00:40:33:22
Sergiy
But then, you need to be able to fetch that data and federation, standardize this way. Like during
my tenure, I have, a, I have seen a lot of approaches when you have just one GraphQL schema
from which is front facing and,under it you have a microservices and, this service with,
GraphQL, it's actually in its resolvers.
00:40:33:25 - 00:41:11:13
Sergiy
It's calls your PC. It calls multiple services and gathers this data and federation. And just
another way of, how you could fetch this data between different services. If we will talk about
what jump it is, jump is an event when, you get all the fields from the current subgraph and you
don't have any fields anymore, and you need to, fetch the fields from another subgraph, but
there is a rules for this jumps and that, basically in Federation, we have kind of unique
identifiers.
00:41:11:13 - 00:41:39:02
Sergiy
And, it is called keys. And, keys would consist of one or multiple fields or maybe set of nested
fields. And basically you need to provide this information to the second subgraph. And when,
you know, calculating jumps in composition, there is additional rules apply. So you, not always
will be able to jump to that subgraph.
00:41:39:04 - 00:42:06:15
Sergiy
And, that is why, like a shareable directive exist, because you could share responsibility resolve,
this field between different subgraphs. But then at some, to some degree, you could control like,
do you really want to jump to this subgraph or do you want to jump only from this subgraph?
Like, is it good accept inbound connections or will it be just only outbound jumps?
00:42:06:18 - 00:42:34:15
Sergiy
And, the most easy way to do that is just to use resolvable false, for example. And it make entity
not, not accepting incoming, incoming request just because you have no way to resolve an end
to from the subgraph. But you could easily jump from this subgraph. And, in this case, like you,
anyway, you will have some root query.
00:42:34:17 - 00:43:07:22
Sergiy
And, this root query, it will be just query mutation or subscription. And this means that your
request almost always will start from some particular subgraph, of course, unless you make this
query shareable. But, for sometime, seeing that it's not a good approach to make root query
field to shareable thing like, just splits responsibility between different subgraphs and, yeah, it
could be a bit weird to do that, but yeah, it is possible.
00:43:07:24 - 00:43:29:14
David
Yeah. To to add on what sergiy said like I like to think of this, is that you have an entry node.
Every GraphQL API has an entry node which is going to be your root of root field. So a query a
mutation or a subscription. And in federation your interface layer is your federated graph. But
under the hood that root field belongs somewhere.
00:43:29:14 - 00:43:57:01
David
It's owned by one subgraph or perhaps more than one subgraph. And that's your entry node.
And then you can think of your lateral jumps to other services as being edges, on a graph. So
you have your bespoke and you have a subgraph which is a bespoke graph. But then there are
these edges between different services in the shape of shared root fields, shared fields and
entity jumps.
00:43:57:03 - 00:44:18:01
David
And these are the edges that allow you to go from service to service. Which is all kind of, I
guess, abstracted away the client and the consumer to see this federated graph. But under the
hood, you have all these links in different ways between different, subgraphs. And we can kind
of refer to those as jumps, these edges between the services, the jumps.
00:44:18:08 - 00:44:23:04
David
And they can be entity jumps and they can be shared field jumps.
00:44:23:06 - 00:44:26:08
Jens
That's just one. Sorry. Go ahead. So you.
00:44:27:25 - 00:44:57:27
Sergiy
Just wanted to mention like, David just, described the, one main difference between, like, what,
metadata do we have in composition and what data do we have any query planning like at
composition type. Do you have like a full blown sub, graph? Like you use graph theory to do that
basically. And, you know, all entry points, you know, all all possible connections.
00:44:57:27 - 00:45:22:04
Sergiy
You have all these edges. But, when you do query planning, you basically have a query and it's
already determined, like, what is entry point is and query planning and just use tree structure.
It's not not a graph. It's more like a kind of directed graph, which has layers. And you go layer by
layer and see what is possible.
00:45:22:06 - 00:45:32:04
Sergiy
Like, it's a bit different context of, what data do you need? And what things are you checking
00:45:32:06 - 00:45:36:06
Jens
You just brought up an interesting thing.
