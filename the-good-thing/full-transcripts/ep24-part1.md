Episode 24
type: podcast-chunk
00:00:25:08 - 00:00:39:18
Stefan
And we're live. Welcome back, ladies and gentlemen. I always do the same intro I just realized.
Welcome back, ladies and gentlemen, to another episode. I'm going to change that up. If you
guys remember, I used to watch, like, Call of Duty videos growing up. And so I would always be
this guy. He'd be like, yo, yo, yo, it's your boy.
00:00:39:18 - 00:00:41:27
Stefan
I should do that one. Yo, yo, yo, it's your boy.
00:00:42:00 - 00:00:52:15
Jens
down developers.
Stefan. Did you know there's, today we talk about the case study, and it says that, AI, slows
00:00:52:17 - 00:00:53:20
(Mix)
You know, I'm actually kind of.
00:00:53:20 - 00:00:56:11
Jens
Why? Why? That's not a problem for you.
00:00:56:13 - 00:01:00:08
Stefan
Well, let me guess, because I'm not a developer.
00:01:00:10 - 00:01:00:22
(Mix)
Hey, one.
00:01:00:22 - 00:01:09:28
Stefan
Thing I actually built, a little thing over the last week, and I'll share it, but, say what you want. I'm
a prompt engineer. Now. Yes, Dont need to.
00:01:09:28 - 00:01:10:26
(Mix)
But nobody needs.
00:01:10:26 - 00:01:18:08
Stefan
To be a developer anymore, because in a couple of years, it's all going to be gone anyways.
Just going to be people just prompting prompt engineers to the new thing.
00:01:18:10 - 00:01:27:19
Jens
Yeah, we don't need developers anymore. Everything can be generated. Nobody needs to
review it. We can fully trust LLMs. Just throw it in
00:01:27:21 - 00:01:32:17
Stefan
we can just get rid of GitHub too. Like what's the point of GitHub anymore?
00:01:32:24 - 00:01:41:08
Jens
WunderGraph we'll be a one person company and it's just me. I wake up in the morning, I'm
like, okay, let's let's go.
00:01:41:12 - 00:01:48:15
Stefan
AI salespeople just go run. Good morning guys. Three of us stand up with them. And over there.
00:01:48:18 - 00:01:59:28
Jens
And then 100 AI developers and they will know themselves what to build. Actually, they could
they could just fire me. They don't need me. It's just ai all the way.
00:01:59:28 - 00:02:04:05
Stefan
You just. Yeah. You just got to keep them running. And so just make sure they don't get
unplugged.
00:02:04:07 - 00:02:11:17
Jens
AI.
Yeah, it will be matrix again. We will all be just plugged into the system to provide energy to the
00:02:11:20 - 00:02:12:29
(Mix)
Probably.
00:02:13:01 - 00:02:30:00
Stefan
I mean it's what we're going towards. But guys, thanks for joining us. We have a lot of topics
today. Today in our tech review today, it's kind of like a news channel if you think about it. We're
going to be talking about. Yeah, because we're just reporting on like the interesting stuff that
happened over the week.
00:02:30:00 - 00:02:46:17
Stefan
But there's some interesting ones actually on here. Jacob did a great job at picking this topic, so
we'll touch a little bit upon. Why we're bullish on gRPC as the next generation for GraphQL
Federation. This we didn't get to touch last week. So we'll start with that today. Second one I
actually read this study as well.
00:02:46:22 - 00:02:58:10
Stefan
But AI is actually slowing down our workflow. I just noticed Jacob's message. Drop your
questions, comments, or insults in the chat below.
00:02:58:13 - 00:02:59:08
(Mix)
Yeah.
00:02:59:11 - 00:03:03:00
Jens
Starting with insults. It's very important.
00:03:03:02 - 00:03:03:09
(Mix)
Though.
00:03:03:10 - 00:03:29:29
Stefan
I love that one. And then, yeah, I read this, in Hacker News, but it seems that developers are
slowed down by an average of 20%. Using tools like cursor or lovable or things like that. So
we'll touch on that. Speaking of lovable, eight months after their feed, from Crandall, my 15
million, they raise a 200 million series A, they're, at over 75 million ARR only 45 employees.
00:03:30:01 - 00:03:35:09
Stefan
And they're getting closer to that 2 billion valuation. I think they're 1.8. Right. Something like,
00:03:35:12 - 00:03:38:06
Jens
Did Cranham, invest.
00:03:38:08 - 00:03:42:04
Stefan
Cranham led their, seed, 15 million seed.
00:03:42:07 - 00:03:44:13
Jens
We know someone at Cranham.
00:03:44:15 - 00:04:05:01
Stefan
Yeah we do. We do new a couple people at random. And then the last one that we'll touch a
little bit upon, which I'm actually very surprised about, which is meta, may move away from open
source AI models. I don't understand this. I remember in 2003 they said that platform behemoth
will win because it's the open one, but now they seem that they're abandoning that opinion.
00:04:05:03 - 00:04:15:26
Stefan
I'm wondering why though. Is it because of China's deep seek? What's making it? Why are they
going back on their open source one And there's going to be a lot of stuff from you on this one.
So it'll be interesting.
00:04:15:28 - 00:04:20:24
Jens
Stefan, how do you call the the guy who who runs a news show?
00:04:20:26 - 00:04:22:13
Stefan
An anchor.
00:04:22:15 - 00:04:28:13
Jens
Are you an anchor now? Anchor. Right. Well, you know the film anchor man, I liked it.
00:04:28:15 - 00:04:29:26
Stefan
Who doesn't know the film?
00:04:29:26 - 00:04:32:24
(Mix)
Anchor man
00:04:32:27 - 00:04:41:24
Stefan
You use that quote all the time. The one with the perfume. What is it? It works. Every time, 60%
of the time or something.
00:04:41:26 - 00:04:43:09
Jens
Yeah. But,
00:04:43:12 - 00:04:54:10
Stefan
And then, what's it called when they get that big fight and Steve Carrol’s like, I kill the man with
the trident, and they're like, yeah, you need to, like, lay low. A couple of days like, that was pretty
crazy.
00:04:54:12 - 00:04:56:10
(Mix)
Do you remember that scene?
00:04:56:12 - 00:04:58:21
Jens
No, no, it was long ago.
00:04:58:24 - 00:05:11:11
Stefan
Okay. We'll have to rewatch it on the next retreat, but let's get back into the topic. So for today
on our news channel okay. Why are we bullish on gRPC as the next generation. It actually
comes. Great timing. Because of the LinkedIn.
00:05:11:11 - 00:05:12:24
(Mix)
That we saw.
00:05:12:27 - 00:05:37:09
Stefan
So, what Curtis posted on LinkedIn and gRPC is the federation, future. Let me bring up just the
blog post because I really like the image. But Jens, let's walk us through this like first of all, your
take on Federation, your take on connectors, which we talk about all the time. But why is gRPC
the future?
00:05:37:12 - 00:06:06:15
Jens
So for quite some time we, we more or less I wouldn't say exactly. We kept it a secret, but it's
more like, like we we we have developed a model of thinking in terms of how we think about
federation. And our our take is that I don't think we need more federation or I don't think we
necessarily need more directives or more complex directives.
00:06:06:18 - 00:06:34:27
Jens
I think what we, what we want to have for federation is actually less and less, especially less
complexity. And, one one of the big issues with Federation is you have many frameworks that
are not 100% type safe. And, and even if they are type safe, like go, then you can have
Federation directive that yeah.
00:06:34:27 - 00:07:02:25
Jens
Like requires or some other cases where it's not 100% accurate that you, you need, you would
need very strong guardrails to ensure that your subgraph implementation is actually correct. But
the majority of subgraph frameworks, they are like JavaScript, TypeScript, Ruby, whatever, they
are much, much less strict. And they, they suffer from this problem even more so.
00:07:02:28 - 00:07:24:25
Jens
That means you have like a subgraph, SDL. It follows the GraphQL Federation spec or Apollo
Federation spec, if you call it the spec. And the big problem is, whatever you do, there's very
little that that will that will enforce that the subgraph implementation is right. Like you can have
the subgraph schema and you have the implementation.
00:07:24:25 - 00:07:50:18
Jens
And if there's a difference between the two, or if the implementation is not accurately following
the the spec, then you you won't notice. And so we have quite a customer base and we know
from experience and from, from customer reports and requests what, what enterprises tell us,
it's a serious problem, especially at scale when there's money on the line.
00:07:50:21 - 00:08:18:03
Jens
Because you have to thoroughly review pull requests to ensure that's what you're shipping is is.
Right. So, we were thinking about this problem, and, what we were thinking about is this. So we
have our client, it speaks GraphQL to the router. And then you have the router. And as of Apollo
spec, it speaks GraphQL to the subgraphs.
00:08:18:06 - 00:08:47:04
Jens
If we could move this whole layer of GraphQL from the subgraph into the router, can we remove
this complete level of complexity? And that was kind of like the the idea we had with, gRPC
Federation. The idea is rather simple. You still write the subgraph SDL like before you define
entities and everything like normal, but then you don't implement a subgraph.
00:08:47:06 - 00:09:13:25
Jens
What you do is you take this file and we have a compiler, and we turn it into a gRPC spec. And
this gRPC spec, it will be generated alongside like a mapping file. And a log file. And we can
then tell Cosmo Router that we have a subgraph schema. But the subgraph is not speaking
GraphQL, it's speaking gRPC.
00:09:13:27 - 00:09:43:27
Jens
And then the, the router will handle, will handle the translation between GraphQL and gRPC.
And what that means is, on a high level, every language that supports gRPC, it can now be
used with this approach. And we made sure that, for example, problems like data loading, that
happen at the GraphQL layer, like for entities, we need to batch load multiple entities.
00:09:44:00 - 00:10:10:00
Jens
We take this problem and we move it into the router. And that means typically you would have to
somehow implement a data loader in your subgraph. With this approach we move the data
loader into the router. So nobody has to implement a data loader anymore. You you just
implement this, this, gRPC thing and then you are done.
00:10:10:03 - 00:10:31:01
Jens
And from our perspective, I think it's, it's the right direction because it achieves multiple things.
So I have a little checklist, which is why I'm looking to the, to the side. So one part is, oh, by the
way, before I go through my checklist, do you have questions?
00:10:31:04 - 00:10:36:23
Stefan
Me? No. One is this released? Can people start using it? Maybe that one.
00:10:36:27 - 00:10:59:08
Jens
It's it's live. Yes. It's live. It's it's in the docs yesterday on LinkedIn, I posted a video about how to
use it, and I gave this to Jacob to post it on YouTube. And, obviously it's not yet on YouTube
because Jacob is super slow, but it will be on YouTube very soon, right? Jacob?
00:10:59:11 - 00:11:06:05
Stefan
continue.
It'll be on YouTube pretty soon. So. Okay, cool. So this is live. People can start using and
00:11:06:08 - 00:11:35:03
Jens
Yeah. So the, the items like why why is this good. So the first part is end to end type safety. So
you have your, you have your, your subgraph SDL, and you compile it to protobuf. And this
protobuf, it will ensure and guarantee type safety. If you use TypeScript for example, we we will
use type checking for all the types.
00:11:35:05 - 00:12:01:26
Jens
With go you can check the interface implementation, everything. So we get much stricter type
safety compared to like there's frameworks that. Yeah, they, they are just not as type safe. And
also, another part, just a side note, just like, one thing we observe a lot in the, in the market is,
and we're actually a little bit confused about it.
00:12:01:28 - 00:12:32:27
Jens
A lot of our customers use code first subgraph frameworks. And, I really don't like this approach
because I think code first is not collaborative. Like, imagine frontend developer comes to you
and says, hey, I have certain requirements. Can you build an API for that? And instead of like
just writing a schema or a scaffolding, a schema for this use case, you now have to write code,
to then generate a schema.
00:12:33:04 - 00:12:57:27
Jens
I personally don't like this workflow, but it's it's another topic code first versus schema first.
Someday we can we can pick it up okay. So that's type safety. The second part is no more N
plus one problem. So what I said earlier with with the batching, normally it's a problem of
GraphQL service in general and with entities.
00:12:57:27 - 00:13:23:22
Jens
It's it's also a big problem. You send entity request to the subgraph and the subgraph has to
handle, to resolve them in batches. So that is something we we have solved because we moved
the sole batching problem to the, to the router. So we always send batched gRPC request to the
to the subgraph. The next part is so that we and by the way this this is not just like an
optimization.
00:13:23:22 - 00:13:46:02
Jens
It's also just less overhead. And we will come to why this is so important at the end. The next
part is performance boost. So one one very big issue with subgraphs and graphql is when you
have a GraphQL server, it needs to parse the text. Then it has an AST, it needs to validate the
AST.
00:13:46:05 - 00:14:10:28
Jens
It needs to execute the AST. This is a very complex operation. And, we can we can solve this
whole problem with, this gRPC approach because we pass the query, validate it, normalize it,
everything once in the router. And then we call your gRPC method methods theres no, no. Yeah.
Like no GraphQL parsing, no validation, nothing.
00:14:10:28 - 00:14:44:04
Jens
It's just calling gRPC method. So it's the overhead on the subgraph is much lower in the world
where you optimize the router, to every degree. I think one one big part that people have
forgotten about is how can we optimize subgraphs. And we had customers they spent
sometimes, like 50 milliseconds in the subgraph for parsing a query because like your elixir
framework or whatever, it's it's not super efficient in parsing a BigQuery with, gRPC, this
problem is gone.
00:14:44:04 - 00:15:15:24
Jens
Okay. Last but not least, the Apollo lock in. So one one big topic in the in the Federation
ecosystem is that even though you could say it's like open and everybody can do whatever they
want, the major subgraph frameworks, they are owned and maintained by Apollo. And, we don't
know what happens to Apollo in the in the future, and how they think about the business model
and everything.
00:15:15:28 - 00:15:41:03
Jens
And currently they have their, their, they kind of own most of the, of the subgraph frameworks.
And, also I would say there's like not that much innovation in making subgraph frameworks
better. Like, in general. And by yeah, by having gRPC between router and subgraph, we can
first of all, we can leverage the gRPC ecosystem.
00:15:41:03 - 00:16:24:29
Jens
And second, if we think there's a useful feature for our customers, we it and it's still vanilla
gRPC. So everybody can now benefit from this feature. So that's that. And then to to just sum it
up or. Yeah. But put like a, like a Tldr why why all of this. So if we have this strong contract and
it's a fast contract, there's a plugin system that allows your cosmo router to run like a gRPC
subgraph as a co-processor.
00:16:25:01 - 00:17:03:00
Jens
So that means if you have APIs, that are not federation, you somewhere need to have
something that translates between your REST API, your Soap API, your legacy weird http, API,
XML, like CORBA, whatever mainframe. So you need to have some code somewhere that does
this translation. And the our game plan is that in the future, we think you shouldn't be writing this
and you shouldn't be deploying this somewhere randomly.
00:17:03:02 - 00:17:44:20
Jens
But instead, we we think that we can build, the necessary tooling to take your subgraph
schema, compile it into your gRPC, take your open API spec curl requests, whatever you have,
and we will then leverage, LLMs to generate the adapter in the middle and run it as a co-
processor with, with cosmo browser, which means from a user experience, you can then say,
okay, here's my SDL, here's the service I want to connect and, WunderGraph, please generate
me the, the plugin and boom, integration done.
00:17:44:22 - 00:18:07:15
Jens
I don't need to think about subgraphs. I don't need to understand what entities are. I don't need
to write connect directives or something that might or might not fit my use case. I can just
express like, hey, here's an open API spec, bring me some fields into my graph. Boom! And
that's it. That's the, the the direction we're going.
00:18:07:15 - 00:18:16:22
Jens
we're doing this.
So in the long term, nobody should ever write boring integration code again. That's that's why
00:18:16:24 - 00:18:35:15
Stefan
And I think it's exciting. It's live now. We can definitely start to have see our customers using it.
We already have a couple using it, which is great from your point of view though. We talk a lot
about connectors and we talk a lot about Apollo, but this is a off topic. What do you think of the
new news of their new leadership?
00:18:35:17 - 00:18:52:00
Stefan
Assignment. So for those of you that don't know, Matt DeBergalis as the CTO is now the CEO.
Personally, I think it's a good idea. Yeah. What did you think? I know because you mentioned
Apollo and the ecosystem, so I wanted to bring it up.
00:18:52:02 - 00:19:22:19
Jens
Yeah. Like. If I'm honest, I always felt like Matt is the face of Apollo. I spoke with him, at least on
two occasions in person and often, at the conferences. He was kind of like leading the the the
conversation on the, on the stage and everything. And to me, it always felt like he he's actually
the, the leader from the outside.
00:19:22:19 - 00:19:49:12
Jens
I have never seen Geoff or what kind of function he, he had. So yeah without like I don't know
we, we also try to be you know, I read something somewhere someone said as a, as a CEO of
your startup, you should always try to be the, the CEO, where you want to be in in 18 months.
00:19:49:12 - 00:20:26:21
Jens
So today, be the CEO. That's you think your customers, your partners and everybody else
expects you to be in like, 18 months? And, yeah, I'm not sure if if 18 months future Jens should
roast, competitors. So in that sense, I think it's, it's the right move, to be honest. And at the
same time, it, it shows that not everything is going right behind the scenes because, like, the
must be going on something with the board and then other, things.
00:20:26:21 - 00:20:32:05
Jens
So. Yeah, that's that's my take.
00:20:32:07 - 00:20:44:18
Stefan
18 months Jens would be very proud of that take. No it's very nice, very political. And I think it's
right regarding gRPC plugins and what we're building. Any last minute topics you want to add to
that before we switch topics.
00:20:44:21 - 00:20:52:16
Jens
Yeah. Like you know, you don't always have to be 18 months in future Jens
00:20:52:18 - 00:20:56:23
Stefan
Okay. And I like that better it makes for better content.
00:20:56:25 - 00:21:07:26
Jens
Is it. Yeah. So, we we we sparked a little bit of conversation on, on Twitter. On Twitter. We're not
on Twitter for some reason on LinkedIn.
00:21:07:28 - 00:21:11:06
Stefan
You want me to bring it up?
00:21:11:08 - 00:21:44:22
Jens
Yeah. We can we can take a look because, someone from Uber wrote about the future of
Federation also has to say some things. And there was some conversation and I think it's it's it's
interesting. And we can also speak about what, what we think about this new, this upcoming
spec.
00:21:44:24 - 00:21:49:05
Jens
Are you bringing it up or are you fighting your computer? Mr..
00:21:49:07 - 00:21:56:14
Stefan
It's because every time I type, you always freak out about the typing. So I had to mute myself
while I typed so and so.
00:21:56:16 - 00:22:01:03
Jens
Maybe, maybe we could have Curtis as a as a podcast guest.
00:22:01:06 - 00:22:05:29
Stefan
Yeah. No, we definitely should. So. Okay, I found the post. Give me a second, guys.
00:22:06:01 - 00:22:11:05
Jens
David, we're not ignoring the chat. We're just ignoring you.
00:22:11:07 - 00:22:18:29
Stefan
Yeah, there's a big difference. Yes. My keyboard. Yeah. Which is funny because I actually got a
keyboard that's not supposed to.
00:22:18:29 - 00:22:20:25
Jens
Do you have a mechanical keyboard?
00:22:20:28 - 00:22:24:07
Stefan
No, I have the Logitech one. Like it's supposed to be quiet, which I like.
00:22:24:07 - 00:22:27:12
Jens
Like I have this guy here. Do you see that?
00:22:27:14 - 00:22:32:09
Stefan
Oh, you have the, the the the when, the apple one.
00:22:32:12 - 00:22:34:01
Jens
Yeah, the little one.
00:22:34:04 - 00:22:49:15
Stefan
Okay, so this is the post. Curtis is a senior staff engineer. Uber. He's been talking about
GraphQL federation, and he wrote a really great blog post. Jens. Do you want me to jump into
the blog post? So we can kind of skim it? Or do you want to just give us like a high level
overview? And then we'll get to the comment?
00:22:49:17 - 00:23:11:05
Jens
I mean, it's it's complimentary to, to, what we say. You can post it on the, on the chat if you want.
And there's one comment, from someone from the, from the, GraphQL working group. Where
was it again? Is it still the.
00:23:11:07 - 00:23:12:14
(Mix)
I don't see it anymore.
00:23:12:17 - 00:23:20:23
Jens
You clicked most relevant. Is there also another way most recent.
00:23:20:25 - 00:23:27:20
(Mix)
Oh. Wow. Was it removed?
00:23:27:22 - 00:23:29:27
Stefan
Can you check on your side?
00:23:30:00 - 00:23:37:24
Jens
Yes.
00:23:37:26 - 00:23:40:22
Jens
I can still see it.
00:23:40:24 - 00:23:47:07
Stefan
Maybe I'm blocked. Did he block me?
00:23:47:10 - 00:23:54:21
Jens
I send you the link. On slack. DM. That would be so funny.
00:23:54:23 - 00:24:00:04
(Mix)
But, Oh, the.
00:24:00:07 - 00:24:02:23
Stefan
No, I don't see it. I think I'm blocked.
00:24:02:25 - 00:24:10:28
(Mix)
Shit. Why? Why are you such a dick? I don't know, I guess he blocked.
00:24:10:28 - 00:24:42:12
Jens
interesting. Okay. All right. Share your screen. Can you share it in chat? Wow. It's, it's actually
not so important, but I think that the gist is that so there is a working group from the GraphQL
foundation, and it's, it's, on its way to create a new Federation spec and, or. Yeah, it wants to
create the Federation spec under the GraphQL Foundation.
00:24:42:12 - 00:25:26:17
Jens
And it, it I think it's it's really like from a technical perspective, I see a lot of very smart aspects.
Like there's like they really try to solve hard problems. And I think from a technical point of view,
I think it's, it's it's a good idea and it makes sense. What I want to say from another perspective
is, I remember like, I don't know, some months, a year or whatever ago, I remember how
various vendors, were on stage together and they had discussions and they were very loud
about like, how this is a collaborative effort and how, also Apollo is, is working with this, this
group and helping and everything.
00:25:26:20 - 00:25:55:00
Jens
But what I figured out recently is I looked into this, the spec working group, and if you go to the
GitHub page and if you check the the contributions, if you're honest, this spec is written by chili
cream, and primarily Michael Staib and Pascal. I forgot the last name, but Pascal, something
two guys from, I think, Switzerland.
00:25:55:03 - 00:26:28:26
Jens
They are primarily writing the spec, and there might be other people joining meetings, but it
appears to me that the major work is being done by chili cream. So I'm not exactly sure how this
is a super collaborative effort or like it appears that theres just like one company pushing
behind. And like I said earlier with, what we're doing with with gRPC, our personal take is that
I'm not sure if we now like, Reinvent Federation.
00:26:28:26 - 00:26:57:10
Jens
I'm not sure how that will absolutely transform. Like, the market. If you look at the Gartner hype
cycle, for example, you can see that, like, GraphQL federation. It's not like on the, on the
trajectory to the, to the moon or something. It's it's somewhere close to the, to the, what's it
called? The the trough of disillusionment.
00:26:57:12 - 00:27:02:24
Stefan
Well, it actually started from up here, and then it just moved slightly down, but it's still in the
trough of disillusionment.
00:27:02:27 - 00:27:18:13
Jens
Yeah. And like I said earlier, there's on the technical side, there's good ideas there. But just on,
on, like what do you say like on the, on the market impact side.
00:27:18:16 - 00:27:20:22
(Mix)
Is it really is.
00:27:20:22 - 00:27:53:00
Jens
It really the right thing to, to now like put all this work into or. I don't know, maybe the real
challenge is somewhere else. Maybe the, the real problems are that it's maybe too hard or the
wrong approach. Or maybe we need to think outside the box and I would, I would argue like
thinking outside the box is we just remove GraphQL because maybe also one of the problems of
federation is that it's called GraphQL federation.
00:27:53:07 - 00:28:16:05
Jens
Maybe it should just be called federation. And we're maybe we're too tied to federation. And
then I'm also wondering like is it I don't know, do you have to solve every problem with GraphQL
or maybe there's like other specs or other ways where where it could just make the problem
simpler. So yeah.
00:28:16:08 - 00:28:38:21
Stefan
Well Said I would like to say that I mean, the non-technical person always said that the big issue
with GraphQL Federation's you had to learn GraphQL. And then the big issue with GraphQL
was you had to use GraphQL. I think you're spot on. Like I don't get this. And I think also you
guys don't know Jens as long as I've known it, but there's an evolution that I've seen Jens go
through.
00:28:38:21 - 00:28:58:09
Stefan
I have also seen Dustin go through it, but Jens always says now he's like, don't get married to
the tech, don't get married to the tech. And I really think this composite working group, they're
married to the technology. Like you don't need to shove GraphQL down to finish every solution
or if for it to be even just the solution.
00:28:58:12 - 00:29:19:10
Stefan
It sometimes kind of feels to me like blockchain. Do you remember like blockchain was looking
for a problem and people were like, oh, we can solve finance, things with blockchain. And I was
like, can I just use a bank? Like, I feel like it solves the problem if everything's all good and if
somebody hacked my account, I can call the bank and tell them somebody hacks my blockchain
account, I can't tell anybody.
00:29:19:10 - 00:29:21:28
Stefan
And so I think you're spot on.
00:29:22:00 - 00:29:46:28
Jens
You know what you said? Don't be married to the tech. I would somehow generify this a little bit.
Don't be married to the solution. Like, be be married to the to the to the problem. To the to the
customer. And, yeah, maybe not married to the customer, but you know what? You know what I
mean?
00:29:47:01 - 00:30:19:15
Jens
Like, be obsessed about the problem, not be so much obsessed about the solution. And one
particular example for this is, like the what the post says on the, on the article from Curtis that
the GraphQL like there's a working group and for in the GraphQL over Http spec, they now want
to create like a new, a new batching API that allows you to, to batch GraphQL requests.
00:30:19:17 - 00:30:50:26
Jens
And the problem is that, by default, the the hack that Apollo is, is using to to make these entity
requests to load entities with this weird like any, underscore any syntax. Yeah. This hack it it
requires or it it's somehow like a hack to solve, batching. And if you want to remove that hack,
you have to somehow do batching in, in another way, in another layer.
00:30:50:29 - 00:31:19:22
Jens
And they are now looking at adding this to the GraphQL over HTTP spec. But then you have
multiple new problems. You first of all, you need to get that spec in. And like sometimes it can
take forever to get this spec signed off. And once you have that in, then you need to get all
frameworks, all subgraphs, all GraphQL service to adopt that new specification, which allows, it
will also have have some lag.
00:31:19:24 - 00:31:31:07
Jens
So, I don't know, like how about just we take the subgraph SDL, we compile it into proto, you
run gRPC, we're done.
00:31:31:09 - 00:31:53:15
Stefan
And that's it. That's it folks. One last note that I will say on this though, the whole thing about,
like the working group and having too many cooks in the kitchen, if you've ever heard of like the
Navy Seals, like they have very strict team sizes, there's two, four, six and a max team size of
eight. That's the max size that they can ever go on a mission is eight Navy Seals.
00:31:53:18 - 00:32:14:24
Stefan
I still think the same way in startups. If you really want to build something, for example, like this
federation spec, and you want to really get this down, you need a maximum of eight people.
When you have this whole governance board and this foundation behind it, I think it takes too
long. I really think that having so many people are too many cooks in the kitchen can be really
detrimental to even driving something forward.
00:32:14:26 - 00:32:17:00
Stefan
Anything else you want to add to that before we jump to the next.
00:32:17:00 - 00:32:44:12
Jens
Oh, I, I agree with this because, I think, like whenever we try to build something big and
something, something very hard, something new, I think it work best when just one single
person worked on it for three months and then said, I'm done. I think that was like the best
approach. We had a funny post from Nithin Be Married to the problem is this life advice.
00:32:44:14 - 00:32:47:20
Jens
This is how you choose.
