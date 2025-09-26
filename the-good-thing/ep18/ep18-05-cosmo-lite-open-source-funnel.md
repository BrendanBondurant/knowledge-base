---
type: podcast-chunk
title: Cosmo Lite and the Open Source Funnel
slug: ep18-05-cosmo-lite-open-source-funnel
series: The Good Thing
episode: 18
chunk: 5
segment: Open source strategy and managed service value
timecode: 00:26:47 – 00:32:13
start_time: 00:26:47
end_time: 00:32:13
speakers:
  - Stefan
  - Jens
topics:
  - Open Source Funnel
  - Sales Cycle Acceleration
  - Managed Services Value
  - Cosmo Lite Introduction
tags:
  - open-source
  - ai
  - cosmo
  - cosmo-router
  - database
  - federation
  - founder
  - go
  - graphql
  - graphql-federation
  - postgres
  - startup
entities:
  - Lovable
  - Cosmo
  - Healthcare company
  - SoC (Security Operations Center)
  - Brendan
summary: Stefan explains how open source creates competitive advantages by shortening
  sales cycles, using healthcare company and Lovable examples where immediate trial
  access led to faster adoption. He discusses the tradeoff between offering free open
  source versus managed services, noting that while open source requires maintenance
  and collaboration overhead, the value proposition lies in production safety, internal
  test suites, and enterprise support that managed services provide.
---

00:26:47 - 00:27:03
Stefan
Have a couple of comments on it. And then after that we'll jump into the TAB. But, on open
source, I think you're absolutely right, because these companies are able to try it out. And this is
just kind of for any software as well. Like if you take lovable, for example, it's just a web app.
You just it's not even an app.
00:27:03 - 00:27:22
Stefan
You just go there, it's a website and right away you can start building things. And if you make the
path to, hey, I want to try this out to wow, this is really cool. The sales cycle gets a lot shorter.
And for example, that health care company, they talked to us eventually, but they came already
with a background.
00:27:22 - 00:27:41
Stefan
Of cosmo, now what they've done to run it, they've set it up in a staging environment. And if you
compare yourself to a closed source solution, you're eight months ahead. So they have to go
through SoC, whatever. So the opportunity for them to close a few is much better. And I think a
lot of good companies do this well is they have a great open source offering.
00:27:41 - 00:28:02
Stefan
And it's it is a funnel, but it's also not a funnel because open source takes maintenance. So it's,
open source takes collaboration. You have to run it. You have to make sure that there's no
security issues with it, and you're offering it essentially for free. But where the value is, is in, in
the managers offering, which is, hey, do you really want to focus all your time on running this
open source piece of software?
00:28:02 - 00:28:14
Stefan
Do you want to be late on release cycles? And a good blog post is Brendan just wrote about this
is when is it time to leave open source? When is it time to like have a connection with
somebody? And the reason that you just said.
00:28:14 - 00:28:15
Jens
Is.
00:28:15 - 00:28:31
Stefan
How can I ensure that when I put this into production, that nothing will go wrong with it? Well, it's
probably having a connection to the company that runs and maintains it at scale. And also they
probably have some internal stuff, some internal test suites from other customers or things like
that to make sure that this doesn't break for their customers.
00:28:31 - 00:28:56
Stefan
And so I think you're spot on there. Open source is fantastic, one, because if you really like
open source and you get to work on open source, it's amazing. You get to collaborate with some
of the biggest companies in the world. But two from a founder point of view, it just lets people
get running with your software. And Jens, if you want, I think we should talk about it a little bit,
like what's coming soon to WunderGraph Cosmos, which is, you know, we have Cosmo.
00:28:57 - 00:29:07
Stefan
It's a complicated stack, you know, and people might think like, oh, it's complicated because you
push people towards managed or whatever, but you have some plans actually around that, don't
you?
00:29:07 - 00:29:51
Jens
Yes. So, because of our experience, where we where we kind of figured out that the faster
someone gets to. This is awesome. The the, the more likely they will at some point end up in our
sales funnel. So the more likely they they will finally, you know, an engineer running Cosmo
locally, open source. This is the first step in the funnel, and I'm not I don't mean this in the
negative frame, but, you know, like, sometimes sales has this negative connection or like, yeah,
I don't like it because ultimately you have someone they try like an engineer try something out
locally.
00:29:51 - 00:30:13
Jens
It works. It solves the problem. They bring it to the company and then at some point the CTO or
the the, the security guys, they say, hey, this is awesome, but can we do SSO? Can we do this?
Can we do that? And then managed solutions, something that that suddenly makes sense. Like
we offer a soc2 stuff like that.
00:30:13 - 00:30:41
Jens
So for me, the first step is we want people to, to be successful as fast as possible to, to be able
to, to try it out to, to get to success. And what are we going to do? We will trim down Cosmo. We
will build kind of like a Cosmo Lite version where we remove some of the more complex
features that have heavy dependencies.
00:30:41 - 00:31:21
Jens
And the goal is you will have the control plane, Node.js, and you will have a Postgres
daTABase, and then you have the studio, the front end. So three components, we bundle them
together and we give you Cosmo Lite and it won't have like maybe the the analytics or other
features that that rely on on Keycloak. Click house and it won't have like SSO which we're
implementing with Keycloakg and it might not have like the full the full feature set of of Cosmo,
but it might be good enough for for many cases.
00:31:21 - 00:31:42
Jens
And we, we kind of also figured like some people, they just start out with Federation. They don't
need the whole thing. They, they actually just want a schema registry and a router. And, if you
think about it, you know, you can try to force everybody to be your ICP, but they, they they just
earn your ICP.
00:31:42 - 00:32:08
Jens
Leave them alone. But maybe they can become your ICP in the future. Are they they let's say
someone moves to another company, then maybe that company could could be ICP. So yeah,
the the goal here is with Cosmo Lite. We we want to we want to help engineers to get started
more more easily. And if they if they are not ready to buy our cloud, it's it's it's fine.
00:32:08 - 00:32:13
Jens
But, if they want to do Federation, do it with Cosmo.