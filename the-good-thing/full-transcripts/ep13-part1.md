Episode 13
00:00:24:22 - 00:00:33:10
Stefan
And we're live. Welcome back, ladies and gentlemen, to another episode of The Good Thing.
I'm joined, as always, by my host, Jens, Jens How are you doing today?
00:00:33:12 - 00:00:38:09
Jens
What's wrong with you? Where's the. Where's the energy? The energy is.
00:00:38:09 - 00:00:42:09
Stefan
Here. What do you mean? I just did my intro. I said, what's up when I'm bringing everybody in?
00:00:42:10 - 00:00:59:08
Jens
But how are you doing? Okay. Yeah, it's. It's good. Sunny day in Germany. It's. It's getting
warmer. kids our starting to to, to play in the garden and, Yeah. It's good.
00:00:59:11 - 00:01:15:13
Stefan
That's awesome. And I'm super excited about today's episode because we're talking about a lot.
I mean, this morning we were just doing a little small demo of what the future is coming to be,
and this week has been crazy for tech. I mean, first we're going to talk about the Toby AI memo,
which is crazy for Shopify. We're going to talk about MCP.
00:01:15:14 - 00:01:31:28
Stefan
We're going to talk about the S and what it stands for. And what I'm really, really excited about is
just kind of like where we're going on the AI direction. And so let's kind of just kick it off. Jens. So
what are you seeing right now in the space, especially around AI?
00:01:34:07 - 00:02:05:03
Jens
So for quite a bit, we had where we were on the, on the path to kind of plateau in what the
models can do. I think the models are now quite good, but we can also see like, yeah, it
currently doesn't look like AGI, but I also think it's not necessarily a bad thing. Because what
we're currently seeing is like an, an integration play coming.
00:02:05:03 - 00:02:30:02
Jens
And, it's something I would say it really excites us because from the very beginning, we were we
were always super interested in helping integrate. And, yeah, I think it's it's just interesting, if we
speak about the elephant in the room, MCP what it means, what it what it does, how it will how it
will change.
00:02:31:17 - 00:03:01:19
Jens
Software development, for example, but also many, many other areas. And, like for me, I'm not
sure if we have this on the, on the, on the roadmap for today's session, but for me, a big topic
would be to talk about, the impact of MCP on, on software development. We just added MCP
support, in a very sophisticated way into, into Cosmo itself, which changes workflows.
00:03:01:19 - 00:03:38:11
Jens
It and just in general, I think one thing I would like to, to show today is, just the impact of MCP
on software development workflows and what I think MCP has, how it will change, the dev tools
space. Because in the past, when you were building dev tools or working with dev tools, it was
always like you, you needed to build, dashboards or whatever and user interfaces to configure
stuff.
00:03:38:11 - 00:04:02:17
Jens
And I think this is rapidly changing with MCP. I have just built a couple of, features into, into
Cosmo, which, from my point of view, it changes how you can structure certain workflows. And,
yeah, I think it's it's exciting and, and, it's a big topic.
00:04:02:20 - 00:04:24:03
Stefan
Yeah. I mean, it is the elephant in, like, every room. And like, last night I was at dinner with, my
wife's parents and a couple of their friends, and, they're a bit older, you know, they're, like, in
their 50s. And they were talking, and I asked them. I was like, well, I'm 27. You guys were alive
and well when the internet was shifting, you know, during the dotcom era and everything was
changing.
00:04:24:06 - 00:04:41:26
Stefan
And then I kind of grew up and I saw the shift, the cloud. I was there when Dropbox was
released, and then I was there also when we shifted to the iPhone, Apple stores, and we went
through all these shifts. But what I can't help but notice is this is probably the biggest shift of
them all. Like it feels like we're in the.com boom again.
00:04:42:03 - 00:05:06:13
Stefan
But for AI, we're on this forefront of unexplored technology. It's just getting better each day. And
if you remember, I think two years ago or a year ago when OpenAI was really, when ChatGPT
was released, if you compare it to what it is now and what it can do. And then I was talking to a
friend, he just graduated college, and he's like, how did you, did you finish your computer
science degree without ChatGPT?
00:05:06:16 - 00:05:25:28
Stefan
Like, we're getting to that point now where people are like, how did you do something before AI?
And so I think right now where we're at and everything that's changing, it's every single industry
is going to change. So healthcare, technology, even like running a small business, everything is
going to eventually have AI. And if you look now, you don't have an iPhone Jens.
00:05:26:01 - 00:05:43:10
Stefan
But I don't know if they've started to add it to your Google Pixel, but they have now Apple
Intelligence, which in the phone it does things to help automate your life and it just adds AI
summarizes messages together. It gives you smart shortcuts and things like that. And so I'm
pretty sure that AI is going to be everywhere, probably in your car soon.
00:05:43:10 - 00:05:48:07
Stefan
It's just going to be everywhere that you could even think of. Insane, right?
00:05:48:10 - 00:05:51:01
Jens
I have a MacBook, you have a MacBook.
00:05:51:01 - 00:06:12:29
Stefan
But you don't have oh wait, you do have Apple intelligence, but it's different on the phone. I'm
going to be completely honest. It's not as good as I thought it would be, but it's getting better, so
I'll give them that. But where we're going now with AI is absolutely insane. And so let's start off,
though, before we go into like the demo of what we've been working on, let's talk a little bit
about the API, or the AI memo is what we'll call it.
00:06:12:29 - 00:06:21:03
Stefan
So for those of you that don't know about, the Amazon API mandate, this was released in like
2002 or something.
00:06:21:06 - 00:06:22:01
Jens
00:06:22:04 - 00:06:44:24
Stefan
And Jeff Bezos made a mandate of like ten rules that everything must flow, all information
between teams must flow through APIs. And it's a famous memo and it's called the API
mandate. And what's crazy is, we're seeing it again. And when we're seeing it, and I'll share my
screen so we can jump right to it. But this is a leaked memo from Tobias Lutke from Shopify.
00:06:44:26 - 00:07:11:03
Stefan
And, he got ahead of the curve and he jumped right into it. And he started to explain that usage
and reflexive AI usage is now a baseline expectation at Shopify. So he's basically telling all his
employees that you have to use AI alongside your journey of working at Shopify. And the
biggest thing here is right here is that in their company, they grow 20 to 40% year over year.
00:07:11:09 - 00:07:28:08
Stefan
You must improve by at least that much each year just to requalify your position at Shopify. That
goes for him as well as for everybody else. What's insane to me about that 20 to 40%
improvement per year is a lot, right?
00:07:29:12 - 00:07:31:16
Jens
I don't know. It's hard to quantify, so.
00:07:31:24 - 00:07:48:00
Stefan
But I wouldn't say it is. But when you incorporate AI, which is exactly what he says out in the
memo, is that it doesn't seem that hard of a fact because you can use AI to basically improve
and go further out. But this is where it gets interesting. And Jens I'd love your thoughts about
this. But this is crazy.
00:07:48:00 - 00:07:57:02
Stefan
So using AI effectively is now a fundamental expectation of everyone at Shopify. What do you
think he means by that?
00:07:58:04 - 00:08:27:13
Jens
So we had we had similar discussions like we we don't have such a mandate, right? Yeah.
We're not big enough. Yeah. We had we had similar discussions. And I think the most important
thing and this is like if you work at Shopify or not, doesn't matter. But I think it is now a
fundamental, requirement for a developer to explore and understand how LLMs work.
00:08:27:16 - 00:08:52:06
Jens
And it's not even about like, liking it or not liking it, but understanding the trade-offs. For
example, and then, and I don't know, I think people who, who don't do it, they are missing out
because, you need to install tools like cursor claude desktop. You need to play with them. You
need to understand how paradigms shift because.
00:08:52:07 - 00:09:22:24
Jens
Yes. So earlier today, we had, we had a demo with our, CTO Dustin, who showed us that he
created an MCP server, from a super graph. And then he, he connected it to Claude Desktop,
wrote a single prompt, and Claude desktop built, an entire dashboard with information about all
employees in half a minute.
00:09:22:26 - 00:09:48:25
Jens
No code was required. And it is not about like you can now say, okay, this is simple, blah, blah,
blah, and you can have opinions, okay? But I think what people need to understand is it's a
paradigm shift there's now something new that it is now possible to to do a certain workflow. It
wasn't possible before and you should be aware of it because you're a software developer.
00:09:48:27 - 00:10:15:29
Jens
You should understand what kind of systems are possible, because I think also one one super
important thing here is, in the past you were always thinking that, okay, we have this this, this
architecture of we build the backend, it has a database, we build a front end, we deploy a front
end, and somebody can then use our front end.
00:10:16:01 - 00:10:54:04
Jens
But with MCP and AI and what's currently happening, you you can actually just build the API
because the front end almost builds itself. Yeah. And yeah, of course like not not every front end
builds itself. Like if you build it like, let's say you build a, I know an app for baseball or whatever.
Like it's not that simple, but there are so many apps where all they need to do is show a bunch
of data, create a table, create a diagram, some forms, whatever, like SAP, style user interfaces.
00:10:54:07 - 00:11:22:06
Jens
And now you don't need to code them anymore. And if you if you if, if the user can now describe
what kind of UI they want and it can be built and all we need is, APIs expose through MCP. I
don't know. It's, it's it's a new paradigm and, like it or not, but be aware of how it works and what
it can do.
00:11:22:06 - 00:11:27:24
Jens
And because I think we're going to see new products with this paradigm
00:11:27:24 - 00:11:49:20
Stefan
And one of the things I was coming up to my mind here is, four and five in the mandate. So
learning is self-directed, but share what you learn. So that's obviously what we're doing at
wunder graph, but everywhere we're experimenting with these tools, we're sharing what works.
We're sharing what doesn't work. But five I think this is going to fundamentally change
companies and software companies selling to other companies.
00:11:49:20 - 00:12:12:13
Stefan
So it's going to change B2B because before asking for more headcount and resources, which
means new tools, teams must demonstrate why they cannot get what they get, what they want
done with AI. What do you think about that? Do you think it's going to be harder now to be in
B2B SaaS when everyone's using AI? And they could, just, like you said, build it themselves?
00:12:13:07 - 00:12:31:01
Jens
I'm not sure if harder, but I like I said before, it's a paradigm shift. And I think there's, there's now
a lot of applications you don't need anymore because they can just be generated. Another thing
I would say is, it is it right to say it it lifts the tide.
00:12:31:04 - 00:12:35:06
Stefan
It's so yes, it lifts the tide or raises the bar.
00:12:35:09 - 00:12:59:21
Jens
Yeah, it raises the bar. But for everybody. So like, but not for people who don't use it. So I mean,
AI is accessible to everybody. If you're not using cursor today, your competitor is using cursor.
Yeah. And, you need to be careful. Of course, it is not good at everything, but it is good at a lot
of things.
00:12:59:21 - 00:13:36:03
Jens
And, yeah, if you if you're not doing it, that that's, that's a problem. And one thing on the fifth part
before asking for more headcount and resources, teams must demonstrate why they cannot get
what they want done using AI. You could also remove AI from this, sentence and replace it with
existing resources. Yeah, because to be honest, from a business point of view, you always need
to demonstrate that you that you cannot do something with existing resources.
00:13:36:15 - 00:14:01:27
Jens
So I think it makes sense. And then essentially what, what Toby is saying here, yeah. Before
asking for more people, try to see what you can do with the existing people and leverage AI
more. And to be honest, I like, you know, there's there's complexity in communication when you
add people. So let's say you have a team of eight people.
00:14:01:29 - 00:14:31:07
Jens
And if you if you think you need three more, the complexity of communication between eight
people and 11, it is it is not like, one third more. It is much more complex. And I think what AI
means in this context is you can have you can still have this two pizza team, like 7 to 8 devs, but
with AI they can now do more.
00:14:31:09 - 00:14:46:11
Jens
So they are even more dangerous. They are even more powerful. So, yeah, I think essentially
what what AI does, it's, again, it's making small teams more powerful. It's it's good for small
startups.
00:14:46:14 - 00:15:03:26
Stefan
Yeah. And I like what he said. There is like, what would this look like with autonomous AI
agents? We're already part of the team. It's what you said. Like, how can we do more with the
resources that we have? And then if you go a little bit further, this is amazing. Everyone means
everyone. So Shopify isn't just developers.
00:15:03:26 - 00:15:26:29
Stefan
You have a lot of different roles in there. So you have HR, you have operations, you have legal.
And what's amazing is now that everybody within the Shopify company, I think how many
employees they have, 1500 or something like that, is expected to be using AI. And what's great
is when leaders of big companies and we always say big companies like cruise ships, because
a cruise ship needs a couple miles to finally stop and turn.
00:15:27:01 - 00:15:41:29
Stefan
But he's putting this in front of them right now. He's saying, we need to get ahead of the curve.
And I'm going to be honest with you, Jens I think this is just one company that's about to follow
suit. You're going to start seeing every other company doing the exact same thing, and you're
also seeing it with companies like cursor.
00:15:41:29 - 00:15:58:18
Stefan
I mean, they went from 0 to 200 million ARR in like a year and a half. And it's because these
companies are open to adopting AI. Everybody is they're skipping their procurement. They're
jumping through everything to get AI into their company. Because I feel like it's a lot of FOMO. A
lot of companies don't want to get left behind on the on the AI train.
00:15:58:18 - 00:16:01:24
Stefan
What do you think?
00:16:01:26 - 00:16:29:26
Jens
I mean, if Shopify is doing it, it means the the the competition must follow almost. Yeah. I think
we will we will we will all get into this direction. And I think also we, we see it inside our own
company. A lot of people, a lot of our developers are using cursor now. Again, like there's parts
where it doesn't work.
00:16:29:29 - 00:16:50:10
Jens
For example, in our router, it is it is very hard to vibe codes. A query planner for GraphQL
federation. You you cannot easily do it, but, Yeah, for many cases, it's good. Yeah.
00:16:50:10 - 00:16:55:19
Stefan
Well, said and then final thoughts on this, this mandate that he put.
00:16:55:21 - 00:16:58:21
Jens
It to me, it's signaling that.
00:16:58:24 - 00:17:17:08
Stefan
The shift of the tide. But it's what you said. We're so early in on it. Like it's actually quite
amazing. And you said one thing is that people building business apps and I'm going to give you
like a real life example. So my mom, she has a pediatric clinic. She wants to build a dashboard,
let's say pre five years ago she would have to go and hire a developer.
00:17:17:08 - 00:17:35:00
Stefan
He would have to go to QuickBooks or whatever, integrate all that data, and then he would be
able to build a dashboard for her. It's long, it's expensive. It takes time. Now fast forward to
today. She could just talk to cursor or she could just talk to, let's say, claude right there. She
doesn't even have to go into an idea.
00:17:35:00 - 00:17:52:25
Stefan
She could just talk to it. Do you think, though, that, like, they can just prompt it already, but. Or is
it easier for us because we're developers that we kind of know how to talk to systems? Where
do you see the curve of like an average person, let's say a small business owner? How are they
going to interact with AI and like, how are they going to learn?
00:17:52:26 - 00:18:02:00
Stefan
Is it going to be like, you know, like taking classes of how to use the computer? It's like, okay,
this is how you talk to AI. This is the context that you give it. How do you see that going
forward?
00:18:02:27 - 00:18:28:11
Jens
I think it's going to be a bumpy road because we have so much knowledge for us. It's all simple.
But you know the first thing you just said, oh I can just go to QuickBooks and use the API. What
is an API like? Your mother will not understand. So yeah, I think the the first piece of the puzzle
is we need to.
00:18:28:12 - 00:18:54:17
Jens
So MCP is really cool. And I think there's a, there's a chance that we turn MCP into Lego bricks
where you can just say like, okay, MCP, let's say, let's just say it's it's like a little box or a
connector or a cable, and I can somehow plug it into my, into my claude desktop or whatever.
And, we currently see this is not yet the case.
00:18:54:17 - 00:19:21:12
Jens
For example, Dustin just showed showed us how do you enable MCP in Claude desktop? You
need to find the developer settings page. Then you enable MCP and then you open a Json file
where you have to put your cursor config, your, your mcp config. Yeah. I unfortunately that that
is not the experience we can, we can give to non-technical people.
00:19:22:09 - 00:19:54:14
Jens
But I, I think what we will see in the future is like marketplaces for these MCP connectors. And I
think we will we will see things like cursor but for humans. So for for normal people with not not
with code, I like it needs to be a different level of abstraction. And I'm, I'm super curious to see
what what kind of applications, people will be, will be able to, to develop.
00:19:54:14 - 00:20:09:18
Jens
But I think the one of the first big problems we have to solve is, Yeah, abstracting away the
complexity of APIs, making APIs easier to, to grasp for for everybody. Do you see.
00:20:09:18 - 00:20:15:21
Stefan
A future where we won't even need APIs? We're just MCp can go and just not even an API.
00:20:15:21 - 00:20:17:22
Jens
But do you know what MCPs.
00:20:17:24 - 00:20:19:07
Stefan
It's basically an API.
00:20:19:09 - 00:20:21:14
Jens
It's an API. Yeah, but I'm just.
00:20:21:14 - 00:20:24:21
Stefan
Wondering, like, and,
00:20:24:23 - 00:20:34:16
Jens
Do you know this this, turtles all the way thing? No. What is a like. Let me check. Yeah.
00:20:34:18 - 00:20:49:25
Stefan
But what I'm trying to get at is like, let's say a website doesn't have an API. Could AI in MCP go
and still grab all the data from that website by just like, let's say, crawling it or whatever. Do you
think that'd be possible?
00:20:49:27 - 00:20:54:23
Jens
But crawling a website. Yeah. And then what?
00:20:54:26 - 00:21:09:22
Stefan
But like it gets all the information. Like if it wasn't a, if it was an API, is that like, say, a website
doesn't have an API or a product, but MCP can go and just grab all the information from it as if it
were an API.
00:21:10:05 - 00:21:47:01
Jens
I think it would definitely be like, technically possible. Yes. Well, one of the big issues is we're
we're building HTML websites with interactive react for humans. So, that there was a time in like
when, when you were very, very young, I was a little bit less young. But I mean, I'm also not so
old in terms of the internet, but there was a time when the when the internet, the, the w w w it
was actually mostly HTML and a little bit of CSS.
00:21:47:03 - 00:22:09:29
Jens
Yeah. And we have turned the internet into a whole mess with JavaScript. And yeah, LLM
cannot really do so much with it. So you, you could or you, you would have to build a browser
like a headless browser browser and then and then like an agent could use this headless
browser to go through the web and do things for you.
00:22:10:01 - 00:22:22:09
Jens
It could kind of work. Yeah. But yeah, I think API sorry, MCP it would just be much easier. Like
just give me the Json thing and I can do something with it.
00:22:22:12 - 00:22:27:03
Stefan
No I agree, and you said you wanted to show something with the turtles. What was that?
00:22:29:06 - 00:22:47:01
Jens
Yeah. Like if you Google turtles all the way, but I can see all the, the, the, the idea is essentially
that if you look through it, it's, it's all just turtles. And then they're small turtles and it's, it's with
API, it's like.
00:22:47:03 - 00:22:50:03
Stefan
Oh I have infinite regress okay I see.
00:22:50:05 - 00:22:59:06
Jens
Yeah it's, it's API, it's all the way like everything is API. It's like your phone and its APIs and even
if it's MCP, it's still APIs.
00:22:59:09 - 00:23:06:15
Stefan
podcast.
Okay. Very cool. Actually, I've never heard that before. I always learn something new on the
00:23:06:18 - 00:23:10:13
Jens
Okay. What next? Security.
00:23:10:15 - 00:23:31:19
Stefan
Yeah. Let's talk about this. So this week there was a I'll actually bring it up a hacker News post,
which was the S and MCP stands for security. But actually let me jump into the post. And he
posted it on medium and it went pretty viral on Hacker News. It was on the top page. But yeah,
The S in MCP stands for security.
00:23:31:19 - 00:23:47:29
Stefan
I didn't actually read the post begins. Walk us through what was happening with the post. And
then kind of like the discussion that was happening in Hacker News, as well as obviously the the
oxymoron, the S in MC stands for security. Like what do they mean by that?
00:23:49:11 - 00:23:56:23
Jens
time, but, yeah.
I think the first thing, by the way, I'm not sure how much value we get from just showing it all the
00:23:56:27 - 00:24:00:00
Stefan
I'll jump up. Yeah, I'll jump out. Don't worry.
00:24:00:15 - 00:24:24:22
Jens
So I think the first thing we need to talk about with MCP is there's two models how you can run
an MCP server. So one way is you have an MCP server that runs over, standard input output.
And then there's a second way how an MCP server could run, over SSE. So it actually exposes
a server.
00:24:24:22 - 00:24:52:00
Jens
And now this server is, is subject to whatever you sent there. And whatever people do with it.
And so we have to distinguish these two cases. To give you an example. In our case, we added
sorry, we added an MCP server, to the Cosmo CLI. wgc, And this MCP server, it actually only
supports standard input output.
00:24:52:02 - 00:25:20:13
Jens
So that means you stop the server and then to have it do something, you need to send a Json
RPC message into the standard input, and you get a response via standard output. What this
means in terms of security is I can have a CLI like wGC. It accepts parameters and it returns
data to standard output.
00:25:20:15 - 00:25:52:19
Jens
We're now doing the same thing with MCP, except we're doing it over the MCP protocol. So in
terms of security it runs in the context of the user. And every like if you have permissions to do
things then the MCP CLI has permissions to do things. So it it's exactly the same context. But
we're not exposing a server of sorts or we're not like there's no port open or whatever.
00:25:52:22 - 00:26:29:15
Jens
So in terms of security, it's as secure or insecure as running any other CLI on your computer. So
it's it's not really changing anything to be honest. It's, it's just, we're giving a more descriptive
way or we have a more descriptive way of communicating over a standard input output. So that
is one way of using MCP. And then there's another way of using MCP, which by the way, it's not
yet so widely adopted.
00:26:29:17 - 00:27:16:11
Jens
For example cursor or claude desktop. I'm not sure on cursor actually but cloud desktop we
know it currently doesn't support SSE. Yeah. SsE if you don't know, it's just, like a, a little bit like,
a little bit more fancy way of doing http, with, some, some quirks. You can stream a response,
but other than that, it's, it's actually more or less just Http, and so the problem with this is let's
say you start an MCP server and it, it, let's say it can read and write, write, read and write in
your file system.
00:27:16:14 - 00:28:01:27
Jens
And you start the server with SSE enabled. Yeah. So what now can happen is all, all sorts of
super dangerous things because I can create a website and this website, well, that there might
be content policies, but let's say I can create apps or stuff that runs on your local machine like
an npm repository. And when you run an npm library, I can build something into it that searches
all parts on the local computer and tries to figure out if there is an MCP server listening, and if
there's an MCP server, I can introspect it and figure out what kind of tools does it give me.
00:28:01:29 - 00:28:32:10
Jens
And if there's an MCP server that allows me to read and write in the file system. Yeah. It means
I can now read your files and I can manipulate your computer. So if I have write access to your
computer, I could write a script that runs every time the computer starts and it does whatever I
want. So I now have kind of free access to your computer, and these are super dangerous
things.
00:28:32:10 - 00:28:57:14
Jens
So, yeah, I, I think that, you know, that there's people who build, for example, MCP servers for
WhatsApp, and you can build like MCP servers for whatever. And if you open them up, even on
the local local machine, it's it is one thing. And now you're vulnerable to all sorts of attacks on
your local machine, but maybe you're you're even, doing other mistakes.
00:28:57:14 - 00:29:20:29
Jens
Let's say you create an MCP server, you listen on, 0.0.0.0. So you listen on all parts, let's say
somehow your computer is accessible through the network, even if it's just a local network. It
now means all devices on your local network can find your MCP server. And by finding your
MCP server, they can now read your WhatsApp messages.
00:29:21:05 - 00:29:52:16
Jens
Is that is that what you want to do? So, yeah. And combine this with Vibe coding. And it's now so
easy to vibe code on MCP server. I think it's a super dangerous time because now everybody
can. Yeah. With with a couple of prompts, they can write, an MCP server. I don't know. On the
one side, I'm super excited about the possibilities of MCP.
00:29:52:18 - 00:30:24:18
Jens
On the other side, there are there are many possibilities. How how MCP can be exploited. If you
want to be on the safe side. Yeah. Build MCP servers with standard IO, because then, yeah, if
you can do stupid things on your, on your terminal, then MCP can also do these stupid things on
your terminal like it's, it's not worse than if you type some, some stuff into your terminal.
00:30:24:18 - 00:30:28:04
Jens
So yeah, long story short.
00:30:28:06 - 00:30:46:14
Stefan
I know, but have you seen, it's actually kind of funny. This guy, he vibe coded like a startup over
the weekend. Something like simple. But he was using MCP or whatever, and he vibe coded it,
so he didn't have very technical knowledge, and he released it on Twitter, and he's like, yellow,
like building in public. This is what I've built.
00:30:46:14 - 00:31:05:08
Stefan
Building people are like, wow, that's awesome. And he's like, I completely vibe coded it. So it
was really, really tough. And this pretty experienced developer, he went in very quickly and he
identified that vulnerability like that. He can get access to the application. And so he just started
messing with him like he would, take away the stripe payments because the guy was making
money from this app.
00:31:05:08 - 00:31:19:02
Stefan
So he removed stripe, and then he would mess up with the app or whatever. And he, like, the
guy goes back on to Twitter. He's like, help! I'm being like, hacked. I don't know how he's
hacking me. Like, whatever. I just vibe coded it. And the hacker himself, you wrote him. You
have a week before I come back.
00:31:19:07 - 00:31:35:14
Stefan
I'm hope I'm teaching you a lesson that you cannot just vibe code. Things need to understand
how they work. And people were like, I kind of respect him. Like, he's teaching you a very
valuable lesson. Like, he could destroy you right now, but instead he's like removing buttons or
doing some simple stuff because he got access to your application.
00:31:35:14 - 00:31:55:02
Stefan
But he's like, you're handling people's money. You're handling people's information. You should
at least know the basics of how to safeguard these things. And it came from this exact thing for
me right here with the MCP is that there was a portal open. He gained access. Eventually he
released a report of how he did it. It was anonymous because he didn't want to get in trouble,
but the guy ended up deleting his app.
00:31:55:02 - 00:32:14:03
Stefan
And I think you're spot on with that is that we're going to see a lot and a lot more unsecure apps.
Maybe it'll get better from just like vibe coding in that it in, you know, it puts in the correct
security protocols into place. But you're absolutely right. With vibe coding, you're opening up a
whole bucket, I guess, of attacks.
00:32:14:03 - 00:32:18:10
Stefan
If you don't really know what you're doing.
00:32:18:12 - 00:32:23:07
Stefan
What do you think?
