---
title: Continuous Learning and Education in GraphQL Development
slug: ep07-09-continuous-learning-in-graphql
series: The Good Thing
episode: 7
chunk: 9
participants:
  - Jens
  - Sergiy
  - David
segment: Education and continuous learning discussion
timecode: 00:45:32:06 – 00:51:06:19
start_time: 00:45:32:06
end_time: 00:51:06:19
speakers:
  - Jens
  - Sergiy
  - David
topics:
  - Computer Science Education
  - Continuous Learning
  - Apollo Federation Critique
  - Working Group Participation
tags:
  - computer-science
  - graphql-federation
  - specifications
  - ai
  - apollo-graphql
  - federation
  - go
  - graphql
  - query-planning
  - rest
topic_tags:
  - computer-science
  - graphql
  - apollo-graphql
entities:
  - Computer Science
  - Git
  - SVN
  - Apollo Federation
  - GraphQL
  - Jens Neuse
  - Sergiy
  - David
mentions:
  - university computer science education
  - graph theory and mathematics
  - SVN to Git transition experience
  - Apollo Federation directive criticism
  - GraphQL Federation working group
  - mathematical foundation of directives
summary: Discussion shifts to education and continuous learning, with Sergiy reflecting
  on university computer science education and his experience migrating from SVN to
  Git. Jens introduces a critique of Apollo Federation directives, suggesting they
  lack mathematical foundation and may create inefficient or impossible planning scenarios.
---

00:45:32:06 - 00:45:36:06
Jens
You just brought up an interesting thing.
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