---
title: Driving Down Infra Cost, Collaboration Features, Vercel, and AWS
slug: ep06-09-driving-down-infra-cost-collaboration-vercel-aws
series: The Good Thing
episode: 6
chunk: 09
participants:
  - Jens
  - Stefan
segment: Driving down infrastructure cost, collaboration features, Vercel, and AWS

timecode: 00:23:31:29 - 00:27:30:06
start_time: 00:23:31:29
end_time: 00:27:30:06
speakers:
  - Jens
  - Stefan
topics:
  - Driving down infrastructure cost
  - Collaboration features
  - Vercel
  - AWS
  - Startup strategy
  - Product differentiation
summary: |
  Jens and Stefan discuss strategies for driving down infrastructure costs, the importance of collaboration features, and how companies like Vercel and AWS approach these challenges in the startup ecosystem.
tags:
  - federation
  - ai
  - cosmo-router
  - cost-optimization
  - infrastructure-strategy
  - collaboration-features
  - cloud-providers
  - startup-strategy
  - product-differentiation
topic_tags:
  - federation
  - ai
  - cosmo-router
  - cost-optimization
  - infrastructure-strategy
  - collaboration-features
  - cloud-providers
  - startup-strategy
  - product-differentiation
entities:
  - Stefan Avram
  - Jens Neuse
  - Vercel
  - AWS
  - WunderGraph
mentions:
  - driving down infrastructure costs
  - collaboration features importance
  - cloud provider strategies
  - infrastructure cost scaling
  - middlemen margin issues
  - team productivity tools
---

00:23:31:29 - 00:27:30:06
Jens
And the big problem here is if you have middlemen in the infrastructure layer, that puts a huge
margin on top of on top of compute. That is that is driving up your cost. And so what we see is
that, like the most expensive asset in your company, it's your it's your people like the, the, the
HR cost.

And because they are so expensive, you want to give them powerful tools for collaboration so
that they as a team can scale and they can work together very well versus on the infrastructure
side, the goal of the company is always to drive down the infra cost. And simply put, it is very
hard to do this. If you have this like these wrappers or however you want to call them.

Like for example, you know, there was like, in the past there were, big discussions, for example,
around vercel. But if you now look closely, what Vercel is doing, just recently they announced
this fluid compute thing, and the goal is to drive down the infra cost, because also, Vercel has
probably recognized that people who scale they want to do it in an efficient way.

So the goal for infra is to drive down the cost. And the goal for collaboration is to enable more
collaboration. And because collaboration, it doesn't scale with with traffic and users, it's okay to,
to pay, a decent amount for that. So what is this, takeaway for us? First of all, router must be
open source. It must be self hostable without extra license cost.

And the goal for router must be to make it cheaper and cheaper and cheaper. So if people have
high traffic, our goal is to drive down the cost of that. And at the same time, on the collaboration
side, our goal is to enable teams to better collaborate. And I think that is very much in line with
the value perception from the from our, our users, our customers.

And I think as a, as a, as a startup, what is very important, if you think about these two buckets
where you can map out your market in other ways. But in our case, if you think about these,
these two buckets, infra and collaboration, you really want to align your revenue with the value
perception of your customer in a way that, if if we make a lot of money, I really want our
customers to get a lot of value because otherwise we get like this asynchronous situation.

That's for example, a lot of people feel with Apollo, you, you have the, your enterprise account.
And the moment you, you scale up your traffic, everybody gets scared because the infra bill is,
is so high. But the point is, it doesn't need to be that high. Like this is margin. And the the
question is, is it should it be like that?

Is it is it really aligned with, with the customer value? And we think it's not.

Stefan
I mean, on episode three, I talked with Dustin about this, which was it was it came from a
conversation with Dax. So for those of you that are, Dax, he's working at SST, which helps you
deploy on to AWS. And one of the things that we were discussing is that eventually, any
company that builds on top of a cloud, whatever their margin is, they're going to have to drive
that price down to be almost the same as Apollo, or to be the same as AWS or whatever cloud
that they're on, because it's what you said when a company scales, they're going to look at the
product and be like, this is on top

of another cloud. Why is there so much margin on top of that? And if you look ahead like how
we are and you're saying, okay, well, how can we drive down the price of infra and increase
more collaboration? That's where you want to be. And I really like the you brought up vercel
because in the past two years they were really struggling with people being upset, like, wow, my
costs skyrocketed.

Why? This is just a wrapper on top of AWS and Guillermo. To his credit, he realized that and he
said, let's drive down the cost of let's increase the collaboration feature, let's increase V0, let's
focus more on building with collaboration, because he saw ahead, and I think we saw that a little
bit earlier, like 2 or 3 years ago when we started, Cosmo was, hey, the value is never in the
collaboration.

It's always going to be a race down to zero because you're on.

Jens
Top of your set. The value is not in collaboration. The value is not an infra.

Stefan
Yes, correct. The value is not in infra because that cost is always going to go down to zero. And
for me I it's but in hindsight it seems so obvious. Like I don't understand like, you know for me
like how some companies don't realize this. You can never compete against AWS. Their
margins will be crazy low always.

Jens
You know, let me be very specific why Cosmo is open source. So let's do some game theory.
So, Apollo, it's closed source. And if you're unlucky, that can result in, in a very high infra bill
eventually, because you have billions of requests, eventually it gets super expensive. It gets
more and more and more expensive, to the point where you start thinking about, could we do it
on our own?

Could we build our own gateway? And a lot of smaller companies will be hesitant to do that.
Luckily, they don't have so much traffic, so they kind of bite the bullet and they are like, yeah,
okay, we we are unhappy and it harms the relationship actually. But they bite the bullet okay. But
then there's hyperscalers like Faang companies who also do federation.

And they can they can staff a whole team and say, you know, it's it doesn't make sense. We're
not paying millions for a SaaS when we host the router in our infra. So what do they do. They
build a team and they build their own router. And if they have good policies in the company if, if,
if it's allowed, they make this router open source.

So now you have an open source router backed by a Faang company. And so we were thinking
okay before that happens, should we not be the ones who built the foundation, the open source
router and the Faang companies can use it and extend it if we're doing it right, maybe they
collaborate with us. And this is actually behind the scenes.

This is what's happening. Like we're we're talking to multiple, Faang companies now. We
already had contributions from people working at Faang sized companies. And even if they don't
buy our cloud service because like, you know, you you can't just sell something like a SaaS to,
to a Faang company like they are. They are a different breed and not always your, your ideal
customer, but they can use your, your, your open source and they can collaborate and they can
help you make it ready for scale.

They can add enterprise features, they can battle test it. One cool thing about Faang companies
is, they can put your component under a lot more stress than you could ever do just because
they have like real traffic of billions per day. Your typical user might not have that. So that's a
whole bunch of, of benefits. And ultimately we thought if we're in the market where we build a
core infrastructure component like engine X, the router and a big Faang comes around the
corner and suddenly creates like an open source alternative, well, what is it going to do to us?

And so yeah, for for us, it was very clear from the very beginning, we don't want anybody to
create an open source competitor to us because we, we don't want to to fight that and then split
the community and everything. So we, we just we just make it open source. And I have to tell
you, I really love one thing about open source because if you have a closed source code base,
you potentially have multiple repositories.

You have maybe some parts source available, some parts enterprise license. And so what you
what you do is you, you have to do all sorts of activities. You have to spend your time to
orchestrating these different repositories to merge some stuff into a private repo. Some stuff is
public. You have to deal with API keys and everything. And we as a company, we're spending
zero time on all of this because we have one single mono repo and everything is there.

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