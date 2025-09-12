Episode 12
00:00:10:15 - 00:00:19:00
Stefan
You.
00:00:19:02 - 00:00:40:29
Stefan
And we're live. Hello, ladies and gentlemen, welcome back to another episode of The Good
Thing. I'm here with my co-host, Jens, and today we have an interesting episode. We're going to
be kind of just talking about beyond GraphQL, some observations that we got from some of our
friends at KubeCon. AI of course, and just more about GraphQL Federation and just scalable
API architecture.
00:00:41:02 - 00:00:45:02
Stefan
Jens, always a good to talk with you. Welcome back. How are you?
00:00:45:04 - 00:00:47:15
Jens
Hi Stefan.
00:00:47:18 - 00:00:50:21
Stefan
I come in with the energy and you're just like, hi, Stefan.
00:00:50:23 - 00:01:15:00
Jens
Yeah, yeah, I'm I'm, I'm a little bit under the weather, but it's fine. At least I can speak again.
And, but today is the. Today is, barbecue weather here in Germany. Okay. So this this podcast
is currently, in between me and the barbecue.
00:01:15:02 - 00:01:18:23
Stefan
Okay. And thank you, ladies and gentlemen. That's our episode today
00:01:18:26 - 00:01:29:04
Jens
that's fine.
No, no, it's it's fine. Like, it's, I would say, in in an hour and a half. It's it's barbecue o'clock, so
00:01:29:07 - 00:01:41:26
Stefan
You know, I love that I'm a big barbecue guy. I think you know that, like, growing up, my dad
barbecued every day. Not like every day, but like, every other day. And sometimes I would come
home and he is just barbecuing a whole pig. And I was like, why are you roasting a whole pig?
It's like, it's Saturday.
00:01:42:00 - 00:01:52:26
Stefan
It's like, okay, like can't complain, but no, that's awesome. But, thanks for joining us as usual. I
mean, you're my co-host, but one thing. I want to talk to you. I have no choice. Right? Yeah. No.
Yeah. We do.
00:01:52:27 - 00:01:56:05
Jens
We need to do the podcast. Can you come?
00:01:56:07 - 00:02:13:19
Stefan
But one thing going forward is that we are going to start introducing guests onto the show. And
so our amazing content producer, Jacob is going to be sourcing guests. If you guys are
interested in coming on the podcast and chatting about things, software engineering APIs,
GraphQL, or just startups in general, feel free to reach out to him at Jacob at
Wundergraph.com.
00:02:13:24 - 00:02:33:20
Stefan
But for the next couple of episodes, we're going to be having some amazing guests from some
companies that you guys know and use every single day. But today you're stuck with me. And
Jens. Let's start off with what we were talking about this morning. So one of our friends and feel
free to mention him. But he went to KubeCon and he gave us some interesting observations of
what he saw at KubeCon.
00:02:33:26 - 00:02:45:24
Stefan
And just kind of what happens each year at KubeCon. But I don't want to take your thunder.
Maybe explain what did he see at KubeCon? What is KubeCon and what trends do you see the
tech world going into?
00:02:45:27 - 00:03:20:23
Jens
So he said KubeCon was 13,000 people, so probably, quite crowded place. And he also said
that that, KubeCon it's it comes in waves or the topics, they come in waves and, yeah, this year
it's AI obviously. And, the big question you have to ask yourself is if you are, for example, in the
API space, do you actually want to be there?
00:03:20:25 - 00:03:52:24
Jens
It's not cheap. And, if everybody talks about AI and you don't really have an AI topic or. Yeah, I'm
not sure if you maybe if you implement some MCP thing, then okay, maybe that's enough AI,
but, probably people will be more interested in talking to the real AI players. So yeah, I'm, I'm,
I'm not sure that there might be better ways for a company like ours to promote API tooling.
00:03:53:00 - 00:03:57:29
Jens
So that's just, I would say the, the observation.
00:03:58:01 - 00:04:23:15
Stefan
And with KubeCon I mean, 13,000 people, that's that's a lot of people. And then with AI think
this is what I'm trying to understand. So like, I wasn't born, I was born before the dotcom burst.
But like three years I was just a baby. And what I've noticed is history tends to repeat itself. And
so you had the.com boom, and then you had the shift towards, towards cloud, and then you had
a shift towards mobile.
00:04:23:18 - 00:04:41:23
Stefan
And then now we're in this wave of AI that everyone is hopping on it, that you can see every
company is rebranding to AI. Where does AI come in to with APIs like APIs might not be sexy as
AI, but you can't have AI without APIs. Would you agree to that?
00:04:41:25 - 00:05:35:04
Jens
I mean, Anthropic and ChatGPT or, or open AI? I think they might make it very clear with MCP,
the model context protocol. That AI need APIs. And actually, I think MCP, it kind of stands for, AI
is useless if it cannot call APIs. And, like, you know, if you put ChatGPT in the box and you don't
allow it to access to the internet and you don't allow it access to your file system, you know,
cursor is AI with access to your file system.
00:05:35:06 - 00:05:37:05
Jens
So if you remove that.
00:05:37:07 - 00:05:38:21
Stefan
Its useless
00:05:38:21 - 00:06:13:28
Jens
AI to talk to your systems and to the internet. So no system is then I don't know, it's it's just,
really cool thing in a box and it's a toy. I think with MCP all of this rapidly changes and we can
do so many new, new, cool things. And, yeah, I think there's a, there's a big drive in the direction
of, of agents and, you know, like, well, one very clear thing that we observe so far is, you cannot
trust AI.
00:06:14:01 - 00:07:04:04
Jens
It does little things. It also doesn't think it predicts tokens, and it predicts tokens in a, amazing
way. Like in in many cases, it can really predict good tokens. But for example, like we're now
using AI at WunderGraph for, for, quite some time with this cursor and other tools and our
observation is that you define tests and you like if a human works test driven, they define tests
and they implement the tests and they actually have, they have an incentive that the tests work
because they know, like someone will review them and they, they like a human doesn't like
developers are lazy.
00:07:04:06 - 00:07:36:09
Jens
So if you write tests and then you implement code that makes the tests go green, but it's wrong,
someone will review it and tell you, like, hey, you need to do this again. It's it's it's garbage. So
humans are incentivized to write code that works. Combine that with tests and you can get good
code. AI doesn't care if you call it twice or a billion times.
00:07:36:16 - 00:08:01:20
Jens
It's just a program. So there's no incentive to write the right to write correct code at the first run.
And also, AI doesn't know what is correct and it also doesn't care. It predicts tokens. So you
write a test and then it runs the test and it sees, oh, it's failing. Let's do things so that the test
maybe doesn't fail.
00:08:01:20 - 00:08:41:02
Jens
And it can sometimes predict the right thing to do that. And sometimes what I saw is AI reads
the content of your test and then it, for example, puts code into your implementation that, that,
references things in the test and then it works like, for example, you need to parse the GraphQL
query and instead of parsing it, you just write code words like if the string is blah blah, blah blah
blah blah, blah blah blah blah, then do the following thing.
00:08:41:04 - 00:09:06:01
Jens
And now the test works because it looks like you had written the parser, but actually you're just
matching strings. Yeah, of course, to test the screen. But yeah. So I don't know, it would be cool
if, if, AI was incentivized to, to do the right thing. But again, what is the right thing? So yeah. So,
up until today, our, our jobs, are safe.
00:09:06:03 - 00:09:18:00
Jens
Right? So if you go tomorrow. But, I don't know, maybe we need some some sort of counter,
like, is our job safe today? Yes, but tomorrow we don't know it.
00:09:18:03 - 00:09:42:19
Stefan
It's a good point, but the thing that kind of I'm confused about, and I think it's what so important
about disruptive technology is that when technology is truly disruptive, all rules and all, you
know, principles that you had before, that they go completely out the window. And what I mean
by that is, for example, with Mac, you have to really give it access to your file system.
00:09:42:19 - 00:10:01:11
Stefan
Like any program that you install on Mac, you have to wake up mac with MacBook. Yeah, yeah.
If you go with MacBook and you want to, like install a program that has access to your file
system, you have to do a couple steps to do that, and you have to make sure that you give it
access. And what's crazy to me is, with like the introduction of ChatGPT and all these AIs is, is
all the rules went out the window.
00:10:01:18 - 00:10:28:03
Stefan
Publicly traded companies are giving access to cursor, to proprietary code, to proprietary
software that they've built in-house. And I'm like, what are your thoughts on the ethics of AI?
Like, for example, like, how are people just giving AI access to their file system, billion dollar
companies that have built up from the ground up on this proprietary software are giving it to a
brand new startup that, you know, just is just around.
00:10:28:03 - 00:10:41:02
Stefan
Like, how can we just give AI access to our code, to our billion dollar ideas, to everything? Isn't
that kind of scary? to you or not?
00:10:41:04 - 00:11:11:24
Jens
It might not be your desired answer, but, actually, I think there's not so much value in most code.
There's value in. We have a bunch of people who understand this code good enough, and we
can change it. And we have distribution and stuff like imagine I, I gave you the code of meta so
you don't have the data but the code.
00:11:11:27 - 00:11:15:15
Jens
So can you now build the social network.
00:11:15:18 - 00:11:16:20
Stefan
I don't have. No, no.
00:11:16:21 - 00:11:41:24
Jens
I mean you would you would have to change people's behavior to move on from meta to meta
one. Or whatever you call it. So yeah, we can give you the code, but maybe there's something
in the code that is more malicious. For example, that can be code, like an algorithm about the
feed or I don't know if people had the code.
00:11:41:24 - 00:12:03:02
Jens
They could somehow cheat to show more more ads or to prioritize ads or whatever. So there
can be harmful ways. But I don't know, I think most code could actually be open source,
because like the the moment you, you open source, it, it's kind of outdated because, you know,
we all have roadmaps like we don't live in the past.
00:12:03:02 - 00:12:28:18
Jens
Like, you know, if you if you look at Cosmo today, who cares? Who cares about Cosmo today?
Because we have a vision for Cosmo tomorrow. So, what is our moat? Our moat is the ability to
create this tomorrow. And we have customers, and we have we have a go to a market, and we
like all of all of this together.
00:12:28:20 - 00:12:55:24
Jens
It's it's kind of like, I don't know our our our our moat, I would say, but just the code. And that's
also why I think it's, it's so harmless to and even beneficial to to make Cosmo open source
because like more people can, can collaborate. But I would say in the, in the ecosystem of
tomorrow, like Cosmo, it will not stay our, our single product.
00:12:55:26 - 00:13:15:22
Jens
So we're, we're building a universe of products and, not all of them will be open source, but,
most and. Yeah, I mean, yeah, do with Cosmo, whatever you want. Yeah. Okay. It's. Well, said,
I, I completely went off the rails. No, no.
00:13:15:22 - 00:13:37:23
Stefan
I, I mean, it's typical. Yeah, it's well said. I mean, there isn't really that much value in the code.
Like, it's everything that you build around the code, the distribution, the brand, the network. And
it's exactly the same example. Is that okay. Like people always say, I could vibe code a
Salesforce in a weekend, like, yeah, you can, but there's no way you can touch the distribution.
00:13:37:23 - 00:13:54:21
Stefan
There's no way you can touch the brand of Salesforce. And so it's not even about the product
anymore. It's about everything around the product. But no, it's a good point. But with AI like and
what we saw in KubeCon and what our friends told us, like at KubeCon is with Federation and
AI and there is no AI without APIs.
00:13:54:24 - 00:14:14:07
Stefan
Where does AI fit into Federation? Where do you see it going and where do you see the
benefits of AI into Federation? Especially for people that are considering adopting the super
graph, people that are considering going into a micro, services architecture where do you see
the benefit of AI? There?
00:14:14:10 - 00:14:17:29
Stefan
And you can go off the rails for this one. It's okay.
00:14:18:01 - 00:14:31:03
Jens
Yeah. You know, I, I'm sometimes I feel like a politician. I have a message I want to send. You
ask a question I start with, yeah. Thanks for your question and then I send my message.
00:14:31:06 - 00:14:33:02
Stefan
But what's the message you want to send?
00:14:33:04 - 00:15:11:07
Jens
No. Okay. AI and Federation. So obviously obviously I say this so often, I'm not sure can even
be insulting because it's not always obvious. Like, to everybody. Okay, but if you have a super
graph, it means we have all your APIs combined under one protocol. Now with AI, it can be it
can be a challenge for AI to talk to many APIs with many protocols.
00:15:11:10 - 00:15:39:12
Jens
And if you let's say you give AI a task and it needs to talk to ten APIs. And so I think that alone is
a question is a is a challenge. And now imagine AI has to speak ten different protocols like soap
rest open API, Postgres, whatever. I think then then AI will struggle even more.
00:15:39:14 - 00:16:03:24
Jens
And I think it can be much easier for, for AI to do the task. If we had one uniform interface. And
then if we take this a step further, we can say, okay, let's, let's take MCP into consideration. So
model context protocol. So for the for the people who I don't know, I don't even have a good
explanation.
00:16:03:24 - 00:16:30:23
Jens
But for me, MCP is I create a bunch of operations. I create Json schema for them so that AI
knows the input and output, and I add some documentation so that AI can read the description
and notes. Okay, I can call this function and it does some stuff okay. So that's great. So now AI
can use MCP and talk to all my things.
00:16:30:26 - 00:16:58:06
Jens
Now you have a next challenge because it means we will we will actually create an ecosystem
to unify everything to speak MCP. And if you build the microservice architecture we are back in
API gateway territory because do you really want let's say you are you are big like,
00:16:58:08 - 00:17:25:03
Jens
Very big company. And you have hundreds of microservices because you have so many teams.
And these microservices are actually good. So it's it's fine. We're not debating microservices
here. So you have all these services and now AI through MCP should talk to all these services.
Do you want every team to build an MCP server. Which means everybody needs to protect
against AI not doing mutation.
00:17:25:03 - 00:17:54:10
Jens
It's not going rogue. Whatever. You might want to have observability. What about permissions
authorization. So again, like MCP, from my point of view it's just an API user. And for a very long
time, I think many people in this economy and in this API economy, they agree, if you have that
scenario, you should have an API gateway.
00:17:54:12 - 00:18:23:24
Jens
And now you can you can shoehorn this topic and be like, okay, we now create an API gateway
for MCP. But in reality it's just an API gateway and MCP or LLM. It is just an API consumer.
Okay. And so coming back to your question, super graph or Federation and MCP or AI, how
does it fit together.
00:18:23:27 - 00:18:52:18
Jens
If we build a super graph, we have a single approach. We have a framework of how to how to
bring all our services together. And second, if we have this, we can now create an MCP
interface on top, which is what we are currently doing. So we're currently working on this topic,
where you say, okay, MCP, what is MCP really?
00:18:52:20 - 00:19:30:08
Jens
You have a function or multiple functions. They have a description. They have an input and an
output and input and output is described as Json schema. So actually for me MCP is a
collection of GraphQL queries. Because a GraphQL query can have a description. GraphQL
gives you back Json, the input can be Json, and I can. I can transform the AST of a GraphQL
query in a way that I get the Json schema for the input, I get the Json schema for the output.
00:19:30:10 - 00:20:04:12
Jens
So if I have federation and the super graph and I have AI, I create a collection of GraphQL
queries. And now I can. With this collection, I can give MCp fine grained access to my super
graph. And this MCP, it will go through a proxy. This proxy it can live in the in the Cosmo router.
And this proxy can ensure that let's say a client is allowed to do mutations or not.
00:20:04:15 - 00:20:32:20
Jens
It's we can control what kind of operations it makes. Cosmo router already has observability. So
we know what an agent is doing. And so yeah, now now we have a very good approach to, to
create MCPs and where I think where the real benefit is of course, you can do it without
federation, without the graph and everything, but the real benefit is all backend devs.
00:20:32:20 - 00:21:05:03
Jens
We just tell them build subgraphs and then if you want to create, an MCP interface, you just
create a collection of queries. And this collection, you I don't know, you somehow persist. It's
stored. And now you have an MCP instance. And so we can almost build a no code, low code
way of. Yeah, just open the browser, create a collection of queries.
00:21:05:03 - 00:21:35:17
Jens
And now you have an MCP interface. And it's protected. We have analytics for it. We can see
exactly what kind of calls is AI making. Maybe AI is doing the wrong calls. So, yeah, I think
that's, that's a great match. Can you do it differently. Yeah. Of course. But I think what, what we
kind of need to figure out is so our approach obviously we have, we have huge investments in
federation.
00:21:35:17 - 00:22:12:01
Jens
So we will continue that and our approach and and like what I just said, like take it with the grain
of salt, of course, because, yeah. But even if you're not using our approach, you somehow need
to figure out, okay, I need to take rest. Soap, Postgres, whatever external services, I somehow
need to unify it to put an umbrella on top json, rpc for MCP, I need to add protection.
00:22:12:06 - 00:22:42:22
Jens
Rate. Limiting security authorization and observability. So you have to do it anyways. Yeah. And
that was the question. This so many of these parts like API gateways can do it like. But what API
gateways don't do is they don't unify all the stuff into MCP. And I think creating an MCP by
writing GraphQL queries that's pretty easy.
00:22:42:25 - 00:23:03:10
Jens
And you can even we're experimenting with this. You can even use AI to turn the prompt into a
query. So it's it's pretty easy to do, if you don't do it this way. I think you need to. And we we will
probably see this. We will we will now see, you know, there was a wave of like startups who.
00:23:03:16 - 00:23:20:00
Jens
Yeah SDK. And I think now we will see a wave of startups who help you create MCP servers for
all your internal stuff. And they will they will reinvent parts of Federation.
00:23:20:02 - 00:23:52:23
Stefan
It's well said and it makes sense when you put it that way. It's funny that you said that like the
waves of making SDK because we did that. So we were in that wave. We pivoted, we left. It was
funny. But one thing about AI is every company is shifting to an AI company. And I was actually
talking about this with Dax the other day is, so many companies with AI, like the ones that are
providing the services that are providing the graphics cards, you know, like Nvidia and that are
providing the actual services to help AI companies man they're going to make an absolute
killing.
00:23:52:23 - 00:24:17:07
Stefan
But side note so that's the future of Federation. Let's go back a little bit in time and just talk a
little bit about like how federation came across. Because federation is kind of a new concept.
Would you agree. Like officially Apollo Federation was released in 2019. But federation as a
concept is not that recent, right? It's kind of a new approach to a microservices architecture.
00:24:17:10 - 00:24:33:18
Stefan
And I want to get your opinion on this, and then we'll go back to where we were right now. But in
2018, you were I forgot what company you were at, but you ended up going to a conference and
we talked a little bit about this, but that's where you were introduced to GraphQL and the data.
What was it?
00:24:33:18 - 00:24:36:17
Stefan
The DGS data graph layer.
00:24:36:19 - 00:24:40:27
Jens
At Tyk I created the universal data graph.
00:24:40:29 - 00:25:00:13
Stefan
The universal data graph. And this has been talking about for like 6 or 7 years. And nobody's
actually really done a great job on it, like creating this universal data graph. But talk to me a little
bit about the history of federation. Like has federation been done before? Why aren't more
companies on federation like with the companies that we see?
00:25:00:13 - 00:25:11:06
Stefan
They make sense and they love it and it does great. But why aren't why isn't every single
company on Federation is what I'm trying to get to.
00:25:11:08 - 00:25:11:16
Jens
Right.
00:25:11:22 - 00:25:17:24
Stefan
I think and don't answer like a politician. Don't answer like a politician.
00:25:17:27 - 00:25:51:13
Jens
No, I'm not okay. I think Apollo did a lot of things right. And also some. Mistakes were made
along the way. No. I think the coolest thing Apollo created is this idea of of, of entities. And the
key concept like, you have, you have an entity and it can be it can be addressed with, with the
key or with the composite key.
00:25:51:16 - 00:26:19:26
Jens
And you can jump between subgraphs and then get more data for an entity that's, that's the best
that it's a it's a great concept. I also think starting federation in the GraphQL space was a good
idea. I mean, it was a it was a it was a natural fit from where Apollo was coming from. I think that
that's that's really strong.
00:26:19:28 - 00:26:44:26
Jens
You have a great client ecosystem like GraphQL is generally speaking, it's front end driven. Like
most, most people. It's not like anybody in the backend is like, hey, I really want to do
Federation. It's it's more or I really want to build a GraphQL server. It's more like, front end guys
say like, hey, we want to use relay.
00:26:44:29 - 00:27:10:27
Jens
Can somebody make it work? And then okay, people figure out, okay, relay, we need a GraphQL
server. And then they realized, okay, we actually want to build the GraphQL server across
multiple teams. And some teams own some parts of it okay. We do federation. But I don't know.
I think in the meantime.
00:27:11:00 - 00:27:45:16
Jens
Honestly, I think in the beginning Apollo had too much success and it, it kind of killed them
because they absolutely stopped innovating. I think the biggest mistake they made is just, I
don't know, not not not thinking further because, federation is such a powerful concept staying
within the GraphQL realm. Yeah. This is such a big mistake.
00:27:45:18 - 00:28:21:15
Jens
And what they are now doing with connectors. I talked to a lot of experts about connectors and
so I wanted to know what what is the take of, of people like, how do they think about
connectors, what do they see in them? And I asked them in a very unbiased way. I also believe I
write that I will do a write up on this in a while, but currently, I'm doing a write up on another
topic.
00:28:21:18 - 00:28:52:08
Jens
But it's the topic of connectors or the direction they are taking. So their approach is no, how can
we help you to get Rest APIs as quickly as possible and glue them to the graph? Yeah. And
there's also this ongoing process of this working group to rethink federation to be more
GraphQL native.
00:28:52:10 - 00:28:55:22
Stefan
Yeah.
00:28:55:24 - 00:29:22:27
Jens
I think I think both both endeavors are like I think it's good to eventually have a specification for
how GraphQL federation should work. Yeah. And at the same time. I think federation as a
concept is limited by GraphQL. It is a good idea that oh, he finally said it.
00:29:23:00 - 00:29:38:29
Stefan
Yeah. I mean I mean the episode, the episode is called beyond GraphQL. And I'll just say one
more time just just so Jacob can clip it that, yes. Yes. So federation is limited by GraphQL. So
what do you mean by.
00:29:39:01 - 00:30:09:24
Jens
Okay. So we have a router and it speaks. It speaks GraphQL. And I think it's great that it speaks
GraphQL. And it will always speak GraphQL. It's like for for people who use relay it's amazing.
Like graphql is amazing for people who use relay for everybody else, it's just a burden. Because
what most people actually want is an SDK and not building queries like nobody wants to build
queries.
00:30:09:24 - 00:30:34:04
Jens
But if you have relay the it's it's a completely different role because with relay you define
fragments of what data do I need for which component and like clients like relay for example.
There's also Isograph from from a friend, Robert Belsky at what company is he currently
working at?
00:30:34:06 - 00:30:37:00
Stefan
And so, Robert, was at meta, but now he's at Pinterest.
00:30:37:02 - 00:31:10:03
Jens
Yeah. Okay. And so, yeah, clients like relay or ISO graph, they, they are so powerful in that you,
you get you get, yeah. The way you can build client architecture. I think if you reach a certain
scale of an application. It just becomes un maintainable if you have something like tRPC or Rest
APIs, you're making like too many calls and everything.
00:31:10:09 - 00:31:44:00
Jens
And this is really where, where, where those clients shine. I think that's, that was also a while
ago. There was a big post by what's is the website again? It's it has something to do with crypto.
Coinbase. Yeah I think Coinbase I think they are also using relay. They are. And yeah if you
build a large front end up like something like relay, it's just it's just fantastic to to work with so
much type safety.
