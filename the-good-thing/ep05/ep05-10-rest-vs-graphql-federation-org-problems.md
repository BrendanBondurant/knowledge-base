---
title: REST vs. GraphQL, Federation, and Organizational Problems
slug: ep05-10-rest-vs-graphql-federation-org-problems
series: The Good Thing
episode: 5
chunk: 10
participants:
- Stefan
- Jens
segment: The outdated REST vs. GraphQL debate, federation, and solving organizational
  problems
timecode: 00:56:05:12 - 01:06:41:00
start_time: 00:56:05:12
end_time: 01:06:41:00
speakers:
- Stefan
- Jens
topics:
- REST vs. GraphQL
- Federation
- Organizational problems
- API design
- BFF architecture
- Microservices
- Collaboration
- Product complexity
- Team structure
- API versioning
- Contract testing
- Product adoption
- Right tool for the job
- Boring tech
- Product architecture
tags:
- rest-vs-graphql
- federation
- api-design
- organizational-problems
- microservices
- team-structure
topic_tags:
- rest-vs-graphql
- federation
- api-design
- organizational-problems
- microservices
- team-structure
entities:
- Stefan Avram
- Jens Neuse
- GraphQL
- REST
- WunderGraph
mentions:
- REST vs GraphQL debate
- federation benefits
- organizational problems
- BFF architecture
- microservices challenges
- team collaboration
- API versioning
- contract testing
summary: Stefan and Jens discuss why the REST vs. GraphQL debate is outdated, the
  real value of federation, and how API choices often reflect organizational problems
  rather than technical ones. They explore BFF architecture, microservices, collaboration,
  and the importance of using the right tool for the job.
---

00:56:05:12 - 00:56:19:03
Stefan
And what are your thoughts on that? Like why is it outdated? Like why is this argument? To be
honest, it is outdated. Like it's I see all the time. If you want to get engagement on Twitter to
start talking about Rest versus GraphQL, if you want to get some upvotes on Reddit, make a
post about how it's outdated.

00:56:19:03 - 00:56:21:06
Stefan
But what are your thoughts on it?

00:56:21:09 - 00:56:56:07
Jens
Yeah, first of all, I think that the discussion is super boring and it's it's led by people who I I'm
sure they live in the past. So if if you look at what's going on in the market, the discussion
around REST versus GraphQL, what people are talking about is two styles of APIs, of how a
client can get data from a server, and then they argue things like over fetching under fetching
whatever.

00:56:56:10 - 00:57:25:05
Jens
And yeah, that that there are pros and cons. But ultimately what we, what we what we see in the
market today is, if you are a company that has grown to a certain size and they provide their
service to other companies like B2B, sometimes B2C, but more and more B2B, you do you and
others want to integrate with you.

00:57:25:07 - 00:57:52:01
Jens
It is typically very intuitive to use Rest APIs because back end to back end, it's it's not beneficial
to in the back end to query exactly the data you need. Because just give me the data, I can I
can then figure out what I need from that. Like the that's is one thing. So like B2B integrations,
it's Rest APIs.

00:57:52:04 - 00:58:22:14
Jens
And then what we see is if a company if a company matures and they are on on rest, they have
all kinds of problems. And we seen so many customers and prospects. You have a microservice
architecture, all microservices. They they expose the rest API and then you have iOS app,
Android app, web app, other apps, and you have point to point integrations.

00:58:22:14 - 00:58:56:17
Jens
So iOS app talks to 20 microservices. That's that's a mess to integrate. And that's it's such a
brittle thing. And then you have versioning and it's it's so complex. It's an app depends on like
20 microservice or something like that. What you can do is build a, BFF architecture. So instead
of one app talking to 20 microservices, it's one app talking to one BFF, talking to 20
microservices, still kind of same, very similar problem.

00:58:56:20 - 00:59:26:09
Jens
And also what we like internally we we kind of named this manual Federation. And you can you
know when when you have an iOS app and it talks to 20, 20 microservices over Rest, then you
also use like you're also using Federation like everybody is federating. The thing is you now
federate in the client. If you have a BFF in the middle, you're federating on the server.

00:59:26:09 - 00:59:52:02
Jens
So on the BFF and it so in the first case one app, 20 microservices, it means that one front end.
It depends on these 20 services. And how do you know that if you're changing one of the
microservices that this app depends on it and that it breaks like, like people have problems with
contract testing and other things and deployments go wrong.

