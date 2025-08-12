---
title: AI-First Strategy and Customer Expectations
slug: ep19-12-ai-first-strategy-and-customer-expectations
series: The Good Thing
episode: 19
chunk: 12
participants:
  - Stefan
  - Robert Farr
  - Jens
segment: AI Strategy and Enterprise Adoption
timecode: 00:58:01 – 01:03:09
start_time: 00:58:01
end_time: 01:03:09
speakers:
  - Stefan
  - Robert Farr
  - Jens
topics:
  - AI-first strategy implementation at Procore
  - Enterprise AI impact and transformation
  - Customer reactions to AI initiatives
  - Internal tool development with AI
tags:
  - ai
  - startup
  - api-design
  - cosmo-router
  - go
  - graphql
  - llm
  - mcp
  - rest
topic_tags:
  - ai-first-strategy
  - procore
  - enterprise-ai
  - customer-expectations
  - internal-tools
  - ai-transformation
entities:
  - Procore
  - Robert Farr
  - Stefan Avram
  - Jens Neuse
mentions:
  - Procore's AI-first approach
  - Enterprise AI transformation
  - Customer feedback on AI features
  - Internal AI tool development
summary: Robert discusses Procore's AI-first strategy implementation, exploring enterprise
  AI impact, customer reactions to AI initiatives, and the development of internal
  AI-powered tools.
---

00:58:01:19 - 00:58:06:06
Jens
This is super interesting because what you're saying is.
00:58:06:09 - 00:58:08:19
Robert Farr
You you.
00:58:08:22 - 00:58:46:01
Jens
You provide an approach how to develop an agent against a graph. So if I can reiterate, you run
the router locally, you switch on the MCP gateway, you you allow on the MCP gateway, you
allow to run arbitrary queries, and then you instruct a model, for example, using cursor. I guess
you instruct the model to perform a certain task, and then you observe what kind of operations
will it do to accomplish the task.
00:58:46:04 - 00:59:12:05
Jens
Maybe we can even build a feature around that and help you capture that in like a session or
something. And then you can say, okay, here's what the, LLM tried to accomplish. Here's the
queries it made. And we can now package up these queries as an MCP tool. And then in
production, the the model will not have it much easier because now it doesn't have to explore
the schema.
00:59:12:05 - 00:59:33:21
Jens
You can precisely describe each tool and how it can help achieve the task, but also from a
security perspective in production, you might not want to expose the the whole graph because it
can, it can it can be confused by a response or something that it calls the wrong tool or
something. So I think that's that's very interesting.
00:59:33:21 - 00:59:49:12
Jens
And Stefan, this is something we should definitely look into how we can leverage our MCP
tooling in in dev mode to help someone develop an agent that is it's interesting.
00:59:49:15 - 00:59:51:05
Robert Farr
Yeah, we.
00:59:51:05 - 01:00:11:20
Stefan
Are a little bit almost at time. But I do want to ask two follow one more two questions actually.
Well, one, your customers are typically, you know, like contractors and people building things.
What is their take? Because what we've heard from the past from you is, you know, you guys
are very customer focused, listening to the customer voice.
01:00:11:20 - 01:00:25:08
Stefan
You're building for the people that are using your product. What is their take on AI? Are they
going to be late adopters to it, or are you guys adopting AI to make yourselves more efficient for
them? But how are they taking this AI boom.
01:00:25:11 - 01:00:48:06
Robert Farr
I'm, I mean, I think it, you know, it probably depends. So we have a range of customers, right?
From very large enterprises down to, you know, small mom and pop shops. So, you know,
depending on the customer, right? Like their, their approach, their I think, you know, at one end,
our customers are asking us, hey, what's your plan?
01:00:48:06 - 01:01:09:11
Robert Farr
Right. What are you doing? And so they they are, you know, they're kind of going through the
same thing we're going through, right? Is all the tools they use to do their job now, like, you
know, AI's coming to bear. You know, it's changing the way I record meetings, take notes,
provide communication summaries. Right. All those things are changing, and they're looking at
us in the same way.
01:01:09:11 - 01:01:32:25
Robert Farr
Right. We're just one of the tools they use to do their job. And how is how is AI going to drive?
You know, better efficiencies in their workflows. So we we get a lot of that. I think, you know, as
you get to the smaller ones, they're looking for just, you know, their, their understanding of AI
might really be just through the lens of the application experience they have.
01:01:32:26 - 01:01:48:16
Robert Farr
Right. So it's it's more of, you know, was it intuitive? You know, I kind of say like, you know,
they're your smaller customers are you know, you got to Google search, right? And you type
something. And every once in awhile Gemini shows you the AI summary. That's probably a
delighter in their world, if we get that right.
01:01:48:19 - 01:02:07:19
Robert Farr
You know, we're, we're kind of adding into their workflow. But where your bigger, more
sophisticated enterprise customers who are also API consumers, maybe, you know, want to
offer their own agents, right? Or leverage their own LLMs against our software stack. They're
very interested in what we're doing there.
01:02:07:22 - 01:02:27:17
Stefan
You know. Well said. And then my last question is, you guys are pretty, I would say tech forward,
you know, for being a public company. You guys are very like on the edge. You're adopting new
technologies, things like that. With your opinion. Where do you see this AI boom going with
Procore? So we talked a little bit about the AI agents, the things like that.
01:02:27:17 - 01:02:34:14
Stefan
But what kind of tooling have you guys adopted to stay on that cutting edge?
01:02:34:16 - 01:03:09:16
Robert Farr
Well, it's you know, I'd say pro core is, very forward thinking there. I mean, we're we're kind of all
in, so we're looking at AI from every aspect. You know, so all of our internal tooling, we're
looking at how AI is going to make us better. So, you know, whether that's atlassian, you know,
Jira or GitHub or, you know, you name it, but we're also then looking at how we're going to be,
you know, how do we apply AI to the the solutions that we build.