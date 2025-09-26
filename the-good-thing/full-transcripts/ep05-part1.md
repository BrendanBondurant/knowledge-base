Episode 5
type: podcast-chunk
00:00:25:16 - 00:00:34:28
Stefan
And we're live. Welcome back, everyone, to another episode of The Good Thing, hosted by
myself, Stefan and my co-founder Jens. Jens how are you doing today?
00:00:35:01 - 00:00:42:08
Jens
Like with the words of Sergei. It's okay. For those of you that don't.
00:00:42:08 - 00:00:58:10
Stefan
Know, Sergei is our first, engineer ever. I wunder graph, and he was a founding engineer and he
doesn't speak much. He delivers like crazy, but he just says it's okay if something's not bad. It
it's okay if something's great. It's okay if something's bad, it's okay.
00:00:58:13 - 00:01:03:23
Jens
He has this Eastern European style. It's okay.
00:01:03:26 - 00:01:25:09
Stefan
What do you think about Eastern Europeans? I mean, me being from Serbia, like, I don't know,
we're known for not showing too much emotion, but. Which is weird because I'm American and
we like emotion. But, yeah , you should meet my dad one day Jens you would laugh. We're
completely different guys. Cool. But yeah. Yeah. Thanks for, I guess, joining me.
00:01:25:09 - 00:01:27:16
Stefan
I mean, you have to join me. This is our podcast.
00:01:27:21 - 00:01:33:15
Jens
You forced me to. Hey, Jens we need to do marketing. Come on the podcast with me.
00:01:33:18 - 00:01:51:18
Stefan
Yeah, it's true, but the people, the people like it, which was fun. But, I mean, we got some cool
topics today. So guys, today we're going to be talking about founder mode is it scalable versus a
founding team. Rest versus GraphQL is outdated. We're also going to talk about some drama
that we saw on Twitter, but also that we're facing with copycat competitors and benchmarking.
00:01:51:18 - 00:02:14:06
Stefan
And just calling out developer tooling in a like respectable way, which I think is BS because
developers like to hide behind, you know, calling each other out on technology. It's interesting,
but I think that's going to be a good content today. And then the last one is just the rise in
content. So yesterday, AVC invested into two content creators, $60 million.
00:02:14:08 - 00:02:29:03
Stefan
And one of their statements in the announcement piece was that founder led content and just
content from companies where it's not like about the company and it's just about the founders is
on the rise and we've seen it. So many other founders are posting more content like this, and it's
good that we're a little bit ahead of the curve Jens.
00:02:29:09 - 00:02:32:03
Stefan
But yeah, I'm excited to chat tday.
00:02:32:05 - 00:03:07:06
Jens
Yeah. I mean, wundergraph it's a it's a you could say dev tool like we don't we have a special
relationship with the word dev tool, but we're, we're, we have a product that that attracts
developers and traditional marketing is dead you need to go different ways and you cannot I
don't know, I think building the brand these days, it's it's very important to stay authentic and to
not actively push the product.
00:03:07:06 - 00:03:34:02
Jens
But rather say, you know, like a while ago, I said, the, the vendor like us. So we should be we
should be advocating the category, not the solution, the category. So we speak about federation
and how it's great. And then we let our customers with their stories speak about how they use
Cosmo. So that's kind of I think that's that's the, the modern, trustful marketing.
00:03:34:02 - 00:04:00:19
Jens
So let people decide with their credit card and talk about what they have decided and let us talk
about, how the how the category works and what you can do with it. And then people can,
decide if they if they like that or not. And, yeah, I think a podcast, podcast, like what we're doing,
I think that's, that's, a good way.
00:04:00:21 - 00:04:32:16
Stefan
I would agree. And the other day I, I watched this video, which was about creating content. And
the thing about creating content is that anybody can create content. It doesn't matter what age
you are. And I think everybody should create content because everyone has unique life
experiences and everybody is experience something that maybe other people havent. And this
analogy that I saw was really helpful, which is that imagine you're in a line of people when you
create content, you're sharing your experiences for all the people behind you that are not where
we're there are not where you are.
00:04:32:20 - 00:04:47:04
Stefan
And so you're helping them get to where you are because they would love to be where you are.
And then you obviously want to get ahead of the line, and there's 50 people ahead of you and
they're creating content. And so you want to get to that point. And so if we all created content
and just passed it back, it's just a unique learning experience.
00:04:47:04 - 00:05:04:18
Stefan
And I think this founder led content that we're doing is super helpful because I'll be honest,
Jens, three years ago, I don't think you would have done a podcast. You you were not very, you
know, you were more like traditional developer. You were great with customers, but I don't think
you would have done a podcast three years ago.
00:05:04:20 - 00:05:29:09
Jens
At least not on my own. I think even today I wouldn't do it on my own because I think there's just
like different types of characters. I, I'm, I'm the type of character. If you start the conversation, I
will happily join the conversation. If there's no conversation and I'm there, there's still no
conversation. Just I don't know, some some characters are not starting conversation.
00:05:29:12 - 00:05:51:07
Jens
But if I go to a party and you don't start the conversation with me, I will drink one beer after
another until I'm drunk and I don't talk to anybody. Just, I don't know, I don't do it. But if you
come to me and say, hey Jens let's talk about Federation, then we can talk all night. But yeah,
it's like people are people are different.
00:05:51:09 - 00:06:06:24
Stefan
Yeah. And I'm the opposite way. Like, you could put me anywhere. And at the end of the night,
there will be people surrounding me. And I'm keeping that conversation alive. My, my wife is
always joking about that. She's like, wherever I bring you, I bring you to like, an influencer event
with nobody in technology. And like, you're just talking to them about stuff.
00:06:06:24 - 00:06:25:03
Stefan
And I was like, well, you can always relate to people about random stuff. Like, for example. Jens
always laughs whenever we meet a company in Europe or, I don't know, just somewhere based
out of like maybe London. I'm like, oh, do you guys support football? 99% of them say no
because they're developers. But eventually we do get 1 or 2 and then we talk about football and
it's honestly, it's a good bonding moment.
00:06:25:03 - 00:06:46:20
Stefan
That's why I like, like being able to do this podcast and create content. And then honestly, it's
fun too, because we brought Dustin on the podcast two episodes ago. And, you could you could
see him getting out of his shell. Like, Dustin is typically like an architect, CTO, but when you get
him to talk about stuff like this, you can see how much more fun it is to get to know the people
behind the product.
00:06:46:20 - 00:07:06:14
Stefan
And our customers have said the same thing. They're like, I really enjoy your episodes of the
podcast. Which one makes us keep doing it, Because customers are saying that they like it, but
also to it's cool to see the people like again behind the product. And I think that's what's really
important about content from founders is that behind wundergraph Cosmo, there's actually
people with personal lives.
00:07:06:14 - 00:07:12:22
Stefan
There's people that are doing this with a passion, and you don't traditionally see that from big
companies, right?
00:07:12:25 - 00:07:40:03
Jens
Yeah. You know, I, like most people don't care about you. Everybody is busy. Nobody cares
what you're doing. Nobody cares. That wundergraph has a new feature, but people are super
interested in the story, in the struggle, in the how did they get there? How? How did they help
someone go to the Super Bowl with their API? Yeah, it's it's stories.
00:07:40:03 - 00:08:10:15
Jens
And, just one thing I wanted to to pick up before I forget about it. You mentioned just start with
content. And here's the thing. You like one of your friends, David K piano. He said this a while
ago. Everybody can record the video just just record it. Even if it's bad. Just record it, put it on
YouTube and then record the second one and make a third one, and you will hate the first ones,
and eventually they will get better.
00:08:10:15 - 00:08:36:10
Jens
And this is for example, like I'm not so like the, the, the video guy, but with you Stefan, it's it's
okay. But I love to write blog posts. And, when I started like a couple of years ago, it was hard
for me to write, and I, I really didn't like my first blog post. But if you write more than 100 blog
posts, then you can more or less write a blog post in your head.
00:08:36:12 - 00:09:01:21
Jens
And the typing in the end is really just like like, yeah, putting it in paper. The rest is already done
because you, you have created like a structure in your head, how to write blog posts and so
yeah, it's so many skills. If you if you want to get good at something, start with it. You will suck
and then do it again and you will suck again.
00:09:01:21 - 00:09:07:21
Jens
Then do it a couple more times and you will suck less and eventually it will be good.
00:09:07:24 - 00:09:25:12
Stefan
And that's crazy that you bring that up. So like every once in a while, like people see like the
success of like Wunder Graph, like my friends from college and they're like, wow. Like the top
on a call. Like, I want to know what you're doing. Like, what are you doing differently? And I
always tell them the same thing is that in the beginning of the day is a Wunder Graph, like when
we were doing this on the side when, you were working your full time job.
00:09:25:12 - 00:09:44:19
Stefan
I was working my full time job. You told me it's like taking spaghetti and throwing it against the
wall, because you can see when it sticks, that it's ready, that it's good to eat. It's all done. But if
the spaghetti falls, it's not ready. And people over overcomplicate things. If you want to get good
at programing, start typing.
00:09:44:25 - 00:09:58:09
Stefan
If you want to get good at soccer, start kicking the ball around. If you want to get good at
content, just start making videos. And it's exactly what you said is that if you want to start
building a startup, the first thing you have to do is just start. Start something, try everything that
you can, and eventually you get good at it.
00:09:58:09 - 00:10:17:23
Stefan
And it's the same thing with sales. Do you remember our first sales call and then now our any
call that we do? I actually don't even remember it actually. Two. But point is on a sales call, I'm
already seeing stuff that's like, I know what to do. Like I'm already seeing the patterns. I'm
already knowing exactly what to do in it because it comes from actually taking the calls.
00:10:17:23 - 00:10:36:03
Stefan
And for me, I think people overcomplicate it because stop thinking and just do. And I think that's
one of the biggest things that people struggle with is they like are thinking theory, like, oh, how
big is the market? How big is this? How big is that? And it's like, dude, you'll never know if you
don't start. You might create a whole new market if you just would just start the frickin product.
00:10:36:06 - 00:11:02:01
Jens
Yeah. You know what's so funny? In the beginning, when we started with sales, I was always
afraid. Afraid of getting rejected. Today, I want to be rejected. Like I actively pursue being
rejected. Because the very last thing you want to end up is in a situation where you have a
potential customer who will never be a customer.
00:11:02:03 - 00:11:22:02
Jens
Like, you know, in the past, I really feared asking the credit, like, you talk to a big enterprise and
you knew you're too small. Like we're two people. Like they will never buy from us. We knew it,
but we wouldn't ask because we were afraid of losing that opportunity. So we didn't ask. And
today we're like, hey, you.
00:11:22:03 - 00:11:51:01
Jens
Like, I don't know, whatever. We're just very upfront, like, hey, we're we're this and that. Is that a
problem for you. Like, can your company deal with that situation? And, and, they say yes, they
say no. If they say no, you have time for all the other leads. So, yeah. Why waste your time with
an opportunity that that's, you know, do you remember that one company where where one
developer was he he kept pushing us towards?
00:11:51:01 - 00:12:22:11
Jens
Yeah. Building more features so that eventually he could convince management. And we we just
couldn't tell him. Dude, either we speak to the manager now, or we have to assume that we're
not bringing any value to your company, and you're not ready to pay for what we're doing
because it doesn't have the value that you're you're willing to put the credit card, but yeah, you
have to you have to learn this right.
00:12:22:14 - 00:12:37:23
Stefan
And that was a rough time because I think you said up perfectly like just get to the no. This is
even also good. And like just life. Like you see a cute girl, go ask her out. The worst thing she
can say is no or maybe she says yes. Just try to get to know. And you taught me this.
00:12:37:23 - 00:12:44:16
Stefan
Actually, in a sales negotiation, the no is the start of the negotiation. The worst thing you want is.
00:12:44:19 - 00:12:46:12
Jens
Explain to me what's the problem.
00:12:46:15 - 00:12:47:29
Stefan
Exactly? You want to get the.
00:12:48:00 - 00:12:55:13
Jens
You cannot use us? Why? Explain to me what's the problem? Oh, we security. Yeah. We have
soc2 and then.
00:12:55:15 - 00:13:11:18
Stefan
It opens it up. That's the way the negotiations start. The worst thing you want is what we had
with this customer, which was a maybe. Oh, we like your product, but if you add this, maybe I'll
introduce you to my manager. And so for six months we're adding features we're building for this
giant enterprise. They're, they're a fortune something company.
00:13:11:18 - 00:13:27:21
Stefan
They're publicly traded. And it was one guy. And eventually I got to the point where we built
everything and he's like, oh, can you add it on the edge? And we were like, okay, you know
what? Like we how long did it take? I think we worked with him for a whole year building stuff,
and we never got a single dollar from this company on.
00:13:27:23 - 00:13:39:09
Jens
What what's the what's the the big, competitor than your competitor, like, how do you lose most
deals? And it's not the competition. What is it?
00:13:39:11 - 00:13:42:22
Stefan
How do we lose the most deals? I mean.
00:13:42:25 - 00:13:45:05
Jens
I put you on the spot right? Yeah.
00:13:45:05 - 00:13:48:05
Stefan
Well, it depends, like, how do we lose? Sometimes it is to the competitive knowledge.
00:13:48:05 - 00:13:50:15
Jens
You just forgot it's indecision.
00:13:50:17 - 00:13:53:10
Stefan
Oh, yeah, 100%. Especially if it takes too long.
00:13:53:12 - 00:14:18:13
Jens
They come to you somehow. The sales process, it's not working like you want. And then they
are like, we're not moving forward with the project. That's. Yeah. You know, you you fucked it up.
You, you you made a mess. And this typically happens when you when you did not fully
understand what the customer's trying to do.
00:14:18:17 - 00:14:37:08
Jens
Because and this is like I would say, I don't know, I'm not a salesperson, but we, we we have a
little bit of intuition about customer comes to us as we want federation and we say we can do
federation and then we show how awesome we are. And then after a while they say, oh, it's not
the right thing.
00:14:37:10 - 00:14:59:16
Jens
And the problem is customer says we want federation and then stop. Yeah. Take a few steps
back. What are you trying to do? Like what? What problem is this solving. Who is driving this
initiative. Where's the money coming from? Who's making the decisions? Like why are you
here? Why do you join this meeting? Why do you talk to us?
00:14:59:19 - 00:15:17:01
Jens
What? What is important to you? It's not really like is it the hair on fire or is it? Someone is
interested in trying out cool tech? Because you don't want to sell to people who try out cool
tech. You want to. You want to to solve the most important problem in that company. Yeah.
00:15:17:03 - 00:15:34:08
Stefan
I would agree to that one thing though. One that is indecision is the biggest like killer of deals.
But you also have to walk a fine line. So like right now I'm currently like negotiating with the
vendor to purchase something for wundergraph. And I got them down to the price that I want.
But they said that price is only active until Friday.
00:15:34:13 - 00:15:34:27
Stefan
You like.
00:15:34:27 - 00:15:37:25
Jens
You got them down. So are you buying or they buy?
00:15:37:25 - 00:15:38:27
Stefan
I'm buying, I'm buying.
00:15:39:00 - 00:15:40:12
Jens
You're buying okay. You're buying. Yeah.
00:15:40:18 - 00:15:55:22
Stefan
I don't want to mention the name because if we go with them. But basically they came in, they
were like all this stuff and they were like, oh, like I got the deal down to this price, but it's only
valid till Friday. And like, I get you want to squash the question. You want to squish the in
decisiveness.
00:15:55:24 - 00:16:06:27
Stefan
But there's also a way to do it. I don't like that pressure that that was put on me like, what would
you do there? I know you could talk a little bit about our sales process and how we handle
indecisiveness.
00:16:06:29 - 00:16:17:10
Jens
Yeah. Maybe it's a German or European thing, but if you hold the gun to my head, I would just
run away.
00:16:17:12 - 00:16:20:28
Stefan
It's the same thing. Like.
00:16:21:00 - 00:16:51:13
Jens
Oh, it it doesn't work. And I think the problem is this person fails to understand your motivation,
and they fail to demonstrate the value because you're like, no, no, no, the price needs to come
down and I need time to, to decide if someone needs a lot of time to decide. The value is not
clear, like if you can, if you can pay $1 and you get five, how long will you think about it?
00:16:51:15 - 00:16:52:15
Stefan
I'm not thinking I'm buying.
00:16:52:15 - 00:17:08:28
Jens
Simple, right? But if someone wants to from you like, I don't know, 500 K and you're like, I need
to think about it. Yeah, it's it's not clear how the 500 K will turn into 5 million.
00:17:09:00 - 00:17:31:05
Stefan
I think you just broke down enterprise sales and probably the most clear way I've ever seen.
Like, that's the biggest problem is that vendors are not demonstrating the value. And what you
can do is if you take away all the layers you want to pitch your product, that you give me $1 and
I will bring you $5. And when the value is so clear, whatever it is, it's so easy to make a decision.
00:17:31:06 - 00:17:48:14
Stefan
I think that's the biggest problem is indecisiveness comes because what you're doing is you're
evaluating the value and it's just not there. If you're still taking a long time to decide on it.
Because for me, if I purchase this, I'm putting my name on the line. I'm bringing this into
wundergraph. Same thing when people purchase WunderGraph Cosmo the champion.
00:17:48:20 - 00:18:04:14
Stefan
They're bringing this platform into their organization. Their name is on it. If things go bad, they
say, hey, Jens was the one that brought in Cosmo. That's clearly not doing a good job. Or if it
does go well, man, Jens. This is a fantastic product. Thank you so much for bringing it in. And
so you also have to do the emotional aspect.
00:18:04:14 - 00:18:14:24
Stefan
But I really like how you broke that down. $1 I give you $1 or you give me $1, I give you $5.
That's exactly the way you should pitch value with your product.
00:18:14:27 - 00:18:46:19
Jens
Yeah. Sometimes it's not so easy to see. Like if I adopt GraphQL federation and I pay a dollar
for it, will I get five? What will I get? Collaboration across teams. I will have better microservices.
I have this and that and this is the point where it can help if you have existing customers. So I
think like unfortunately the cheat code to startup success is to have customers.
00:18:46:22 - 00:19:21:21
Jens
That's and yeah, I just watched the documentary and it was about billionaires and the billionaire
said, yeah, I inherited some money and I had to do all this hard work. Yeah, of course, like,
dude, of course you did hard work. And also when you were young, your parents had all these
connections and they gave you this starting money and they helped you to get into circles where
nobody else like, the reality is, if you want to be successful, you need a network.
00:19:21:23 - 00:19:40:26
Jens
And you need, like, ideally, you have customers and you can you can, you can create or you
can derive customer stories, like what problems did you solve for customers? And then you go
to the next prospect and tell them, like, hey, do you have this problem? Do you have this
problem? They say, yes. And then you can you can teach them how.
00:19:40:26 - 00:20:06:26
Jens
That company solve this problem. So now it's actually clear how you get $5 from, from one or
more. And yeah. So it's a code. And because this is the cheat code, you need customers. So
how do you get your first customers? It's simple. Build any whatever build something like your
first startup idea is garbage. Like even if you think it's smart, it's garbage.
00:20:06:28 - 00:20:28:24
Jens
Because what you need is distribution. So build whatever gets distribution, build some sort of
distribution. Five customers talk to them, figure out the pattern like, oh, these five customer.
They have the same pattern. I build a new tool. I sold it and then I have five customers already.
So they pay you. So it's easier to upsell them to something else.
00:20:28:24 - 00:20:50:04
Jens
So you give them this new solution and then you you write a customer success story or you do
a podcast with them, and now you can go to other people and say, hey, we solved this problem
for these five people. So yeah, in retrospect, startup it. It's not so hard just yeah, I think and this
is something for technical founders.
00:20:50:06 - 00:21:08:03
Jens
Don't get hung up on your idea because your idea is garbage. Like even if you're a super smart
like, but your first idea is just whatever. Just just build something, distribute something, get the
customers. Because then you have a playbook of selling something and yeah, so I don't know.
00:21:08:05 - 00:21:27:02
Stefan
It's spot on. YC always say like their motto is build, build things that people want. And one of the
manifest in their manifesto, one of the rules is just have a small group of customers. It's better to
have ten customers that absolutely love your product, then 100 customers that are like, yeah,
it's not bad, it's okay.
00:21:27:04 - 00:21:42:02
Stefan
And the reason that they say that is because what you just said is that once you have a couple
customers that love your product, you start to open up network effects. They'll start to talk to
their friends about this product. Hey man, have you tried I wundergraph cosmos like you're
using Federation. It's fantastic. Try it out.
00:21:42:04 - 00:21:57:08
Stefan
You know this solves all these problems. And the second part is it's so easy to see patterns is
that you have this customer and you're like, oh, that's a use case. And then you talk to another
company like, oh, we actually solve that problem for this customer here. Look at this case study
that they did. And it makes the sale even easier.
00:21:57:08 - 00:22:12:14
Stefan
But then they're like and then in decisiveness and what you do is you take that customer and
you bring them into a call and you just sit back and just watch them talk. And what they do is
that they're selling your product in a non salesy way because they're actually collaborating
together. And that's also one of the benefits.
00:22:12:14 - 00:22:31:28
Stefan
And it's funny that you said billionaires because they all say the same thing like the first million
is a bitch. It's the hardest thing to do. And it's the same thing in startups. It's the hardest to get to
the 1 million ARR mark. It's really hard to get your your first customers that love you, but after
that it just scales up so easily because you have these customers.
00:22:32:03 - 00:22:50:09
Stefan
Same thing with if you make $1 million, once you get the first million, you invest a little bit.
Compound interest starts to take into effect. You make some more actions, you purchase some
real estate, and then after that, from the one to the 5 million to the ten, it just exponential growth.
But getting to that first 1 million is really a bitch.
00:22:50:12 - 00:23:28:03
Jens
And maybe one little bit spicy take to add opinions without a credit card are noise. So if you
have a startup idea and you go to your friends, they like you and they will say it's cool, I could
imagine buying it. Whatever, but they are not buying it. And the same as with developers who,
who, who show up on your open source repo and say, oh, it's great, I have an idea how you
could make it better.
00:23:28:06 - 00:23:54:19
Jens
And they're also not buying. They are not a customer. So I think if you want to build a great open
source project, yeah, of course you can listen to to like, I'm, I'm, I love open source, like open
source collaborations. It's great. I love it. But if you want to build a business, you you need to,
you know, it's it's it's a bit like, like, like giving a loan.
00:23:54:19 - 00:24:07:08
Jens
You need to underwrite opinions with money. Opinion without money. Just someone saying
words, not saying agree.
00:24:07:10 - 00:24:26:27
Stefan
I think, though, that only in the context of B2B. So like software and like selling to businesses
because do you think that applies for like let's say Facebook like Facebook didn't charge. And
the first thing that everyone told them was no ads. Who was it in the, The Social Network, I think
it was Edwin Stavros. He was like, you need to start charging for ads.
00:24:27:00 - 00:24:44:01
Stefan
And one of the other founders was like, no, get as many people as you can onto the platform.
Once you do that, you can figure out how to make money. Same thing with Uber. Their biggest
thing was growth. But I think that only applies to B2C. Would you agree?
00:24:44:03 - 00:24:51:21
Jens
I would say I don't understand B2C, but, ask people who do.
00:24:51:23 - 00:25:03:04
Stefan
That's fair. I also have one theory, though. Every successful B2B company eventually becomes
B2C. What do you think about that?
00:25:03:07 - 00:25:16:17
Jens
Every successful B2B company eventually becomes B2C. Yes. Interesting. Is Salesforce B2B.
00:25:16:19 - 00:25:20:01
Stefan
Kind? Salesforce? Yes. But look at them now.
00:25:20:01 - 00:25:21:16
Jens
Is it B2C now?
00:25:21:18 - 00:25:40:11
Stefan
Yes. Now they do for restaurants. They do for personal stuff. They do like this agent force AI and
they went from like typical enterprises to restaurants into smaller mom and pop stores, and
they're spreading their network as farther as they can, like yes technically it is still is B2B, but
they're going now further.
00:25:40:13 - 00:25:44:24
Jens
Is the the TAB to smal whats the issue?
00:25:44:27 - 00:25:58:14
Stefan
Know, I think that's a byproduct of being too successful is eventually like for example, if you're a
B2B company, to get to the utmost success, you eventually become B2C. You start to spread
out to everybody and you start to change things. I just a theory that I have.
00:25:58:16 - 00:26:08:19
Jens
plan?
Interesting. So, in the, in the, in the long term we will federate your mobile phone or what's your
00:26:08:21 - 00:26:36:13
Stefan
Yeah. I haven't thought about that yet. Like, like some theories are like with developer tooling
you should build for the enterprise, but also the individual developer should be able to use your
product. I don't think that's correct. True. Because individual developers don't like to pay for
stuff, which is totally fine. Our product is open source, but for us, what I think is, I mean, we
currently have like the number one, one of the most popular apps on the App Store is using
Wundergraph Cosmos to power it.
00:26:36:16 - 00:26:48:07
Stefan
It's the deal that we. Yeah, yeah, I'll explain to you afterwards. I can't say their name yet
because we don't have, the NDA, but I'll tell you afterwards. Well, the number one app in the
United States, actually, and you're going to like actually doing B2C.
00:26:48:09 - 00:26:50:25
Jens
At least we enable it.
00:26:50:28 - 00:27:04:24
Stefan
Yeah, kind of. But it's an interesting topic. Like, for example, like Salesforce. Yes. Like now
they're going out to B2C. And I'm trying to think of a couple other examples of like really
successful B2B companies.
00:27:04:26 - 00:27:10:23
Jens
So the way you argue is you make a big point and then you don't back it up.
00:27:10:25 - 00:27:30:10
Stefan
No, it's just a theory. Like it's a hypothesis. That's that's my hypothesis. I haven't figured it out
yet though. But yeah, honestly it's a good transition though, so let's go back to some of the
topics that we have today. Like for example, is founder mode scalable versus a founder team,
founding team. And for what it's like founder mode.
00:27:30:16 - 00:27:37:24
Stefan
Are you going to ask me of my definition or what? Like Paul Graham said,
00:27:37:26 - 00:27:39:21
Jens
Both. I don't know.
00:27:39:23 - 00:28:06:03
Stefan
So Paul Graham wrote this great, essay, and it came from him sitting at a, I guess, like a what is
it called, a fire fireside chat? And he was sitting down with the founder of Airbnb. And it's kind of
like counterintuitive, but it's also startups like startups are very counterintuitive. And so my take
on founder mode is doing what you're doing now with under 15 people.
00:28:06:05 - 00:28:36:22
Stefan
And you still do that when you have 1500 people. And for me, founder mode isn't
micromanagement. It's managing. It isn't over optimizing. It's optimizing. It's being involved in
the nitty gritty. Even when you still have 1500 people. And I think that's a superpower at the
beginning of startups is that, hey, for example, you can talk about today Jens like last week, you
went on a customer call with one of our smallest customers, and you came back with so many
insights of things that we can improve for them, that you definitely see some value for them as
well as for us.
00:28:36:23 - 00:28:49:27
Stefan
And so my definition is founder mode is doing what you're doing at the start of the startup and
also doing the same thing that you're doing when your startup is absolutely massive. What
about you?
00:28:50:00 - 00:29:27:09
Jens
To to pick up your case. I'm just wondering if you have a 1500 people organization, the CEO
should probably somehow be involved in making sure that these 1500 people do something
meaningful. Should they be doing support? I mean, yes, of course it would be super nice to be
hands on and understand the product, but you also at that stage you will also have like product
owners and yeah, I'm not sure how much you want to interfere with with these kind of people,
but yeah.
00:29:27:09 - 00:29:54:12
Jens
And then, you know, then then there's this other thing I wrote about it, like, a few days ago, the
scalability of founder mode and, I mean, for, for, for a very long time, we were a small founding
team. I would say like four founders and, and a handful of of founding engineers, and we, we
kind of expanded founder mode to this whole team.
00:29:54:12 - 00:30:17:08
Jens
And this is. Yeah, until today and even today, I would say, that that we were able to, to infect the
whole team to the to be at least somewhat informed, like I'm not expecting people to work
through the weekend or something. I that that's like, it's still a job. You have a life. It's I respect
that it's fine.
00:30:17:11 - 00:30:32:06
Jens
But yeah, I mean sometimes as a founder you you have to you have to walk the walk and thus
there's no way around. But, yeah, I, I'm, I'm not sure.
00:30:32:08 - 00:30:51:26
Stefan
I think you're right though. So at 1500 like obviously you won't be able to do support like you
won't be able to get in the nitty gritty. And you also want to hire smart people and get out of their
way. But it's what you just said. Like if you walk the walk organically, people are going to see
that and they're going to be like crap, like, look at what Jens is doing and it just motivates them.
00:30:51:26 - 00:31:10:19
Stefan
And it's like the the benefit of it is not to be a CEO is to be a leader. And leaders don't tell people
what to do. They show them what to do. And I think that's one key aspect that we have. at
Wunder Graph, is that these founding engineers have, in a way, become founders themselves.
You know, some of our engineers have shifted into parts of one graph, and they founded
something.
00:31:10:19 - 00:31:30:10
Stefan
They founded the composition, they founded the engine, and they own that. And they're the
startup owners of that. And I think the most successful startups are companies that are really,
really good, are actually an umbrella of startups where you just have founders all throughout
them and they own it and they build mini startups. What do you think?
00:31:30:12 - 00:31:56:21
Jens
Yeah, kind of, I was I was just thinking, what what makes us different? And, I would say one
thing that we really live is the way we do support. And, like, nobody pays for a support or
nobody wants to, like, nobody said, yeah, give me, give me the biggest support plan because
everybody just expects good support.
00:31:56:27 - 00:32:31:24
Jens
But one thing I realized over the last couple of months is somehow we have created an industry
in SaaS, where support is typically absolute garbage because everybody tells us our support is
is top notch, like ten out of ten the best. Like they recommend us so much and I don't know, it's
it's just our culture. We we as a company, we we we we do our thing.
00:32:31:26 - 00:32:53:20
Jens
And I think one of our core values is we, we want to do things right. If someone is not able to
use our product the way they they, they want to, if, if that's a problem or a use case, we're not
fully enabling it. It bothers us. And it's, it's like, yeah, we we want to enable it. And obviously we
you you have to prioritize.
00:32:53:20 - 00:33:21:12
Jens
You can't do everything at the same time. But it's I don't know, it's I would say that's a core
value. We really care and we you know, not not not you know, sometimes you, you, you you
might think about competition and everything. We don't think so much about competition. We're
mainly concerned about, like just today give you an example.
00:33:21:15 - 00:33:51:09
Jens
Customer ask a question. They say can we use cosmo router and add a custom middleware? I
want to manipulate the response that we're sending to the client. So one way you can take this
question is you can say, yeah, we have a custom module system. You can create a middleware
and then you can manipulate, the response. This is one way how you can not now you're out of
support.
