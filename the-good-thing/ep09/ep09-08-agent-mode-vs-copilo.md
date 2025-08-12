---
title: Agent Mode Coding vs Autocompletion and Prompt-Based Tools
slug: ep09-08-agent-mode-vs-copilot
series: The Good Thing
episode: 9
chunk: 8
participants:
  - Jens
  - Cameron
segment: Vibe coding and development tools
timecode: 00:30:07:13 – 00:33:27:02
start_time: 00:30:07:13
end_time: 00:33:27:02
speakers:
  - Jens
  - Cameron
topics:
  - Vibe coding definition and approach
  - GitHub Copilot vs Cursor comparison
  - Agent mode vs autocompletion
  - Frontend development effectiveness
  - AI prompt engineering challenges
  - Context management in AI tools
tags:
  - github-copilot
  - agent-mode
  - ai
  - go
  - graphql
  - rest
topic_tags:
  - github-copilot
  - agent-mode
entities:
  - GitHub Copilot
  - Cursor
  - Next.js
  - React
  - Vue
mentions:
  - tab-tab-tab autocompletion
  - multi-file editing capabilities
  - frontend framework effectiveness
  - AI prompt autocomplete problems
  - context file selection
summary: Jens and Cameron compare different AI-assisted coding approaches, from GitHub
  Copilot's autocompletion to Cursor's agent mode. They discuss "vibe coding" effectiveness,
  particularly in frontend development, while highlighting challenges with AI prompt
  engineering and the importance of careful context management.
---

00:30:07:13 - 00:30:33:19
Cameron
Yeah, that's that's pretty much exactly what the verification is doing. Right now I'm not doing any
kind of actual linting on the query. I'm more just, ensuring that the, that, query it returns can be
parsed into AST, and then I'm validating that that AST is valid against the current schema.
However, you know, as with anything in this world, there's still a lot of experimentation to be
done around.
00:30:33:21 - 00:30:49:27
Cameron
And, you know, does it perform better when we add in a linter and feed that back? How does it
perform? And you know what what tweaks to this can we make to make it more accurate, more
performant and just overall better?
00:30:49:29 - 00:31:07:15
Jens
Yeah. Okay. Which which we can actually use as a transition to, to the topic of, of vibe coding
for those who don't know, like what what what do you consider vibe coding? Cameron.
00:31:07:17 - 00:31:24:23
Cameron
Whenever you're working with like something like cursor or any of those tools and you are just
really able to move quickly and it, you know, kind of saves saves time. And it's being actually
helpful. It's that makes sense.
00:31:24:26 - 00:31:50:02
Jens
Yeah. So, the way I would describe vibe coding or I kind of say like, coding with an agent or
coding an agent mode, like, you know, for a very long time, I was using, GitHub copilot. So that
is kind of the approach where you, you tab tab tab and it kind of gives you a better
autocompletion.
00:31:50:04 - 00:32:09:13
Jens
And then after a while with copilot, we had this new feature where we can we can mark some
code and then we can write a command to, to change this code. And now agent mode, it's it's
kind of completely different. You you tell it like, hey, here's a bunch of files. Here's I want to
here's what I want to do.
00:32:09:13 - 00:32:31:08
Jens
And it, it kind of changes all the files for you. And it makes all the, all the edits and, it's. Yeah, it's
an interesting approach. What what what is your experience so far? Like, where does it work?
Well, where does it not like what what what is it good at? What what what are the problems?
What have you observed.
00:32:31:10 - 00:32:56:15
Cameron
Yeah, so I have I heavily use cursor. I actually was not a big GitHub copilot user, believe it or
not. I have I've really liked cursor. However, I found that it works really well with front end work.
So with building out like, things in next or react,or Vue or any of those different front end
frameworks, and even on the back end it works.
00:32:56:18 - 00:33:27:02
Cameron
Okay. One of the big challenges, though, that I've found is actually when doing prompt
engineering and working with AI prompts, is that it'll try to autocomplete and try to autofill things
and AI prompting AI it's not at a point where it's super great yet. So I've just found that if you're
not careful with what files you allow it access to, it will mess up your prompts.