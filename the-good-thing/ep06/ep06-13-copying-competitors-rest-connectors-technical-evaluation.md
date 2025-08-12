---
title: Copying Competitors, REST Connectors, and Technical Evaluation
slug: ep06-13-copying-competitors-rest-connectors-technical-evaluation
series: The Good Thing
episode: 6
chunk: 13
participants:
  - Stefan
  - Jens
segment: Copying competitors, REST connectors, and technical evaluation

timecode: 00:41:07:19 - 00:45:00:15
start_time: 00:41:07:19
end_time: 00:45:00:15
speakers:
  - Stefan
  - Jens
topics:
  - Copying competitors
  - REST connectors
  - Technical evaluation
  - Product strategy
  - Engineering philosophy
  - Startup competition
summary: |
  Stefan and Jens discuss the challenges of copying competitors, the technical evaluation of REST connectors, and the importance of thoughtful engineering and product strategy in a competitive landscape.
tags:
  - graphql
  - ai
  - apollo-graphql
  - rest-connectors
  - startup
  - startup
topic_tags:
  - graphql
  - ai
  - apollo-graphql
  - competitor-analysis
  - rest-connectors
  - technical-evaluation
  - product-strategy
  - engineering-philosophy
  - startup-competition
entities:
  - Stefan Avram
  - Jens Neuse
  - WunderGraph
  - Apollo
  - graphql
mentions:
  - REST connectors evaluation
  - competitor copying decisions
  - N+1 problem identification
  - technical architecture review
  - customer migration compatibility
  - engineering philosophy
---

00:41:07:19 - 00:45:00:15
Stefan
So we were talking about copying the competitors. There's something that a competitor
released rest connectors, another copycat competitors copying that. We're not copying that.
Why are we not copying risk connectors? What is your opinion on the rest connectors. And I can
bring up the diagram if you want as well, because I know you made a LinkedIn post on it, but I
want to go through it anyway.

Jens
So we we it's possible that we would have to somehow copy it if customers want it. So far they
don't want it, which we're lucky about it. Well, one thing about copying competitors is, if you
want to allow customers to migrate from a competitor to your solution, somehow there needs to
be some sort of compatibility.

And, for example, we created some compatibility feature flags, because, there's cases where,
Apollo router and gateway, they do very interesting things. For example.

Stefan
That's interesting. I like how you said.

Jens
Interesting, keeping it interesting. So, there's I, I don't know, they. Yeah. I mean, I'm not blaming
them. Okay. But sometimes you, you come up with quick solutions for problems and, you know,
like, well, one of the, one of the most persistent, solution is a quick solution because you
implement the customer uses it, then somehow you, you, you can never remove it because it
would break someone.

So there's just features in Apollo Gateway where it, it puts errors in weird places like not in
errors but in some other field. And sometimes they format things differently. And so we created
some feature flags so that we can accommodate for a customer to, to to easily, move over. But
if we look at connectors, so, you know, there's always this tension between what customers
want and somehow we try to push back if we think it's not a good idea.

But you cannot always push back all the way. So, I think we have prepared some screenshots. I
did a post like, a while ago, and that's just one thing I wanted to talk about this with connectors,
is, because, you know, we're we're our, our philosophy is not to, to to generally shit on
competitors like this is it's not our it's not our style.

We, we understand ourselves as engineers, and we just want to evaluate the technical solution
and look at the architecture and see it doesn't make sense or not. And, so Apollo did this demo
this week with, connectors. And, if you are, like, a GraphQL veteran like me you spot n plus one
problems from 100km away like it's you just see them immediately, like you look at something
and n plus one boom.

And here so we have this situation where, you know, we, we, we have one API call this plus one
where we load, products. And then we have n API calls where for each product we make a
second rest API call to fetch the price. And if you go to the next slide.

Here go to slide three first. So the slide four actually. Okay. The reason why you can so simply
spot this problem is so you see here that we have products and we attach this connect directive
and it returns a list of product. So this is the first hint. And now you go back to slide 3. We.

So you know we're getting a list of producst. And then here inside product you see that inside
the product type we now connect the price. And if you connect these dots you know we now
attach a single field resolver to an entity to to a type that's within a list. And the problem is very
simple like how can you avoid this is what you need to do is if you create like a list of things and
you want to attach something to the list, both resolvers need to be on top of the list, because
what you need to do is you need to fetch the list.