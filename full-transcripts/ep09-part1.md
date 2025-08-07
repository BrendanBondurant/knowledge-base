Episode 9
00:00:00:00 - 00:00:48:09
Jens
And we are live and back with the good thing. I'm your host today, Jens. You can already see we
don't have Stefan today because, last minute he figured out that, he's he's actually on an
airplane. I think he's currently about, to board because he is coming over to, to Germany. We
meet, we meet next week, and so, yeah, he's currently traveling.
00:00:48:11 - 00:00:57:09
Jens
But we found a very interesting, co-host for me today. Welcome, Cameron. Hi.
00:00:57:11 - 00:01:00:06
Cameron
Hey Jens. Thanks for having me.
00:01:00:09 - 00:01:27:03
Jens
Cool. Yeah. Cameron Cameron just recently joined WunderGraph. He's a senior software
engineer. He joined us with the focus on on AI. And, we have a couple of topics. Today we want
to talk a little bit about, what's happened with, the TypeScript, rewrite, which seemed to be, not
happening in rust.
00:01:27:06 - 00:01:48:02
Jens
And, yeah, probably the biggest question they have to ask, ask themselves is, Yeah. Why why
did they, had they written it in rust? That would have invited a bunch of questions, but no. Okay.
So that's one topic we talk about. I'm curious about your your opinion. We haven't spoken about
that yet. And then let me see.
00:01:48:04 - 00:02:21:13
Jens
I have this this, list. So other topics, we want to talk about vibe coding or, in general, like coding
with agents. Very interesting topic. We want to talk about MCP. I'm very interested in the topic. I
think, Cameron knows a little bit more about it. Yeah. And first of all, we would like to, to get to
know a little bit about you, how you joined, WunderGraph what you did prior to to WunderGraph.
00:02:21:13 - 00:02:25:20
Jens
So, yeah. Maybe give us a little bit of an intro.
00:02:25:23 - 00:02:51:00
Cameron
For sure. So I've been a software engineer for the last, so I'm ten years working specifically with
startups to help build artificial intelligence powered tooling. I have also worked with different
organizations to empower them to do cool things with their data. Right before joining
WunderGraph, I was the chief information security officer, actually at a customer of
WunderGraph.
00:02:51:02 - 00:03:03:27
Cameron
And, you know, I really enjoyed working with the team. And when that ended, I decided that it
would be awesome to come work with the WunderGraph team. So here I am.
00:03:03:27 - 00:03:11:07
Jens
Great, And at the company were you you worked before, you were using GraphQL Federation?
00:03:11:10 - 00:03:29:25
Cameron
We were. Yes, we had 13 different microservices, that were all federated together through
Cosmo. And our entire front end leveraged that API. We didn't have any kind of other APIs that
we used. So everything was done through GraphQL Federation.
00:03:29:28 - 00:03:42:02
Jens
Okay. And like, in general, what what's your what's your take? What's your opinion on on
GraphQL Federation from from a user slash consumer point of view?
00:03:42:04 - 00:04:16:28
Cameron
Yeah. I think it makes things really simple for both the frontend engineers and also for backend
engineers. I think it's something that empowers the engineer to focus on the product and the
focus on building cool tools, as opposed to having to worry about how to, you know, stitch
together data, how to, you know, I need to get one field that say, like the orders or billing service
has on to the user that comes from the account service, so that the front end doesn't have to
make 100 API calls.
00:04:17:01 - 00:04:27:03
Cameron
And I think that it just really simplifies that process. And there's no you know, you don't have to
think about it. You can just deploy and it works.
00:04:27:06 - 00:04:41:04
Jens
Yeah. If if you don't have Federation what what have you seen in in in companies. What what
what are the alternative approaches when you when you don't use Federated GraphQL.
00:04:41:06 - 00:04:59:08
Cameron
Yeah. So I've seen a couple you know, one of the ones that I've seen is that the front end just
has to make multiple API calls. It has to call the it has to call the account service. Then it has to
call the back or the billing service. There's just it's not stitched together which is inefficient on the
front end.
00:04:59:11 - 00:05:08:19
Jens
If I may interrupt because I want to categorize this. So, in this scenario you could say you're
federating in the client, right?
00:05:08:21 - 00:05:09:26
Cameron
Yep.
00:05:09:28 - 00:05:13:28
Jens
Okay. So so that is one thing we have seen. What are other approaches.
00:05:14:01 - 00:05:40:27
Cameron
Another one, if we kind of go on that same like category path is federating on the back end
where the account service might make, a call to the other microservice to get the data, as
opposed to the client doing it, we do it on that side, which is I mean, personally, I think it's a little
better than, doing it in on the client, but it's still something that engineers have to actively think
about and implement.
00:05:40:27 - 00:05:50:21
Cameron
And you have to think about microservice authentication, and you have to think about all of the
different things that go into microservice to microservice communication.
00:05:50:23 - 00:06:07:24
Jens
If you do it in the backend, it means. So the latency for these multiple calls, it will be better. So
performance is better. But in terms of complexity, we're now creating an endpoint that has more
capabilities because it federates right.
00:06:07:24 - 00:06:09:21
Cameron
Right, exactly.
00:06:09:23 - 00:06:33:28
Jens
And like in in technical terms we we kind of call this like a back end for front end. So for this
specific use case, we, we create a, a BFF or even worse, if you don't create a BFF. Something
that I have also seen a lot in the past is people add stuff to REST APIs. So hey, can we get
some more data just added to the REST API?
00:06:33:28 - 00:07:00:06
Jens
And then the expanded, and then if, if you have, a BFF approach, for example, we work with,
SoundCloud together they, they, used BFFs heavily in the past. And, what you eventually end up
with is so you have one front end and one backend. Then you add more front end capabilities or
more front ends in general.
00:07:00:07 - 00:07:50:16
Jens
So you expand your backend or you go the BFF approach. And if you start the BFF approach,
then you start adding BFFs and eventually you end up with like, you have end clients, BFFs and
I don't know, 0 number of backends. And you, you create like a very interesting matrix
configuration. And, well, one feedback I got from many customers is in this kind of configuration,
it is often very hard for someone on the backend side to understand who's on the client side,
because they they, they don't have all these client teams in the team because it's other people,
maybe even in other parts of the organization.
00:07:50:19 - 00:08:36:11
Jens
So what then happens is you can very easily break clients. You can very easily break
dependencies between services because you don't know who's using you. And also, like, what
you need in the, in the front end side to, to make it somehow scalable and work is you add more
and more contract tests that somehow try to articulate that there is a contract between clients in
the backend, clients in the frontend and our microservices and this whole level of complexity,
federation kind of deals with it, like it has constraints.
00:08:36:13 - 00:08:59:22
Jens
But in federation you have your super graph schema, you have your subgraph schemas, and
you have clients using that. And then you have a schema registry like Cosmo. And Cosmo
knows the schema of the supergraph. It knows the schema of the subgraphs. It knows, like your
linting rules and other things, and it knows all clients by name version.
00:08:59:29 - 00:09:20:28
Jens
And what fields they use in what query and when. For example, it knows exactly “oh, we have
these 20 clients and this are the, I don't know, 2000 queries. They, they made, over the last 30
days”. So now if you change a subgraph, first of all, you know who's using you. You can look at
the analytics.
00:09:20:28 - 00:09:40:29
Jens
You know that. So you can talk to the people. And second, if you are on the client team, it's
actually very easy to figure out if you let's say you load an entity and it needs an additional field,
you can actually look at the schema of the super graph. You can figure out where is the stuff in
the super graph coming from, like which subgraph.
00:09:41:02 - 00:10:20:29
Jens
So you can figure out who are the people behind that. Because the schema registry, it's kind of
like a map for you to to map like things in your domain to people. And so you can figure out who
other people you can talk to them. And then in terms of breaking changes, we have one, one,
customer, who reported once they moved the project on to Federation, they saved more than
30% of the time in QA for contract testing because they they just wouldn't have to write the
conflicts anymore because, we have this command WGC check.
00:10:21:01 - 00:10:51:05
Jens
So you run a check when you want to change a subgraph, and then it verifies that you're not
breaking clients. So yeah, overall, you can have, you know, lots of people have opinions on on
GraphQL. It's good, it's bad. It's replacing REST. It's not replacing REST. But at the end of the
day, I would say our opinion that at WunderGraph, we're actually not like GraphQL is the best
thing in the world.
00:10:51:05 - 00:11:21:09
Jens
We're more like federation allows us to have many clients and many backends. And without this
middle layer in between and without the matrix, and we know what is using what and where is
something coming from, and we can prevent breaking. So yeah, like for us, federation solves a
huge problem of scaling clients and backends. And if you if you want to scale a company, it
means you're adding products.
00:11:21:09 - 00:11:31:09
Jens
It means you're adding business logic. So you add backends. So yeah this needs to live
somewhere. So. Yeah. Anything you want to add.
00:11:31:12 - 00:11:43:26
Cameron
Exactly
Now I think you hit the nail right on the head. You know, it, it's just a really great tool, in my
opinion, to empower scale and ease of use and to empower stability.
00:11:43:28 - 00:12:16:10
Jens
Yeah. Which leads to, the next topic. So, like I said, we like federation, but, one, one problem of
federation is, it relies on GraphQL. And not everybody knows GraphQL, like the majority of the
market has not yet adopted federation has not yet adopted GraphQL. So one topic we're
working on is we want to make federation like again.
00:12:16:10 - 00:12:43:16
Jens
Like when when when when we think about what we're doing, we're thinking less about
GraphQL. We're thinking more about federation. Like the problem like we solve the problem. I
just described federation or GraphQL is a detail. So one of the challenges we we find is that, as
you bring federation into a company, more and more people are interested in using it, in
leveraging the graph.
00:12:43:20 - 00:13:07:13
Jens
And obviously your graph, it becomes a more powerful asset for the company if it's more
capable. So there's like, yeah, like a, like a flywheel effect. You have more users, you have more
use cases. It can do and then it attracts more people. So how can we get more people to to
leverage the, the graph, maybe even without understanding GraphQL.
00:13:07:13 - 00:13:22:13
Jens
And this is something where, where you came, you joined us and we started, exploring, new
ways of, of dealing with, with GraphQL. So maybe, we can expand a bit on that.
00:13:22:15 - 00:13:52:22
Cameron
Yeah. For sure. So one of the things that I've been exploring since I joined the team is how we
can leverage artificial intelligence on top of a super graph or even some subgraphs, to empower
people like business users or, empower front end engineers who’ve never encountered
GraphQL or really anyone to be able to query the graph, to be able to use, to be able to just ask
the graph, hey, how can I find out how many users, are in this organization?
00:13:52:22 - 00:14:17:06
Cameron
Hey, can I get this user's name and it can spit out the query and help them run that query
against the graph. And that's something that personally I feel like will really empower and allow
even people who are super familiar with graphQL that haven't worked with that specific schema
before and might not fully know the schema. It might.
00:14:17:06 - 00:14:29:06
Cameron
It will be a faster way for them to find new queries to figure out the data they need, and to
actually activate and use that data.
00:14:29:09 - 00:14:56:05
Jens
Yeah, this is a good point because, So one use case we give the we give people access to the
API that are not really developers, business people. That is one use case. And they they might
not even know how to write a query for them. It's it's truly helpful because they can have a chat
interface to, to talk to the, the, the API.
00:14:56:07 - 00:15:09:03
Jens
That's helpful. But also for developers. If you look for example, at, let's say you have a schema
like, GitHub, how big is the schema? Do you know that on top of that.
00:15:09:06 - 00:15:13:09
Cameron
It's like 336,000 tokens.
00:15:13:12 - 00:15:15:05
Jens
Okay. So lines of code.
00:15:15:08 - 00:15:24:17
Cameron
And lines of code, I want to say it's like this. I'm not 100% sure. Actually. I think it's like 1500. It's
in the thousands.
00:15:24:19 - 00:15:56:22
Jens
Okay. In the thousands. And like obviously you it's it's impossible to to quickly weed through
that. And so what we could now do is we could go to the GitHub documentation and search and,
and probably they have a good search function like every API should have a good
documentation. But at the end of the day the question is will every company build GitHub level
documentation for every API they, they have?
00:15:56:24 - 00:16:24:12
Jens
We think that's it's kind of hard to, to accomplish. And then there's this other question. If you
have GraphQL schemas with, I don't know how many thousands of, of lines of code, how can
you actually navigate that? But because even if you're a dev, even if you know how to write
GraphQL queries. How do you how do you efficiently navigate, a big, a big GraphQL schema
and understand.
00:16:24:12 - 00:16:56:18
Jens
Okay, how how can it help me? How can it solve my problem? And you could now say, it's it's
easy, simple, simple problem. I just take the schema, I dump it in my file system, and, I just ask
ChatGPT to to look through that, and then we're done. Right? Is it so easy to to do that or what
what what are the challenges working with like
00:16:56:21 - 00:17:04:24
Jens
If we build an application that looks at the GraphQL schema, and then we have a use case and
it should give us a query, well, where's the challenge?
00:17:04:26 - 00:17:30:23
Cameron
Yeah, there are several challenges to think of. So the first large challenge that I see to do it
quickly is especially when you get to the GitHub size schemas or you get to, you know, any
large GraphQL schema, you don't want to be putting that into the model every single time you
want to query it, you know, you want to figure out how to slice it and only give the model access
to the data it needs to generate that query.
Jens
why?
00:17:30:26 - 00:17:54:05
Cameron
So you want to do that because of speed, cost, You know, you can also hit the limit of the
maximum number of tokens that the model can actually process and context. And once that
happens, you know, it will lose parts of that memory. And for all you know, it might be that very,
very top line that it actually needs.
00:17:54:08 - 00:18:03:05
Cameron
query.
So you need to figure out what it needs in order to, in order to allow it to accurately generate the
00:18:03:08 - 00:18:14:10
Jens
You said speed, you said cost. is cost. Really? Like, are we talking about cost here or is it like
an artificial problem that you think it exists?
00:18:14:12 - 00:18:36:22
Cameron
It's in the current state of the market. It's not as large of a problem as I think it will be in the
future. As models get more and more stable and more and more accurate and more and more
able to do things, I think we'll see the cost rise. However, right now, you know, you're it's you're
constantly querying git all day.
00:18:36:22 - 00:19:01:12
Cameron
You're still not looking at, you know, if you're, constantly uploading 400,000 tokens, you're not
looking at a super nominal cost, like it's still something that will add up over, you know, a month
or two months or something. You know, it's not going to be tens of thousands of dollars, but it's
still, you know, if you have 20 engineers querying it, it still could be thousands of dollars.
00:19:01:15 - 00:19:13:16
Cameron
And that is something to kind of think about when you're looking at an organization. And how an
organization can implement a tool like this, at scale, is that scaling factor of cost?
00:19:13:18 - 00:19:35:06
Jens
Yeah. And and the other problem you mentioned performance. So let's say a schema has
hundreds of thousands of, of tokens. Do we always have to stick that into the, into the context
or, or like is that necessary. And also does it lead to good results or what. What is a better
approach.
00:19:35:08 - 00:20:00:05
Cameron
Yeah. So it when you just stick the entire schema in it leads to a very slow time to actually
generate, a query and generate the response. But it also is not necessarily the most accurate
because you're overloading the model with data. So you're giving it way too much information
for it to try to parse through all of it and know exactly what's happening.
00:20:00:08 - 00:20:51:09
Cameron
Because, you know, there could be like a user could be returned from both a search result and
from a viewer field or from a me field on the schema on the query type. So, you know, having it
identify the difference in those things is a little it it's not the greatest. You get some weird queries
out of that. And so by slicing up the schema into basically what I call like the root types, you're
able to do some very interesting things in order to actually calculate and figure out the vector
distance between the query and the and the different slices of the schema, allowing us to only
inject pieces and parts of the schema
00:20:51:09 - 00:21:03:29
Cameron
as opposed to the entire schema as a whole, which produces better performance, lower context
usage, and it also allows for better accuracy.
00:21:04:01 - 00:21:14:15
Jens
When when you say, yeah, I think you mentioned root types or something, right. Well, what is
the root type.
00:21:14:18 - 00:21:38:20
Cameron
A root type is, is basically what anything that is returned by an operation. So like if you have
create user and it returns a user and then you have get user and it returns a user, one slice
schema would have a query with get user and the mutation and type would have the operation
of create user.
00:21:38:22 - 00:21:48:05
Cameron
And so it's just that very base root type that is defined as a return type on the mutation or on the
query types or the subscription type.
00:21:48:08 - 00:21:56:15
Jens
So so you mean like the the fields on the root operation types like query, mutation, subscription.
00:21:56:17 - 00:21:58:15
Cameron
Yep. Exactly.
00:21:58:17 - 00:22:06:22
Jens
Okay. And so you take you take a root field or you take all of the root fields. And what are you
doing with each of them.
00:22:06:25 - 00:22:42:06
Cameron
Basically I'm grouping them by their return type. So I create like sub graphs of just only one
return type. So only have the user type or only of the search result type. And that allows me to
significantly reduce the size of the schemas and also reduce the context like not the context
size, but reduce the amount of information that I'm passing in because I'm only passing in one,
like there's only one real return type that's possible.
00:22:42:09 - 00:23:18:21
Cameron
And then I enable the model to use tools to actually find other types as well. So like for example,
you might in the GitHub schema, you might ask for the number of stars on the WunderGraph or
the WunderGraph Cosmo repository. And you might ask for the current user's username. And so
what it would do is you would return in the initial run, it would actually show, it would give the
repository and it potentially would return, for a secondary subgraph or for the secondary sliced
graph of the user, slice.
00:23:18:23 - 00:23:38:16
Cameron
However, even if it doesn't, the model actually has access through tools to enable it to re query
and re look up for different root types so that it can still access the data from other root types
and answer complex queries.
00:23:38:19 - 00:23:55:00
Jens
Okay. Got it. And one one other part you mentioned earlier is I think you you mentioned the term
vector. How how do vectors play into this whole exercise?
00:23:55:02 - 00:24:22:09
Cameron
Yeah for sure. So, we are using a vector database to do this, however, the way that, you know,
really in, in natural language processing works is that, I mean, really any artificial intelligence is
that you calculate, you turn everything into a vector. And specifically with natural language
processing, the placement of the vector is determinant of the similarity of words.
00:24:22:12 - 00:24:46:07
Cameron
So like, a user and human aren't the same thing, but they would be pretty close to each other. In
terms of where they are in the vector graphs. So you would be able to, to search for a user and
the distance would be filtered down by how far apart that vector between a user and a human is.
00:24:46:14 - 00:24:53:29
Cameron
And that's based off of the embeddings model that you use to actually generate those vectors.
00:24:54:01 - 00:24:57:10
Jens
Well what what is an embeddings model.
00:24:57:12 - 00:25:32:08
Cameron
The embeddings model is basically it's the tokenization model. So it's actually how the vectors
are calculated and it's trained on and it's trained on all of the data that goes into training
something like Gemini or Claude or, ChatGPT. So it, it holds where those, items live. So it like,
you know, like going back to the human and user, it the embeddings model would actually be
the one that would calculate and learn that human and use are near each other and close to
each other.
00:25:32:11 - 00:26:05:27
Jens
So, so that means so, frankly speaking, you read a lot of books, and from these books you kind
of learn that human and user somehow they are correlated. And so they are nearer, or whatever
you would say. And so this is then what what's in the in the embeddings model, if you put user
like I assume like an embeddings model, let's say it's a function you put in whatever and it gives
you a vector kind of right.
00:26:06:00 - 00:26:07:16
Cameron
Yep. It gives you the token which is a vector.
00:26:07:16 - 00:26:46:04
Jens
And so the vector of human and, and person would be closer or more similar than a vector
between human and car, okay. And now we have our query. We have or we have our prompt
like hey, I want to get the stars of the WunderGraph repository. So you take this text and you,
you also make it a vector or and then, then, then you search for, for your slices in the graph that
are most similar to that.
00:26:46:06 - 00:26:48:05
Cameron
Yeah. Exactly.
00:26:48:08 - 00:27:12:28
Jens
Okay. So on the high level you're kind of saying “I have a question. Take a look at all the parts of
the schema that you have indexed that are most similar. And then and then load those into the
context. And I give you then the prompt again, maybe in some other format. And then you,
you're telling me how to write the query to do that.”
00:27:13:00 - 00:27:14:12
Cameron
Exactly.
00:27:14:14 - 00:27:41:06
Jens
Okay. And then if you do that, we know there is this topic of hallucinations. Okay. So how do I
know that the query that it generates like, or how can I somehow force it to create a graphql
query, or will it just create text? Or how do I get to the point where it actually makes me a
GraphQL query and that is actually valid?
00:27:41:08 - 00:27:56:28
Cameron
Yeah. So we I did handle that in two different ways. So the first way is actually by, in the
prompting, which is it works most of the time. I actually.
00:27:56:28 - 00:27:59:12
Jens
60% Of the time, yeah.
00:27:59:13 - 00:28:03:16
Cameron
Require, You know, that's why. It's why it's two steps, not just one.
00:28:03:18 - 00:28:05:17
Jens
Okay.
00:28:05:20 - 00:28:42:06
Cameron
But I, I provide it with a tool, the validate query tool that allows it to actually verify and validate
queries against the full, the full graph. So, you know, it'll actually run a validation on the full
GitHub query or not query the full GitHub schema and it'll return back to the model, the validity
of it, or if there are errors, any errors that happen so that, that kind of acts as like a feedback
loop almost to give the model context and information about that graph and where it's going
wrong.
00:28:42:09 - 00:29:14:05
Cameron
And then the second thing that happens is actually verifying the query and parsing out the
response. After the model says, hey, I'm finished. I think this is a valid query. I actually validate
and verify the query post response. So I will parse through the returned values and I will find the
query, and I will revalidate it and triple check it against that that schema again to ensure that it is
accurate.
00:29:14:07 - 00:29:49:19
Jens
Yeah. One one one pattern I have seen with using cursor is and I think this, this is really smart.
We, we also we will also talk about what are good languages for for vibe coding. But one thing I
saw is when you have like cursor write code for you, it immediately uses a linter, which I think is
really smart because if you if you have an AI write something and then you run a linter over it,
Linters give you very good information about the thing that you just tried.
00:29:49:19 - 00:30:07:10
Jens
It's actually wrong. It's broken. So if you do that, you can immediately feedback the linter result
to have it properly form, the query or whatnot. Or maybe it's even not parseable because it's
broken. Then you can fix that. So are you are you using like a similar technique?
00:30:07:13 - 00:30:33:19
Cameron
Yeah, that's that's pretty much exactly what the verification is doing. Right now I'm not doing any
kind of actual linting on the query. I'm more just, ensuring that the, that, query it returns can be
parsed into AST, and then I'm validating that that AST is valid against the current schema.
However, you know, as with anything in this world, there's still a lot of experimentation to be
done around.
00:30:33:21 - 00:30:49:27
Cameron
And, you know, does it perform better when we add in a linter and feed that back? How does it
perform? And you know what what tweaks to this can we make to make it more accurate, more
performant and just overall better?
00:30:49:29 - 00:31:07:15
Jens
Yeah. Okay. Which which we can actually use as a transition to, to the topic of, of vibe coding
for those who don't know, like what what what do you consider vibe coding? Cameron.
00:31:07:17 - 00:31:24:23
Cameron
Whenever you're working with like something like cursor or any of those tools and you are just
really able to move quickly and it, you know, kind of saves saves time. And it's being actually
helpful. It's that makes sense.
00:31:24:26 - 00:31:50:02
Jens
Yeah. So, the way I would describe vibe coding or I kind of say like, coding with an agent or
coding an agent mode, like, you know, for a very long time, I was using, GitHub copilot. So that
is kind of the approach where you, you tab tab tab and it kind of gives you a better
autocompletion.
00:31:50:04 - 00:32:09:13
Jens
And then after a while with copilot, we had this new feature where we can we can mark some
code and then we can write a command to, to change this code. And now agent mode, it's it's
kind of completely different. You you tell it like, hey, here's a bunch of files. Here's I want to
here's what I want to do.
00:32:09:13 - 00:32:31:08
Jens
And it, it kind of changes all the files for you. And it makes all the, all the edits and, it's. Yeah, it's
an interesting approach. What what what is your experience so far? Like, where does it work?
Well, where does it not like what what what is it good at? What what what are the problems?
What have you observed.
00:32:31:10 - 00:32:56:15
Cameron
Yeah, so I have I heavily use cursor. I actually was not a big GitHub copilot user, believe it or
not. I have I've really liked cursor. However, I found that it works really well with front end work.
So with building out like, things in next or react,or Vue or any of those different front end
frameworks, and even on the back end it works.
00:32:56:18 - 00:33:27:02
Cameron
Okay. One of the big challenges, though, that I've found is actually when doing prompt
engineering and working with AI prompts, is that it'll try to autocomplete and try to autofill things
and AI prompting AI it's not at a point where it's super great yet. So I've just found that if you're
not careful with what files you allow it access to, it will mess up your prompts.
