---
title: Alternatives to GraphQL Federation and Their Complexity
slug: ep09-02-alternatives-federation-complexity
series: The Good Thing
episode: 9
chunk: 2
participants:
  - Jens
  - Cameron
segment: Federation alternatives discussion
timecode: 00:04:17:01 – 00:08:36:13
start_time: 00:04:17:01
end_time: 00:08:36:13
speakers:
  - Jens
  - Cameron
topics:
  - Client-side federation (multiple API calls)
  - Backend federation approaches
  - Backend for Frontend (BFF) pattern
  - Microservice authentication complexity
  - REST API expansion problems
  - Matrix configuration complexity
  - Contract testing challenges
tags:
  - bff-pattern
  - microservices
  - api-design
  - ai
  - authentication
  - benchmarking
  - federation
  - go
  - graphql
  - graphql-federation
  - rest
  - rest-apis
  - startup
topic_tags:
  - bff-pattern
  - microservices
  - api-design
entities:
  - SoundCloud
  - GraphQL Federation
  - REST APIs
  - Backend for Frontend
mentions:
  - frontend making multiple API calls
  - account service and billing service
  - microservice-to-microservice communication
  - SoundCloud BFF usage
  - contract testing matrix
  - breaking dependencies
summary: Cameron and Jens discuss alternatives to GraphQL Federation, including client-side
  federation with multiple API calls and backend federation approaches. They explore
  the complexity of Backend for Frontend (BFF) patterns, using SoundCloud as an example,
  and explain how federation helps avoid the matrix configuration problems that arise
  with multiple clients and backends.
---

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