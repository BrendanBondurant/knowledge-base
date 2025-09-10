---
title: Fundamentals vs Vibe Coding Security Mindset
slug: ep13-09-fundamentals-vibe-vs-secure
series: The Good Thing
episode: 13
chunk: 9
segment: Programming Fundamentals vs AI-Generated Code
timecode: 00:32:18 – 00:36:09
start_time: 00:32:18
end_time: 00:36:09
speakers:
  - Stefan
  - Jens
topics:
  - Programming Fundamentals
  - Vibe Coding Limitations
  - Network Troubleshooting
  - SSH and HTTPS Ports
tags:
  - mcp
  - ai
  - computer-science
  - go
  - rest
entities:
  - SSH
  - GitHub
  - Git
  - HTTP/HTTPS
  - TLS
  - Port 22
  - Port 443
summary: Jens reflects on learning programming in the pre-AI era and the importance
  of fundamentals. He shares a real-time example of a colleague unable to clone repositories
  from a hospital due to SSH port blocking, demonstrating how fundamental networking
  knowledge helps solve problems that vibe coders might struggle with.
---

00:32:18:12 - 00:32:23:07
Stefan
What do you think?
00:32:23:10 - 00:32:56:17
Jens
I mean, I'm now, a few more than I don't know how many years, ten, 12, whatever. I guess doing
doing software and, I learned a, I learned coding in the pre vibe coding era. Yeah, it's I don't
know how you did it thing. Yeah. And we, we had to learn the, the, the fundamentals. And you
know, the funny thing is just, just today I had maybe maybe he's listening, but I, I for me this is
funny.
00:32:56:24 - 00:33:06:23
Jens
clone something.
So one of my colleagues, he said like, hey, I'm currently in the hospital and I want to I want to
00:33:07:10 - 00:33:11:04
Stefan
Can. Right. Because of GitHub. Oh, he can't clone it cause in the hospital.
00:33:11:04 - 00:33:27:10
Jens
Right. So he wants to clone the repo, and he was like, yeah, I get this timeout error. SSH is not
working. And you know, like so you're you're also like a vibe coder. So ssh it's not working.
What's the problem. What is the hospital doing then?
00:33:27:12 - 00:33:38:28
Stefan
I think they're blocking from GitHub because I know in hospitals you can't like bring down repos
for protection from the hospitals. Am I right there?
00:33:39:00 - 00:33:40:18
Jens
Kinda like they don't want to.
00:33:40:18 - 00:33:44:07
Stefan
They don't want you to bring down some malicious repo into. They won't in there.
00:33:44:12 - 00:33:47:20
Jens
What is what is port 22?
00:33:48:20 - 00:33:52:08
Stefan
I don't know if it's like a port like computer.
00:33:52:10 - 00:34:25:20
Jens
It's it's the SSH port. Okay, so the hospital is for whatever reason, they are they are just
allowing, like port 80, probably. Maybe not even 80, but 443. So, TLS and they obviously block
for 22 because I don't know, maybe it's, it's malicious or whatever. And yeah. So he cannot
clone repositories and because his git is using SSH.
00:34:25:21 - 00:34:30:17
Jens
So how could you how could you solve the problem.
00:34:30:19 - 00:34:33:22
Stefan
Can you use a different port.
00:34:33:25 - 00:35:09:24
Jens
That's. Yeah. So you could use git over http. For example https them and that should be port
443. That should work. Or you could you could create a proxy proxy. SSH. Over, over. Over TLS
that that could also be a possibility. But yeah, it's it's just, you know, and these are the
fundamental, like a vibe coder would be like, oh, I don't know, like my internet working or
whatever, but yeah, it's it's,
00:35:09:27 - 00:35:16:18
Stefan
No, it's true. Like, you know, the ports like that in a vibe coder wouldnt be able to know exactly
what to do. That's interesting.
00:35:16:20 - 00:35:39:10
Jens
But, you know, you're in a hospital and you get the timeout when doing ssh. It it's kind of very
obvious that it must be something with, with ports or a firewall or something. And now you need
to see, okay, which, which ports are open and how can I can I tell my client to use another port
or whatever.
00:35:39:10 - 00:35:41:15
Jens
Like how how can. Yeah.
00:35:41:18 - 00:35:47:21
Stefan
different port?
It's kind of funny though. I wonder, did he manage to fix it though once you told them to use a
00:35:47:23 - 00:35:53:06
Jens
I don't know, he he he said he try some stuff.
00:35:53:08 - 00:36:09:05
Stefan
no. But you got a good point there and then I mean yeah we're opening it up into a huge space
like the S in MCP stands for security. I see it's going to get it's going to get interesting these next
couple months these next couple of years. I'm excited for that. And then let's transition to the
next topic though.