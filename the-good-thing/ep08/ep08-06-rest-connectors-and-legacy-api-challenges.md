
---
title: REST Connectors and Legacy API Integration Challenges
slug: ep08-06-rest-connectors-and-legacy-api-challenges
series: The Good Thing
episode: 8
chunk: 6
participants:
  - Stefan
  - Jens
segment: Analysis of REST connector approaches and limitations
timecode: 00:42:02:19 – 00:49:03:07
start_time: 00:42:02:19
end_time: 00:49:03:07
speakers:
  - Stefan
  - Jens
topics:
  - Apollo REST connectors critique
  - GraphQL directive complexity for REST mapping
  - Testing and CI/CD challenges with directive-based APIs
  - Real-world REST API complexity beyond simple examples
  - Mutation and POST request handling difficulties
tags:
  - federation
  - graphql-federation
  - ai
  - rest-connectors
  - graphql-federation
  - api-integration
  - testing-challenges
  - graphql-directives
  - legacy-apis
entities:
  - Apollo
  - graphql
  - REST APIs
  - Stripe
  - OpenAPI
  - JSON Schema
  - Stefan Avram
  - Jens Neuse
mentions:
  - per-request billing concerns
  - JSON mapping limitations
  - HTTP status code handling
  - discriminator fields
  - CI testing framework needs
  - Stripe mock integration
  - PATCH and POST complexity
  - n+1 problem solving
summary: |
  Critical analysis of REST connector approaches in GraphQL federation, with Jens explaining the limitations of directive-based REST integration. Discussion covers the complexity gap between simple demos and real-world REST APIs, testing challenges, and the need for proper CI/CD integration beyond playground validation.
---

00:42:02:19 - 00:42:18:09
Stefan
Yeah. And it was fantastic collaboration all around. And what was cool is there's a quote in the
case study is like, or the creators or Prometheus or the creators of the framework, and they
scope it out and they were like, we don't want to build our own gateway. We should just partner
with someone has done it before.
00:42:18:09 - 00:42:34:11
Stefan
And that's exactly what happened with SoundCloud. And we also have more exciting features
coming soon, so I'm happy that theyre a customer, I use them daily. I actually am a pro user of
SoundCloud. That's where I find all my new music, so check them out. Also check us out if
you're interested in partnering up with us. But yeah.
00:42:34:14 - 00:42:56:19
Stefan
Okay. Let's go through a little bit. There's some spicy topics on here. We have to keep the last
one for the end. But talk to me a little bit about what you've been seeing from these rest
connectors. So obviously Apollo's pushing these out. There's other vendors in the space that
are trying to like adapt it. And I don't know I know your thoughts on it, but to me it just doesn't
feel right.
00:42:56:21 - 00:43:15:23
Stefan
And I'd love to know from you why why doesn't it feel right. And we've looked at the examples. It
goes back to that model of charging per request, and that this might just be a gateway to just
charge more per request. But what are your thoughts on these Rest connectors that are coming
out into the GraphQL space?
00:43:15:26 - 00:43:48:18
Jens
Yeah. So I, I understand the motivation or I think I understand the motivation. You, you have
existing Rest APIs and you, you want to bring them onto the graph and, yeah, ideally you don't
have to maintain extra subgraphs. You can just write a bunch of directives. And and now it's, it's
on the graph. And I think for super simple use cases it's probably going to work.
00:43:48:18 - 00:44:22:17
Jens
Or even for medium advanced use cases, it could work. But at the same time, what I see is,
okay, you write these descriptions, you describe how to get the data from a URL, and you also,
you describe how to probably map it. And the the issue here is the examples we see. They go
like okay, you go to a URL and back comes a JSON.
00:44:22:19 - 00:44:51:21
Jens
And then we map this JSON. And this is, this is not the reality. The reality is if you have well-
designed REST APIs, a REST API can return anything, I don't know, like it can return the 200.
Okay. It can return, bad request. It can return 404, 401. It can return all sorts of status codes.
00:44:51:23 - 00:45:21:16
Jens
It can also return unions or combinations like, you know, there's, there's one of or any of, like
these, these, directives and open API and the REST API can also have, a field that acts like a
discriminator. And based on this field, the response shape will look differently, like it's it's open
API, it's JSON schema. So it can get super complex.
00:45:21:18 - 00:45:51:06
Jens
And so far the examples I saw is just yeah URL you get one thing back super simple and that's
it. And I don't know it's it's not realistic. I think what is much more realistic is that you need a lot
of, a lot more code to handle different cases. And then there's the question if you write these
directives, you need to have a process of getting this into production.
00:45:51:06 - 00:46:18:23
Jens
So how do you test that the directives properly describe your API. And then in the future, if the
API changes or you need more features, it means you need to change these directives. And
once they are changed, you need to test again that it works. And what I have seen in demos is
we create these directives. Then we open the playground and we make a test request.
00:46:18:26 - 00:46:50:26
Jens
And now we see this works. Okay. Yeah. That's not how we do CI. We do CI by running a test
framework of sorts. So if I if I can only describe the schema with directives, how do I write my
tests. Because in the end I need to write code to run a test framework. So if I write code for the
test framework, can I also just write code for for the resolvers.
00:46:50:26 - 00:47:31:06
Jens
And then I can do all sorts of mapping and everything. And the other thing is all of this is super
easy if we're talking about, GET requests. But what about PATCHes? What about POSTs? What
about mutations in general? Like you can't. If you have a well-designed REST API, you can't just
map a GraphQL input to a JSON PATCH object or POSTs if if I if I make a POST and I open the
playground to test it, then I'm mutating data.
00:47:31:06 - 00:47:58:11
Jens
So now I need a mock or like and how do I do all of this? So I don't know. It doesn't feel right for
me. To give you an example, Stripe, if you want to integrate with Stripe, there is a component
that Stripe offers where you can set up a Stripe mock locally because nobody wants to run tests
and send money.
00:47:58:14 - 00:48:23:02
Jens
Why, why, Stripe or create transactions? You want to run this against the mock. So you need a
valid Stripe mock of sorts. And you can run this locally or in your pipeline. So you need
orchestration code to run this Stripe thing. And yeah, I don't know. So I don't want to say it's
100% bad, but I understand the desire.
00:48:23:04 - 00:49:03:07
Jens
It needs to be easier. Yeah. To bring rest and other legacy APIs onto the graph and at the same
time and, and, like, you know, it's it's competition, but, I think my, my, my biggest pet peeve with,
with Apollo is I think they rush these kind of things. I think we need to go much slower and think
more about what is what is a good framework to bring REST APIs onto a graph, because there
are problems like you need to solve ‘n plus one’ problems.