---
type: blog
title: The Impact of MCP and LLMs on Software Development - A Practical Example
slug: 2025-04-17-impact-mcp-llms-software-development-practical-example
series: WunderGraph Blog
date: 2025-04-17
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - LLM Development
  - Developer Productivity
  - API Tooling
  - Automation
tags:
  - graphql
  - graphql-federation
  - llm
  - mcp
  - developer-experience
  - automation
entities:
  - Model Context Protocol
  - LLMs
  - Cursor
  - WunderGraph
  - GraphQL Federation
  - API Tooling
summary: |
  Model Context Protocol (MCP) enables LLMs to complete complex development tasks like schema exploration, query generation, and router configuration in a single prompt. This practical example demonstrates how MCP transforms multi-step CLI workflows into streamlined, agent-friendly interactions, making development more efficient and accessible.
faqs:
  - q: What is Model Context Protocol (MCP) and how does it relate to LLMs?
    a: MCP is a protocol inspired by LSP (Language Server Protocol) that enables LLMs to interact with local developer tools via standard input/output. It allows tasks like schema exploration, query validation, and router configuration to be handled in a single prompt using lightweight, task-specific tools.
  - q: How does MCP improve developer workflows?
    a: MCP lets developers "one-shot" complex tasks like writing queries, updating schemas, or configuring routers without switching tools. It automates the same steps you'd perform manually with a CLI, turning multi-step workflows into single prompts inside your IDE or agent-based environment.
  - q: What is the dream query workflow?
    a: The dream query workflow lets you describe a query you wish worked—even if the schema doesn't yet support it. MCP then proposes schema changes to make the query valid, eliminating manual exploration and CLI steps.
  - q: How is MCP different from OpenAPI?
    a: MCP is designed for tool extensibility and stdio communication, not HTTP-based API documentation. Unlike OpenAPI, which models REST resources and operations, MCP exposes simple RPC-style tools that enable dynamic, task-oriented interactions suited for LLMs.
  - q: Is it safe to run an MCP server locally?
    a: Running MCP locally requires caution. It's similar in risk to running any local dev tool—safe when you trust the source. MCP doesn't open network ports, but if misused (especially over SSE or shared environments), it could allow unintended access or file modification.
  - q: Who should use MCP?
    a: MCP is for anyone who wants to automate development workflows with LLMs. While the blog focuses on frontend and GraphQL developers using tools like Cursor, the same principles apply to other roles, such as business analysts generating dashboards or backend engineers working across APIs.
canonical_url: https://wundergraph.com/blog/impact-mcp-llms-software-development-practical-example
---

## TL;DR
Model Context Protocol sounds fancy, but what can you actually do with it?
In this post I'll show you how to use MCP to one shot real tasks like exploring an API schema, writing GraphQL queries, or configuring a router.
There is no deep domain knowledge required, no hype, just practical examples.

## How MCP and LLMs Actually Help

There's a lot of talk about Model Context Protocol (MCP).
A lot of people are excited about it,
others are concerned about security,
and then there's a whole lot of confusion.

Why another protocol? Why not just OpenAPI?
Who actually needs this? And what problems does it solve?

To answer these questions, let's be pragmatic and look at three scenarios and how MCP impacts them;
no specific knowledge of our domain is required.

## Scenario 1: Exploring GraphQL API Schemas with MCP

We're the creators of an open source Schema Registry for GraphQL Federation called [Cosmo](https://github.com/wundergraph/cosmo).
You're a frontend developer using the GraphQL API of a company using Cosmo as their Schema Registry.
You could also be using REST APIs, SOAP, gRPC, or anything else.

Your task is to build a new feature that makes it possible to show all of the company's employees,
their availability, and make changes to their information.

You're not wasting time on the boring parts of software development,
so you're [using Cursor to do the boring parts](https://wundergraph.com/blog/cosmo-mcp-automates-graphql-federation-development), like making the API calls,
mapping the data to frontend components,
handling errors, and so on.

But speaking of "API calls", which APIs should we use to solve this task?
We're not exactly sure what the GraphQL API Schema looks like,
so we ask Cursor.
The problem? Cursor doesn't know exactly what the Schema looks like either,
and it could be hallucinating when creating the API calls.

This is where MCP comes in.
We've built an extension to our existing [CLI](https://cosmo-docs.wundergraph.com/cli/mcp)
that starts an MCP server locally.

With the "fetch_supergraph" tool, the LLM can fetch the most recent Schema of our GraphQL API.
In addition, the model can use the "verify_query_against_remote_schema" tool to verify that a generated query is valid.

This is a game changer,
because we can implement the complete feature in a single prompt.
There is no need to switch between different tools,
or manually copy and paste information.

The frontend developer can now make a prompt like this:

