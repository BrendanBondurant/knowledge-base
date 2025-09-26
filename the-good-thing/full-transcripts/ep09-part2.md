00:33:27:04 - 00:33:55:05
type: podcast-chunk
Cameron
But, you know, doing, you know, doing all of the things that are time consuming is just super
simple, like writing SQL migrations, writing comments, helping to write tests, helping to, you
know, build out data models like those types of things. It is super powerful and it's a very helpful
tool for, you know, an engineer to have in their back pocket to be able to move extremely
quickly.
00:33:55:07 - 00:34:15:07
Jens
Yeah. But what I've found where it works really well is if you give it a pattern and you, you want
to replicate this pattern for other things. So let's say you create like, like a design of a new
solution. And you, you make the design for queries and then you tell it, okay, can you do the
same thing for mutations?
00:34:15:09 - 00:34:39:29
Jens
Because it's kind of almost the same. But it would be nice to have also a spec for mutations. But
you are lazy and it's very good at that. One use case where where I found it to be dangerous is.
So let's say you have an AST in one language and you want to make some transformation and
create an AST in another language.
00:34:40:01 - 00:35:02:12
Jens
So what I have found cursor doing and this like you need to be extremely careful with this kind
of stuff. So you add a simple use case. So I'm, I'm the way I try to approach it is I try to start with
something super simple so that I bootstrap like one function that does one thing, and then I add
another test case.
00:35:02:12 - 00:35:28:29
Jens
So I go like very test driven. So I start by writing one test and an empty function. And then I tell it
to implement this okay. And then I write a second function where I add one more feature. So I
make this test a little bit more complex. And for example there one one pattern I already
observed is you need to be thinking about do I want to stick all tests in one file or one file per
test?
00:35:28:29 - 00:35:52:15
Jens
Because like these files, they can quickly go super large. And then the model might get
confused by so much context. So these are things you need to to consider. But what I have
found is so you start with a simple use case. It it implements it. Then you add a more complex
one. It figures it out and then you add like a really complex one.
00:35:52:17 - 00:36:35:03
Jens
And what I have observed there is. So again this use case is AST transformation. So you have
one nasty, you turn it into another. And what's, what's so I was using 3.7 solid agent model and
what it kept trying to do is instead of writing a function that looks at my AST and tries to
dynamically or tries to write code that dynamically derives something from the AST, it kept
hardcoding AST literals into the implementation for a specific use case.
00:36:35:05 - 00:36:56:01
Jens
And I had like over and over and over I had to force it and tell it like, hey, don't, don't do that. Do
dynamically write code that looks at the AST and that derives this kind of function and that that
was really, really, really tough because, I don't know. It just wants to, to go like the simple route.
00:36:56:05 - 00:36:59:21
Jens
But do you have similar experiences?
00:36:59:23 - 00:37:25:18
Cameron
Oh yeah. There. Very much so. I have, you know, I there was something the other day that I
was working on, where I was working on doing an implementation of, within our, artificial
intelligence work, that of kind of an abstraction layer. And it just kept wanting to over even
override me sometimes, which was a little frustrating.
00:37:25:20 - 00:37:53:13
Cameron
Because it would want to override me to actually put in, like, hard, hard coded, defined literals
as opposed to doing something dynamically and actually extracting it to where it is an
abstraction layer and not just, copy and paste of JSON information into Go, so it. Yeah, that's
why like for me, I really have enjoyed using it to do kind of the opposite of, what Jens has been
using it for.
00:37:53:13 - 00:38:17:28
Cameron
I'm using it to write tests, to validate, the code that I've written or to write help write comments
out to kind of almost using it like my second set of eyes, as opposed to the, as opposed to the
like, you being the human being, the second set of eyes, almost doing it kind of reverse.
00:38:18:00 - 00:38:30:13
Jens
If you have the model writing the tests, which is it? I think it's a good idea. Can you somehow
ensure that it's not looking at your implementation?
00:38:30:16 - 00:38:36:16
Cameron
It probably will look at the implementation, to be honest.
00:38:36:19 - 00:38:37:04
00:38:37:06 - 00:39:12:04
Cameron
I, I yeah, probably I mean, you can, my cursor at least I know you can define what files it uses
and context, but, yeah, my guess is that odds are there is, you know, something that enables
that to look back at the implementation. However, I think that that is somewhere that AI is
hopeful in is that humans might look at that implementation and have a bias towards ensuring
that it works and ensuring the tests pass, whereas AI is not necessarily going to have that bias.
00:39:12:07 - 00:39:31:01
Cameron
Whereas, you know, I've found that. It's more likely to come up with test cases that are failing
even in a state that I would expect, like. I found it comes up with some crazy edge cases
sometimes. Is what I'm getting at there.
00:39:31:04 - 00:39:52:26
Jens
Yeah. You know, I, I was thinking it's a bit like the, like, the pink elephant kind of scenario. If you
tell it, don't look at implementation. Don't go, what will it do? Will it ignore that. Will it think, oh,
you mentioned implementation, but but.
00:39:52:28 - 00:40:00:11
Cameron
You know my guess is it's going to it's, it's going to go after the second one. And I kind of want
to try that now and see what happens.
00:40:00:13 - 00:40:27:09
Jens
Yeah it will probably look at the file and be like, okay, I should not look at the file. So I need to
read it to know what I should not look at. Right. So yeah, yeah, yeah, it's very, very interesting.
But like overall like I can say it's a, it's a super useful tool. For me I guess, one, one scenario
where I found, please write me a story that has absolutely no cats in it.
00:40:27:11 - 00:41:03:19
Jens
Okay. Yeah. Thank you, thank you. David. Here, message from David. That makes it all sense.
Yeah. So one one scenario where I found, Agent mode super, super useful is, writing RFCs
because, I'm super lazy, like, and so if you write an RFC, so two, two scenarios where I found it
useful to use cursor, the first one is you write an RFC, and after a while you come to the
conclusion that you made a mistake.
STOPPING POINT ON MARCH 19 - BRENDAN
00:41:03:21 - 00:41:32:10
Jens
Like that's very natural. You want to refine the RFC, so you want to make significant changes to
like a root concept in your RFC. If you do this by hand, it means you have to go through this
whole document. And wherever you use this root concept, you now have to make changes. And
it's gonna be tough. It's going to be like you can very easily forget something, with cursor,
00:41:32:12 - 00:41:50:23
Jens
It's it's so good. You just tell the tell the AI like, hey, here's this root concept. I don't like it. I
changed my mind. And, can we, can we refactor that? And then it will go through the whole
document, make the changes. It will tell you like which part of the code it changed. So that's
pretty useful.
00:41:50:25 - 00:42:14:25
Jens
And the second use case I really like this. So you create your RFC, you publish it to gets up like
a markdown. You create a pull request so people can comment. You let them comment, and
then you take the URL with the comments and you tell, you tell the AI, hey, here's a, here's
some comments, some feedback.
00:42:14:28 - 00:42:37:18
Jens
Apply the feedback to the RFC so you can have AI read the comments and apply them. And
then you can review. Okay. How would it look like like, do I like this? I mean you don't have to
accept it right away. You can just iterate on it. And yeah, I find it very useful. Also, some other
things I did is in cursor you can index websites and documents.
00:42:37:21 - 00:43:03:19
Jens
So for example I indexed the the documentation of WunderGraph I indexed the GraphQL
specification and some other websites. And then let's say you want to work with GraphQL or
write an RFC about GraphQL or something. You can you can look at these documents. For
example, there's a there's a working group, the GraphQL composites schema working group.
00:43:03:19 - 00:43:31:19
Jens
It's it's working on creating like a, yeah, like a federation specification for GraphQL federation.
And let's say you create an RFC that is in the federation space, you can just ask cursor, hey, I
have this RFC here. Take a look at the Federation specification from the composite Schema
group. Are there similar concepts. And how are they dealing with this situation.
00:43:31:19 - 00:43:45:18
Jens
Do they have an opinion on that. And then you can you can learn from that. So I find that very
very useful. Any any other topics, topics any other like approaches or patterns you're using.
00:43:45:20 - 00:44:10:14
Cameron
And I think, you know, I really relate with the RFC type, approach. I think that it's yeah, I've used
it largely to write documentation and keep track of things that, you know, to help me, like just
share what my brain is thinking as I'm going through and writing code and writing, you know,
writing things that make sense to me at the time.
00:44:10:16 - 00:44:36:09
Cameron
And, you know, being able to have a tool that you share that can document it well, in, you know,
either in comments or in just like a markdown file somewhere is very helpful to allow me to, you
know, bring in other engineers to, you know, give people the information they need. And I think
that that's something that I don't necessarily enjoy doing.
00:44:36:09 - 00:44:42:11
Cameron
So I think it's something that is very helpful. For me.
00:44:42:13 - 00:45:15:25
Jens
Yeah, And to be honest, like I think even for example, reporters or like non deaf people should
consider using cursor because let's say you're a reporter, you're you're researching for a topic,
create a project, open cursor. And let's say you have a bunch of websites and Wikipedia articles
and sources that talk about this topic, like for each source, create like one agent tab.
00:45:15:27 - 00:45:41:02
Jens
Tell it to read the website, figure out with a prompt the relevant information something, and then
you I don't know it's you can use it as a research tool. I think cursor is not just like a coding tool.
You can do research, you can write, I don't know, content. I like to write it with, to use it with,
with, writing, blog posts.
00:45:41:09 - 00:46:21:14
Jens
But I have like one, one, one note I have to make because, for me, blogging is an art. And I, I, I
think quite often you can see, when someone wrote an article with AI and for me, it's a big
difference if I ask an agent to write an article or if I use, for example, autocompletion to complete
my sentences, and I have to say I, I, I don't know, but I don't like using the agent mode for
writing blog posts because I think it's not authentic.
00:46:21:14 - 00:46:35:29
Jens
It's, it's it's too much like it's too much following like a structure and the pattern. And it's not for
me. It's not human like, I, I want to have the human touch in an article, so I'm not sure how I'll.
You see that?
00:46:36:01 - 00:46:57:01
Cameron
Yeah. No, I totally agree. I think it's actually very important. And, you know, a lot of the big
search engines have actually found ways to identify fully AI generated, content, and have
started flagging them and tagging them so that, you know, so then your blog doesn't really help
you as much as, human written blog post might.
00:46:57:01 - 00:47:36:27
Cameron
So I think it's. Yeah, I think so. We kind of get further and further into the AI and then how I can
work with us. You know, we have to be very careful and cautious of validating and backing up
what AI is writing and adding that human touch to what it's, you know, to what it's outputting. I
mean, even in code, there's a certain level of, you know, there's a certain level of need still for
an engineer to actually sit there and look behind the model and make sure that, you know,
because there are things that an engineer can see dynamically, that the model just can't.
00:47:36:27 - 00:48:00:01
Cameron
Because at the end of the day, a model is just probability, like it's just the probability of
something happening. And yeah, so that's kind of how our brains work at this too. But our brains
can take in so many more parameters than a model can look at. And that enables us to think,
you know, to think a hundred miles wide compared to 20 miles wide.
00:48:00:03 - 00:48:29:09
Jens
I think another part is also taste. So I'm not sure if a model has taste, but I definitely have taste.
And like you can agree and disagree. And that's the good thing about taste. But if you, for
example, see over like you can, you can see like I wrote, I don't know, hundreds of blog posts
over the years, and you see content and videos of, of, of me where I appear.
00:48:29:09 - 00:49:06:17
Jens
And you, you can see I have a certain style and I have a certain way to communicate. And, I
have opinions, like all the time they change a bit, but but overall, like, you can see like I have,
like, like a signature. Right. And I think it can be really hard to to, you know, if you just look at
content from, from vendors or you go through tech blogs and they all have like the same style,
the same from the model derived style, okay.
00:49:06:17 - 00:49:30:13
Jens
You can you can tell the model to have a certain style, but it's that personality. And then and I
think also when we're now building software with, with models, it's, it's increasingly important
that we have our that we have our style that, that you can actually see, oh this is this is
WunderGraph. You know what I mean.
00:49:30:16 - 00:49:51:19
Cameron
Yeah. No, I totally agree. I think it's you know, there's nothing interesting about everything being
cookie cutter. It's just like a, you know, we don't talk in monotone. We talk with, you know,
deflections in our voice. We write with that too. We just. Yeah, that's just human and models a
computer still.
00:49:51:21 - 00:50:11:23
Jens
Yeah. For example, I'm pretty sure you can read that. I'm not a native speaker, so you can
somehow see that. And that is one part of, of my identity. And I think it's, it's actually good
because you can. Okay. Yeah. It's a human because AI wouldn't write this way. Yeah. I would
like flatten this or like a noun.
00:50:11:23 - 00:50:33:00
Jens
Right. And, and maybe even in my language how I write, you see certain patterns that are like,
yeah, that's it's not how you normally write in English, but he's doing it all the time. So this is this
thing, okay? He makes this mistake all the time. And, yeah, I, I think that that makes the, the
authenticity. Well, one one other topic slightly correlated to this.
00:50:33:02 - 00:50:35:28
Jens
We talked about cursor tools like that.
00:50:37:23 - 00:51:03:02
Jens
Let's talk about MCP. So everybody's talking about MCP. We were talking about okay I can, I
can I can bring files into the context. I can bring websites into the context by writing like add web
into the chat and other things. I can index, websites and documentation. And I can also use this
MCP thing. What?
00:51:03:04 - 00:51:05:04
Jens
What is that?
00:51:05:06 - 00:51:30:13
Cameron
Yeah. So MCP stands for the Model Context Protocol. It was a protocol that was designed by
anthropic. Right now it's being implemented in their claude, models. So with Cloud Desktop or
the cloud API, the super high level basic of what it is is that you have, a client which is the
desktop or is the A is the, SDK.
00:51:30:16 - 00:51:59:24
Cameron
And then you have a server that the model runs. And this the model actually communicates via
JSON, RPC, in order to ask questions. So it's very, very similar to how something like Gemini or
something like OpenAI or Mixed Role actually allows for you to provide it with tools. The big
difference is just that it's, defined protocol.
00:51:59:24 - 00:52:25:17
Cameron
It's a defined method to how to do it remotely without it needing to be, inside, you know, like with
Gemini for example, like it's actually in the stream of the, model execution. So you have to
iterate through the, the response candidates to find the function calls, whereas MCP, the model
will actually take that onus off the user and it will actually call the function.
00:52:25:19 - 00:52:48:13
Cameron
Then the server will return it as opposed to you needing to to act to execute it. Then re prompt
the model again and then run through that whole cycle again. So it's kind of just a way to allow
that communication efficiently and to kind of take the, extrapolate it out some and to set a
defined protocol.
00:52:48:16 - 00:53:27:12
Jens
And so, for those who don't know, in open API, you can define tools and essentially the kind of
the way like it's I find it really interesting how tools is implemented. But you make a request and
as part of the request you also send like which is super expensive, by the way. You send that all
the time, like what tools you have, but so you make a request with the prompt and you also say
like, hello, AI like imagine I had functions like I don't really have functions, but imagine I had and
they can do certain things which I describe here in text.
00:53:27:15 - 00:53:46:04
Jens
So do whatever you want. And if you think one of these functions would be somehow useful to
what you're doing, then tell me to call the function so they send you like a string where they say,
okay, yes. Call the function with the following inputs and you can define the input with the JSON
schema. And so you call the function.
00:53:46:06 - 00:54:05:12
Jens
And then you tell them like okay this is the result of the function call which is like I understand
why the model has to work this way because you can just yeah, it's you can't just have the
model go outside in the world and then call your service because it's, it's it's in the cloud so it
doesn't have access to your, to your computer.
00:54:05:18 - 00:54:46:10
Jens
But now with this MCP thing, what you're saying is I don't have to define tools over and over and
over again and send them back and forth, but instead I can say kind of like, hey, here's here's
an API. I follow a contract and you can you can tell if you do this in the MCP spec, you can, you
can essentially like, yeah, you can prepare those tools, package them maybe, and then
someone else can just use the tool so someone else can say, okay, I have cursor and I want to
use, one example I saw there, someone built a tool that uses the Docker, the Docker daemon
so it
00:54:46:10 - 00:54:58:18
Jens
can talk to the Docker daemon and start containers. And so now if you enable this thing then
your cursor can now use Docker over JSON, RPC kind of.
00:54:58:21 - 00:55:22:16
Cameron
Yeah, exactly. So it allows just a really easy way to package up those tools that we, you know,
have already used. And it provides a way to package them and extrapolate them out so that,
you know, you're not having to write extensions for cursor, to in order to get it access to Docker.
You can just say, hey, add this to that model.
00:55:22:18 - 00:55:25:11
Cameron
Cool. Now I can access Docker.
00:55:25:14 - 00:55:54:13
Jens
Yeah. What I find kind of interesting is, you know, I'm, I, I would consider myself an observer, of
the hypermedia world, you know, there's, there's this group of. And do you know what
hypermedia is
Cameron
somewhat.
Jens
Okay. So I can only answer this in the, in the wrong way because depending on who you ask,
they will always say you're wrong.
00:55:54:16 - 00:56:24:08
Jens
But on a very high level, hypermedia is kind of like the web works. So you go to a website, it
returns hypertext, and in the hypertext you have URLs and you can follow them and it can
somehow, for example, return using using JSON LD or whatever schema. It can tell you there
are certain actions. And if you send a Post request to this URL, you can add something to the
shopping cart.
00:56:24:10 - 00:56:52:16
Jens
So that's kind of like hypermedia APIs. And what I find so interesting is now we have these
super smart models and everything and they are advancing. And still we, we go back to RPC
and hard coding tools because AI is not able to navigate the internet or like, like, is it really
necessary that we now map out the world in MCP?
00:56:52:16 - 00:56:56:15
Jens
Or where do you think this is going?
00:56:56:17 - 00:57:24:17
Cameron
Yeah, I think I think it's going to take steps. I think that I think MCP is a step towards making the
tools easier for the model to use. I think, you know, I think we'll continuously see, AI evolve into
where it eventually can, process the, you know, the hypermedia can process, you know, RSS
feeds. It can process, you know, even GraphQL schemas.
00:57:24:17 - 00:57:47:08
Cameron
Getting back to that, like being able to take that in and actually execute on it, based off of what it
can scrape and what it can find. But I think today it's still kind of we're still limited by the fact that
even beyond it's just it's a cloud thing, it's still just the end of the day.
00:57:47:08 - 00:58:12:10
Cameron
It's still just attention heads and a feed for or for a neural network or for mixture, for a lot of the
mixture of experts models, you know, you'll have a router and then you'll have multiple different,
feeds, like different wow words. Multiple different models behind that router. But at the end of
the day, it's just it's still just a model.
00:58:12:10 - 00:58:43:10
Cameron
It's still just processing numbers and vectors and weights. It's not you know, the human brain
can conduct the rest of our body. It can tell our arms and our legs and feet to do things. You
know, today, these models don't have that unless we provide them things like tools through
MCP or, you know, tools through the vertex AI SDK or through OpenAI's SDK.
00:58:43:12 - 00:59:05:26
Cameron
That's I think that's one of the big like things that we have to kind of figure out is how do we give
them access? What do we want to do with that access, you know, and should it be done on the
model level, or should it be done or should it be kept at the user level? So I think that there's still
a lot to figure out there.
00:59:05:29 - 00:59:28:25
Jens
Yeah. Interesting. I mean, one way you could, you could actually go with MCPs. You could tell,
let's say you have like an MCP registry where the model can search for MCPs and then figure
out which one to use. Then you have a new problem, authentication authorization. How do you
do that on the B on the behalf of the user.
00:59:28:27 - 00:59:53:25
Jens
And the other problem is, if you let the model run free and select MCPs on its own, you kind of
want to want to regulate that or verify that. Like then we kind of end up with, with a Docker
situation where we need like a public registry, where where people can somehow validate that
an MCP is actually official.
00:59:53:27 - 01:00:28:19
Jens
So now you could say, okay, you can use the MCP hub, but only the, official connections or
whatever, because I think in general it's it's interesting if, if, if every if every company opens up
like an MCP channel and you want to build integrations and work something out across multiple
like even think about your you're like a bookkeeper and you can have an MCP interface with all
the banks you have and with your bookkeeping software and everything.
01:00:28:19 - 01:00:50:13
Jens
And you can then ask a question like, hey, is this where is the money? Is it here? Is there? Give
me the latest transactions can be can be very powerful. And I think we will we will see new kind
of tools pop up that are not geared towards developers but geared towards, yeah, like,
business, business users.
01:00:50:13 - 01:01:20:10
Jens
And I guess the foundation for that is something like MCP. So it's it's interesting. Last topic
before we wrap it up. Microsoft has announced they they are in the making of rewriting
typescript in go and not in rust. Yeah. Well, what are your thoughts on TypeScript in general?
Also in the context of of AI and yeah.
01:01:20:10 - 01:01:22:26
Jens
What are your thoughts on this rewrite?
01:01:22:28 - 01:01:48:11
Cameron
Yeah. I think it's very interesting. So, I'm a big fan of TypeScript. I use, I've used it frequently for
front end and for some backend stuff. You know, on the, in the AI space, it has its place. It's
being used more and more and supported by more and more groups. I think, you know, it's
great for having just a basic serving engine.
01:01:48:11 - 01:02:17:26
Cameron
So just to be able to, you know, pass three requests back to like the open AI, API or for, you
know, quickly scaffolding those types of things. But it's, you know, for model training. And for,
you know, actually doing any kind of like experimentation around models, I'm going to choose
other languages other than TypeScript. But that being said, I do think it's very interesting that
they chose go.
01:02:17:29 - 01:02:45:09
Cameron
You know, that it was something that I did not necessarily see coming with Microsoft. I, you
know, I you hear constantly about the about compilers being written in rust or C honestly. And to
me, you know, Microsoft, their entire background is in c, C++, C#, you know, .net, all of those
things.
01:02:45:09 - 01:03:15:19
Cameron
So I'm actually pretty pretty shocked and honestly excited that they've decided to go the route of
go because I feel like go is a language. I always, say that it really feels like the best of like C++,
Java, Python and TypeScript all in one. So I feel like it's, it's a language that has a lot of power
and has and has the ability to do more than we typically do with it.
01:03:15:19 - 01:03:27:11
Cameron
So I think it's exciting to see a large compiler for one of the mainstream, languages be rewritten.
In something like Go.
01:03:27:13 - 01:04:23:25
Jens
Sidenote GitHub actually uses go internally to, to, to write some of their, the backend logic. But
aside from that, what I find interesting. So I, look at some of the discussions around this rewrite
and, and yeah, obvious question like why, why not rust and some of the explanations I really, I
watch, an interview and what I really or what resonated a lot is when you have the compiler
written in TypeScript, which is a garbage collected language, and you rewrite it in go, and if you
go like function by function, go is, very similar to, to C, I would say it has structs.
01:04:23:27 - 01:04:59:24
Jens
It has almost no magic. And you can probably if you don't use so much, so much functional
programing, you can probably go quite straight forward from TypeScript to Go versus with rust if
you build parsers and other things, and if you transform ASTs, one thing you have to deal with in
rust is this, this borrow checker, which helps you understand the lifetime of, of values.
01:04:59:26 - 01:05:30:28
Jens
And then you, you, you get into the problem where, okay, let's take an AST and you want to
rewrite it. So how long will that thing live and etc., etc.. So you have a whole bunch of problems
that TypeScript and go they simply don't have, which means just by high level looking at the
code, the go code would be quite similar to to TypeScript versus rust would be more, more
complex, more complicated rust.
01:05:30:28 - 01:05:54:17
Jens
It would probably give you better, better performance out of the box. With go. You can also be
pretty fast, but at the same time there's this tool, um I'm not sure if I remember, but there's,
there's tooling in go already to compile, TypeScript like bundle it. So there's bundlers some,
written in go and they are quite fast.
01:05:54:19 - 01:06:29:17
Jens
So, yeah, I mean go is quite performant. And I think in general, garbage collection can be a
great feature because you don't have to think about memory management at all. And if you, if
you write, you know, if you write a web server, you are somewhat concerned around like things
like garbage collection in the sense that you can have stop the world scenarios where the
garbage collector really blocks your server from doing something.
01:06:29:17 - 01:06:41:22
Jens
So if a new request comes in to the server while the server is GCing, you can have latency
spikes. At the same time, if you build a compiler, that's that's.
01:06:41:27 - 01:07:08:29
Jens
Not Really something you're worried about. You stop the compiler, it does the thing and then it
ends and you just free the memory. So I'm not sure like GC is not a concern. Because you have
so much memory, you probably just run through your work without doing GC at all and then just
throw away the memory. So that might even be, a good scenario so I can kind of understand it.
01:07:08:29 - 01:07:42:13
Jens
I, I was super surprised when I saw it, I, I, I would have never thought that someone would write,
in, in, in go, but at the same time, if you talk about the topic of what are good languages, to, to
write, code in AI and I think for web development, I would always and I'm curious about your
opinion, but I would always choose TypeScript simply because, you let it code something.
01:07:42:13 - 01:08:05:29
Jens
And the first thing you can do is you run the TSC compiler, and whatever comes back, you
throw it back, to the, to the AI to, to correct that. So I think that's, that's, that's one, one pattern.
And then on the backend side, I saw a lot of people who like Kotlin, like when, when it comes to
backend, lots of people like like Kotlin, I haven't used it so much.
01:08:06:01 - 01:08:35:00
Jens
I think it's a bit magical to me. And I personally like I'm biased. Obviously I'm writing Go for for
many years, but I think go is a great language to generate with AI simply because go has no
hidden features. It has concurrency. That's that's okay. But overall go is just super simple to
read, like the the code goes from top to bottom.
01:08:35:00 - 01:08:48:15
Jens
It's borrowing code and I don't know, it works. It's fast. It's it's good. What's what's your take.
What what what language would you use for for verb and what would you prefer on the
backend.
01:08:48:18 - 01:09:15:18
Cameron
Yeah. So for web, I agree with you. TypeScript is the way that I always go. I think that it enables
you to have type safety and to be, you know, it's quick to write for me. So I it's what I always go
with. But on the back end, if we're specifically talking about AI stuff, I'm probably going to go
with, with Python and I know, or C++.
01:09:15:20 - 01:09:41:11
Cameron
Actually for depending on what exactly I'm doing. The reason that I say that and that I don't say
go because I am, you know, my background, I've worked a lot with go and I really love go as a
language is honestly it comes down to tools and to what you have access to. You know, with go,
there's a lot of things that are not supported still, within the AI ecosystem.
01:09:41:13 - 01:10:03:05
Cameron
So you don't have access to do some of the things that you need to do to enable, you to really
keep track of the model and the model usage and how the model functions. So that's one of the
hard parts of go right now. And I think that we'll see that change as things mature and develop in
the AI space.
01:10:03:05 - 01:10:29:00
Cameron
But, yeah, that's really where I'm at right there. As for Kotlin, I've seen that a lot too. I'm not a
huge fan, just out of personal preference, but, I have seen it being used and I've seen, you
know, I've also seen Scala Spring Boot as well. But, you know, I try to stay away from Java as
much as possible.
01:10:29:03 - 01:10:31:19
Cameron
If I can. So.
01:10:31:22 - 01:10:45:29
Jens
Awesome. Yeah. Great. I think it was a very interesting conversation. We we went a couple of
minutes over. Do you know what we always do at the end of the episode?
01:10:46:01 - 01:10:47:08
Cameron
I don't.
01:10:47:11 - 01:10:54:23
Jens
Okay, well, what's the title of the show?
01:10:54:26 - 01:10:55:28
Cameron
The good thing.
01:10:56:01 - 01:11:00:27
Jens
The good thing. Okay, you need to ask me what is the good thing?
01:11:00:29 - 01:11:02:18
Cameron
What's the good thing?
01:11:02:21 - 01:11:05:25
Jens
We're we're back in a week. Well.
01:11:05:27 - 01:11:06:24
Cameron
Woo, yay!
01:11:06:27 - 01:11:22:09
Jens
Yeah. Oh, okay. Cameron, thank you so much. This was a cool show. I will I will end the stream.
Thanks, everybody, for, for joining and. Yeah, see you in a week.
01:11:22:11 - 01:11:27:06
Cameron
See you guys.