---
title: Using Cursor for Writing and Refining RFCs and Indexing Docs
slug: ep09-11-using-cursor-for-rfcs
series: The Good Thing
episode: 9
chunk: 11
participants:
  - Jens
  - Cameron
segment: RFC writing and documentation workflows
timecode: 00:40:00:13 – 00:43:03:19
start_time: 00:40:00:13
end_time: 00:43:03:19
speakers:
  - Jens
  - Cameron
topics:
  - RFC Writing with AI
  - Documentation Refactoring
  - Comment Integration
  - GraphQL Spec Research
tags:
  - graphql-spec
  - ai
  - federation
  - go
  - graphql
  - graphql-federation
  - rest
topic_tags:
  - graphql-spec
  - ai
entities:
  - Cursor
  - WunderGraph
  - GraphQL
  - GitHub
  - GraphQL Composite Schema Working Group
mentions:
  - RFC refactoring workflows
  - pull request comment processing
  - documentation indexing
  - GraphQL specification reference
  - composite schema federation
  - markdown documentation
summary: Jens demonstrates practical applications of Cursor for RFC writing, including
  automated refactoring of root concepts throughout documents and integrating pull
  request feedback. He also shows how document indexing enables research by cross-referencing
  against GraphQL specifications and working group documentation.
---

00:40:00:13 - 00:40:27:09
Jens
Yeah it will probably look at the file and be like, okay, I should not look at the file. So I need to
read it to know what I should not look at. Right. So yeah, yeah, yeah, it's very, very interesting.
But like overall like I can say it's a, it's a super useful tool. For me I guess, one, one scenario
where I found, please write me a story that has absolutely no cats in it.
00:40:27:11 - 00:41:03:19
Jens
Okay. Yeah. Thank you, thank you. David. Here, message from David. That makes it all sense.
Yeah. So one one scenario where I found, Agent mode super, super useful is, writing RFCs
because, I'm super lazy, like, and so if you write an RFC, so two, two scenarios where I found it
useful to use cursor, the first one is you write an RFC, and after a while you come to the
conclusion that you made a mistake.
STOPPING POINT ON MARCH 19 - BRENDAN
00:41:03:21 - 00:41:32:10
Jens
Like that's very natural. You want to refine the RFC, so you want to make significant changes to
like a root concept in your RFC. If you do this by hand, it means you have to go through this
whole document. And wherever you use this root concept, you now have to make changes. And
it's gonna be tough. It's going to be like you can very easily forget something, with cursor,
00:41:32:12 - 00:41:50:23
Jens
It's it's so good. You just tell the tell the AI like, hey, here's this root concept. I don't like it. I
changed my mind. And, can we, can we refactor that? And then it will go through the whole
document, make the changes. It will tell you like which part of the code it changed. So that's
pretty useful.
00:41:50:25 - 00:42:14:25
Jens
And the second use case I really like this. So you create your RFC, you publish it to gets up like
a markdown. You create a pull request so people can comment. You let them comment, and
then you take the URL with the comments and you tell, you tell the AI, hey, here's a, here's
some comments, some feedback.
00:42:14:28 - 00:42:37:18
Jens
Apply the feedback to the RFC so you can have AI read the comments and apply them. And
then you can review. Okay. How would it look like like, do I like this? I mean you don't have to
accept it right away. You can just iterate on it. And yeah, I find it very useful. Also, some other
things I did is in cursor you can index websites and documents.
00:42:37:21 - 00:43:03:19
Jens
So for example I indexed the the documentation of WunderGraph I indexed the GraphQL
specification and some other websites. And then let's say you want to work with GraphQL or
write an RFC about GraphQL or something. You can you can look at these documents. For
example, there's a there's a working group, the GraphQL composites schema working group.