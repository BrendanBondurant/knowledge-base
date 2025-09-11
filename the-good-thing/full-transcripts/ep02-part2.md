00:29:35:15 - 00:30:01:03
Stefan
First of all, I think that explanation was absolutely brilliant. And one of the coolest things that I
absolutely love about, you know, working with such technical folks like yourself and building this
company is that we get to see deep into consumer facing applications, and we get to see what
actually happens behind the scenes. And from let let's abstract a little bit away from the tech,
from the business side.
00:30:01:06 - 00:30:19:05
Stefan
What is the impact of slow performance on the company. So for example, they launched this ad
on the Super Bowl. And if you guys remember and Jens you might not remember this but coin
Coinbase they did an ad with just a floating QR code. And that was the entire ad. And a bunch
of people scanned it.
00:30:19:05 - 00:30:33:18
Stefan
And so many people at the Super Bowl scan it that they crashed the website. Let's say the
website doesn't crash, but it's slow. Like, what are the business impacts of slow performance
times that the pre warming cache offers for like the business impact?
00:30:33:20 - 00:31:00:27
Jens
I think I don't have to to teach business people that especially if you're in in areas like e-
commerce or something like every second counts in terms of yeah, people abandoning the
website or something. So yeah, latency or or high latency means you, you lose sales as as
simple as that. You lose customer conversion.
00:31:00:27 - 00:31:33:12
Jens
So it's it's super important and thus sorry to drift back to the technical side, but I want to
emphasize on, on one thing because I keep seeing discussions around REST versus GraphQL
and, REST versus federation and, other things. And well, one thing that that is, I think it's very
important to talk about because sometimes I hear people say like, yeah, but we can do it with
with REST and it will be faster and so on and so forth.
00:31:33:14 - 00:32:05:24
Jens
The reality is, and this is like it took me very, very long to to kind of conclude this, but if you have
a website that does what we just described and it's using REST APIs, it is very likely that you
are not fully aware what kind of Rest API calls this website does until it's fully functional versus
you have a federated GraphQL query and you're now complaining about like, hey Jens, why
does it take 10s to plan?
00:32:05:26 - 00:32:43:25
Jens
And the thing is, with Federation, we are fully aware of the complexity to load this page and, the
computation to load the data from, from all these, from all these subgraphs, from all the
microservices. This computation, it happens when we start up the router when we warm up the
cache, we compute this once and then we have a description of how do we get the data for this
page versus if you have a rest API, the front end starts up and it starts firing all these rest API
calls.
00:32:44:02 - 00:33:18:19
Jens
So with a rest API approach, this whole computation of getting all the data to make the the the
the website work, it's the federation in the sense it's happening in the browser and it's
happening at runtime when the user waits. And now the question is like you have latency
between the front end and all your microservices. And this means going back and forth between
the front end and all those microservices.
00:33:18:19 - 00:33:43:24
Jens
It's much slower than doing. It's on the backend. So now you could say, okay, Jens, let's solve
this problem with rest. We move this computation, we move it into the backend, we create a
backend for front end, which creates a single rest API that federates the data from my
microservices. You can do this now you make a single rest API call to this BFF.
00:33:43:26 - 00:34:09:19
Jens
Now you have a new problem. The BFF essentially means every time you need a new query in
the front end, someone has to build and deploy the BFF that now needs to fetch more or less
data or whatever, versus in a federated graph, you have all these teams building microservices.
They contribute to the federated graph and you have the frontend team.
00:34:09:27 - 00:34:36:10
Jens
They write the query. So actually they work like fully independent versus with Rest. Either you
have the federation in the frontend or you have it in the backend with the BFF. But now the BFF
is is like your, your yeah, your, your bottleneck because you have a BFF is nothing else but a
self-built single use case federation approach.
00:34:36:12 - 00:35:05:19
Jens
And actually what we have figured out is the limiting factor is not so much the tech and the
reason why many companies use federation. It's not a technical reason. It's an organizational
reason because you can have the BFF approach or the federation approach, but people prefer
the federation approach because it gives them more flexibility on the frontend team, on on the
backend team, because you don't have to constantly update this BFF.
00:35:05:21 - 00:35:07:08
Jens
I hope it makes sense.
00:35:07:10 - 00:35:24:01
Stefan
It makes sense. And you said something super interesting. So yesterday, if you remember, we
were on a call with the customer and you asked them like, okay, how many people like the
platform team? Like how many people are using Federation? And it was one team. And you just
said that federation solves an organizational issue. Can you expand a little bit upon that?
00:35:24:01 - 00:35:35:20
Stefan
Like what problems does this solve? Where do you see Federation, where it's the top tier
solution, and why does it solve an organizational issue?
00:35:35:22 - 00:36:04:18
Jens
Think about think about the use case where we're a product owner and we want to bring new
functionality onto our Superbowl landing page. So let's say you you have some existing
functionality. You want to expand it. So you you say okay, we need I don't know, I keep using
this this stupid example. You have a user and you want to show the avatar of the user when
they login.
00:36:04:20 - 00:36:36:11
Jens
Okay, currently our API doesn't give us the avatar. So you're the product owner. You sit together
with the frontend guy and the designer and you're thinking about, okay, how do we get the
avatar? First problem, you have this big microservice architecture. You don't even know where
the user comes from. This is not a technical issue. The first issue you encounter is who is
responsible for providing me the user data.
00:36:36:13 - 00:37:02:22
Jens
So you could look at let's say your your in rest API land. You look at the, the rest API, call that
you're making and then somehow you need to figure out where is this Rest API coming from.
What's, what are the people behind it? And, oftentimes what we hear is the frontend guy goes to
the platform team asking them, hey, can you figure me out where this API is coming from?
00:37:02:22 - 00:37:26:01
Jens
Who's building it? I need to talk to the people. I have a I have a, requirement, versus in a
federated graph, you look at the schema, you see, okay, here's the user entity. You can look
what subgraphs is this coming from. So you know okay it's subgraph user, you know, in which
team the user subgraph resides.
00:37:26:01 - 00:38:04:18
Jens
So you know who to talk to. And the next thing is if you have like a Rest API landscape, and
someone changes the user type, adds the avatar, maybe it's possible that's another team has a
similar user type, and they use it in a similar way. And they might have a word with you on
adding this avatar because they also want to have the avatar, but they don't just want the
avatar, they also want to be able to to compute, the avatar size in terms of like pixels or
something, because they have a feature for that.
00:38:04:20 - 00:38:36:26
Jens
So ideally you would know who are all the people in your organization who are stakeholders on
this user entity. Maybe you can talk with them and discuss this change. And this is something
we have seen a lot with, with Rest APIs that theres like, I don't know, 20 APIs that do something
with, with user and everybody like if they are unhappy with another API, what they do is they just
add one more rep, the previous user API and add whatever they want.
00:38:36:26 - 00:39:08:14
Jens
And that's, that's their API. Because there's no like real collaborative schema design versus with
Federation, you can actually say, okay, we have this entity, we talked with these other teams
and yeah, we, we believe enabling teams to, to collaborate on, on schema design. It's, it's it's a
big enabler to, to, to help you have, have a, have a better, more concise API that really makes
sense to the frontend teams.
00:39:08:16 - 00:39:32:04
Stefan
That that's so interesting. So allow me to abstract a little bit. Let's say that I sign up for a very
large organization. I'm a junior developer, and I was given a ticket that I need to go change the
user avatar. And we have a Rest landscape. So are you telling me that I would have to go and
ask the platform team, hey, who implemented this portion of the user entity and our other teams
using it?
00:39:32:04 - 00:39:37:11
Stefan
Like I would physically have to go and talk to it. I wouldn't be able to figure it out from the code.
00:39:37:14 - 00:40:12:18
Jens
It really depends. Like there are things like backstage, where where you have like a tool that
really, has an open API spec for every subsystem that that exists. And you can figure out who
are the people behind, but yeah, we, we have seen that very few companies actually use like,
like a registry or thing of that sort with GraphQL federation, you have a schema, it's not optional,
like open API, you can have it. GraphQL.
00:40:12:18 - 00:40:42:09
Jens
GraphQl You must have a schema, otherwise it doesn't work. And so in the in the federated
graph you must have a schema registry. So that means you must have subgraphs. Each
subgraph has a schema. And if you have a schema registry, like, like Cosmo, you also can
associate people and teams with that subgraph. So if you look at the schema, you can
immediately figure out who, the people behind it.
00:40:42:09 - 00:40:49:20
Jens
You can you can talk to them. It's it's very transparent. And it takes very, very low effort to, to
figure all these things.
00:40:49:23 - 00:41:13:27
Stefan
And for the non-technical audience, the schema is just simply like a blueprint of that service.
And so basically what you're saying is, let's say that this rest, landscape, we might use
something like backstage, but it's optional. We might not do it. Maybe we're growing so fast we
might not do it. But with GraphQL Federation, you cannot have it without a schema, which is a
blueprint of how that service works.
00:41:14:00 - 00:41:35:20
Stefan
And with GraphQL, Federation enforces that strictness. So theoretically, in a GraphQL
federation landscape, I have a visual graph of how the company kind of works in a more or less
sense. And so I can go and I can make changes. And I can also kind of tangibly see what
services are interacting with others by just simply looking at the schema.
00:41:35:24 - 00:41:38:07
Stefan
Would you say that's correct?
00:41:38:10 - 00:41:44:20
Jens
Yeah, very much. And it's it's also interesting theres what's the name again. This.
00:41:44:22 - 00:41:49:11
Stefan
It's the law right. Yeah. Moore's law I think
00:41:49:14 - 00:42:20:14
Jens
No, that's that's about growth of CPUs. I forgot the name. It's not Hyrum's Law, but that's the
law. Maybe the audience knows that's a law. It's not really a law, but the Conway's law.
Conway's law. Yeah. So good. Conway's law. So the architecture that software engineers built, it
kind of replicates the communication. Our, the communication paths of the organization.
00:42:20:16 - 00:42:50:01
Jens
So if you have three teams in your organization, it's very possible that you have three
subgraphs in your federated graph, which is a pretty good feature, because if you if you happen
to be a front end dev and you use an entity on the user service, all you need to do is figure out
who are the the people, behind the user service.
00:42:50:03 - 00:43:16:23
Jens
And it's kind of like the, the subgraph architecture you have. It's it's somehow like sometimes a
team has more than one service, but somehow the subgraph architecture, it also kind of reflects
the, the team structure of the, of the company. So it's it's it's yeah, it's it's a pretty cool feature.
And just a question, Stefan. So I know you used to be a developer in the past.
00:43:16:25 - 00:43:20:11
Jens
Have you ever created a rest API?
00:43:20:13 - 00:43:30:06
Stefan
believe so.
I did, yeah, from the beginning. Yeah. And I had to, like, did it have an Open API spec? I don't
00:43:30:09 - 00:43:56:08
Jens
Yeah. Most, most APIs in the world are Rest APIs without the spec. And there's also, you know,
there's this debate that, like, I really like the, the ideas behind hypermedia. Hypermedia API is a
pretty cool kind of like self describing you go to the API, it it tells you like, hey, here's some some
information and if you want some other information, here's some links and you can follow them.
00:43:56:08 - 00:44:26:29
Jens
And it's super cool. I just think, it's not really for humans. I think humans, they are much better
off with, with a spec. However, I actually believe that, that there will be like a new summer for
hypermedia APIs in the age of of agents because humans, they. For humans to collaborate, it's
better you have an open API spec or a GraphQL schema for, for LLM agents.
00:44:26:29 - 00:44:50:00
Jens
It's super cool. You you give them a thing like, like a user profile, and you give them a link and
say, if you want to have the comments, here's the links to download the comments. This is
absolutely perfect for an LLM agent because it can just then follow. And if you ask the the agent,
hey, can you give me information about Stefan and all the posts he ever did?
00:44:50:03 - 00:45:12:12
Jens
So you go to Stefan's website, you get the the posts. And then it gives you a link to the to the,
you get the info about Stefan, it gives you a link about his post, and then you can download that.
So yeah, I think hypermedia will be, very interesting to to see the, the effects of, of agents on
hypermedia.
00:45:12:15 - 00:45:35:03
Stefan
Yeah. I think it's super exciting. And I mean, it's just a description you kind of gave us with the
rest with GraphQL Federation I think is fantastic. With that, though, I did want to jump back real
quick to, a CEOs point of view. So we have an amazing customer. They're preparing for a Super
Bowl commercial, their first one, and it's going to be absolutely massive.
00:45:35:03 - 00:46:05:13
Stefan
They have a federated architecture. Cosmos kind of is crucial to them, which is why we've been
working so closely for this preparation. But talk to me like what's going on to your head as you
prepare our startup for an amazing opportunity? What are we going to be doing with this
customer? The war room, if you remember. What kind of preparations are we taking in place, to
prepare for this event and what can people expect will come post not mortem, but like after what
will happen, we write a blog post about it, what we describe it.
00:46:05:18 - 00:46:10:26
Stefan
Talk to me about how you're preparing for our Super Bowl event as well.
00:46:10:28 - 00:46:38:18
Jens
Yeah, so we're planning to have a war room to to support them during the event. But actually
we're or I'm thinking of this war room more like observing because I think all the work it needs to
be done ahead of time. If we have to do something in the war room, it's simply too late. So all
the all the load testing, everything, it happens ahead of time.
00:46:38:18 - 00:47:02:28
Jens
We're we're in very close contact with them, now and, yeah, we're, we're, we're working super
hard to, to gather to, to prepare everything to make sure a cache warming behaves the way we
want. So far, results are looking very good. And yeah, obviously for us, it's a, it's a huge
opportunity to to show the, the scalability of our platform.
00:47:02:28 - 00:47:37:18
Jens
So you, we, we, we hope that later on we, we can talk about the, the event and, outcomes and
everything. With permission of the, of the customer and. Yeah, but honestly, I'm not so much
afraid of the event because really, the, I would say the the bulk of the work, it's in the last year,
like, you know, you, you kind of know if your software is working or not and you kind of build this
level of confidence.
00:47:37:18 - 00:48:05:01
Jens
And I would say, like in, in German honesty, in the very early days of, of Cosmo, there were
simply situations where we kind of knew there's queries we cannot really plan. Or even worse,
there are situations where we do not fully understand how federation works. This was like very,
very early days, like over a year ago.
00:48:05:03 - 00:48:37:02
Jens
And over the last year, we, we have, like, specialists working on composition and query
planning, and they have built so much knowledge and so many, I would say, safe gates into, into
our composition and query planning and we, we really have built up confidence. Just to give you
an idea, internally, we have a database of all customer queries, all schemas.
00:48:37:05 - 00:49:07:12
Jens
And whenever we change something like composition or something like that, we have like very
rigorous process where we run through all possible combinations of schemas and queries and
we check are the query plans changing is the behavior changing. And then we verify all of that.
And yeah. You see like reliability, it's a it's a big topic for us, but it can only come from having
enough use cases.
00:49:07:15 - 00:49:56:16
Jens
Unfortunately, there's not yet like a full specification for what federation is. So, the best or the
the closest you can get to a federation specification is to to have as many customers as
possible, take all the use cases and observations and, yeah, I, I would say that's actually I
mentioned earlier there's something it's called Hyrums law and Hyrum's law kind of says that the
specification of of a software, it's, it's not really just the API specifications, but all observable
behaviors from a software are the specification of the software.
00:49:56:16 - 00:50:22:19
Jens
So for example, if you have a software that's super inefficient and it creates a lot of heat on your
CPU, it's possible that someone in Siberia is using your software to heat the room. And if you
now make the room, if you now make the software faster, it means the CPU won't heat up that
much, so they might now freeze.
00:50:22:24 - 00:50:46:08
Jens
So you you didn't change the API, you made it faster. But by making it so much faster, you you
changed one of the outcomes, one of the behaviors of the software. So you need to be careful.
You can't just make something too fast, maybe make it slightly faster or something. So I mean,
this is a ridiculous example, but coming back to Federation.
00:50:46:13 - 00:51:16:25
Jens
Federation is such a complex beast. I would say there's not a single company that knows
federation from, from, or understands it from, from A to Z. And as such, it's very important to
have things like, like benchmarks and audits and collaboration between vendors to to kind of
conclude, what is what is the agreement that the majority of people find in in how federation,
should work.
00:51:16:27 - 00:51:38:29
Jens
And on our end, it means we we have a lot of customers, we have their schemas, we have their
queries. We know what kind of outcome we want when we run the query. So we have all of that
in the in the huge internal database. And every time we change the behavior, we, we check
against that. And that's yeah, that's really helping us to to improve it but not break it.
00:51:38:29 - 00:51:44:12
Jens
And yeah. Now you know a little bit about, our life here.
00:51:44:14 - 00:52:03:09
Stefan
Yeah. Well said. So we are nearing the hour, but we do still have two more topics I want to
discuss. So I want to talk a little bit about the conversation that we had with that crazy large
customer that has a first world tech problem. But before we go into that one, let's talk a little bit
about descriptions and federation.
00:52:03:09 - 00:52:16:05
Stefan
Since we're in federation land right now. So this was a topic that came up this week. And I know
you have some thoughts on it, but what are descriptions in Federation. Why are they important
and what are your thoughts on.
00:52:16:07 - 00:52:38:00
Jens
Okay problem. Very simple. So every node in the GraphQL schema you can or I think most you
can puts a description on the node. It means you have a field. The field allows you to query user
info. And you can put the description to say like what is the purpose of this field? And this is very
important.
00:52:38:01 - 00:53:04:00
Jens
Like I mentioned earlier, you need specifications for for users. And code is not self-documenting.
You need to document why this field exists, what is the use case? And, what's important about
that? Now, you have a little problem in Federation that we figured out it it came throug, one of
our biggest customers. You have one team.
00:53:04:02 - 00:53:28:18
Jens
They create an entity, they add a field on the entity. They put a very thorough description on the
field to tell everybody else in the company. What's the purpose off the field? Amazing. Perfect.
That's the way we want to have it. Well documented APIs. Awesome. So we ship this into
production. Then a while later, second team comes along, says, oh, that's an awesome entity.
00:53:28:24 - 00:53:50:03
Jens
We add something, so they create a subgraph, they put something on top and they are like, you
know what? I want to have your field, I can use it as an input because I want to compute
something with your field. So they use the provides directive and, add this other field. They
cannot resolve it. So they put external on it.
00:53:50:05 - 00:54:19:20
Jens
So now we have a second graph that has this field. By the way same problem with shareable.
And essentially you have two graphs. They have the same field. And now both put a description
on it. One team put a description on it to tell the rest of the company, what's the point of this
field? The second team puts a description on the field because they want to have some internal
information, telling the rest of the internal team why they have this field and it's external and
blah, blah, blah.
00:54:19:23 - 00:54:43:18
Jens
So the purpose of a description in a schema can be to communicate something to the rest of the
company, or it can be to communicate something to the team. In both cases, your your tool of
choice is the description. And there's no two descriptions. There's no internal or external
description, all these kind of things, you don't have that.
00:54:43:20 - 00:55:14:14
Jens
So now you have a little bit of of yeah, of a race between, because whoever comes first, they,
they push their description or there's algorithms in other, federation solution that pick the longer
description or. Yeah, like what description should we, should we choose for our federated graph
and for the subgraph. Like what's. Yeah what's the right description.
00:55:14:14 - 00:55:39:16
Jens
And so we were thinking about this problem started an RFC process. How do we do this. Quite
often and we we are getting close to, conclusion. And somehow, we, we think the, the right ways
we introduce a new directive. This directive allows us to say the description we have on this
node. It's public, yes or no.
00:55:39:17 - 00:56:04:01
Jens
So if it's not public, it will not go into the super graph. We we want to keep that to ourselves. If
it's public, it goes into the super graph. And if a second team tries to bring in a description on the
same fields, also make it public, we will have a composition error. So in this case we now have
composition to to prevent this error from happening and not randomly choosing one description.
00:56:04:03 - 00:56:32:10
Jens
And then there's a second thing. We can now put a description on the, on the on the field. And
we can have on this description configuration directive, we can have the second field where we
can define like a custom description and this custom description. We can then publish that into
the super graph. So this allows us to have a private description for the subgraph team a public
description for the super graph.
00:56:32:10 - 00:56:39:05
Jens
And we can decide do we want to have a private or public. And if that's still not enough, we can
even have a custom one.
00:56:39:08 - 00:57:03:07
Stefan
Very interesting. And so with maybe for like the non-technical folks, this issue with the
descriptions, what's happening on the business impact or developer stepping over each other is
a slowing down development. On the business side, what is the problem that this is happening
not related to the tech side? Does that make sense?
00:57:03:10 - 00:57:35:16
Jens
I think yeah. So I would say for the, for the different stakeholders in your company, it's it's super
important to have, first of all, to have documentation on what the API does, how it works. And
sometimes you simply want to keep information within the team. And from our point of view,
coming back to our thoughts from earlier, Federation, it's a collaboration tool.
00:57:35:16 - 00:57:59:09
Jens
It allows teams to work together on an API, documentation, good documentation. It's it's
paramount to, to achieve that. It's it's the most important thing. So being able to have external
and internal documentation on, on the field, it's it's, yeah, it's it's very important because
otherwise people cannot work together. You want to know what's the what's the purpose of the
field.
00:57:59:12 - 00:58:07:01
Jens
And you want to explain to others how to use it. So yeah, I mean, that's. Yeah.
00:58:07:03 - 00:58:25:05
Stefan
Yeah. Well said and so we are at time. So what I do want to say are a little bit of closing notes.
So as discussed in the beginning wundergraph is hiring, we're hiring for engineers. We're hiring
on the marketing side. And there's going to be a lot more job postings coming soon. Benefits are
working. I wonder graph you get to work on some amazing technology.
00:58:25:05 - 00:58:44:25
Stefan
You get quarterly retreats, competitive compensation, choose your equipment, and quite
honestly, it's such a fun place to work as we did that like scale on the retreat, the biggest things
that our employees loved was how close they are to the customer and the impact that they're
making. So Wunder Graph is hiring. You can find it under our jobs.
00:58:44:27 - 00:59:01:21
Stefan
Link. Quickly apply. And if there is a job that isn't there but you think would be a great addition to
wundergraph some skills that you have. You're like, you know what I think I can bring this impact
to Wunder graph does email us directly. Mine is Stefan at wunder graph.com. And this is Jens at
wunder graph.com.
00:59:01:24 - 00:59:17:06
Stefan
From that pre warming cache setting up for the Super Bowl is going to be amazing. Super
excited for that. But other than that Jens. Any closing words any exciting things. Other anything
that we should mention before we end episode two.
00:59:17:08 - 00:59:20:11
Jens
Do you know what the good thing is?
00:59:20:13 - 00:59:22:16
Stefan
What is the good thing?
00:59:22:18 - 00:59:24:10
Jens
We're back in a week.
00:59:24:12 - 00:59:30:06
Stefan
Yeah. Is it true we are back next week, 9 a.m., eastern time and 3 p.m. Central European.
00:59:30:06 - 00:59:34:14
Jens
No, not not not not not next week. We're we're back in two weeks. Actually.
00:59:34:16 - 00:59:53:00
Stefan
Oh yeah. Jens is off next week, but I think I'm going to do an episode next week with Dustin or
Bjorn, one of the other co-founders, and I'll just chat with them. Could be fun, but you're going
skiing right? Oh, look who decided to show up. It's our good friend Mark. I hope Mark, you were
here the whole time to hear our discussion on Federation.
00:59:53:00 - 01:00:08:11
Stefan
We went quite deep on the topic, but, Awesome. Jens, as always, it's a pleasure to do this with
you. Thank you guys and everybody that joined us. Please apply if you're looking for a great job
to work on some interesting technology, and I will see you next week and you'll see Jens back in
two weeks. Thanks, guys.