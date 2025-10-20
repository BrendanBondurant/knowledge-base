---
type: podcast-chunk
title: Vision vs Feedback and the Power of Caring
slug: ep04-11-vision-feedback-caring
series: The Good Thing
episode: 4
chunk: 12
segment: Vision vs Customer Feedback and the Power of Caring
timecode: 00:35:10 – 00:44:09
start_time: 00:35:10
end_time: 00:44:09
speakers:
  - Stefan
  - Jens
topics:
  - Cache Warmer Success Story
  - Customer Feedback
  - Vision vs Feedback
  - Caring and Passion
  - Team Culture
  - Founder Mindset
tags:
  - cache-warming
  - startup
  - founder
  - performance
  - query-planning
  - graphql-federation
  - cosmo
  - enterprise
entities:
  - WunderGraph
  - Cosmo
  - Super Bowl
  - Dustin
  - David
  - DeLeon
  - SpaceX
  - Tesla
  - Elon Musk
summary: Stefan and Jens continue discussing the cache warmer success story, then explore
  the balance between founder vision and customer feedback. Stefan shares personal stories
  about the power of caring in work, including a college restaurant job lesson and a passionate
  job candidate. They discuss how caring creates company superpowers and debate whether
  billion-dollar companies succeed through vision or customer feedback.
---

