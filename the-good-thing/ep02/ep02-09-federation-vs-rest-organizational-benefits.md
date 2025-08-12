---
title: Federation vs REST Organizational Benefits
slug: ep02-09-federation-vs-rest-organizational-benefits
series: The Good Thing
episode: 2
chunk: 9
participants:
  - Stefan
  - Jens
segment: Federation vs REST Comparison
timecode: 00:33:43:26 – 00:39:32:04
start_time: 00:33:43:26
end_time: 00:39:32:04
speakers:
  - Stefan
  - Jens
topics:
  - Federation vs REST comparison
  - BFF pattern limitations
  - Organizational benefits of federation
  - Team collaboration advantages
  - Schema transparency
tags:
  - bff-pattern
  - ai
  - api-design
  - federation
  - go
  - graphql
  - graphql-federation
  - microservices
  - rest
  - rest-apis
  - startup
topic_tags:
  - bff-pattern
entities:
  - WunderGraph
  - GraphQL Federation
  - REST APIs
  - BFF Pattern
  - Schema Registry
mentions:
  - backend for frontend
  - team independence
  - schema design
  - organizational structure
  - collaboration tools
summary: Jens explains how federation provides organizational benefits over REST APIs,
  highlighting the limitations of the BFF pattern and how federation enables better
  team collaboration. He discusses how federation enforces schema transparency and
  enables teams to work independently while maintaining coordination. The conversation
  covers why many companies prefer federation for organizational reasons rather than
  purely technical ones.
---

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

big enabler to, to help you have, have a better, more concise API that really makes sense to the frontend teams.

00:39:08:16 - 00:39:32:04

Stefan

That that's so interesting. So allow me to abstract a little bit. Let's say that I sign up for a very

large organization. I'm a junior developer, and I was given a ticket that I need to go change the

user avatar. And we have a Rest landscape. So are you telling me that I would have to go and

ask the platform team, hey, who implemented this portion of the user entity and our other teams

using it? 