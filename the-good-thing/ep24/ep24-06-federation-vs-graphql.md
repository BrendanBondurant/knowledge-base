
---
title: Federation vs GraphQL Philosophy and Team Size
slug: ep24-06-federation-vs-graphql
series: The Good Thing
episode: 24
chunk: 6
participants:
  - Stefan
  - Jens
segment: Technology Philosophy and Development Approach
timecode: 00:28:16:08 – 00:33:06:05
start_time: 00:28:16:08
end_time: 00:33:06:05
speakers:
  - Stefan
  - Jens
topics:
  - Don't marry the technology philosophy
  - GraphQL Federation challenges
  - Blockchain analogy for solution-seeking problems
  - Focus on problems vs solutions
  - GraphQL over HTTP batching complexities
  - Navy SEALs team size principles
  - Governance and foundation overhead
tags:
  - technology-philosophy
  - problem-focus
  - solution-obsession
  - blockchain-analogy
  - team-size
  - governance
  - graphql-http
entities:
  - Stefan Avram
  - Jens Neuse
  - Dustin Goodwin
  - Navy SEALs
  - GraphQL Foundation
  - Apollo
  - Nithin
mentions:
  - don't marry the tech evolution
  - blockchain looking for problems
  - bank vs blockchain security
  - be obsessed with problems not solutions
  - GraphQL over HTTP batching API
  - entity request hacks
  - specification adoption lag
  - Navy SEALs team size limits
  - eight person maximum teams
  - too many cooks in kitchen
  - governance board problems
summary: |
  Stefan observes Jens's evolution toward not being married to technology, comparing GraphQL Federation's approach to blockchain's solution-seeking behavior. Jens advocates for being obsessed with problems rather than solutions, critiquing the GraphQL over HTTP batching approach. Stefan applies Navy SEALs team size principles to argue that large governance boards hinder effective development.
---

00:28:16:08 - 00:28:38:21
Stefan
Well Said I would like to say that I mean, the non-technical person always said that the big issue
with GraphQL Federation's you had to learn GraphQL. And then the big issue with GraphQL
was you had to use GraphQL. I think you're spot on. Like I don't get this. And I think also you
guys don't know Jens as long as I've known it, but there's an evolution that I've seen Jens go
through.
00:28:38:21 - 00:28:58:09
Stefan
I have also seen Dustin go through it, but Jens always says now he's like, don't get married to
the tech, don't get married to the tech. And I really think this composite working group, they're
married to the technology. Like you don't need to shove GraphQL down to finish every solution
or if for it to be even just the solution.
00:28:58:12 - 00:29:19:10
Stefan
It sometimes kind of feels to me like blockchain. Do you remember like blockchain was looking
for a problem and people were like, oh, we can solve finance, things with blockchain. And I was
like, can I just use a bank? Like, I feel like it solves the problem if everything's all good and if
somebody hacked my account, I can call the bank and tell them somebody hacks my blockchain
account, I can't tell anybody.
00:29:19:10 - 00:29:21:28
Stefan
And so I think you're spot on.
00:29:22:00 - 00:29:46:28
Jens
You know what you said? Don't be married to the tech. I would somehow generify this a little bit.
Don't be married to the solution. Like, be be married to the to the to the problem. To the to the
customer. And, yeah, maybe not married to the customer, but you know what? You know what I
mean?
00:29:47:01 - 00:30:19:15
Jens
Like, be obsessed about the problem, not be so much obsessed about the solution. And one
particular example for this is, like the what the post says on the, on the article from Curtis that
the GraphQL like there's a working group and for in the GraphQL over Http spec, they now want
to create like a new, a new batching API that allows you to, to batch GraphQL requests.
00:30:19:17 - 00:30:50:26
Jens
And the problem is that, by default, the the hack that Apollo is, is using to to make these entity
requests to load entities with this weird like any, underscore any syntax. Yeah. This hack it it
requires or it it's somehow like a hack to solve, batching. And if you want to remove that hack,
you have to somehow do batching in, in another way, in another layer.
00:30:50:29 - 00:31:19:22
Jens
And they are now looking at adding this to the GraphQL over HTTP spec. But then you have
multiple new problems. You first of all, you need to get that spec in. And like sometimes it can
take forever to get this spec signed off. And once you have that in, then you need to get all
frameworks, all subgraphs, all GraphQL service to adopt that new specification, which allows, it
will also have have some lag.
00:31:19:24 - 00:31:31:07
Jens
So, I don't know, like how about just we take the subgraph SDL, we compile it into proto, you
run gRPC, we're done.
00:31:31:09 - 00:31:53:15
Stefan
And that's it. That's it folks. One last note that I will say on this though, the whole thing about,
like the working group and having too many cooks in the kitchen, if you've ever heard of like the
Navy Seals, like they have very strict team sizes, there's two, four, six and a max team size of
eight. That's the max size that they can ever go on a mission is eight Navy Seals.
00:31:53:18 - 00:32:14:24
Stefan
I still think the same way in startups. If you really want to build something, for example, like this
federation spec, and you want to really get this down, you need a maximum of eight people.
When you have this whole governance board and this foundation behind it, I think it takes too
long. I really think that having so many people are too many cooks in the kitchen can be really
detrimental to even driving something forward.
00:32:14:26 - 00:32:17:00
Stefan
Anything else you want to add to that before we jump to the next.
00:32:17:00 - 00:32:44:12
Jens
Oh, I, I agree with this because, I think, like whenever we try to build something big and
something, something very hard, something new, I think it work best when just one single
person worked on it for three months and then said, I'm done. I think that was like the best
approach. We had a funny post from Nithin Be Married to the problem is this life advice.
00:32:44:14 - 00:32:47:20
Jens
This is how you choose.
00:32:47:22 - 00:32:50:17
Stefan
I don't know anything. You're the problem. So I don't know if you can marry yourself.
00:32:50:17 - 00:33:06:05
Jens
So. But you know, like like from a from a technical point of view, from a mathematical point of
view, if you're married, you definitely have at least one problem in your life. Absolutely.