00:35:10:29 - 00:35:16:00
Stefan
No, it's fine, it's fine. I'm like, tracking in my head, like things to jump back on, but real quick.
00:35:16:01 - 00:35:18:19
Jens
Yeah, okay. Well, one thing I finished.
00:35:18:19 - 00:35:19:22
Stefan
Finished the monologue.
00:35:19:24 - 00:35:58:06
Jens
Yes. So you you ship something, and then there's this magic moment. It sometimes happens,
and and everybody loves it. It's like, okay, we built something. It's called cache warmer. So we
had a customer they are preparing for, a huge, huge, huge event where they expect Super
Bowl, but they expect insane amount of traffic and they weren't really afraid of can the can the
router sustain the load because they have a bunch of queries that take many seconds to to
plan, like grow planning and GraphQL Federation.
00:35:58:06 - 00:36:28:10
Jens
It's a it's a complex topic. Competitive products. It took them like 50s or longer to plan this
cruise. We were able to put it under 10s. But imagine you are you're in a big event, you scale
our traffic and you have to plan a query for 10s like completely unacceptable. And they tried to
build like custom scripts to to warm up the router before they send the production traffic.
00:36:28:10 - 00:36:55:10
Jens
And it didn't really work. And coming back to this magic moment, they come with the
requirement we build cache warmer. I think it took us a month or two. It was a big effort. We can
talk later about what cache warmer is. And then they did like a pre run with the smaller event
where they prepared everything and they send you a screenshot like you know they.
00:36:55:16 - 00:37:27:19
Jens
Yeah, it's so funny like you do all this work and then they say it's working one screenshot a tiny
screenshot and it shows like the squiggly lines like flaky between eight and 10s. And then
suddenly everything below one second and that's that's like, yeah, this is why we're doing it,
this, this kind of moment. And, that, that was such a great collaboration because, you know, we
didn't know it's such a big problem.
00:37:27:21 - 00:37:42:12
Jens
Like, obviously you you always have like, your backlog is full of stuff, but, yeah, we always try to
find stuff that is really impactful. And yeah, in this case this is the graph.
00:37:42:14 - 00:37:44:05
Stefan
Yeah. There we go.
00:37:44:07 - 00:38:20:29
Jens
So on the left we see like spiking. So this is the maximum time that it took routers to plan
querys. That's in seconds. And we see yeah something flaky between whatever four and 15, 16
seconds. And then suddenly you can see on on, Friday 24, you can see, full deployment of, of
Cosmo Cache, Warmer and, yeah, it seems like everything is below one second, which is
absolutely amazing.
00:38:21:01 - 00:38:45:19
Jens
And yeah, this is just, you know, we really love this collaboration because, we have a long term
vision where we want to go. But in the, in the, in the medium time, like, how can you be you
know, it's it's so easy to say like, hey, like, you know, some, some people in the GraphQL
community, they do this, they say, oh, we have the fastest router, we are the best, blah, blah,
blah.
00:38:45:19 - 00:39:09:00
Jens
We have the best quality. But yeah, but what what we are doing is we we listen, we figure out,
okay, how can we prepare for Super Bowl. We identify the problem. The problem is, is, query
planning time and then we figure out how to solve it. And it's not like, oh, yeah, cache warming,
like super easy.
00:39:09:00 - 00:39:37:17
Jens
No, it's it's a really hard problem because you have directives like skip includes. They can they
can dramatically change. The shape of a query. And then you have processes like normalization
and, and other things you have like inline arguments, all these kind of things. They make
caching query plans in graphical federation very very complex. We have a I have a rabbit in my
garden
00:39:37:19 - 00:39:38:27
Stefan
This is a.
00:39:38:28 - 00:40:09:17
Jens
Rabbit running around. It's it's funny. I don't know what it's doing, but. Okay. Yeah. All these
things, we we have a blog post on the topic on normalization. We will soon release another blog
post on on the cache warming. But yeah, back to the original point. This feedback loop
customer comes with the problem. You discuss it and then the close interaction we have like
weekly or bi weekly meetings with our customers, and then the screenshot.
00:40:09:19 - 00:40:11:06
Jens
That's why we do it.
00:40:11:08 - 00:40:32:08
Stefan
But so like my two points, while you were going on your little monologue. Yeah, look at that. You
need a water break. No, jokes aside, so, like, caring. And I want to tell two stories. One is we
recently got an application from a candidate for a position that we don't even have. Like, we
don't even have this position.
00:40:32:11 - 00:40:52:02
Stefan
But he went and he demonstrated, like, why he would be a good asset to the company. He
wrote this giant long email of the things that he would own, the things that he would create and
how passionate he is about it. And then he actually went and took a bunch of our videos and he
clip and he's like, this is how I envision you guys would do it.
00:40:52:08 - 00:41:05:27
Stefan
So we're not even hiring for like a content creator. But he got mine, and Jens attention to the
point that we were talking about him for two days, like, wow, like this type of passion and this
type of care and you can see that people, when they care about something, how much different
they are to work with.
00:41:05:27 - 00:41:23:20
Stefan
And when you care about something, it's what makes working at a company a superpower.
Because if the company truly cares about the problem that they're solving, you feel like you can
rely on them for anything. And one small antidote that I had is this was like a life lesson that,
like, completely changed my mind when I was in college.
00:41:23:22 - 00:41:38:16
Stefan
I just signed to play college soccer. I felt like a hot shot, you know, like I'm going to a school that
costs 90,000 a year, and I'm going for free. And, during the winter break, my mom was like, you
need to get a job. And I was like, mom, like, I'm going to school for free. She's like, you need to
get a job.
00:41:38:19 - 00:41:55:27
Stefan
So she gave me a job. I got a job in a restaurant for like two months. And I was like, oh, like,
why do I need a job? Like, I'm a college soccer player. I go to college for free, I'm a big shot.
And, they gave me a job as a, like a bar hand or like, like basically just helping out in the
restaurant cleaning stuff.
00:41:55:29 - 00:42:08:12
Stefan
And, one of the managers was like, hey, can I see you? And I was like, yeah. He goes, this plate
isn't really that clean. Neither is that one, like, what's going on? And I was like, oh, come on,
man. Like it's just to play it like, who cares? And he's like, let's go outside. And he pulls me to
the side.
00:42:08:12 - 00:42:24:12
Stefan
He's like, listen, I understand your college soccer player. I understand like, you know, this to you
is a small task, but he's like, I care about this. This to me is my college soccer. This to me is
being on the field. And he's like, I care. And he's like, I'm going to tell you something. And like,
maybe you'll listen to me.
00:42:24:12 - 00:42:42:23
Stefan
Maybe you don't. But I love this. This to me is my passion. And he's like, when somebody
comes in and they don't care. And that reflects badly on me. It hurts me. And he's like, for me,
what's most important is that how you do anything is how you do everything. So he's like,
hopefully that helps you as a lesson.
00:42:42:26 - 00:42:58:21
Stefan
And I remember that's smacked me in the face. I was like, Holy crap. Yeah, he's right. Like
something that I care about might be completely different from what he cares about. But that to
him was his college soccer. And it's the same thing that I see at Wunder Graph is that we hire
people that truly care about their whatever it is.
00:42:58:21 - 00:43:17:03
Stefan
You know, Dustin with his telemetry pipelines, David with composition is that they actually care
and they don't just put out crap is that they put out the best of their ability because they
genuinely care about the problem they solve. And so for me, that's what I like about Wunder
Graph. And then second, let's go back on the the customer feedback.
00:43:17:03 - 00:43:40:01
Stefan
So, DeLeon founders, fund guy, he said you can't ab way your your way to success like billion
dollar companies are started because somebody has a crazy vision and they're like a train.
They just go they're Elon Musk with SpaceX. He's like, I want to commercialize private space
travel. He didn't ask for feedback from customers. He just did it.
00:43:40:04 - 00:43:53:25
Stefan
Same thing with Tesla. Do you think that they kind of listen to the customers with the car like,
hey, can we fix this handle? Can we do this? Or was it just, I have a vision, I have the money
and we're going to execute. I'm not going to listen to everybody. Like how do you balance that
as a founder?
00:43:54:00 - 00:44:09:21
Stefan
Like how do you balance like the vision that we have for Wunder Graph, but also all the
feedback that we're getting constantly customers, because if we just listened all the time to the
customers, we would go this way when when the vision is we want to go that way.