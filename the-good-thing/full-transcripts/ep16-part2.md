00:29:03:05 - 00:29:42:04
Jens
And here starts the first problem. If you fork Cosmo. We currently have close to 20 developers
working full time on Cosmo. It so like some people, they had a little bit of experience. But now
we have many developers with multiple years of experience working on Cosmo. And I can tell
you from, from the expertise you find in the market, you find people who understand GraphQL,
you find people who understand how to write code and communicate.
00:29:42:07 - 00:30:12:29
Jens
You don't find people who understand, GraphQL federation at the depth where we operate. And
like, there's nobody on the market, these people work at the other federation companies. So
hiring it can take you a year or maybe longer to hire people, to hire the right people and to to get
up to speed, to that. You can actually maintain the, the, the software.
00:30:12:29 - 00:30:19:16
Jens
So that's, that's like a huge problem to solve. In the beginning.
00:30:19:18 - 00:30:39:08
Stefan
Well said, I think people missing most on the domain expertise, like just because you get the
software, you don't have the expertise to run it, especially at scale. And one of the biggest
things is Dustin, our CTO, like, let's say I go and I set it up. I follow you guys with reference
architecture that you guys very nicely put on the documentation page.
00:30:39:08 - 00:30:56:08
Stefan
I fork everything, I copy it perfectly fine, but you also don't have the expertise that Dustin has
and the things that he's done on GCP in Kubernetes to make sure that we run this scale for
customers doing billions of requests per day. I think that's also an important factor, is that
offering this as a managed service is hard.
00:30:56:11 - 00:31:23:22
Stefan
Offering this as a managed service with 99.99% uptime and availability and minimal incidences
of extreme hard. You have to also figure that out. And then the third part, I do want to add this
because I always say this in sales calls is there's probably ten really deep federation and query
planning experts in the world. And I'd say about eight of them work at WunderGraph like the
domain expertise is the biggest part that most people are misunderstanding.
00:31:23:22 - 00:31:39:18
Stefan
Like, oh, I can just go Salesforce like over a weekend using cursor, you know, as an example.
Sure, you can build Salesforce, but there's so much that you don't know what they've done in
their history of why they've added certain things or build things a certain way. And you'll only
understand that when you actually start going through it.
00:31:39:18 - 00:31:57:08
Stefan
But I like what you said. These developers, they have years of Cosmo experience, and that's
not something that you can just steal. What are some other points though? Okay, so let's say
that I do figure that out. I figure that out. I'm able to run Cosmo. What about like on the branding
or customer side?
00:31:57:10 - 00:32:29:20
Jens
Maybe, maybe one other topic that I think is worth mentioning. We can also talk about branding,
customer and everything, but another topic is pricing. So, there is the pricing we have on our
website today. There's the pricing from other competitors. And then there there is the pricing we
want to have in the future because we're, we're we're changing our pricing.
00:32:29:20 - 00:32:52:15
Jens
And it takes a bit of time and it will have no negative impact on our existing customers. But,
we're changing things because we have learned a lot of stuff. And then there's one big piece.
We are now more than modern, I think two and a half years or something in the business. And
we have had hundreds and potentially thousands of sales calls.
00:32:52:17 - 00:33:23:28
Jens
We have a feeling for what people want, how they how they want it. What's the packaging, what
pricing works, what doesn't work? What do competitors do like? It's it's not super hard to get
pricing from from competitors. And you, you you get a whole feeling of what's going on in the, in
the market. If you take our code, you would, you would, yeah.
00:33:24:00 - 00:34:02:26
Jens
Imagine a few scenarios. Let's say you, you do the exact same pricing, but you know, like we
have more developers who know how cosmo works. So we are faster. At least today. So if you
do the same pricing but we are faster, we're delivering more. And we have a stronger brand
because everybody knows us. Okay. Let's say you have a much bigger brand, but overall, do
you think like do you think it would work charging the same amount?
00:34:02:29 - 00:34:19:28
Stefan
No, it's a differentiator. Like there's no winner in being the cheapest solution. But if we charge
the same and you don't have the logos that I have, like, why would I go with you over
wundergraph? I don't I don't think that there's any advantage there. None.
00:34:20:01 - 00:34:58:02
Jens
And you know, if if you take this approach, you could also think about who could successfully
pull this off. So let's go about different categories of of of people who who could actually do this.
So let's assume you are a startup okay. You are I don't know how much like let's say early
stage. You're like, okay, we build a startup, we take this code and we, we, we we clone that
because we have an idea how to do it better and yada, yada.
00:34:58:05 - 00:35:04:03
Jens
Okay. Can you imagine what happens next?
00:35:04:06 - 00:35:07:00
Stefan
Because I can go. What happens next?
00:35:07:02 - 00:35:16:00
Jens
Okay. Well what does the startup need to do to get started and be able to hire a bunch of
people?
00:35:16:03 - 00:35:18:07
Stefan
Well, they have to have money.
00:35:18:09 - 00:35:20:22
Jens
Okay. How do you get money as a startup?
00:35:20:24 - 00:35:25:12
Stefan
We either venture capital most likely round okay or you go to venture capital.
00:35:25:19 - 00:35:28:28
Jens
Okay. Tell tell me your pitch.
00:35:29:01 - 00:35:38:00
Stefan
Hey, guys, there's this company, WunderGraph. We're going to fork their code, and we're going
to basically build a WunderGraph 2.0.
00:35:38:03 - 00:35:48:00
Jens
Okay. So you have been on VC pitches, right? Yeah. Well what would VC say to this.
00:35:48:00 - 00:36:03:02
Stefan
Where's the market opportunity there. How big is this market. Why. What differentiates you from
wundergraph. Why can't a customer just why would a customer choose wundergraph over you?
It asked a lot of interesting questions, mostly around that.
00:36:03:04 - 00:36:25:10
Jens
Okay. So let's assume you are one a graph and you're pitching to investors. Okay. And investors
will say, oh, WunderGraph. That's nice. So we just raised a series A so not so long ago this
happened okay. So you are wondering if you go to investors the first thing they will say is like
not the first thing but the second thing.
00:36:25:13 - 00:36:50:28
Jens
Okay. Apollo. But Apollo, what about Apollo? Like everybody asks you about competition and
the question about competition. And this is very important. Like early it is like first time founders
in the beginning. They don't get it. The funniest thing is very early first time founders, they will be
like, there is no competition.
00:36:51:00 - 00:36:53:12
Stefan
They said, don't worry about the competition. Yeah.
00:36:53:15 - 00:37:24:08
Jens
Yeah, that's no competition. And if you say there's no competition, what we see here is there is
no market. Because if there was competition it means okay, so market like no competition
means no market. Okay. So then there is competition. Now let's look at the market okay. We
have Apollo and now we're pitching WunderGraph. And the way you pitch WunderGraph when
there is Apollo is you say okay they do this we do that.
00:37:24:10 - 00:37:51:09
Jens
Here is the clear differentiator. And here's what we're going to do in the future with your money.
That really sets us apart. We're building a new category. We are blah blah blah blah. Big story
that tells the, the investor, how do we go from our our investment to, to, 10x that big exit, etc..
So you need to think about it like that.
00:37:51:11 - 00:38:21:25
Jens
There is an existing market Apollo. So it's proven there is a market also. Now you have to prove
to investors that this market is big enough for Apollo and you, or it is big enough for you to go
outside of this category, build a bigger category, or advance into another category or something
that has a big enough term total addressable market to help you 10x their money.
00:38:21:27 - 00:38:48:09
Jens
That's kind of the pitch. Okay. Now now here are you saying, okay, there's Apollo and
WunderGraph and now we're forking WunderGraph and we we do the same thing where where
is our differentiator. And that's up there. Let's go there. Really that's going to be a really hard
pitch. I'm not so sure if if you can if you can pull this off.
00:38:48:11 - 00:38:54:18
Jens
And even if you do, do you know the term tar pit ideas?
00:38:54:20 - 00:39:17:29
Stefan
Yeah, it's it's coined by YC. But for those of don't know, it's an idea that basically is like a tar pit.
You know, you go in there and you just keep working and working and working and working and
you keep working on it and it never goes anywhere, just a tar pit. It's an idea that goes in there
like there's so many of them, like, like a bar splitting up, like an app that allows you to split bills
and it's like, well, what are some of your favorite tar pit ideas?
00:39:17:29 - 00:39:19:20
Stefan
Actually, that's a good question.
00:39:19:23 - 00:39:57:08
Jens
My favorite tar pit ideas. Competitors to WunderGraph. No, but one of the biggest tar pit ideas I
would say we we ever had is, generate it APIs from databases, like, everybody wanted to do it.
Everybody tried it. And, just like 1 or 2 days ago hasura, change their landing page. It is now
promptQL and they, they fully focus on like they, you know, they, they just build their DDN like I
don't know, they did.
00:39:57:10 - 00:40:00:16
Stefan
Data data driven network data.
00:40:00:18 - 00:40:25:00
Jens
Something like that. Yeah. But they they kind of abandoned it. And yeah I, I really hope that for
everybody from now on hasura is an example that you that that we all just end with this tar pit
idea. So please stop it. Don't generate APIs from the database.
00:40:25:02 - 00:40:30:14
Stefan
called.
Don't do it. Yeah, I think you're absolutely right. I think they get rid of the DDS or whatever it's
00:40:30:17 - 00:41:07:02
Jens
Well, there's like a link and you can go back to it. But there's also there's a select, there's a slack
channel where we're like it's called GraphQL community leaders. And there was just a message
the other day that, that, Hasura was not focused on GraphQL anymore. So, yeah, that's one of
the tar pit ideas. But okay, so I think we're, we're we're in the clear that the startup, maybe they
can pull it off, but, I'm not so sure.
00:41:07:02 - 00:41:34:24
Jens
And by the way, this is not a time where you pitch like an API startup or a GraphQL startup. This
is the time where you pitch an AI startup, like we are in the age of AI. If you think if you think in
VC investments, it always happens in waves. There was like, the cloud native wave, which has
kind of ended.
00:41:34:26 - 00:42:01:18
Jens
And now if you go to KubeCon, for example, it's all about AI. So now is the AI wave. And if you
want to raise money, just raise money for something AI because that's currently what, what, VCs
are interested in investing. And so I think startup would have it super hard, but who could be
more successful, who could pull it off?
00:42:01:21 - 00:42:02:05
Jens
Well,
00:42:02:07 - 00:42:21:06
Stefan
This is so interesting, by the way, because, it's like, again, I was listening to a podcast on the
way here to Orlando, and one of the biggest ones is there's this guy. I forgot the name of the
company. I'll drop it in the comments on YouTube. But there's this guy that has a $10 billion
company. He owns about 90% of it.
00:42:21:09 - 00:42:44:29
Stefan
It's a very successful startup. It's a big company. And he said, I'm not scared of the big
companies. I'm not scared of our enterprise. Corporate competitors. I'm not scared of them. I
am scared about the group of kids that I don't know. I'm scared about them because they might
be as crazy as me. And the reason why this company is so successful is because of me, I think
about it, I breathe it.
00:42:44:29 - 00:43:00:27
Stefan
It's not a 9 to 5 to me. I'm not a typical corporate CPO. I am a full time founder. And if you
notice, all the best companies that are founder led, they always do more successful. But he
said, I'm not scared of the corporate companies. They're too slow. They don't care. It's not their
bread and butter. They don't live this.
00:43:00:28 - 00:43:15:18
Stefan
You said it like this. They don't live this shit, he said. I'm scared of those kids. I'm scared of the
ones that are like me and they live it. But what do you think? Do you think it could be
competitors? Could competitors could possibly do this? They fork, not a competitor like a big
company. Let's say a big company.
00:43:15:18 - 00:43:27:15
Stefan
Forks cursor. Let's say Microsoft, you know, makes their own cursor or something like that. So
it'd be a big company. But the same thing with Cosmo.
00:43:27:18 - 00:43:34:17
Jens
Cursor maybe, but do you do you think forking Cosmo is attractive?
00:43:34:19 - 00:43:40:02
Stefan
No, not in any sense. I mean, no, I don't think so.
00:43:40:05 - 00:43:44:10
Jens
Like, you know.
00:43:44:12 - 00:43:59:06
Jens
Take AWS, for example. There's AWS Appsync I, I'm yet to meet anybody who's like, I love
Appsync. And there's also what's, what's this other AWS service called.
00:43:59:07 - 00:44:04:26
Stefan
It's AWS is is the async one, but is there another one for APIs?
00:44:04:29 - 00:44:28:04
Jens
Is that there? They have another thing, but not not so important. My point is, I think AWS would
be amazing at running cosmo router as a service. Yes. And actually it would be pretty cool if
they did, because, we're not planning to do it. And then, they, they, they can offer it as a service.
00:44:28:04 - 00:44:54:13
Jens
Maybe we can, we can collaborate on. That would be nice. Imagine you, you click a button in
your AWS console and you have a fully managed, cosmo router in your, in, in your infra in your
network and everything. That's PCI compliant and whatnot. That, that would be nice. But I think
everything else around Cosmo, first of all, it's it's built our way.
00:44:54:16 - 00:45:20:03
Jens
So it's not built the AWS way. So if you would build it with AWS, you you would, for example, not
use keycloak for authentication. You would use Cognito and then you go further and you would,
I don't know analytics. We have clickhouse . I'm not sure if if AWS would have clickhouse or the
other thing. So they they would rebuild that.
00:45:20:05 - 00:45:56:23
Jens
So in the end they, they would end up forking. It's now their own product. And I really doubt that
they, they have the same energy, the same the same drive behind such a project. I think one
one, one piece people have to understand is, when we hire, it's actually very hard to, to hire
people because and we typically never hire from, from like companies like AWS or something
because there's a huge problem.
00:45:56:25 - 00:46:28:27
Jens
These are people who want to get paid three, four or 5 or 10 times more. Then then we get paid
and they are doing, a mediocre job because they understand politics and they understand like
backlog machines and how to, how to drive initiatives. And they, they have learned how to climb
up the ladder and how to to follow the rules and play by the book of, of getting up the ranks.
00:46:28:29 - 00:47:00:10
Jens
But all of this is not relevant. And then in an environment like, like a startup. And so for us, we're
not really hiring those kind of people. And I'm absolutely not afraid. Competing. Imagine I
imagine they would they would clone us. So they would build a team with like the product owner
and then some developers and and who, who would really care about this whole topic as much
as we do.
00:47:00:12 - 00:47:22:07
Stefan
Nobody. And that's the thing. Like, I think we're really lucky. Like we work with some amazing
companies where you meet these people and these big companies from these enterprises, and
you find true people that care, you know, they're true technologists. But I don't think in this case,
you know, like, okay, we're forking Cosmo like, like, okay, I at 5:00, my job ends, I get paid 300
4hundred K.
00:47:22:08 - 00:47:47:12
Stefan
I have some bureaucracy. And so I know because we're we're running close to the end of the
episode is, did you see that tweet, by the way, from this girl? She just got a job at Google, and
she's like, working at FAANG can be way harder than working at a startup. Like, I was just on
call for two hours, post, post, like working shift, like, it's kind of crazy, like, like, people can
compare building a startup to working at Faang in a stress levels.
00:47:47:12 - 00:48:06:02
Stefan
And a good thing is, you should never, like, try to match trauma or stress like, oh, my stress is
more than your stress. Like stress, stress, my trauma is worse more than yours. But I think
you're absolutely right on that front. Which is that working on a big company, it has trade offs.
Working at a startup has trade offs, and you have to just pick which trade offs you want.
00:48:06:02 - 00:48:33:04
Stefan
But it's absolutely true that when you come from a big company, it's harder to change you.
You're more into politics because you've been dealing with politics all year round. And third, at a
big company, it's very easy to coast. If you do what you're asked, you will be employed. But if
you do a little bit more, then you actually get in the tricky situation where you get more
responsibility, maybe not for more pay, but more responsibility, more work.
00:48:33:07 - 00:48:49:12
Stefan
And it's a really tricky situation. I wouldn't say to your point though, we're not hiring from those
big companies. If you're ambitious, if you want to get away from the bureaucracy, if you want to
work on software that impacts developers, and then you want to work on software impacts some
of the biggest companies in the world, I would take a look. At Wundergraph
00:48:49:12 - 00:49:05:14
Stefan
I wonder if you want to leave the corporate card, take a look. I wonder if but if you want to coast,
if you want to talk to bureaucracy, if you want to wait months to ship software, WunderGraph is
not the place for you.
00:49:05:16 - 00:49:12:29
Stefan
Any thoughts on there Jens? Would you agree?
00:49:13:01 - 00:49:38:08
Jens
Yeah, I, I just I just cannot imagine how how would a big company pull it off, how it's such a
complicated project and it's, you know, from the outside it looks shiny. You know, the, the I think
one thing I, I really don't like about being a founder in the public, you cannot talk so much about
the the nuance.
00:49:38:08 - 00:50:02:08
Jens
You know, it's a bit like landscape you have. You have hills, you have like it goes up and down
like founder life is one day can be amazing. Next, next. day can be absolutely horrible. Yeah.
And so what you see in public is everything is going is going good. And but it's not the reality.
It's, it's a, it's a really tough game.
00:50:02:15 - 00:50:37:27
Jens
And if you now think about okay, let's say you build a corporate team ten, 15 people whatever.
And then you have so many seniors with, with opinions and, and, I don't know, it's it's it's
probably going to be tough. And then there's this other thing. Is it even viable? Because at our
current level, I think if you, if you, if you copy us like, I mean, you're, you're instantly also,
competing with Apollo, they are much bigger, much stronger.
00:50:38:00 - 00:51:18:03
Jens
Do you really want to compete with them? But still, even Apollo, for someone like, let's say IBM,
their ARR it's kind of like a rounding error. So yes, I don't know why, why, why even do it? It's
such a tiny market. In the end, it needs to grow much, much, much bigger. But you I don't know,
I think the, the reality is you have these startups, many of them fail, some succeed, and then
they IPO, gets acquired or die and and, yeah, I, yeah, that's that's kind of my thing.
00:51:18:05 - 00:51:45:14
Jens
I wanted to bring in some other topics just to, to, to field, to, to complete the discussion. One
part, is SLA, if you, if you copy what we're doing, you need to really figure out how to do SLA,
because if you want to to sell, like to to real enterprise customers, you have to provide them a
SLAs.
00:51:45:17 - 00:52:25:29
Jens
And I think it will take you a lot of energy, knowledge and learning and everything to be able to
provide such a slice. And this other part, this we have a blog of over, 200 blog posts that we
have built over the years, which kind of built a, a, this blog, it built like a knowledge base, but
also a brand, like, also, a lot of people know that WunderGraph exists if they are in the GraphQL
space because they have read one or more of our blog posts.
00:52:26:02 - 00:52:52:25
Jens
You can't just copy that kind of stuff. What else do we have to? Yeah, I think that's kind of good.
And then there's there's one other thing. We have logos, we have opinions. Public opinions from
people who use Cosmo. For example, on our website, we have eBay who is, customer but also
a user.
00:52:52:27 - 00:53:20:06
Jens
And we also have, for example, a very good story from SoundCloud. But we also have have
other, companies who, who use us and you have to ask yourself again, if, if we have those
logos, if we have those stories, how will we now compete with that? And if you then want to win
customers, they will ask you, okay, there's Apollo, they have these customers, there is
WunderGraph.
00:53:20:06 - 00:53:46:11
Jens
They have that customers. What do you have? And so I would say the market is quite mature
already. So it's going to be tough in anyway. But we have this we have this message from
Frankelly. Yeah. Let's read that out. Startups. They often tackle niche pain points over
overlooked problems in clever, tech enabled ways. When they get it right, they can redefine
entire industries.
00:53:46:18 - 00:54:09:18
Jens
And and that's. I very much like what you say here. This is this is really this is also my opinion
that you have a startup. They figure something out in the niche and then eventually they can
really scale it out into like a whole industry or completely redefine an industry or something. And
but this, this kind of movement, it must start in the niche.
00:54:09:18 - 00:54:44:23
Jens
It must start with four or 5 or 6 crazy people who believe in something that, that nobody else will
believe. You know, if you think about our timeline, the reality is the first year was really bad. I
think the second year was a little bit better. And then in the third year, we finally figured out
some stuff. And if you if you would work in a corporate project that cannot show substantial
results in the first two years, I think first of all, the project will be dead.
00:54:44:24 - 00:55:07:11
Jens
But second, if you know a little bit about politics in in, in, in, in corporate world, typically if you
work like for a FAANG company, you get to go for the current year to get to the next promotion.
So you get some like a project within the timeframe of like this year or something where you
have to show the results.
00:55:07:14 - 00:55:21:06
Jens
So like two groups of people have to get fired before you build a wundergraph. So in the
corporate world, it's it's not unrealistic.
00:55:21:09 - 00:55:36:02
Stefan
Guys, we do need to end the episode five minutes a little bit early today because me and Jens
have a meeting. But what I will say though is I really enjoyed this episode. I think we want to
make it part two. If you guys like when Jens is little bit more spicy, which I prefer, please let us
know below in the comments.
00:55:36:02 - 00:55:51:15
Stefan
Because excuse this German if you will, but I think it's much better. I also just learned today.
Hasura gave up on GraphQL? It's very interesting. But next week we'll be back. We're going to
talk a little bit more interesting topics. I still want to bring back open source, because I want to
talk about the importance of choosing a good license.
00:55:51:15 - 00:56:16:25
Stefan
Like why do we choose Apache 2.0 and MIT, how some licenses are weird, for example, BSL
and what the enterprise paywall and stuff like that. But we'll be back next week with another
episode of The Good Thing, and we'll talk a little bit about that. We'll talk a little bit more on kind
of just more about like what would happen if you would kind of fork wundergraph and then, what
what's what's the good thing?
00:56:16:27 - 00:56:19:13
Jens
Before, before this.
00:56:19:15 - 00:56:21:15
Stefan
The medium thing here.
00:56:21:18 - 00:56:27:04
Jens
You know, you said BSL, you know, you know what what this translates to.
00:56:27:06 - 00:56:33:13
Stefan
Is it BSL or is it. Oh yeah. So what does it translate to?
00:56:33:15 - 00:56:36:11
Jens
Bullshit license.
00:56:36:13 - 00:56:39:19
Stefan
Okay. What a way to end the podcast. Well, the good thing.
00:56:39:19 - 00:56:46:20
Jens
Is the good thing is we are we are continuing this discussion in a week.
00:56:46:23 - 00:56:50:20
Stefan
That is so funny. Thanks guys. And see you guys next week.
00:56:50:26 - 00:56:51:21
Jens
But so.