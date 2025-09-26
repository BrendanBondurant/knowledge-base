Episode 18
type: podcast-chunk
00:00:19:17 - 00:00:38:08
Stefan
And we're live. Welcome back, ladies and gentlemen, to another episode of The Good Thing.
Today we're back, of course, with my co-host Jens. Jens How are you doing today? I'm good.
It's the same introduction every week. Before we start, I would love to share a little joke that I
told Jens yesterday that I thought was pretty funny, but,
00:00:38:13 - 00:00:43:20
Stefan
How do you know if somebody is a Linux or neovim user? Ends.
00:00:43:23 - 00:00:45:11
Jens
They tell you.
00:00:45:13 - 00:01:03:25
Stefan
That the first thing they'll do is say, hi, I'm a Linux in the neovim user and my name is Jens.
They say their name. Second, after they tell you that they use Linux in the other room. But I'm
glad you found that joke funny yesterday. But today we're going to be talking about what is a
TAB. So a TAB is a technical advisory board.
00:01:04:02 - 00:01:22:18
Stefan
And we've been rolling it out with our customers for a new product that we're building. And Jen's
been a little bit closer to date on the TAB I set it up. But he's been doing more of the meetings.
So we're going to kind of do an interview style today where I'm going to be asking you questions
about the TAB, things that you've been learning, and then you talk back to me and explain, like
what usefulness a TAB is.
And I think, honestly, anybody building a new product should set up a TAB. Would you agree to
00:01:22:18 - 00:01:29:17
Stefan
that?
Yeah, probably before we dive into the TAB, should we should we talk about some current
00:01:29:20 - 00:01:40:29
Jens
events.
00:01:41:02 - 00:01:45:03
Stefan
Current trends. Yeah. We should do like a current events type current current trends.
00:01:45:06 - 00:01:53:09
Jens
Think I think a bunch of a bunch of, GraphQL experts are on the market. Yeah.
00:01:53:12 - 00:02:10:18
Stefan
So you guys probably haven't seen this if we're not as deep into the space as we are. But, last
week or this week and yesterday, there were significant layoffs. Apollo, mostly the go to market,
the sales and the, was it the product engineering side just kind of all over the company. There
was layoffs.
00:02:10:20 - 00:02:14:17
Jens
I haven't looked deep into it, but I saw some messages.
00:02:14:20 - 00:02:31:01
Stefan
Yeah. So there's been layoffs on the Apollo team. As you mentioned, if you're a GraphQL expert,
we are hiring. So take a look at our hiring things. But, layoffs are never fun. It really sucks. Also
sucks to see this one since its happening in our space, Jens, What are your thoughts on this?
00:02:31:04 - 00:02:55:10
Jens
Yeah, I have a question for you. Like, you know, we we we like to be transparent. We like to, to
talk about things. And, if your competitor has layoffs, how how do you think about it? Because it
the if you, if you look at it face value like as a competitor your first reaction might be, oh that's
funny.
00:02:55:10 - 00:03:20:03
Jens
Like haha losers blah blah blah. But we're, we're, we're not looking like that at at Apollo. We're,
we're I see this more like a formula one. You know, you you can you can respect other drivers.
You can fight with them once you're in the racing seat. It's a race you have rules of the race, but
you can still respect your, your peers.
00:03:20:03 - 00:03:37:09
Jens
And I think yeah, from from your perspective because it, it actually has also negative effects for,
for us. How how do you, how do you think about, a competitor having layoffs? Well.
00:03:37:11 - 00:03:54:24
Stefan
I first try to remove the competitor part and give the sympathy. Like, these are human beings,
human beings with families that they have to support, especially, you know, if they're engineers
or if they're within that team and they're supporting their families. So first is the sympathy part,
because, you know, losing your job is never easy, especially in today's market.
00:03:54:24 - 00:04:11:24
Stefan
It's a little bit harder. Also, when it comes as a surprise, you know, nobody wants to wake up on
a Friday. You know, this happened to me and you're locked out of your email and you get some
bonus bogus email to your personal email saying, hi, you've been laid off effective today. So my
first one is sympathy. You know, like I feel bad.
00:04:11:26 - 00:04:34:14
Stefan
The second part is now looking at the overarching it's never great when a competitor has a
layoff because of two reasons. One is, what does it say about the space and the market? And
they found something that they've experienced, before us, maybe they ran into a roadblock that
we might run into later down the road. So it does put a little bit of fear to that part.
00:04:34:16 - 00:04:53:13
Stefan
And then the other part is maybe it's them, you know, maybe from my founder hat this is a good
thing, you know, like if you go into like the Art of War, now's the time to strike our competitors
weak. But, you know, when you remove that siding to go back to the human side, layoffs are
never fun. And you know, I have the deepest sympathies for everybody.
00:04:53:16 - 00:05:10:06
Stefan
Actually got in a fight with yesterday with some stupid VC because he was punching down on all
the people that got fired from Microsoft. He's like, why would I hire you? You worked at
Microsoft, you're a big cog in the factory. And I was like, you had the opportunity to be nice and
offer sympathy. Instead, you're punching down to people that just lost their jobs.
00:05:10:06 - 00:05:34:01
Stefan
So I think the sympathy part is important. And then I also have a controversial take which might
get me in trouble, but usually layoffs. And I'll explain. My reasoning is you kind of cut the bottom
20% of the quadrant not performing. You know, you wouldn't release your best employees. But if
you're a big enough company, sometimes people do get caught in that as like strays.
00:05:34:04 - 00:05:52:13
Stefan
So you might get some really amazing people that were just accidentally laid off or they were
too expensive, or maybe they just had some issue that the management didn't see. But the first
thing first is always sympathy. I always feel bad when any company has layoffs, even our
competitors. What do you think?
00:05:52:15 - 00:06:26:27
Jens
I, I have a multifaceted view on this. So first of all, my view on startup layoffs is this, and it's, you
know, sometimes I hear people being overly negative towards founders who execute layoffs.
And I think that's so I, I agree with your part where you say, okay, you have empathy for the
people who got fired, who got laid off, at the same time, we have to be realistic.
00:06:27:00 - 00:06:56:17
Jens
If you join a startup, you should be aware how a startup works. And yes, I think one fundamental
concept of a startup is the idea behind the startup is, we are not profiTABle. We are growing
faster than we organically could. So we need outside capital to fund this fast growth. So now
you have a problem. You have kind of like two lines.
00:06:56:17 - 00:07:20:08
Jens
So there's like one line is what you expect that the market pulls from you in terms of like like
dollars luck. So you say okay, end of this year we want to make 1 million ARR or end of this
year we want to make 100 million or whatever. So let's say you are at 50 million a year and you
plan that you grow like 10%.
00:07:20:08 - 00:07:45:25
Jens
So 55 men are you want to grow 20%, so you want to grow two to, 60 million. Or maybe you
want to grow to 70 million. Okay. So you have a growth plan. And so to to execute this growth
plan, you need a certain amount of people. Maybe you have a, a function where you can say,
okay, to generate this amount of net new ARR.
00:07:45:27 - 00:08:13:03
Jens
We have to have this amount of new sales, marketing, devrel support or something. Yeah. So
you have a hiring plan to achieve this goal. And obviously nobody can look into the future. So
we can we can make a plan. And we have we can have high hopes. And, I would even say like,
like, you know, I, I respect other founders.
00:08:13:03 - 00:08:52:15
Jens
So I also think the Apollo founders, they know how to execute. So they make a plan and then
comes reality. And I think when you see layoffs, what this means is that there was a plan and
the plan didn't work. They were not able to put the plan into reality, how they wanted and or they
they it's also possible that the company or founders or the management board or whatever, it's
also possible that they have, an idea how they want to execute something or they, they, they
make a project and they hope that they get something out of the project.
00:08:52:15 - 00:09:15:08
Jens
And then after six months, they realize we're we're not getting there. So it's it's it's not going to
work like that. So yeah, I think on the one side, empathy for the employees who got laid off, it's
it's a it's a bad situation of of course. And at the same time, I also have empathy for the
management, for the founders.
00:09:15:08 - 00:09:37:17
Jens
Whoever makes those decisions. Yeah. Because that's that's just how startup mechanics works.
Like, you want to grow fast, you have VC funding and then there's this, this, gap between your
plan and reality and, Yeah, it I think it can happen to every company.
00:09:37:20 - 00:09:56:12
Stefan
You ever heard the quote? I think it's by Mike Tyson. He's like, it's about life or it's about when
you get into the boxing ring, which, like, symbolizes life. But he's like, everybody has a plan till
they get punched in the face, and then the plan goes out the window. And I think you're spot on
is like, people will be very quick to jump on the founders, be like, you idiot, like you knew you
were planning ahead.
00:09:56:17 - 00:10:09:06
Stefan
You knew that you didn't have the thing. And it's like, well, that's the whole point of a startup.
And a good example of this is, remember we were working kind of close with, was it Conway?
No. What was that? Trucking company. Conway.
00:10:09:09 - 00:10:10:10
Jens
Convoy.
00:10:10:13 - 00:10:32:03
Stefan
Convoy. Yes. Yes. So convoy. For those that don't know, they raised a billion, $1 billion in
funding and they went completely under. And the reason why is reality caught up to them. You
know, they weren't producing the maybe the PMF wasn't there. And, you know, startups are
very, very tricky. And, you know, people are very quick to jump onto founders and, to bash them.
00:10:32:03 - 00:10:48:27
Stefan
And one of the biggest things. So again, my dad told me this, he goes, you know, everything in
this world is because the founder took a risk. Everything that you have, everything that's
invented, everything that a company produces is because a person decided, you know what? I
don't like the way the world is. I'm going to go and I'm going to take a risk.
00:10:48:27 - 00:11:07:06
Stefan
And so when it works, it works. And when it fails, it fails. The sympathy and the empathy is
there. And I really think it's important. But I would add to your point, I agree. I think for
management it's tough. You have to go back into the red room. They have to figure it out. They
have to see how to, you know, keep everybody motivated, especially during a layoff.
00:11:07:06 - 00:11:24:23
Stefan
But I would agree. What do you think though about layoffs. And like I see it all the time on
LinkedIn. But like you wouldn't get that stupid quote. By the way you won't get laid off if you
were producing. Do you agree or disagree with that?
00:11:24:26 - 00:12:01:21
Jens
Let's say I hire Lewis Hamilton. Probably not the worst F1 driver, and I put him on the tractor.
Can he be producing? Yeah. Like he's the one of the best drivers. I can also take Verstappen
and tell Verstappen to to do I don't know to, to to build a better framework to, to do federation.
Well so I mean it's, it's super simple to put it on the, on the people.
00:12:01:26 - 00:12:26:29
Jens
I being, being at the head of the company, I have the opinion that if something is not working in
the company, it's always my fault. Like you have someone in the front line, maybe they have a
manager and, maybe not. Maybe they report to me, or maybe they report to someone and that
someone reports to me, or that someone reports to someone and this person reports to me.
00:12:27:03 - 00:12:45:15
Jens
So at the end of the day, it's it's like a tree. I am at the top. And if it's not working, I'm
responsible. Super simple. So just putting it on the like, you know, if WunderGraph doesn't work
or work out, I don't I won't go to the engineers and be like, guys, you have fucked this up like
that.
00:12:45:22 - 00:12:47:20
Jens
Yeah. That doesn't do.
00:12:47:20 - 00:13:04:22
Stefan
Very much for you. It's a very mature yourself. That's a very mature answer. And sometimes you
see like CEOs trying to hide behind that. But really like if you're CEO like you have to take the
blunt of everything. If the company doesn't work, it's because of you. You didn't make the right
decisions or the founding team. But I like that answer.
00:13:04:22 - 00:13:08:14
Stefan
It's very mature.
00:13:08:16 - 00:13:11:19
Stefan
You're deep in thought what are you thinking about.
00:13:11:22 - 00:13:38:18
Jens
I don't know. I just think it's important to, to to to own your stuff and to to to not blame people.
Like especially in the startup, if the strategy doesn't work out, who is to blame? Like I think it it's
super simple and yeah. So you're you're. Yeah. No, I, I think that's that's my answer. It's tough.
00:13:38:21 - 00:13:43:14
Stefan
Should we transition into a TAB and just kind of explain what it is and what we've been doing.
00:13:43:16 - 00:14:18:13
Jens
Yeah, I think it actually aligns perfectly with layoffs because layoffs means, plan didn't align with
reality. And what we kind of figured out over the course of like, two and a half years is, you don't
want to build the startup that where you have to push the solution into the market, where where
you have to to invest so much into into marketing and sales and everything to, to move on and,
or to, to get going.
00:14:18:13 - 00:14:44:02
Jens
And, I think we all know how it feels or like, I don't know, I know it, but, you know it. I'm not sure
our audience knows, but, I think you can imagine if you don't know, if you if you have a startup
without product market fit, everything feels a little bit off. There's this pain, there's this.
00:14:44:05 - 00:15:11:07
Jens
I don't I don't know how to articulate it, but somehow, like you, you can have some sales. It can
work to some degree. But but somehow you you I don't know, every deal takes forever. It's it's
complicated. And, somehow you're you're not speeding up and, Yeah, the question is Stefan.
Where where does this problem actually come from?
00:15:11:10 - 00:15:35:05
Stefan
It's a great question. And you mentioned sales and a lot of people get sales wrong because
sales isn't about forcing your solution down someones throat. it's really listening to people and
figuring out, hey, what is the biggest problem? Why is this the biggest problem? Why is this a
problem within the company? And to a little iterate on the lack of pmf like it's so interesting.
00:15:35:05 - 00:15:53:23
Stefan
Everybody will tell you this is like how it feels. And I think you just described it. It feels off, you
know, like you come in to work, there's some sales, there's some growth, but everything just
feels kind of slow versus the opposite where there's sales, a lot ,things are breaking. People are
moving fast, people are talking about your product.
00:15:53:25 - 00:16:16:23
Stefan
And this really comes down to is really listening to your customers or to your users and to really
figuring out what they want, but also what the market wants. And your analogy is great.
Everybody says it's like a startup is that you can't push your way into the market, but you can
kind of get there or whatever. But if the market's not pulling you in, you're going to have a really
hard time.
00:16:16:29 - 00:16:36:04
Stefan
But I think to answer your question, where it comes from is, is that when like when people are
feeling the lack of it is that they're not feeling the pull, that they're not listening to their customers
and they're not truly understanding what these people are doing their day to day and what they
want from a product. What do you think?
00:16:36:07 - 00:16:58:01
Jens
What what would you say is the, the the best way, how customers can vote, how how can they
very clearly say their opinion? Well, what is the most obvious way? credit card Yeah. Look.
00:16:58:04 - 00:17:17:11
Stefan
As you know, we learned this the hard way. I'm going to tell small little story Jens. So when we
first started the SDK do you remember huge company. We were so excited with them. We had a
slack connect and they said, I'm going to pay. If you add this. So what do we do? We add this
and before you know it, they say, can you add this?
00:17:17:11 - 00:17:35:12
Stefan
Can you add that? Can you add this? And before you know it Jens, the entire company was
working to help this one customer frickin sign their credit card. it took us seven months. And I'll
never forget, like, we were a little bit down and I was like, don't worry, they're going to sign.
They're going to sign. And you were like, when it's been eight months, like, what the hell?
00:17:35:14 - 00:17:54:24
Stefan
And you know, we shut the door on them. We closed the slack channel and we moved to
Cosmo. Cosmo was built in three weeks, but by week two, somebody was paying for it. They
were paying for the excuse, my french, but the dog shit version, it was very bare. I don't even
know how they were paying for it, but they paid for it.
00:17:54:27 - 00:18:05:06
Stefan
And I think you're absolutely right Jens, if they're not paying for it, the credit card is not attached.
You're not solving something painful enough for them. You're absolutely right.
00:18:05:08 - 00:18:40:13
Jens
You know, the the funny thing is, connecting to this anecdote from Stefan. So, I think this this
week, a big, well known company signed up on Cosmo and paid us, immediately. They they
start with the small self-serve account, and they later they want to grow it. But the most
important thing is they they just signed up and paid and members joined, and they are now
building their graph with WunderGraph.
00:18:40:15 - 00:18:57:17
Jens
And what did we do this time this week to do it? Did we convince them? Did they come into the
door like, well, how did the because I wasn't even involved in the sales process. But but what
did you do to make this work?
00:18:57:19 - 00:19:14:08
Stefan
And just for clarification, this is the same company that a year and a half ago wouldn't pay us
and we just kept building features for them, so we completely stopped talking to them. We went
all in on Cosmo, and the only thing that happened is we would have conversations from time to
time, but about football, about football. Yeah.
00:19:14:08 - 00:19:35:12
Stefan
So we were talking about football. And then what happened is we actually solved a problem for
that. A problem they are willing to pay for. That's the biggest difference, is that we didn't talk to
them. We went all in on the solution and we were listening. And while we were listening to our
other customers, this customer also had the problem our other customers have.
00:19:35:14 - 00:19:55:25
Stefan
But it was a big enough problem and they attached their credit card to it. And right away they
validated our solution, which was, hey, we're solving this problem. We could have spent, by the
way, with the SDK years trying to convince people. But you cannot convince people to buy
something. You can, sometimes. But what's going to happen is they're going to churn because
they're going to realize it's not a good fit for me.
00:19:55:27 - 00:20:00:05
Stefan
And I think you're absolutely right, by the way, we talked about football. That's all we did.
00:20:00:08 - 00:20:10:13
Jens
So you would say product market fit is someone comes to your website and then they click a
button and buy the product.
00:20:10:15 - 00:20:21:27
Stefan
Product market fit is it's very different definitions, but it's you're solving a pain big enough that
people are willing to pay for it. That's my definition of it.
00:20:21:29 - 00:20:45:28
Jens
And today we want to talk a little bit about the TAB because, yeah, I think it's super important to
share some experience and how to actually get there because, you know, a lot of the time you,
you hear people saying like, yeah, you just need to find product market fit, iterate, blah, blah,
blah. But the real question is how do you how do you iterate?
00:20:45:28 - 00:21:11:20
Jens
How do you how do you get there? Before we talk about that, I want to share, like in an open
secret that we figured out because I think it's, it's just, I don't know, I yeah, I want to to, to help
others also also find out something. We had a super interesting call, I think was it yesterday or
the day before, like 1 or 2 days ago?
00:21:11:23 - 00:21:54:20
Jens
We, we had a call with a company, enterprise company in healthcare space. And, what, what we
figured out is, you know, we had discussions before about the topic of open source versus
closed source and things like that. And, what what we learned from the from the market
because it's, it correlates to, to TAB and everything but one, one big thing we learned and we
we we took a bet on this is when you think about enterprise sales, one of the biggest hurdles in
enterprise sales is there are engineers in a big organization.
00:21:54:22 - 00:22:28:23
Jens
They are interested in solving a problem, but they cannot try it out. They cannot learn about
your solution. They cannot get experience because their organization blocks them from trying
something out. So we were talking with them and they were looking into another solution from
another vendor, like different market. They were trying to try. They wanted to try it out and for
more than eight months, their company blocked them from doing anything.
00:22:28:25 - 00:22:59:16
Jens
And we we see this with with other companies as well with banks or something where we're,
we're simply like, yeah, they they want to do something. They want to try something. It's
ridiculous. But we, we, we had a sales conversation with, with a very large bank. And, what they
did is they did a POC with Cosmo, but they couldn't use their own graphs because during a
POC, they can only use like, play graphs.
00:22:59:16 - 00:23:34:22
Jens
So they, they kind of used, like, dummy subgraphs just to get experience with, with the, with the
software. And in both cases, the enabler to even get to the point where we can talk to them,
where they can build the experience with Cosmo, the enabler was open source. And yes, we we
did this in the past or we we did a we made a bet in the past and we were like, open source is
the right way, especially for for infra like we want it to be simple.
00:23:34:22 - 00:24:13:25
Jens
People should be able to try it out. And as it turns out, open source is is such a big enabler, for,
for enterprise sales, because open source means if you are in this healthcare company and you
you don't have to wait like eight months or longer to get, permission to, to to sign up with a
proprietary service, you can just download it, you can Docker run it and I think, you know, one of
the biggest fears of people with open source is, but how will people pay for this?
00:24:13:25 - 00:24:44:15
Jens
Or will they ever pay? And to, to answer the question, or to, to to answer something to, to that
fear. I think there's two components. One component is there will be people who won't pay you
ever. And you just have to accept it because if you make something open source or closed
source, if you make it open source, they will use your solution.
00:24:44:18 - 00:25:08:16
Jens
If you make a closed source, they will use another open source solution. So you can decide if
they should use your solution or something else, but they still won't pay you. And then there's
the question. If you have a managed offering, is there any value in the managed offering? And
for example, in our managed offering, like Cosmo, it's complex.
00:25:08:16 - 00:25:37:17
Jens
You have key cloak, you have Kafka, you have clickhouse you have other components. And for
some people, there's enough value in having this managed. And then what we are also doing is
we have, a line, for example, we say in our cloud version, you, you will not get, like advanced,
role based access control or you will not get things like SSO or skim or you will not get audit
logs or something.
00:25:37:23 - 00:26:05:24
Jens
We think that's like an enterprise feature. So there is like a, like a line and then people can
decide, okay, do I want the managed solution with those extra features, or do I, do I not care?
Another capability we are offering on our cloud is for every customer we have, a schema
registry internally, like a private repository where we, where we store all schemas and all
operations for all customers.
00:26:05:27 - 00:26:30:20
Jens
So before every single release, we're testing automatically against all their schemas that this
new release won't break anything. So we can tell our customers like you can you can safely
upgrade to this version, depending on what kind of company you are, this can be valuable. If
that's not valuable for you, it's it's fine. Like you don't have to buy.
00:26:30:20 - 00:26:47:12
Jens
I.
So, Yeah, just just wanted to, to bring up like the, the topic of, of open source. And I think our
open source is an enabler for, for an enterprise sales funnel. Stefan. Any any comments? Yeah,
00:26:47:12 - 00:27:03:04
Stefan
Have a couple of comments on it. And then after that we'll jump into the TAB. But, on open
source, I think you're absolutely right, because these companies are able to try it out. And this is
just kind of for any software as well. Like if you take lovable, for example, it's just a web app.
You just it's not even an app.
00:27:03:04 - 00:27:22:13
Stefan
You just go there, it's a website and right away you can start building things. And if you make the
path to, hey, I want to try this out to wow, this is really cool. The sales cycle gets a lot shorter.
And for example, that health care company, they talked to us eventually, but they came already
with a background.
00:27:22:13 - 00:27:41:12
Stefan
Of cosmo, now what they've done to run it, they've set it up in a staging environment. And if you
compare yourself to a closed source solution, you're eight months ahead. So they have to go
through SoC, whatever. So the opportunity for them to close a few is much better. And I think a
lot of good companies do this well is they have a great open source offering.
00:27:41:12 - 00:28:02:22
Stefan
And it's it is a funnel, but it's also not a funnel because open source takes maintenance. So it's,
open source takes collaboration. You have to run it. You have to make sure that there's no
security issues with it, and you're offering it essentially for free. But where the value is, is in, in
the managers offering, which is, hey, do you really want to focus all your time on running this
open source piece of software?
00:28:02:24 - 00:28:14:03
Stefan
Do you want to be late on release cycles? And a good blog post is Brendan just wrote about this
is when is it time to leave open source? When is it time to like have a connection with
somebody? And the reason that you just said.
00:28:14:03 - 00:28:15:18
Jens
Is.
00:28:15:20 - 00:28:31:27
Stefan
How can I ensure that when I put this into production, that nothing will go wrong with it? Well, it's
probably having a connection to the company that runs and maintains it at scale. And also they
probably have some internal stuff, some internal test suites from other customers or things like
that to make sure that this doesn't break for their customers.
00:28:31:27 - 00:28:56:27
Stefan
And so I think you're spot on there. Open source is fantastic, one, because if you really like
open source and you get to work on open source, it's amazing. You get to collaborate with some
of the biggest companies in the world. But two from a founder point of view, it just lets people
get running with your software. And Jens, if you want, I think we should talk about it a little bit,
like what's coming soon to WunderGraph Cosmos, which is, you know, we have Cosmo.
00:28:57:00 - 00:29:07:08
Stefan
It's a complicated stack, you know, and people might think like, oh, it's complicated because you
push people towards managed or whatever, but you have some plans actually around that, don't
you?
00:29:07:10 - 00:29:51:13
Jens
Yes. So, because of our experience, where we where we kind of figured out that the faster
someone gets to. This is awesome. The the, the more likely they will at some point end up in our
sales funnel. So the more likely they they will finally, you know, an engineer running Cosmo
locally, open source. This is the first step in the funnel, and I'm not I don't mean this in the
negative frame, but, you know, like, sometimes sales has this negative connection or like, yeah,
I don't like it because ultimately you have someone they try like an engineer try something out
locally.
00:29:51:13 - 00:30:13:18
Jens
It works. It solves the problem. They bring it to the company and then at some point the CTO or
the the, the security guys, they say, hey, this is awesome, but can we do SSO? Can we do this?
Can we do that? And then managed solutions, something that that suddenly makes sense. Like
we offer a soc2 stuff like that.
00:30:13:20 - 00:30:41:19
Jens
So for me, the first step is we want people to, to be successful as fast as possible to, to be able
to, to try it out to, to get to success. And what are we going to do? We will trim down Cosmo. We
will build kind of like a Cosmo Lite version where we remove some of the more complex
features that have heavy dependencies.
00:30:41:21 - 00:31:21:24
Jens
And the goal is you will have the control plane, Node.js, and you will have a Postgres
daTABase, and then you have the studio, the front end. So three components, we bundle them
together and we give you Cosmo Lite and it won't have like maybe the the analytics or other
features that that rely on on Keycloak. Click house and it won't have like SSO which we're
implementing with Keycloakg and it might not have like the full the full feature set of of Cosmo,
but it might be good enough for for many cases.
00:31:21:27 - 00:31:42:16
Jens
And we, we kind of also figured like some people, they just start out with Federation. They don't
need the whole thing. They, they actually just want a schema registry and a router. And, if you
think about it, you know, you can try to force everybody to be your ICP, but they, they they just
earn your ICP.
00:31:42:18 - 00:32:08:24
Jens
Leave them alone. But maybe they can become your ICP in the future. Are they they let's say
someone moves to another company, then maybe that company could could be ICP. So yeah,
the the goal here is with Cosmo Lite. We we want to we want to help engineers to get started
more more easily. And if they if they are not ready to buy our cloud, it's it's it's fine.
00:32:08:24 - 00:32:13:10
Jens
But, if they want to do Federation, do it with Cosmo.
00:32:13:13 - 00:32:30:14
Stefan
I like that. And it kind of transitions into where we're going. So the topic of today's episode is a
TAB, a technical advisory board, and not only do I think this is great if you have a company, I
also think this is a great for personal. Like if you want to improve yourself, you should probably
set up.
00:32:30:18 - 00:32:59:29
Stefan
It doesn't have to be technical advisory, but a board of people that you trust or people that you
want to learn from, or people that you want to sell to, or people that you just trust that can give
you feedback back, people that will give you unfiltered feedback about your product or even
yourself. And so what the technical advisory board is, is you create imagine like a board of
people, like the board of directors at a company or just a board of people that give you their
feedback and you set up every two weeks, meetings on the same day.
00:32:59:29 - 00:33:18:08
Stefan
So we do Thursday, and sometimes we do Wednesday afternoon because our schedule is a
little bit different. But Wednesdays and Thursdays every two weeks, I think Jens has six
meetings a day. And with these people, it's a 30 minute zoom meeting and it's no show and tell.
For the first couple weeks. You don't show them anything about the product that you want to
build.
00:33:18:10 - 00:33:38:16
Stefan
Instead, you just talk to them and you listen. And we'll take it from the technical advisory board
of what we want to do, and we just talk with them and we understand their day to day. And it's
important that you build your TAB with people that you think could potentially benefit from your
solution. So we have principal engineers, we have CTOs, we have architects, we have senior
developers.
00:33:38:16 - 00:33:56:27
Stefan
We even have a couple of junior developers. But we have that whole range on to there.
Because the problem that a junior developer has is completely different than a problem that a
CTO has, but you still want to talk to them and understand what it is. And this is from actually
Adam Frankl. He's this, developer marketing guy, this guru, and it's kind of amazing.
00:33:56:28 - 00:34:15:29
Stefan
Like, we set it up and already in the conversations, what you're seeing is things that we're
already working on. But it's so cool to see a customer say it in their own words in a way that you
probably didn't have in your head. And so each meeting that you have every two weeks, the
vision of what you're building, it's clear, clear and clear.
00:34:16:01 - 00:34:36:03
Stefan
And a little anecdote about this is if you ever heard of a company called zip, which is a
procurement software, they built a TAB when they first started of ten procurement people and
they had them pay. By the way, this was crazy to me. They had them pay and they said, I'm not
going to give you the solution yet, but I'm going to give you the best solution in six weeks.
00:34:36:03 - 00:34:49:07
Stefan
But I need you to trust me on this. I need you to be my design partner on it. I'm going to build it
to exactly what you want, but let me, like, talk to me about the biggest problems that you have.
And so for six weeks they worked very closely with these people, this TAB. And they built the
product.
00:34:49:07 - 00:35:06:03
Stefan
And now they're a series D company. And I think what we're doing with this world class TAB is
you're understanding deep down from all these members what their biggest problem is. And I'll
pass it off to Jens now because he's been the closest to them Jens. What have you learned so
far? What do you like about the TAB?
00:35:06:05 - 00:35:14:14
Stefan
What are some of the biggest, you know, antidotes or observations that you've seen that our
customers have been telling us?
00:35:14:16 - 00:35:48:07
Jens
First of all, I think building building a TAB, it's it's a lot about trust. So it's it's hugely beneficial if
you have already built a relationship. So with many of our customers, we we are now together
more than a year. Some of them have renewed already. And so we have built the relationship
with Cosmo. And obviously with the series A investment, we want to go beyond Cosmo, we want
to go further.
