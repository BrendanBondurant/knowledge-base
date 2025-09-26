00:00:22:20 - 00:00:33:03
type: podcast-chunk
Stefan
And we're live. Welcome back, ladies and gentlemen, to another episode of The Good Thing.
Today we have a very special guest, which I've been really excited to bring on Sam Lambert
from Planet Scale. Sam, how are you doing today?
00:00:33:06 - 00:00:35:04
Sam
Hey. I'm great, thank you. How are you?
00:00:35:06 - 00:00:44:27
Stefan
Awesome. Doing great. Thank you so much for joining us. We really have a lot of topics we are
going to be discussing today. And for those of the new viewers that are kind of just sinking in,
you guys know Jens. He is my co-host. Yeah, I'm also here.
00:00:44:28 - 00:00:46:06
Jens
Thank you, thank you.
00:00:46:08 - 00:01:03:29
Stefan
Why do we have to intro you? We already know you. But for those of you that don't know Sam,
Sam is the CEO of Planet Scale. And before this, he spent years at GitHub and meta or as
Facebook, where he's been building distributed systems of scales. Some of the things that he's
passionate about is technical insights, strong product vision, strong product leadership and
uptime.
00:01:04:00 - 00:01:08:24
Stefan
You might have seen it on Twitter. He's very passionate about uptime. But Sam, we're so happy
to have you here. How are you doing?
00:01:08:27 - 00:01:13:27
Sam
Thank you. No, I'm really good. Thank you so much for having me on the show.
00:01:14:00 - 00:01:21:29
Stefan
Yeah. We're excited. Did I miss anything in the intro? If you want, feel free to just kind of walk us
through a little bit if I missed anything, but I think I kind of hit some good points there.
00:01:22:01 - 00:01:41:06
Sam
No. Yeah. I think you got I think you got all of it. I can guess I can summarize what plant scale is.
planetscales kind of now the, the database platform we, host MySQL databases at hyperscale
using vitess. Running some of the world's largest consumer products. And now we have, for
vitess as well, which is, well, it's two products, actually, unsharded.
00:01:41:06 - 00:01:46:11
Sam
And sharded vitess products, that we now have out there in the world.
00:01:46:14 - 00:01:50:08
Jens
What's the difference between unsharded and sharded?
00:01:50:11 - 00:02:11:16
Sam
So yeah, actually thats good question. So our current product so the, the product that most
people know and the largest planet scale product is planetscale vitess, which is sharding for
MySQL. That's the product that our largest customers run on. And it doesn't it's always vitess,
right. If you spin up whatever you spin up, you always get a vitess database, whether you're
sharding or not.
00:02:11:19 - 00:02:37:25
Sam
Our new suite of products for the Postgres world was actually split. So they it has an unsharded
product, which is the one that's in private. But, right now it's like a private preview, hosting real
applications for companies. That's. Yeah, like I said, available, but it's pure Postgres hosted on
our operater, with our proxy layer and all the various things that makes planet scale special.
00:02:37:27 - 00:02:59:05
Sam
And then currently now in development and in a phase working with sort of key customer
partners is, our sharded, Postgres product. So the cool thing about that is, you know, because
there's so many people that use Postgres but don't necessarily need sharding, they don't want
to deal with the trade offs that you would get from having a sharding layer in between them and
the database.
00:02:59:05 - 00:03:12:26
Sam
And so we now just provide kind of you directly access or directly through a pooler, to a very
vanilla Postgres, set up. And then the sharding product, we'll put a layer in between that, which
gives you some trade offs, but obviously significantly more scale.
00:03:12:28 - 00:03:24:29
Jens
Yeah. So that means regular Postgres. On planet scale. It's fully hosted by you, but it's like
vanilla Postgres, like, no, no special thing.
00:03:25:01 - 00:03:42:01
Sam
No. I'll proxy the proxy and pooling layer that we have is special and bespoke to us. The
underlying infrastructure that it runs on is also unique. So our operator that allows you to run on
metal nodes, inside AWS and inside GCP, is kind of one of the secret sauce pieces that we
bring to the postgres world.
00:03:42:01 - 00:04:04:01
Sam
And if you look at our launch for the Postgres product, we benchmarked ourself against the sort
of current cohort of, Postgres hosts. And, you know, we can we showed we demonstrated
significantly better performance and throughput. With that, with that product, by giving you
what's kind of good about Postgres, it has some of Postgres downsides. Super.
00:04:04:01 - 00:04:05:21
Sam
That's fine.
00:04:05:23 - 00:04:33:11
Jens
Yeah. For, for for like a very long time when when you were thinking about planet scale, you
were you were immediately thinking, okay, it's it's MySQL. Yeah. MySQL with sharding. But and
then it almost felt like a bit there's like, like a connection of the brand planet scale with MySQL,
almost like you're against Postgres, but it seems like you're absolutely not against Postgres.
00:04:33:11 - 00:04:42:24
Jens
You're, you're, you're, you're kind of rebranding to, okay, planet scale does relational database
at planet scale. Yeah.
00:04:42:27 - 00:05:02:27
Sam
Yeah. Basically. Is that right? Yeah. And definitely not anti Postgres. Very excited by working
with Postgres and the companies that build on Postgres most specifically, I mean, we can dig
into like the core differences that we've already observed between mysql and Postgres, if you, if
you are interested. But yeah, basically we're kind of the database company now, right?
00:05:03:00 - 00:05:20:08
Sam
In fact, shipping Postgres meant that so many more people reached out asking for us to do
other database services. We won't be doing that for a while, maybe one day. But right now we,
we've got a long road ahead in the Postgres world. So we're building building that and enjoying
ourselves so far.
00:05:20:11 - 00:05:49:20
Jens
No, absolutely. Sorry. There were there were so many like, players before who did Postgres with
sharding. Some were acquired, others were not super successful. Why? Why are you doing
this? Like what? Why is it now the right time to do the same thing that others were okay ish
successfully like, why now?
00:05:49:23 - 00:06:12:09
Sam
So many reasons. Yeah. So you're really good. Why now? Question. So there's the like the
broader pieces that like kind of the Postgres community, and market is getting ready for
sharding. There's now companies that are running Postgres at some significant scale. It's
actually very interesting. I see people even yesterday I was reading someone talking about an
at scale Postgres workloads.
00:06:12:11 - 00:06:31:27
Sam
I know how large that workload is. I've seen it under NDA and it's not very big, in compared to
the size of the MySQL workloads that we see. But they're starting to grow. We've seen a few
large ish, but nothing that's anywhere near the size of the MySQL workloads that we've seen.
But it's happening and, and all and every company builds on Postgres.
00:06:31:27 - 00:06:57:11
Sam
Right. So it's coming. Postgres is probably going to go through the same era of the tens that that
MySQL went through from like 2010 to, 2020 in terms of very large and successful companies
building on Postgres, and it needing to mature and scale to make that happen. But it's like very
exciting. And so that's one why now question.
00:06:57:13 - 00:07:45:04
Sam
So the other is, we're doing it very simply, that we've done we have built the only generally
available large scale sharding solution that's out there, like there were attempts in the Postgres
world before, architecturally, they were misguided. And weren't built to support any large, really
large workloads. And so what we're doing is building from the first principles that we've learned
through sharding, databases, at very extreme scale, applying that to the world of Postgres,
building it into the ecosystem that Postgres has, which has some like bits that make that easier
bits that make that harder.
00:07:45:07 - 00:08:06:00
Sam
And it's just about the, the way we'll deliver it. And the other side of the coin being the hosting of
that. Right. So you can build an open source sharding solution. And people are and people have
it's very different than building a solution to run large scale workloads, then open sourcing it.
Right. And that's what we're doing.
00:08:06:00 - 00:08:28:25
Sam
We are working with design partners, to build sharded Postgres for the scale theyre at and then
once it's and then we get that loop of us directly seeing it and hosting it for them, and then we
will open source the byproduct of that meaning it will be very robust and resilient. We don't I'm
following along kind of a couple of open source sharding solutions right now.
00:08:28:27 - 00:08:40:19
Sam
And they're kind of achieving, the kind of spec of what you need to do. But that's very different
from battle hardening, at scale, which is what we are working on right now.
00:08:40:22 - 00:08:41:12
Stefan
No, also.
00:08:41:12 - 00:08:46:20
Jens
Not the database expert. Stefan, can I contribute?
00:08:46:21 - 00:08:47:11
Sam
Sorry.
00:08:47:13 - 00:08:52:10
Stefan
You're you're hijacking. We got to follow the agenda. The thing is, what agenda?
00:08:52:10 - 00:08:53:26
Jens
We're just talking. Who?
00:08:53:26 - 00:09:08:10
Stefan
Who is saying we got to get the background first? Oh, I'm boring to the Sam. How did we get
into databases like that? Just for the audience. So they know, like, how did you get into
databases? And then we're going to get into the nitty gritty details of tech, like how did you end
up at planet Scale? How did you start it?
00:09:08:10 - 00:09:09:13
Stefan
Just like that part.
00:09:09:16 - 00:09:31:18
Sam
So I I got into databases the same way I think most people do, which is it's the worst problem at
most tech companies they work at, and they kind of gravitate to those issues and start fixing
them. I was doing that of, like various different companies. And then I went up, went to a small
but growing company called GitHub to be their first sort of database engineering hire.
00:09:31:21 - 00:09:56:01
Sam
Worked there, eventually became VP of engineering, running like the platform infrastructure
teams there, which, you know, basically everything below the web app. And, you know, took that
to being like the 40th largest website on the planet, then worked at meta on the traffic
engineering team, which is a significant portion of the internet's traffic, and obviously running at
extreme stream scale.
00:09:56:03 - 00:10:15:21
Sam
And then I came to planet scale, you know, planetscale was founded out the back of the Vitess
project, leaving Google. It was it was really more of a consultancy and not really a business
with, with a web product, with like a hosted product. So I came to like, kind of join and build that
hosted product and then took over running the company.
00:10:15:23 - 00:10:36:03
Sam
A little while after joining. Yeah, we became very successful. I mean, the we went from having
just a tiny, user base to now just a very, very large user base in some of, the largest relational
databases in the world running on the platform, as well as a ton of very large scale kind of
consumer platforms that run on top of us.
00:10:36:03 - 00:10:50:07
Sam
It was really fun to know that, you know, pretty much every working adult in America or, you
know, in the tech industry will interact with products built on top of that scale every single day,
which is really cool, No well said.
00:10:50:12 - 00:10:56:24
Stefan
Jens over to you now on the tech questions. Now we got, we got the background out.
00:10:56:26 - 00:11:25:17
Jens
Okay. Well, one thing I'm interested in and, I'm not a database expert, but a user, but I, I read
about planet scale metal. Yeah. And it's it's very interesting. The graphs you're showing, the
performance and everything, like, in very simple terms, why is planet scale metal so much more
performant than other database solutions?
00:11:25:19 - 00:11:47:29
Sam
So the reason it's more performant is a very simple one. And it's the same thing anyone could
achieve on a local server, you know, a server that they rack themselves is that it just uses, the
NVMe drives that are inside the server, which sounds like when you say it like that, it sounds
silly and, unimpressive. Like obviously you should use the disk inside your server, but in the
cloud that doesn't happen.
00:11:48:01 - 00:12:10:09
Sam
The main reason is really impressive that we do it. The way we do it is because we, we, we're
running those bare metal inside AWS and inside Google by using the machines that they use to
build their services on top of. And and these machines are ephemeral, so the the disks don't
stick around. If you're racking your own servers in a data center, you have rate arrays inside
those servers, and you can go and access them if you really needed to to get access to the
data.
00:12:10:09 - 00:12:32:27
Sam
We can if we provision a server, it's gone forever. If it fails, it's gone forever. So we handle all of
this state, running on ephemeral machines that happen to be extremely fast and much cheaper
than the other hosts that you get inside Amazon. And it means that we get this huge
performance increase, like, you know, Aurora and some of the other databases, they they just
aggregate storage and compute.
00:12:32:27 - 00:12:49:13
Sam
They separate those things, which means they put a network layer, in some form between the
the server process and the disks, which adds a significant amount of latency, to each query. We
don't do that and it makes it a lot faster.
00:12:49:15 - 00:13:12:17
Jens
So if I have, planet scale metal database, it it runs on a computer. The computer has a local
drive that makes it super fast. But what if the computer or the drive fails like my database? Is it
then down, or do you have some sort of like H.A. or. Yeah.
00:13:12:19 - 00:13:32:10
Sam
There is no non ha configuration for this. It's all highly available. By default. You get given three
nodes when you spin up. So you have two replicas in the in the instance that you would if you
say lost a primary node, we very, very quickly detect that failure. We throw that node out we
promote the node that's furthest ahead.
00:13:32:10 - 00:13:58:18
Sam
We have say semi synchronous replication, which means that by the time you write, we know
that the write has left to another machine. We then promote whichever of those machines put
the replicas underneath and then add a replacement node for that, for that primary. And that's all
done very, very quickly. In the time of failure, a proxy will buffer and hold off the queries and wait
for that to happen, and then send them through to the database when it's done.
00:13:58:18 - 00:14:08:25
Sam
So we basically, we handle all of that for you to give you high availability without the kind of
trade offs of disaggregating storage and compute.
00:14:08:28 - 00:14:43:25
Jens
Okay. And then do you, do you have to deal with, with problems like you make a write on like a
master chair and then you, you get you get it back, it's working fine. And then you make a read
request and it wasn't replicated or something or like, you know, there's like different guarantees
you can get from a database or like, is that like, does it behave like a singular Postgres or
MySQL or other differences and guarantees?
00:14:43:25 - 00:14:45:14
Jens
I can go from such a setup.
00:14:45:17 - 00:15:16:19
Sam
Nope. It it does. It works like the storage engine below. It's supposed to work with replication.
That's a core principles. We don't fake out the storage system like, you know, there's other
scaling solutions for these products that basically re-implement a different storage solution
under the hood to allow stronger consistency with significant trade offs there. But, yeah, you if
you read, write to a master and you require the the row on the replica for the same request, if
there's replication delay, it may not be there.
00:15:16:22 - 00:15:33:21
Sam
That's fine. And kind of normal. And that's an edge case to, to deal with any of these types of
systems. It's more like to, to do that kind of guarantee, you then pay a different penalty, which is
a penalty that we don't pay because it doesn't really scale. That's not really what our users are
looking for.
00:15:33:24 - 00:16:12:21
Jens
Okay. So you're at that scale. Your users, they have like database usage patterns, like for
example, like massive writes or something where you you don't immediately read it. Like for
example, I, I saw another, another podcast you did where you were talking about how how
planet scale benefits from, from the AI boom. And so I, I could assume, for example, that you
have, or you could have a customer where, where people have conversations with an AI, and
then you would write the conversation to the database, and that would be like quite write.
00:16:12:21 - 00:16:15:18
Jens
Heavy, but not so many reads in that scenario.
00:16:15:20 - 00:16:33:25
Sam
We do have that. Yes. And we have we do. We're very good at write works, write bound
workloads. We have a lot of very high scale, write bound workloads, whether or not they're AI or
not. They they store a lot of data. You find that in the consumer space, right? Like most
consumer apps. You know, the only thing that makes them specific to you is the data behind it,
right?
00:16:33:25 - 00:17:13:08
Sam
So they log a lot of things, a lot of transactions, transaction volumes, log lists, or just, you know,
data that they're ingesting from other platforms to do training on. That's all stuff that we're very,
very good at. And, you know, having the consistency model we have allows you for a much
higher writes. We also allow you when you shard to have multiple writer nodes, which means
you can actually scale up writes like one way that people give you that kind of consistency is
they do things like serialized isolation or have, single writer threads that mean you kind of
enqueue everything behind, those that kind of, isolation patterns, meaning it's slower,
00:17:13:08 - 00:17:27:15
Sam
but you get that consistency. We don't have that, consistency we have. We go for the
performance. That's different to durability. Your data is always there. We've never lost a
customer's data that, it's just that kind of trade off in terms of the multi-node consistency issue
there.
00:17:27:16 - 00:17:47:04
Stefan
So, when you kind of explain it like this, it's it sounds pretty easy, like you're like the way you
explain in the beginning, like, anybody could have done this, but why is nobody else doing this
the way you explained it? Like it seems like from first principles, like, why did no one else think
of this? But when you guys came along, you guys did like, why is no one else replicating it or
trying to copy it?
00:17:47:06 - 00:18:12:17
Sam
I think they definitely are. Whether or not they're doing it as well. We didn't invent anything like
we we, I said on Twitter a while back that I don't think theres very much IP in the database
world, like we're all looking at papers that are from the 60s. The rules of computers have really
not changed either. Or physics, like the constraints that we're dealing with in most computer
science problems of physics, latency, the speed of light.
00:18:12:19 - 00:18:36:27
Sam
You know, all of these failure rates, all of these various factors, we just provide we apply a very
pragmatic approach to how we deal with these things. And through experience, we've seen the
ways that fail. A lot of databases have a kind of high hopes of reinventing the wheel when it
comes to these kind of architectures, and it just never really works.
00:18:36:28 - 00:19:02:26
Sam
The history of most large scale database applications end up in the same way, looking the same
way in similar ways. And we've provided that in a very generalized manner, which is itself which
is a really hard task. I mean, operations and good operations, it's not about being kind of fancy
and crazy, like you're just not going to you're not going to kind of crack the nut on, like, okay, I
don't have airplane advances in airplanes.
00:19:02:26 - 00:19:22:22
Sam
Right? Like the physics of how a wing creates lift is like, it's written, it's done. But now the the
operations of making sure there's no single points of failure in that process, and it can continue
and it can do the process over and over again is the bit that's difficult and takes a lot of
knowledge and sedimentary knowledge and layers built up.
00:19:22:22 - 00:19:27:02
Sam
And that's what we have. That makes us pretty different.
00:19:27:04 - 00:19:52:18
Jens
Also one, one, one thing I'm interested in is so planet scale it, at least from the outside, it looks
like you're you're largely basing on top of vitess, which is an open source project. Yep. Like you
said, coming from from Google, Google or my understanding is it was something it was used for,
for YouTube. Right? Yes.
00:19:52:21 - 00:20:00:26
Jens
And so being an open source project and you are a company hosting that open like obviously
you're doing more than just hosting a project you were the.
00:20:00:26 - 00:20:02:16
Sam
We are the Maintainers as well. Yeah.
00:20:02:19 - 00:20:30:03
Jens
Okay. But one of the biggest fears of like startups with open source projects is like, yeah,
Amazon could just take vitess and and hosted like they they can probably do it cheaper. They
have data centers etc., etc.. Like you probably saw like all this back and forth between like, like,
like OpenSearch and Elasticsearch and other database companies.
00:20:30:03 - 00:20:35:03
Jens
Like how, how are you thinking about this, this topic.
00:20:35:05 - 00:20:56:12
Sam
I think that, you know, there's a this is a world where that's true, that can happen. vitess is like
half, half of our offering, right? A lot of the the stuff that makes planet scale really special is not
open source. And vitess is like it's a code base for the engine of our product. And it's incredibly,
incredibly important to us.
00:20:56:14 - 00:21:18:07
Sam
And yes, it would be a big step up, like it would be a big benefit to certain companies to go and
just take that and use it. And there's people that self host vitess at very, very large scale, and it
works for them. It's more like, can they replicate how well we operate databases and they
haven't.
00:21:18:12 - 00:21:40:24
Sam
I mean, we've got multiple public case studies out there of people moving from Aurora or
wherever, and becoming much, much more reliable, on top of our platform, we specialize in
databases, engineers some of our engineers have worked on. But there's no secret, like, they
have a lot of money. They can put a lot of people on these problems.
00:21:40:24 - 00:22:02:25
Sam
But at the end of the day, right, there's expertise. At companies like ours, that far exceeds what
they have, current, current Amazon specifically. And you look at the current tools, they've,
they've, they've built like limitless. We've moved their largest customer over to, to, to us because
it wasn't reliable. I, you know, literally this morning spoke to another limitless customer.
00:22:02:25 - 00:22:21:27
Sam
That's not a very large scale. That's also having problems on these platforms. So them just I'm
sure they've had they've had access to the vitess code base for years. It hasn't really improved
anything they do. They could just take the technology and host it. It's only half the problem for
them. I don't think their problem is writing the code that could look like vitess to go and do the
stuff.
00:22:21:27 - 00:22:35:13
Sam
It's a load of other tail factors that impact whether or not they can hurt your business. But there's
just plus there's also just much more coarse grained, brutal ways Amazon can can hurt you than
just take the code of what you're doing.
00:22:35:15 - 00:22:38:01
Jens
Yeah. What's your current headcount?
00:22:38:03 - 00:22:39:17
Sam
55.
00:22:39:19 - 00:22:58:13
Jens
55. And how does this distribute across like database operators or let's say like infra people or
what do you call it like like platform engineering versus like engineers working on the on the
vitess product or like proprietary products.
00:22:58:15 - 00:23:08:12
Stefan
And Sam real quick 55 with 100% uptime, reliability. That is insane. I mean, that is an insane
stat. Oh yeah. We're deep into this.
00:23:08:14 - 00:23:30:20
Sam
We're very proud of being a small company. We're doing some hiring. We're not going crazy. But
yeah, like this startup, like two other very popular Postgres startups like host hosts have their
engineering teams are three times the size of ours. And we're very proud of having a very small
company and team. These are exceptional people that we have working for us.
00:23:30:20 - 00:23:48:04
Sam
And we know like it's it's a known thing about our culture that we behave that way. Pretty much
every engineer at Planet Scale could be a principal engineer at any other company. We don't
really have any engineering titles that way, or it's just everyone's just an exceptionally good
engineer that's had a long career at scale. And that's how we achieve this.
00:23:48:07 - 00:24:16:02
Sam
And if you build good infrastructure, you shouldn't need to throw tons of headcount. Or
infrastructure team itself is very small. It's like four people. The vitess team is around ten. The
rest break up between what we would call orchestration, which is a large amount of what we do,
which is kind of orchestrating. Database failurover is happening like there's no there's nothing in
terms of how we handle our operations that require human to be around.
00:24:16:02 - 00:24:23:06
Sam
Otherwise we wouldn't have the high uptime that we have.
00:24:23:09 - 00:24:39:16
Sam
And then we have a small team of people that build the what they call the surfaces team, and
they build the surfaces that you interact with. They bring the build the the app, web app, the CLI,
and all the other tooling that you interact with to go and use the platform there is like five of
them. So it's mainly all in orchestration.
00:24:39:16 - 00:24:53:25
Sam
There's no sysadmin style people, right? Like that. It's all writing automation that manages the
fleet, continually. Otherwise it would it would not scale. Basically.
00:24:53:28 - 00:24:57:12
Jens
Well, what's your what's your headcount in marketing and sales?
00:24:57:15 - 00:24:58:09
Stefan
Yeah, I was going to ask.
00:24:58:09 - 00:25:38:24
Sam
The marketing is two people, two exceptional people, Ben and Holly. And then we our, our
approach to marketing is very different to most companies. Our sales team is a one sales rep
and two sales engineers, and they basically are both engineers that work with, customers
migrating over, and helping them plan through how to go and do that and, and work through any
kinks that they're seeing on the you know, if you're a very large customer, like very, very, very
large database installed, you spend a lot of time working through making sure you've mitigated
all risks and things work well.
00:25:38:26 - 00:25:48:05
Sam
And we want to do that with them too. And so yeah, they work with that and that's it. It's mostly I
mean it's really how a tech company should be, right. Lots of engineers.
00:25:48:08 - 00:26:00:11
Jens
it out.
So it's all like inbound and people come to you, they say, hey Sam, do you have a database for
me? I have some petabytes of data. And you say, yes, we have something, and then you figure
00:26:00:17 - 00:26:22:27
Sam
We figure it out. Yeah. We don't. The reason we do marketing the way we do is because I don't
think there's much like you go to some, some other companies website and doing infrastructure
and they have all these flashy animations and hypey stuff and I mean, what's it for? Anyone,
any buyer with any money or sophistication is going to want the technical criteria to be put
forward.
00:26:22:27 - 00:26:40:28
Sam
And that's what we do. Like, the way we market ourselves is we do very technical content,
blogging content and whatnot, blog posts are well known for this now, that go really deep into
the kind of things that we find interesting or that our customers might find interesting about
databases or general computer science problems. And that's all we do, really.
00:26:40:28 - 00:26:44:04
Sam
There's no no magic to it.
00:26:44:06 - 00:26:53:01
Stefan
But, Sam, are you involved though? Like, would you say founder led sales? So you have a big
customer that's coming in and you're selling an Enterprise contract. How involved are you in that
process with the sales team?
00:26:53:03 - 00:27:16:00
Sam
If it's a large customer, always very often I'll be the first person people speak to because like,
why not? Like there's only much what else would you do? Like I work with engineering to help to
like, shape how the product should be. From what I'm hearing from customers and speaking to
customers and working creatively with the marketing team, you hear the best things from
customers directly and you learn.
00:27:16:07 - 00:27:39:02
Sam
And I think it's just a good way to do it. Like, I don't hop on a call with every customer. That's
obviously not possible, but it's really powerful to go and work with our large customers and bring
be very sort of human. And I think even even if we were in the billions of revenue or whatever, I
mean, you still want to be working on the largest potential deal you can bring in for your
company.
00:27:39:02 - 00:27:41:12
Sam
So I would always be doing that now.
00:27:41:12 - 00:27:55:06
Stefan
Yeah. Well, sir. And then one of the things we've experienced and I wonder if you've
experienced this is like you've got a typical guy at a very big enterprise and he says, well, you're
only 55 people. What's if you go out of business or something like that. We've also dealt with
that. Have you ever dealt with that while you guys are dealing?
00:27:55:06 - 00:28:06:22
Stefan
These big things are like, well, this company has 300 people in like for me, headcount does not
equal success. I actually think of it as counterintuitive if you have more people, but have you
ever had to deal with that in your sales process all the time?
00:28:06:25 - 00:28:27:00
Sam
And, it's much less of a problem now. But in the early days, oh, for sure, you had to sit. I mean,
you'd sit opposite the CTO of, like, a public company. And I remember one very specifically said,
if you go bust, we go bust. And I was like, and I just there's only one thing you can do in the
moment, which is tell the truth and go, that is true.
00:28:27:00 - 00:28:32:06
Sam
Yes. I think that might be true. What kind of. I can't hide that from, from you. Right.
00:28:32:06 - 00:28:33:03
Jens
Like, did you get the deal?
00:28:33:09 - 00:28:54:04
Sam
Yes. We did. Yeah. you have to be very honest about these things, and, it's less of a problem
now that we have so many large companies running on us, and we're a profitable business,
meaning we don't, you know, for those that don't run a company on this who are listening to this,
if you're if anyone you depend on or yourself are not profitable, right.
00:28:54:05 - 00:29:10:01
Sam
Like, you know, there's a date where your company could go bust, right? Like that's just a thing
that happens. You know, there's just there's such thing as a cash out date that you think about.
We don't really have that right. We have. In fact, last quarter we had a surplus, that was even
more money that we had planned that we were going to have that quarter.
00:29:10:01 - 00:29:28:13
Sam
So we just put that back into hiring and things like this. But when you can show that to
companies and show that you have a sustainable business model, they know you're going to be
around. And luckily, people a lot of people don't really equate headcount with like, I yeah, I'll give
you an example. Amazon's got thousands of engineers on the competing product to us.
00:29:28:13 - 00:29:53:22
Sam
And it's and it's outperforming our products is outperforming theirs. What's headcount doing I
mean it's worse right. And so you get over it over time. But yes it is I'm not going to say it's not
like it is a factor. But you then go it kind of becomes this rolling Stone where I'll say to, that
person, okay, well, why don't you chat to one of the other large companies that runs on us and
they can share that experience.
00:29:53:22 - 00:29:58:02
Sam
And then it's a good thing, it you know, it just yeah, it goes, well, you know.
00:29:58:02 - 00:29:59:15
Stefan
Yeah I do the same. Yeah.
00:29:59:17 - 00:30:16:14
Sam
Yeah. One of our recent new companies is one of the fastest growing companies of all time, and
they're tiny too. And so they don't just bother them, they just want. I think we're getting to that
world right? Actually, where we're seeing more, much more small companies defeating very,
very large ones. And I think people like that and I and it just shows.
00:30:16:16 - 00:30:21:19
Sam
Yes. Clearly impressive. Right. If the small team of people can do what we do, it's clearly
impressive.
00:30:21:21 - 00:30:28:19
Jens
No, you said you you had a surplus, but you're a VC backed company.
00:30:28:22 - 00:30:30:14
Sam
Yes.
00:30:30:17 - 00:30:54:02
Jens
But what what are the. Because I looked a little bit in the, in the past and that was, there was a
moment in the, in the history of planet scale where I think you changed a bit the course you had,
like, marketing people and other things, and you, you kind of changed a bit. And, and for a
moment, I was, I was worried like about the, the future of, of planet scale.
00:30:54:03 - 00:31:33:09
Jens
It was like, Is everything going right? Like it was a weird moment. And so I'm, I'm just wondering,
like your investors, they will also have expectations and, and, first of all, I'm curious about, like,
the there must have been, like, a big shift and, like, as a founder, I'm, I'm always interested to to
learn like how how did that moment build up and and what happened there if you can talk about
it and besides also like now with the, with the surplus, like wouldn't VCs normally say like, hey,
can can you burn more money and raise more and then grow whatever, whatever.
00:31:33:09 - 00:31:36:12
Jens
Like, yeah, okay. Multiple topics.
