---
title: AI Impact and Database Usage
slug: ep26-14-ai-impact-and-database-usage
series: The Good Thing
episode: 26
chunk: 14
segment: AI's Impact on Database Infrastructure
timecode: 01:05:02:27 – 01:09:22:10
start_time: 01:05:02:27
end_time: 01:09:22:10
speakers:
  - Stefan
  - Jens
  - Sam Lambert
topics:
  - AI Impact on Databases
  - Data Generation for Training
  - Cursor Integration
  - Development Tooling
tags:
  - ai
  - database
  - go
  - mcp
  - rest
  - startup
entities:
  - AI
  - Cursor
  - PlanetScale
  - GitHub
  - Facebook
  - MCP
summary: Final technical discussion covering the aesthetic satisfaction of large-scale
  infrastructure orchestration and AI's transformative impact on database usage patterns,
  including PlanetScale's relationship with Cursor and the new constraints AI applications
  create.
---

01:05:02:27 - 01:05:21:13
Sam
It's just so fucking cool. Like it just was so nerdy. Like you just go, wow, like, you know what I
mean? It's just this orchestration of, yeah, I've always just love this all, seeing all these nodes
kind of, like, dance together, come together and do one thing. It's just amazing to me. And I just
beautiful. And I just love it so much.
01:05:21:15 - 01:05:41:20
Sam
It just feels so satisfying. Like, same with GitHub. You just get hooked too. You get, you know,
it's fun. Is living dangerously, deploying a website that I remember the first time, like when I
when I was onboarding at Facebook. Like deploying like pushing code that was about to get
deployed to Facebook for millions or billions of users. And you're just like, it just feels so cool.
01:05:41:20 - 01:05:55:21
Sam
It feels so meaningful. It's hard to go back and and and do anything differently. I'm glad other
people do. But for me, some for me, it's all theory until it works at extreme scale.
01:05:55:24 - 01:06:04:11
Jens
Do you have like a cool visualization layer or something that where you can where you can see,
like all the planet scale nodes across the globe or something?
01:06:04:14 - 01:06:36:10
Sam
No we don't. This is the thing we're very like. We're too utilitarian for that stuff. We don't do any
of the flashy bits. We just make it work. I mean, our UI is very beautiful. Jason and the team
have done a phenomenal job of making it look lovely, and it looks really nice, but it very simple.
It it kind of I don't know, it doesn't make you an even when you the you get tempted sometimes
like we could make some really cool visualizations show everyone all of these nodes all
orchestrating together, and then we just go back to doing other things.
01:06:36:17 - 01:06:46:12
Sam
You know, it's really hard to to fight the temptation to make all that fancy stuff. But no, you really
just see it in a terminal or a graph or something and, you know, it's cool.
01:06:46:15 - 01:07:04:22
Jens
Maybe if you want to do some cool marketing stunt, you know, there's from I think GitHub,
there's like, this animation they have like a globe and you can see all the, the commits,
whatever. Yeah. Maybe you could do like a globe where, where I could see all the planet scale
nodes coming up and down like green and red then.
01:07:04:23 - 01:07:05:08
Jens
Yeah.
01:07:05:11 - 01:07:32:24
Sam
I have so I actually started messing around with, like I sort of like dots that represent each one
of our nodes. And then as they flip, they change colors. And so I may do something similar to
that. It depends where the thing is from is people when you put stats like, like we announced
large customers migrating. And I don't want people to be able to correlate change with that with
those like people are very sensitive about data and the scale of what they do.
01:07:32:26 - 01:07:50:20
Sam
We just have to be very careful because, you know, what we put out there. But I do try and think
of ways we can represent that. And sometimes, you know, we've got one customer that's going
to talk publicly about the scale. They run out on plant scale. And I think some of those numbers,
well, will really impress people.
01:07:50:22 - 01:08:07:25
Stefan
And what I said and then we got a comment from somebody in the audience. But the last one
that I wanted to kind of end on. So we are a little bit over. But Sam, like, we can't end the
episode without talking about AI. And so how do you see AI interacting with databases? Has
MCP change how plants go conducts its day to day?
01:08:07:25 - 01:08:14:12
Stefan
databases?
Have you guys adopted tools like cursor windsurf or things like that? How do you just see AI in
01:08:14:14 - 01:08:41:11
Sam
It's lovely. I mean, there's the A's had an effect on databases in many ways. One way is that,
you know, there's there's this new type of database which is not really for production usage, but
they're like fit for AI. You know, they spin up quickly in serverless and all this sort of stuff. And
that's kind of interesting. It's not really what we do, but it's made it's out a different set of
constraints for what AI needs.
01:08:41:13 - 01:08:59:13
Sam
The impact it's had on us is large companies creating lots of data that they need for AI and
wanting to keep hold of that data as well as AI. Companies know cursor is a customer of ours,
and we use cursor. So it's really fun to like be in the loop and there's some new features that
shipping that we have access to that we're integrating with.
01:08:59:13 - 01:09:22:10
Sam
And that's extremely cool itself. Like there's just you know, it's it's it's it's impacting databases in
so many ways. One of them being that we're using a ton of AI to actually write the software that
we use. And that's fun. And it's creating new usage patterns and new things at scale. And that's
extremely fun. Yeah, it's just brought more load, more demand, more concurrency.