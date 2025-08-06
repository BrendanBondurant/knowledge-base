
00:09:03:15 - 00:09:23:07
Stefan
Happy to be back on the podcast. And we got some exciting topics today. So Jens let's kind of
kick this off. You've been tweeting about this, but it's also been controversial. Like if you've seen,
Zig, the founder of Century, he's also been talking about it is that a lot of VCs are really not OSS
friendly, open source friendly.
00:09:23:10 - 00:09:48:27
Stefan
And one of the things that you brought up is how fantastic open source is for inbound sales. And
so let's talk a little bit about like our OSS inbound sales notion and like what you think about it.
Because a little context on it is that Zig said that OSS is good for VCs. This is the VCs point of
views for seed and series A, but around B or C, if you're not aligned with the VCs, they will force
you to flip the camp.
00:09:48:27 - 00:10:03:28
Stefan
And you've seen it with HashiCorp. Where is that? They flip the licensing because it they really
just saw it as a funnel. But for us, I don't see it just as a funnel. I think one, it's a philosophy but
also an inbound funnel as well. What are your thoughts on that?
00:10:04:00 - 00:10:07:22
Jens
Okay. That's a that's a big topic.
00:10:07:24 - 00:10:09:12
Stefan
Theres a lot to unpack.
00:10:09:15 - 00:10:37:15
Jens
Yeah. I mean, one aspect is in the, in the, one, one core part of, of the customer architecture is
customer router. And customer router, it's, it's serving the requests between client and
subgraphs. And it translates, all of that. And it needs a schema. So we need a schema registry.
So that schema registry and customer we, we call a, custom control plane.
00:10:37:17 - 00:11:21:06
Jens
And these two components, for example, in Apollo, the control plane, it's graph OS and it's
closed source, and it's just a proprietary service. And our control plane is open source. You can
self-host and run it. And the Apollo router is elastic license. And, our router is Apache. And so
let's say you work in a very big bank and, or you work in a, in a big FAANG company, and you
would like to federate something or you are interested in creating federated architecture.
00:11:21:09 - 00:11:45:00
Jens
And then, you know, the, the legal guidelines and people tell you like, hey, what's the license of
that repository? And you look at the license and you could use Apache, you could use like MIT,
but if it's something different, legal will simply say, we we cannot allow you to use this. So now
the the POC stopped before it began.
00:11:45:02 - 00:12:14:18
Jens
And the second thing is, like we are developers and one of our, our target audience, big target
audience for us is developers. And so, we know how we tick and developers don't like to sign up
somewhere just to try something out. And so one of the things we're, we're actually looking at is,
so you can already self-host Cosmo.
00:12:14:18 - 00:12:39:05
Jens
And even if you work in a, in a big bank, it's super simple for you to, to try it out and run it
yourself. And the second thing is we're even trying to making self-hosting easier. And this it
sounds counter intuitive because you could say, well, if we make self-hosting easier, are we not
making it harder for us to get customers?
00:12:39:08 - 00:13:05:20
Jens
Because like our our managed solution cosmo cloud? It's, if we make self-hosting easier then
then why would people sign up and do that? And the reality is. So first of all, the router is an
infrastructure component. And one of our main goals is that we want everybody in the
Federation space to use this router as a base.
00:13:05:22 - 00:13:31:00
Jens
And if you, if you want to to customize it, then you should be able to customize it. If you want to
build custom modules or something, do that. If you want to run it with our managed cosmo
stack, that is great. We love that. We love to to work with you together. But even if you don't
want to do that, if you look closely, we have built the router in a way that you can.
00:13:31:02 - 00:13:59:05
Jens
You don't need Cosmo. You can just take the router and point it to an S3 bucket. And in this
bucket there's the config for the router, the execution config. And then router works. And so
yeah, we, we believe that if you really want to build, the standard in an ecosystem, it needs to
be open source, because otherwise you have these legal issues.
00:13:59:12 - 00:14:29:12
Jens
And on top of that, it needs to be affordable. Like if someone wants to scale up and they have a
lot of requests, you need to have a solution that works for everybody. So like at super small
scale, it it should be affordable. And you should have good analytics. But also if you have like
billions of requests per day, it should be similarly affordable.
00:14:29:14 - 00:14:59:06
Jens
And yeah, we, we see with alternative products this value is simply simply down the line. And for
us I would say one, one of the, one of the most interesting observations we didn't think about
that's in the very beginning is, but one big observation is when you make it open source and you
have a really powerful managed solution with with value, with a lot of value added.
00:14:59:09 - 00:15:25:13
Jens
What happens is people in a big bank, they try it out, they do a POC, even without talking to you
because it's too complicated. They do a POC and then if everything goes well, they say like,
okay, POC was great. We we love your tool. We would now, do a POC with your managed
solution because we don't want to host the whole cosmo stack.
00:15:25:14 - 00:15:47:01
Jens
It's too complicated for us. And then they start legal process security validation and and all this
kind of stuff. And what is so cool about this motion is we didn't do any selling. It's really just them
coming to us and saying, hey, we we we love your open source router. We have set it up. It
works. We have a small project.
00:15:47:03 - 00:16:08:08
Jens
Can you now help us get into production. And that's that's the sales pro. It's not it's not top
down. It's it's it's it's great bottom up motion. That gets us access to, to super big companies
and, yeah, we're, we're super happy with that. And you see, there's a lot
00:16:08:11 - 00:16:27:21
Stefan
Not add maybe after. But I want to like just kind of dive deeper into it. So like full transparency,
like we did the same approach with the SDK. You remember it was fully open source, but why
like full transparency? We made some money off them off of it. It was okay. And then we try to
build a cloud on top of it.
00:16:27:24 - 00:16:46:26
Stefan
But Jens what's the main difference between why now with Cosmo is we're making 100 x more
money than we were with whatever with the SDK, but they were both open source. We kept the
same notion. And I'll never forget this point where when we were pivoting, we were like, Jens
was like, we need to make it fully open source.
00:16:46:26 - 00:17:02:24
Stefan
And we were all like, but we just did that. It didn't work. And he's like, trust me, we need to make
it open source. Just trust me on that. Well, why did you come up with that? Like you had that
thinking a year and a half ago, and it ended up being right. Is it the same intuition that you have
now too to make it even easier to self-hosted?
00:17:03:01 - 00:17:08:06
Stefan
And what was the difference between the SDK and Cosmo, especially in terms of revenue?
00:17:08:08 - 00:17:49:09
Jens
So, the SDK allowed you to define API dependencies, glue them together so you could say,
here's a Postgres database, here's a rest API, here’s a GraphQL API, glue them all together into
a single unified GraphQL schema, and then expose that as an API. Cool tool. Was a lot of fun to
build. Problem. The, I would say that the impact radius of the solution and that's it's like super
important concept impact radius of the solution is single person or single team.
00:17:49:12 - 00:18:21:07
Jens
This is not a multi team solution. And so if you want to sell to enterprises and you want to make
money, there needs to be more impact then single person single team like big budgets in an
enterprise. You don't have big budgets. For one dev can create an API faster. That is. No, it
needs to be something like all people across 20 teams.
00:18:21:07 - 00:19:15:04
Jens
They can work more efficiently together. Or they can. They can. Yeah. Build an API together with
Federation, for example. That, that that's one aspect. Okay. The this radius and the second
aspect, this kind of what we figured out is, you have solutions that are in the infrastructure
bucket and you have solutions that are in the collaboration bucket, like, customer router, it's
infrastructure and Cosmo Studio where you have schema checks, where you have, for example,
our playground with with as an explorer of the schema one, one feature we recently added in
the explorer, you can see if you need to be authenticated, if you want to use a