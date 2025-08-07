00:00:22:23 - 00:00:35:06
Stefan
And we're live. Welcome back, ladies and gentlemen, to another episode of The Good Thing.
Today we have a very special guest. As always, you know my co-host. Jens who is here. He's
not the special guest, but we have Kevin Swiber. Kevin and I pronounce that correctly.
00:00:35:09 - 00:00:36:24
Kevin
Perfect. Thank you.
00:00:36:27 - 00:00:50:25
Stefan
Awesome. Kevin's joining us over from the West Coast. So it is six am for them again. Thank
you so much for joining us so early. We have to have a talk with our content producer so he can
make these a little bit easier for guests that join us on the West Coast. But again, thank you so
much.
00:00:50:28 - 00:00:58:02
Kevin
Oh, yeah. No, no, this is this is fine. Sometimes I like to be awake before the sun is up, you
know? I feel like I'm racing it and then I win.
00:00:58:04 - 00:01:14:09
Stefan
No, no, you definitely won today. So Kevin one sun zero. So great job on that. And thanks again
for joining us. We're really excited today because and the good thing we typically talk about just
kind of like technology, what's happening around in the world. And then we really try to focus it
back on what we specialize in with APIs.
00:01:14:09 - 00:01:31:26
Stefan
And I don't know, I would say you're probably one of the biggest influencers in the API world. I
don't know if you would say that, but for us, we've been following you for a long time. I mean,
you have an amazing experience from being the outreach chair at the open API from working at
stripe. You have a long history at Postman, so if you want I mean, introduce yourself to the
audience.
00:01:31:26 - 00:01:36:21
Stefan
Kind of tell us a little bit about your history and what brought you into the space of APIs.
00:01:36:23 - 00:02:06:20
Kevin
Yeah. So I've been in the API space for, just over 15 years. Yeah. My, when I got started in this
space, I was doing like, you know, software engineering at typical enterprises, and that got into
enterprise architecture. And then, you know, a while back now, started interacting with kind of an
early API community, you know, worked on some some API standards, and then, started
working for API product company.
00:02:06:20 - 00:02:30:27
Kevin
So I went over to Apogee, for a while. We built, gateway and I did some IoT stuff and, you know,
ended up bouncing around to a couple of other startups after that and then landed at postman
for five years. And now I'm sort of working independently, and, you know, having kind of a range
of clients that I work with, they give me a really good kind of 360 view of the API space.
00:02:30:27 - 00:03:03:12
Kevin
So I work with enterprises on their API strategy. I work with API product companies on their
product strategy and go to market strategy. And then I work with investors who are looking to
invest in API companies. So, yeah, really, kind of try to hit every angle of, of APIs. And you
know, what was really interesting and I'm sure we'll talk about is a few months ago, sort of all of
these personas started talking to me about AI and MCP and how that's impacting the industry.
00:03:03:12 - 00:03:08:17
Kevin
So now a lot of my focus, in the last few months has been on MCP.
00:03:08:20 - 00:03:09:21
Stefan
You know, fantastic.
00:03:09:24 - 00:03:17:03
Jens
We can now all pack up the APIs. They they are not needed anymore. We replace them with
MCP.
00:03:17:05 - 00:03:20:27
Kevin
So you can do a hard pivot. Hard pivot. API to MCP. done.
00:03:20:29 - 00:03:22:09
Jens
It's a new age right.
00:03:22:11 - 00:03:24:15
Kevin
Yeah.
00:03:24:18 - 00:03:26:28
Stefan
It's it's interesting.
00:03:27:00 - 00:03:41:08
Jens
I'm curious about few things. I, I read on Twitter like some time ago that you wrote API
gateways. Did you write the API gateway for Apogee?
00:03:41:11 - 00:04:07:23
Kevin
So I worked on API Gateways for Apogee. We actually had a few, so, for a brief time, I was
managing kind of our, our main gateway team. And then we had, what was called a micro
gateway, for, for a while I was managing that team for a little while as well. And then we had kind
of like this separate open source initiative that I was a part of.
00:04:07:25 - 00:04:44:21
Kevin
And I built, an API gateway called Argo, in Node.js at the time. And that was a little bit more
developer friendly. Like, instead of doing, like config for policies, you did code for policies. And
we ended up sort of integrating that, into the product, at one point. So, so yeah, I mean, and
then sort of post apogee, went to another company where we built this open source gateway
called Express Gateway, which is still out there in the world somewhere, but that company is
now now gone, as startups, tend to do sometimes.
00:04:44:23 - 00:04:46:08
Kevin
But yeah.
00:04:46:10 - 00:05:11:14
Jens
Well, one thing I'm curious about is, you rare on the vendor side, and now you're on the
consulting side. How how how is it different to be a vendor in the API space and to be a
consultant? Like what what's what's the what's what's the biggest difference and what what what
kind of did you learn about companies when you when you switched sides?
00:05:11:14 - 00:05:39:13
Jens
Because like I worked for for tyk technologies for a couple of years now. I'm doing
WunderGraph for a couple of years. I'm on the vendor side all the time. And, you know, one
thing that I learned as a vendor, as you don't always see the whole company, for example,
oftentimes we interact with the platform team, and the platform team is, I wouldn't say like they
shield us, but they are our customer and the users like front end devs, backend devs, designer,
product owner.
00:05:39:18 - 00:05:52:18
Jens
Sometimes we we never really interact with them. So I guess if you're on the consulting side,
you, you see the whole space from from a different angle, like what's what's the biggest
difference?
00:05:52:20 - 00:06:11:26
Kevin
Yeah. Well, I think I always saw the vendor side from a slightly different angle because as I
mentioned before, I got into the vendors, I was doing enterprise architecture stuff at, you know,
enterprises. So I was, I was the person, like, evaluating the vendors, and, you know, giving sort
of a go or. No, go on that before joining the vendor.
00:06:11:26 - 00:06:35:15
Kevin
So I always sort of brought that experience into what I was doing. And in my, my startup days,
one reason I like working for startups is that I tend to work cross-functionally. So even though I
might be doing like engineering management, you know, I'm also working in, pre-sales capacity,
doing often consulting with, with those customers to figure out where their problems are.
00:06:35:18 - 00:07:00:00
Kevin
You know, what they need? I think when you are in that vendor space, though, it's kind of easy
to forget that you're not the center of the customer's world. Right? And, you know, as as I've
moved into consulting and now have sort of a bigger picture, you know, when I was at Apogee
or postman for us, you know, we're thinking like, okay, let's, let's work on, on this customer.
00:07:00:00 - 00:07:22:26
Kevin
Let's see how we can best provide a solution with our product for this customer. Meanwhile, the
customers, you know, got 15 different initiatives going on. And like, you're just one of them,
right? And so, you know, I think it's, it's easy to, to start wondering as a vendor like, why isn't this
person responding to me? We have to, to move this deal forward.
00:07:22:28 - 00:07:41:16
Kevin
Is it not the right time right now? You know, and trying to avoid things like having a no decision
On The deal, and I think it's, like, really easy to forget that you might get to a no decision on the
deal because that person has changing priorities and you're just a small part of their world.
00:07:41:19 - 00:07:57:07
Stefan
Yeah, yeah. Well said. And, question from my end. So, this consulting side that you're doing
now working with vendors, you also mentioned with investors especially now in this, you know,
field of AI. Like what are you currently seeing from your point of view? Like what are you
advising investors on is like on companies that you're seeing?
00:07:57:07 - 00:08:03:20
Stefan
How do you see AI and, you know, APIs, from an investor's point of view?
00:08:03:22 - 00:08:27:15
Kevin
Yeah. Well, you know, again, the last few months has been a lot of questions about, how is AI
changing everything, you know, how is it, impacting their current investments? Should they be
investing more money? Should they be looking at a new round? Should they be advising their,
you know, portfolio to, to start doing more with AI or MCP?
00:08:27:17 - 00:08:51:03
Kevin
So, I wouldn't say that there has been, an anxiety around it. But, you know, a curiosity for sure.
And, and I think by, you know, the vendors in the startups, I think there's an excitement there as
well. I think, you know, as a product company, there's always in the back of your mind, like, am I
going to be irrelevant?
00:08:51:03 - 00:09:27:06
Kevin
in the next five months, am I going to be irrelevant, you know, in the next year? And so working
to stay relevant is, is an important thing. But yeah, there's certainly I wouldn't say like there was
any panic, recently or anything. But you know, even sort of prior to, AI and MCP taking off, you
know, a lot of the concerns were around, what is actually still relevant in the API space, are
gateways becoming more commoditized?
00:09:27:09 - 00:09:53:09
Kevin
You know, is is design becoming, more important? Is there more opportunity out there, to, to get
sort of a larger customer base? What are the different customer, portfolios out there, between
sort of startup, midsize, enterprise. And you know, what's the the difference in sort of
approaching those markets. So I think all that stuff still exists now.
00:09:53:12 - 00:10:03:03
Kevin
But now we're wondering, how do we how do we grow our product? How do we stay credible?
How do we stay relevant, going forward in this new AI space.
00:10:03:06 - 00:10:26:06
Jens
You just said what is relevant. But if you turn it around, what would you say? Given what LLMs
can do today and the the trends we're seeing, what would you say, what what's became
irrelevant or what what will fade away from from now on? Well, do you have any observation in
that direction?
00:10:26:08 - 00:10:47:15
Kevin
Well, I mean, I tend to think things stay around for a really long time, right? So, even if it's
dropping in relevance, it will probably still be around for a long time. There are still there's still
plenty of good business to be done in mainframe computing, you know, and and we've largely
gone away from that as an, as an industry.
00:10:47:15 - 00:11:15:18
Kevin
Right. So, but for some people, mainframe computing is incredibly relevant to their day. Right.
So I think, you know, what's popular is probably, a different question. I think you can continue to
make tons of money off of all the software that we've built and all of the different technologies
we've built over the years. But if you want to stay on a wave of what's popular, that's, that's
changing a little bit.
00:11:15:20 - 00:11:40:29
Kevin
You know, I think, I think infrastructure companies are, becoming more boring, to, to folks, which
isn't necessarily a bad thing. I think you kind of want your infrastructure to be boring in some
ways. But, you know, it it's it doesn't always feel good to be like a startup who is trying to get
your name out there.
00:11:41:02 - 00:12:04:09
Kevin
And, you know, try to get some press and try to get some people who love your product. It
doesn't always feel good to to think, oh, maybe my stuff is boring, right? But as, as sort of times
shift and new exciting things come in the way, I don't think it necessarily means things become
irrelevant. It just means the focus is elsewhere.
00:12:04:09 - 00:12:06:08
Kevin
For a time.
00:12:06:10 - 00:12:36:16
Jens
Well, one observation I made is when you when you go to to tech, TechCrunch or press in
general, like you can announce a funding round or you can announce a crazy thing in AI and
everything else, like, I don't know if you're not all new API standard or something or I don't know,
like there's, you know, there there was like a specification thing or like other things like in, in the,
in the, in the, in the surrounding AI noise.
00:12:36:16 - 00:12:48:02
Jens
these days it's extremely hard to do anything with, with APIs or something where, where people
are like that's, that's interesting. Like, yeah how do you see that?
00:12:48:04 - 00:13:25:18
Kevin
Yeah. And I think it's hard as a, tech industry as well, because we are kind of on the bleeding
edge of things and like, we, we are early adopters to a lot of different things. And so, you know,
from our perspective, sometimes it's like, oh, like the whole industry is moving in this one
direction. But if you talk to like, you know, normal people who aren't in, in tech, people who are
just doing their jobs at regular enterprise companies around the world, you know, they aren't
they don't have 15 claude code instances running and trying to automate their whole lives.
00:13:25:18 - 00:13:47:02
Kevin
Right? Like they're they're, just trying to figure out, you know, okay, I'm using ChatGPT. Now my
boss wants to use ChatGPT. What does that look like? Right. So it's. And, you know, they don't
they don't have a whole they're not like, already planning out a whole MLOps thing internally.
You know what I mean? Like, it's.
00:13:47:04 - 00:13:47:15
Stefan
Yeah, I.
00:13:47:16 - 00:14:05:25
Kevin
Yeah, we are looking at, at this and our focus and even the journalists focus, tends to be, Along
where kind of the bleeding edge tech folks are. And I don't, I don't think it really matches what
the regular person is doing out there today.
00:14:05:28 - 00:14:20:22
Stefan
I think you're spot on. Like, I was talking to a couple of my buddies. They work at big enterprises
like fortune 500 companies. I'm like, oh, like, have you heard of cursor? Or they're like, what's
cursor? And I'm like, have you heard a lovable? They're like, what's lovable? And I'm like, have
you heard of ChatGPT? They're like, yeah, we just kind of started using it.
00:14:20:22 - 00:14:37:01
Stefan
And like, these are smart guys. But like, I think what you said is spot on. Like, we're kind of in a
bubble, like our own bubble. We're on the bleeding edge. We see this stuff. We see these crazy
rounds these valuations and everything. But when you back up and you go talk to actual normal
people, nobody actually sees that stuff, which is I think you nailed it on the head.
00:14:37:01 - 00:14:38:06
Stefan
There.
00:14:38:08 - 00:14:48:28
Kevin
Yeah. You know, like, did you see that there's a new dotnet runtime that released, you know, like
that's that's where they are. And we're like, no, actually, I didn't notice that at all. You know.
00:14:49:00 - 00:14:53:06
Stefan
It's so interesting. And then, go ahead. Jens, I think you had a question.
00:14:53:09 - 00:15:21:13
Jens
You know, when when I talk to our bigger customers, like bigger enterprises, and we're talking
to, like, an architect or someone like topics that they are interested in this, like they also look at
AI and things, and they are using Cursor like they are modern, but topics they are interested in
is things like API governance. Like how can we build a robust process to roll out API changes
and not break things?
00:15:21:13 - 00:15:54:21
Jens
And how can we collaborate better? Like very like I sometimes feel like there's so much AI noise
and there's fundamentals in the, in the API space that are not yet solved Well, like for example,
one, one big topic we're, we're working a lot on is how can we help people better collaborate on,
on API design and, how to how to implement APIs and how to structure them and best practices
and blueprints and these kind of things.
00:15:54:23 - 00:16:23:13
Jens
And, I wouldn't exactly say it's like the most exciting topic, but it's a very important problem to
solve. And there's not so great tooling to figure out, okay, if we have a microservice landscape
of of hundreds of services and potentially tens of thousands of of Rest API endpoints, how can
we manage that level of complexity? And you can't just take this whole thing and say like, okay,
here's like an LLM.
00:16:23:13 - 00:16:52:26
Jens
It figures it out. No, that's like, you can't solve every problem with fancy LLM tech. And there's
but from, from a messaging perspective, these are things where I would say the reality check is
schema governance, things like that. This is something enterprise architecture, architects think
about. And then you have this, this whole like, hey, I have five, five cursors running in parallel
and they co generate something.
00:16:52:26 - 00:16:57:23
Jens
And, yeah, for me it's to two realities.
00:16:57:26 - 00:17:21:27
Kevin
Yeah. It's something that, you know, really stuck with me. In my enterprise architecture days, is
this concept of having a priority, people then process, then technology. Right. When we put, like,
the technology first above the rest, we end up in a place like having, a bunch of APIs spread out
everywhere. A bunch of duplication.
00:17:21:27 - 00:17:43:20
Kevin
Nobody knows what the other person is doing. And, you know, we don't even have a good idea
of what APIs are out there, right? I work with tons of companies who are like, yeah, so we went
to this sort of autonomous teams, kind of approach where they got to do the development and
the deployment for themselves. And, you know, that's that's kind of worked out.
00:17:43:23 - 00:18:01:03
Kevin
But now we have no visibility into what any of these teams are doing. And we have seven
address verification APIs, and we're paying vendors on the back end for this. Right. Like we've
got three different vendors for address verification that we have APIs on top of, you know, how
do we how do we get out of this mess?
00:18:01:06 - 00:18:21:07
Kevin
And so it's been it's been interesting to kind of take a step back and, and go to the process and
not just look at, oh, let's do microservices everywhere. Let's have autonomous teams. But like,
let's go back to the process of, how do we actually launch software here? And, you know, how
do we get the most out of the investments we've already made?
00:18:21:09 - 00:18:28:26
Kevin
And how do we get kind of a handle on, on the API sprawl that's happened in our organization,
right?
00:18:28:28 - 00:18:51:22
Jens
Yeah. You know, this is interesting what you're saying. Because for us, like, we we made and I
would say we we made a super interesting journey on, on like a fast track because when we
started, it was all about, okay, we want to build something cool with GraphQL. That was like our
starting point. And it's a valid starting point.
00:18:51:22 - 00:19:15:17
Jens
Like it's fun. It gives you motivation. And then, we we we iterated on that and we kind of realized
developers like our tool, but it is hard to sell it into enterprise. Like for for enterprise there's no
sellable unit like, they they like it and some people use it but not really enterprise. So we pivoted
into federation and federation.
00:19:15:19 - 00:19:52:19
Jens
Like, you know, you have like multiple GraphQL servers and together they, they federate and
then you have like a unified thing, on, on a high level. And what that allowed us to do is we were
able to get into enterprise accounts where multiple teams wanted to collaborate on creating a
GraphQL API. And then we didn't stop there, but we were curious to figure out, like, you know, if
you if you if you are an ambitious startup, you are you're looking for not just people who like
your tool, but you you really want to make an impact.
00:19:52:19 - 00:20:23:03
Jens
And then like, you know, like on a monetary side, you want a fast growing startup. But how do
you create a fast growing startup? You really must find a lot of value in the market. You must
find value for the customer. So we dig deeper. And if you go beyond GraphQL, if you go beyond
Federation, if you go beyond API gateways, what we kind of realized one of the biggest
problems our, our customers have is, collaboration.
00:20:23:09 - 00:21:01:18
Jens
It's it's working together. It's what you said. It's about people and process. And so, we're we're
kind of expanding beyond just the tech, like, we're we're stepping more and more away from the
tech, and we're trying to help people work together better and collaborate better. And also we
help them to, to take their existing processes and optimize them because we we kind of realized
that, you know, one of the funniest things we realized is when people want to change their, their
APIs, and I explicitly go away from the from the GraphQL language.
00:21:01:18 - 00:21:35:07
Jens
But when they try to change their APIs, we ask a bunch and we realize a lot of our customers,
they use miro boards. They put a screenshot of an application on the Miro board, and then they
put post-its on the screenshot side by side to try to articulate what could be the API
requirements and such. And then they create gigantic Miro boards with lots of screenshots and
post-its all around, and try to figure out what could the API be.
00:21:35:07 - 00:22:07:03
Jens
And then they take these post-its and somehow translate them into other tooling where they
actually create APIs for that. And we kind of realized if we want to, if we want to expand our
scope, if we want to bring more value to them, it's actually not so much about API gateways and
these kind of things and federation. It's more about how can we help the people and, and
optimize the process of designing and working together and, and these kind of topic.
00:22:07:03 - 00:22:25:06
Jens
So that's I don't know, it did it, it it clicked for us. And it, it's, it excites us much more to help the
people get something done than just building like a faster gateway or something. So I don't
know, our our thinking has completely changed. I'm curious, what you think about it?
00:22:25:08 - 00:22:53:21
Kevin
Yeah. It's, you know, I, I, I think being in this business is super interesting. And I particularly like
working for startups. When I went over to postman, my background had always been in sort of
engineering, engineering management. But when I went over to postman, at the time, they had,
a need for people with, like, enterprise experience as they were going to start trying to sell more
to enterprises.
00:22:53:23 - 00:23:20:19
Kevin
And so, you know, where they really needed help on was, in sort of pre-sales and post sales,
technical folks. Right. So I joined as a solutions engineer, and got to work with, with people, with
a bunch of different companies, as they were, you know, having struggles with their API
programs, trying to figure out kind of broadly with their API programs, not necessarily specifically
with postman.
00:23:20:19 - 00:23:58:11
Kevin
Right. That kind of led to a role where I acted as sort of a field CTO, for a while there. And that
was that was hugely rewarding, right? Because, after spending so much time with all these
different companies and, like, understanding all of their different problems, then you're in a
position to, actually talk about that experience and say, here's what I've seen work, for these
companies or, you know, the position that you're in right now, I know it feels like you're alone in
this, but you're really not like, you know, I've worked with several companies who have been
here before, and here are some things that they're trying,
00:23:58:14 - 00:24:16:29
Kevin
to to ease the pain of these problems that your experience, and that kind of stuff is not only is it,
like, rewarding for me to do, and I think it's rewarding for a lot of people to do. But it really
develops these close customer connections. And like, you're really, you're really in it to help
them succeed, right?
00:24:16:29 - 00:24:40:11
Kevin
Like that. That's part of the job. If they're not succeeding and you're not a part of their success,
then you're not really doing your job. Right. So it's it's well beyond, here's a product that I'm
building that you're buying and that you're implementing, and, and more like, how do we build
these connections that are going to last a long time and be mutually beneficial?
00:24:40:14 - 00:25:05:13
Jens
Yeah, that makes sense. I, I have one question you mentioned earlier. You work with investors.
If I'm, venture capitalist. What what's your suggestion? What what should I invest in? What
should I, not not touch like, what's what what's your current thinking of the of the market from an
investors perspective?
00:25:05:15 - 00:25:41:07
Kevin
That's an interesting question. And saying it's usually kind of more specific, than that. You know,
kind of looking at, the entire market through a particular lens. So, you know, if we, we take
gateways, for instance. Right. There's, a portion of gateways that have really become
commoditized over time. And, you know, I wouldn't say all of what gateways do because I think
gateway companies actually have platforms for the most part.
00:25:41:07 - 00:26:06:21
Kevin
And they they do quite a lot. But, you know, once you start seeing Amazon come out with a
product through AWS and GCP and Azure all have products for something, these are
essentially our utilities. These are essentially the electric company, for tech. Right. And so this
stuff starts to become utility. And they charge utility rates.
00:26:06:21 - 00:26:33:20
Kevin
They charge sort of like, you know, usage based, for, for all the different meters that they might
have. And so, you know, the what I often say to, to product companies as well, is that, and to
investors, what they're looking for is a company that is is credible. So like, they've got, some
experience that means they know what they're talking about.
00:26:33:22 - 00:26:55:02
Kevin
A company that's that's relevant. They're producing something that people actually want today.
And a company that's differentiated, like you're, you're able to look at them and say, here's, you
know, here's what makes them uniquely them, and, and where they sit in the market. So you
can still do all three of those things, and, and be a gateway company.
00:26:55:05 - 00:27:14:11
Kevin
But you've got to understand that there are certain table stakes that are higher now because a
certain portion of what you're doing is utility is commodity. And so you've got to build on top of
that. Right. Like so the bar to entry is higher than it used to be. Could because a portion of this
has gone to commodity.
00:27:14:11 - 00:27:34:01
Kevin
So, you know, often when they're evaluating companies, I'm kind of starting with that as a
baseline and then saying, oh, you know, here's you know, the three different ways they
differentiate or looking at the market and saying, like, here's you know, how the these five
companies are differentiating in this market.
00:27:34:04 - 00:28:05:28
Jens
So if you look at if you look at the the Magic Quadrant these days, like if you look at big players
like like Kong and Apogee and, and gravity and others, where, where do you see the, like the
API space going in terms of vendors? Like, is there like one one winner or is it like iterations or
hype cycles or what's your what's your take on, on on where the magic platform is going.
00:28:06:00 - 00:28:28:23
Kevin
Yeah. Well I mean that's, that's a, that's a whole other game, right. With with the analysts. And I
think it's a, I, I think it's really easy to get, jaded by the analyst model. But I think they actually do
provide a really good service. And, you know, I've worked with analysts from the enterprise
architecture perspective.
00:28:28:23 - 00:28:49:15
Kevin
I've worked with analysts from the vendor perspective. And it's a hard job to have, like a trusted
third party between everyone. Right. And a lot of people think it's like, you know, sort of a pay to
play thing. As a vendor, you pay them so much money, and then you get on the quadrant. And
I've found that's not necessarily the case.
00:28:49:17 - 00:29:13:17
Kevin
You know, typically, for folks who are getting on that quadrant, you're going to be bigger anyway,
because you're one of the top players in the space. So you're probably going to have like, a
subscription to, to Gartner at that point just because of the size of your company. But they, they
constantly mentioned sort of smaller companies that, that aren't that big who certainly aren't
paying them.
00:29:13:19 - 00:29:41:14
Kevin
You know, and, so, yeah, I think looking at the the quadrant is super helpful for folks who don't
have the time and the energy to go really deep into all of these companies and having a
relationship with folks like, like Gartner or Forrester, helps them sort of, speed run in into, into
the space that is really complex.
00:29:41:14 - 00:30:08:24
Kevin
You know, the API space is super complex. I always say it's like, the most difficult Venn diagram
of vendors who are providing services, and some of them overlap, and like trying to figure out
which vendors do I purchase to to piece together my API program is an incredibly difficult task,
because you're going to be buying from three vendors, and maybe they have four things that
overlap all three of them.
00:30:08:24 - 00:30:30:27
Kevin
And you've got to choose which vendors you're going to to actually adopt for, for those certain
features. And it's, it's incredibly difficult. So I think the, the Magic Quadrant, is it can be super
helpful for folks who kind of know where they sit, where they're like, oh, we always buy kind of
the luxury products, right? Like, what is the most luxurious product on here?
00:30:31:00 - 00:30:48:26
Kevin
Well, this one's all the way up into the right. They're probably the most expensive. Let's go with
them. Are there are folks who are like, like, we don't want to commit that much. Like we know
that we're we're kind of early in this. Maybe there's there's someone over here towards the,
closer to the the bottom left, that we should go with.
00:30:48:26 - 00:31:06:16
Kevin
So I think I think it is it is helpful is certainly not everything. I think you can't look at a magic
quadrant, and know for certain where to go. You still almost kind of need a trusted third party in
there to help you out. If it's if it's all brand new to you.
00:31:06:18 - 00:31:07:17
Stefan
Yeah, I think that's super well said.
00:31:07:18 - 00:31:31:29
Jens
1 of the big, benefits of, of analysts I see is let's say you're you're a CTO of a fortune 100
company. You want to you want to start an API initiative, and you, you you don't know what is
the right thing. You can go to an analyst and say, hey, here's my requirements. What's your
recommendation? They give you a shortlist of three vendors.
00:31:32:02 - 00:31:57:17
Jens
You evaluate them and that's that's probably a very good starting point. And if you pick any of
the three it will probably and be an okay solution. And that's ultimately in in in that kind of roles.
It's also a lot about like risk management. It's not just like making a decision but not making a
bad decision because it can it can, affect your job.
00:31:57:17 - 00:32:01:21
Jens
So I, I think the model makes sense. Right.
00:32:01:24 - 00:32:16:04
Stefan
It's a very fair model. Like I think I would agree. I mean, Gartner, what they do is they provide
you a service just based on like what you said, like you do pay to get in and if you are a big
company, but that doesn't necessarily mean you're going to be put in the quadrant. The
quadrant has rules.
00:32:16:06 - 00:32:34:17
Stefan
And also the analysts stay very fair, which I appreciate. They put smaller vendors into there.
They put bigger vendors into there. My my question though is knowing that and now your
background is I mean, just given your your entire experience. But now as a consultant, what are
some tools that you recommend? If people come to you and they're like, hey, like I'm looking for
a gateway.
00:32:34:24 - 00:32:44:09
Stefan
Like, what are some of the tools that you go top of mind where you're like, hey, I'd work with
these three or this type, but tools that you recommend in the API space.
00:32:44:12 - 00:33:07:00
Kevin
Yeah. You know, there are tools that I definitely do not recommend. I don't think I should call
those folks out necessarily. But, you know, I think there are, there are a lot of great tools out
there, and I think that there are good open source tools out there as well, for, for folks who want
to get started.
00:33:07:02 - 00:33:35:06
Kevin
You know, typically, I, I look at, what their requirements are. If it's just like one small project that
they need to to stand up and get running, I'll typically do an evaluation between, you know, like,
kong and tyk, maybe, maybe gravity who is open source, at least their open source version, and
kind of see where that's going to fit for them.
