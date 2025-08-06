00:26:44:19 - 00:26:46:23
Dustin
And,
00:26:46:25 - 00:27:07:05
Stefan
Yeah, it's getting better, but no, it's a good point. And then I kind of want to transition into kind of
what we've been talking about this week. So I just released a, broadcast to all of our customers.
And so we made some really cool changes. And Dustin worked on something pretty cool, which
is a blog post coming out soon.
00:27:07:07 - 00:27:18:26
Stefan
But talk to me a little bit about the telemetry pipeline and maybe for some of the viewers, kind of
explain, like what that was, why you built it, and what it's going to do to cosmos as a platform.
00:27:18:28 - 00:27:55:14
Dustin
Yeah. It's a yeah. I think it's a very technical, very interesting, interesting technical issue. It's not
so, amazing, but it's it's it's. Yeah, I would say it's still pretty interesting. So you need to imagine
that when, a customer runs a router and, a graphql requests, hits the router, we analyze what
types and fields has been used, and this, this usage data is then, pushed to our cloud
infrastructure and need to be ingested into our clickhouse cluster.
00:27:55:16 - 00:28:26:14
Dustin
So now you can assume that when, a customer with a lot of traffic, we also produce a lot of,
schema usage data. So first step is to batch the data inside the router. So assuming, someone,
someone sent the graphql. Always the same operation until it hits 500,000 times. The router. So
we don't have to send, we don't have to send 500,000 operations, schema usage operation to to
to cosmo.
00:28:26:16 - 00:28:57:15
Dustin
We will batch it and we will, then send a counter of 500,000 to our cloud. So that was the first
optimization step. So in other words, we we batch at the router level and then periodically push
the schema usage data to our cloud. And what I mean with cloud is like we maintain, a fleet of
metrics, collect collectors, which are responsible of ingesting this data directly to clickhouse.
00:28:57:18 - 00:29:29:17
Dustin
And, if you're familiar with, data pipelines, you know, that the more traffic we will produce on the
router side, the more traffic it will push. It will generate and push to our collector fleet and if the
collector fleet will directly ingest the data to a click cluster, the the we will have at some point,
we will hit a wall because, clickhouse cannot.
00:29:29:20 - 00:29:51:00
Dustin
Yeah. Click house, will not be able to keep up with the load. And we would need to, need to,
scale clickhouse and that is, expensive. So what can we do? When you have to, you have to
instead of pushing the data, we have to pull the data from, from and from a queue.
00:29:51:01 - 00:30:13:18
Dustin
For example, for example, Kafka. So what we what we did was to implement, like, we could say
a buffer or the buffer structure between the collectors and clickhouse. So clickhouse is able to
pull the data at his own pace. And then that way we don't have to over scale the clickhouse
cluster just to to to keep up.
00:30:13:20 - 00:30:25:11
Dustin
With a load we can, we can yeah. Have, implement like a back pressure mechanism between
the collectors and clickhouse.
00:30:25:14 - 00:30:44:07
Stefan
Yeah. That's super cool. So, like, if I understand it from, like, so, we always joke around, so, like,
I'm non-technical. I have, like, very limited experience as a software engineer, but I did
implement some cool stuff, but I didn't work with clickhouse. I didn't work with redis, I didn't I
have nowhere near the experience with you, but if I'm understanding this correctly, so cosmos
growing.
00:30:44:12 - 00:31:04:19
Stefan
We have some customers that do billions of requests per day, and what that would do is once it
goes through the router and it heads over to click house, it would kind of overload clickhouse
and it would kind of, have to scale up super fast. It also isn't super performant. And it would not
only just drive the cost up like crazy, it also wouldn't be performant for the customer.
00:31:04:19 - 00:31:27:04
Stefan
And so what you've implemented with this telemetry pipeline is a system that basically kind of
we still take in the same amount of requests, like you said, like 500,000 requests, but we kind of
spread it out and kind of put it in a queue, and then it's processed into clickhouse on a schedule.
And what that does is it allows clicks to scale up slowly and it doesn't actually overload
clickhouse.
00:31:27:04 - 00:31:27:24
Stefan
Right.
00:31:27:27 - 00:32:02:16
Dustin
Exactly. And also interesting is because we're using clickhouse cloud, they're they have an
offering called Click Pipes that allows you to connect, click your clickhouse cluster with any third
party, database, which includes Kafka, which includes, BigQuery. And they're, they maintain, the
worker fleet that pulls the data from your data source, for example, Kafka and imports the data
into the right, clickhouse tables.
00:32:02:19 - 00:32:26:12
Dustin
So that way we don't have to maintain the worker fleet. We don't have to be an expert in that
area. And the only the only responsibility we have is to push the data into the Kafka cluster,
taking care of it, that, retention policies are properly configured, that the kafka clusters are
healthy and, yeah.
00:32:26:15 - 00:32:45:14
Stefan
No, it's super interesting. And people are always saying this in discord. They're asking, hey, like,
I want to spin up, Cosmo. I want to self-host it, but I don't have any clickhouse experience. Do I
need to click House? And we always tell them, yes. It's like the central source of truth. You need
to clickhouse and like.
00:32:45:17 - 00:32:51:15
Stefan
Any thoughts on that dustin? It's it's a funny question we get all the time.
00:32:51:18 - 00:33:17:00
Dustin
I would say it's still a good question. There might be users out there that that don't need that
scalability that clickhouse can provide. And there would might be sufficient with Postgres, but
that wouldn't that would require a lot of. Yeah, implementation on all sides to also support
different databases and yeah, on our current router
00:33:17:00 - 00:33:42:25
Dustin
That's not, that's not worth it. But yeah, overall you need some database. That that is, is suitable
for analytics, workloads to process. The opentelemetry data that is emitted by the router and
also the schema usage data. If you don't want analytics and only you want to use a schema
registry, that's.
00:33:42:27 - 00:33:46:14
Dustin
Yeah. I'm not sure. Who's doing that?
00:33:46:16 - 00:34:07:10
Stefan
Technically, it's possible. It doesn't make sense for us because we are ingesting large scale
data. So for us, that's the reason why we built that. We built it with scale in mind. I mean, it
makes sense. I mean, yeah, like, maybe someday in the future, there's like a Cosmo light where
it's like a smaller version of Cosmo with just a schema registry in the router and like a Postgres
database.
00:34:07:10 - 00:34:27:09
Stefan
But for now, there isn't. And so to answer the question, like, yeah, if you're going to self-hosted
Cosmo, you will need to use clickhouse. But I like what Dustin said. Like when you're building a
platform that uses other people's technologies or other technologies, frameworks, concepts, it's
better not to be an expert in them. Like we're not authentication experts.
00:34:27:09 - 00:34:40:16
Stefan
We use key cloak and then we use cloud IAM, which is a managed service of Google because
you know, you don't want to be an expert. We don't want to roll our own auth. What we want to
do is provide the most value we can for our customers. And the same thing with clickhouse we
use manage clickhouse, right?
00:34:40:16 - 00:34:50:27
Stefan
We don't tell folks like us exactly. Everything is just kind of manage, right? We use GCP, their
Kubernetes offering. Do we self host anything?
00:34:51:00 - 00:35:24:03
Dustin
Except from our company, our own components we have developed no know at least we, we
you know, we try our best not to doing it. It's also, for example, valid for, our Kubernetes cluster,
we use GCP, autopilot. So we don't have to worry about autoscaling. We use GCP as a
complete observability platform for, to ensure uptime, to, to implement proper, alerting and,
yeah, analytics.
00:35:24:05 - 00:35:34:22
Stefan
Yeah. And why did we decide or why did you decide to go with GCP over AWS? When we first
started out with Cosmo?
00:35:34:24 - 00:36:13:12
Dustin
That's a good question. I, I had, experience with GCP already. I knew, about the autopilot,
offering and, I did a quick POC and GCP and the whole the whole user experience was much
better than on AWS. And, yeah, yeah, I think your point. Yeah, you could have built the same on,
on on, AWS or on Azure, but, none of these providers as far I as far I remember, do not offer, a
similar service to, to autopilot.
00:36:13:15 - 00:36:36:21
Dustin
You can, you can, you can implement it. For example, AWS has karpenter, which is like a,
Kubernetes controller that does auto scaling for you. But yeah, again, I don't want to
experiment. I just want to buy something and solve the problem. So throw throw money, throw
money at it and.
00:36:36:24 - 00:37:00:14
Stefan
Yeah, I mean, that's what you're supposed to do with VC funding. I mean, no jokes aside, I think
this is what like. This is what I struggle with a lot. So I have a lot of good technical folks like
friends. And this is the first mistake we made. Wunder graph is we built a super technically
super cool product, like with firecracker, the CI CD pipeline that we set up the GitHub actions.
00:37:00:14 - 00:37:19:25
Stefan
We use so much cool tech. It was bleeding edge. It was amazing. But it didn't solve a problem.
It didn't solve the problem pain enough. And then when we pivoted into Cosmo, we started
realizing that the tech is secondary. You want to choose boring, reliable tech that gets the job
done, but you want to focus on solving the problem for the customer, right?
00:37:19:29 - 00:37:38:28
Stefan
Exactly. Yeah. Dustin, you did a quick POC, you tried AWS, you tried GCP. You saw that the
developer experience allowed you to ship faster. It had the autoscaling feature. You thought of
our customer and boom, that's why we implement it. There's no weird like oh like this. It's it's a
better technology. It's now I got the job done and we need to focus on our customers.
00:37:38:28 - 00:37:43:21
Stefan
I like that, so yeah. Don't don't like freaking out.
00:37:43:24 - 00:37:52:03
Dustin
Don't forget, big, big motivation was, Google GCP startup credits.
00:37:52:06 - 00:38:12:19
Stefan
Yeah, I actually forgot about that. So, like, if you're a startup, clouds will give you crazy
discounts. They'll give you like 100,000 in like, credits and, let me actually give you guys a very
good tip, okay? If you're building on any cloud platform, get the credits as soon as the credits
are over, tell them that another competitor is giving you double the credits.
00:38:12:25 - 00:38:32:24
Stefan
If you migrate over and tell them you're going to migrate over, you don't have to actually migrate
over, but they'll come back and they'll give you 50,000 credits or 60,000 credits as long as
you're small enough. Always use the other cloud provider as leverage to get more credits. I it's
somebody told me this, the guy from railway actually he said to use this.
00:38:32:24 - 00:38:50:06
Stefan
And so now every time you know like they come up to us and they're like, hey, like, you guys are
running low on credits or like, yeah, we're looking at jumping to AWS. They're like, wait, no, no,
no, here's 40,000 credits. Please stay. We're like, okay, we'll take it. I think that's kind of like a
funny little hack.
00:38:50:06 - 00:39:09:27
Stefan
It also is like startup mentality. Like, always make sure that you're getting the cheapest, you
know, tools, but that get the job done. And Dustin my next question I want to ask you is, we've
built a lot of cool features into Wunder Graph Cosmo, what was a feature that you were really
proud about or like, really enjoyed building, but also made a big impact with our customers.
00:39:09:27 - 00:39:13:29
Stefan
Like our your favorite feature to Cosmo?
00:39:14:02 - 00:39:18:12
Dustin
My favorite feature?
00:39:18:15 - 00:39:29:09
Stefan
I know there's so many. There's advanced request tracing. There's, I mean, just basically the
analytics view, there's the router, there's studio.
00:39:29:12 - 00:39:54:11
Dustin
I think the most I would say the, the complete, open telemetry integration. So from the router
into Cosmo, setting up the auto collectors, properly setting up click house, steam. I think that
was very interesting. And, it's. Yeah. And it's still not, not done yet. It's, yeah, it's still there's still
a lot of things to do.
00:39:54:13 - 00:39:54:28
Dustin
Okay.
00:39:55:00 - 00:40:18:16
Stefan
And walk me through that. So like, I understand to an extent of like open telemetry, but basically,
a year ago, I mean, our major competitor, they didn't allow you to kind of like, send Otel data to
your own, like Datadog or wherever you wanted to monitor it without an enterprise plan. And we
built that fully into the solution.
00:40:18:16 - 00:40:30:01
Stefan
And so what does that mean? Like otel telemetry that you can export it to Prometheus, to
Datadog, like, kind of explain it to me. And for maybe some of the non-technical folks.
00:40:30:03 - 00:41:10:19
Dustin
Yeah. Opentelemetry is a standard how to collect metrics. Trace suspends events. And they
also now support logs. It is just like a convenient, unified approach to, to instrument your
application. Yeah. For for observability needs and yeah. So before you usually use, custom
integration like Datadog, New Relic, which auto instrumented application through some some
non standardized API you were able to create custom metrics.
00:41:10:22 - 00:41:29:08
Dustin
And now you can just, use an ultra compatible SDK and push the data to a, compatible, auto
collector. And from that point on, you can distribute, or share the data, across multiple platforms.
00:41:29:11 - 00:41:51:28
Stefan
Yeah. And also the interesting is so it's observability, like if you talk to any big company, the first
thing that they'll tell you is, are AWS bills crazy And then they'll say, our data dog bill is crazy.
And so the reason why it's so expensive is like when you're such a big company is observability
is key. Like imagine like having like what would you not do if you didn't have any analytics or
data of like, your platform?
00:41:52:00 - 00:42:17:15
Stefan
And one of the things there's a company that's doing, an open source alternative to Datadog
and their key selling point is that you can self-host it and I always thought that was weird
because I don't think you should self-host observability, because if your infrastructure goes
down, how do you know what happened? If you're self-hosting, your observability?
00:42:17:18 - 00:42:32:12
Stefan
Right. Like like what do you do then. Oh, our infrastructure's down. I can go look at Datadog and
I can understand and look at the tracing, the spans. I can see what services went down. I can
understand it. But if I'm self-hosting, it, in my infrastructure then, like, how do I know what
happened?
00:42:32:14 - 00:42:41:26
Dustin
Yeah. But also nothing prevents no, nothing. Also, data could go down right then you also are
blind so
00:42:41:29 - 00:42:48:23
Stefan
Yeah, but data going down is like AWS going down. That's a lot of a lot of money on the stock
market. That'll be really upset.
00:42:48:26 - 00:43:11:07
Dustin
That's right. I would also say that, the probability that datadog goes down is, is less than your
own infrastructure. I think at the end it's always a question of, of, of money and, how much you
can spend on such a service and again as again, what I already said on the, on the cloud part,
on the cloud architecture, on the, on the design principles.
00:43:11:10 - 00:43:32:14
Dustin
Mind your own business. And buy buy the service, unless you have very good reason to ship
your own stuff like, if. Yeah, if you're if a data the business is a couple of millions. Maybe it's
time to to move on and, optimize your stack and, yeah.
00:43:32:16 - 00:43:52:19
Stefan
The thing is, the problem I have with that is you don't know you're different because you're a
startup founder. But as an engineer, then, like, somebody actually told me this is that, they work
at, like one of the largest retail companies in the world. And, one of the engineers said, we are
not a tech company.
00:43:52:19 - 00:44:12:00
Stefan
We are a fashion company. And the issue with that is that, engineers like to build cool stuff.
They like telemetry pipelines. They like trying to self-host stuff. They would be super interested
in, you know, setting up, bare metal servers and the racks and everything. And you want to work
at a company where you get to do that type of stuff.
00:44:12:00 - 00:44:29:04
Stefan
And so the issue is engineers want to build cool stuff. They don't really care for the business.
Like, I have a couple friends that work at, like Pinterest, or they work at Walmart and they don't
actually care about Walmart, but they care about the tech, the stuff that goes into power that
they build cool stuff, and it's really cool.
00:44:29:04 - 00:44:51:21
Stefan
And same thing with Pinterest. Like they don't even have a Pinterest, but they the stuff that
takes to power Pinterest is interesting for them. What do you think on that? Like it took you a
little bit of time. We've seen it with all technical folks on the team that they went from a pure
engineer mindset to a business mindset like, let's get the job done because the customer
matters not, hey, this is the coolest solution.
00:44:51:21 - 00:44:58:03
Stefan
Let's build this because it's super cool. And then the customer comes second.
00:44:58:06 - 00:45:01:18
Dustin
Great question.
00:45:01:20 - 00:45:02:24
Stefan
I know it's tough because.
00:45:02:24 - 00:45:26:09
Dustin
Like, I mean, as an engineer, you always you love to experiment. You love to innovate, but you
also need to yeah, you need to compare with the reality. Like how if you if you build this, if you're
building a business, I think there are a lot more things you need. You have to worry about than,
than the about your foundation.
00:45:26:09 - 00:45:48:24
Dustin
So you need to build, you need to you need to build the right foundation. But nothing prevents
you from experimenting and innovating. So, I think you can you can still you can still do great
stuff and you can still bring in doing interesting stuff. For example at wundergraph. But, yeah.
00:45:48:27 - 00:46:12:00
Stefan
You need both. I think you need, like, I think this is a great career advice. Like, if you're early in
your career or you're a senior engineer or principal engineer at that point, you're not hired
because you like cool tech and you can build cool POCs. You're hired to make direct business
impact. And if you put on your business hat and think, okay, I'm going to build something, but
how is it going to generate more business?
00:46:12:00 - 00:46:31:18
Stefan
You can rise up the ranks pretty quickly. And for example, I have a friend, he works, I think it's
meta or it's Microsoft. He's a like, distinguished principal engineer. He makes like over two, 3
million a year, like he makes crazy money as an engineer. And people are always blown away
like, oh my God, this engineer, like, he makes 2 or $3 million a year.
00:46:31:18 - 00:46:55:27
Stefan
And it's like, you don't understand that the initiatives that he leads, they're not fun, they're not
cool tech, they're not crazy. They're very boring, but they drive significant revenue to the
company. And when he fixes a problem, it's a problem that's costing them millions of dollars.
And he does it only in a way that it brings impact. And so but Dustin I agree with you, 90%
needs to go towards business impact.
00:46:55:27 - 00:47:13:16
Stefan
But if you just focus on the business, some of the best stuff is just made by experimenting. You
know, like we tried out the AWS Lambda router, we experimented with all sorts of stuff at wunder
graph, and it actually led to some stuff that's actually used by our customers today. Yeah.
00:47:13:18 - 00:47:15:10
Stefan
Yeah. It is an interesting thing.
00:47:15:12 - 00:47:39:16
Dustin
It's it's always a matter of calculating risk and benefits. Like if there is a benefit of of of going this
approach huge, then we can think about to, to invest in it. But I don't want to write my own
JavaScript framework just for the sake of, of having fun and use it in my application, like, yeah.
00:47:39:18 - 00:47:42:14
Dustin
Go. Yeah.
00:47:42:17 - 00:47:59:01
Stefan
I’d agree. You know what I struggle with? And like, I, I don't think people understand this is that
the biggest thing is not that you can't do it, it's just that you don't even know what you don't
know. Like, oh, I want to build my own content management system. And it's like, people have
been doing this for a while.
00:47:59:01 - 00:48:19:18
Stefan
They made strict decisions because of their learnings. Same thing with building our router or a
GraphQL federation platform like, there's reasons we made these choices because of some of
the mistakes that we made early on. And it's like when you try to build something or self-hosted
something like you don't actually know what you don't know before you even start building
because you haven't been so deep into it.
00:48:19:20 - 00:48:31:17
Dustin
I mean, you can write your own interpretation database. I think you you will learn a lot, but I
don't want to care about the fundamentals when I when I have to build something complex.
00:48:31:19 - 00:48:35:04
Stefan
Yeah, but when do you care about the fundamentals?
00:48:35:06 - 00:48:36:07
Dustin
When?
00:48:36:09 - 00:48:36:18
Stefan
Yeah.
00:48:36:18 - 00:49:01:26
Dustin
When when my, when I mean, I would say every time there must be I think there must be a
good reason why you have to change fundamentals. For example, something doesn't exist yet.
It would enable your use case. You you, Yeah.
00:49:01:28 - 00:49:03:12
Stefan
Like, if it doesn't exist.
00:49:03:15 - 00:49:17:09
Dustin
Yeah, exactly. It doesn't exist. It would be a big differentiator for you on the market. Look at the,
there no reinventing or rewriting SQLite.
00:49:17:12 - 00:49:20:24
Stefan
Why are they doing that?
00:49:20:27 - 00:49:41:21
Dustin
Well, first of all, nobody would ever nobody would ever have done that because nobody
everybody knows that SQLite is super reliable. It is the most used database in the world. And,
now theyre rewriting it in rust. And I think, there want to leverage that on, on on the edge and
Yeah.
00:49:41:28 - 00:49:59:11
Stefan
But the, but this whole thing with the edge. So, there was a GraphQL backend as a service
company that was all on the edge. And then Vercel was like, deploy the edge, but then we're so
kind of like, dropped that initiative, like, like, what is the edge? And like, I'm seeing more and
more people, like, care less about it.
00:49:59:13 - 00:50:03:08
Stefan
If you will.
00:50:03:10 - 00:50:32:08
Dustin
Yeah. It's it's about, being being being local, being, near to to your customers. It's about latency.
It's about, Yeah, I would say performance, but you need to good use case. I mean, you I think
we wouldn't have any benefit from deploying our control plane to the edge. If our existing use
case is.
00:50:32:10 - 00:50:37:13
Dustin
That's already is already more than good enough for the, like.
00:50:37:15 - 00:51:08:10
Stefan
Yeah, I would agree. The only use cases that I can understand is, like. So, for example, like
what some of our e-commerce companies like for them, latency and like the web page being
slow, it actually loses money for them. So they have to be the most performant and it has to be
fast. Because the way you think about it is I'm a user, I go on and I don't know some Sheahan or
some fashion Nova, and if my experience on there isn't good, like I'm adding things to my
shopping cart and when I go to click checkout, it takes like 10s.
00:51:08:12 - 00:51:29:29
Stefan
The likelihood that I leave is extremely high because it's slow and it's not performant. So I can
see for like e-commerce edge being important because you want to be as quickly as possible,
get them from shopping to the counter to pay and then pay. But do you see anywhere else
benefits? Like maybe like streaming? Streaming would be good.
00:51:30:01 - 00:52:00:03
Dustin
Yeah. It really it really depends on the use case. I mean, even if you deploy your application or,
your logic at the edge, your database will probably still, sit somewhere else in your internal
structure. So, that's why fastly Cloudflare trying to build a complete ecosystem around that. You
have a key value store, you have, S3 API, you have not even a database.
00:52:00:05 - 00:52:23:02
Dustin
So then it makes absolutely sense. You can build complete application at the edge. And I mean,
what we, we did already like in Cosmos Cloud is a solid architecture. So we have, we have
implemented, cloud for worker that, is connected with an S3 integration where we upload a
router configurations and make them accessible to, to the customers.
00:52:23:04 - 00:53:01:17
Dustin
So we have we have to develop a small application that is essentially an Http server and has S3
integration, you can call it its database. And why did we do this? Because it's so easy to deploy.
It's we can be sure it's it's it's scalable. It works everywhere. It's, it's cost efficient. And we don't
have to deal with anything like, like deployments, maintenance because it's it's essentially for
us, it's just a script.
00:53:01:19 - 00:53:26:20
Stefan
Yeah, basically. And it works pretty well. One of the biggest things I hear with like, our
customers. So for example, we we have a great uptime. Obviously, since we provide Cosmo
managed, we have to adhere to certain SLAs. And, since customers self-host the router. So
they sell post a router on their infrastructure and then they interact through our studio on our
platform with a, oh, are we almost at time?
00:53:26:20 - 00:53:32:27
Stefan
this, right?
I just realized that's okay. I just realized we're almost that time. And you have an interview after
00:53:33:00 - 00:53:34:03
Dustin
Yeah.
00:53:34:06 - 00:53:53:11
Stefan
Okay. So I will ask this last question, and then we're going to have to end a little bit early
because we started late. But Dustin is interviewing and so we're actively hiring. But the router is
self-hosted. It interacts through the control plane, which is a Cloudflare, like you said, what
happens if our infrastructure goes down?
00:53:53:13 - 00:54:09:29
Stefan
The customer has the router self-hosted on their infrastructure, but their customers won't be
affected. Right? The only things that will be affected is they maybe can't log in to the Cosmo
studio and stress a little bit on why we made that architectural decision and like, what would be
the impact if we go down.
00:54:10:01 - 00:54:50:14
Dustin
Yeah. So first of all, we didn't want to, enforce people or to opt in our cloud because there are a
lot of use cases where people don't want to use cosmo router. And because we have integrated
opentelemetry, it's their choice if they want to push the data, for example, to Datadog to New
Relic. So, yeah. And also it's very, very important that we can say that they're there, that the that
our infrastructure is not a critical factor for being operational on their end.
00:54:50:16 - 00:55:04:18
Dustin
So it's it's it's it's a huge benefit also for us that we don't you can can't break customers will be
we are yeah. We are not the de facto when, when there, have issues.
00:55:04:20 - 00:55:10:18
Stefan
So I think this comes from our learning as well from Cosmos Cloud. You remember like when
flag would go down, our customers were affected.
00:55:10:21 - 00:55:37:00
Dustin
Yeah. So right now, there are two ways to, to deploy the super graph configuration. So you can,
you can build it locally and pass it directly to, to the, rather than the routers completely,
autonomous. It has no connection at all to the control plane and to, to Cosmo, except for
analytics purposes. But this is, handled gracefully when something goes wrong.
00:55:37:02 - 00:55:58:28
Dustin
And then there's the option that, you can issue a graph token, and the router will pull that
configuration from the CDN. And even in case of the CDN is down, by the way, we provide like
six nine on the, on the kind of ability even in that case, the router would be still function.
00:55:59:01 - 00:56:08:08
Dustin
It would just not be able to pick up the latest graph configuration that has been recently pushed,
to our control plane. Yeah.
00:56:08:11 - 00:56:21:05
Stefan
No, it's a good explanation. So I know we're a little bit over, but Dustin, thanks for joining me
today since Jens is out of town and, really appreciate you kind of just talking into it for your first
podcast. You did a good job. I mean, I told you, it's very chill. We just relax. We talk a little bit.
00:56:21:05 - 00:56:22:19
Stefan
Tech. What do you think?
00:56:22:22 - 00:56:28:15
Dustin
No, it was a great experience. A little bit of a time, but, Yeah, I'll.
00:56:28:15 - 00:56:41:00
Stefan
Let you get to it then. You got to get to your interview, right? Yeah. As long as you enjoyed it. We
had a good time. But Dustin, thanks so much for joining us. I'm going to clip this up. You'll see it
on LinkedIn. So make sure you share. And then yeah thanks so much I'll see you soon.
00:56:41:03 - 00:56:44:11
Dustin
Thank you. But.
00:56:44:13 - 00:56:45:00
Stefan
Later.