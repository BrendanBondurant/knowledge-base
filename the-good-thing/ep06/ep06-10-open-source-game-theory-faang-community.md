---
title: Open Source Game Theory, FAANG, and Community Contributions
slug: ep06-10-open-source-game-theory-faang-community
series: The Good Thing
episode: 6
chunk: 10
participants:
  - Jens
  - Stefan
segment: Open source game theory, FAANG, and community contributions

timecode: 00:27:30:06 - 00:31:41:10
start_time: 00:27:30:06
end_time: 00:31:41:10
speakers:
  - Jens
  - Stefan
topics:
  - Open Source Game Theory
  - FAANG Companies
  - Community Contributions
  - Startup Growth
summary: |
  Jens and Stefan explore the game theory behind open source, the role of FAANG companies, and the importance of community contributions in building successful products and growing startups.
tags:
  - graphql
  - ai
  - apollo-graphql
  - open-source
  - startup
  - api-design
  - cosmo-router
  - go
  - rest
  - rest-apis
  - rest-connectors
topic_tags:
  - startup
  - graphql
  - ai
entities:
  - Stefan Avram
  - Jens Neuse
  - FAANG companies
  - Meta
  - WunderGraph
mentions:
  - open source game theory
  - FAANG company strategies
  - community contributions value
  - code quality in public
  - security auditing benefits
  - procurement advantages
---

00:27:30:06 - 00:31:41:10
Jens
And so our, our, all our time goes into into making it better, fixing bugs that we have created and
yeah, adding adding features. So, I don't know, it's, it's like open source allows you to be very
efficient. And also, sorry. Monologue again. Too long, I know, but, if, if, if you're open source, you
cannot you, you know, you don't fart in public, right?

Like, there's there's ways. Okay. I don't know about you. I'm no Jedi. Okay? You know, we, we
are civilized people, and you just have, like, somebody like you also, I don't know you. You don't
go in public, and then you you poop on the road or something like that. It's not like, no, we know
it's wrong.

And so the same thing in open source is you just don't commit garbage code and you don't
commit untested bullshit because everybody sees it like it's in public. So being open source, it
forces you to, to to think about some stuff, to think about security. Everybody can can see it. If
you build a proprietary source, God knows what's what's going on because we don't know the
code.

Is anybody auditing it? We don't know. If you have an open source repository. Pen testers can
test it. They can tell you about issues. They can, they can, disclose it in the, in the correct way.
So lots of benefits, I would say, where open source helps you to build better software.

Stefan
I mean, I would agree with all those points, some points that I have on that, the focus, like when
you start off as open source, you already protect yourself against, like you said, from a big
company going, you know what? No. Like we're going to just build our own. And it's backed by
meta. Like how do you compete against that?

You really can't. And so open source is a way to just kind of get it out in the front that like, yeah,
we're open source and I like that. And then the second one is open source in procurement. Like
it's a hack. Like they run a a security audit on it. It goes through and then they start
implementing it into a dev environment and boom you're already there.

If you were closed source one, you would have to solve a really big problem for them to. They
would have to go and ask procurement, hey, procurement, can you talk to Jens these guys from
one to to have a great solution. They would come talk to us. It would take a month for an NDA to
get signed, to set up an evaluation.

And then you know what happens after a month, the developers on a new project, he forgot why
he was even looking at Wunder Graph. And so being open source also helps on the sales front.
And then my final point on open source and just building a company is that or back to the
infrastructure, is that infrastructure usage based works for small scale companies.

When you have no users, it's fantastic. Oh, I just pay for the traffic that I use and I have no
traffic, so it's fantastic. My bill is zero. Oh it's amazing, but this is a trade secret if you want to
get with the enterprises. They are so against usage based. And the reason is, we can't say the
name, but me and Jens we're talking with a really cool guy from a really great company.

Everybody knows this company. And, we were just curious. We're like, so, like, we we love this
company. We all use it. How much traffic do you guys do per day? He's like, I'm not sure, but he
said, what was it, 500 million per second?

And it was a lot.

Stefan
Some ridiculous number. So let's just say 500 million per second, 500 million requests per
second. Do the math on usage based. There's no way anybody in their right mind could use any
SaaS that charges per request. I mean, that bill would be absolutely astronomical. And so when
you're thinking about starting a startup and you want to build for the enterprises, keep in mind
usage based pricing.

It works great in the beginning. But what they want at the end is predictability. And I think the
word that we were missing is exponential. You don't want your cost to rise exponentially. And I
love your example. Yeah, I have 100 employees. We have no traffic whatever. But over the year
we figure it out. We're doing crazy traffic, but we're still 100 employees.

I don't mind paying up for 100 employees, but if my traffic went from 0 to 50 million requests
today, okay, my cost could have, you know, astronomically rise. But no, I think it was a great
point. I think it was a great transition into that. And we kind of jumped one thing. But I want to go
back to this.

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