00:59:52:02 - 01:00:30:07
Jens
And everybody, everybody hates it BFF if you move Federation to BFF, that means the app at
the BFF, typically that's owned by one team. This contract is kind of stable, but you still have the
same problem that when backends change, when microservices change, you have to to catch
up with the change in the BFF. So you're still manually federating and you're like a new query,
how we would say in Federation it's not a new query.

01:00:30:07 - 01:01:06:25
Jens
A new query means you have to change an endpoint. It's so much manual work and it's, you
know, in in GraphQL Federation, we can change a subgraph. We run check and it tells us not
breaking clients because we can look at the traffic, we can analyze, breaking changes and
everything. Right. So we're doing all of this. We have a super like, I think one of the big points
about Federation is, you know, exactly what depends on what.

01:01:06:28 - 01:01:34:07
Jens
And you don't have to manually build that BFF. So we save all that. And ultimately what we
enable is collaboration across the teams. And so what this comes down to Federation is not
really solving a technical problem because you can federate in the client, you can federate in
the BFF or you federate using GraphQL Federation. What it solves is an organizational problem.

01:01:34:11 - 01:02:08:00
Jens
And then there's this question coming all the way back to where we started REST versus
GraphQL. It's not about commodity style versus resource style or whatever. It's it's about it's
about solving an organizational problem. And then that's why I'm like, please stop this
discussion with with REST versus GraphQL. Because it's it's about something else. And it's
yeah, it's just, it's boring.

01:02:08:03 - 01:02:13:22
Stefan
Do you think smaller organizations should use GraphQL?

01:02:13:25 - 01:06:41:00
Jens
It depends. So one of the, one of the great benefits of GraphQL is if you're really doing it right,
you can you can co-locate fragments with your user interface components, and you define the
data dependencies, like what's from the graph? Do you need per component. Then you hoist up
towards the root of the app. You hoist up all these fragments, build a single query.

And now before we load the page, we execute that, query. We pass down the data to the UI
component tree and every fragment that we have created with data masking, it picks up the
data needs and great approach. And there are tools like, relay that do this for a very long time.
There's IsoGraph from Robert.

And I think also, also Apollo client supports fragments and this kind of workflow. And I also think,
from the from the Guild, the GraphQL code generator, it it also has some very advanced tooling
to, to help, with these kind of, situations. So that's very powerful. The question to ask is, like,
what's the structure of your organization?

Do you really need this? If you are a super small startup, one single team, five devs, or if you
are in a large organization, five devs, could you just get away with Next.js and tRPC or
something like that? Because why introduce, why introduce the complexity? Like maybe this
whole fragment workflow. It gives you something if you benefit from this, if your UI is very
complex, like things like ISOgraph, like really powerful features, do you benefit from this?

It's okay. Go, go for it. Like we on our end. That's that's the funny thing. So cosmo has a control
plane. The back end.

I was gonna ask you.

This, by the way. So we have a backend. It's the control plane. It's And we have a front end. It's,
like react Next.js, and we're like, okay, this. And we have a CLI. So we were thinking, okay, cli
frontend, TypeScript, backend Node.js. How will they speak to each other? And we, we thought,
you know what, buff connect slash gRPC.

We're just creating RPC endpoints with codegen. Like we, we define like the protobuf. We
generate the code. And now you can make jokes about us. We're selling federation. We're not
federating ourselves. We're not eating that portion of the dogfood. But the reality is why should
we because we have one mono repo that contains the backend. The CLI and the frontend
owned by one team.

No other teams, no microservice architecture, one single backend. What what should we
federate? And so we don't need federation for this architecture. Use the right tool for the right
problem. And the second thing is should we use GraphQL? And we we're not we're not people
who go. We decide for GraphQL. Let's find a problem that we can solve with it.

We're more like, okay, we need to talk between a node backend, a node CLI, and then a node
react frontend. What do we do? What's easy? What's boring RPC okay, let's solve customer
problems and yeah like don't don't get hang up on, you know, built fancy tech with boring tech
like cosmos, cool cosmos fancy. Yeah. But the way we've built it is boring.

You know, Postgres, next.js super boring. The absolute worst boring thing you could imagine, is
our auth. What's the auth thing again? keycloak like the boring, boring, ugly Java thing, but it
works. And it has. It has the device flow. So device flow is very important for the for the cli.

And you can run it locally like so many auth things. You cannot run them locally. We want it to be
able to run it locally with CLI. And then you Postgres take house boring stuff. So yeah, build
build cool tech with boring tech.