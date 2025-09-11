Episode 16
00:00:12:22 - 00:00:22:06
Stefan
You.
00:00:22:08 - 00:00:44:22
Stefan
Good morning, ladies and gentlemen. Welcome back to another episode of The Good Thing. I'm
joined by my co-host Jens, as always. And today we actually have what I am probably going to
say. My most excited episode, especially because of what's been going on in the news with
Redi's just open source in general, and I just listen to a podcast from an Epic Games founder,
which kind of goes into about distribution and licensing.
00:00:44:24 - 00:00:48:13
Stefan
But Jens, how are you doing today?
00:00:48:16 - 00:00:55:18
Jens
It's the first day where I switched on my my, cooling. Oh.
00:00:55:20 - 00:01:08:02
Stefan
Yeah. Yeah, yeah. I mean, you guys got spring. It's getting hot over there. So. Yeah, I could tell
Summer is coming to Germany. That's crazy. Because, you know, in Florida year round, we're
always wearing like we always have the AC here on.
00:01:08:04 - 00:01:13:08
Jens
Yeah. So yeah, it's getting hot today.
00:01:13:10 - 00:01:20:03
Stefan
I think today's also going to be a hot topic too. We got some spicy takes. We'll talk a little bit
about open source. I'm really excited.
00:01:20:05 - 00:01:23:20
Jens
Yeah. So you mentioned the podcast.
00:01:23:22 - 00:01:43:07
Stefan
Yeah I mean we can go into but today the topics we're going to be discussing are license lovers,
dual licensing and open core trademark and branding, commercial community. And just kind of
the strategy around a question that somebody asked us was, hey, what's if somebody forks an
open source is Cosmo? Or like, what's if somebody makes a copy of Cosmo, what would you
guys do?
00:01:43:09 - 00:02:02:27
Stefan
Well, we can kind of start off with the podcast that I listened to yesterday. So podcast was, from
Lex Friedman, and it was about the founder of, Epic Games. So the creators of Fortnite and
Unreal Engine, and he is himself a billionaire. And what I loved about him, first of all, is he loves
building games like it's his passion.
00:02:02:27 - 00:02:22:04
Stefan
And he just made a lot of success doing it. And one of the things he said was Lex was like,
okay, like you created something so valuable and you made it basically free, which was Unreal
Engine. And he had such a developer mindset because he was like, you see, I love games and I
love building games. And he's like, I wanted to release that to the world.
00:02:22:11 - 00:02:39:19
Stefan
And he's like, what? I realized from the business point of view is that people building on top of
our platform, it only grows further. So the more people that we can have building and using our
software, the more people that know about us, the more people that could purchase our
products, and the more people in collaboration that we get.
00:02:39:21 - 00:02:57:21
Stefan
And I started really thinking about that, and I was like, yeah, like open source is such a fantastic
way to just get mass volume. And if you think of video game, you know, editors or people
building games like Unreal Engine comes up as number one and it's because it's free, it's
globally distributed, allows indie gamers to start with it, and it just allows people to expand.
00:02:57:21 - 00:03:16:23
Stefan
They go around with it. It's a really, really powerful tool. And he was so bent. And he also had to
fight leadership. By the way, when they got it a little bit more successful because they wanted to
close the licensing of it, but he wouldn't allow it because his goal was if every single person that
plays video games uses Unreal Engine, they're not using our competitor.
00:03:16:25 - 00:03:21:13
Stefan
But it was fascinating. Do you have any thoughts on that?
00:03:21:16 - 00:03:27:29
Jens
Yeah. It's interesting. by the way, do you have at least some some background music?
00:03:28:01 - 00:03:33:16
Stefan
Yeah, it's my mom's alarm clock. Let me get that. While you discussed because I didn't know if
you're going to hear it.
00:03:33:18 - 00:03:48:03
Jens
Yeah I know we we heard but I think one one part that's that's really interesting is when you
when you said if they use our engine, they are not using our competitors engine. Right.
00:03:48:05 - 00:03:57:11
Stefan
Is what I said. But that's was the biggest point for him was that, hey, if we build something big
enough and everybody uses it, they won't use our competitors.
00:03:57:13 - 00:04:30:14
Jens
Yeah, yeah. I think that that is similar to to a thought we have. So we're not thinking in one year
or two years, we're thinking about, let's say, a ten year horizon. So in ten years from now we we
obviously we as a company, we make a bet. We bet on on we bet on Federation. Not like if you
listen to one of the previous episodes, we're not betting specifically on GraphQL federation.
00:04:30:14 - 00:05:00:12
Jens
We're betting on federation, the idea of federation. And we, we think it can be it can be loosely
coupled with GraphQL, like GraphQL can be there. But it can be like any federation, like API
federation. But yes, if we're thinking long term, we're like, okay, in ten years from now,
everybody should be using Cosmo. Everybody should be using our federation.
00:05:00:15 - 00:05:34:27
Jens
If we make it somehow hard for companies to adopt it, that's not going to happen. And, from my
previous job, I worked together with very, very large banks, and I worked together with with
other companies where I knew how they, how they work with, with open source, also Faang
companies. And what I learned is if you put certain licenses on your, on your software, then
they, they cannot adopt it, they cannot use it.
00:05:35:00 - 00:06:11:27
Jens
So imagine federation wins in the long term. So that that goes through. But we made some dual
license bullshit or whatever. And so what a Faang company could now do is they could fork
Cosmo or fork Federation, fork Apollo or build their own, for example, Netflix, because of the
behavior of Apollo, has built their own Federation Gateway. And, well, I don't know the the
internals allegedly.
00:06:11:29 - 00:06:33:00
Jens
I cannot speak about the the internals. I can only speak about like, hear say and, you know, but,
Netflix is very big on the, on the Java virtual machine, so, so it made sense for them to, to build
their own gateway. But now you could ask yourself, okay, why didn't they adopt the, the rust
router from Apollo?
00:06:33:00 - 00:07:06:06
Jens
Shouldn't it be the most performant one? Yeah. The the answer is probably somewhere in the
area of. Yeah, maybe they couldn't use rust in the in the company. But you could also ask
yourself, why would Netflix invest their developer time to build their own gateway on top of the
JVM when there's a standard already? And you could also think about, okay, maybe it's it's
actually about the licenses, which is also a likelihood.
00:07:06:09 - 00:07:32:17
Jens
And so to summarize this licensing topic, if we are betting on federation and if we're betting long
term, we don't want companies like Netflix to build their own. And then we have an, an
ecosystem, where everybody has their own thing. But rather we want to be the standard. So I
think the, the only way to get there is by building, by becoming the standard.
00:07:32:17 - 00:07:39:07
Jens
So it, it must be on a liberal license.
00:07:39:09 - 00:08:09:11
Stefan
I agree, but one question that I was thinking about during the podcast is like being the standard.
Okay, so like Epic Games, like Unreal Engine, like if you're an indie developer, that's the
standard. But let's take Salesforce for example. So Salesforce is not open source, but they are
the standard CRM. Do you think it was because of the timing where they just completely just
grew really fast, or their literal Salesforce and getting into companies early on and just growing
or like, how are they the standard, the CRM, but they're proprietary software.
00:08:09:11 - 00:08:17:04
Stefan
What's the balance between being the standard proprietary and being the standard and open
source? Does that make sense?
00:08:17:06 - 00:08:38:03
Jens
I would say one one big difference here is, is, what what kind of solution are we talking about?
For example, Federation. We, we, we have this in the category of, of it's a platform tool. It's a
tool to build a platform like an API gateway, like a proxy like Kubernetes. You I wouldn't compare
us to a Salesforce.
00:08:38:03 - 00:09:05:22
Jens
I would more, compare us to, to like for example, do you think Kubernetes would have been a
success if it was closed source? Kubernetes? You can now, you know, you can now build a
Kubernetes cluster in Azure, GCP, AWS and some smaller players. So there is a standard. How
was it possible the the big players worked together.
00:09:05:22 - 00:09:15:11
Jens
They, they collaborated and they it's a standard. This would have never happened if it wasn't
open source.
00:09:15:13 - 00:09:35:24
Stefan
It's true. So what I'm seeing also what I kind of can imply, like the best developer tool facing
companies, they kind of have to be or at least start in open source, because with development,
you if it's open source, you invite the collaboration. But I feel like if you really, truly want to be a
successful dev tool company.
00:09:35:26 - 00:09:42:05
Stefan
You have to be open source. What do you think about that?
00:09:42:08 - 00:10:11:09
Jens
Yeah, it it depends. And it's hard. For example, we we talked to the investors of, of engine X or
engines or how do you call them enginex. Enginex. Okay. So we talked to them and, and there
was this time where so next open source and then they, they added like, I don't know, engine X
Pro or something with advanced features.
00:10:11:12 - 00:10:45:07
Jens
And nobody wanted to adopt it. But they didn't change the license. They just added another
enterprise tool. Adoption wasn't great, but what it what it did this it created room for alternative
players to create like API gateways that are open source. And for example, one one company I
worked for, before creating wundergraph, is Tyk analogies, who have an API gateway.
00:10:45:09 - 00:11:09:08
Jens
And I think one one decision they made was was very good is they had the open source
gateway, which was just the gateway. But if you wanted to run multiple gateways in a cluster or,
or something like that, then, yeah, you had to had like a dashboard, like a management
component. And this was just closed source from the very beginning.
00:11:09:08 - 00:11:33:21
Jens
There was no discussion around it. And I personally, I have no strong opinion whether a
company should make something closed source or open source. I would rather say, make it
open source if you have a long term plan and understanding of what that means and make it
closed source for the same reasons.
00:11:33:23 - 00:11:48:26
Stefan
It's all said. And what's interesting is I think you're going to laugh at this, but in your mind
actually just in general is I know the answer, but is open source free?
00:11:48:28 - 00:11:51:02
Jens
That's a stupid question.
00:11:51:04 - 00:12:09:02
Stefan
I know it's a stupid question, but we get it very often. Is open source free? I mean, like, the
license is very freeing. I can run it. I don't have to pay you a cent. It's essentially free is what I
hear a lot from I don't know, I wouldn't say the word stupid, but sometimes misguided people.
But why isn't open source not free?
00:12:09:05 - 00:12:13:11
Stefan
Or what are your thoughts there on launch? I'm going to clip that, by the way. That's a stupid.
00:12:13:11 - 00:12:35:05
Jens
Idea. But you know, my my biggest my biggest pet peeve is not not just like it's open source.
Obviously it's not free. It's, I come to that in the moment, but what annoys me the most is people
who think I will support them for free on my open source, because why.
00:12:35:05 - 00:12:40:03
Stefan
a can.
Not? Like I have a big logo, I have a big logo and I work in a big company. I'm going to give you
00:12:40:03 - 00:13:06:25
Jens
I have a full calendar? Like, I'm I'm building a business. Sorry. Like I really have no time for for
you. But, you know, like, I think the most important thing people have to, to understand is open
source is a way of distribute software. You you are allowed to download the software and to
replicate it, whatever the license is.
00:13:06:25 - 00:13:37:01
Jens
And you can do whatever you want with it. And that's it. Exactly. There it ends. Like I owe you
nothing. You owe me nothing. The software is just open. Why is cosmo open and what kind of
interactions do I actually like? There are people who I think who understand open source, and
they come to us and say, hey, we have found a bug in your query planner.
00:13:37:04 - 00:14:09:06
Jens
Here's a replication. In this particular case, it's panics and we think it shouldn't. And then we
collaborate on solving the problem. Or they come in and say, hey, you have this feature. I think
there is a security problem. Here's how you can replicate this. Can we collaborate on on
improving the software? This is why Cosmo is open Source, we we think making it open source
will lead to Cosmo being the best for everybody.
00:14:09:09 - 00:14:34:07
Jens
What? What is not open source? Is someone coming to us saying, hey, I demand that you teach
me how to use this software. This this has nothing to do with open source. And some people
have a misunderstanding that just because I made it open source, just because it appears to be
free, it doesn't mean that my time is free.
00:14:34:09 - 00:14:58:12
Jens
You need to pay for my time. So if you want to have my time, then I don't know, consult our our
sales team. If you want to have our our hosted service, consult our our, sales team. If you have
a question and you come to the to the discord and you want to collaborate with others, you
know, there's also there's two categories of questions.
00:14:58:18 - 00:15:22:28
Jens
There's one question where where someone asks, for example. And this is something I'm very
happy to do. Someone comes to the discord and ask like, hey, do you have some some ideas?
Or can you share some strategies? How how do I do certain things with Federation? Right? And
I'm happy to share experiences on what we're doing with with other customers and how we're
dealing with this.
00:15:23:01 - 00:15:45:13
Jens
This is something I'm super happy to talk about. Something that people absolutely love to do is
they, they think discord is the search function for our docs. And instead of searching in the docs,
they just ask a question on discord, like, can you not just ask in the docs or like search the docs
we have like AI search on the docs?
00:15:45:13 - 00:16:26:10
Jens
It is very helpful. Super good tool. So and then there's people and this is yeah, I, I, I being
German, I should not directly translated to English, but some one thing I really don't like is
people really and I mean it literally demanding that I do something for them. And this is just not,
not possible. We don't have a business relationship and and even, you know, and this is the
thing, people who pay us, who have an enterprise plan, they are not as demanding as some
people on, on a free discord or something.
00:16:26:10 - 00:16:33:09
Jens
And that's, I don't know, some, I'm not sure what's going on, but yeah, this is something that's
like.
00:16:33:11 - 00:16:51:11
Stefan
There's a meme about that. Like, you have a customer that's paying you five bucks a month,
and they're demanding. They're screaming, they're asking, hey, what's the return policy? Then
you have the customer paying you 5000 a month, and he's just like, yeah, okay, see you next
invoice. And he's totally fine. And it's because there's a different allocation of value there.
00:16:51:13 - 00:17:11:10
Stefan
And then the other point I want to add is, there's a couple points you might have missed. And
the open source is like, we've created something, we've distributed it, we're maintaining it, we're
keeping it in a good state. We're constantly adding features to it all for free, and you have no
interest in contributing to it or in supporting the company financially.
00:17:11:10 - 00:17:28:17
Stefan
But you're demanding for help. Like, come on, man, that's like a clear imbalance is that there's a
little bit of abuse there. And we see it a lot in open source is that somebody will come and they'll
drop their big logo there, say, hey, we're interested in using you guys, but we need this, this and
this. We say, great, let's talk sales.
00:17:28:19 - 00:17:47:24
Stefan
Oh, we don't want to pay anything, okay. Do you want to contribute to it and implement those
features? No, we want you to do it. And it's like, wait, I'm so confused. Like where's the
relationship here doesn't it? It sounds almost like abusive. I'm a little confused. And then the
second part is that people don't understand is, open source is not free because it requires
maintenance.
00:17:47:27 - 00:18:06:21
Stefan
It requires collaboration from other teams. We have to properly make sure that all of our code is
done correctly. We have detailed tests and everything, and it's because there are big companies
relying on this software. And so another issue that I see is, okay, I made a PR, why are you not
merging my PR Jens? I made a PR, I contributed to open source.
00:18:06:24 - 00:18:09:05
Stefan
Why are you not? Why not merging my PR?
00:18:09:08 - 00:18:15:03
Jens
It's not my priority. Not. It's not mine.
00:18:15:06 - 00:18:16:24
Stefan
And so I don't.
00:18:16:24 - 00:18:42:28
Jens
Even mean this in a negative way. It is simply you want to make changes to the software. And I
have customers and I maintain the software on the behalf of my customers. Maybe there's
overlap between your goals and my goals. Maybe there is no overlap. And at the end of the day,
I'm responsible for our resources and our time.
00:18:42:28 - 00:19:09:22
Jens
And yeah, if you find a security bug, it might be our highest priority if you want to add a feature
that you need, but we don't need, and none of our customers needs them. It's. And again, I'm
not saying this in a, in a negative way. Just just think about it. Like if the software was closed
source, then yeah, the collaboration would not be possible.
00:19:09:22 - 00:19:25:26
Jens
And you also need to think about if you create a pull request and you merge it. No. You create a
pull request, we review it, we merge it. Who's liability is the code now?
00:19:25:28 - 00:19:34:29
Stefan
Yeah, I was going to say that like you're taking on risk by taking in the PR and you have to you
we're taking on the liability. It's us. Now if we take in that PR.
00:19:35:02 - 00:20:03:04
Jens
You know, let's think about like let's say you have you have a cosmo router and someone says, I
have an amazing feature and I make a pull request. I add this for free. I even add tests here.
You go. And by adding this code, future refactors of the router are now more complex because
the code base just got more complexity.
00:20:03:07 - 00:20:37:19
Jens
So this is also something sometimes people think if they contribute something, they, they, they
give their time. And we should be just thankful and accept it. And why are we not merging it?
And, so the problem now is if we merge it, it is it is now our burden because we have to
maintain it because let's say we merge your code and we have a customer that now uses this
code.
00:20:37:22 - 00:21:10:12
Jens
So now the customer depends on us of making it right. We cannot do like a sloppy job in
merging it fast or not reviewing it properly. Because if a customer now uses it, it must follow the
same standards. So we need to spend time like is this the right architecture? Is it? And you
know, if we would have built it ourselves, it is quite likely that we we would have gone through
like an RFC process or something where we internally discussed like, here are three
approaches we could take.
00:21:10:15 - 00:21:45:00
Jens
And maybe you didn't do that in your PR and now we're in the situation where you want this PR
merged and we're thinking, actually it's not really our priority. We also think it's just 60% right?
There needs to be like work on it. But even just spending time helping you to get the PR right
means we're now spending time and like frankelly, just said in the in the chat, yeah, it's one of
the most nuanced and challenging responsibilities to maintainer has.
00:21:45:00 - 00:22:13:01
Jens
Truly. Absolutely. And the point is, I, forgive my German for for saying these things in such a
direct way, but, it is it is hard to maintain software, especially open source, if you do this over
many years, like I'm now maintaining open source from like, open source. But I have one
project, the engine of Cosmo, the Cosmo router.
00:22:13:01 - 00:22:36:01
Jens
It's called GraphQL Go Tools, and I'm now one of the maintainers. I created this in 2018. So you
can you can look at your calendar. That's more than seven years now. So we're maintaining that
over such a long period of time. And, I'm, I'm more and more in a passive role in maintaining
that. But over the years I have learned a lot about maintaining open source.
00:22:36:01 - 00:23:14:14
Jens
And, yeah, in, in, in many ways it is complicated. It is hard. But Stefan, today we we want to talk
a little bit about what would happen if someone stole our code. Well, it's not exactly stealing
because it's open source. So what if someone took our codes and cloned our business? And I
was thinking about how can we approach this topic, and, I, I yeah, a little bit about that.
00:23:14:16 - 00:23:42:21
Jens
And I think we can, we can look a little bit into what are the different aspects of, of topics you
have to cover. And then we go through them like, like one by one. So if you would build so let's
say you could just okay you can do the let's say you copy our Cosmo code if what other aspects
if we're thinking in categories, what other categories do we have to cover to build a successful
business.
00:23:42:21 - 00:23:46:20
Jens
So so what other things need to be there?
00:23:46:23 - 00:23:58:20
Stefan
Are you talking more general or just like more technical? Like so for example, like with the
technical, they would have to understand composition for the general, they would have to have
like brand awareness or are we talking about both?
00:23:58:23 - 00:24:24:03
Jens
Yeah. A bit of both. So if we stay high level so the first thing or let's just build some categories.
So I would say one, one big category is engineering. We can we can split it a little bit. We can
also say you have to do like maintenance and development on the, on on Cosmo, but also
platform engineering because you need to to run our cloud.
00:24:24:06 - 00:24:28:04
Jens
What other categories can you think of?
00:24:28:06 - 00:24:36:25
Stefan
I would say branding. So like customer success, customer use cases that you have just those
from around customers and a brand around wundergraph.
00:24:36:25 - 00:24:55:13
Jens
The brand is a good topic. Because by copying the code, you are not copying the brand. So you
have to build a brand. What about other topics? Go to market sales.
00:24:55:15 - 00:25:00:28
Stefan
Domain expertise. Technical ability. What else?
00:25:01:00 - 00:25:02:18
Jens
Hiring.
00:25:02:21 - 00:25:18:16
Stefan
Hiring, procurement. You'd have to learn procurement you have to learn sales. You would have
to learn how to operate a company. Oh, security. Like, Cosmo is, soc2. Like, type two. So you
have to do compliance, security.
00:25:18:16 - 00:25:45:03
Jens
So, so you need to build the, the the processes to be compliant, right? Yes. So we have to build
a framework, okay. That, that that can take up a significant amount of time. But okay. If we dive
a little bit into this topic. So I would say the the first problem you run into is so let's say you copy
the code you want to you'll want to run it.
00:25:45:05 - 00:26:16:06
Jens
The first problem is you don't have the expertise. Why we build things. You can see what we
have built. You can see like a snapshot, like, okay, here is Cosmo. You don't know why we have
build things this way, and you don't know what we had in mind for the future. You just have a
snapshot and so the moment you kind of fork it or whatever, then you, you kind of have the
snapshot.
00:26:16:06 - 00:26:33:04
Jens
So now you're lagging behind. Now your counter argument might be but Jens I don't need to
fork it because, I can just copy all your updates. I just follow all your commits. Do you know why
that's not possible?
00:26:33:07 - 00:26:53:05
Stefan
Well, one point before you answer that is also like, even though you copy over the code or you
fork it or whatever, you also don't know why we made certain decisions, why maybe something
is missing or why maybe something is there, and then you also don't even know what you don't
know because of the things that we know.
00:26:53:05 - 00:27:08:07
Stefan
If that makes sense, stick to things that we had to figure out. It did through trial and error and
everything. But to your point with the counter argument, what? Why wouldn't it work? Okay, I
just follow you commit by commit, I'm a little bit lagging behind. Why why why wouldn't it work in
a business model?
00:27:08:10 - 00:27:29:13
Jens
Okay, let's assume you somehow, figure out sales and branding and other things. Maybe you
already have a brand. It's possible. Okay, I have it all, let's say. But let's say you get your first
couple of users. What happens when you have users?
00:27:29:15 - 00:27:31:10
Stefan
Are they paying or they just users?
00:27:31:13 - 00:27:34:02
Jens
They're paying.
00:27:34:05 - 00:27:44:24
Stefan
Well, now we have responsibilities. They were oh. They'll want support. They want education.
They want guidance on how to implement it in the best way possible.
00:27:44:27 - 00:27:52:26
Jens
Let's say they ask for bug fixes or feature requests. So if you just follow our commits.
00:27:52:28 - 00:27:53:13
Stefan
How are you going to do.
00:27:53:13 - 00:27:59:08
Jens
That? We are not aware of the bug fixes your customers need and the features.
00:27:59:11 - 00:28:04:06
Stefan
What's if I just open up the PR? I ask in the discord for the other. I'm just asking you guys.
00:28:04:09 - 00:28:08:16
Jens
I told you before, I'm busy.
00:28:08:19 - 00:28:36:08
Jens
Okay, so you see, you have customers. They want something, so you need to stop maintaining
that. So you, you make commits to to do what they need. You you will quite quickly figure out
that. So you will see that we we are we are not merging this because we're we don't have time
for the frequency of of changes you make.
00:28:36:10 - 00:29:03:05
Jens
And so you add commits. We have commits. Maybe you are able to merge them for a little while
until you come to a point where we just have different opinions. And because we are not
collaborating, we're colliding. And so from, from that point on, the code is more or less
incompatible. So, so you're now forking and the moment you fork, you take full responsibility.
