Episode 14
00:00:00:00 - 00:00:41:06
Stefan
And. Well, I know, I'm just kidding. Ladies and gentlemen, welcome back to another episode of
The Good Thing. This time, we are actually not live. We're recording this because, tomorrow,
when we usually record is Easter weekend. So tomorrow is Good Friday, and then Easter
Monday, the following Monday. And, some of us are celebrating. For those that are celebrating, I
hope you enjoy a great Easter weekend with your family.
00:00:41:09 - 00:01:01:06
Stefan
For those that do have the day off, maybe watch this episode while you're hanging out with the
family. It would be great, but we didn't want to miss our routine. Every Friday at 9 a.m., eastern
time at 3 p.m. Central European time is when the good thing goes live. And we didn't want to
miss that time because we have a really exciting I guess we have had a really exciting couple of
weeks.
00:01:01:06 - 00:01:20:17
Stefan
And so today it's a little bit of an improv session. We didn't have a cool topic to talk about other
than what we've been building. And so today we invited Dustin, our co-founder and CTO.
Obviously, you see, my co-host Jens always is joining me on today. And today we're going to
talk a lot about what we've been building, especially around with AI MCP, and we even have a
small demo for you guys.
00:01:20:17 - 00:01:34:03
Stefan
So hopefully you enjoyed this format just as much as you enjoy the live one. But we wanted to
keep the consistency. Feel free to add comments to the video though to let us know what you
guys thought about it, but yeah, Jens. How are you doing today? Doing good.
00:01:34:06 - 00:01:45:24
Jens
Yeah, I just realized, you know, this is something. It hurts my eyes, but can you make a capital F
for co-founder in your name?
00:01:45:27 - 00:01:56:12
Stefan
I actually can. Yeah, I can do that live. Hold up. Edit name. One sec guys. How do you know you
work with developers is when they are anal about the small details I like it.
00:01:56:16 - 00:02:08:28
Jens
Not now. Now you know about Stefan's life as a co-founder. Like whenever there's, like a little
tiny thing, like your co-founder finds it and annoyts you about it.
00:02:09:00 - 00:02:15:24
Stefan
It works. I'm. I'm like a little co-founder, you know, with the little f, but I fixed it. Are you are you
happy now? Are we good?
00:02:15:27 - 00:02:20:11
Jens
Yeah, it's it's awesome. And, Dustin, you've been busy.
00:02:20:13 - 00:02:24:11
Dustin
Is my background Okay.
00:02:24:13 - 00:02:27:12
Stefan
Yeah. It could be better.
00:02:27:14 - 00:02:45:24
Jens
It's fine. Okay. Dustin, you've been busy. Yeah. So we have built, some stuff, and we want to.
Yeah. What what are we. What are we doing? What are we helping people with?
00:02:45:27 - 00:03:00:01
Stefan
Well. It's interesting, I'm not going to say, Dustin, from your point of view, what have you you've
been working over these past couple of weeks, and you can keep it technical, and then we'll
strip out the non-technical stuff for our non-technical viewers. But what have you been working
on these last couple of weeks?
00:03:00:03 - 00:03:31:19
Dustin
I think if you look closely or you do not even have to closely follow the tech news, but I think
your experience, like the huge hype around MCP and everyone wants to provide their own MCP
either either from your own SaaS product or from your local services. Everyone wants to provide
MCP services, so they are so that, I modeled AI modeled LLMS can connect against that and
enrich their context to do more things than they could do before.
00:03:31:22 - 00:04:05:24
Dustin
Well. And yeah, and what I have observed a lot is that everyone is doing that, SaaS provider,
super base, etc.. But nobody is really focusing on, the people who actually running software on
their own on an on premise and wouldn't be, wouldn't be awesome if you if you would have an
already existing API landscape. Let's say you're using cosmo or any other GraphQL provider,
and you could easily just expose this data to bots in a secure way.
00:04:05:26 - 00:04:42:06
Dustin
Export this data to an LLM model to have to automate your workflows like building apps. Yeah.
Accessing the data, building reports, building presentations, without any without writing any line
of code. And yeah, so we analyzed the market. We figured out that actually, what we have
already with cosmo is like everything you need to build this scalable, secure, and centralized
MCP gateway to provide this to our customers.
00:04:42:09 - 00:05:15:13
Dustin
And, so what we have built in the last seven, I would say almost 14 days, is to build like a first
class integration with MCP. So it allows you to implement implement what what in the graphql
space is trusted document persistent operation. It allows you to expose those operations
through MCP. And then you can easily connect it to your AI tools like Cursor, Claude desktop,
open AI, or other agentic frameworks to, to automate the workflows.
00:05:15:16 - 00:05:15:24
Dustin
Yeah.
00:05:15:24 - 00:05:31:23
Stefan
And and, I was telling my wife about this earlier today, so I was trying to explain to her what
MCP was and let me know what you guys think of her analogy. So she said basically, MCP is
when you take your phone and you plug it in, you plug in the usb-C into your phone and then
you plug it into your laptop.
00:05:31:23 - 00:05:50:11
Stefan
And you remember when that pop up pops up, like give access to this computer. And so then
when you're on the computer, you can access the information that's on your phone. And she's
like, is that what you're doing? You're letting products get access to cosmo. So let's say
someone builds on top of Cosmo, are you giving them access that they can start building from
all that data and stuff like that?
00:05:50:12 - 00:05:51:13
Stefan
What do you do now?
00:05:51:14 - 00:06:16:17
Dustin
Like I would say, it's it's even simpler. Imagine you have a conversation with four people and
each and if a guy represent a system. So with MCP you just bring another person into the
discussion and then you can discuss the things and you can come up with a solution based on
what, what context that can provide to the conversation.
00:06:16:19 - 00:06:20:12
Stefan
I like that, what about Jens?
00:06:20:15 - 00:06:51:03
Jens
I want to take one little step back because, everybody can build an MCP server. Right. And the
MCP, it's a protocol. Now, if you go to, for example, the subreddit slash MCP, like there's so
many MCP server like everybody is building MCP servers. By the way, I have just, used one
really cool one because, I wanted to build a new landing page today, and I thought, okay, I want
to know, does it have a good Lighthouse score?
00:06:51:05 - 00:07:30:21
Jens
So I added a lighthouse MCP server because somebody has built it already. So now my cursor
can change something on the website and then run a lighthouse test without me because I'm
too lazy opening the browser and clicking on lighthouse test so I can I can now do that. So
yeah, like essentially what Dustin said you can now instead of clicking around you can now just
write what you want and and cursor ensures that cursor MCP ensures that cursor or your model
it can now talk to lighthouse score.
00:07:30:21 - 00:07:58:16
Jens
It can talk to Cosmo. It can talk to GitHub. It. Yeah. Yeah. That's so that's right. But one step
back because everybody can build an MCP server. Now there's a new problem. So you you
have this huge opportunity to that's a model can now through MCP talk to anything. The
problem is we have we need to bridge between anything and MCP.
00:07:58:18 - 00:08:21:27
Jens
And so this is the problem Dustin was looking into because we already have a solution to bring
to to turn anything into something very specific and then go from something very specific to
MCP. And so in our case, I mean, you you know, us this anything it is the concept of the super
graph. It's the concept of GraphQL federation.
00:08:21:29 - 00:08:55:24
Jens
If we have a GraphQL federation layer and our router can go from federation to trusted
documents / MCP. So now MCP can actually talk to all the things we have already federated. So
so that means if we if we have this component that goes from federation to MCP, all we have to
do as a company is bring more capabilities to our federated graph, and it becomes available to
to MCP.
00:08:55:24 - 00:09:24:01
Jens
It becomes available to the models. The problem do you want to give everybody access to
everything? Do you want the model to do whatever it wants? Do you somehow want to limit
that? And now you can even ask yourself the question, if you let's say you are not doing
Federation, you just have MCP and you, you manually implement from MCP to anything.
00:09:24:03 - 00:09:56:21
Jens
Essentially, this MCP server is now a BFF, and you will very likely want to have one MCP server
per use case because let's say you are a big a big, media company, that offers streaming
services. And let's say you have hundreds of microservices. Do you really want to create one
single MCP server and for, for all use cases and give that to a model, like, first of all, the model
will be overwhelmed by the capabilities.
00:09:56:23 - 00:10:28:12
Jens
You will have problems because these features, they come from over 100 microservices. So
there's a lot of people behind the. Do you really want to bring all of this together in a BFF? It
means that you now have to maintain a BFF across, I don't know, 100 services, potentially
hundreds of people. So you're kind of back to the BFF versus federation problem, where now
the API consumer, it is not the website where it is not one single web front end.
00:10:28:12 - 00:10:51:05
Jens
You know, we have BFFs in the past like SoundCloud, where where you have multiple apps,
you have like web, iOS, Android, etc. for each app, you have a BFF, and now there's a new API
consumer. It's not a website, it's not a browser, it's not, an app. It is a model. And we have
different models and different tasks.
00:10:51:05 - 00:11:35:06
Jens
Models should do. So. Now we need BFFs for these models or we do what Dustin has built
because that means we're not building one BFF per model, per use case. We all contribute to
the super graph and with yeah, a tiny amount of work, we create an MCP server for a very
specific use case. And, and I think that that's ultimately it's, it's the right approach because if
we're not doing it like this, so what is the what are the alternatives if we don't use the approach
by Dustin, we will essentially go back to the BFF pattern.
00:11:35:08 - 00:12:02:07
Jens
And everybody is currently talking about how we have API sprawl and we have too many BFFs
and there's too little resources to maintain the BFFs. So if we don't have the resources to
maintain BFFS for different apps and websites and products, we also don't have the resources
to maintain BFFS for MCP, for for models. So yeah, there needs to be a solution.
00:12:02:10 - 00:12:05:06
Jens
And Dustin.
00:12:05:09 - 00:12:05:27
Dustin
One comment.
00:12:05:27 - 00:12:07:28
Jens
Maybe. Sorry.
00:12:08:01 - 00:12:25:25
Dustin
One comment on the BFF analogy. It's I think also important is that you have to re-implement
everything, authorization, authentication, telemetry, who is doing what. And rather than doing it
twice, why not putting the MCP expose, MCP on the source of truth?
00:12:25:27 - 00:12:52:02
Jens
Yeah. Thank you for the curveball. I actually forgot this, but it's so true. No, no, no, that was
actually one of my bullet points. If you if you have 100 microservices and you build an MCP
server and now in this MCP server, you implement authorization, and then someone else builds
another MCP server for another use case. So now you're building authorization for that twice.
00:12:52:05 - 00:13:10:06
Jens
Yeah. If you have if you build this on top of your super graph and you put authorization into the
super graph, now it's a solved problem for both cases. Plus our router, it already has
authentication authorization. It has analytics. It has all these things.
00:13:10:06 - 00:13:12:26
Dustin
And so schema you.
00:13:12:28 - 00:13:17:12
Jens
Schema usage what. Let's give.
00:13:17:14 - 00:13:18:04
Dustin
You session.
00:13:18:07 - 00:13:19:04
Stefan
Yeah. Yeah. Right.
00:13:19:04 - 00:13:44:06
Jens
Otherwise yeah. You know what who's using what etc.. And then you have breaking change
detection. This is a not I mean the defining thing is an MCP server is really just a BFF. And if you
manually built built this BFF, you don't have a real time map where you know, that's clients, in
this case MCP clients, they talk to your backends.
00:13:44:06 - 00:13:58:07
Jens
You don't know that because there's the MCP in the middle with Federation we have schema
usage. So we know that an MCP client is talking to your subgraphs. We know that. So you
cannot break it.
00:13:58:09 - 00:14:19:23
Stefan
So that part right there though you cannot break it. So the CEO of browser Base, he tweeted the
other day that like MCP is great for 80%, but that 20% where it connects and makes sure that
nothing breaks. That's where it hallucinate. And I was talking to you Jens about this, and we
were talking with one of our customers that the power of federation, if you strip it away is
checks.
00:14:19:28 - 00:14:40:15
Stefan
Is is this going to break a client, is this going to break an API? And what I think is so powerful
behind what we're building is that we give you the power of MCP, we give you the power of AI
and generative AI, but we're also making sure that you're not breaking anything. So we
eliminate that 20% where it could hallucinate, it could break because you're running checks
against the schema.
00:14:40:17 - 00:14:52:05
Stefan
It tells you if it'll break it, and then it will tell you if you are going to break it, what you should do
to not break it. And so that's just my non-technical piece I want to add there. I think it's too too
powerful really.
00:14:52:07 - 00:15:30:28
Jens
But that's one more thing because we're talking about checks and breaking changes and
whatsoever. But we're also building a new product. We're not yet talking about it, but it's going to
be amazing. And so this new product, it it knows about. So cosmos already knows that. But so
we know about all your subgraphs. We know your schema. We know all your clients, including
MCP clients and the, the the one thing that we find super interesting is we have built a
serverless cosmos router that is not serving traffic.
00:15:30:28 - 00:15:55:17
Jens
It can it can batch generate query plans. And we were like, oh interesting. We batch generate
query plans. By the way this is open source. Like everybody can just see this on our repo. We're
not hiding this. So you can batch generate query plans. And if you look into them we have
created a very simple algorithm that that calculates the complexity of a query plan.
00:15:55:19 - 00:16:18:20
Jens
And so we can for example, say if you if you have like a sequence and then in the sequence
you have two fetches, they get a certain score. If you have a parallel node and it has to try to to
child fetches, then the parallel to fetches, they have a lower score. Then a sequence of two to to
fetches.
00:16:18:22 - 00:16:44:14
Jens
Because obviously like the sequence is is slower, it has more of a cost. So we have built this
cost function. And now the, the what that you mentioned checks and breaking like breaking
change. Cool. Yeah it's very important. Like it's the foundation. But what I find also like super
interesting is imagine you are making changes to your schema or you're thinking about making
changes to your schema.
00:16:44:16 - 00:17:11:18
Jens
And now you can see, let's say you have 100 MCP clients that use your schema and you know,
their complexity score and you make changes. You move something around in your in your
architecture and you see that all scores stay. They go up by 20%. So that means you you would
now negatively impact all the clients, all the models because it it's going to take longer.
00:17:11:21 - 00:17:38:17
Jens
And this is also where I think Federation or what. Like it's not federation anymore. It's more like
what we're doing with it. It's so powerful to understand who is using what and what is the cost of
using your architecture. Because most of the time, let's say you have your client, you have your
custom built MCP server, you will never understand what is the cost of making of calling a tool.
00:17:38:20 - 00:17:47:11
Jens
And we can make that transparent and we can tell you there's negative impact. So yeah, the
super graph is powerful.
00:17:47:13 - 00:17:53:17
Stefan
I love it.
Let them cook. Let them cook. I really like anybody can make changes. Anyone can run checks.
00:17:53:20 - 00:17:59:04
Jens
We have we have built a landing page I think it's it's not yet live right.
00:17:59:06 - 00:18:02:00
Stefan
No, it's not a little sneak. I we're.
00:18:02:03 - 00:18:03:18
Jens
We're working on it.
00:18:03:20 - 00:18:03:27
Stefan
Okay.
00:18:03:27 - 00:18:04:22
Jens
So so.
00:18:04:22 - 00:18:05:23
Stefan
Today.
00:18:05:26 - 00:18:25:23
Jens
Oh we're we're, we're we're introducing the MCP gateway. And, Dustin built this page, so maybe
you can guide us through. Yeah. Well, what's going on? What are the what are the big concepts,
the big topics. What does everybody need to understand okay.
00:18:25:25 - 00:18:48:26
Dustin
So MCP is a protocol. So that means a server has to implement a protocol. So like so that the
client can speak to to a server. So what we have done in the in other router, we have extend the
capability of implementing a MCP server. And using by using trusted documents, exposing
those operations as MCP tools.
00:18:48:28 - 00:19:20:01
Dustin
And of the nature of an MCP server is it has a discovery endpoint, it has metadata, and it is it
can you provides the the metadata to understand what tools prompts, routes and resources are
available. So what we have built into the into the router and we call it the MCP gateway is a full
integration with MCP protocol over GraphQL.
00:19:20:03 - 00:19:52:15
Dustin
So yeah. So that means we provide tools to discover to discover your graph, grow, a graph to
discover what operation you have, have expose through customer, through trusted documents,
and by connecting all your services. We essentially have we are providing access to your
services through MCP. And if you look at the left side, you get a very, I think, good
understanding of how that will work.
00:19:52:15 - 00:20:24:01
Dustin
You define a graphql operation, let's say a trusted document as a file on the on the file system.
You put that for instance in the operations there. Then we will automatically based on the graph
operation create an MCP tool, export it through MCP protocol. And we also based on your
inputs we infer the right JSON schema so that the end so that the LLM knows how to call that
tool in the type safe way.
00:20:24:03 - 00:21:04:14
Dustin
And we will also leverage this information to validate, once you make a request to the router to
ensure that, this this operation is valid according to according to it generate JSON schema.
Yeah. Schema. So here you see a very simplistic example like someone has exposed a get
product operation. It was exposed to execute operations. Underscore. And then if let's say you
ask for a product price, the llm would be able to figure out that because you have exposed this
method to the LLM, I can call that to get the price.
00:21:04:16 - 00:21:08:07
Stefan
Insane. And you might have.
00:21:08:10 - 00:21:34:11
Jens
Yeah. Just few questions for clarification. You mentioned JSON schema and, like, I know what
you're doing, but maybe we can explain for the for the audience what what is the role of JSON
schema in, in MCP. And what are we doing here to to help people. Yeah. Make it make creating
MCP server is actually easier okay.
00:21:34:11 - 00:22:00:19
Dustin
If you create if you want to expose the MCP tool you need to define the contract. It's called the
input contract. So how what does, an what does an llm has to call the the, the tool in a way that
it's will comply with your contract. So in case of this example here, the LLM has to pass, an
argument, primitive argument of type string.
00:22:00:21 - 00:22:44:12
Dustin
But this can get much more complex. You could have recursive input types. You could, in a later
a demo, we will show you, and find employees, tool that allows you to filter for employees by
nationality, moods, etc.. So what we have to do is we take the, the input, type, we convert that
into, JSON schema and then provide this schema to the, to the tool so the LLM can understand
what the how does the call has to look like in order to fulfill the user request in the LLM session.
00:22:44:14 - 00:23:17:06
Dustin
And this sounds very easy, but if you read the documentation of all the models, you will figure
out that they do not support the full specification of JSON schema, they only support a subset of
it. So for example, the the don't allow the don't support recursive, for the, the recursive
structures. For example you if you, if you would build this from scratch, you would, you would
detect recursion and you would replace and for example definitions references.
00:23:17:08 - 00:23:44:03
Dustin
And yeah, there were there were a lot of edges cases where we had to optimize that for LLM
usage. So instead of, providing definitions like at a dollar depth definition or as part of JSON
schema, we just, limits limiting the recursion at the specific depth. So to have to, to produce a
valid Json schema. And then you need to understand that, yeah.
00:23:44:03 - 00:24:17:26
Dustin
All these nuances of when is a field nullable, we have to provide all the values in case of you
using enums, required needs to be, correctly implemented, when at least one argument is
required. Then the, the object is required of the input, and so on and so forth. And one comment
I or I know I, we will I think we when we, when you scroll a little bit more we will come to the
okay.
00:24:17:29 - 00:24:55:01
Jens
But let's stay here for a second because that's there's more to it. I could just create my own
MCP server. I, I, I guess I would vibe code it and I would just put no, like, for real. I mean, who,
who writes code today. So you vibe code, it, you just give it this query or you tell it like, here's a
schema and put and put this query and, would this just work or what kind of problems can I run
into if I built my own MCP server and just tell like, hey, put this get product query.
00:24:55:01 - 00:24:59:26
Jens
What, what what's, how will the outcome look like?
00:24:59:29 - 00:25:10:04
Dustin
I mean, I mean, you would like to to pass the, the, the exercise to generate the JSON schema
for the, for instance, is the right.
00:25:10:06 - 00:25:29:02
Jens
Yeah. So if you so you let's say you, you vibe code the JSON schema for the, for the query. You
vibe code this how how confident would you be that this is that this is correct.
00:25:29:04 - 00:25:37:19
Dustin
I would say it really depends on on your proficiency in the domain, but it's I would say.
00:25:37:22 - 00:25:53:00
Dustin
It's I would say it's pretty. It's pretty pretty pretty. Difficult because you would need to understand
how the GraphQL specification works and how it will be or how it can be mapped to JSON
schema. In that case. Yeah.
00:25:53:00 - 00:25:54:06
Stefan
Yeah.
00:25:54:09 - 00:26:15:18
Jens
I think so. I think what would happen is you have this ID, which is mandatory. AI will probably
figure out, okay, JSON schema needs to be a string and it needs to be not optional. And we can
look at it as a human because we need to review the vibe code stuff. And we will say, okay, this
this looks about right.
00:26:15:20 - 00:26:43:17
Jens
But then later I think you will show us an example of a more complex query and data structure,
and it will very easily reach the point where our input variable, it is so complex that a. we are not
100% sure if every field the LLM has actually translated in the right pattern. And second, I think
it can easily get to, level of complexity where we're we're not 100% certain anymore.
00:26:43:24 - 00:26:50:20
Jens
would yeah.
Like, even if you look at it, you will not immediately see it's wrong. It could be wrong. So and I
00:26:50:22 - 00:27:17:00
Dustin
I would even say this is like the perfect example by not using LLMS for because this is like a
deterministic, task to convert something from A to B. If you would use LLMS for that, it is not
even it is super costly, but also that you wouldn't leverage the power of LLMS in this case,
because LLMS, are good at being creative, finding patterns.
00:27:17:03 - 00:27:21:07
Dustin
In that case, this is pure. This is an algorithm.
00:27:21:09 - 00:27:44:07
Jens
Yeah. This is what I actually wanted to to get at that some problems, they are deterministic and
you can parse the query, take the AST and generate the JSON schema with an algorithm. This
algorithm can have tests. And now we are very much certain that the JSON schema is is right.
Or even if it's if it's wrong, we know we have a bug.
00:27:44:07 - 00:27:50:16
Jens
We can we can fix it. If you if you do this task with an LLM, it might be right, it might be wrong.
00:27:50:19 - 00:28:08:12
Stefan
But isn't it kind of? What I mentioned though, is that like with the schema checks, that you kind
of get the security that it'll work, so you get to the 80% vibe coded, but the 20% now with MCP,
with Cosmo, and with Federation in general, it makes sure that you're making the right
decisions, even though you, vibe, coded it.
00:28:08:14 - 00:28:17:11
Dustin
I would say it's a little bit different. I think the point here was you should not use LLM at all to do,
to solve this puzzle here.
00:28:17:13 - 00:28:39:29
Stefan
Okay. well said? And then, so if I scroll down a little bit I want to understand this part here. So
why you need MCP for your GraphQL API. And you listed these four points AI discovery,
operation control, rich metadata and instant integration. Can you walk us through each of the
points? Dustin. And then yeah. And also feel free to jump in and just kind of explain to us why do
we need MCP for our GraphQL APIs?
00:28:40:01 - 00:29:18:12
Dustin
Yeah, I think the first point ai discovery means it or it is more or less inherits the benefit of the
MCP protocol so that mcp allows to list tools and resource and so on. And this gives essentially
the the the power to, to to to list what is what is your MCP gateway capable of. On the other
hand, I think that's something about Jens mentioned like if you if you're building and or if you
have a route, a gateway which is connected by GraphQL federation, and you can integrate any
type of, of service.
00:29:18:14 - 00:30:07:26
Dustin
So essentially you can expose anything to AI because you can by the nature of GraphQL
federation, you can just write query that spans across multiple services and aggregate data. And
this this is yeah. No, this is more more about the operation control, where you can create trusted
documents on your file system, write the operation in a way that you only want to expose the
that the data you will, you want to expose to LLM, for example, let's say someone want you
want to expose, the list of employees so you can build dashboards or you can boost a report,
but you usually don't want to export the, the location, the
00:30:07:26 - 00:30:24:03
Dustin
h age. Yeah. Bank information. But the the way how you approach this, you just you do not
include this particular field in the trusted document. That's everything you have to do to limit
access to the, LLM
00:30:24:06 - 00:30:25:02
Stefan
Information.
