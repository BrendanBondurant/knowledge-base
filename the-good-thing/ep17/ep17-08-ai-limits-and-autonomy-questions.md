---
type: podcast-chunk
title: AI Limits and Autonomy Questions
slug: ep17-08-ai-limits-and-autonomy-questions
series: The Good Thing
episode: 17
chunk: 8
segment: Future AI autonomy and current limitations
timecode: 00:34:58 – 00:39:24
start_time: 00:34:58
end_time: 00:39:24
speakers:
  - Stefan
  - Jens
topics:
  - AI Autonomy
  - AI Limitations
  - Autonomous Systems
  - Future Potential
tags:
  - ai
  - go
  - llm
  - mcp
entities:
  - Iron Man
  - Jarvis
  - Ultron
  - Marvel Avengers
  - Tony Stark
  - LLMs
  - MCP
summary: Stefan questions whether AI will eventually become fully autonomous like
  the Iron Man villain Ultron, able to solve problems and work independently without
  human oversight. Jens acknowledges current LLM agents can handle complex tasks through
  tools like MCP but questions their ability to operate sustainably without human
  motivation and direction, suggesting current AI lacks the intrinsic drive needed
  for true autonomy.
---

00:34:58:06 - 00:35:20:09
Stefan
But you go back to the question like I'm also with you. I think AI is going to empower developers.
I not yet. I don't see a world where software is just being built by AI, but could it happen? Do you
think sometime in the future that, you know, just things are being built with AI and that there's no
like the way I envision is, have you ever seen Iron Man?
00:35:20:12 - 00:35:30:22
Stefan
What was the name of that AI villain that he created? There was a whole, Marvel Avengers on. I
think it was the second one.
00:35:30:25 - 00:35:35:05
Jens
So I know Jarvis, but that's not what you're looking for, right?
00:35:35:07 - 00:35:52:16
Stefan
No, Jarvis is the good one. Which which could be amazing. But there was the one that was so
smart and so sentinel that it ended up being bad, and it hated Tony Stark and I forgot the name
of it. I'll post that later in the comments. But with AI, do you ever see a future where, like, it's
kind of like its own thing?
00:35:52:16 - 00:36:03:10
Stefan
It solves problems and it works and it just does its own thing without humans like we've built it.
And at this point, sustainable.
00:36:03:12 - 00:36:34:29
Jens
So theres probably people smarter than me. And they have more knowledge about what's
what's going on in the AI market. But from, from my perspective, where we currently are at is,
we have agents like LLMS, we we prompt them something. We can give them tools, for
example through MCP. And then they can do like more complex tasks and yeah, the the results
are, are okay, like some tasks they are really good at.
00:36:35:02 - 00:37:03:03
Jens
And now there's like a new protocol, agent to agent. So instead of one agent doing like a super
complex task where it would get stuck, we divide the task into smaller pieces. And then agents
can, can essentially call tools. And these tools are other agents. So now we have agents
collaborating with agents on like more complex problems.
00:37:03:06 - 00:37:31:00
Jens
I, I don't think this is intelligence. It's still LLMS. It's still each agent does a task and it can predict
something, like then the next token and it can I mean, you can train these models further and
further. It will not be intelligence, but it will be extremely capable. We can automate it and it will
be able to do things that today humans do.
00:37:31:07 - 00:38:02:06
Jens
It will look very intelligent, although it's not. And so coming to your question Will, will that's AI will
replace how we do software or something. I'm not sure in the in the current form, I think what is
what is currently missing is like motivation, like, what you don't see in LLMs is they are not really
motivated in doing anything.
00:38:02:09 - 00:38:39:23
Jens
For example, when I did some, some experiments with, with cursor, like one, one workflow that
is quite, quite useful when you work with LLMs is you write a test and you ask cursor to make
the test go pass. And the stupid thing is that cursor doesn't really care if your code is right and it
it doesn't know exactly what, what does it mean that code is right, or it also doesn't care about
your business, or that this is scalable or whatever.
00:38:39:23 - 00:39:24:07
Jens
It's just make it. Yeah. You you asked to make the test pass. So what can happen quite likely is
that the implementation looks at the test and it's it somehow implements the logic in a way that,
yeah, it makes the test pass. But this is not good architecture or something. And now you have,
you have a bigger problem in, in large organizations I would say because imagine you have a
big org, you have a thousand developers, and they all work, work on, on several projects and
they all want to achieve something.