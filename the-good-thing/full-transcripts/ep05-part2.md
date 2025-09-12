00:33:51:09 - 00:34:19:28
Jens
So in my past life I was a consultant and if you're an external consultant, if you get a ticket, your
goal is to write something into the ticket. That's not offending, that's not negatively affecting any
relationship. That's politically correct, but you really want to get it off your table. You want, do
you? You don't want to have open threads and you do.
00:34:19:28 - 00:34:42:22
Jens
So you get the question. You answer the question in some way and you throw the ticket away.
And not my the I don't care. So I didn't do that, but I asked them like, a couple of questions and
then I realized, okay, I want to huddle a with this person. So I huddle with this person.
00:34:42:25 - 00:35:25:00
Jens
Luckily they, they, they are open. We we started the discussion. It's a health care company.
Healthcare companies are super concerned about security and HIPAA. And one aspect of that,
this is personal information. And so what they, what they were looking at this when there is a
problem with a doctor or a patient and they report this problem and the developer wants to
replicate this, they want to they want to mask data because the, the developer shouldn't see,
like the date of birth or something of a patient, like that's the as a healthcare startup of you
cannot do it.
00:35:25:03 - 00:35:58:03
Jens
And his thought was that wouldn't account would provide him a custom module. So we're a
module system so that he can build his customization to handle PII and to mask the data. And
my thought is, or the way I think is, how can wundergraph build a native or offer a native
solution to handle PII? Because I think it's is it is our responsibility as someone who provides a
router.
00:35:58:06 - 00:36:27:03
Jens
Yes, that the router understands that certain fields in your GraphQL schema are PII, and if the
user is a developer and they have a certain JWT with certain claims and scopes, that under
some conditions, because it's the real user, they can see the unmasked data, but if it's
developer they shouldn't see the data. You should mask it. So and I think like PII that's a it's a
problem that's everywhere.
00:36:27:06 - 00:36:51:27
Jens
The router should come with a native solution. So we're now collaborating on the on on how can
we build a native solution instead of just saying yes, build the middleware. And that's that's
simply I think I don't know, it's so simple to move your start up forward. Just just look at what
people are trying to do.
00:36:51:29 - 00:37:13:21
Stefan
Yeah. Talk to users. One thing that you mentioned that was like we don't really focus on
competitors, we focus on the customers. And a cool antidote is from back in the day. There was
a board meeting at Amazon when Jeff Bezos was CEO and, Amazon was profitable the first
year. And then in year 3 or 4, they really took off in the early 2000s like they were crushing it.
00:37:13:24 - 00:37:32:26
Stefan
And so they were having a I think that they even went public. So let's say they were a publicly
traded company and they were so far ahead in the e-commerce space in books that Barnes and
Nobles, which is one of the biggest retailers for books in the United States, they started
launching a online website to sell books, basically what Amazon is doing to compete with them.
00:37:32:29 - 00:37:52:26
Stefan
And a lot of the employees at Amazon got worried. Oh my God, like, oh my God. Barnes and
Nobles has so much distribution. Like we're a startup, how are we going to compete against
Barnes and Nobles? And one of the things that happened was, Jeff Bezos wrote a memo to the
entire company, and he says the way we win against Barnes and Noble is by focusing on the
customer.
00:37:53:02 - 00:38:11:14
Stefan
We don't give any attention to Barnes and Nobles, and we just focus on the customer. And he
kept doing that throughout the years at Amazon. That if you focus on the customers, if you have
the conversations with them, if you don't try to solve the problem, but instead learn exactly what
the problem is, is that this is how you scale your startup.
00:38:11:14 - 00:38:36:03
Stefan
And that's literally the definition of founder mode. He kept it from the beginning, all the way up
until the end. Now it's a little bit tougher, but they're still have that mantra of listen to the
customer. And so this is a great point to talk a little bit about competitors. So yeah. So Jens
have a copycat competitor. Literally if you guys have seen Borat where it's like we implement a
router, they implement a router, we implement this, they implement that.
00:38:36:09 - 00:38:57:15
Stefan
We have customers. They don't have customers. No I'm kidding. But jokes aside, we have a
competitor and they do false marketing. And me and Jens are having a debate about this. And I
want maybe if the audience wants to chime in. But my take on this is if a competitor is doing
false marketing and saying false information about your startup, you should correct it.
00:38:57:18 - 00:39:14:24
Stefan
You should call them out. And then yeah, and you have your opinion on this. You can give it if
you want, but yours is. Don't even give them any attention. But what do you think about that like
and also it's a good transition. There was some drama on Twitter this week where a really big
what series B startup.
00:39:14:27 - 00:39:23:22
Stefan
He started causing drama about a competitor that was doing false marketing. And for me, I don't
think that there's a way to win. What do you think?
00:39:23:24 - 00:39:28:15
Jens
So many topics to unpack. Well, where do we start?
00:39:28:17 - 00:39:33:22
Stefan
Whichever one you want, we can start with founder mode, or you can start back with the
competitors.
00:39:33:25 - 00:40:21:08
Jens
Okay. Competitors. So, so one, one thing like, I don't know, it's it's like, it's just my playbook.
When I have a much bigger competitor, it's it's okay to say that name. It's okay to sometimes
compare with them. But I also try to be not too impolite. Like, of course there can be some
banter, but no enterprise ever really like WunderGraph when the founders or the people of
WunderGraph shits on Apollo like.
00:40:21:10 - 00:40:54:28
Jens
I don't know, it's you can't it shows. It shows something about you. Like you can compare and
maybe. Yeah, but it's a, it's a gray zone. And then there's another thing. If you have smaller
competitors, people copying you or something. My my simple rule is to to never use the name of
the company and just pretend they're not there, because my, my assumption is why should I use
my audience to give them attention?
00:40:55:00 - 00:41:02:10
Jens
I said? But way,
So I have the my network. I have my audience like they they don't deserve it. Did you hear what
00:41:02:12 - 00:41:06:27
Stefan
I you know who always says that? Like, why should I use my audience to give you attention?
00:41:06:29 - 00:41:07:20
Jens
Nope.
00:41:07:23 - 00:41:10:07
Stefan
Your buddy Theo, he's always saying that.
00:41:10:09 - 00:41:41:19
Jens
Yes. Okay. Yeah. My my my best friend. Theo. I met him in person. It wasn't just a good day,
okay? But. And and then there's this thing about these data base companies. And I think one
thing we need to be super careful about is, benchmarks. So for many years now, I have
benchmarks on my computer to compare all the different graphql gateways, like all of them.
00:41:41:21 - 00:42:11:09
Jens
And I do little tweaks and tests and I, I know a lot about how they behave. And I'm I really love
benchmarking on my own, but I have never committed this anywhere, and I'm not intending to
publish it for a simple reason. Everybody who knows enough about benchmarking also knows
that I can benchmark. I can define the results and benchmark backwards if I want to.
00:42:11:09 - 00:42:41:04
Jens
Everybody can do this and I don't know if you benchmark like a database, and one database
has cold starts and one database doesn't have cold starts, yeah. Well, what are you expecting?
And then I don't know why. Why create this kind of drama? To be honest. Like, we we are. We
are a super boring company. Just deploy a Postgres database.
00:42:41:11 - 00:43:19:17
Jens
No serverless Postgres. Just a boring Postgres on GCP, Azure or AWS. It's always on, it costs a
few bucks, but we have users. Who cares? There's no cold start and I don't need to benchmark
it and I can trust it that it works. And yeah, okay, there's maybe other solutions, but maybe, for
example, this is not advertisement of sorts, but with neon you can have like serverless,
databases and you can have branches and other things.
00:43:19:19 - 00:43:41:26
Jens
And the benefit of a serverless database can be, that you can have many of them and they don't
cost you something when they are asleep. And they they might have a cold start or Prisma or I
don't know, I don't care about databases, but let's say you have a cold start. Use the right tool
for the right job.
00:43:41:26 - 00:44:12:28
Jens
Like if you need 10,000 databases but you rarely use them, maybe that's good. We need one
Postgres and it it should be fast. And we want to have a boring, simple solution. We just use
AWS or GCP like. But the one thing I would really avoid with these benchmarks is, I actually I
tell a trade secret, no.
00:44:12:28 - 00:44:37:13
Jens
Do it. Yeah. The reason I'm not publishing benchmarks where other gateways look bad is, I'm
not giving away my knowledge. Like, if I show you where your gateway is really bad, it means
that I'm pointing you exactly to where you have to improve. Like, I'm not gonna do that. Like.
Yeah. No, I was.
00:44:37:13 - 00:44:38:17
Stefan
Wondering when you were going to say.
00:44:38:17 - 00:45:03:06
Jens
That. So, I don't want others. Like, my product is better, but I don't have to tell you where, like,
you have to figure out on your own and, so, I don't know if someone publishes a benchmark
that's like, please beat these results. Like you urge the competition to act like, why do it? Keep it
to yourself.
00:45:03:06 - 00:45:06:08
Jens
Like, I don't know. It's it's not smart.
00:45:06:11 - 00:45:24:16
Stefan
I agree. For me. What I don't understand with benchmarks is like early in the journey is people
would ask us for benchmarks against a competitor, and me and Jens hated that question
because it's first of all, I honestly thought it was kind of lazy. Like, do the benchmarking yourself.
Like, here's how you can do it, spin it up on yourself and run the benchmarking yourself.
00:45:24:18 - 00:45:47:08
Stefan
But also we always said this a customer never complained about performance. Like it's very
fast. It's trusted by some of the biggest enterprises in the world, but they're like, oh, but this
one's a little bit faster. And for me, I don't know, it kind of annoys me with benchmarks because
it's exactly what you said. Every benchmark, the vendor can manipulate it to make themselves
always look the best it can use.
00:45:47:08 - 00:46:06:21
Stefan
cold starts. It can use a outdated version of the gateway. I don't understand even why there's
any relevance to benchmarks, and why do developers like it so much. And the biggest thing for
me about performances, you think of these things at scale, but the second you start thinking
about it, before you even have any users or any customers about it, I think that's waste of time.
00:46:06:21 - 00:46:11:25
Stefan
Like, why are you worrying about the performance when you should be worrying about the
customer? What do you think?
00:46:11:28 - 00:46:18:14
Jens
Yeah, and that's another thing. So benchmarks are very concerned. What's the right way to test.
00:46:18:18 - 00:46:20:07
Stefan
synthetic.
00:46:20:07 - 00:46:53:19
Jens
Synthetic. Yes. Synthetic. Because so we just recently built a new feature cache warmer. It's it's
so cool. So you run routers, they send telemetry data to our telemetry collector, and they tell us
which queries is this your router planning and how long does it take. So we put that into a click
house and we create a top end list of queries that take a long time to plan.
00:46:53:21 - 00:47:26:04
Jens
And we we every day we rebuild this list, put it on the cdn. And when the router starts or gets a
new config, we have to invalidate all caches. We have a query plan, a cache normalization,
cache validation cache. So we invalidate all these caches. Then we take this list and we pre
warm based on this list, based on the traffic you had yesterday and the queries that were worst
to plan based on that we warm up the caches.
00:47:26:06 - 00:47:51:05
Jens
And now when you get these requests that are really bad in planning time they hit the cache. So
that means we take we get the request, we parse it and then we execute it. We don't plan and
plan. It can take milliseconds. It can take sometimes seconds. In really bad cases it and it takes
CPU time. Io is cool I o means router waits.
00:47:51:08 - 00:48:19:28
Jens
Awesome. We can wait. We have go. We have goroutines we can wait. So like thousands of
requests we can write but CPU it's limited. We don't want to wait for a CPU because like we can
only have so many CPUs. So with this approach, in the real world scenario, we were able to
help the company go through Super Bowl without crazy flakiness on the router setup.
00:48:20:01 - 00:48:58:15
Jens
However, if you run your synthetic benchmark, you you will never see this kind of stuff because
you're you're benchmarking like how much RPS can I hammer the router with one single curry
where the subgraphs are just returning static data? Like what actually are you testing? Like
that's not realworld, and in real world scenarios, when we talk about benchmarking, what we
actually need to do is let's say you are Super Bowl and you get traffic or you have Black Friday,
you get a lot of traffic.
00:48:58:17 - 00:49:26:29
Jens
So you have to ramp up your routers. You need to autoscale your router so more routers, if you
deploy new routers and the caches are cold, it means you have spikes in latency, spikes in CPU
time. So the reality is you need a solution that can cope with these kind of situations like scaling
up, scaling down, reloading the config.
00:49:27:01 - 00:49:48:14
Jens
And then if you look at the benchmarks, is anybody reloading the config during the benchmark?
Yeah, of course not. Because I don't know what they are testing. It's and the thing is if you ask a
customer like hey what are your need? Like listen to the customer, you know, it's always the
same thing. Listen to your customer doesn't say, oh, we want to hammer the router with the
same query.
00:49:48:15 - 00:50:14:18
Jens
No customer says, guys, we have a problem. When we scale up our routers, the caches are
cold and we have latency spikes. Can you solve that? So this is like a real world problem versus
just hammering a router with the same static query like it's yes, you can benchmark it and the
benchmarks can say something. But it doesn't mean in the end that this router will work.
00:50:14:21 - 00:50:17:26
Jens
On Super Bowl. I don't know.
00:50:17:29 - 00:50:34:15
Stefan
You hit so many good points there. So for one, the only people that do these benchmarks, the
synthetic ones, are the ones that feel threatened or they want to kind of do a little performance
thing, you know, like AWS doesn't run benchmarks. They don't have to. They're AWS. Who are
they going to like run a benchmark for?
00:50:34:15 - 00:50:57:17
Stefan
And so for me, benchmarks are synthetic. But to wrap this point home, what I think is interesting
is that if you collaborated with the companies on that use case for a Super Bowl, that's a good
benchmark because it's an actual customer one, but you kind of can't because it's your
customer that's the only way that a benchmark would work, because all these use cases are
complex.
00:50:57:17 - 00:51:15:25
Stefan
And, you know, with the pre warming cache and the traffic spike, that's important. But what's
synthetic about just hammering the router is that that's actually not a good benchmark because
it's not even a real life use case. You're not just going to hammer with the static query 150 times
and then measure the difference between Cosmo and whatever the other routers are in.
00:51:15:25 - 00:51:27:12
Stefan
And for basically benchmarks are just kind of BS. They kind of always are. If we could do them
collaboratively, I think it'd be great. But I also, I don't know if you can do them collaborative. Do
you think you could.
00:51:27:14 - 00:51:51:03
Jens
You just did a rookie mistake, but you're not a senior developer. It's fine. Like benchmarks are
useful. For example, I can run a local benchmark and I can enable pproff So pproffallows me to
analyze CPU usage and memory usage of the router. So I can enable people, if I can run a
benchmark, and then I can, for example, introspect.
00:51:51:06 - 00:52:10:13
Jens
What what is what is the number of memory allocations. How many objects have been allocated
and where in the code have they been allocated. And so it can help me as a developer to, to
optimize my tool and to also see like is there is the huge changes in behavior. But we have to be
like super careful.
00:52:10:13 - 00:52:39:27
Jens
And this is like one of the I would say big things I learned over the years of maturing as a
developer. There's micro benchmarks and there's macro benchmarks. Micro benchmarks is you
write like a go test and you micro benchmark, assume like a single function, and you then see
the allocations line by line, and you see where you spend CPU time.
00:52:39:27 - 00:53:10:00
Jens
And now you could go and optimize this function. And if you do this, what can happen? And it
will happen. If you're inexperienced you will optimize like so many functions and you will turn
your code into an absolute mess. Because like micro optimizations, the problem is let's say you
have a function and the function creates it allocates memory and that has to be garbage
collected.
00:53:10:06 - 00:53:33:21
Jens
So if you micro benchmark it it looks bad. So you're like okay, now I rewrite this function. I make
the code like typically code can be easy to read or fast. Like the faster you make the code, the
worse it reads. And that's you know, it's like, yeah. Do you want to be like super fast? Okay,
assembler. You want to be like somewhat slower and readable?
00:53:33:21 - 00:53:59:27
Jens
Okay. Go. And you want to be like faster, but use go okay, actually go. And yeah, you can write
super fast Go. And it's going to be more and more ugly, harder to maintain. And then you realize
something. This function in the broader scope, it almost gets never called. And so you micro
optimize something. You made the code harder to maintain.
00:54:00:00 - 00:54:19:26
Jens
But actually in the big in the grand picture, like let's say you micro optimize this and for each
request this function it creates, let's say ten kilobytes of of memory that need to be garbage
collected. And you know, like, oh, that's bad. Let's make it zero like zero garbage collection. Like
we, we build something amazing, okay. You optimize it.
00:54:20:03 - 00:54:44:21
Jens
And then in the big picture, let's say one request, it takes about 100MB of memory. So what is
ten kilobytes? Was it worth wasting your time in this function and then complicating this code.
And that's so yeah. You need to be very careful with micro optimizing stuff. It's sometimes it's
better to do like to do macro optimizing.
00:54:44:25 - 00:55:07:06
Jens
But even with macro optimizing like you're benchmarking the whole world and then you show
like the top ten memory problems. But even then you have this other problem of if you run pprof,
you would never see that when the customer scales up routers, the caches are cold. You don't
see that. You need to think about the architecture.
00:55:07:06 - 00:55:25:02
Jens
So if you want to make something fast, you can just benchmark your way to, you know, it's like A
B testing your way to product market fit. You can benchmark your way to, to to, good
performance. You really need to understand the architecture.
00:55:25:02 - 00:55:44:08
Stefan
And I think it's a good, like the way you explained it. From my point, though, it's not internal, like
we don't release our internal benchmarks, but we use them and we use competitors to make
our product better. But I think marketing benchmarks, I just think it illustrates a position of
weakness. And also you can always tweak them.
00:55:44:08 - 00:56:04:15
Stefan
And so that's my point on that. And then we are almost out of time. So last topic I want to talk
about you brought this one up. So you're going to have to lead it on this one. But Reddit is
always saying GraphQL is dead, GraphQL is dead. Or they're saying REST is REST. And
honestly REST versus GraphQL is a bit outdated, right?
00:56:04:17 - 00:56:05:09
Jens
Yep.
00:56:05:12 - 00:56:19:03
Stefan
And what are your thoughts on that? Like why is it outdated? Like why is this argument? To be
honest, it is outdated. Like it's I see all the time. If you want to get engagement on Twitter to
start talking about Rest versus GraphQL, if you want to get some upvotes on Reddit, make a
post about how it's outdated.
00:56:19:03 - 00:56:21:06
Stefan
But what are your thoughts on it?
00:56:21:09 - 00:56:56:07
Jens
Yeah, first of all, I think that the discussion is super boring and it's it's led by people who I I'm
sure they live in the past. So if if you look at what's going on in the market, the discussion
around REST versus GraphQL, what people are talking about is two styles of APIs, of how a
client can get data from a server, and then they argue things like over fetching under fetching
whatever.
00:56:56:10 - 00:57:25:05
Jens
And yeah, that that there are pros and cons. But ultimately what we, what we what we see in the
market today is, if you are a company that has grown to a certain size and they provide their
service to other companies like B2B, sometimes B2C, but more and more B2B, you do you and
others want to integrate with you.
00:57:25:07 - 00:57:52:01
Jens
It is typically very intuitive to use Rest APIs because back end to back end, it's it's not beneficial
to in the back end to query exactly the data you need. Because just give me the data, I can I
can then figure out what I need from that. Like the that's is one thing. So like B2B integrations,
it's Rest APIs.
00:57:52:04 - 00:58:22:14
Jens
And then what we see is if a company if a company matures and they are on on rest, they have
all kinds of problems. And we seen so many customers and prospects. You have a microservice
architecture, all microservices. They they expose the rest API and then you have iOS app,
Android app, web app, other apps, and you have point to point integrations.
00:58:22:14 - 00:58:56:17
Jens
So iOS app talks to 20 microservices. That's that's a mess to integrate. And that's it's such a
brittle thing. And then you have versioning and it's it's so complex. It's an app depends on like
20 microservice or something like that. What you can do is build a, BFF architecture. So instead
of one app talking to 20 microservices, it's one app talking to one BFF, talking to 20
microservices, still kind of same, very similar problem.
00:58:56:20 - 00:59:26:09
Jens
And also what we like internally we we kind of named this manual Federation. And you can you
know when when you have an iOS app and it talks to 20, 20 microservices over Rest, then you
also use like you're also using Federation like everybody is federating. The thing is you now
federate in the client. If you have a BFF in the middle, you're federating on the server.
00:59:26:09 - 00:59:52:02
Jens
So on the BFF and it so in the first case one app, 20 microservices, it means that one front end.
It depends on these 20 services. And how do you know that if you're changing one of the
microservices that this app depends on it and that it breaks like, like people have problems with
contract testing and other things and deployments go wrong.
00:59:52:02 - 01:00:30:07
Jens
And everybody, everybody hates it BFF if you move Federation to BFF, that means the app at
the BFF, typically that's owned by one team. This contract is kind of stable, but you still have the
same problem that when backends change, when microservices change, you have to to catch
up with the change in the BFF. So you're still manually federating and you're like a new query,
how we would say in Federation it's not a new query.
01:00:30:07 - 01:01:06:25
Jens
A new query means you have to change an endpoint. It's so much manual work and it's, you
know, in in GraphQL Federation, we can change a subgraph. We run check and it tells us not
breaking clients because we can look at the traffic, we can analyze, breaking changes and
everything. Right. So we're doing all of this. We have a super like, I think one of the big points
about Federation is, you know, exactly what depends on what.
01:01:06:28 - 01:01:34:07
Jens
And you don't have to manually build that BFF. So we save all that. And ultimately what we
enable is collaboration across the teams. And so what this comes down to Federation is not
really solving a technical problem because you can federate in the client, you can federate in
the BFF or you federate using GraphQL Federation. What it solves is an organizational problem.
01:01:34:11 - 01:02:08:00
Jens
And then there's this question coming all the way back to where we started REST versus
GraphQL. It's not about commodity style versus resource style or whatever. It's it's about it's
about solving an organizational problem. And then that's why I'm like, please stop this
discussion with with REST versus GraphQL. Because it's it's about something else. And it's
yeah, it's just, it's boring.
01:02:08:03 - 01:02:13:22
Stefan
Do you think smaller organizations should use GraphQL?
01:02:13:25 - 01:02:42:22
Jens
It depends. So one of the, one of the great benefits of GraphQL is if you're really doing it right,
you can you can co-locate fragments with your user interface components, and you define the
data dependencies, like what's from the graph? Do you need per component. Then you hoist up
towards the root of the app. You hoist up all these fragments, build a single query.
01:02:42:24 - 01:03:10:10
Jens
And now before we load the page, we execute that, query. We pass down the data to the UI
component tree and every fragment that we have created with data masking, it picks up the
data needs and great approach. And there are tools like, relay that do this for a very long time.
There's IsoGraph from Robert.
01:03:10:12 - 01:03:39:01
Jens
And I think also, also Apollo client supports fragments and this kind of workflow. And I also think,
from the from the Guild, the GraphQL code generator, it it also has some very advanced tooling
to, to help, with these kind of, situations. So that's very powerful. The question to ask is, like,
what's the structure of your organization?
01:03:39:01 - 01:04:17:14
Jens
Do you really need this? If you are a super small startup, one single team, five devs, or if you
are in a large organization, five devs, could you just get away with Next.js and tRPC or
something like that? Because why introduce, why introduce the complexity? Like maybe this
whole fragment workflow. It gives you something if you benefit from this, if your UI is very
complex, like things like ISOgraph, like really powerful features, do you benefit from this?
01:04:17:16 - 01:04:26:26
Jens
It's okay. Go, go for it. Like we on our end. That's that's the funny thing. So cosmo has a control
plane. The back end.
01:04:26:29 - 01:04:27:17
Stefan
I was gonna ask you.
01:04:27:17 - 01:05:05:08
Jens
This, by the way. So we have a backend. It's the control plane. It's And we have a front end. It's,
like react Next.js, and we're like, okay, this. And we have a CLI. So we were thinking, okay, cli
frontend, TypeScript, backend Node.js. How will they speak to each other? And we, we thought,
you know what, buff connect slash gRPC.
01:05:05:11 - 01:05:39:17
Jens
We're just creating RPC endpoints with codegen. Like we, we define like the protobuf. We
generate the code. And now you can make jokes about us. We're selling federation. We're not
federating ourselves. We're not eating that portion of the dogfood. But the reality is why should
we because we have one mono repo that contains the backend. The CLI and the frontend
owned by one team.
01:05:39:19 - 01:06:10:15
Jens
No other teams, no microservice architecture, one single backend. What what should we
federate? And so we don't need federation for this architecture. Use the right tool for the right
problem. And the second thing is should we use GraphQL? And we we're not we're not people
who go. We decide for GraphQL. Let's find a problem that we can solve with it.
01:06:10:17 - 01:06:41:00
Jens
We're more like, okay, we need to talk between a node backend, a node CLI, and then a node
react frontend. What do we do? What's easy? What's boring RPC okay, let's solve customer
problems and yeah like don't don't get hang up on, you know, built fancy tech with boring tech
like cosmos, cool cosmos fancy. Yeah. But the way we've built it is boring.
01:06:41:00 - 01:07:07:23
Jens
You know, Postgres, next.js super boring. The absolute worst boring thing you could imagine, is
our auth. What's the auth thing again? keycloak like the boring, boring, ugly Java thing, but it
works. And it has. It has the device flow. So device flow is very important for the for the cli.
01:07:07:23 - 01:07:25:16
Jens
And you can run it locally like so many auth things. You cannot run them locally. We want it to be
able to run it locally with CLI. And then you Postgres take house boring stuff. So yeah, build
build cool tech with boring tech.
01:07:25:18 - 01:07:51:28
Stefan
No, I like it. And then with the in mind though, maybe we'll have to talk about this on the next
episode. But big companies, big tech companies, huge ones, Netflix, Expedia, just big
enterprises in general, especially if they're a little bit more modern, like last 20 years. I will say
they like to build stuff internally themselves. They like to build these things.
01:07:51:28 - 01:08:11:26
Stefan
They like to complicate things. And I think it's because you attract talented developers that want
to solve cool problems. Like, I don't want to throw Pinterest under the bus, but one of our a guy
that I know that works at Pinterest, he's like, I don't care about mood boards, but I care about
the tech and the stuff that we're internally building at Pinterest.
01:08:11:26 - 01:08:27:08
Stefan
But he's like, I don't care about that. And you always say this, don't focus on the tech, focus on
the business. But for developers, for example, like choosing boring tech, they like to work at
companies with complex tech. They like to spin up their own bare metal servers. They like to
solve these technical problems. What do you do at that point?
01:08:27:09 - 01:08:43:17
Stefan
Like do companies? Should they focus on boring tech even though it's boring and providing
value to the company? Or should they focus on building stuff themselves? Because it's cool and
it's interesting, and they have the resources because they're a big company.
01:08:43:19 - 01:09:17:08
Jens
Good question. I mean, I'm I'm the wrong person to ask what a big tech company should do. I, I
lead a very small tech company. Yeah. I, I don't know, like, in the past. So I don't want to rant
about anybody. I can, but I can speak from experience. In the past, I worked for, for a big
German company, the news company, and we had bare metal servers.
01:09:17:11 - 01:09:50:11
Jens
Crazy. And we had a data center. Actually, two and because we had these data centers, we had
people to maintain the data centers. So the logical thing you do is if you have data centers,
racks with big machines, and you have people you install and run your own Kubernetes
clusters. And I think that's that's a fabulous way of wasting all your time and doing stuff that
doesn't bring the business forward.
01:09:50:11 - 01:10:24:14
Jens
So and I think as a developer, it's very dangerous to do things that do not directly affect the
business. Like, you know, we keep hearing about people getting cut like the last 10% here,
20%. They're like, people are getting cut and lose their jobs. Do you lose your job if what you're
building directly affects business, or do you lose your job if you run Kubernetes clusters?
01:10:24:14 - 01:10:33:10
Jens
When we could also just go to the cloud and click on the button and have a Kubernetes cluster. I
know it's not like you.
01:10:33:10 - 01:10:34:16
Stefan
Know that spicy.
01:10:34:22 - 01:10:36:03
Jens
Button, but.
01:10:36:05 - 01:10:44:11
Stefan
That's spicy. That's a good topic for next week. I like that one. So sadly we are at time. But Jens
you're going to say.
01:10:44:13 - 01:10:47:07
Jens
Do you know what is the good thing?
01:10:47:09 - 01:10:49:10
Stefan
What's the good thing?
01:10:49:12 - 01:10:51:16
Jens
We're back next week.
01:10:51:19 - 01:11:00:09
Stefan
And we have a spicy topic how to avoid a layoff. I work on the title but I like it. Thanks you guys.
Thank you guys so much. And we'll see you guys next week.
01:11:00:11 - 01:11:00:21
Jens
Cheers.