---
title: Federation Directive Complexity and Technical Debt
slug: ep07-10-directive-complexity-and-tech-debt
series: The Good Thing
episode: 7
chunk: 10
participants:
  - Jens
  - Sergiy
  - David
segment: Apollo Federation directive critique and solutions
timecode: 00:51:07:21 – 00:57:00:21
start_time: 00:51:07:21
end_time: 00:57:00:21
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - Apollo Federation directive problems
  - Implicit behavior and edge cases
  - Evolution of federation specifications
  - Lord of the Rings "one ring to rule them all" metaphor
  - Power concentration in single directives
tags:
  - apollo-federation
  - technical-debt
  - directive-problems
  - implicit-behavior
  - specification-evolution
entities:
  - Apollo Federation
  - Facebook
  - GraphQL
  - Ruby on Rails
  - Lord of the Rings
  - Jens Neuse
  - Sergiy
  - David
mentions:
  - efficient computation problems
  - engineering complexity
  - Ruby on Rails evolution example
  - Facebook GraphQL origins
  - inaccessible directive power
  - shareable directive handshake
  - mass user enterprise effects
  - xkcd workflow comic
summary: |
  Jens critiques Apollo Federation directives for lacking mathematical foundation and creating computational challenges. Sergiy explains federation as evolutionary like Ruby on Rails, while David uses Lord of the Rings metaphor to describe how single directives can control multiple subgraphs, creating responsibility disparities and unintended consequences in large deployments.
---

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