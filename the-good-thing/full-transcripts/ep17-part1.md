Episode 17
type: podcast-chunk
00:00:22:17 - 00:00:31:05
Stefan
You.
00:00:31:07 - 00:00:51:13
Stefan
And we're back. Welcome back, ladies and gentlemen, to another episode of the. Good Thing.
You might notice I'm not in my usual studio today, and this is actually a recording reason why I'm
actually out this Friday heading to a funeral. So I will be out this Friday. But we wanted to stay
consistent and make sure that you guys get your daily or your weekly viewage of the good thing.
00:00:51:13 - 00:00:55:07
Stefan
Jens, as always, good to see you. How you doing today?
00:00:55:09 - 00:00:57:04
Jens
I'm good.
00:00:57:07 - 00:01:00:24
Stefan
Typical German response. Not bad. I'm good. It's same.
00:01:00:27 - 00:01:03:04
Jens
Every Week.
00:01:03:07 - 00:01:25:03
Stefan
That's awesome. Well, thanks for joining us. Today we're going to be talking about what we call
Conway's law and just kind of going I want to say, like, off script. We don't have a strict agenda
today, but I kind of wanted to talk about organizations, what we're seeing with the rise of AI, just
kind of how companies are adopting AI, where we're going with AI and just kind of like API's and
how it fits into that space.
00:01:25:06 - 00:01:41:22
Stefan
And the first topic I wanted to talk about is, Conway's Law. This is a law that I learned about
when I started at WunderGraph. But it's one of those things and I'll give you like a story is, I'll
forget. Like when I was in college, I didn't understand recursion. I couldn't understand it. I
couldn't, like, figure it out.
00:01:42:00 - 00:01:59:24
Stefan
And for the longest time, like the exam was coming up and I was scared. I was like, I don't
understand recursion. I don't know, understand why anybody would use it. And, this was a
solution to a problem. And what I realized quickly was I couldn't figure it out. There's no way,
there's no way. I spent hours in the lab trying to figure it out.
00:01:59:24 - 00:02:15:08
Stefan
It didn't make sense to me, but when the tests came, they gave me a problem. And I was like,
okay, well, to get to the solution in this problem, which if I go four steps this way and then to the
right, and then just keep kind of doing that, and then it just kind of clicked right there is what I
was doing was recursion.
00:02:15:08 - 00:02:38:03
Stefan
And so because I had an actual problem and I had the solution in my brain or in my toolbox, it
clicked in my head. And what I'm trying to get at is I didn't get Conway's law in the beginning. I
didn't understand it. But now when we work with these enterprises and we talk to them and we
learn about their tech specs and their architectures, and then we actually talk to their teams, I'm
like, holy crap.
00:02:38:03 - 00:02:59:24
Stefan
Like, this is Conway's law at play. And so I want to talk about today of what we have been
seeing with Conway's Law. And this is a very simple paraphrased version of Conway's Law. But
basically, the structure of your software will mirror the structure of the organization that built it,
which I think is super fantastic. And like it's kind of cool how we figured this out, but it totally
makes sense.
00:02:59:25 - 00:03:07:23
Stefan
I'll pause there. Jens, though like, what have you seen lately on Conway's Law? And just I
mean, we talk about it all the time, but why is it important?
00:03:07:25 - 00:03:17:13
Jens
Maybe before we talk about that, I'm curious what what what observations have you made
talking to to to customers.
00:03:17:15 - 00:03:39:25
Stefan
Well it's cool. So like, for example, us, we're a single monolith, one monorepo. And that's how
we work. Everybody works to the same contributing. And then with our customers, what we'll
see is that they'll either be one large team working together with a monolith. And what's quickly
you realize there is they want to take that monolith and they want to break it apart.
00:03:39:27 - 00:04:01:08
Stefan
And the reasoning isn't actually the software, it's what's happening inside the organization.
We're moving too slow. We're stepping on each other's toes. It's just getting too big. We're cut.
We're company. And what you realize quickly with these companies that go from monolith to
federated architecture is that they started off small, which is great, but they grew very fast.
00:04:01:10 - 00:04:17:25
Stefan
For example, we have a construction company that grew from zero to IPO in about six years.
And what they've quickly realized is we've built this huge legacy. We're one big team, but we're
so slow we cannot be slow. And so what we're looking at is a federated architecture to break it
apart. And that's where federation comes in handy.
00:04:18:01 - 00:04:38:06
Stefan
And then we also see is these small distributed teams that kind of started out from the
beginning. It might have been a little bit of a hurdle at first. A lot of times you tell people you're
too small for Federation, but for them it ended up working and they kind of have this modular
type where different teams own different services and they all work together, work together.
00:04:38:08 - 00:04:54:21
Stefan
But it's kind of what we're seeing within the companies is that if you remove the software and
you don't actually talk about the software, just look into the teams and ask them like, okay, how
are you working together with team A, B and C, or are you guys just one team? How do you
push code? How do you collaborate with those teams?
00:04:54:24 - 00:05:10:20
Stefan
And I think that this Conway's Law, it's it's more about the teams than even about the software.
You can always figure out what software they're using or like what architecture that they have by
just talking to them and how they interact with each other. So that's kind of what I've been
seeing. What about you?
00:05:10:23 - 00:05:30:14
Jens
I think when I was first introduced to Conway's Law, there was an like an example. Let's say
you, you have two teams and they, they want to build a compiler. Well, what do you think? How
many steps will the compiler have?
00:05:30:17 - 00:05:34:29
Stefan
How many steps? If it's two teams, how many.
00:05:35:02 - 00:05:36:26
Jens
Get.
00:05:36:28 - 00:05:38:16
Stefan
Ten steps?
00:05:38:19 - 00:06:03:18
Jens
You said the number before. So yes. So and that's that's the interesting part. So at the very
beginning I didn't really understand what is the meaning. You know, I didn't have so much
experience yet and like, okay. Yeah, it's interesting two teams build a compiler, a compiler has
two steps. But but what does it mean?
00:06:03:20 - 00:06:33:28
Jens
And in reality, what I would say one, one pattern I learned in software development is, code that
changes together. It should be very close. And code that, doesn't change together. It should be
like further away. So for example, code that changes together all the time. It could be in a
package. It could also be in a function.
00:06:33:28 - 00:07:03:13
Jens
So the closer the code is together, the easier it is to change it together. For example, if you look
at our architecture, you can kind of see that we have somehow two teams, not one, but the two
we have, we have graphQL Go tools. We have the engine and we have the router. And you can
see there is a clear line between what does the engine do and what does the router do.
00:07:03:13 - 00:07:34:02
Jens
And so some modules you will see or some functionality. We do it in the router, some
functionality. We do it in the in the federation layer. And so yeah you kind of can see how the
way we shaped our organization, the way we kind of even if it wasn't really like a real split, but
somehow it was kind of a split in terms of communication because our engine team, it was
always a little bit like on the side.
00:07:34:05 - 00:08:06:02
Jens
And yeah, I think you can you can see that also in the, in the architectures. And then if, if you
look at our customers, I think one, one very interesting observation is, you can see the structure
of the architecture they built. You can see it in communication patterns. You can see it in, in
which people join on a, on a meeting, how they work together, how they, how they
communicate.
00:08:06:04 - 00:08:31:14
Jens
And, I think it's it's a very interesting problem. And also one observation we made is that
different API styles have an influence on, on how you can deal with Conway's Law. But before
we dive into that, I, I pause and maybe you have some, some other thoughts or, or questions.
00:08:31:16 - 00:08:57:15
Stefan
Well it's interesting. Like you say, it's a problem, and I know it's a problem. We can see it's a
problem with the companies that we work with. But like what what would be a good organization
structure where you wouldn't run into this problem because it just simply mirrors how you guys
communicate. And like, obviously the answer is with APIs and just having a good structure and
being able to communicate across teams with APIs.
00:08:57:15 - 00:09:05:28
Stefan
But have you seen from one of our customers maybe a good structure, that they have an
organizational structure that tends to work for them?
00:09:06:00 - 00:09:33:16
Jens
I wouldn't say per se, Conway's law is a problem. It's is more like, yeah, it, it it's it's more like the
reality. And so the, the question is, does your workflow fit this reality? For example, if you want
to make, let's say you, you build an app where people can, can book like, a limousine service or
something.
00:09:33:18 - 00:09:59:02
Jens
And let's say to add one single button to this front-end application, you have to make changes in
seven different places in seven different systems. And they are all like super complex. And you
have to talk to different people and whatnot. At this point, the question is, have we built a system
that prevents our engineers from making changes?
00:09:59:08 - 00:10:29:03
Jens
Because obviously you want to change your button, but if you have to change multiple systems
that are all over, does this code structure, does it support us in making changes to to this code
base? And, yeah, I think this is this is very tough. And you need, a lot of knowledge and seniority
to, to make changes in such a code base versus.
00:10:29:05 - 00:11:01:07
Jens
And this is something I think a lot of people, they, they got tricked a little bit into, into following
microservice patterns or trying to adopt modern patterns. For example, I would say one, one of
the biggest anti-patterns you can establish in, in, in service architecture is you have one single
team and you're, oh, you're thinking and let's say you were five developers and you're thinking,
microservices seems modern.
00:11:01:09 - 00:11:30:23
Jens
Let's build a microservice architecture and split out certain functionality into a separate service,
because we want to make it scalable or something. And yeah, I mean, there's many stories of
companies that have used something like Ruby on Rails, for example, GitHub. And they scaled
very, very, very well. So there's a lot of these stories where people will be like, oh yeah, we have
a monolith.
00:11:30:23 - 00:12:02:24
Jens
It's scaled to a certain degree, like now we have some problems, but it it scaled really well for
us. There's very few stories of companies that say, oh, our company completely messed up.
Like, we, we went bankrupt because of our monolith. I have never heard such a story, but there
will be many stories where people say, well, we we we messed it up with complexity and now
our microservices architecture is too hard.
00:12:02:26 - 00:12:29:13
Jens
Because the point is, if you are a single team, five devs, why do you need to split anything into
another service? Why can't you just focus on solving the problem? And solving the problem
typically means just create a boring monolith, solve the problem, move forward. For example, in
in in our architecture we have Cosmo, we have one backend.
00:12:29:13 - 00:12:55:12
Jens
It's called control plane. And it's one backend and it's it's okay. We have like an RPC contract,
this RPC contract, it's it's we use buf connect to implement this. And it can be called from our
front end. And it can be called from the CLI. And that's okay. We can generate clients and go in
TypeScript and we call it a day and that's it.
00:12:55:14 - 00:13:09:19
Stefan
Question though. Have you ever worked or seen a company that started with the microservice
architecture and it was success was successful? Or maybe we read about a blog where they
from the beginning, they started with the microservice architecture and it was successful.
00:13:09:21 - 00:13:15:25
Jens
So I did that in the past, and the project was killed.
00:13:15:27 - 00:13:35:24
Stefan
So I don't know if you would say that was a success, but I mean, it's interesting, like I hear it all
the time, we'll talk with people and they're like, oh, we're we're preparing for scale. And it's like,
why don't you hit scale first and then deal with the problems that come from it?
00:13:35:26 - 00:14:25:04
Jens
I mean, I can speak for myself, if you are, I don't know if every engineer has this journey. But for
me, I made a I mean, you you know me quite well over the years, and I made a huge journey
from being obsessed about tech to. So that was my past. And now being obsessed about
solving problems and figuring out how, how much deeper can we go in the problem space and
what else can we do for for customers and, I kind of transitioned from thinking so much about
tech and more thinking about what can we enable, what what can we achieve together with our
with our customers?
00:14:25:06 - 00:14:51:25
Jens
Nowadays I find it more interesting to, to building like a great product and to solving the hard
problems for our customers. Not so much. How do we do it? Like which tech? But yeah, I guess
like a big problem some developers have like me in the past is we read these blog posts from
Netflix and whatnot, and then we're like, oh, I also want to be like an engineer from Netflix.
00:14:51:28 - 00:15:20:23
Jens
I also want to use Kubernetes. I also want to use go and microservices, and I want to use
GraphQL and Federation and Relay. And yeah, I, I don't know, maybe it's a little bit of, of resumé
driven development. Maybe it's a little bit about about hype. Maybe it's anxiety. Like you need to
stay up to date with the stack or something.
00:15:20:25 - 00:15:43:19
Jens
I think that can be they can be many reasons, but I would say if you want to make a successful
career in tech and you're an engineer, I think the the, the engineers who make the most money,
those are people who understand the, the root of the problem. They understand the the
business behind the code. Not just the code, not just the tech.
00:15:43:19 - 00:16:11:13
Jens
They understand the customer. And I think they are getting closer and closer to the to the
customer. The you know, there's a distinction for me between someone who writes code and
someone who solves customer problems. It can be the same person solving customer
problems. It can mean to write code, but you're you shouldn't writing code or creating
architecture or building services.
00:16:11:13 - 00:16:36:15
Jens
It shouldn't be your one hammer and then you want to hammer it everywhere. You should be
more focus on okay, what what does the customer really need? How can we solve it and tech
tech is do you know in it's funny how I go from one to the next, but do you know in in when you
go to, to car design there's a, there's a saying like form follows function.
00:16:36:18 - 00:17:10:04
Jens
I know it's not what, what people like who who do art and stuff, but sometimes it's, it's just easier
to to think about the, the problem and then you derive the solution and you're on and going like,
oh, we're building a new thing. Let's create microservices. What what problem are we solving.
Are you really focusing on the problem or or are you prematurely scaling because you're like,
yeah.
00:17:10:06 - 00:17:30:15
Stefan
You had a couple good points there. And last week, somebody posted on, Hacker News. They
posted a screenshot of when they announced cursor, and the top comment was a developer
saying, I don't understand why this is x, y, z, I just did this is just a fork of VS code. This is VC
bs, oh no, it wasn't cursor.
00:17:30:15 - 00:17:56:15
Stefan
It was, Windsurf. And then somebody posted it on Twitter and was like windsurf acquired for $3
billion and I posted a comment which was like, I've noticed that developers get obsessed with
the technology and not actually solving about the problem, which is true because they focus
more on the technical implementations. Like, sure, windsurf is more or less not a super
impressive piece of technology, but what it did is it solve the problem, and it solved it pretty well,
and I solved it pretty quick.
00:17:56:18 - 00:18:14:27
Stefan
And I think you're spot on. And if you remember the Dropbox example, do you remember when
he announced Dropbox and developers started ripping into it? They were like, oh, this is this,
this isn't bad. Like, that's not super impressive because they were just talking about the tech,
but they were not solving what the problem is that now you can transfer files into the cloud with
the click of a button.
00:18:15:00 - 00:18:40:13
Stefan
And I think what you said is the nail on the head. It's resumé driven development. They want to
say that I've built this with Kubernetes. I've added microservices and things like that, I don't
know. For me it's cool. I've always seen coding as just a tool. It's a means to an end. Coding
isn't anything else but a tool that helps you solve a problem in terms of programming and
architecture and software, all it is is solving your problem.
00:18:40:13 - 00:18:56:14
Stefan
But you should be obsessed with the problem, not how you get there or the tools that you use.
You know, like carpenters. I mean, you were a carpenter, which is a great example. You liked
building things, but you weren't obsessed with your hammer. You know, you didn't be like
hammer for everything, hammer for everything. And it's like, no, we need to.
00:18:56:17 - 00:19:14:05
Stefan
We need to build the drywall. No hammer. I'm going to use my hammer. And that's the way I see
developers that are obsessed with, you know, like microservice architecture. It's like, oh, I have
this new hammer, it's golden, and it has a different claw or a sledgehammer, and it's going to
solve my problem. And it's like, you. And what did I agree to that?
00:19:14:06 - 00:19:16:25
Stefan
What do you think?
00:19:16:27 - 00:19:56:21
Jens
Yeah. Like you can be super obsessed about how you build dry walls. And you can you can
have your, like your craziest set up and tooling and whatnot to, to do dry walls. And then the, the
customer, they will take the drywall. They will they will paint it whatever. They will not care about
your drywall. They, they just want a drywall and yeah, this is this is another interesting point
because, another observation I made about myself, but also other developers.
00:19:56:21 - 00:20:22:04
Jens
And, by the way, I'm, I'm not ranting about developers. I also have a lot of empathy for for
resumé driven development because, as a developer, you always have this this. I don't know if
you had this, you were a developer also for a time, but I always felt a little bit like an imposter.
You know, I, I always felt like, I don't know, there's people they know so much more like, I need
to learn faster.
00:20:22:04 - 00:21:06:02
Jens
I need to to understand more. I so I think imposter syndrome, it's a, it's a real thing as a, as a
developer and yeah, you can, you can really have anxiety that you're not able to catch up or
something. So, I think, yeah, there is something to, to just trying out new, new things and stuff.
But I would also say it's, it's a thing of experience and one observation is that over the last
couple of years, I feel like on, on one hand, software development became increasingly more
complex, like the tools we have today.
00:21:06:04 - 00:21:34:22
Jens
They're just so much more complex than what you had in the past. You know, when I learned
programing, you would have a PHP file and Apache server or Engine X, and you would upload
your PHP file with FTP, and then you have a website. And that was okay. That, that, that was it,
that and, and maybe had you had a MySQL database.
00:21:34:24 - 00:22:04:24
Jens
And today look at our stack frontend, we have Next.js. Then we have keycloak for federated
authentication. In the backend we have Node.js. For the database we have Postgres for
caching. We have Redis for analytics we have clickhouse. Then we have opentelemetry for
telemetry and tracing and metrics and like holy shit it's it's it's so complex. This is one part.
00:22:04:26 - 00:22:37:18
Jens
So you have a lot to learn to understand this modern stack. And then the second part is, last
couple of years, like last ten years, there was like a huge influx of new developers. There's huge
demand for for developers. And what this results in is that if you have demand for developers
and on such a steep trajectory, what it means is that the majority of developers, they actually
have like below 2 or 3 years of experience.
00:22:37:21 - 00:23:08:21
Jens
So I think we are now at a at a time where, where the majority of developers, they are not
seniors. And so combining these two, a lot of not seniors, a lot of junior or mid-level people with
not so much experience, then you have this ever increasing complexity of of the stack of the
web, and now you combine it with AI and whatnot and vibe coding.
00:23:08:21 - 00:23:47:02
Jens
And now everybody has anxiety and what is what is next. And, you know, you now have this
new generation of, of of junior deaths. You give them cursor, they vibe code something together.
They don't even see that it's broken or that there are security vulnerabilities. They have never
done it by hand. And this is something, you know, I, I think it's it's it's something good about
when you do an apprenticeship as a, as a carpenter, you know, we, we have machines to, to do
carpentry.
00:23:47:04 - 00:24:06:09
Jens
And you can automate many of the steps, and there's like super cool tooling. But if you do an
apprenticeship, the first thing you do is you, you do these kind of things by hand. And it takes a
lot of time. And when you mess it up, you have to do it again. And you yeah, you really learn the,
the details.
00:24:06:09 - 00:24:13:27
Jens
And that might be something in software development that we're, that we're lacking a little bit.
00:24:14:00 - 00:24:33:12
Stefan
I want to add to that. Like if you remember pre-COVID like engineering was up and coming like
not up and coming, but like we were hiring like crazy. And then COVID hit and the number of
engineers being hired was like crazy. Companies like zoom, Cammy, all these companies
exploded hiring engineers. And one unique thing came out of it, which was bootcamps.
00:24:33:15 - 00:24:54:13
Stefan
These bootcamps were exploding people. Everybody was becoming a developer because as
soon as you graduate, you get a job for 200 K somewhere in the Bay area. And it was insane.
And there was basically like this gold rush of developers. And the point that I'm getting at is if
you look now, bootcamps are dying, and the reason that they were dying is because they were
just like a mill.
00:24:54:13 - 00:25:14:25
Stefan
They were taking in developers give them flask and a little bit of a database and some
experience, and then they would send them out into the world. And it's what you said they were
very junior developers, and the reason that they're dying now is because if you give a person
with a little bit of technical knowledge cursor, you're getting the same output that you get from
one of these bootcamps.
00:25:14:25 - 00:25:36:12
Stefan
You're getting a very junior engineer that has a lot to learn. And what the bootcamps did really
wrong is they didnt actually give world like real life experience, oh build this to do app with this
database. Okay. Boom, there you go. And you can do the exact same thing with cursor. And so
it's kind of interesting. And we were talking about this today as well is which I like.
00:25:36:14 - 00:25:58:11
Stefan
People are on one side of the fence is that AI is going to make developers 10x faster and better.
Or the other side of the fence is that we're going to replace developers with AI. And I think that's
super interesting, and I don't understand which side of the fence I'm on. Obviously, I'm on the
side of the fence that it's going to make developers stronger and faster and better because
you're always going to need good people, good technologists.
00:25:58:11 - 00:26:23:08
Stefan
It's like what you said is imposter syndrome is a very real thing with developers because
engineering is one of the only careers where you have to constantly relearn everything, like for
example, doctors, they go, they finish medical school, and then they have continuing education
every two years where they go and they just get up to update practices. And the thing about the
medical field is a lot of the stuff doesn't change for ten, 15, 20 years or it never changes.
00:26:23:08 - 00:26:46:18
Stefan
Like you're still doing stitches the same way that they were doing them in the 70s. And that's
totally fine with technology. If you were a developer in 1997 and now your world has completely
changed completely changed. Like, and what's cool about technology? Somebody wrote this, I
forgot what book. But every 17 years, technology, like everything that you know about
technology, is completely wiped away.
00:26:46:18 - 00:27:06:07
Stefan
Like back down to what you said, you know, you had FTP, you could write a file and boom, that's
a website. Back in the 90s, if you knew how to run servers and machines, you were an anomaly.
You could build things. Now you don't even need to understand how the cloud works. You could
just tell ChatGPT, hey, help me connect this with AWS and boom, you have something running
on the cloud.
00:27:06:07 - 00:27:22:08
Stefan
And I think you're absolutely right. But with this transition, what do you think about that fence
with AI being introduced and cursor and all these tools? What do you think is going to happen to
developers? Are they going to get stronger or are they going to get worse? Or are they going to
become obsolete?
00:27:22:10 - 00:28:02:07
Jens
Yeah, that that's a great question. I mean, I'm, I'm biased. I'm, I'm a developer myself. But I
would say maybe maybe I'm naive, but. So you have two options. You replace developers with
AI. So that means you can achieve the same goal but with less resources. So your your more
efficient. But the the outcome is still the same or you have the same resources and you, you
accelerate your you increase your outcome.
00:28:02:10 - 00:28:59:08
Jens
So I would say if you can increase your outcome with AI, it means you can release faster, you
can release better, you can release more. So that means you will learn faster. You will get more
experience into the market faster. So ultimately I think that will compound. And people who
replace developers with AI, I think they will slow down because the, the they, they kind of have
like a flat going function or a function that goes slightly down, even though they are more
efficient, but they are on the, on the, on the dying slope versus I think the, the companies who
will who will, who will keep their, the developers give them.
00:28:59:08 - 00:29:14:04
Jens
AI or keep the right developers who understand AI, I think they will be more like on the
exponential function. So you know, there was this old saying like software is eating the world
and I'm wondering company
00:29:14:04 - 00:29:14:28
Stefan
Right?
00:29:15:00 - 00:29:56:16
Jens
Yes. Companies with the right mindset, with the right engineers, with with AI, I think they can
accelerate even more and by the way, I, I kind of have developed an opinion that when we now
interview people, I ask them how they think about AI and if they are against using AI on the job. I
see it as a red flag because I think, like nobody should be vie coding or just like, I don't know,
like use AI to do random stuff.
00:29:56:16 - 00:30:28:18
Jens
But I can give you an example how how I used AI today. So I wanted to write an RFC for a new
feature, and I knew based on my domain knowledge, there are like seven links that point to our
GitHub repository, to our docs, to some other documents, to our, to, to some code examples.
And so I compiled a list of, of, links to research.
00:30:28:21 - 00:30:57:26
Jens
I added a bunch of, of, requirements for my RFC. And I didn't intend to use AI to write the RFC. I
just wanted the AI to do the research and to give me ideas. So I go to chatGPT and I go to the
deep research mode. I give it the links, some prompts. So I and I actually invested like ten
minutes into really articulating what I'm looking for.
