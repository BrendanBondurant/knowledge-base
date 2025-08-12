---
title: Exposing Secure Workflows to LLMs
slug: ep14-08-exposing-secure-workflows-to-llms
series: The Good Thing
episode: 14
chunk: 8
participants:
- Stefan
- Jens
- Dustin
segment: Workflow Design and Security for AI Integration
timecode: 00:31:08 – 00:34:58
start_time: 00:31:08
end_time: 00:34:58
speakers:
- Jens
topics:
- Problems with exposing raw APIs to LLMs
- Context limitations with large GraphQL schemas
- Trusted documents for workflow control
- Dream query workflow example
- Tool interaction storytelling for LLMs
- Democratizing MCP access through no-code solutions
tags:
- trusted-documents
- dream-query-workflow
topic_tags:
- trusted-documents
- dream-query-workflow
entities:
- GraphQL API
- REST API
- Trusted documents
- Dream query workflow
- Cosmo
- Visual query builder
- LLM
mentions:
- LinkedIn discussions about MCP
- schema size exceeding context limits
- human vs model interaction patterns
- multi-step workflow design
- tool description and interaction
- GraphQL query writing accessibility
- prompt-to-GraphQL conversion
- no-code MCP server creation
summary: Jens explains the risks of exposing raw APIs to LLMs, including context overflow
  with large schemas and unfocused responses. He advocates for trusted documents to
  create secure, workflow-oriented tools that guide LLMs through specific tasks like
  the dream query workflow. He envisions democratizing MCP access through visual query
  builders and no-code solutions for non-technical users.
---

00:31:08:12 - 00:31:41:24
Jens
So one topic we talked about on on LinkedIn and other discussions about MCP is, if you simply
expose a GraphQL API or a Rest API or any API or a database through MCP, what is very likely
to happen is that you you give AI a task. You know, let's let's say the LLM model has a tool to
get the whole GraphQL schema and then a tool to make queries and mutations.
00:31:41:27 - 00:32:17:25
Jens
And now you type in the prompt to do something. Will it actually understand to look into the
GraphQL schema to then parse the GraphQL schema, which it can be so large that it actually
goes beyond the context? And then will it be busy figuring out your schema, or will it actually
answer your prompt? And so the the the problem we're we're solving here is if we can persist
some documents or create trusted documents, persisted queries, and limit what we want to
expose.
00:32:17:28 - 00:32:41:11
Jens
First of all, we we make it technically much easier for the model to interact with our with our
tools. And the second thing is, you don't just want to expose GraphQL or Rest APIs through
MCP. You want to carefully think about what are you exposing and what are the workflows you
want to enable the model to do.
00:32:41:11 - 00:33:06:27
Jens
Because a model is not just it's not a human that clicks on the user, that loads the user and then
loads the posts and then adds a comment to the post. A model is an LLM that that does a task.
For example, 111 workflow we have in cosmos, we have a query that's not working and we want
to go through a workflow to change the schema so that the query works.
00:33:06:27 - 00:33:30:16
Jens
We call this the dream query workflow. So that's the workflow of like many many steps that the
model can go through to accomplish the task. So if you model your MCP tools you need to think
about these workflows. These like what what should the model do. And so what you can do with
like exposing operations by writing the query, each query, you can give it like a description.
00:33:30:23 - 00:33:53:24
Jens
And you can also tell the story of okay, here's here's a tool to do this. It gives you an employee.
And then you can also call another tool to do something with the employee. So your your
explaining how the different tools interact. And then that enables the LLM to, to to accomplish
like a real task. So yeah I think that's that's very important.
00:33:53:27 - 00:34:24:11
Jens
The, the other parts I think Dustin mentioned the most important things. One other comment is I
would say, we by by by simplifying the creation of an MCP server to write a GraphQL query, we
we actually give a lot more people access to this capability. You don't need to be a programmer
to write the GraphQL query, because we also offer it in the very near future.
00:34:24:11 - 00:34:58:26
Jens
Tools to create, a GraphQL query with a visual query builder or even prompt to GraphQL query.
So that means in the in the future, there will be a no-code solution or a low-code solution. So
that's everybody with a super graph without technical knowledge can create a secure MCP
server for their particular use case. And so in this sense, we're also democratizing access to
this, to this capability.