```
Given my existing component @EmployeeList.tsx,
I want to add a new feature to show and manage the availability of the employees.

Use the "fetch_supergraph" tool to fetch the most recent GraphQL API Schema.
Generate a query to fetch all employees and their availability,
and add a mutation so that the availability can be updated.

Verify both GraphQL operations using the "verify_query_against_remote_schema" tool.

Once the operations are verified,
add them to the existing component @EmployeeList.tsx by following the same pattern as seen in @Organization.tsx.

Once operations are added, run "pnpm generate" to update the generated models.

Finally, update the user interface to show the availability and allow for updates by modifying @EmployeeList.tsx.
```

We might have to iterate a bit on our prompts,
but then we can implement features like this in a single prompt,
or at least get close.

It's important to note that you can easily use CLI commands to achieve the same result.
You can download the latest version of the GraphQL API Schema with "npx wgc federated-graph fetch mygraph".
Cursor can then generate GraphQL Operations for you,
and you can verify them somehow.

The "big deal" about MCP in this scenario is that you can model your tools in a way that supports an LLM to one-shot entire tasks like this.
Build one powerful prompt that leverages all the tools available,
instead of having to go step by step.

In terms of security,
we've just automated the steps you'd usually do manually with the CLI.
The client must configure an API key in the same way as if they were using the CLI without the mcp subcommand.

## Scenario 2: Using the Dream Query Workflow and MCP to Design GraphQL APIs

Another scenario is the [dream query workflow](https://cosmo-docs.wundergraph.com/cli/mcp#dream-query-workflow),
a tool that allows developers to describe their desired GraphQL Query,
and the LLM will then propose schema changes to make the query work.

In this scenario,
you're a frontend developer whose job is to build a new feature,
e.g., to show each employee's department.

The problem? The GraphQL API Schema currently doesn't support this field,
so we have to come up with a proposal on how to change the Schema.

Without MCP,
the steps look like this:

1. Go to the Schema Registry UI (Studio) and search for the type "Employee"
2. Search through all Subgraph Schemas to find which one implements Employee type fields
3. Think about the best Subgraph to add this new field to
4. Create an updated Subgraph Schema with the new field and Department type
5. Run the "check" CLI command to verify that the proposed changes will work (compose) with all other Subgraph Schemas

With MCP,
you can one-shot this with the following prompt:

```
Supergraph: mygraph
Namespace: default

Use the dream_query_workflow
to enable the following query
on this Supergraph:

query {
  employees {
    name
    department {
      name
    }
  }
}
```

Similar to the previous scenario,
there's not much magic involved.
But instead of having to manually go through all the steps,
we can have the LLM read through our existing Schema and propose a solution.

Now you might ask,
but what if the LLM proposes a schema change that we're not happy with?
In this case, you can continue the conversation with the LLM and leverage it to iterate on the proposal or come up with alternative solutions.
Just create another "AI-Tab" and try with a different prompt.

{% partial file="blog-callout.md" /%}

## Scenario 3: Using MCP to Configure Cosmo Router

The last scenario is about [Cosmo Router](https://cosmo-docs.wundergraph.com/router/configuration),
or more precisely, its configuration.

The Router could also be understood as the API Gateway for GraphQL APIs.
It's a very complex piece of software with endless ways to configure simple use cases like authentication,
or really hard ones like limiting Prometheus attributes to reduce the cardinality of the metrics.

Enough domain knowledge...
let's talk about the problem of configuring a complex software thing.
To actually make this problem solvable by an LLM,
we've set some important basics.

As you've seen in the previous scenarios,
we've been pretty successful in creating feedback loops that allow the LLM to iterate on a solution.
As such, we're doing the same here.

As a foundation, we're using JSON Schema to describe the configuration.
An LLM can use this schema to understand the configuration and propose changes,
and we can expose a tool to verify a proposed configuration against this schema.

In addition, we're exposing another tool so that the LLM can make full text search queries through the documentation of Cosmo,
the Router, and all other available documentation.
This allows the model to come up with a configuration based on a meaningful prompt.

Let's look at an example.

```
Look into the cosmo_router_config_reference
and help me to enable WebSockets
in my Router config: router.yaml
```

Why is this powerful?
You might know that the Router supports Subscriptions over WebSockets,
but you're not exactly sure what the configuration syntax looks like.
We can search through the docs, copy-paste, and then fight with YAML indentation.
Or we just ask the LLM to propose and validate our desired configuration.

## Conclusion

We can look at MCP as just another protocol to expose an API.
We can get stuck in details like the syntax of the protocol,
but we might be missing the bigger picture.

Agent Mode combined with MCP completely redefines how we build software.
With carefully crafted workflows,
combined with powerful tools and the right prompts,
we're enabling developers to one-shot tasks that would otherwise take hours or days.

Developers can be architects, rather than code monkeys.
You can only put so much context into a single prompt,
but with MCP, we can compose much more complex workflows,
combine tools that use other tools, and so on.

Just ask yourself,
why are you following a 5 step process to build a feature?
Are you able to write down the steps in a markdown document?
And if so, why don't your automate the steps by turning them into an MCP tool?

---

{% faq /%}

---