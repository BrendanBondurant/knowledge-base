00:27:51:12 - 00:28:26:10
Jens
Yes. Like and I think in infra, if someone creates a proprietary product with a high margin that is
billing per traffic, then you can, you can, you can set a counter and someone will build an open
source alternative. And they they will create an alternative model where self-hosting works in
some way or where they, incentives better align for people with, with high traffic.
00:28:26:10 - 00:28:46:19
Jens
And, yeah, which is one of the reasons we said like or, you know, I still remember like one and a
half year or. No, I think it's now two and a half years ago, I was on vacation and I was, you
know, every time I go on vacation, I'm thinking outside the business.
00:28:46:22 - 00:28:47:07
Stefan
And, and.
00:28:47:07 - 00:29:15:07
Jens
I, I came back and I told Stefan, no, I, I actually went on a call, like, I called you guys because I
was like, calling my co-founders and said, guys, we will make Cosmo open source 100%. And
we were debating like, you can't do this. Like we're giving away everything and so on and so
forth. But I was like, you know, I, I don't want to build this whole platform and router and
everything.
00:29:15:07 - 00:29:43:24
Jens
And then someone comes around the corner and says, open source. So, you know, we say
open source alternative to Apollo Router. And then we make the control plane closed source.
And then the next guy comes around and says open source alternative to cosmo control plane.
And I'm like, no, I don't want this to be happen. Like, I, I want everybody to to use it like, like
they want.
00:29:43:24 - 00:30:14:15
Jens
And I think our cloud service needs to be much more powerful and it needs to give much more
value than just Docker compose up. And, you know, like the these days, if you look at our cloud
stack, there's clickhouse, that's database migrations. We now have our telemetry pipeline
hosted in multiple regions. It's highly available. We have the CDN hosts highly available in those
operations.
00:30:14:18 - 00:30:41:03
Jens
We have internally. We now use Kafka to ensure that we have high throughput processing of the
telemetry pipeline with back pressure and all these kind of things. It's such a complex stack. For,
for most customers, it's it's just so much easier to. Yeah, talk to us. We we figure out, pricing
strategy that that works for everybody.
00:30:41:03 - 00:31:24:12
Jens
And, yeah, that's so we're we're not just running Cosmo. We're, we're doing more. And it's a
complex second. The question if you're if you really want to self host is do you want to, to own
all these components or do you want to use them. But that's one thing because it's open source,
it kind of establishes a level of trust, because even if we in the future, driven by VCs or
whatever, even if we decide to change course, which I, I don't intend to do because we have, a
different strategy that goes beyond Cosmo.
00:31:24:12 - 00:31:57:10
Jens
But, even if we would, you can self host Cosmo. And I think also, if you could self host
something, it somehow sets, threshold of how hard can you squeeze a customer? And I think
this aligns our values better with the customer values. Like, you know, if you if you can, if you
can self host something for, I don't know, let's say, let's say 1 million per year and we're charging
you 50 million.
00:31:57:12 - 00:32:12:01
Jens
Something is wrong. Completely wrong. And and by making it open source, we, we kind of set
the threshold to ourselves of, of playing fair. And to be honest, I think that's that's good.
00:32:12:03 - 00:32:31:04
Stefan
Yeah. And I think those are I mean, I agree with all of those. And I think the benefit of open
source is definitely on the procurement side. But also, I had the conversation with my mom, like
I first I had to explain to her what Cosmo does using the waiter example. And then, once they
got that, they were like, well, how can you sell something that's basically free?
00:32:31:06 - 00:32:50:15
Stefan
And I was like, mom, like, the mode isn't actually in the software, it's in the knowledge and the
experience of running it, but also the knowledge and experience that we bring from all of our
customers. And what I love the most about our customers is they love what they do. And we get
to work with some amazing, talented engineers, but they're also open to meeting with other
customers.
00:32:50:15 - 00:33:08:22
Stefan
So when we have a customer that's using EDFS or subscriptions, we can take that knowledge,
take it to another organization, and then they become successful subscription. And that's only
possible. I really think it's only possible through open source. And this past week we announced
a really cool customer, which I want to dive into this topic a little bit.
00:33:08:22 - 00:33:14:14
Stefan
So, I'll actually bring up let me share my screen so people can see the blog post.
00:33:14:21 - 00:33:18:23
Jens
Okay. Can I add one one thing to this mote, right.
00:33:18:27 - 00:33:21:15
Stefan
Yes, yes. Before I share, go ahead.
00:33:21:18 - 00:33:53:27
Jens
So this week a customer came to us and said we're using, we're using your. So our router has a
feature to upload files using multipart. Yeah. And they were not exactly implementing the spec.
They wanted to send the requests slightly differently. And they said we don't have the resources
to to change all our clients. Can you add a feature flag or can you somehow help us how to how
to accomplish that?
00:33:54:00 - 00:34:19:06
Jens
And here's the thing. People have business goals, like your business goal is not to host Cosmo.
Your business goal is to find a partner that helps you get this thing working. So. So ultimately,
there are there are a lot of people you don't really have to convince them to to use the service or
partner up with us because they, they are busy and they, they want help.
00:34:19:06 - 00:34:25:04
Jens
So yeah, we're, we're we're not so worried about making something opensource.
00:34:25:06 - 00:34:41:19
Stefan
If you remember the guy from suit supply when we first started talking to them. So they were
evaluating Cosmo, but then they ended up not even going to GraphQL. But we were talking with
this guy and he goes, I'm not in the technology business. I'm in the retail business. He's like, I
just buy software to get the job done.
00:34:41:21 - 00:34:58:13
Stefan
And I remember that always stuck with me because some people are in the technology
business like us, other people are in whatever business that they're in. But if it solves a
business goal, are you really in the business of hosting, building your own gateways? It's cool.
It's great, and if that's something you want to do, you should really consider applying to
WunderGraph, because that's what we do.
00:34:58:15 - 00:35:12:27
Stefan
But if you're at a bigger company and they're making you build gateways, there's a lot that you
don't even know that you don't know. And there's a lot of use cases and edge cases you haven't
even thought of yet. But if that does interest you, we are hiring across the board. So take a look
at some of our open job sites.
00:35:12:27 - 00:35:34:04
Stefan
But yeah. So Jens with that in mind, I wanted to transition into this amazing graphic that we
have. So this was written by Brendan, our technical content writer, and I am this is probably one
of the customers that I'm the most excited about. So SoundCloud. We've been working with
them for how many months now? 4 or 5 months?
00:35:34:06 - 00:35:35:00
Jens
Yep.
00:35:35:03 - 00:35:55:29
Stefan
I'd say so. And for those of you that aren't familiar with, with SoundCloud, SoundCloud is a very
strong engineering team, extremely strong. They're the creators of Prometheus, they're the
creators of the BFF framework, and they've kind of migrated over to GraphQL Federation, and
we work very closely with their team. Their former CTO, Matthew Druker. He will be joining us
on the podcast in a couple of weeks.
00:35:55:29 - 00:36:18:11
Stefan
So it'll be great to have some questions beforehand about what it's like to be a CTO. He's been
a CTO at multiple companies, and he's also, he was the CTO at, SoundCloud. But Jens, this
was super exciting from a tech point of view. I mean, the headline is a banger. They cut their
computing costs by 86%, walked me through a little bit from the beginning and, you know, keep
the details high level.
00:36:18:11 - 00:36:39:25
Stefan
But this was a really exciting use case that we had with SoundCloud. Also, the graphic is my
favorite, but basically the Tldr is they cut the, infrastructure cost by 86% and when we estimated
it with them, this was about $265,000 in annual savings on AWS Fargate. And then with Cosmos
and Cosmos Studio, they were able to increase or improve the query latency by 45%.
00:36:39:27 - 00:36:56:07
Stefan
So there was performance improvements all across the board. Do you have any thoughts on
that? What was what like you worked very closely with the tech side. I worked mostly on the
procurement side, but tell us a little bit on the insides of like what we did with SoundCloud, why
it was so exciting as well as I mean, the partnership with them was just fantastic.
00:36:56:10 - 00:37:46:09
Jens
Yeah. So first of all, the the engineering team of SoundCloud is really smart and it's it's a lot of
fun working together with them. They, they have a lot of scale. And for, for someone like us
creating a router and this whole infrastructure, it's always super useful to have very tech savvy
people on on the other side of the table because they bring the scale, they bring the use cases
and, the operational complexity, and we bring the, the, the tech, we bring the solution, and
together we get insights into, okay, well, what happens if you throw billions of requests at
Cosmo router?
00:37:46:12 - 00:38:22:11
Jens
What are the pitfalls? What what can go wrong and how can we improve the product. So we
always love these kind of relationships because they are definitely a power user. And they they
help us to to make it better. And then at the same time, so they, migrated from a Node.js based
gateway and as we all might know, Node.js being single threaded and just by the nature of the
architecture has some limitations in terms of how it can handle, throughput and, and other
aspects.
00:38:22:14 - 00:38:55:28
Jens
And we know that, quite a lot of people in the market are still on Node.js based, GraphQL
federation gateways. So, what you can expect by migrating to, a Golang based router with
query planned caches and many other improvements, it's, first of all, you get a lot more bang for
the buck. So we get more throughput, out of a single, out of a single instance.
00:38:56:01 - 00:39:38:01
Jens
Deployments are much easier because our router is, it's working multi multi-threaded. So it's it's,
it linearly scales with the number of CPUs. So, we, we did some, some, benchmarking with, with
customers where we found that, if you, doubled the number of CPUs, you double the, the
amount of throughput you get. And so that means you don't have to deploy, hundreds of single
CPU pods on your Kubernetes, but you can actually deploy instances with 4 or 8 CPUs.
00:39:38:01 - 00:40:13:24
Jens
So it's, it's, less complex to handle. And then the architecture is just faster and more efficient.
So, so that means we get more requests per, per watt per per per power. So that means overall
you can deploy much less instances in case of SoundCloud, 86% savings. And then on top of
that, because the component, the router is more efficient.
00:40:13:26 - 00:40:56:02
Jens
We also, decrease latency. So the single request, we're serving it faster. And now SoundClouds
bottleneck is the subgraph. So the service behind the router. And and that's something we see
quite often. We had another customer who did a POC. And as part of the POC, they they did
heavy benchmarking. And if you set up or if you give Cosmo enough resources, then you are
actually measuring your subgraphs because Cosmo is faster than your subgraphs, because we
have so heavily optimized it and, yeah.
00:40:56:02 - 00:41:30:22
Jens
So overall, it's a great relationship with SoundCloud. In the in the beginning, we built, we, we
collaboratively built a library where you can send analytics data from your Node.js based,
GraphQL gateway or Node.js based GraphQL server to Cosmo, which is pretty cool because,
you might have the issue during the migration that you want to use both services for, for a
period of time so that you can serve some traffic here, some there.
00:41:30:25 - 00:41:56:08
Jens
And then when you move to Cosmo, you want to have breaking change detection based on
traffic. So if you if you don't yet run on on Cosmo, you you would lack this kind of data. So we
build a library that can send, analytics data from a Node.js based gateway to Cosmo. And so
you can, you can kind of warm up the analytics database and then make the switch.
00:41:56:08 - 00:42:02:16
Jens
So yeah, that's I think that's, that's, mostly the SoundCloud story.
00:42:02:19 - 00:42:18:09
Stefan
Yeah. And it was fantastic collaboration all around. And what was cool is there's a quote in the
case study is like, or the creators or Prometheus or the creators of the framework, and they
scope it out and they were like, we don't want to build our own gateway. We should just partner
with someone has done it before.
00:42:18:09 - 00:42:34:11
Stefan
And that's exactly what happened with SoundCloud. And we also have more exciting features
coming soon, so I'm happy that theyre a customer, I use them daily. I actually am a pro user of
SoundCloud. That's where I find all my new music, so check them out. Also check us out if
you're interested in partnering up with us. But yeah.
00:42:34:14 - 00:42:56:19
Stefan
Okay. Let's go through a little bit. There's some spicy topics on here. We have to keep the last
one for the end. But talk to me a little bit about what you've been seeing from these rest
connectors. So obviously Apollo's pushing these out. There's other vendors in the space that
are trying to like adapt it. And I don't know I know your thoughts on it, but to me it just doesn't
feel right.
00:42:56:21 - 00:43:15:23
Stefan
And I'd love to know from you why why doesn't it feel right. And we've looked at the examples. It
goes back to that model of charging per request, and that this might just be a gateway to just
charge more per request. But what are your thoughts on these Rest connectors that are coming
out into the GraphQL space?
00:43:15:26 - 00:43:48:18
Jens
Yeah. So I, I understand the motivation or I think I understand the motivation. You, you have
existing Rest APIs and you, you want to bring them onto the graph and, yeah, ideally you don't
have to maintain extra subgraphs. You can just write a bunch of directives. And and now it's, it's
on the graph. And I think for super simple use cases it's probably going to work.
00:43:48:18 - 00:44:22:17
Jens
Or even for medium advanced use cases, it could work. But at the same time, what I see is,
okay, you write these descriptions, you describe how to get the data from a URL, and you also,
you describe how to probably map it. And the the issue here is the examples we see. They go
like okay, you go to a URL and back comes a JSON.
00:44:22:19 - 00:44:51:21
Jens
And then we map this JSON. And this is, this is not the reality. The reality is if you have well-
designed REST APIs, a REST API can return anything, I don't know, like it can return the 200.
Okay. It can return, bad request. It can return 404, 401. It can return all sorts of status codes.
00:44:51:23 - 00:45:21:16
Jens
It can also return unions or combinations like, you know, there's, there's one of or any of, like
these, these, directives and open API and the REST API can also have, a field that acts like a
discriminator. And based on this field, the response shape will look differently, like it's it's open
API, it's JSON schema. So it can get super complex.
00:45:21:18 - 00:45:51:06
Jens
And so far the examples I saw is just yeah URL you get one thing back super simple and that's
it. And I don't know it's it's not realistic. I think what is much more realistic is that you need a lot
of, a lot more code to handle different cases. And then there's the question if you write these
directives, you need to have a process of getting this into production.
00:45:51:06 - 00:46:18:23
Jens
So how do you test that the directives properly describe your API. And then in the future, if the
API changes or you need more features, it means you need to change these directives. And
once they are changed, you need to test again that it works. And what I have seen in demos is
we create these directives. Then we open the playground and we make a test request.
00:46:18:26 - 00:46:50:26
Jens
And now we see this works. Okay. Yeah. That's not how we do CI. We do CI by running a test
framework of sorts. So if I if I can only describe the schema with directives, how do I write my
tests. Because in the end I need to write code to run a test framework. So if I write code for the
test framework, can I also just write code for for the resolvers.
00:46:50:26 - 00:47:31:06
Jens
And then I can do all sorts of mapping and everything. And the other thing is all of this is super
easy if we're talking about, GET requests. But what about PATCHes? What about POSTs? What
about mutations in general? Like you can't. If you have a well-designed REST API, you can't just
map a GraphQL input to a JSON PATCH object or POSTs if if I if I make a POST and I open the
playground to test it, then I'm mutating data.
00:47:31:06 - 00:47:58:11
Jens
So now I need a mock or like and how do I do all of this? So I don't know. It doesn't feel right for
me. To give you an example, Stripe, if you want to integrate with Stripe, there is a component
that Stripe offers where you can set up a Stripe mock locally because nobody wants to run tests
and send money.
00:47:58:14 - 00:48:23:02
Jens
Why, why, Stripe or create transactions? You want to run this against the mock. So you need a
valid Stripe mock of sorts. And you can run this locally or in your pipeline. So you need
orchestration code to run this Stripe thing. And yeah, I don't know. So I don't want to say it's
100% bad, but I understand the desire.
00:48:23:04 - 00:49:03:07
Jens
It needs to be easier. Yeah. To bring rest and other legacy APIs onto the graph and at the same
time and, and, like, you know, it's it's competition, but, I think my, my, my biggest pet peeve with,
with Apollo is I think they rush these kind of things. I think we need to go much slower and think
more about what is what is a good framework to bring REST APIs onto a graph, because there
are problems like you need to solve ‘n plus one’ problems.
00:49:03:07 - 00:49:43:10
Jens
Yes, you need to solve authentication and yeah, so, I don't know, I, I would love if we could
move a little bit slower and, but yeah, it is what it is. And, and the harsh reality unfortunately, is I
think we, we will end up supporting it anyways because at some point people want to migrate to
cosmo and they say, yeah, but we use these directives and yeah, until then, maybe we figure
out a better way to, to do, to do REST with GraphQL.
00:49:43:10 - 00:49:50:11
Jens
But so far, yeah. The other aspect. Sorry for my real quick.
00:49:50:11 - 00:50:08:03
Stefan
Real quick Jens, And before we jump in there, we have a decent amount of viewers. Guys stick
around till the end because, we have a cool, I guess, a surprise or it's a bundle of knowledge
that you don't want to miss and you definitely want to get access to so Jens continue your rant.
But please stick around till the very end.
00:50:08:09 - 00:50:25:24
Stefan
We're going longer for just ten minutes and five minutes, we're going to announce something
really cool that we spent a lot of time working on. Honestly, my fault because Jens told me about
it three months ago and it took forever. But I'll expand on that a little bit less. But Jens continue
on the REST connector. So I understand the technical application to implement.
00:50:25:29 - 00:50:32:12
Stefan
I don't know the work, but you know, the word I'm trying to say, but I understand that part. But
continue on the REST connectors.
00:50:32:14 - 00:51:06:27
Jens
Yeah. So I understand the desire. But at the business side, I can also talk to all our customers
and it doesn't seem to be the biggest problem to write the subgraph. There are many other
problems like security. What? I hear people talk a lot about is Things like the @provides
directive and @requires directive and like these directives in general.
00:51:06:27 - 00:51:41:02
Jens
And how can we properly map dependencies between fields and how can we achieve better
type safety in subgraphs, and how can we achieve that? If a subgraph says they implement a
schema, how do you actually verify that they really implement that schema? So these kind of
things so the quality of subgraphs, the quality, the type safety, the developer experience of
creating subgraphs.
00:51:41:04 - 00:52:09:24
Jens
Yeah. We we think there's a, there's a, there's a huge gap. And I think if we, if we make building
subgraphs better and easier and more type safe and all these kind of things, then there is the
question of is REST connector? Is it really the biggest problem or. Yeah. So but this is this is our
focus, this is our understanding of the of the market.
00:52:09:24 - 00:52:16:24
Jens
And yeah, future will will will tell us if, if we're right or wrong or whatever.
00:52:16:26 - 00:52:44:22
Stefan
Yeah, TBD. We'll figure it out. It's I haven't been hearing it from our customers. But then again
let's see. Let's see where the market pulls us. I do know that one of the biggest use cases for
GraphQL federation is modernization efforts. It's companies that have grown super fast. They
have a lot of tech that or that. They're just significant behemoths like SAP or large big
companies, and they want to modernize their stack and they have a bunch of legacy old Soap
or REST APIs.
00:52:44:22 - 00:53:03:04
Stefan
I can see the use case there, but like you said, I think the approach is a little rushed. I think it
needs to slow down a little bit, use these behemoths as a way to kind of move towards that. But
I have the same thoughts with that. And then guys, since we are almost at time definite. Yes.
00:53:03:07 - 00:53:04:24
Jens
Just one thought.
00:53:04:26 - 00:53:10:05
Stefan
Yes. Continue. That on the REST connectors though.
00:53:10:07 - 00:53:14:20
Jens
Yeah. Like but it's, it's the last the last puzzle.
00:53:14:22 - 00:53:17:06
Stefan
What is it?
00:53:17:08 - 00:53:54:17
Jens
From conversations with, I would say our biggest customers and users, I would say the, the big
thing I learned is the most important thing is the schema. The most important thing is to have a
good and well-designed schema. If we are building our schema in a way that wants to just
connect REST APIs, there's a likelihood that we are leaking the REST API abstractions into our
schema, because the REST APIs might dictate structure.
00:53:54:17 - 00:54:23:05
Jens
They might dictate behavior that we actually don't like in in the GraphQL world. Or maybe it's not
really compatible with GraphQL. So yeah. Our we're what we're what we're aiming for is to help
customers build great schema and to build a great API. And, this might be conflicting with
connectors. So that's my my last thoughts on the topic.
00:54:23:05 - 00:54:44:07
Stefan
Your mic, your mic drop. Boom. No, but very fair. And then last topic I want to discuss. And so I
made a little joke. Jens had this idea. I would say November or December, but he's like, you
know what we should do? We should interview all of our customers and we should create a
State of Federation report.
00:54:44:10 - 00:54:59:05
Stefan
Postman does it with their state of APIs report. And so I was like, yeah, Jens, that's a great idea.
But a lot of stuff has been happening between it took me forever to get this out and finally into
the public. But today, what we're excited to announce, let me present my screen.
00:54:59:07 - 00:55:01:24
Jens
You didn't like the idea right.
00:55:01:25 - 00:55:26:28
Stefan
I just thought because I will explain why. So I like the idea. The only thing is, is it's a little bit
tricky because our market size isn’t massive. So the state of APIs from postman was like
45,000. And so we're giving you the full disclaimer. This state of GraphQL Federation report is
based on insights from over a thousand developers, architects and CTOs, but from our base,
our customer base.
00:55:26:28 - 00:55:46:07
Stefan
So full disclaimer, but that doesn't mean that the information inside it is not useful. So if you
head over to our website, you'll see at the very banner that it says the state of GraphQL
Federation. And you can quickly just enter in your email and you'll be able to get the report
emailed over to you. But this is jam packed with information of why GraphQL Federation.
00:55:46:14 - 00:56:15:27
Stefan
It comes from some great use cases, great customers that we have as well as from comments
and everything on them. Federation trends that we've seen. You'll also notice that we still have
the disclaimer there that all the respondents in the survey are WunderGraph customers, or in
the transition period of becoming a WunderGraph customer. But the information that is in there
is jam packed, and it also includes the future of federation where we see federation going and
why customers have been adopting federation.
00:56:15:29 - 00:56:48:19
Stefan
And so this is available today. It's a 48 page report. Just head over to the state of GraphQL
Federation slash 2024 and you can get the report. Jens. Any thoughts on this? I know why you
wanted to do it I think is jam packed with information, but what are your thoughts on the
GraphQL Federation, especially with that Gartner quote, which is let me scroll down to it and I'll
read it out loud, because this has been a milestone in the Federation space, is that by 2027,
more than 60% of enterprises will use GraphQL on production, up from less than 30%.
00:56:48:21 - 00:57:04:17
Stefan
But what's even more interesting is that 30% of these enterprises that are using GraphQL will be
using GraphQL Federation. This is up less than 5%. So Jens, what are your thoughts on the
state of GraphQL Federation? Why do we do it? What are the trends that we're seeing and what
can people expect from this report.
00:57:04:19 - 00:57:33:20
Jens
So our observation in the in the market is that, you know, when we when we started building
Cosmo, we, we, we initially thought that, most of our market would be coming from Apollo
because we're, we're the open source alternative to Apollo, or at least that's how we started.
And we thought most of our market is is coming from there.
00:57:33:22 - 00:58:09:13
Jens
What we what we see like this year, for example, let's I don't know, 80, 90% of our customers
are coming from outside Apollo. So the market is expanding. There is a lot of traction, a lot of
companies adopting, adopting federation and I wanted to start this initiative because I think, it's
super important to educate outside the people who are not yet on federation for them to
understand.
00:58:09:13 - 00:58:34:04
Jens
What do the people think who are on federation, how do they think about it? How do they, adopt
it? What are the benefits? Why do they do the adoption, all this kind of stuff. So we want to
share the knowledge from within the community with, or within the Federation community, with
the wider API community, so that everybody can, can learn.
00:58:34:04 - 00:59:00:05
Jens
What are the what are the impacts? And if, for example, you're a developer and you work at a
big bank or whatever, and your company is not yet using Federation, you want to have material
for your management to convince them this is the right direction and other companies are doing
it. It's successful. They have benefits. And so yeah, I think it's it's it's super important to to share
this, message.
00:59:00:08 - 00:59:24:00
Jens
And also you saw it with the disclaimer. So yeah, we interviewed all our customers. But what we
really would love to see if you sign up, we will include you in the, in the next survey for, for this
year. And we are really hoping to to see, to see also a much bigger usage numbers for Apollo
Federation.
00:59:24:02 - 00:59:56:00
Jens
Because ultimately, Apollo is the is the is the market leader and one very important message we
want to get out is we see large organization using both. So they use Apollo, they use Cosmo
side by side. And I think it's important for a stable ecosystem that there is no one player, that
there is no monopoly, but rather there are multiple players in the market.
00:59:56:03 - 01:00:26:05
Jens
There is competition. To be honest, I think if anything, we really pushed Apollo very hard to work
on, on, on some things and to, to improve stuff. So I think it's, it's great for everybody to have
competition and yeah, the, the state of federation should show that, federation is becoming an
enterprise standard. Companies are adopting it.
01:00:26:05 - 01:00:38:20
Jens
And, yeah, we, we really hope that this helps you to convince your management and your
company, to adopt federation. Whichever vendor you're going with.
01:00:38:22 - 01:00:55:01
Stefan
Well, said Jens, so you guys can find the report on our website. It's on the banner. So if you just
head over to WunderGraph.com, you can click on the banner and it'll take you there to get to the
report. You can also head over to WunderGraph.com slash state of GraphQL federation slash
2024. With that. That is a conclusion of another episode of The Good Thing.
01:00:55:01 - 01:00:59:05
Stefan
But Jens, what's the good thing?
01:00:59:07 - 01:01:02:08
Jens
We're back next week.
01:01:02:11 - 01:01:20:11
Stefan
The good thing is we're back next week. We have some exciting stuff planned in the next couple
of weeks. We have an exciting announcement coming in the next couple of weeks, so maybe
we can hint a little bit about that. Look out for another case study coming out next week as well.
Feature updates from February. We're going to have a massive blast of those.
01:01:20:11 - 01:01:42:19
Stefan
There was a lot of stuff that happened in February and just a lot of exciting stuff. As always, we
are hiring. If you're really interested in GraphQL gateways or just high performance gateways
Federation, or just working really closely with enterprise customers with developer tooling,
please head over to our jobs page and apply. We are hiring. We have a person full time now
helping us recruit these, so we are growing and we are in a very good position.
01:01:42:19 - 01:01:59:09
Stefan
So if you want to join a really cool startup where we talk about cool stuff, build cool things, and
we're just completely transparent about the entire process, take a look at WunderGraph and as
Jens mentioned, the good thing is we are back next week. Thanks everybody. I just realized my
shirt says I don't work here. I actually do work here.