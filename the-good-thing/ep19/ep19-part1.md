Episode 19
00:00:09:26 - 00:00:27:17
Stefan
Oh, cool. And we're live. Thanks for joining us for another episode of The Good Thing. Today we
have a very special guest, someone we've been working very closely with. But Robert Farr, a
principal architect at Procore. And as always, I'm joined by my co-founder and co-host, Robert.
How are you doing today?
00:00:27:19 - 00:00:36:11
Robert Farr
Doing great. Doing great. It's a beautiful morning. So a little overcast, but, you know, it's bright
out. So enjoying the day.
00:00:36:11 - 00:00:40:11
Stefan
hear again.
Fantastic. And where are you calling off from? Is a, You've told me before, but I'm curious to
00:00:40:14 - 00:00:47:02
Robert Farr
Yeah, we're, I'm out of, well, north of Kansas City, Missouri. So right in the central, United
States.
00:00:47:02 - 00:01:09:23
Stefan
So awesome. And I don't know if you know this, but I used to go there often last year or. No,
three years ago before we started WunderGraph, because I worked for a company called Milo,
which was literally, like on the line of Kansas City and Missouri. So you can go back and forth
between the two, which kind of threw me off a little bit, because you would see the you would
see the different license plates, but it was a good it was a good place to be.
00:01:09:23 - 00:01:24:14
Robert Farr
I loved it. Yeah, yeah. No, it's an interesting city. And we're right on the border between two
states. Their state line drive is probably, right in that range of where you were. So. Exactly. A lot
of a lot of culture.
00:01:24:17 - 00:01:41:12
Stefan
So awesome. Well, thanks for joining us today. So today we're going to be talking about is just
kind of your role and experience. So first you roll out procore. You're leading overview of your
experience. And then we're going to dive a little bit into the kind of the conversations that we've
been having, you know, things that you've seen and your years of experience.
00:01:41:12 - 00:02:00:08
Stefan
For example, with delivery pipelines, GraphQL, GraphQL, Federation, AI, how AI is coming into
organizations and things like that. It would just be like an ad hoc discussion like this. But to kind
of kick things off, Robert, tell us a little bit about your experience. So we've been working with
you as you've been a procore but where did your journey begin?
00:02:00:10 - 00:02:27:26
Robert Farr
Yeah, yeah. So I've, you know, my procore journey has been the last, I would say three and a
half years. But prior to that, I spent, really got my start, at my company. So 22 years at a,
enterprise healthcare IT company, that that companies now part of Oracle Health. So for those
that are curious, but I started out there as a software engineer, right.
00:02:27:26 - 00:03:02:09
Robert Farr
Junior software engineer and, got to experience, building an enterprise company that ultimately
became an enterprise SaaS company, over those years. So, learned a lot, learned a lot from a
lot of very knowledgeable architects, over those years and got to see how you can transform an
industry, with software, in this case, it was very, you know, health care focused, and now I find
myself kind of doing the same thing in the construction industry.
00:03:02:12 - 00:03:06:26
Stefan
Very cool. And this company, what was it called before it became Oracle Health?
00:03:06:28 - 00:03:11:19
Robert Farr
It was called Cerner. Cerner, so certainly operation. Yeah.
00:03:11:26 - 00:03:14:12
Stefan
They they just recently became, Oracle Health.
00:03:14:12 - 00:03:18:25
Robert Farr
Right. Yeah. In the past couple of years I believe. Yeah.
00:03:18:28 - 00:03:26:26
Stefan
So I had a lot of friends that worked at Cerner. And then they went to Milo, which is where I was,
because Cerner has a good headquarters out where you're based, right?
00:03:26:29 - 00:03:53:24
Robert Farr
Yeah, yeah, Cerner headquarters was here in Kansas City. It was, founded in Kansas City back
in 1979. So, I had the privilege of getting to work for the the founding CEO or the founders for,
the majority of that time. And, the, it's really, you know, I would say a lot of my, my colleagues
and coworkers, they have spread out into a number of different startups and companies.
00:03:53:26 - 00:03:58:17
Robert Farr
In this area, some of those are working remote, but some are really right here in Kansas City.
00:03:58:19 - 00:04:10:11
Stefan
Kansas City has a decent tech hub. From what I remember when I was there, there's some
decent startups and just kind of established companies. I worked at Lockton, but Cerner is
there. There's Procore, I have an office there now.
00:04:10:14 - 00:04:34:11
Robert Farr
We we have a, we have a, wework, so procore, shortly after I joined, we, we, acquired a
company called Labor Chart, which had a office in Overland Park. So there is a number of
procore, employees and engineers that, live here in the Kansas City area. That's awesome. Just
go ahead.
00:04:34:14 - 00:04:50:14
Robert Farr
Oh, no. Yeah. You said, you know, in terms of its tech hub. Yeah, I think Kansas City is is it's got
a really interesting tech hub. There's the the Kaufman Institute downtown that really helps
startups get going. So it's fostering a lot of innovation.
00:04:50:16 - 00:05:01:15
Stefan
You know, I can attest to I've seen when I visited, it was awesome. And then you started off your
career at Cerner and you said you spent 20 years there, or how did you make the jump to pro
core?
00:05:01:17 - 00:05:26:26
Robert Farr
Yeah. So, so funny enough, I, so towards the end of, you know, the last thing I was working on it
at Cerner, we had built a, you know, a SaaS cloud based SaaS offering, multi-tenant, and, you
know, when I first got there, you know, often when you go really fast, right, you, you hit that
initial thing and then you start to scale, right?
00:05:26:26 - 00:05:57:09
Robert Farr
And scale brings new challenges, when you're adding customers very rapidly. And, so I deviated
from kind of, you know, distributed systems, a distributed databases for a while and help bring
in, kind of the site reliability engineering practice in that space. And two of, my main leads, a
week apart, in 2020 told me, hey, we are going to go work for this exciting new company.
00:05:57:11 - 00:06:11:21
Robert Farr
And neither knew that either. Or. And they both went to the same place. It was procore. So that
caught my attention. And, it was a little about a year later, that, I finally saw a position and
decided to take a deeper look.
00:06:11:23 - 00:06:15:09
Stefan
And was this pre IPO that you joined or post?
00:06:15:11 - 00:06:20:18
Robert Farr
I joined post they joined pre. So we're right on that. Both sides of that boundary okay.
00:06:20:25 - 00:06:42:27
Stefan
And if you could for the audience just tell a little bit about what Procore does. Because most
people don't know this. But a building that you've probably been in used software to help build it
with. Procore was a very fast growing startup. I read a little bit about, about the CEO and the
journey that he took it, but hold on, it's a little bit about what Procore does and the software and
just what you've helped build with them.
00:06:42:29 - 00:07:11:16
Robert Farr
Yeah, yeah. So Procore, so Procore really, you know, history historically is really focused on the
general contractor. So, project management, quality and safety has kind of been the bread and
butter. And so really any large, you know, schools, hospitals, buildings. Right, you know, roads
and bridges. Right. All of these large construction projects, almost all of them use procore, in
some sense to help manage those projects.
00:07:11:19 - 00:07:35:16
Robert Farr
Manage all the details, all the workers. And we're continuing to then build and expand upon that,
doing more and more what we call workforce management, you know, work, field work
solutions. So when you get to the construction site and you see software on site, you know,
helping and helping those in construction, get the job done and you'll see Procore present there.
00:07:35:19 - 00:07:40:01
Robert Farr
It's amazing. And go ahead. Oh, go ahead, go ahead.
00:07:40:04 - 00:07:50:00
Stefan
I was just going to say so, like when I did the research on Procore the founder. He was a
contractor, right. And then he kind of saw that in the market that there was no tool to help with
this.
00:07:50:03 - 00:08:18:07
Robert Farr
Yeah, yeah. To, you know, to me and this is what's for me was interesting. Right? Because
when you see, founder led startups, there's a lot of passion that goes with that. And that Tooey.
He saw a problem in the construction industry. And, you know, took that opportunity to say, let's
go build something different. What's interesting and, and this is, you know, my, my theory on
enterprise SaaS, is it actually takes a long time, a lot longer than you think.
00:08:18:09 - 00:08:46:29
Robert Farr
So Procore had been around 15 to 19 years, I think, before it really before an IPO. And yeah,
and some of that is, you know, you're trying to serve an industry that is not yet quite caught up
to technology adoption. Health care was very similar. I would say it me, you know, led
construction, you kind of see the construction industry really embracing technology.
00:08:47:02 - 00:09:02:25
Robert Farr
And, you know, there's, I think Tooey said of one time he said he was trying to decide, you know,
if it was construction or agriculture. So, you know, maybe someday agriculture would be that
next big wave of, kind of technology innovation and the enterprise side. So that's a great point.
00:09:02:28 - 00:09:12:18
Stefan
Jens. Do you have any questions or points to add to that? I, I read a lot about Tooey journey.
Know that he started off as a contractor. He didn't have a tech background. Right. He was just a
general contractor. And he saw a problem.
00:09:12:19 - 00:09:34:26
Robert Farr
Yeah. Yeah, yeah, he he was, you know, Tooey, you know, as I understand, you know, he was
the guy that came in and he framed everything up right? Like that was his, his trade. But he, you
know, like you said, he saw that it was hard on those in construction, right? Like, it's it's, you
know, for those who who work construction, they know how hard it can be.
00:09:34:28 - 00:09:53:17
Robert Farr
Many times as long hours. It's aggressive timelines. And there's communication is paramount,
right? Like the ability to share information accurately is paramount when you're trying to
coordinate, you know, so many different companies and so many different individuals on a large
and complex, project.
00:09:53:20 - 00:10:10:26
Stefan
You know what's exciting Jens I don't know if you're hearing it, but, we're going to dive into, like,
your experience and what you're building up for. But what you just said was construction like
timelines, communications. You guys are more or less doing the same thing now, but just in the
software space. You're not building hospitals, you're building the software that helps power
those hospitals.
00:10:10:26 - 00:10:30:01
Stefan
So communication is important. The, the deadlines are important. The grid, you know, you're not
lugging around things, but still, there's a lot of stuff that you have to do with that. And so this is a
good segue into, like your role, at Pro Core. So you're a principal architect. What does that
entail? Like what are you tasked with architecting is it the entire Pro Core platform.
00:10:30:05 - 00:10:33:06
Stefan
What are you kind of specifically focusing on?
00:10:33:09 - 00:10:55:01
Robert Farr
Yeah. So I mean, my, my, so my primary focus of Pro Core is, is really, I would say trying to help
us, become a construction, platform. Right. Or a platform for construction on which to build. And
so that that takes me into a number of areas, right. It takes me in to, kind of our, our
infrastructure.
00:10:55:01 - 00:11:18:08
Robert Farr
Right. How do we think about scaling and building and managing, our customers data? It also
takes me into how we build services. You know, especially with all of the changes. So I'm
always trying to stay just a little bit ahead of the curve or enough ahead of the curve that I can
help guide us to where things are evolving.
00:11:18:10 - 00:11:35:12
Robert Farr
And, you know, we'll talk about AI more, here in a bit, but it's probably the biggest shift in, in
software engineering or in a lot of the industry at this point, at least in my career. You know, 20,
25 plus years. But, so I spent a lot of time there and then.
00:11:35:12 - 00:11:55:09
Robert Farr
And then what's the last part of that is really, you know, what are some of those core services,
the core entities, information architecture that makes us up and those kind of those pieces come
together to really say here in Harare, a platform company, you know, here's how we allow it to
be extended here, how we allow our customers to leverage and then build upon it.
00:11:55:11 - 00:11:59:24
Stefan
What? Well said. And I would sometimes I'll go ahead and
00:11:59:26 - 00:12:00:03
Robert Farr
In,
00:12:00:09 - 00:12:31:22
Jens
In a company like Procore, what role do APIs play and, and how does how does the company
high level think about APIs? Like what? Like if you asked the non-technical people in in
leadership, how do they, do they know APIs? Do they think about APIs who how? Yeah. Just
how do how do different stakeholders inside an organization like, like Procore think about APIs?
00:12:31:24 - 00:12:33:14
Stefan
It's a great question. By the way.
00:12:33:16 - 00:12:54:25
Robert Farr
It's it's a it's a great question. I, I'm going to say it, you know, really depends. And that's, that's
where, you know, when you look at how the software was built, how it's evolved over the years.
You know, we do have a very healthy marketplace and API ecosystem. So you can go to
developers, at procore.com.
00:12:54:27 - 00:13:17:06
Robert Farr
you can see that, so there is a component of Pro Core that's very interested in API contracts,
making sure that we can, you know, enable partner integrations and enable our customers
where they need to be. And then there's the other side where I think, you know, were more the
focus is on the application itself.
00:13:17:07 - 00:13:41:01
Robert Farr
Right? So whether that's, you know, building a particular, you know, web based workflow or a
mobile application where the APIs a lot of times I feel like are a secondary concern. Right. They
become a, a need based on trying to satisfy what you're trying to build or provide from a the
application experience.
00:13:41:03 - 00:14:09:03
Robert Farr
So it's kind of depends. Right? It depends on on where, you know, I guess the, the perspective
or context that somebody was in and how much they worry about APIs. I would say, you know,
those that like when we look at our developer ecosystem, it's much more concerning. I, as a
software architect, I generalize it more and to maybe, you know, I mean, APIs, but ultimately
APIs are contracts.
00:14:09:05 - 00:14:39:22
Robert Farr
And in any large software system, I think contracts are paramount. That is where you get
yourself into trouble, really quickly as you scale. And it's it's not a new idea, right? Like, it's, you
know, loose coupling, high cohesion. Right. Like, these are, these are concepts that have been
around for a long, long time. But they're hard to hard to adhere to at scale, especially when
you're going fast and, but ultimately, it's when you have tight coupling and loose cohesion, right?
00:14:39:22 - 00:14:47:03
Robert Farr
You really start to have to, what we say as tech debt or maintenance burden, that, kicks in as a
result as well.
00:14:47:04 - 00:14:58:05
Jens
So it sounds like you would you would not say procore is an API first company.
00:14:58:07 - 00:15:13:24
Robert Farr
I, I would, I would say no, not yet. And, just because that's where I think, you know, historically,
it's been more solution first and then ecosystem second.
00:15:13:26 - 00:15:19:04
Jens
When you say not yet, do you think it should?
00:15:19:06 - 00:15:49:20
Robert Farr
Well, I think I think every company so, and, and that's because of what the change, like I would
say, what AI is doing right to how we build software, what software we build. I think it's going to
reinforce that need for solid API contracts. And so you're going to have to, you know, the first
consumer, right, that that we start thinking about in the future is probably an agent, right?
00:15:49:20 - 00:16:11:04
Robert Farr
An AI agent rather than, you know, an external developer rather than an internal developer
trying to build a, you know, either a mobile or web application. That's kind of the opposite of
what it is today, right? Like, or at least it has been where, you know, I think first we think about
our internal developers and then you think about your external developers.
00:16:11:04 - 00:16:34:27
Robert Farr
And this is not uncommon, I would say, at many companies, and, you know, some get it, you
know, some do it the other way. Right? Like it's it's baked into the DNA of the company.
Sometimes that starts from the top down. But but I'll, you know, you'll see one of those two
orientations, and I think that's going to pivot.
00:16:35:00 - 00:16:35:10
Robert Farr
Yeah.
00:16:35:16 - 00:16:38:12
Jens
That's that's that's very interesting.
00:16:38:14 - 00:16:39:16
Robert Farr
00:16:39:18 - 00:17:20:20
Jens
Before we dive deeper into the into the ecosystem of AI, like, I, I'm for me, the foundation of AI is
APIs, AI or LLMs without data is just a cool model that can, yeah, can come up with whatever
token you ask it to come up. But yeah, how much can it do? Well, one great example, for
example, is if you go to chatGPT deep research, I think deep research is a prime example for
how the future looks like.
00:17:20:22 - 00:17:50:25
Jens
And if you can have something like deep research and you can give it MCP access to all of Pro
Core APIs, even if that's just internal, it doesn't even have to be public. That can be just for
people inside Pro Core. This can be, in a crazy interesting use case because it would allow
someone like a business person to ask a very complex question.
00:17:50:28 - 00:18:37:25
Jens
And then the deep research model can go on the journey of, working for ten minutes, crunching
data from various sources and creating a report. And then this business person, they just. And,
the coffee break, and now the report is ready and fresh. And I think that that is where, where the
industry is heading. But before we go deeper into, into AI, one thing I'm curious about is so we
can talk a little bit about your API stack, the API stack you're you're building currently, you're
building something with, with WunderGraph, with Cosmo, which brings us here.
00:18:37:29 - 00:19:01:00
Jens
But I would also love to hear your your journey. How how do you how do you think about APIs
and how has your opinion of APIs changed over the years? Like how how did you end up with
the mindset where you are today? And then how did that change over the last couple of years?
00:19:01:03 - 00:19:10:04
Robert Farr
Yeah, that's a good question. I would say,
00:19:10:06 - 00:19:42:06
Robert Farr
You know, I've had I've had several experiences with monolithic databases, both at, at Cerner
and at Procore. And so, you know, for me, it started at with what you see is it's very easy for
your table schema. Right. In a, in a monolithic scenario to become the API, right, to become the
contract. And so that really impressed upon me early the need for proper, you know, API
encapsulation.
00:19:42:09 - 00:20:05:20
Robert Farr
Because otherwise it's very hard to evolve. Right. Like it, it, one trade off you make when you
define contracts or you define APIs is, is you sign up for, you know, passivity and, you know,
thinking about the impact of API change on your customers or the customers or those APIs. And
so there's there's a higher level of responsibility there.
00:20:05:20 - 00:20:30:09
Robert Farr
You're right. You don't you just can't change it, or break it, willy nilly, so to speak, your internal
details. Right. You have a lot of flexibility to refactor that, to evolve it. Much more so, right, than
your, your external API contracts. So that really kind of I would say set, this set up, the kind of
rule system in my mind of like, okay, let's make sure these are important.
00:20:30:09 - 00:20:57:00
Robert Farr
They, they weren't the extra time to try to make sure your, your you're going to do them right or
doing well. They're they're never. All right. There's something I've learned over the years, so that
that kind of frames that, you know, I think other things, you know, we've seen, you know, just,
you know, the advent of, of REST, right, and REST APIs.
00:20:57:00 - 00:21:20:19
Robert Farr
And what's interesting, I watch that evolution. And there's this tension. Right. I would say in , you
know, when you're trying to define contracts, you're trying to find certain patterns or styles, even
in rest. So, you know, hey, those very few things actually adhere to it. Well, right. Or perfectly.
And that's because there, you know, pragmatism comes in.
00:21:20:19 - 00:21:43:13
Robert Farr
But also it's hard, right? It's hard to, consistently, you know, approach some of those standards.
In a, in a way that then also is, you know, is it useful to the consumer. Right. What's the impact
on the consumer of those APIs. And so that's the other friction, I think I, you know, really, you
know, comes to mind, right?
00:21:43:13 - 00:22:12:05
Robert Farr
Is I think about contracts, I'm thinking about like, how do we how do we deal with that kind of
governance problem or the, consistency problem at scale. You know, when you start, it's not like
there's one engineer, right? Or one person that goes and defines the API for everything. And
you see this in other industries anywhere where, like, you know, health care, there's HL7,
standards body and there's an immense amount of hours and people that that are involved in
making those standards.
00:22:12:05 - 00:22:41:11
Robert Farr
And it takes a long time to change them. Right. There's a lot of discussion that goes into it. And
then and then it's not necessarily the easiest thing to write, to go, adhere to consistently. And
even, you know, in health care, you know, we always found just because there was HL7, you
would still find differences between providers of that API, whether that was Cerner or, you know,
epic or one of our, kind of competing, health care solutions.
00:22:41:13 - 00:22:46:23
Robert Farr
The same API. They wouldn't quite behave the same.
00:22:46:25 - 00:22:51:09
Robert Farr
So for,
00:22:51:11 - 00:22:56:07
Stefan
I see you thinking Jens he’s thinking. What's the follow up question there?
00:22:56:09 - 00:22:58:14
Jens
I'm processing.
00:22:58:16 - 00:22:59:22
Robert Farr
Yeah, yeah.
00:22:59:24 - 00:23:02:15
Jens
I need to split the tokens, but.
00:23:02:17 - 00:23:04:00
Robert Farr
00:23:04:02 - 00:23:11:04
Jens
What what what do you think is the is the best API style?
00:23:11:06 - 00:23:20:12
Robert Farr
The best API style?
00:23:20:14 - 00:23:31:24
Robert Farr
Well. And, maybe maybe I don't, What do you mean by style? Are you thinking just in terms of,
like, approach to how you.
00:23:31:26 - 00:23:33:09
Jens
RPC style.
00:23:33:12 - 00:23:35:12
Robert Farr
RPC or Rest? Okay, okay.
00:23:35:13 - 00:23:39:01
Stefan
RESTful query Style?
00:23:39:06 - 00:24:13:25
Robert Farr
Yeah. So to be honest, you know, I find RPC to be probably the simplest, most straightforward.
But it also has, right challenges of bloat and maintenance. At times I think that was something
that, you know, rest, Rest style APIs tried to simplify, right? You know, the hope was you have
resources with a few operations and a lot of things you could do, on the other end.
00:24:13:25 - 00:24:37:05
Robert Farr
So that's kind of two ends of the spectrum. You know, the way I think about it, but I find, like, as
a consumer, RPC is a lot easier to, to reason about. Right. Take this action. I understand what
the you know, here's a response that tells me what it did. And if you think about, you know, what
kind of changes, right.
00:24:37:05 - 00:25:01:15
Robert Farr
What kind of changes do we make to state, you know, your basic Crud operations, they're
they're there, but they're really changing information. But the moment that you start getting into
what I'll say are the kind of the, the logical changes of state, you know, statuses and, you know,
you know, maybe, evolving something from published, you know, from draft to published.
00:25:01:17 - 00:25:22:11
Robert Farr
That's where RPC really kicks in, right? And rest, it starts to get kind of, funky or you'll see
people kind of move away from rest and they'll add these, you know, you know, my resource
slash publish, right? Which is not a RESTful API, at least in terms of Http, but becomes more
RPC like, over time.
00:25:22:11 - 00:25:45:19
Robert Farr
I'm, I'm usually and, you know, you know, think about the consumer of the API. Right. And so
sometimes it's a, you know, right. Like the basic Rest stuff is exactly what they need. And
sometimes you need more of that RPC style of API, because at the end of the day, it's your
consumer that kind of drives the contract you really should be providing.
00:25:45:21 - 00:26:11:17
Robert Farr
If you're not satisfying, you know, kind of what they need, then you're really you're just creating
friction, right? You're creating, friction for them. You're creating adoption friction if you're trying
to, you know, create more value, with the service you're building. And so you've got to be
pragmatic. So I guess at the end of the day, I'll say I favor whatever works, but, but I probably
think RPC is a little simpler.
00:26:11:19 - 00:26:16:19
Stefan
What about you Jens what's your favorite API style?
00:26:16:22 - 00:26:18:21
Robert Farr
00:26:18:24 - 00:26:52:10
Jens
So if we go through all of them, I, I personally think hypermedia is the, the smartest style ever
invented, which nobody really understands. So, you know, when I heard the first time about
agents and, and how they or llms how they could use APIs for me, it was immediately clear
hypermedia was built for agents. And do you know how many people use hypermedia for
agents?
00:26:52:10 - 00:27:21:11
Jens
Exactly. Nobody. Because I think nobody ever understood the power of hypermedia, because,
you know, you you go to the landing page of a thing and it returns a hypermedia answer with,
hypertext that tells you this is a shopping cart. Here are things in the shopping cart. If you want
to go to the checkout, send a post, request to the checkout.
00:27:21:13 - 00:27:22:23
Robert Farr
This this is.
00:27:22:25 - 00:27:47:21
Jens
This is so much smarter than MCP. Are we doing it? No, because I think most people don't
understand the intentions of the web. And, so I, I fully agree with you in the sense that and this
is how my how my thinking has evolved over the years. In the beginning, I was, I was, driven by
excellence.
00:27:47:21 - 00:28:34:09
Jens
I was driven by perfection. And I thought the best solutions are the ones that are perfect from a
technical point of view. And what I have learned is the the reality is the best solutions are the
solutions that work for the people who need them. And what you're saying, I think, I would add
one thing you said, RPC, I agree RPC is great and I would add web webhooks because, if you if
you have an integration with something like GitHub and then something happens, you need to
be notified about that and you want to you want to have notifications that are not tied to an open
connection or something that are super
00:28:34:09 - 00:29:02:17
Jens
simple to implement, and nothing is easier to implement than, than uh web hook. So, so I think,
RPC and webhooks are great. And then another opinion I have and happy to to see if you if you
disagree or have another opinion. But one thing I have observed is a lot of companies try to use,
internally, try to use gRPC and REST.
00:29:02:20 - 00:29:34:21
Jens
And I think it's not working well. And I know I'm biased, but I think internally everybody should
have a graph because, the, the, the for me, the, the big advantage of having a graph is you're
not tying a resource to one service because I think the, the, the absolute worst thing you can do
is you can say we have this core entity in our construction, whatever.
00:29:34:24 - 00:30:03:11
Jens
And it has 50 fields and they all must be implemented by one service. And that's just not going
to fly. Because what what you will run into is you will have you know, in in a domain model, you
always have like certain entities that somehow they are correlated to everything, like a user
object or something. And then everybody comes to this user service and says, guys, we need to
integrate with your user service.
00:30:03:11 - 00:30:26:03
Jens
It needs to give us certain things. And then suddenly user service, 50 fields, 100 fields,
whatever. And every time someone wants to somehow evolve the API, they have to add
something to the service. And this is where, where, Federation would, would simply allow you to
say you can add three fields and you put them into another service.
00:30:26:03 - 00:30:51:20
Jens
And that means you're, you're freeing up this one team to that, that owns this. But on the
surface, I think so internally a graph and then to the outside some sort of webhook system. And
I think to the outside there should be an easy way to create SDKs because that's, that's another,
opinion for me that has evolved.
00:30:51:22 - 00:31:23:27
Jens
When I was like a few years ago and I was observing how everything unfolds, I saw that
somehow REST APIs are winning. And I was wondering, is it like are Rest API is really that
good? And kind of what what what crystallized for me is nobody wants REST APIs because they
are also they typically lead to situations of very tough conversations because it's not entirely
clear how you should structure a URL.
00:31:24:00 - 00:32:12:07
Jens
Do you put the version in the in the URL in the header in whatever, and then you can have so
many debates around whether you should design something like this or that. Super simple,
straightforward solution, just RPC, JSON over Http and then yeah, some sort of RPC contract,
wrap it up with SDKs and make it simple for people to to download an SDK and have like, type
safe integration, which also I think in the, in the age of AI if I want to integrate with Pro Core,
give me an SDK, give me documentation how the SDK works, and I can tell Curser to vibe code
whatever we need because it can just call these
00:32:12:07 - 00:32:32:16
Jens
functions and it's clear what they return. And then I think yeah, for, for, for those reasons. So
yeah, my, my opinion internally you should have a graph. You should have to the outside you
should have a webhook system, JSON, RPC, SDKs. What's your take.
00:32:32:19 - 00:33:00:20
Robert Farr
Yeah. So I might my might be a little bit more nuanced. And I would actually argue that, most
companies want a graph. Now, I'll be very, very careful here to say I'm going to separate
GraphQL from graph. Think of graph in terms of the data. And this is one of the reasons why I
think about our information architecture at Pro Core so much.
00:33:00:22 - 00:33:24:28
Robert Farr
Fundamentally, you want to understand all the connections of the data, be able to navigate
through them. So you want a graph, and if you think about hypermedia, one of the intents of
hypermedia was I always thought about hypermedia as a way to expose that graph to a
consumer. Right. Because your you hit a URL, but then you also get linkages to all of these
other things from that point.
