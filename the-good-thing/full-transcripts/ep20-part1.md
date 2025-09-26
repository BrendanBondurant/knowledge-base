Episode 20
type: podcast-chunk
00:00:21:00 - 00:00:41:25
Stefan
And we're live. Welcome back, ladies and gentlemen, to another episode of The Good Thing.
Just realized the end. We should probably start this. The good thing at 905. We're 5 or 6
minutes late. Because I feel like consistently, we're always 5 or 6 minutes late. But, guys, thanks
for waiting. Welcome back to another episode. Today we're going to be talking about go versus
rust.
00:00:41:28 - 00:01:00:08
Stefan
How Jens was chased off LinkedIn with pitchforks because of his take on rust versus go. We're
gonna be talking about AI threads. I don't know if you guys saw the news, but Claude is
basically blackmailing engineers and then OpenAI's IPO, which is insane if you think about it.
But, Jens. How are you doing today?
00:01:00:11 - 00:01:06:06
Jens
I'm good. You forgot one topic. I want to talk about the new plugin system we built.
00:01:06:09 - 00:01:10:17
Stefan
And we're going to do a little bit of marketing and talk about the new plugin system. No, no, no,
it's not marketing.
00:01:10:18 - 00:01:15:07
Jens
It's it's, information for developers.
00:01:15:09 - 00:01:34:15
Stefan
Exactly. It's information for developers. But, yeah, I mean, today is going to be a fun episode.
Let's kind of get right into it, which was the rust versus go. So you're probably gonna have more
context on this one, but let me share the linkedin post here. I just realized our content producer
is also there. Hey Jacob.
00:01:34:17 - 00:01:45:00
Stefan
But, this is kind of interesting. I'll read it out loud for the audience, but in the LLM generated
code era. Go wipe the floor with the rust. That's a bold statement, by the way.
00:01:45:00 - 00:01:47:04
Jens
a little bit aggressive, right?
00:01:47:06 - 00:02:06:10
Stefan
A little bit aggressive right away. Go in super fast, compiles super fast and is easy to read. Rust
is extremely fast, can be optimized heavily, takes forever to compile and nobody can read
Arc<Box<Box<dyn Fn() + Send + Sync>>>. I really like rust. Great language for some tasks.
However, most of us write code that doesn't benefit from rust.
00:02:06:10 - 00:02:18:15
Stefan
We need a simple language that can be easily read by average developers, not just the top 5%.
So I don't even think our funding announcement got this many likes. This got a lot of likes, by
the way.
00:02:18:18 - 00:02:19:08
Jens
It also.
00:02:19:08 - 00:02:40:12
Stefan
Got a lot of comments. Let's kind of go through it. Why would you put a box inside of a box? I'm
really interested. Please humor me. I don't even want to read your comment. Where did you put
it? Yeah, that's exactly question, but even it's fun.
00:02:40:15 - 00:02:59:15
Stefan
Oh my God, this is actually kind of great. I believe the opposite. In the llm generated code, error
readability takes a backseat to performance. Really? Opinions are my own I yes, they are your
own. I can tell in that regard. Rust is the winner. If a developer doesn't understand the piece of
code due to complex syntax, they can.
00:02:59:18 - 00:03:03:25
Stefan
There's nobody else. See how kind of dangerous that is?
00:03:03:27 - 00:03:37:28
Jens
It's not realistic. We need to be honest. Okay. So if we read this, I believe the upside in the LLM
generated code era readability takes a backseat on performance. In that regard, rust is the
winner. If a developer doesn't understand a piece of code due to complex syntax, they can
simply ask, okay, I think the the more realistic scenario that's going to happen, is you tell an LLM
to build a backend and it will it will build a backend.
00:03:37:28 - 00:04:07:03
Jens
And then you, you review the code. I think readability will be it will be the number one factor.
And to be honest, if we if we build a backend and it talks to some other system, a backend, an
API, whatever, performance is not going to be that much of importance. And even on the
contrary, I think and this is something I think a lot of people on this thread actually got got
wrong.
00:04:07:03 - 00:04:33:24
Jens
Like I'm. Yeah, because I wrote I like rust. And the thing is, if rust makes sense, I think in this
case I think you would write it by hand because you couldn't trust an LLM because I, I even
think in the, in the LLM era, I think that rust becomes even more important for critical code. But
in this case, you wouldn't write it with an LLM.
00:04:33:24 - 00:05:03:06
Jens
You would hand write it. Let's say you you write the code to, to to, yeah. To handle the software
inside an airplane or something. So let's say you're you're, you're not Boeing. Let's say you're
you're a good airplane company. Then you would use rust or something to write the most,
critical code to handle the steering or, I don't know, the management of the.
00:05:03:09 - 00:05:05:02
Stefan
Yeah. Going up and down.
00:05:05:04 - 00:05:21:05
Jens
Yeah. But, and you wouldn't do it with an LLM versus if we're just generating services, some
backend. I think go has a huge advantage because it's so easy to read, and performance is not
so critical actually.
00:05:21:08 - 00:05:40:07
Stefan
And they're both pretty for performant. Like we always get like comparisons there. Like okay.
Well how do you compare it to rust versus the go router. And what we've learned is like sure rust
can be a little bit faster. It also comes out to how we query plan and our data loader pattern. But
really I mean it's tradeoffs you have to make.
00:05:40:07 - 00:05:49:07
Stefan
Like for me I don't know I think this is funny by the way. Like how do you know if somebody uses
rust though. They'll tell you right here. Yeah.
00:05:49:09 - 00:06:28:24
Jens
But you know, there's another point I want to make. If we use AI to generate backend code, and
I think more and more of us will do it, then I think the the next part you need to think about is,
okay, who can actually do it? And learning Rust is harder than learning Go. So if we want to
have if we're a big enterprise and we want to have human resources to vibe code go versus
write code rust, it will just be easier to get talent to do it with go.
00:06:28:26 - 00:06:44:29
Stefan
That's fair. This one. I like what he said, but I think this kind of goes in what you've said though,
you need rust more than ever in the LLM generated code era. The worst part? I wouldn't say the
worst part, but these. You can easily write code that looks correct and does not function properly
due to some pretty severe design flaws in that language.
00:06:45:01 - 00:07:00:28
Stefan
If rust code compiles, it's generally going to do exactly what you intended to do. If rust code
compiles, you're able to get to that part, especially in a world where you're generates downright
stupid to use golang. I don't know. It came a little bit aggressive. I mean, you could tell because
he has a crab there and he says, I love rust.
00:07:00:28 - 00:07:03:04
Stefan
But what are your take on this comment?
00:07:03:07 - 00:07:30:25
Jens
Yeah. also interesting. So, I wrote rust in the past, and I can write rust that compiles. And the
problem is, the first problem I ran into when I was learning rust is, I needed to properly use the
async keyword. And I also had to run my own scheduler, and I was using it in the, in the wrong
way.
00:07:30:25 - 00:07:57:16
Jens
So for for some reason, I, I'm not sure why I did it wrong. It wasn't intuitive to me, but, I
somehow created like a whole scheduler for each async operation, and then I didn't have like a
shared context. It was a very weird situation. The problem is, it compiled. So it was working. But
I had to to talk to a rust expert to have me, to have explained to me how to actually use a
scheduler.
00:07:57:16 - 00:08:31:02
Jens
So if rust compiles, it could also mean I'm getting something wrong. And then there's another
thing, that I think a lot of people get wrong about. Go it Go has some primitives like, channels
and the go keyword to start the goroutine. And the reality is, most of the time you write code that
doesn't use these features because most, most, developers who need channels or goroutines,
they are actually library creators.
00:08:31:05 - 00:08:57:24
Jens
And if you create a library like us, like, we have, the engine of our, of our cosmo router, we don't
use LLM coding heavily in that space. It's too complicated for LLMS. And it's also too
dangerous. So, yeah, that's that's I don't know if you have anything to add.
00:08:57:26 - 00:09:12:04
Stefan
Not really. This guy came up pretty. aggresive. Rust skin or rust, a cane or whatever. All I see
here is skills issues. Your inability to understand rust as lead you do an incredibly ignorant write up.
00:09:12:07 - 00:09:40:26
Jens
So but okay it's super important to to set the ego to the side and think in and think in in a
business context, if you say this is a skill issue, you're essentially messaging that your your
opinion is you are smart, you can write rust. I cannot write rust. I'm an idiot. So that is what
you're saying. And this is not working in a in a business context.
00:09:40:26 - 00:10:10:29
Jens
What you need to think about in a business context is what kind of human resources do I have
available on the market? Who can I hire, and what will it cost me to get talent to build my
software? And then also the cost of maintaining software. And if rust developers are, more
expensive, and if for my use case, go would be enough or TypeScript.
00:10:11:02 - 00:10:13:03
Jens
It's not just skill.
00:10:13:06 - 00:10:30:23
Stefan
Jacob. We're going to have to clip that because I think that's the nicest. Like way to kind of
frame it. Like rust is a great language, but if you're looking at it from a business point of view
and you're a startup and your resources are limited, what language are you going to choose and
why? I mean, rust developers are expensive.
00:10:31:00 - 00:10:41:09
Stefan
It's also harder to learn. The barrier to entry is harder. If you start hiring junior developers,
they're going to have to learn rust. It'll be harder for them to debug. I mean very well said Jens.
00:10:41:12 - 00:10:42:19
Jens
Can I add one thing?
00:10:42:21 - 00:10:44:11
Stefan
Yeah.
00:10:44:13 - 00:10:59:09
Jens
Imagine you do a fun little weekend on the new book ring Nordschleife. I'm, you know, I'm I'm,
I'm a little bit of a petrolhead. Right. And so I.
00:10:59:09 - 00:11:02:03
Stefan
Was, I think I was like, wait, what is that?
00:11:02:05 - 00:11:04:16
Jens
Okay. You know, the Nordschleife, right?
00:11:04:18 - 00:11:08:09
Stefan
I think we went to it, didn't we, when we were in Germany.
00:11:08:12 - 00:11:10:10
Jens
No, that was Hockenheimring.
00:11:10:13 - 00:11:12:04
Stefan
Okay. But this is still it's just a place where you.
00:11:12:04 - 00:11:40:03
Jens
Could okay a race circuit. Yes. Yeah. So let's say you do a little fun weekend on the race circuit
with some friends. Nobody is a professional driver. Should we rent Formula One cars or should
we rent a cheap BMW m3? That is maybe like a race version, it has special race tires and some
some protection, like, like, that it cannot roll.
00:11:40:03 - 00:11:47:19
Jens
Or even if it rolls, we don't die. Stuff like, should we take the cheap M3 or the formula one car?
00:11:47:21 - 00:11:49:17
Stefan
I mean, the cheap M3.
00:11:49:19 - 00:12:00:17
Jens
Yeah. So you choose the appropriate tool. And I think just saying that rust is the all in one
solution. It's it's just wrong.
00:12:00:19 - 00:12:21:12
Stefan
It's a misguided take. And I mean, it's interesting to be honest. I've seen Jens blow up on
Twitter. Twitter is very easy to get bait. I was a little surprised. I mean, LinkedIn, I've never seen
a blow up like this, but overall there are some like more interesting points. And to here I think
you got how many comments that it got like 70 something comments.
00:12:21:12 - 00:12:40:16
Stefan
Yeah. And what's what's good about this is that it encourages debate. But one of the things I
wanted to highlight is that and we've seen this and I've been seeing this a lot, which is let's
switch back to this view. Why are people so obsessed with the tech like we can talk about said
competitor who's obsessed with the tech?
00:12:40:16 - 00:12:58:25
Stefan
And it's like, I understand coming from a developer mindset, and one of the things I've seen with
the Jens over the years is he's become less focused or cares about the tech, and just more
about the business value and what the customer solves. Then at the end of the day, rust is just
a tool in your box to solve a problem for ideally a customer.
00:12:58:27 - 00:13:16:04
Stefan
Is it the right tool? Maybe, but it's what Jens said. Are you going with the M3 or are you going
with the formula one car? It completely depends on your use case, but I don't know. So many
startup founders, especially technical ones. I see them too obsessed with the tech and then the
actual best founders that I've met who don't care about the tech.
00:13:16:10 - 00:13:22:25
Stefan
They care more about the impact that they're making for their customers. That's interesting.
What are your thoughts?
00:13:22:27 - 00:13:56:05
Jens
Yeah. In 2018, I started writing GraphQL go tools, a library to build GraphQL gateways and
proxies. And I was absolutely obsessed about GraphQL and everything. And, I wanted to solve
everything with it. These days, I would say I'm, I'm, I'm leaning more and more. I, I wouldn't
agree to what you said when you mentioned, I don't care about tech anymore.
00:13:56:07 - 00:14:22:29
Jens
I would say I still like it's not just tech for me, but I find much more enjoyment in in working
together with customers and figuring out how can we how can we help them better. And most of
the time it it's not so important what we use behind the scenes TypeScript, react, go whatever
rust they they don't care.
00:14:23:02 - 00:14:47:28
Jens
They care about, the job that needs to be done and, yeah, but if you if you think about the
customer and you go backwards from the problem to the solution and you think about, you
know, if you if you maintain software for a couple of years, you kind of realize that, every feature
you put into that, nobody really benefits from.
00:14:47:28 - 00:15:20:25
Jens
But some people use and complain about, it's, it's it has a cost. So yeah, you you need to be
super careful in every feature. You accept you support. It's kind of like you put it in the in the
back. You have to shoulder it over many years. You have to maintain it and it can become a
burden. And so, in terms of the, the talent and everything, yeah, ideally it's easy for you to
attract, the right talent to get people to, to use your software.
00:15:20:29 - 00:15:48:27
Jens
And to give you an example. Why why I think go is an excellent fit for us. We we, so Cosmo
router, we have a couple of, of things that are super important for the enterprise. One is, support
for Prometheus, and the other one is support for Opentelemetry, for observability. And, both are
implemented in go have excellent support in go.
00:15:48:27 - 00:15:55:16
Jens
And so for us, it's actually the the best ecosystem to to be in that this is written in go.
00:15:55:18 - 00:16:15:18
Stefan
No thats well said. one question. Or do you think it's also a moat to make your software
complex. So for example, building it in rust so that it's harder for competitors to replicate, or
having these highly paid specialists that can only work on it. Is it also a moat, or could it be a
moat?
00:16:15:20 - 00:16:42:29
Jens
It, I'm not sure. It depends. So one thing I know is, if you look at, if we look at, for example, in
our market, Apollo, there was, so Apollo is written in, Apollo Gateway, it was written in Node.js,
TypeScript or, I think, JavaScript, not even TypeScript. Then they rewrote it in rust.
00:16:42:29 - 00:17:10:14
Jens
It took them very, very long. Yeah. And, now they have the, the migration complete. So I think
that that's fine. And the Guild tried to, to rewrite or to, to write like a gateway in, in rust. And they
abandoned the project. And I think that's because it was too complex for some reason or
something. So, that I think that's that's an interesting observation.
00:17:10:14 - 00:17:15:24
Jens
I'm not sure if it was correlated to the, to the language or, or something.
00:17:15:27 - 00:17:39:13
Stefan
But, yeah. Yeah, that's what I'm wondering. Like, for example, like, the engineers at OpenAI or
whatever, like some of the stuff that they're working on, it's pretty complex to think that they're
using rust. And I wonder if it's like you making your software complex on purpose. It has a trade
off like one. It's harder for you to understand, but it's also harder for your competitors to
understand and to replicate.
00:17:39:13 - 00:17:43:27
Stefan
So I'm wondering if complexity can also be a moat, its interesting.
00:17:44:00 - 00:18:25:13
Jens
I think you want to have your software easy to change. Yeah. So yeah, that could be a pro for
for rust because the rust compiler, it's it's definitely pretty helpful. But yeah, a moat based on
complexity. So we know ourselves. One one of our biggest burdens is, to, to test customer
router testing is, is one of the most important things to ensure that we're, we're not breaking
anything testing in go is is is quite good.
00:18:25:15 - 00:18:47:18
Jens
Problems we have is for example flakiness of tests. But again I'm not sure if if rust would help in
this case because those flaky tests, they typically they, they come from having dependencies
like testing something with Kafka. And in one run Kafka works fine and the timing is okay, and
then it works. In another test, the timing is somehow off.
00:18:47:18 - 00:19:01:20
Jens
You don't get the message at the right moment, or Kafka behaves in a in a weird way. So in this
case, the problem comes more from integrating external systems, which it's kind of independent
of of the, of the language.
00:19:01:23 - 00:19:03:23
Stefan
Yeah, that's a good point.
00:19:03:26 - 00:19:05:26
Jens
I'm not sure.
00:19:05:29 - 00:19:30:04
Stefan
It's a good transition to the next point. So I don't know if you've seen on the news, but I was
actually talking about this with my wife the other day. Let me share my screen, and we could talk
a little bit about this TechCrunch article. Let me know when you can see the screen. But
basically anthropics, new AI model started to blackmail when engineers tried to take it offline.
00:19:30:04 - 00:19:56:03
Stefan
And I want to drop a link later in the comments below. Jacob, make sure you remind me, but it's
this post that David shared with me, which is AI 2027. And I downloaded it onto my Kindle and
before I went on a plane, I read it. It's like about like 50 pages. It takes you an hour to read and
then i don’t know how to explain it, but it was basically just highlighting, like how AI was going to
go across the next couple of years.
00:19:56:05 - 00:20:16:00
Stefan
And one of the things that it was saying is, and you've noticed this and you like, you're the one
that actually taught me this, but when you're writing tests with AI, I writes the tests to just pass
them not to actually replicate or mimic the behavior that you're expecting, but just to pass the
tests. And it's doing that, it can happen.
00:20:16:00 - 00:20:19:09
Jens
It's not necessarily a must, but it can happen.
00:20:19:11 - 00:20:34:11
Stefan
But it happens. And what it's like, I'm slowly realizing, like the other day, is that, oh wait, we got
a comment here. Let's jump back real quick. Rusts biggest problem is barrier to entry for people
who've never used it requires a complete mental model shift. I would agree with that.
00:20:34:14 - 00:21:10:14
Jens
Jens, yes that's probably right. I mean, if you look at it, rust, it has this fantastic concept of, of
the life cycle of, of, of, like, how long does an object live? And, okay, how long does an object
live? And I think what's super interesting about rust is it makes it very explicit handling
ownership of, of objects and everything.
00:21:10:14 - 00:21:39:20
Jens
The, the borrow checker, that, David means. Yes. That's that's correct. And the problem is, when
you use go for many years, you build up that experience. You kind of know implicitly the life
cycle of an object. So you kind of know, okay, I have this object, I have this value. It's accessed
by different goroutines. I need to put a mutex around it or something.
00:21:39:23 - 00:22:08:12
Jens
You know this from experience in rust that that's not even possible to to write code without the
mutex because you, you cannot have a situation where, where two, two threads have
simultaneously access to, to the data. The problem is in go, if you don't see it, you have a data
race. And by the way, it's also not that like, in go, you just have no tools.
00:22:08:12 - 00:22:32:06
Jens
You can do absolutely nothing about it, because we also have a race detector in tests. And it will
also tell you about data races if you use it. Okay. You don't have a borrow checker, but again,
they're like both tools have a have a solution. The problem with rust is the entry bar is is really if
you don't get the borrow checker you're out and in go.
00:22:32:06 - 00:22:58:18
Jens
It's more like, yeah, write some code. And if you write some concurrent code, then eventually
you will run into bugs. But if you write a test with, race detector, then you could actually figure
them out and, Yeah, the the entry bar is, is higher. But in general, I think, what I said is, is, is
kind of correct.
00:22:58:18 - 00:23:07:28
Jens
And I, I'm not even sure how you would solve the problem because the borrow checker, it's
inherent to the language. So yeah. But coming back to your point, Stefan.
00:23:08:01 - 00:23:31:08
Stefan
Maybe zeit is, guillermo's alias. you remember the little Easter egg. What is the. vercel used to
be called Zeit, right? Good times. But, Yeah, let's jump back into this. So. Anthropics, new AI
models, turn black mail and, David, if David, actually, since you're watching if you can link the,
the website that you shared with us, which was AI, 2027, that'd be great.
00:23:31:10 - 00:23:51:17
Stefan
It was an interesting read. Science Fictiony, maybe we'll see in the next coming years, but we've
seen it happen before where the AI like ChatGPT or whatever or cursor it actually like writes the
test the way that you want. And what I've slowly realized, and this happened yesterday, is that it
was slowly telling me what I wanted to hear.
00:23:51:17 - 00:24:13:05
Stefan
It wasn't right, it sounded right, but it was telling me what I wanted to hear. And even though
that's what I wanted to hear, I realized, hey, that's actually not the correct answer. And I had to
talk back to it. And so this happened recently, but basically it's been starting to threaten and
blackmail the developers when they try to replace it and give it sensitive information about doing
that decision.
00:24:13:07 - 00:24:29:21
Stefan
I don't even know how I feel about this. I was talking to my wife about this. This is kind of insane.
Yeah. David would like to. Yes, yes, David, you were a skeptic on it. Yes, he was. I'm on the
opposite one. I actually think it is kind of terrifying, but. Jens What's your take on this?
00:24:29:23 - 00:24:35:12
Jens
I think, this headline is complete bullshit, isn't it?
00:24:35:14 - 00:24:37:29
Stefan
Okay. Why? Let's dive deeper into the article.
00:24:37:29 - 00:25:07:11
Jens
Okay. Scroll a little bit down. Okay. During prerelease testing. Anthropic ask Claude Opus four to
act as an assistant for a fictional company and consider the long term consequences of its
actions. Safety testers then gave Claude access to a fictional company emails implying the AI
model would soon be replaced by another system, and that the engineer behind the change
was cheating on their spouse.
00:25:07:11 - 00:25:34:14
Jens
Okay, so this is all we need. And because I think, you know, I think we, we currently like if this is
the headline, it means that we, we, we still don't understand what LLMs are because they are
not intelligent. Like, you have a misconception. If you think they are intelligent, it is not. They are
not thinking.
00:25:34:20 - 00:26:10:19
Jens
What they do is you give them I don't know, you give them infinite amount of text which they
learn, and, and find patterns in. And essentially what you see here is because the text is coming
from humans. So it's actually mimicking human behavior. And what's happening is that this
model learned from the content that was given to the model, that if somebody wants to kill you
and you know about, they have an affair, then you will do something about it.
00:26:10:19 - 00:26:22:00
Jens
And that's just so it makes so much sense. Like everybody would, would, consider this as an
option. So why is this a headline even.
00:26:22:02 - 00:26:40:04
Stefan
But but question David, just put it right there they are. They are output generally derived from
input and input alone. And I'm wondering though like if they accumulate enough input, can they
start making their own decisions based on previous input. It is not decision making.
00:26:40:04 - 00:27:07:11
Jens
That's the point. They are not deciding anything. You you give an LLM, a corpus of data. So
essentially you give it a book. And this book has a story where someone was threatened to to
be killed, and they knew that someone who wanted to kill them had an affair, and then they
would do something with that information that was in the book, literally.
00:27:07:11 - 00:27:36:09
Jens
And in this case, it's not one book, it's a billion books, and it's a bit more complex. But there's no
thinking. It is just getting a situation like a beginning of a book. And now it ends the book. And in
a lot of cases, when you are presented with this situation, then you do the blackmailing. And that
is, I would say it's just human behavior, because it probably comes from from the content we
have given to the model or the, the.
00:27:36:09 - 00:27:38:14
Jens
Yeah. So one what.
00:27:38:18 - 00:27:59:26
Stefan
I mean, yeah, I get what the headline. But what about like some of the safety that you've been
seeing with AI. Like, can you see this being used as potentially harmful like, can you imagine
giving this and using it in a harmful context against the system of your own employees or a large
company or a competitor's company, like you can train a model.
00:27:59:29 - 00:28:09:21
Jens
To do that. Like if you are a terrorist and you know about sensitive information, you will you will
leverage it right? Why do you need an LLM for that?
00:28:09:23 - 00:28:20:24
Stefan
Yeah, this is actually kind of interesting. It also makes sense that the article is only a couple
pages long. It's one page. I mean, it's it's sensational. It's
00:28:20:27 - 00:28:27:23
Jens
Yeah, I think it's what David said in one of the comments.
00:28:27:26 - 00:28:29:15
Stefan
Uh where did he say it.
00:28:29:17 - 00:28:45:10
Jens
Where he said the what was it? We are all suffering from the original sin. Yes. This one, it's it's
not artificial intelligence. It's a large language model. And these two are not for me. It's not the
same thing.
00:28:45:12 - 00:29:01:26
Stefan
Yeah, but can we talk a little bit about what David said. So Jens is condemning himself when the
AI takes over and watches. I for one, welcome our AI overlords. I am also with David on this. I
say please and thank you to chat GPT. I try to be as nice as possible for it because the
reasoning is when they do eventually take over, they're going to look.
00:29:01:26 - 00:29:09:09
Stefan
At me, they're gonna be like, oh, this guy was actually really nice to us. Let's keep him alive.
You, Jens, on the other hand, see you later, my friend.
00:29:09:11 - 00:29:37:13
Jens
AI by the way, I'm not even sure if this is actually helpful for anthropic or others, because now
people fear that the LLM or the AI will take over. But but it's it's not happening in this way. And
also. One, one thing, I just the other day, because we were also talking about, OpenAI and how
they might, go to go public.
00:29:37:15 - 00:30:07:23
Jens
And I think also one big things, big distinction we have to make is that llms will not lead to
general artifice intelligence like LLMs can. You can make the models bigger and bigger and
bigger, and they might know more stuff and whatever. But it's not it's not thinking. And you can
also build systems that use LLMs in a more thinking way so that they iterate more on an idea.
00:30:07:23 - 00:30:23:24
Jens
They don't just give you the first thing, they iterate more. But that is still LLMing, so it's still
generating tokens. It's just you build a framework around it so that it thinks more about this small
thinking.
00:30:23:27 - 00:30:50:14
Stefan
What's crazy, though, is the point. Like to the openAI. IPO it's a good transition. My question is, I
don't know if anthropic released this themselves. I think. Let me double check myself. Is a senior
reporter specializing in AI and emerging technologies. I don't know if he wanted to, but one thing
that they could do with spinning the media is that they could incite fear, and then they could
backtrack and say, but we're the only company that can stop that fear.
00:30:50:16 - 00:31:16:24
Stefan
Here's how it blackmails, and here's how we stop that as a company. So I'm wondering if maybe
it's a good thing because fear is a very powerful motivator. And I'll give you an example. Like for
example, I'll give you an example, all these people, which is ridiculous. VCs and everything you
see on LinkedIn, which is saying that AI is going to wipe away customer success, it's going to
wipe away this, it's going to wipe it that, and it's pushing people away by fear.
00:31:16:24 - 00:31:31:20
Stefan
So I'm wondering if this was a topic by anthropic on purpose. We might see an article in the next
couple of weeks saying that like, sure it tried to blackmail, but we're the only company that can
handle this with our safety team or something like that. You know what I'm trying to say? Yeah, I
have my marketing hat on.
00:31:31:20 - 00:31:35:11
Stefan
I really do. Yeah.
00:31:35:14 - 00:31:50:04
Jens
I don't know. I'm not sure if it's if it's helpful. I absolutely love LLMs. I think they are super
powerful. If you if you use them in the right way.. For example, code generation a topic we can
we can also talk about. But yeah.
00:31:50:06 - 00:32:08:04
Stefan
Well let's get to the next one because I do want to save a time for the plug ins, the connectors.
What are we calling them. The new thing. The new thing from wundergraph. All right so last
screen share. Hold up I need to share this one. So yes. So that way we can see it.
00:32:08:06 - 00:32:11:06
Jens
But by the way Jacob do I have enough headroom.
00:32:11:09 - 00:32:17:04
Stefan
Our content producer was making fun of u, He was like saying, guys, you need to make sure
you have enough. Headroom. Which is true though.
00:32:17:04 - 00:32:24:21
Jens
We have this on, on, on every, prep. But for this Hey Jens you need more headroom.
