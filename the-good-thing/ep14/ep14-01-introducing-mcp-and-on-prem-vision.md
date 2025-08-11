---
title: Introducing MCP and On-Prem Vision
slug: ep14-01-introducing-mcp-and-on-prem-vision
series: The Good Thing
episode: 14
chunk: 1
participants:
- Stefan
- Jens
- Dustin
segment: Introduction, MCP overview, and on-prem focus
timecode: 00:00:00 - 00:05:15
start_time: 00:00:00
end_time: 00:05:15
speakers:
- Stefan
- Jens
- Dustin
topics:
- MCP introduction
- On-premise solutions
- Easter weekend recording
- AI integration
- Cosmo vision
- Episode format
tags:
- mcp
- on-premise
- ai-integration
- cosmo
- episode-intro
- product-demo
topic_tags:
- mcp
- on-premise
- ai-integration
- cosmo
- episode-intro
- product-demo
entities:
- Stefan Avram
- Jens Neuse
- Dustin
- The Good Thing
- MCP
- Cosmo
- WunderGraph
mentions:
- Easter weekend
- recording schedule
- AI MCP integration
- product demo
- co-founder introduction
- live format
summary: Stefan introduces episode 14, explaining they're recording instead of going
  live due to Easter weekend. He introduces the topic of MCP (Model Context Protocol)
  and on-premise solutions, setting up for a demo with co-founder Dustin joining the
  discussion.
---
Episode 14
00:00:00:00 - 00:00:41:06
Stefan
And. Well, I know, I'm just kidding. Ladies and gentlemen, welcome back to another episode of
The Good Thing. This time, we are actually not live. We're recording this because, tomorrow,
when we usually record is Easter weekend. So tomorrow is Good Friday, and then Easter
Monday, the following Monday. And, some of us are celebrating. For those that are celebrating, I
hope you enjoy a great Easter weekend with your family.
00:00:41:09 - 00:01:01:06
Stefan
For those that do have the day off, maybe watch this episode while you're hanging out with the
family. It would be great, but we didn't want to miss our routine. Every Friday at 9 a.m., eastern
time at 3 p.m. Central European time is when the good thing goes live. And we didn't want to
miss that time because we have a really exciting I guess we have had a really exciting couple of
weeks.
00:01:01:06 - 00:01:20:17
Stefan
And so today it's a little bit of an improv session. We didn't have a cool topic to talk about other
than what we've been building. And so today we invited Dustin, our co-founder and CTO.
Obviously, you see, my co-host Jens always is joining me on today. And today we're going to
talk a lot about what we've been building, especially around with AI MCP, and we even have a
small demo for you guys.
00:01:20:17 - 00:01:34:03
Stefan
So hopefully you enjoyed this format just as much as you enjoy the live one. But we wanted to
keep the consistency. Feel free to add comments to the video though to let us know what you
guys thought about it, but yeah, Jens. How are you doing today? Doing good.
00:01:34:06 - 00:01:45:24
Jens
Yeah, I just realized, you know, this is something. It hurts my eyes, but can you make a capital F
for co-founder in your name?
00:01:45:27 - 00:01:56:12
Stefan
I actually can. Yeah, I can do that live. Hold up. Edit name. One sec guys. How do you know you
work with developers is when they are anal about the small details I like it.
00:01:56:16 - 00:02:08:28
Jens
Not now. Now you know about Stefan's life as a co-founder. Like whenever there's, like a little
tiny thing, like your co-founder finds it and annoyts you about it.
00:02:09:00 - 00:02:15:24
Stefan
It works. I'm. I'm like a little co-founder, you know, with the little f, but I fixed it. Are you are you
happy now? Are we good?
00:02:15:27 - 00:02:20:11
Jens
Yeah, it's it's awesome. And, Dustin, you've been busy.
00:02:20:13 - 00:02:24:11
Dustin
Is my background Okay.
00:02:24:13 - 00:02:27:12
Stefan
Yeah. It could be better.
00:02:27:14 - 00:02:45:24
Jens
It's fine. Okay. Dustin, you've been busy. Yeah. So we have built, some stuff, and we want to.
Yeah. What what are we. What are we doing? What are we helping people with?
00:02:45:27 - 00:03:00:01
Stefan
Well. It's interesting, I'm not going to say, Dustin, from your point of view, what have you you've
been working over these past couple of weeks, and you can keep it technical, and then we'll
strip out the non-technical stuff for our non-technical viewers. But what have you been working
on these last couple of weeks?
00:03:00:03 - 00:03:31:19
Dustin
I think if you look closely or you do not even have to closely follow the tech news, but I think
your experience, like the huge hype around MCP and everyone wants to provide their own MCP
either either from your own SaaS product or from your local services. Everyone wants to provide
MCP services, so they are so that, I modeled AI modeled LLMS can connect against that and
enrich their context to do more things than they could do before.
00:03:31:22 - 00:04:05:24
Dustin
Well. And yeah, and what I have observed a lot is that everyone is doing that, SaaS provider,
super base, etc.. But nobody is really focusing on, the people who actually running software on
their own on an on premise and wouldn't be, wouldn't be awesome if you if you would have an
already existing API landscape. Let's say you're using cosmo or any other GraphQL provider,
and you could easily just expose this data to bots in a secure way.
00:04:05:26 - 00:04:42:06
Dustin
Export this data to an LLM model to have to automate your workflows like building apps. Yeah.
Accessing the data, building reports, building presentations, without any without writing any line
of code. And yeah, so we analyzed the market. We figured out that actually, what we have
already with cosmo is like everything you need to build this scalable, secure, and centralized
MCP gateway to provide this to our customers.
00:04:42:09 - 00:05:15:13
Dustin
And, so what we have built in the last seven, I would say almost 14 days, is to build like a first
class integration with MCP. So it allows you to implement implement what what in the graphql
space is trusted document persistent operation. It allows you to expose those operations
through MCP. And then you can easily connect it to your AI tools like Cursor, Claude desktop,
open AI, or other agentic frameworks to, to automate the workflows.
00:05:15:16 - 00:05:15:24
Dustin
Yeah.