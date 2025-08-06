00:34:28:20 - 00:35:10:05
Jens
This is what's happening. Like we're we're talking to multiple, Faang companies now. We
already had contributions from people working at Faang sized companies. And even if they don't
buy our cloud service because like, you know, you you can't just sell something like a SaaS to,
to a Faang company like they are. They are a different breed and not always your, your ideal
customer, but they can use your, your, your open source and they can collaborate and they can
help you make it ready for scale.
00:35:10:05 - 00:35:55:24
Jens
They can add enterprise features, they can battle test it. One cool thing about Faang companies
is, they can put your component under a lot more stress than you could ever do just because
they have like real traffic of billions per day. Your typical user might not have that. So that's a
whole bunch of, of benefits. And ultimately we thought if we're in the market where we build a
core infrastructure component like engine X, the router and a big Faang comes around the
corner and suddenly creates like an open source alternative, well, what is it going to do to us?
00:35:55:24 - 00:36:26:27
Jens
And so yeah, for for us, it was very clear from the very beginning, we don't want anybody to
create an open source competitor to us because we, we don't want to to fight that and then split
the community and everything. So we, we just we just make it open source. And I have to tell
you, I really love one thing about open source because if you have a closed source code base,
you potentially have multiple repositories.
00:36:26:27 - 00:37:04:05
Jens
You have maybe some parts source available, some parts enterprise license. And so what you
what you do is you, you have to do all sorts of activities. You have to spend your time to
orchestrating these different repositories to merge some stuff into a private repo. Some stuff is
public. You have to deal with API keys and everything. And we as a company, we're spending
zero time on all of this because we have one single mono repo and everything is there.
00:37:04:05 - 00:37:35:17
Jens
And so our, our, all our time goes into into making it better, fixing bugs that we have created and
yeah, adding adding features. So, I don't know, it's, it's like open source allows you to be very
efficient. And also, sorry. Monologue again. Too long, I know, but, if, if, if you're open source, you
cannot you, you know, you don't fart in public, right?
00:37:35:17 - 00:37:58:25
Jens
Like, there's there's ways. Okay. I don't know about you. I'm no Jedi. Okay? You know, we, we
are civilized people, and you just have, like, somebody like you also, I don't know you. You don't
go in public, and then you you poop on the road or something like that. It's not like, no, we know
it's wrong.
00:37:58:27 - 00:38:27:00
Jens
And so the same thing in open source is you just don't commit garbage code and you don't
commit untested bullshit because everybody sees it like it's in public. So being open source, it
forces you to, to to think about some stuff, to think about security. Everybody can can see it. If
you build a proprietary source, God knows what's what's going on because we don't know the
code.
00:38:27:00 - 00:38:49:13
Jens
Is anybody auditing it? We don't know. If you have an open source repository. Pen testers can
test it. They can tell you about issues. They can, they can, disclose it in the, in the correct way.
So lots of benefits, I would say, where open source helps you to build better software.
00:38:49:15 - 00:39:07:23
Stefan
I mean, I would agree with all those points, some points that I have on that, the focus, like when
you start off as open source, you already protect yourself against, like you said, from a big
company going, you know what? No. Like we're going to just build our own. And it's backed by
meta. Like how do you compete against that?
00:39:07:23 - 00:39:27:09
Stefan
You really can't. And so open source is a way to just kind of get it out in the front that like, yeah,
we're open source and I like that. And then the second one is open source in procurement. Like
it's a hack. Like they run a a security audit on it. It goes through and then they start
implementing it into a dev environment and boom you're already there.
00:39:27:14 - 00:39:43:23
Stefan
If you were closed source one, you would have to solve a really big problem for them to. They
would have to go and ask procurement, hey, procurement, can you talk to Jens these guys from
one to to have a great solution. They would come talk to us. It would take a month for an NDA to
get signed, to set up an evaluation.
00:39:43:29 - 00:40:04:27
Stefan
And then you know what happens after a month, the developers on a new project, he forgot why
he was even looking at Wunder Graph. And so being open source also helps on the sales front.
And then my final point on open source and just building a company is that or back to the
infrastructure, is that infrastructure usage based works for small scale companies.
00:40:04:27 - 00:40:25:28
Stefan
When you have no users, it's fantastic. Oh, I just pay for the traffic that I use and I have no
traffic, so it's fantastic. My bill is zero. Oh it's amazing, but this is a trade secret if you want to
get with the enterprises. They are so against usage based. And the reason is, we can't say the
name, but me and Jens we're talking with a really cool guy from a really great company.
00:40:25:28 - 00:40:39:27
Stefan
Everybody knows this company. And, we were just curious. We're like, so, like, we we love this
company. We all use it. How much traffic do you guys do per day? He's like, I'm not sure, but he
said, what was it, 500 million per second?
00:40:39:29 - 00:40:42:01
Jens
And it was a lot.
00:40:42:03 - 00:41:07:19
Stefan
Some ridiculous number. So let's just say 500 million per second, 500 million requests per
second. Do the math on usage based. There's no way anybody in their right mind could use any
SaaS that charges per request. I mean, that bill would be absolutely astronomical. And so when
you're thinking about starting a startup and you want to build for the enterprises, keep in mind
usage based pricing.
00:41:07:19 - 00:41:25:27
Stefan
It works great in the beginning. But what they want at the end is predictability. And I think the
word that we were missing is exponential. You don't want your cost to rise exponentially. And I
love your example. Yeah, I have 100 employees. We have no traffic whatever. But over the year
we figure it out. We're doing crazy traffic, but we're still 100 employees.
00:41:26:00 - 00:41:41:28
Stefan
I don't mind paying up for 100 employees, but if my traffic went from 0 to 50 million requests
today, okay, my cost could have, you know, astronomically rise. But no, I think it was a great
point. I think it was a great transition into that. And we kind of jumped one thing. But I want to go
back to this.
00:41:42:03 - 00:42:03:00
Stefan
So we were talking about copying the competitors. There's something that a competitor
released rest connectors, another copycat competitors copying that. We're not copying that.
Why are we not copying risk connectors? What is your opinion on the rest connectors. And I can
bring up the diagram if you want as well, because I know you made a LinkedIn post on it, but I
want to go through it anyway.
00:42:03:02 - 00:42:33:16
Jens
So we we it's possible that we would have to somehow copy it if customers want it. So far they
don't want it, which we're lucky about it. Well, one thing about copying competitors is, if you
want to allow customers to migrate from a competitor to your solution, somehow there needs to
be some sort of compatibility.
00:42:33:18 - 00:42:49:23
Jens
And, for example, we created some compatibility feature flags, because, there's cases where,
Apollo router and gateway, they do very interesting things. For example.
00:42:49:25 - 00:42:51:24
Stefan
That's interesting. I like how you said.
00:42:51:24 - 00:43:18:08
Jens
Interesting, keeping it interesting. So, there's I, I don't know, they. Yeah. I mean, I'm not blaming
them. Okay. But sometimes you, you come up with quick solutions for problems and, you know,
like, well, one of the, one of the most persistent, solution is a quick solution because you
implement the customer uses it, then somehow you, you, you can never remove it because it
would break someone.
00:43:18:10 - 00:43:53:24
Jens
So there's just features in Apollo Gateway where it, it puts errors in weird places like not in
errors but in some other field. And sometimes they format things differently. And so we created
some feature flags so that we can accommodate for a customer to, to to easily, move over. But
if we look at connectors, so, you know, there's always this tension between what customers
want and somehow we try to push back if we think it's not a good idea.
00:43:53:24 - 00:44:25:00
Jens
But you cannot always push back all the way. So, I think we have prepared some screenshots. I
did a post like, a while ago, and that's just one thing I wanted to talk about this with connectors,
is, because, you know, we're we're our, our philosophy is not to, to to generally shit on
competitors like this is it's not our it's not our style.
00:44:25:02 - 00:45:00:12
Jens
We, we understand ourselves as engineers, and we just want to evaluate the technical solution
and look at the architecture and see it doesn't make sense or not. And, so Apollo did this demo
this week with, connectors. And, if you are, like, a GraphQL veteran like me you spot n plus one
problems from 100km away like it's you just see them immediately, like you look at something
and n plus one boom.
00:45:00:15 - 00:45:26:04
Jens
And here so we have this situation where, you know, we, we, we have one API call this plus one
where we load, products. And then we have n API calls where for each product we make a
second rest API call to fetch the price. And if you go to the next slide.
00:45:26:06 - 00:45:51:28
Jens
Here go to slide three first. So the slide four actually. Okay. The reason why you can so simply
spot this problem is so you see here that we have products and we attach this connect directive
and it returns a list of product. So this is the first hint. And now you go back to slide 3. We.
00:45:52:00 - 00:46:39:11
Jens
So you know we're getting a list of producst. And then here inside product you see that inside
the product type we now connect the price. And if you connect these dots you know we now
attach a single field resolver to an entity to to a type that's within a list. And the problem is very
simple like how can you avoid this is what you need to do is if you create like a list of things and
you want to attach something to the list, both resolvers need to be on top of the list, because
what you need to do is you need to fetch the list.
00:46:39:11 - 00:47:07:13
Jens
And then for the list you need to fetch the prices. But the problem here is you can see we make
a Post request and the product ID is a single ID. So this endpoint it can only give us pricing for,
for for one product. And and this is the problem and you know like in general my thoughts on
this connect thing is like yes.
00:47:07:20 - 00:47:38:00
Jens
Like it it's a quick fix. It can help in situations to quickly get the rest API into your, into your,
GraphQL federation thing. But like, I'm you Stefan. You know, how we built, how we build
cosmo. We our our thinking is never to to go fast or something. It's always to to think about
doing the right thing.
00:47:38:03 - 00:48:05:10
Jens
And I mean the, the, the biggest topic if you want to unshare, that's that's fine. But the biggest
topic in GraphQL or one of the big topics, you know, everybody's talking about persisted queries
and then everybody is making jokes about n plus one problems and I don't know why. Why do
we create a new solution that from the very beginning is not thinking about.
00:48:05:10 - 00:48:32:16
Jens
n plus one. And, and I think, you know, if you, if you, if you look at this, there's a high likelihood
that your Rest API doesn't have batching. That's no batch endpoint. And so for me, the big
question is, let's say you are like, like, high traffic site. Do you really want to make that?
00:48:32:16 - 00:48:57:18
Jens
Let's say you, you load 100 products. Do you want to make 101 API calls? Like, what's the
performance? If your router makes 101 API calls per single request to the router, it means
you're creating a lot of traffic in your infrastructure. Is this really the solution or should you think
about, okay, we have this Rest API.
00:48:57:20 - 00:49:26:19
Jens
Maybe on the Rest API we can add another endpoint. We can turn it into a subgraph. And this
subgraph will support batching so that we make two requests for this whole thing. And so like
the pitch of Apollo is you don't pay millions. By the way I don't buy this like this is it's ridiculous.
But they say save millions, save a year of work and you can solve this in two days.
00:49:26:25 - 00:49:58:17
Jens
But that's another thing. So you have this connector stuff. It's GraphQL, SDL how do you test it?
And I see it from Apollo in the demos. And by the way this is I'm not ranting against Apollo. I'm
ranting against bad engineering because what I see is so in the demo they create this thing and
then they save and then they open the playground and they click a button and then they see,
okay, now this thing works.
00:49:58:17 - 00:50:22:01
Jens
And yes, it works, but no developer ever wants to have a workflow where you write your SDL
and then you open the playground and then you test if it works like what a developer wants is
you write code, you check it into CI, you run tests, and then you can deploy that. So where are
the tests? Where's the test framework?
00:50:22:01 - 00:50:43:14
Jens
And I don't know but you need a data loader. You need batching. You need tests. You need
other things. At the end of the day, if you want to do this right, we need to write some code and
we need to have a repository. And yes, maybe it's not going to take two days, but adding this
one endpoint, maybe it takes a few more days, but then it's performant.
00:50:43:15 - 00:51:05:18
Jens
It's tested like what happens if the API changes. Yeah. You go to your SDL, you add the field,
you open your playground and then it works right. Like, okay, you check this in. There's no test.
Pull request is open. How do I verify that it works? Should I also run it locally and open my
playground and test how?
00:51:05:18 - 00:51:11:03
Jens
Like, I don't know. That's not that. That's not a I don't like it.
00:51:11:05 - 00:51:39:03
Stefan
But let's discuss a little bit. Two topics is one like like our relationship that we have with Apollo
engineering team. And then the second one is regarding how we do it. You said how do we do
engineering. And I think this backtracks to open source is if we were to do something like Rest
connectors, the process that we would do is we would open up an RFC and we would invite all
of our customers to contribute to it, because it's not a quick fix.
00:51:39:03 - 00:52:01:04
Stefan
We're getting in use cases, and people would bring up, hey, like this might introduce the n plus
one problem. Like, how were you guys thinking about that? Hey, how are you guys thinking
about if it's going to be performant and I don't understand or I do understand why, but I won't
say it. This is the benefit of open source is that you get to create these RFCs, and you get
collaboration from all these companies to help you think through the use cases.
00:52:01:06 - 00:52:20:29
Stefan
And so I like that. But I understand you said rant about engineering, but I think it's important to
clarify. We have a very good relationship with the engineering team. We talk with them, they talk
with us. We contribute together. In the GraphQL foundation. We go to the working group.
Everything is basically in very good terms, leadership.
00:52:20:29 - 00:52:40:01
Stefan
they might not like us. I kind of understand why, but that's okay. But it is important to know that
this rant isn't about them as a company. It's a rant against engineering. It's a rant that kind of
bothers us to our core because it should. Maybe it shouldn't be done that way. I don't know that
those are my thoughts on that, but Jens, we are almost out of time.
00:52:40:01 - 00:53:01:23
Stefan
So let me get a couple more of the topics that we wanted to discuss today. Because we have a
lot, but we've done the rest. Connectors, the Krueger Gartner hype cycle. I find it interesting, but
I would love to talk a little bit about startup ideas. How the heck do I generate a startup idea?
What do I do there?
00:53:01:25 - 00:53:14:09
Stefan
Like how did you come up with the idea of wundergraph? How how did how do I if I'm a young
entrepreneur and I want to start a company, how do I figure out startup ideas?
00:53:14:12 - 00:53:42:04
Jens
I think the most important bit is you need to you need to get in motion. So it's a bit like if you
want to get in shape, it's not so important that you do the right workout or that you have the best
gym, or that have you, that you have the best trainer, the most important thing is that you you
wake up and you go to the gym and you do something and do it on a regular basis.
00:53:42:04 - 00:54:10:18
Jens
Just, just repeat, wake up, and then and do it. And, you know, there was this guy, I'm not sure
where I have this from, but if you wake up and you you, learn about the problem that
exaggerated. Yeah. David. Oh, yes. You know, if you if you if you wake up in the morning and
the first thing you do is you make your bed, and then a really bad day happens.
00:54:10:20 - 00:54:39:26
Jens
At least you made your bed like, well, one thing and it's it's a bit the same with, with, how do you
find, success in building a startup? Wake up. Do your bed. So do something. And, figure out
where where the market is. And it's extremely likely, I would say almost like 99%. That's the first
thing you do.
00:54:39:28 - 00:55:10:12
Jens
It's wrong. It will not work. But maybe you learned how to talk to customers. Maybe you learned
how to network or something, and then you're starting to get in motion. And maybe you go to
network events, or maybe you have learned how to program. For example, in my first startup,
which wasn't a success, I learned how to program iOS apps, Android apps and backends and
websites and all this kind of stuff.
00:55:10:15 - 00:55:47:06
Jens
So at least I had, I had to take away and, the, the overnight success from from Wunder Graph, it
came from me having this idea of building, the SDK, WunderGraph SDK when I worked at, tyk
technologies before. I wonder if, tyk Technologies is an API management solution. So, they offer
an API gateway, and I always thought a bit correlated to my, to my rant on this, connector
solution.
00:55:47:08 - 00:56:08:27
Jens
I always thought it's it's kind of stupid that you have a gateway. This gateway is connected to a
dashboard. So if I want to configure something on the gateway, I go to the dashboard. I make
changes in the dashboard in the user interface. And then I click save. And then it pushes this
config to the to the gateway.
00:56:08:27 - 00:56:38:14
Jens
And I thought that's that's a very unnatural workflow for a developer. I would ideally I could just
write code to. Yeah. To configure what the gateway should do. And I commit this code and then
it deploys and I don't need a dashboard I don't want to click buttons. The cool thing is if you put
your config in code, you have a history, you know what changed, etc. and you can propose
changes, you can review it and in a pull request you can test it.
00:56:38:15 - 00:57:03:03
Jens
You know what I just said. So that was the idea of the gateway, of the Wonder Graph SDK. And
yeah, I thought it's right. But, you can do so many mistakes in bringing an idea to market. We
were not successful. I'm honestly, I don't like. It's possible that if you started now, it would work.
00:57:03:03 - 00:57:09:19
Jens
Or maybe if you started it five years ago, it. Whatever. On our timeline, it didn't work.
00:57:09:19 - 00:57:11:22
Stefan
Didn't work.
00:57:11:24 - 00:57:40:07
Jens
But what it allows, allowed us to do is. So we built a GraphQL gateway. Not exactly. For
Federation, but a GraphQL gateway. And we made it open source. And so what happened is a
bunch of people came to us and said words about GraphQL federation. And they were
somehow upset with license changes from Apollo. But we were on our path.
00:57:40:07 - 00:57:58:25
Jens
We were we were not listening so well. We were on our path to the SDK, world. And the SDK
world shouldn't happen. And so there was like a pivotal moment in, in the summer two years
ago.
00:57:58:27 - 00:58:01:14
Stefan
June or July of 2023.
00:58:01:16 - 00:58:27:19
Jens
Yes. There was like a pivotal moment where the team was on a retreat. We sat together, we
figured out we're dead. We're running out of money, and we need to change. We need to pivot
and step back and, yeah. Do you remember? Yeah. Like Stefan opened. Like we will, you know,
we that we had, like a, like a big house.
00:58:27:19 - 00:58:47:14
Jens
Everybody was sitting somewhere. The mood was really bad. And Stefan had his notebook and
we were like, okay, Stefan, go through the, notes with customer calls. Before grain. Let's try to
find the last straw. Right? Yeah. So was cool. You can talk a bit about that situation.
00:58:47:16 - 00:59:04:02
Stefan
Yeah. So currently we use like grain and like circle back to record our customer calls. But before
then before like AI was able to transcribe it we use I use the red notebook I had a red notebook
and every customer call I would talk to the customer with the Jens and I would write down and
yeah, just sense, like we're sitting down.
00:59:04:03 - 00:59:27:18
Stefan
We're like, we're we're just throwing ideas out there. We're like, it's not going to work like
Cosmos Cloud won't work. We would have to get this many users. It's impossible. And, I'm
sitting there and we're going through my notebook and I have a red. The the book is red, and,
everything's written in black ink. And I took a highlighter, and I'm just going through the pages,
and I we did a lot of customer calls, though, in 2023, like before we even launched Cosmo.
00:59:27:20 - 00:59:47:07
Stefan
And I just kept noticing was federation. Federation. And so I'm going through the book and I'm
highlighting federation. I'm like, Jens, I think this is it. Look, they're all talking about federation.
And the three key pain points are I can't self-host my router. It's not open source. And there was
another reason. And yeah, I mean, it was crazy.
00:59:47:07 - 01:00:11:22
Stefan
It was crazy that all these people were telling us what they want. And it was popping up on
every single page. And Jens, explain a little bit, because I think the story is so cool, because
when we came to the retreat, it was great. The mood during the retreat wasn't the best because
we kind of realized we were dying, but when we left, we were like, okay, now I know what to do
and you can explain a little bit because we figured out what we needed to do.
01:00:11:24 - 01:00:14:12
Jens
Well.
01:00:14:14 - 01:00:20:05
Stefan
And David has his thoughts as well about what we were trying to sell.
01:00:20:07 - 01:00:21:21
Jens
Yeah, I think.
01:00:21:23 - 01:00:30:19
Stefan
Wait, one thing, one thing here. Who puts relish on a burger? That's a really weird thing to put
on a burger, David, I'm not a relish guy.
01:00:30:21 - 01:00:35:05
Jens
Continue. Yeah. Like,
01:00:35:07 - 01:00:36:04
Stefan
It's.
01:00:36:07 - 01:01:01:16
Jens
I, I so for me, I remember I had a bit of a hard time of letting go of the SDK. You know, I still
remember the first one two months. Like on the retreat. I was not fully convinced it for me, it was
more like, okay, that's that's our last opportunity. I know we have to do it. I don't like it.
01:01:01:18 - 01:01:29:00
Jens
And I remember for the next two months or so, I, I was really struggling because my, you know,
you're the technical founder, you you had the idea, you raised money. You wanted to prove to
your investor that you're right. And you have to admit that you're not right and you have to admit
to the team. That's the path you you have taken.
01:01:29:03 - 01:02:00:21
Jens
You know, you're you're the leader. You said, we go this way, and now you have to admit it was
a mistake. But I think in the, in the, in the, in the life of a leader, it's important to, to somehow
simply be realistic and say like, hey, what what we're doing, we're, we're, we're building cool
tech, but we're not really targeting a market where, where we can turn this into, into, into a
working company.
01:02:00:21 - 01:02:28:22
Jens
So it was a bit of a of a struggle for me. But the good thing is, yes, we are four co-founders.
Okay. And, one of our co-founders, Dustin, he's a little bit different. Like, you know, everybody's
different. And it's it's it's good to have like, diversity in the founder team. And I'm, in retrospect, I
really appreciate it.
01:02:28:22 - 01:02:55:07
Jens
Like, you know, Stefan, you and me, we have we have different skills. Bjorn, bring something to
the table. But Dustin, he's like, he's for one. He's like an engineer at heart. And also, he's an
amazing team player. So if everything falls apart, he somehow he or he can focus and he wants
to make it work. And he's he's like, I don't know he's carrying you.
01:02:55:07 - 01:03:21:19
Jens
You know, when when it's raining, when everything sucks, he, he keeps going. And the craziest
thing that's happened is like, you know, I was still in my in my shit. My idea sucks depression.
And two weeks after the retreat there was like a post from Dustin like, hey guys, I have prepared
the repository, and he was like, oh yeah, it's it's called Cosmo.
01:03:21:19 - 01:03:52:20
Jens
We're now building Cosmo. And I'm like, what's going on here? Like, the the name is weirdly,
you know, in the beginning I thought the name was stupid. I thought we should name it cosmos.
But somehow, Dustin, you know, Dustin being Dustin, he's like, yeah, let's call it Cosmo.
Whatever. And then we had this new thing and then, Nithin and Suvij, our devs from from India,
you know, they are they, full stack killer machines.
01:03:52:23 - 01:04:24:28
Jens
They jump right into this thing and and help Dustin, build it up. David was there. He was like,
okay, we don't have anything else to do. Let me figure out composition. And, Sergei, my my long
time, friend from from tyk, it was clear that, he and me, together, we would form the, the
backend team, we would start building, the router and all this kind of stuff, and.
01:04:24:28 - 01:04:47:10
Jens
Yeah, this is, I don't know, like a magic moment. It was an interesting time. And then just a few
weeks, months, I don't know, later, we got our. I think our first customer was, Soundtrack Your
brand. Right.
01:04:47:13 - 01:04:49:07
Stefan
Travel pass first and then soundtrack.
01:04:49:09 - 01:05:27:10
Jens
Okay. Travel pass and soundtrack your brand and soundtrack your brand. They had, they had,
like, a really complex graph. But the thing is, you know, sometimes you need to be extremely,
extremely lucky to, like. Yeah, you cannot imagine how lucky we are that that Cosmo actually
exists because, so there's there's, Yeah. I think it's fine to talk about this because, there was a
situation where we, you know, we we kind of didn't know how to move forward.
01:05:27:12 - 01:05:49:00
Jens
And there was a really cool guy. You know, him from the GraphQL community. Uri Goldstein,
he's, very active, with, with the guild. And he introduced us to Walmart because, Walmart was
looking for, for a GraphQL solution. This is like years ago and. NDA, has.
01:05:49:00 - 01:05:51:06
Stefan
Expired. No, I'm just kidding. You're good to talk about it.
01:05:51:07 - 01:06:03:01
Jens
I'm not talking about NDA stuff, but the one thing where we were so lucky is Uri introduced us,
by the way. You're you're you're responsible for this. At least partially. Okay.
01:06:03:05 - 01:06:07:00
Stefan
So he's a good guy. He's very good and collaborative. I really appreciate Uri for that.
01:06:07:00 - 01:06:41:22
Jens
Yeah. So he introduced us to Walmart and, Walmart wouldn't become a customer because, like,
we just started with cosmo. Like it. It wasn't ready, but they were extremely friendly to us. They
were so nice. And they, gave us under NDA. They gave us their GraphQL schemas. So we had
the subgraph schemas of Walmart, and they gave us some queries and they told us, guys, you
are cool, but the queries don't plan like we will not work with you, but something nice.
01:06:41:28 - 01:07:08:22
Jens
We give you the stuff and maybe it helps you. And to be honest, this was such a lucky moment
because with this, with these schemas and the queries, we were able to to kind of figure out
how Federation works and then how the Query planner should work to the degree that we
could. Then a couple months later, we could onboard, soundtrack your brand.
01:07:08:24 - 01:07:32:05
Jens
They also had a very complicated graph. And I still remember, like, it took us 2 or 3 months to
actually make it work. And they were such amazing people because from the very beginning,
they knew that we have a lot of homework to do, but they they trusted us, and we built a
fantastic relationship with, Frederik and Sven.
01:07:32:07 - 01:07:56:26
Jens
In the meantime, we have actually visited them and, in, in, Sweden, we ate meatballs with them.
Like, it's really, really cool, guys. We met them in the office, and. Yeah, like, if you look back, it's
just amazing to see that, like the the the reason why wundergraph and Cosmo today is what it
is.
01:07:56:28 - 01:08:04:18
Jens
It's really like, I don't know, you. You cannot plan this. It just happens.
01:08:04:20 - 01:08:20:22
Stefan
It's kind of like life. I always tell all my friends, build the startup. When you're young and in your
20s, you go from 22 to 27, in a blink of an eye. So it's going to go quick. So if you can take the
risk, do it. If you can take the risk any time in your life to build a startup, I think you absolutely
should.
01:08:20:22 - 01:08:28:28
Stefan
And I mean, there's so much to talk about. But Jens what what's the good thing?
01:08:29:01 - 01:08:30:06
Jens
The good thing.
01:08:30:09 - 01:08:35:07
Stefan
Yeah, the good thing is we're back next week. But who's going to join you next week? Do you
know yet.
01:08:35:10 - 01:08:36:26
Jens
Who's gonna join me next week?
01:08:36:28 - 01:08:38:10
Stefan
Yeah, I'm getting married. I won't be here.
01:08:38:11 - 01:08:58:10
Jens
Oh, you're not here. What do we do? We'll figure it out. Good. Who will be this? This person
moderating and with the good looks. And so I'm here for the for the good input and and
everything. You're here for the looks. But how do we replace you?
01:08:58:12 - 01:09:15:04
Stefan
We'll figure it out, guys. Comment below or on any of the post of who you would like to meet
from the team. Take a look at our LinkedIn. Maybe Bjorn our SEO. We can bring somebody on
for the show, or we might just skip next week, but we'll keep you guys updated. So the good
thing is then it's not that we might be back next week, but also I'm getting married, so that's a
good thing.
01:09:15:11 - 01:09:25:00
Stefan
Thank you guys again so much for joining us Jens always a pleasure. See you guys. Ciao.
01:09:25:02 - 01:09:27:19
Stefan
It's funny it it wasn't letting me end the stream by guys.