00:45:36:09 - 00:45:37:24
David
You, you.
00:45:37:24 - 00:46:06:25
Jens
You brought up the topic of data structures, directed graph, whatever. And, and so I didn't study
computer science, but, I think you, you to study that, at least I think correct me if I'm wrong, but
no, David. No. Okay. You're you're. Yeah. You're just gambling. It's cool. But just a question. Like
Sergiy, I know you you studied, computer science at university at least.
00:46:06:28 - 00:46:32:09
Jens
And probably, a lot of us think about, like, okay, we we go, we go to university, we learn
computer science, and we never need this, this bullshit again. It's just nonsense. But, if you
think about your work at WunderGraph and query planning this kind of stuff, do you do you think
you you learned something useful at university?
00:46:33:17 - 00:47:00:18
Sergiy
Like it? It is a bit more hard question. Like I haven't learned the Graph Theorem at university
because it's, first of all, it's, it's sits something in between, between math and, actually
programing. It's very involved into math world. And basically, I will believe that mathematicians
will, just, definitely learned in more detail that way than, I do that.
00:47:00:20 - 00:47:34:12
Sergiy
But, about education, you know, you, you may not learn everything which you need to on
because our area changing is so fast that you always need to be on the top and you always
learning something new, but it just talks, teaches you about, the approaches about, some
investments, like maybe some, algorithmic approaches just brought the basic one, maybe a
couple of programing languages, a bit of Qa bit of, project planning.
00:47:34:15 - 00:48:00:27
Sergiy
So it just prepares you to some degree, to the real world. But, anyway, once, once you start
your first job, it will be a whole different, world. Like you will need to adopt to approach this,
subject in this company. Just learn the project. Like, even when you're using git, you, you just
have a lot of approaches.
00:48:00:27 - 00:48:36:23
Sergiy
How you do the branch and how you do releases. And it's all very nice. Now, when I started
working, basically, we, initially we even didn't use git. We were using, like, the, what it was. So it
was a svn, and it is like code difference from git. And when we, when I started learning git, I just
was thinking what it is like, why we need that, like I was, I was happy with svn like why breaking
my workflow?
00:48:36:23 - 00:48:56:27
Sergiy
I don't want to do that. But then just start to learn it and yeah, actually it's quite useful. It allows
you to do a lot of things like, it allows you to do some kind of magic. It could help you with
testing, like, but, I'm not using all features of the git in, day to day basis.
00:48:56:27 - 00:49:28:19
Sergiy
Like, it's the same with education. Like, it gives you base, some some baseline. And probably I
think it teaches you how to learn things. And, this is the most important thing. Like, you just have
a lot of time when you learn something and you just trying to get used to learning something.
But, what I really enjoy in my work, like it is continuous learning, like many way you learn new
tools, you learn new stuff.
00:49:28:22 - 00:49:44:27
Sergiy
And with GraphQL, even with GraphQL, with which I worked for five years, I continuously learn
something new and we continuously improve, some old things. And, yeah, the funny thing,
sometimes I need to learn my own.
Code.
00:49:46:11 - 00:49:55:21
Sergiy
Again because, yeah, we have so much of code. It's sometimes hard just to understand, like.
Keep everything in my head.
00:49:58:23 - 00:50:00:18
David
Yeah.
00:50:00:20 - 00:50:33:17
Jens
A little bit of a spicy topic. So there is a an Apollo Federation subgraph specification that from
my perspective, it's not really a specification, but rather it's more like, hey, here are some
directives. And then there's no GraphQL Federation spec. There's a working group that is
composed of of various vendors that discuss how could such a spec actually look like.
00:50:33:17 - 00:50:59:07
Jens
But if you look at these Apollo Federation directives, like for me, I can't say that like on the high
level GraphQL federation as a concept, it's a it's a it's a good concept. It allows multiple people
to, to work together, build services. So it's a good concept. But on the technical level, to me,
sometimes it looks like, these directives were invented.
00:50:59:07 - 00:51:06:19
Jens
They were created without thinking about the math behind what they do. So there Are.
00:51:07:21 - 00:51:36:06
Jens
And I'm I'm an outsider. So I, I put this question up for you, but from an outside perspective, it
sometimes look like the directives created situations that you cannot really efficiently compute or
you cannot efficiently plan them, or maybe even it's impossible. So how do you how do you
think about these, these directives and then and how how federation works in the on the
mechanics.
00:51:37:09 - 00:52:23:24
Sergiy
What I could say about Federation, like, when you just say a use it as a consumer or just, the
customer use federation, you built your subgraphs. It's, one separate topic, like it could be an
information or what you do, but when you use it as a concept overall and you need to work with
this, this concept from an engineering point of view, it is rather huge, like it has a lot of moving
pieces, like from how you will compose things, what will be the actual results, which will be
executed and, such kind of things that could not be built, right away.
00:52:23:26 - 00:52:38:03
Sergiy
Like, it is always like some kind of abstraction, like, Ruby on Rails, like was born from, the work
which was done on some particular project. Right? GraphQL was, born like from.
00:52:39:26 - 00:53:07:21
Sergiy
From Facebook approaches and what was convenient for, from Facebook. And it is always an
evolution. So, yeah, strictly believe like Federation always also was an evolution. And you go
continuously adding features to it and sometimes you just stop to see the edge cases, and
sometimes you just do not understand all the, how these things, interact with each other.
00:53:07:28 - 00:53:16:18
Sergiy
And it is really hard to test it. But, yeah, we tried to do this.
00:53:16:21 - 00:53:24:06
Jens
David, from the perspective of composition, how do you how do you think about this topic?
00:53:24:09 - 00:53:31:17
David
Jens. If you are you familiar with Lord of the rings, do you at least know what it is?
00:53:31:19 - 00:53:36:02
Jens
There's there's a guy who lost a ring and he searches it.
00:53:36:04 - 00:54:07:24
David
Yeah, essentially. So there's one ring which rules them. All right. And I think the problem that
you have in composition is that, or with the, with federation directives in general is that there's
one directive which rules them all. And by that I mean you can have say 90 different subgraphs.
And that's just for the sake of example, say that each of these 90 subgraphs all define, the exact
same one set of coordinates that exists in all of them.
00:54:07:24 - 00:54:37:02
David
Let's say it's, Sergey is cool. Let's say that's in every single graph. And the power resides with
one person. Now, one person can add one directive on there which is inaccessible, and then
every single one of the other graphs, all 89 of the graphs, are at the mercy of that one graph
that has been now, written that it's it's that that team decided, okay, this is inaccessible on it and
it takes away the responsibility from absolutely everybody else.
00:54:37:05 - 00:55:09:07
David
And you have this disparity of responsible data. You also have it with the shareable directive,
which is a very the shareable directive trying to solve a real problem like collaboration between
teams, make sure you've got the same data. But once the handshake is completed, once, you
never have to complete the handshake again. And so essentially you have shareable in one
graph, one shareable and the other graph, and then someone else comes in, announced that
field, they could return something completely different to everybody else, but because it's
already been marked sharable elsewhere, they don't have to have any conversations.
00:55:09:09 - 00:55:29:24
David
So you have this one directive to rule them all, taking away the responsibility from everyone
else. So there were good intentions with what these directives are trying to achieve. And again,
inaccessible was designed this way for the for for the sake of migration so that you could mark
something as inaccessible in one place so you didn't have to do in every single other graph.
00:55:29:27 - 00:56:06:22
David
But it does mean that you, you do have like un, I guess, consequences that might not be so
apparent. And how many graphs and how many teams and how many people you're actually
affecting with very small changes. I think that is one of the, I guess one of the problems in how
you have you try to solve a problem, you propose a solution to a problem, and then it's only
when you have mass users and enterprises using that those features you actually start to see,
what could have been, what should have been done and what should have been improved.
00:56:06:28 - 00:56:27:05
David
It's essentially tech debt, isn't it? Like you, it's only after use and iteration you realize what could
have been done better. But at that point you've already got people, like that comic. I like xkcd
comic I posted the week. You know, no matter how bizarre your use cases is, somewhere, some
someone, somewhere that relies on that for their workflow.
00:56:27:08 - 00:56:30:13
David
So you have to be careful. Yeah.
00:56:30:15 - 00:56:38:22
Jens
If you could time travel and go back into the past and be an. Employee.
00:56:40:14 - 00:56:50:19
Jens
Or a founding engineer at Apollo, how would you change Federation? What what what would
you remove, add or or.
What?
00:56:51:07 - 00:57:00:21
Jens
Well, one thing where you say, oh, my God, like, it would be better if we didn't have to deal with
that.
00:57:00:23 - 00:57:25:09
David
For me, it would just be trying to make everything as explicit as possible we’re of the opinion
that you should, if you have an entity key and you intend to use that to jump to another graph,
you should write that entity key in that subgraph. So you have an entity key on the source. You
have an entity key on the on the target, and you have a handshake.
00:57:25:11 - 00:57:47:12
David
You only need to define the target because as long as you have, you can satisfy that entity key.
You can make that jump that edge between the graph. But well the problem with that is in the
subgraph. So you have a team that owns that subgraph. They might not know that this other
subgraph has a key an entity key that says that it accepts the ID.
00:57:47:16 - 00:58:02:10
David
For example, an ID to be able to jump there and in their graph ID is just a normal field. Perhaps
it's just marked sharable. It doesn't look like it's doing too much. They think, oh, you know,
maybe I can just remove this field because it's not a it. Apparently it's not a key because it's not
defined as a key.
00:58:02:13 - 00:58:19:26
David
I'll just get rid of it and then they get rid of it and then they realize, oh shoot. Like now, that the
composition doesn't work because it says it can't jump to this subgraph. And this was the only
route. So you could have completely avoided that problem if you just made everything explicit,
make your intent explicit in the graph.
00:58:20:01 - 00:58:22:13
David
So for me, it's explicitness.
00:58:22:16 - 00:58:25:24
Jens
It's this what you call an implicit key.
00:58:25:26 - 00:58:46:21
David
Yeah. We call this an implicit key. So you you define a key field that is not a key field in the
subgraph that it's defined. But it's a key field in another subgraph. So there's another subgraph
that has a key directive that references that same field. It's just then in that particular subgraph
that is the source that's making the jump.
00:58:46:25 - 00:58:51:21
David
It is not a key, it's just a key in another graph. And we call that an implicit key.
00:58:51:23 - 00:59:03:02
Jens
And if I'm on the receiving end of the jump and I have this implicit key and I remove it, it's that's
a composition error or what will happen.
00:59:03:04 - 00:59:12:00
Sergiy
jumps.
You can't be at receiving entries implicitly. You need to have explicit key to be able to accept
00:59:12:02 - 00:59:14:20
David
So the target. So when I say target.
00:59:14:22 - 00:59:16:19
Jens
That's what I mean. I mean the target. Yeah.
00:59:16:21 - 00:59:50:02
David
So the target has the key directive. And the key directive has a field set. And the field set
references one or a number of different fields. You cannot remove those fields because then it
doesn't satisfy the fields set define in that graph. What you can do is from the source graph that
doesn't have the key directive, you could just simply remove that and you're at the mercy of the
composition internal satisfiability graph telling you, okay, if you remove this we can no longer
jump from A to B, and that makes such and such a thing impossible.
00:59:50:07 - 01:00:10:18
David
There's a chance that, there's a chance that you don't actually need that jump. But another
consequence is that while you don't need that jump, you might have changed a single A to B
into a bunch of leapfrogging where you have to go from A to C to D to E to F to G, to H, etc. to
get to where you actually want to be, which is, say, subgraph B.
01:00:10:20 - 01:00:13:23
Jens
This is what you guys call Lego brickies.
01:00:13:25 - 01:00:37:16
David
No, this is what we call leapfrogging. We call leapfrogging. Yeah. Leapfrogging is where you
have a middleman or multiple middlemen. I guess middleman is not right. So a middle graph
and where you're visiting that graph just because your root or your destination is one place. But
to get there you have to go down certain roads because there are no other roots to that field.
01:00:37:18 - 01:00:44:07
Jens
And the middle graph, it fits into your your Lord of the rings story because it's it's middle earth.
Oh yeah.
01:00:44:08 - 01:01:07:22
David
Yeah, yeah, yeah, exactly. Yeah, exactly. Yeah, we have, we have all these internal terms like,
like, leapfrogging and Lego brick keys is another thing which I think we've discussed on this
podcast before, I'm not going to go into now, but there are a few things we don't agree with. As
such, I think Sergiy would actually agree with me that we would just prefer things to be much
more explicit.
01:01:07:25 - 01:01:19:07
David
It would prevent a lot of errors on the developer's part and a lot of guesswork on the developer's
part. If the contract and every single subgraph was made explicit.
01:01:19:09 - 01:01:21:09
Sergiy
Yeah.
01:01:21:11 - 01:01:29:13
Jens
Sergiy anything you would change about federation federation directives?
01:01:29:15 - 01:02:00:29
Sergiy
Yeah. Sometimes, more sometimes you just have allowance of some not so clear behavior, like
when you, you basically could have the same field, which, returns interface or union in one
subgraph, and then you have, as a subgraph which just returns one single member of the
interface or a union. And literally, it's not, not do an interface or union in that subgraph.
01:02:00:29 - 01:02:24:04
Sergiy
And you potentially, may even didn't have this definition of the interface union. We just will have
one connected type. And it is also more about, visibility when you just have type you don't know,
like where in, what union or interface it, participate. And it is not from the federated graph level.
And federated graph.
01:02:24:05 - 01:02:59:27
Sergiy
You will see it. Yeah. Right. That I have this type and implement this interface. But it's a
microservice architecture kind right. You have a lot of teams, one of like some of our customers
have like 10 maybe two, 20 teams, which, each works on, separate subgraphs and they have to
coordinate each time, like, the collides with each other, because so yeah, just not that's visible
when you do some changes that you will, affect that as a subgraph.
01:03:00:00 - 01:03:24:13
Sergiy
But of course it will get you that composition. But then you need to do change and to check,
compatibility, with just like a typical workflow how you federation. But, yeah, but just believe that
this workflow could be better and, it could bring you add just a bit more information, imagine
your just a new developer and you join in the team.
01:03:24:16 - 01:03:48:27
Sergiy
But by reading just only subgraph schema, you, will see some kind of possible things which, you
could expect to have another subgraphs without need to see into huge federated graph schema
with which could be like, three, 30,000 K of lines. Right. Or I don't know the numbers.
Like.
01:03:49:21 - 01:03:58:01
Sergiy
It has no limit. It just depends on your, on your amount of subgraphs and the amount of types
and fields and so on.
01:03:58:04 - 01:04:06:14
David
That's a baby graph. Sergiy So I think my biggest, the biggest I've seen is over 100,000.
01:04:06:17 - 01:04:41:29
Jens
I think what you what you two are kind of saying it. It's also in the, in, in the same ballpark of of a
tweet I saw a while ago from, from Marc-Andre working at Netflix who like a while ago, he said
something like, it would be nice if if GraphQL Federation had a few less directives and if it was
more, more strict and and I think this is this is overall kind of similar to to what you guys are
saying.
01:04:41:29 - 01:05:13:00
Jens
And, yeah. If you talk a little bit about the, the GraphQL Federation ecosystem. So you guys are
participating in the, GraphQL working group for the, composite schema. That's, living under the
umbrella of the GraphQL Foundation. Maybe you can explain a little bit, what what is the, what
is the goal of this of this, working group?
01:05:13:00 - 01:05:18:10
Jens
And then what are the the participants trying to achieve?
01:05:18:10 - 01:05:23:23
David
Yeah, it's under.
To rule them all. But, yeah, we've.
01:05:23:23 - 01:06:03:00
Sergiy
Been participating for not a long time. We was not there from the beginning. So, we just get into
speed up to get into understand it a bit, but, one, one cool part about it, but, like, the main goal
is that you won't need subgraph libraries anymore of this composition spec, because with the,
Apollo Federation, you basically need to comply with a specific format of, subgraph and specific
behavior, which is also kind of implicit behavior that is getting added into your GraphQL schema
by the subgraph library.
01:06:03:02 - 01:06:45:03
Sergiy
Like, you get some service fields, some internal fields which, are intended to be used not by
user, but by the, Federation getaway. It is possible to use it, manually in case you know what
you are doing, but it is not that friendly. And, yeah, one of the interesting things it's, that really it
should make possible to use more regular GraphQL, APIs by just instructing, the query planner
of how to fetch data, how to set entry points, how to send keys, and, it will allow you to just
bypass subgraph libraries.
01:06:45:05 - 01:07:24:15
Sergiy
Potentially you just will need some kind of validation. Apply it to that. But, even not sure that
subgraphs are typically have, some kind of validation which, different from their regular
GraphQL validation. Usually you just doing that at, composition time with composition checks
and. Yeah, this is cool concept. But, yeah, I just didn't know when it will be adopted because it
has taken a lot of time to adopt graphql across, the tech world.
01:07:24:18 - 01:07:38:00
Sergiy
And, then there was some time like, from 2019 when the Federation righ, David do you recall?
01:07:38:03 - 01:07:41:04
David
Let's, let's say 2018.
01:07:41:06 - 01:08:09:03
Sergiy
Yeah. So like 6 or 7 years ago, it's, it's a period and now now it's adopted. And, yeah, it's
supposed to be an evolution of federation, but, it could take some time to migrate to this
approach. And, yeah, it's quite interesting to participate and to see, what will happened. And it is
the same, the same thing basically, as with our day to day work.
01:08:09:05 - 01:08:14:07
Sergiy
It just interesting to see wasn't the first you could have and how people will use it.
01:08:14:09 - 01:08:25:22
David
2019 sorry. 2019 was the earliest sort of made public. And then 2020. So it probably existed a
bit before that. But yeah, 2019 2020.
01:08:25:25 - 01:09:07:06
Jens
Yeah. What one one like you mentioned Sergiy, one, one idea of this new spec is it you can just
have a regular GraphQL server and the router will figure out stuff and query planner. But at the
same time, if you if you look at these early designs, one thing that immediately caught my eye is
batching, because I would say the, the, the one thing that I, I have like a love and hate
relationship with in Federation is we have this entity underscore entities field that gets an array
of any which is representations.
01:09:07:08 - 01:09:33:17
Jens
And we have no clue what that is. It's just JSON. But the the good thing about this approach is,
we have automatic support for batching, as bad as it is, but that's like the upside, if we go away
from this approach and we just have, like, regular GraphQL fields in the root, and we want to
batch load, entities or something.
01:09:33:17 - 01:09:37:00
Jens
How how will that work?
01:09:37:02 - 01:10:06:20
Sergiy
There's ongoing discussions and that's, how it could be done. There is, multiple possible options
like, you could just have like kind of kind of batch root fields like get product and get products,
for example. Then all the possible way that it will be somehow uploaded, to their top level of
GraphQL spec, there is some concepts, of batch execution of variables and queries.
01:10:06:22 - 01:10:37:16
Sergiy
And I'm not fully aware of this option. Yeah. But it will just offload some work, probably to the
execution pipeline that you will need to more carefully, plan what you will be, doing and to my
opinion that you just need to have some kind of batch endpoint because currently it's frequent
problem, even with, reference resolvers that you anyway need to have some kind of data loader,
even if something subgraph to not have.
01:10:37:16 - 01:10:41:01
Sergiy
n plus one problem.
01:10:41:04 - 01:10:42:07
David
Yeah.
01:10:42:10 - 01:11:37:05
Jens
Okay. Yeah. Very very interesting. Another another development we've seen in the, in the
community is the, benchmarks and audits that try to benchmark and and verify the
implementation of, of, GraphQL routers. And I'm curious to, to hear what you, what you think
about benchmarking and auditing, and different approaches how to do it and, and yeah, just like
in general we do we do a lot of benchmarkING internally and we do a lot of testing and, and like
what I said earlier, we have a batch query planner that's like a headless router that can build
query plans, you can compare them, etc. if you look at this ecosystem and
01:11:37:05 - 01:11:54:02
Jens
the different ways where, where, other parties, try to, to bring tooling to verify and benchmark,
like how, how do you think about these, these approaches and maybe you see some, some,
some good things about it, but also some drawbacks.
01:11:54:04 - 01:12:42:19
Sergiy
Any given benchmark. And there's always questionable topic because the benchmarks could be
biased. Like you could, have some kind of, a particular conditions under which, you will
degradation performance or, you will get high end performance. And sometimes it is, not like a
feasible to, to have a one single benchmark for every possible scenario because there actually
is federation, like bunch of possible scenarios you could benchmark, just a router, gateway, just
make sure that you are not, testing actual throughput of your subgraph, because it also could be
a case that just your subgraph is not not so fast.
01:12:42:19 - 01:13:09:06
Sergiy
Right. Then you could, sometimes benchmark like, a full life cycle of the query, like, and it will
involve, query planning, and you will, of all kinds, for example. Right. Just to measure like how
fast you could find the query and, typically you should spend that time in. planning just the first
time when you reach the query and then after that it will be cached and just like negligible.
01:13:09:09 - 01:13:47:11
Sergiy
But at the same time, if your cold query takes like a lot of time to just fetch so some for the first
time, it also could be a problem, then it could be a complexity benchmark and like how fast you
will be able to transform some query, which requires a lot of transformation. But yeah, all these
different parts, it will have an influence on the, results of benchmark and just, typical benchmark
around the gatewayt involves, like throughput, like requests per second and, some other data.
01:13:47:11 - 01:14:15:10
Sergiy
P95. Yeah, something like that. But, it is really just a bit more about that in this case. And, yeah,
you should be just careful when you're creating benchmarks or I believe we should be careful,
even if you, publishing our own benchmarks, because maybe we could also be a bit biased, a
bit. And, yeah.
01:14:15:10 - 01:14:42:16
Sergiy
Second topic. It was about the audit. Yeah. I know in particular what audit you are talking about,
it is actually interesting. Like I have also my own opinion about that and this opinion not related
to the audit itself. It is kind of like, related to the evolution of, Federation itself.
01:14:42:19 - 01:15:10:28
Sergiy
And, it's everything about the customer experience and customer like way of thinking. Yeah.
Actually, you do not have a lot of directives in Federation, I believe. I'm not sure which could be
safely removed because it's highly adopted right now. But, the important thing is that there is ton
of, combinations. How you could apply them.
01:15:11:00 - 01:15:44:06
Sergiy
And, the more subgraphs you have, the more complicated they are. It is much more or less
predictable. And, it is hard to, to find all these edge cases, but, probably it is more simple when,
you just have a graph and to have some basic set of rules, how you interact with that. But, it is
will be like you just need to implement it right.
01:15:44:08 - 01:16:14:02
Sergiy
In this graph and you may not even know how customers will use your, implementation in which
way they will use it. And, yeah, this is a problematic. So, audits, somehow could also biased, but
they are very useful because in case they are done by a third party company, like, will not
involve it in your approaches, in your relations with customers.
01:16:14:04 - 01:16:43:00
Sergiy
It's actually a very good thing because it just whole lot, different point of view, into this area. And,
it is useful to have different points of view and, it really could show how you could improve and,
you could contribute there and, also improve, other solutions. It's kind of, so some role it is to
have the single spec.
01:16:43:02 - 01:17:05:27
Sergiy
But, until the not all the rules are defined. Each of the parties could, try to show, the bits of, this
rules and, you just at least you have some basics to, to implement something you, try to cover
some basic things and such kind of audits. It could help you.
01:17:05:28 - 01:17:29:28
David
Is that if every now and again we get a question from somebody like in one of our community
places like discord or whatever, and they ask us about, benchmarks. And typically our answer
is, the only benchmark you can trust is your own, when you when when you have vendors
creating benchmarks, you have to ask yourself.
01:17:30:04 - 01:17:53:22
David
And this includes, wundergraph as well is, is, is a vendor going to, deliver something to the
public that makes them look bad? But and the answer is that, obviously, no, you're not going to
do that. So it is a is a benchmark really capturing the reality of all situations when, the real
reason the benchmark is created is for marketing purposes.
01:17:53:24 - 01:18:18:24
David
So you have to you the only the only data you can trust is your own. And that's my first opinion.
And when it comes to things like, audits, again, if, if that's led by a vendor, and the vendor is
deciding what is or isn't important to include in said audit, they've decided what is it, not audit
what is not in the audit.
01:18:18:27 - 01:18:49:22
David
Federation is a topic that is huge and the, the, the combination of directives and different types
of graphs and, different ways to, write schemas and things mean that you have infinite
combinations. And there's not one vendor, Apollo included, anybody who can solve absolutely
every single possible thing because there are endless, endless possibilities and no one can
account for endless possibilities, no matter how good you are.
01:18:49:25 - 01:19:12:24
David
So who decides what is important is, is is one topic. What's important to, one company might
not be important to another company. And what really is important is what, customers want.
And, and every vendor has their own customers, and those customers have issues. And those
issues need to be solved or need to be, the solution needs to be reliable.
01:19:12:27 - 01:19:41:16
David
And those are the real kind of benchmarks. Is that is it working for these customers? Do they
are they able to get the, data reliably and safely? Are they able to prevent downtime and
whatever else? And there's only so much that an audit is a, or any, any benchmark or any audit
is always just, a lens on a small is a small lens that's focusing on, on a small section of the
bigger picture.
01:19:41:19 - 01:20:04:28
David
That's kind of how I see it. I could, like anybody here, could find any number of things wrong
with any of the number of vendors. You you could, you could, you could. I could create
something that makes, you know, company y look terrible because I've written that. So you
make everything that is in this is in this, audit makes that that company fail everything.
01:20:05:01 - 01:20:28:10
David
Likewise, I could make it look like I, I pass everything, whereas I'm not passing things up. As
long as you go out of that scope, I'm no longer passing those things. So I would take any
benchmark, any, any audit, anything like that with a grain of salt and do my do your own kind of
research and benchmarking and figure out what what what works for your solution, what works
for your company and whatever else.
01:20:28:13 - 01:20:36:07
David
trust things so far.
I think it's important to know that everybody wants to look good. So, you know, you can only
01:20:36:10 - 01:21:04:16
Jens
Yeah. Well, one comment from my side, I would say, even if there's no ill intent on the side of
someone creating and publishing a benchmark or an audit, I would say there's always bias. Bias
in the sense that I mean, obviously, like, even if we if you said like, okay, everybody wants to
look good, but at the same time, everybody knows the tool best.
01:21:04:16 - 01:21:43:16
Jens
So I know exactly how to configure wunder graph, cosmo router. But another vendor who
doesn't know it and who actually doesn't care to correctly configure it because they want to look
good and they are not deeply interested in in perfectly configuring cosmo router, they will maybe
just use defaults and then deploy the whole thing on the machine that is so big that the defaults
don't make sense, because the defaults are designed for, for a smaller machine or whatever.
01:21:43:16 - 01:22:25:28
Jens
It can be any situation, and this can happen to anybody in any direction like that. There are
other vendors. They have a gateway in written in Node.js. So we know if you want to build
something or if you want to get the best performance out of Node.js, it's probably very likely that
you deploy a large fleet of gateways on ports with one CPU, because there's no big reason to
deploy Node.js on multi CPU machines, or you add like an extra scheduler and then you run
multiple instance, like you can do things like that, but it's it that's complexity.
01:22:26:04 - 01:22:53:26
Jens
So I think that's always this kind of bias that for example, you you like we know how cosmo
router works. We know what kind of caches it has. And we know how to use these caches
efficiently. And so that that's that's one topic. And another topic is I particularly dislike crafted
unrealistic benchmarks. And I explain why.
01:22:53:29 - 01:23:17:26
Jens
So a benchmark you can use k six or whatever and you can design this benchmark how how
you, how you like it. And then typically you can do things like ramp up and then you have like a
bunch of queries and you fire these queries in various ways, and you benchmark the shit out of
the router.
01:23:18:01 - 01:23:51:02
Jens
Okay. So you're hammering the router with traffic, and you get whatever results and you're like,
okay, one benchmark is faster than another, and now you go into production. And in production,
something completely different happens in production. Let's say you are a very big e-commerce
website, and you have billions of requests per day. That means you don't have one router, you
have a hundred routers, maybe a thousand, I don't know, like it.
01:23:51:04 - 01:24:12:00
Jens
It can be many, many routers. And so what is the life cycle of a router? From time to time, you
need to ramp up the number of routers. Then you scale them down because you have changes
in traffic patterns. Like maybe at night there's less traffic a day there's more traffic. So you ramp
up, you ramp down. So you have new instances of the router.
01:24:12:02 - 01:24:49:26
Jens
And then there are situations where someone changes a subgraph. So you publish a new
configuration. So now the router needs to invalidate the configuration. And the thing is in your
benchmark you're assuming that you have one single router and it has a stable config. But that
doesn't really matter so much in reality because in reality, let's say you have 100,000 concurrent
users on your e-commerce website and they are loading the shopping basket or whatever they
want to buy your products, and you invalidate the router config.
01:24:49:28 - 01:25:22:12
Jens
That means we would now have to query plan all queries. On I don't know, 100 routers. So we
would immediately get the spike in, in in CPU and latency because sometimes query planning
can take milliseconds. It can take second sometimes worst case, some queries are very
complex to plan. So what you benchmarked in your lab versus what really matters in reality it
can be different things.
01:25:22:12 - 01:26:02:29
Jens
And this is something it's very hard to, to capture and to to end this real life story. We, we had
this situation with one very big, customer. There's a solution. And I think we're the we're the first
in the market to do this. We built, the cache warmer that is based on heuristics. So we sent
information from the router to our analytics warehouse, and then we we built, like, a top list of
queries that take a long time to plan and or the worst time to plan.
01:26:03:01 - 01:26:23:15
Jens
And this top list, we put that in the CDM. And when we start a new router or when a router gets
a new config, we load this top list. We don't yet accept traffic. We load this top list, we warm up
the cache. So we plan all queries, we normalize, we do all this and then we we warm up the
caches.
01:26:23:22 - 01:26:48:06
Jens
And once that step is done, we then have it accept traffic. So that means even if you have
100,000 concurrent users, they never hit like a cold router. And now you could say, well, in your
lab you're never actually testing that. So what you're testing is a warm router where all caches
are filled and that's the easy part.
01:26:48:06 - 01:27:16:17
Jens
But the hard part is we want to continuously evolve our schema. So these are the kind of
scenarios where I think yeah your your benchmarking completely fails. And that's just like from,
from my experience, think about what you're benchmarking and think about like real life stories
and real life, scenarios. So that's just my, my personal take on.
01:27:18:09 - 01:27:22:13
Jens
Benchmarking and audits and, yeah.
01:27:22:16 - 01:27:24:12
David
I know we are.
01:27:24:14 - 01:27:47:10
Jens
We are way over time. Like, but when I, when I watched, the, the the clock like half an hour ago,
like, typically we do this for, for, one hour, but I watch the number of, of, participants. We have
quite a lot of viewers actually more than, than typically. So it seems to be, a topic of interest.
01:27:47:12 - 01:28:11:17
Jens
So we we kept running. We are now getting close to the one and the half hour mark. And so I
want to I want to slowly wrap it up, I have two questions for both of you. Number one, I'm
curious to hear about, like what? What, what excites you about the future of GraphQL and
Federation?
01:28:11:20 - 01:28:24:05
Jens
And why do you think people should join WunderGraph on our journey? Why why should you,
join WunderGraph and and work here?
01:28:24:08 - 01:28:30:14
Sergiy
Yeah. For the first question answer is yes. For the second you should.
01:28:30:17 - 01:28:36:00
Jens
Okay that that is typical efficiency.
01:28:36:02 - 01:28:50:09
Jens
Sergiys end, give me a real answer. What what excites you about this, this, this job, this
ecosystem and why why should someone join us?
01:28:50:12 - 01:29:22:00
Sergiy
Yeah, they will be like, we we always have some ideas, and, we sometimes go just from small
ideas like, this configure subscription directive. It's, rather tiny change. It's not trivial to do it,
inside a composition, but for a user perspective, it looks like, router didn't change. But it's also a
lot of problems, which you actually could hit.
01:29:22:02 - 01:29:49:05
Sergiy
And when you consume API, it's important to have a proper description when you just, use the
UI, for example, to build, to query. Since you need the proper docs, it's very important to have it.
And, yeah, we continuously try to improve quality of life when we, when we, when you are using
the Federation and just by having such bits, you could, improve, a lot, gradually.
01:29:49:11 - 01:30:05:14
Sergiy
And in case you with us, you will have that, that things and you will help in the future. And we
have some other ideas, but, yeah, let's keep it secret for now.
01:30:05:16 - 01:30:16:09
Jens
David, what's what's what's your take? What what excites you about the stuff we're currently
working on? And why should someone join us?
01:30:16:11 - 01:30:35:23
David
I mean, I think I've been lucky that in, I think every job I've had, I've, I've liked to, I've worked
with. But, I really do like the whole team. I work very closely with Sergiy. I work very closely with
you. I work closely with a lot of people on the team, and I like everybody. We're quite a diverse
team.
01:30:35:23 - 01:31:02:13
David
We're spread across different, lots of different countries, continents and cultures. It's great that
we, like all in it together, building something. And we've all and a lot like Sergey, me, Suvij and
nithin, anything. Been here from kind of the inception of Cosmo. We've had new people since
who are doing a great job as well. And, yeah, I, I never wake up in a morning and think.
01:31:02:15 - 01:31:24:20
David
Oh, Lina. Oh, shit. I need to go to work for me. It's like I wake up in the morning, and I'm ready
to, start doing some stuff because I really just enjoy being able to develop things and then see
directly the consequences of those developments, whether whether that's breaking something
or someone being really happy because everything's working.
01:31:24:22 - 01:32:02:16
David
And regarding well, like joining wundergraph, like if you enjoy, solving sometimes like, I'd say
challenging problems. I mean, because essentially what we do here is that we, we solve
problems, we're a problem solving company, and we do that by software. But at the crux of it,
we're a problem solving company. And if you like to solve problems and you like to solve
problems that maybe have never been solved before, then by all means, like this is this is the
kind of job for you, if you like seeing the fruits of your labor in terms of what you're actually
building.
01:32:02:19 - 01:32:20:25
David
And if you like different perspectives, if you want to not only join the space, but actually really
set your footprint so you're not just following, you're actually leading the space. I think, that is
what we want to do here at wundergraph. And I think we're well on the way to doing that.
01:32:20:27 - 01:33:06:03
Jens
Yeah. Yeah. Great. Great insights. And I really appreciate, what you, what you shared about,
federation and, and, I think we learned a lot today about query planning, the, the various
directives, the relationship between, between composition and query planning and all of that.
And like, from my perspective, I would say, what what what brought me to this ecosystem, I, you
know, like some, I don't know, 2018 when I started working on, on graphql goo Tools, I, I was
really just interested in working with GraphQL Asts and transforming them and doing something
with it.
01:33:06:03 - 01:33:34:16
Jens
I thought that was interesting so that kind of brought me here. And today I see that with
everything we have built, we are leaning more and more towards building collaborative tooling.
So we enable other developers to to collaborate to build APIs together. We, we build tooling for,
for teams to work better together, and to build great internal APIs.
01:33:34:16 - 01:33:43:03
Jens
And, and I think this is it's a very rewarding thing because we, we have the, the,
01:33:44:04 - 01:34:11:25
Jens
I would say the, the pleasure to have so many slack connects with smart people where we build
something, they give us new use cases, we can iterate that. We can make it the tooling better
for for everybody. People can now collaborate better. And yeah, we're doing that in the in a very
fast paced loop. And yeah, no, no, we have great people inside the company.
01:34:11:28 - 01:34:43:16
Jens
We have great people outside the company like collaborating with us, working with us. And it's
it's it's just yeah, it's it's a, it's a joy. And I think we, it's also one thing I would say is when I like,
I'm, I didn't study computer science, so I'm, I'm a self-taught engineer, and I never thought that I
would be able to work in a big company, like, because, who am I?
01:34:43:16 - 01:35:12:03
Jens
You know, my education, and, like, I, I'm not I'm not on the, on the path where I would be
working at an Uber or at an eBay or at a GitHub or Microsoft, because that's smarter people out
there and they have the right curriculum to join these companies. But with WunderGraph. And
because so many big companies use GraphQL federation, we are now in the place where we
have slack connects with many such people.
01:35:12:03 - 01:35:29:00
Jens
And that's it's it's super cool. We're now at this level and we kind of bootstrapped our way there.
And yeah, I think it's it's pretty cool. Like we, we, we cannot work there, but we're actually
working with them and that's I think that's awesome. Yeah.
01:35:29:00 - 01:35:34:04
David
Don't make a blunder. Join WunderGraph.
01:35:34:07 - 01:35:37:04
Jens
Okay. I think now it's time that we shut up.
01:35:37:07 - 01:35:40:04
David
And, you know, the good thing is what what.
01:35:40:08 - 01:35:42:08
Jens
What is the good thing, David?
01:35:42:10 - 01:35:45:13
David
That I'm not here next week. What you are.
01:35:45:16 - 01:35:58:27
Jens
Yes, I am. And, Stefan will be back. So, guys, if you like this episode, you know, we don't do this
bullshit with, like, and subscribe. Like, we like. This is not a YouTube channel. This is just.
01:35:58:27 - 01:36:02:23
David
Like. And subscribe. Ring that bell to make sure you don't know this.
01:36:02:23 - 01:36:31:16
Jens
Okay, but, but but I really I'm really like honestly I'm curious. So the last episodes with Stefan,
it's typically more on the end of, we're talking about everything and we're kind of business
focused more and startup focused. This was very like deep tech. If you are interested in more
deep tech, in more deep federation discussions, tell us over whatever channel you like.
01:36:31:18 - 01:36:44:25
Jens
And we we bring back Sergiy and David I really enjoyed this episode was a lot of fun. Thank you
guys for for joining me today. And yeah, I think that's it. Thanks.
01:36:44:27 - 01:36:52:16
David
So.