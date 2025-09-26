00:33:35:08 - 00:34:07:21
type: podcast-chunk
Kevin
Of course, looking at, you know, are their needs going to grow and expand? And what does that
look like to a lot of open source projects? Have vendors associated with them as well. You
know, so they have they have hosted products. They have, customer managed products, all
sorts of things. What a lot of folks are kind of leaning towards now, especially with kind of cloud
deployments, is, there's a bit more comfort with having like a centralized control plane that that's
hosted as a SaaS.
00:34:07:24 - 00:34:27:12
Kevin
And then a distributed data plane that, that they host themselves. So having all the gateway
runtimes running their own infrastructure essentially, but then doing management of all of those
gateways through a centralized place. So, you know, they log into the SaaS and they can set
permissions and sort of RBAC stuff for, for other folks logging in there.
00:34:27:19 - 00:34:52:21
Kevin
And then manage who has sort of control over that. And then there are, you know, folks who are
looking for things like, a cleaner sort of git ops, approach to it. Right. And so, there are vendors
like, like Zuplo that, serve a particular section of the market really well, and have a decent kind
of git ops flow to them.
00:34:52:21 - 00:35:12:19
Kevin
So, I mean, it really it really depends. I would say there are probably, there are probably more
vendors that I've recommended, depending on the specific use cases and the needs of the
customer. There's, there's more that I've recommended than I've said stay away from, you know.
00:35:12:21 - 00:35:19:14
Stefan
That one’s curious, but I'm not going to ask you that one. I’ll ask you offline.
00:35:19:16 - 00:35:50:04
Stefan
That's awesome. But, let's kind of acknowledge, some of the topics that we had planned, which
is, again, Jens this all the time, I think you also say, and I also wholeheartedly agree on this, it's
APIs all the way down. APIs quietly power everything. And one of the things I realized, the
space that we're in, I was once I had a bachelor party, and in the hotel there was an Hvac and
plumbing convention, and there was people going crazy about the type of, like, angles on the
plumbing, the type of material used in the pipes and everything.
00:35:50:06 - 00:36:04:18
Stefan
And I kind of realized, like the API space is the plumbing space, like we're the weird people that
get excited about what type of piping we use, how we connect different systems together. So I'm
like looking at this conference and I'm walking around and I'm looking at all these booths and
everything, and I'm like, oh, this is true.
00:36:04:18 - 00:36:21:20
Stefan
If you think about it. Like every physical building in the world has plumbing, every digital system
in the world has plumbing. And so one of the things we all agree on, I think, Kevin, I'd love your
take on this is I mean, APIs, power, everything. It's APIs all the way down. Would you agree with
that? What's your take on that.
00:36:21:22 - 00:36:40:24
Kevin
Yeah. So first off, let me just get this straight. You're at a bachelor party. And instead of spending
time at the bachelor party, you decide to go to an HVAC and plumbing convention that happens
to be in the same venue and think about APIs. That's that's it sounds like a pretty wild bachelor
party.
00:36:40:26 - 00:36:41:21
Jens
If I'm.
00:36:41:21 - 00:36:55:01
Stefan
Honest, though, I was at the bar, I saw all these people. They were getting super excited. So I
got a couple of drinks into me and I went into the conference and it was a little bit more fun like
that. But yes, yes, you got that right, I did okay. APIs are always on the top of my mind.
00:36:55:04 - 00:37:20:28
Kevin
No. It sounds like something that would happen to me too, but like at then suddenly I was
looking at, you know, plumbing, like, how did how did that happen? But, yeah, I mean, I think
it's, it's, you know, I as much as we've tried to, steer away from, from APIs and I think even in
the GraphQL space, it was almost like, oh, you know, to hell with APIs.
00:37:21:01 - 00:37:40:22
Kevin
I'm going to go use GraphQL. And I think for a lot of the those people, it took a while to realize,
like, oh, this is still an API. Like, I still I still have to worry about the network. I still have to, you
know, maybe the tools are really great for me. Client side. But there's still, like, a whole network
here that I've got to think about, right?
00:37:40:24 - 00:38:10:12
Kevin
So, yeah, we just we can't escape it. Right? Like, client server is a really good model. And to do
client server, there are a few different patterns. But they all end up looking like APIs. No matter
how you slice it. So, so, yeah, I think, you know, when we, we look at kind of AI and, MCP now
there are like a group of people who are saying like, oh, I don't need my API anymore.
00:38:10:12 - 00:38:41:02
Kevin
I can just make an MCP server. But then, you know, what happens is you want to centralize this
functionality somewhere. You want to provide this functionality to multiple consumers. You know,
you've got natural seams. Where you need to scale separately. And so you're looking at, you
know, having a distributed model of some sort. And when you have a distributed model and it's
going over the network, suddenly you're building an API that your MCP server is a consumer of.
00:38:41:04 - 00:39:02:25
Kevin
Right? And it's just, every time we say, like we're trying to, to get out of doing APIs, we end up
just creating more APIs. And, and so, like, you know, I don't I don't think that's, that's going
away. And I think, you know, some people are, I think they're experiencing the pain of having so
many APIs.
00:39:03:01 - 00:39:30:23
Kevin
And so they're like, no more APIs, you know, like, let's just stop. Stop doing it. I don't think they
can right. I think, like, APIs are here to stay. They're going to keep proliferating. And so doing a
better job managing that proliferation, is, you know, is probably the way to go there. But yeah, I
think, you know, as AI, we're we're never going to get rid of APIs because we live in a connected
world.
00:39:30:26 - 00:39:47:00
Kevin
And we, we have our systems living in the cloud now, and, you know, we have, distributed
network of applications that we need to talk to. So it's always going to be APIs.
00:39:47:03 - 00:39:58:10
Jens
You mentioned 1 point. and it it gave me like a curveball. But so you're the creator of siren. We
both know that, Stefan doesn't know what siren is.
00:39:58:13 - 00:40:03:03
Stefan
Yeah, yeah. Well, we're the audience for the audience. Give a give the audience. 30 second
elevator pitch.
00:40:03:03 - 00:40:35:02
Jens
Yeah. You can do that, Kevin. But I kind of thought when when LLMS became more powerful
and when everybody started talking about MCP, I was immediately reminded by, I thought
hypermedia would have been the the right approach to let an and an agent talk to an API. And
then the API tells you what other things you could do and then interact.
00:40:35:02 - 00:40:44:13
Jens
And I thought that's that's the hypermedia moment. And it didn't come like, well, what do you
think about it? And then what is siren again for everybody.
00:40:44:15 - 00:41:14:11
Kevin
So so siren is a hypermedia type. What hypermedia means is, you know, having, basically links
and forms in your API response, so, you know, what you can travel to next, and you know, the
actions that you can take, it's defined, in the response itself, much like HTML, which is a
hypermedia type. So, you know, HTML, you can get links that you can go to the next page, you
can get forms that you can submit.
00:41:14:13 - 00:41:36:05
Kevin
When you talk about a hypermedia API, it's just really presenting that in a way that's, you know,
more easily consumable by a machine. So, you know, when you think of things that are very
dynamic coming from the server side, you know, like, you know, I might not statically know
which entities are related to this entity.
00:41:36:08 - 00:42:13:17
Kevin
Until I do the call at runtime, that's very much where, LLM interactions are today. And I think we
are actually seeing, like, some hypermedia elements, pop into the scene. We probably won't call
it hypermedia anymore. But, you know, the patterns, like we're coming back around to them.
Yeah. With, with MCP, there's this whole MCP, UI, track that's going on right now where they're
talking about how to have like, a tool response come back that essentially has forms in it.
00:42:13:19 - 00:42:33:18
Kevin
So you know what to do next. There's like something called elicitation where you get input from
the user. So like we're we're coming back around to a hypermedia whether we know it or not.
And that's fine. We can take whatever name we want. I've stopped fighting the name thing a
long time ago. You want to call anything?
00:42:33:18 - 00:42:37:20
Kevin
REST. Call it REST. Have fun. Go for it.
00:42:37:23 - 00:43:02:21
Jens
Yeah. No. Like it? It makes sense. And and, Well, one thing I'm curious about, maybe have an
opinion on that, but Will and I think it's actually happening because if you search in Google now
you have the, the I summary and the changes user behavior. That's already proven like there's
statistics that people stop clicking on links.
00:43:02:21 - 00:43:34:06
Jens
And and I have I personally have a feeling that user behavior will change in the sense that we
we open ChatGPT, we ask a question, and maybe it serves the web and does something and
presents us something. And, you now can add your MCP service to, to the chat as well. And, I, I
have a feeling that it's possible that the internet, or at least the internet behavior, it somehow
changes that we're no longer, you know, in the, in the, in the beginning.
00:43:34:06 - 00:43:46:01
Jens
And then you're longer in tech than me, but in the, in the in the early days you had these
registries or what's, what was it called like that were sites that had links like what was the name
directories or something.
00:43:46:04 - 00:43:48:13
Kevin
That link aggregators generic.
00:43:48:13 - 00:44:08:06
Jens
Yeah. So you went to like a page and it has links and everything and you clicked on the links
and then came came Google. Okay. You can search. It takes you to the, to the next pages. And
maybe the next iteration is we're, we're abandoning that as well. And we're just asking
questions. And then we, we we just get the information back.
00:44:08:12 - 00:44:34:24
Jens
But at the same time, it also feels a bit like the, the, the web becomes like a walled garden
again, because we're we're not exploring the web ourselves. We hand this over to a machine
and then ChatGPT decides for us what is relevant or not, what should we say? And then, I don't
know, a lot of people trust what comes back from an LLM which can also be, a mistake.
00:44:34:24 - 00:44:47:20
Jens
And. Yeah. How do you think about LLMs? ChatGPT, Claude, all these things. How do you think
about changing user behavior and then how it affects the the internet?
00:44:47:22 - 00:45:09:12
Stefan
Real quick before you answer that one, Kevin, I just want to add my mom, my dad, my dad, who
came from, Yugoslavia, who doesn't know anything about technology. He uses ChatGPT my my
wife, like they've stopped googling. They just ask ChatGPT and they assume it's correct. It's it's
blown my mind. And my dad, I asked him a question is like, I don't know, let me ChatGPT it.
00:45:09:15 - 00:45:19:00
Stefan
This man thought Amazon was a hoax. So like it is absolutely changing user behavior. But I
would love to hear your opinion on that.
00:45:19:03 - 00:45:45:23
Kevin
Yeah, I mean for sure it is, right? Like, ChatGPT is like one of the biggest consumer products to
ever launch period. Right. And you know, what is interesting to me is that, the experience almost
reminds me of the early web, where things were very information based. The idea was we're
sharing information with each other.
00:45:45:23 - 00:46:11:18
Kevin
Right. So you have a very plain looking site. Essentially, you're just getting the text. Right. And
that's what's happening with with an LLM. You ask it a question and text, you get a response
back in text. At some point, like we decided, okay, we've got this, this whole presentation layer
that, you know, we're providing folks, how can we improve that experience.
00:46:11:18 - 00:46:46:02
Kevin
And so, you get into all sorts of, you know, cool web design things sometimes kooky web design
things, and you're presenting them with an experience, not just text. Right. And, and we've gone
really, really far with that. You know, some websites look incredible. You can have an incredible
experience on that website. When we talk about, like, LLMS kind of scraping those websites
and providing data, we're losing the entire experience of the web that someone has crafted for
us.
00:46:46:05 - 00:47:23:01
Kevin
And it's it's a trade off that we're making. Right. So I think it makes information incredibly
accessible. You know, we could say that Wikipedia made knowledge and information incredibly
accessible. But to to make it more of a personalized thing. Right? Like the the chat bot can learn
my style over time. It can know when, you know, it needs to ask me to, to go deeper on a
question like it can it could be a very personalized experience for me.
00:47:23:06 - 00:47:54:23
Kevin
I think that is is really going to change a lot of things. Where essentially, you know, you want to
own the experience instead of giving that experience to someone else to present to you. You
want to own the experience yourself. I think there are pros and cons either way. You know, I
think, I've personally enjoyed, the experience of surfing the web and seeing what other people
have created, and the different creative ways they want to present information to me.
00:47:54:26 - 00:48:16:28
Kevin
You know, I don't think it'll it'll it certainly won't go away. That will always be there. Like the the
web's not going to go away. It's just it's too vast. It's too big. You know, it will. Will a lot change
about it, I think. So, you know, ad revenue, right? Like, ad revenue became a huge thing.
00:48:17:01 - 00:48:38:00
Kevin
What happens to ad revenue in a ChatGPT world? You know, and for the folks who went too far,
who were showing me five different ads when I'm trying to review an article, you better believe
I'd rather go to ChatGPT than get spammed with, you know, five different windows. I need to
close in order to read an article.
00:48:38:03 - 00:49:08:15
Kevin
Right. So I think it's it's going to help drive better practices there that care more about the user
experience. But yeah, it's, it's it's interesting like the, the value that folks are getting from
interacting directly with their users, directly with their consumers. That's, that's shifting. And
there's now a third party in the mix. And everyone's kind of beholden to that third party.
00:49:08:15 - 00:49:30:27
Kevin
What information are they going to share with me? You know, what information can I, present
through them back to the user, if anything at all? So I think that there's a lot that we're going to
need to think about moving forward. I know a lot of people are like, I just want all chat bot, all
chat interface, all natural language experience all the time.
00:49:30:29 - 00:49:51:19
Kevin
Because I think they're really excited about it and because I think they're, they're sick of getting
spammed with a bunch of ads. But, you know, we we lose some stuff there too. So I think, you
know, over time, we'll, we'll start to figure out what this really looks like for us. But certainly
there's a shift, there's a change, and we're all going to have to adapt.
00:49:51:21 - 00:50:17:18
Jens
It's it's also quite likely that at some point, if we, if we look at what, like Netflix and others did, at
some point maybe we will just see ads in ChatGPT. I was going to. Yeah. And then you can
have like the premium version that might not have ads and it's the bit faster and the, the cheap
or free version that it shows you an ad before it gives you your, your text.
00:50:17:18 - 00:50:46:27
Jens
Right. But, on another side, I think what's, what's also cool about, about, the coming back to the,
the chat is the interface in just text. I think it has also also positive effects on accessibility. Like
everybody who had issues using, the, the web in its animated visual form, they, they can now
ask, chatgpt and they can consume it as text or they can they can listen to it.
00:50:47:00 - 00:51:17:04
Jens
So I think that's also like, like that side. So that's that's also a thing. One other question I have is
if you think about, you know, we, we were speaking earlier about, like you're consulting to, to
enterprises. And I'm curious in this, in this, ChatGPT AI world or LLM world, where in reality,
because there's a lot of hype and people who build cool stuff and talk about cool stuff.
00:51:17:04 - 00:51:33:19
Jens
But if you come from an enterprise angle, where do you see, like, real market pull for LLM
tooling? Like, what are the things that enterprises are actually buying and they don't churn? Like
what what is the stuff that sticks?
00:51:33:21 - 00:51:34:11
Stefan
Good question.
00:51:34:11 - 00:52:01:24
Kevin
And in terms of like LLM stuff, I mean, yeah, but most folks are, just trying to figure out ChatGPT
and their technical teams are starting to investigate things like cursor, or more more commonly,
depending on the type of company is, it'll be them getting started with, like, a GitHub copilot,
right. Because they're they're using VSCode already.
00:52:01:26 - 00:52:29:11
Kevin
I do I do see people quickly going from copilot to, to cursor, to, to windsurf to like investigating
cursor and windsurf as soon as they get familiar with copilot. So I, I think it's mostly in kind of
like the technology team adopting this stuff now, and business folks starting to say how do I how
do I get a ChatGPT like experience for the things that I'm asking for?
00:52:29:18 - 00:53:00:21
Kevin
So I think it's very, very early days for, you know, more digital native, I guess companies,
companies who weren't around before the web. Right. Like you've got companies that are like,
300 years old who've been around for a long time, that companies who are 20 years old or 15
years old. For those those newer companies, they are much quicker to adopt, AI and and, and
MCP that I'm working with now.
00:53:00:21 - 00:53:35:22
Kevin
Right. Like they're super early adopters for, for MCP, they're creating MCP servers. They're,
figuring out how to, have authorization controls. And as the safest way possible to present it to
their business users. Like, they're kind of ahead of the curve. And then there are certainly folks
who have been doing, ML for a really long time, you know, prior to the LLM boom, even even
big, like, insurance companies and things like that, mortgage companies.
00:53:35:22 - 00:53:56:24
Kevin
Right. Like, they're, they have tons of data, that, that they can use for various reasons. And
they've been looking into this for, for a while. So I think, there are certainly new technologies in
that space that are very interesting to them, that they can leverage. But I, I would say, like, there
isn't really good in enterprises right now anyway.
00:53:56:26 - 00:54:27:09
Kevin
There isn't really good like deep penetration of AI into those enterprises, smaller companies.
Right. They'll have they'll have like, you know, AI mandates where like, you've got to be using AI
in your job. Some, some larger companies are starting to hire like chief AI officers, to, to kind of
oversee this. And not just on the technology side either, but like on the business side too.
00:54:27:11 - 00:54:44:14
Kevin
And like, they're really just getting started. So all this stuff is, is brand new. I think it will be in a
much different place in five years, on on the enterprise side, I think on sort of the cutting edge
side, we're in a new place every three months. So.
00:54:44:16 - 00:54:57:28
Stefan
Well, so very well. So and Jens, by the way, to your point about the ads thing, I was thinking that
exactly when Kevin was saying I was like, wait till you're here on ChatGPT. And it's like, well,
this is loading. Please take a look at an ad from our sponsor. And I'm like, oh my God, when is
that?
00:54:57:28 - 00:54:58:19
Stefan
They're going to come.
00:54:58:19 - 00:55:26:03
Kevin
Yeah, but the difficult part of that is like attribution, right? Like you don't even know where the
data came from at that point. And so like there's no money filtering back to the source. It's just
OpenAI taking your money at that. At that point. Right. And so that that creates a whole other
issue there of do I try to block the, the scrapers that are coming to my site like Cloudflare is
looking at, at some of this as well?
00:55:26:05 - 00:55:50:06
Kevin
Do I charge, do I try to charge OpenAI for, for coming to take my data? Right. It's a there are a
lot of things we still need to figure out. There's certainly a lot of ethical things we still need to
figure out with AI and biases. So yeah, I think I think it's going to be, it's going to be a really long
decade of, of really trying to get our hands around this technology now.
00:55:50:06 - 00:55:57:07
Stefan
Well said. And I was laughing one one go ahead Jens. Because I actually forgot my question.
00:55:57:10 - 00:56:32:28
Jens
Okay. So we're we're we're, a GraphQL vendor, and I think this, this wouldn't be a good podcast
without, a GraphQL, roast. So I'm curious from, from your perspective, if you take REST APIs
and we add an LLM, we we have a query language, right. We can query the REST API. So in
the and the age of LLMs do we, do we actually need GraphQL or is it, is it like like a dead thing?
00:56:33:01 - 00:56:57:27
Kevin
You know, well, like I said, I don't think this technology actually dies after it reaches a certain
level of, you know, widespread adoption. It sticks around forever. I think we we've gone on a
roller coaster with GraphQL, where you know, it comes out and that a lot of people are saying
this is the only thing I ever need for the rest of my life is GraphQL.
00:56:57:27 - 00:57:19:19
Kevin
I don't need anything else. And then I think we've we've kind of settled down to a point of saying,
okay, here are GraphQL strengths. And here's where I need GraphQL. And here's where I need
other kinds of APIs. Right. Instead of being a complete replacement for everything, it became
additive. And LLMS I think are similar.
00:57:19:19 - 00:57:46:28
Kevin
Like, we're not going to an MCP is similar. Like we're not going to replace everything. Or with
this new technology, it's going to be additive. And we just need to figure out where it really fits in.
There are certainly, you know, folks who are exposing GraphQL through MCP now. And so you
can like, you know, do queries and mutations, through a natural language interface.
00:57:47:01 - 00:58:02:20
Stefan
Yeah. Also, I also like you could tell very well that you're a very good consultant because you're
always like, it depends. Let me understand the use case first. And you go in first by saying, well
it always depends. And like whenever, like we talk to a consultant who has a very strong opinion
on something. I'm like, you don't know the full use case.
00:58:02:20 - 00:58:06:02
Stefan
So I really appreciate that. It depends type.
00:58:06:05 - 00:58:14:13
Kevin
Know it's frustrating to it's frustrating to tell people it depends. Right. So I don't yeah.
00:58:14:15 - 00:58:16:28
Stefan
No. Well said though, Jens You had another question.
00:58:17:00 - 00:58:49:20
Jens
You know like my and this is just something I don't know. I think hopefully every developer they,
they learn it in, in their career at some point. But I think every developer with enough
experience, it's, it's like, you stop having extremely strong opinions on something because
there's always someone who knows one particular topic better. Like you're either like extremely
broad in your knowledge or you're deep in some specific topic.
00:58:49:23 - 00:59:09:11
Jens
So if you're deep in one topic, you won't know other topics as deep. If you're broad, there's
people who are more deep on one topic. And so I think in general, like one one of the traits I
had as a, as a young developer, you know, I, you know, this probably from the, this
Dunning-Kruger thing. There's this, this mount
00:59:09:11 - 00:59:36:29
Jens
Stupid. I love to refer to that. You learn a little bit about the topic like, you know, early Jens
learns about GraphQL, knows everybody, everything about GraphQL. And then you're, you're
hammer to solve every problem is GraphQL now So you keep only talking about that and yeah.
Until eventually you run into like an enterprise architect. Who who who I don't know who who
sets you back.
00:59:36:29 - 01:00:00:04
Jens
And he's like, dude, this is just one of the many tools we're using. And relax. And you kind of
realize that, okay. Yeah. That's I don't know. Did you also have, like, like a Mount stupid moment
where someone where someone kicked your ass and you kind of realize, okay, I didn't know
everything.
01:00:00:07 - 01:00:23:17
Kevin
Oh, I mean, constantly, you know, I, which is which is why I think my, my attitude and my
approach is so different now than when I was younger. You know, I would I would be like, oh, I
think I have it all figured out. And then someone's like, oh, well, you don't understand all of these
design patterns, or you don't know the solid principles or whatever.
01:00:23:17 - 01:00:40:23
Kevin
And I'm like, oh, okay, I guess, I guess I'll go learn those. And then I'm like, Now I've got it all
figured out. And then folks are like, well, this is too complex for for what you need. Like, why do
you have, a factory, factory, factory, like, just stop. Just stop that. Like, it's too complex. And I
was like, oh.
01:00:40:28 - 01:00:59:22
Kevin
So, like, things are, they always end up being in the middle. There's that, like, bell curve meme,
right? You know, where you start everything simple and and everything's great, and then
everything becomes really super complex, and then you go back to things being really simple
again. And, you know, I think, I think that there's a lot of truth in that.
01:00:59:22 - 01:01:19:16
Kevin
And it's interesting to have like, you know, early career folks in your network and kind of see
them go through this experience of being like, oh, you know, I was so naive. And now I have it
all figured out and here's, here's how everything's going to work going forward. And you're like,
oh, you know, sweet summer child.
01:01:19:16 - 01:01:23:18
Kevin
Like it's you're going to have another awakening coming soon.
01:01:23:21 - 01:01:54:15
Jens
Yeah. You know, it's so funny. Like, I had this meme in my head while you were talking and you
didn't mention it already because, you know, I was young and I had no clue I was doing things.
And I was reading, like, clean code. And then I had this phase where everything had to be clean
code. And then you get older and you work on different projects, and you kind of realized that if
you go hardcore, clean code, you're actually harming your company.
01:01:54:15 - 01:02:18:14
Jens
Like it's harmful behavior. Like you don't need to be hardcore, you need to be a little bit or a
nuanced way of clean code. And in the end, if you go to this down, down this hill again, you kind
of realize some aspects of clean code. They are good, but it's not like, I don't know, it's clean.
Clean code is one of the many things that that matter to you.
01:02:18:14 - 01:02:40:10
Jens
And it's yeah, it's I think we often we go through this cycle of we learn something and we're
absolutely crazy about it and then we normalize. And if you if you become like this, like a, a
more experienced developer, you kind of figure out that you're I would say you're also less
excited about new stuff because you already kind of know, like, yeah, okay.
01:02:40:10 - 01:02:56:19
Jens
Like it's LLMs a new thing. But in the end it's also just an LLM. And then like everything else
also matters. So I think we're this is why you why you see like older developers, they, they calm
down a little bit.
01:02:56:22 - 01:02:57:25
Stefan
It depends.
01:02:57:28 - 01:03:28:15
Kevin
Yeah I think to be effectively pragmatic you need experience. Right. Like you need to to know
well, you know, sometimes I need a hammer or sometimes I need a screwdriver. And then
sometimes I got to go, you know, build my own tool to get this done. Right. But, yeah, it's, it's
easier to be more pragmatic when you've got, experience over time and you understand, you
know, what patterns and what solutions work for, what problems.
01:03:28:16 - 01:03:50:04
Jens
You know, this is another thing. When I, when I was like younger, I would I would always go like,
oh, let's buy a $5, droplet on Digital Ocean. It's cheap. And we can, we can with Docker, we can
run Postgres and everything there like it's cheap and everything. And these days I would never
want to run a Postgres database myself.
01:03:50:04 - 01:04:26:15
Jens
Like, never like, can we just buy something and you know, have you ever tried like we have and
you know, there's all these cool vendors that can deploy your stuff like render and whatsoever.
And I'm not talking negative about any of them. Okay. But we have, we have our backend for
our platform. It's, it's on Kubernetes. It's, it's on the most expensive tier of, of GCP Kubernetes
with just some kind of autopilot thing, like it's more expensive, but we have this pod or this stuff
we have this running for, I think more than two years.
01:04:26:17 - 01:04:51:14
Jens
Not a single glitch like nothing to deploy it. It works for two years. Like it's insane. And if you
understand this, you're like, why try out like a cool vendor? I was like, oh, we like, you know, this
is also something like, you know, with with WunderGraph, we built cool new tech, but we, we
tried to build it on the most boring tech we can.
01:04:51:14 - 01:05:30:00
Jens
We can. It's like Kevin said, yeah, the things we want to use are we, we want to like, we don't
want the fancy database. We want the most boring Postgres. And it just like make the problem
go like, and this is, I don't know, if you build for a long enough, you're kind of realizing I just want
the boring stuff because it doesn't break apart and you stop trying out like vendors like fly where
I don't know, suddenly your your deployment disappears and you don't know why and the
support doesn't answer or you're going through those kind of scenarios and then you realize,
you know what?
01:05:30:07 - 01:05:34:03
Jens
We just take GCP, Kubernetes and call it a day.
01:05:34:06 - 01:06:03:13
Kevin
Stability is really comforting, right? Like using tools that aren’t boring means they're probably
going to have a breaking change come through at some point. Which which is, is fine if you're
taking advantage of, you know, some, some new features or, or something new that's really core
to what you're doing. But, you know, especially with infrastructure people, people want boring
infrastructure, because they don't want to wake up at 2 a.m. and hear that everything went
down, you know.
01:06:03:15 - 01:06:04:18
Stefan
No well said.
01:06:04:20 - 01:06:27:25
Jens
And the, the, the sorry. The hardest thing like or the one thing like nobody wants to have is you
don't want to have a vendor. And every week you get a slack notification that something is
wrong, or even worse, it just blows up like customer calls you, hey, your service is down and
your vendor didn't even like you, wasn't even able to tell you.
01:06:27:25 - 01:06:47:16
Jens
Like these are the scenarios like this happens three times and you just switch away. And then I
think that's also like there's some some funny stuff going on between database vendors. And I
think next week we actually have, a database, guy on the, on the on the podcast. Stefan. Right.
01:06:47:18 - 01:07:05:26
Stefan
Yeah. So good segment. Guys. So we are at time. So. Kevin, thank you so much for joining us.
Jens the good thing is, is we're back next week. Next week we're back with Sam Lambert. So
CEO of Planet Scale. And if you've been seeing the Twitter drama, which is funny, but, Planet
Scale does insane, insane uptime 100%.
01:07:05:26 - 01:07:19:28
Stefan
Cloudflare GCP goes down planet scales untouched. So but other than that, we'll have them
next week. Kevin, this was a fantastic app. So thank you so much for joining us. Go get your
morning coffee. Next time that we have you on the podcast, we're going to do it at a little bit of
an easier time for you.
01:07:19:28 - 01:07:21:09
Stefan
But thank you again so much for joining us.
01:07:21:09 - 01:07:23:20
Kevin
No problem. Thank you so much for having me.
01:07:23:22 - 01:07:28:16
Stefan
Awesome. Thanks everybody. And then it takes a couple seconds to.