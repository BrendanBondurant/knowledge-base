---
type: blog
title: Cosmo MCP: Agent Mode now handles all the boring parts of GraphQL Federation (Right in your IDE)
slug: 2025-04-14-cosmo-mcp-agent-mode-graphql-federation-ide
series: WunderGraph Blog
date: 2025-04-14
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - Developer Experience
  - IDE Integration
  - Automation
tags:
  - graphql
  - graphql-federation
  - mcp
  - developer-experience
  - automation
  - ide
entities:
  - Cosmo MCP
  - Model Context Protocol
  - Cursor
  - Windsurf
  - VSCode
  - WunderGraph
  - GraphQL Federation
summary: |
  Cosmo MCP (Model Context Protocol) integrates with Agent Mode in Cursor, Windsurf, and VSCode to automate GraphQL Federation workflows directly from your IDE. Developers can now handle schema changes, query validation, and router configuration without leaving their editor, streamlining the development process and reducing manual CLI operations.
faqs:
  - q: What is Cosmo MCP and how does Agent Mode enhance it?
    a: Cosmo MCP (Model Context Protocol) extends the Cosmo CLI with an IDE-integrated agent that communicates over STDIO. With Agent Mode in editors like Cursor, Windsurf, or VSCode, developers can automate schema changes, query validation, and router configuration without leaving their IDE.
  - q: How does Cosmo MCP simplify schema changes in a federated GraphQL API?
    a: Cosmo MCP provides workflows like `schema_change_proposal_workflow`, which automates tasks such as downloading subgraph schemas, updating types, and running composition checks. This allows developers to propose valid schema changes with minimal manual effort.
  - q: What is the "dream query" workflow?
    a: The dream query workflow lets developers write a query they *wish* worked, even if the schema doesn't support it yet. Cosmo MCP validates the query, identifies what's missing, and generates a schema change proposal to support it, therefore bridging the gap from idea to implementation.
  - q: Can Cosmo MCP help configure the Cosmo Router?
    a: Yes. With tools like `cosmo_router_config_reference` and `verify_router_config`, MCP enables models to suggest and validate configuration options against the Router's JSON schema. This helps prevent errors and misconfigurations.
  - q: What IDEs support Cosmo MCP?
    a: Cosmo MCP works with any IDE that supports Agent Mode, including Cursor, Windsurf, and VSCode. Setup involves configuring the IDE to invoke the `wgc mcp` command with a Cosmo API key.
  - q: Do I need to manually sync the latest schema to use MCP workflows?
    a: No. Cosmo MCP handles schema retrieval automatically. Whether you're exploring a type or proposing a schema change, the agent fetches the latest Supergraph and subgraph schemas for context.
canonical_url: https://wundergraph.com/blog/cosmo-mcp-agent-mode-graphql-federation-ide
---
## TL;DR

Cosmo MCP now works with Agent Mode in Cursor, Windsurf, and VSCode.
That means your IDE can help you navigate your schema, propose changes, validate queries, configure the router, and more — all without leaving your editor.

{% partial file="blog-callout.md" /%}

## Let’s take a closer look at how Cosmo MCP + Agent Mode works

In our latest release, we've added support for the Model Context Protocol (MCP) to the Cosmo CLI, [wgc](https://www.npmjs.com/package/wgc).

With Cosmo MCP and Agent Mode in Cursor, Windsurf, or VSCode, your IDE can now assist you with powerful workflows for Schema Development, Schema Exploration, Router Configuration, and more.

In this post, we'll go through a few examples of how Cosmo MCP can make your life easier.
If you want details on all of the features, look at the [Reference Documentation](https://cosmo-docs.wundergraph.com/cli/mcp).

## How the Cosmo MCP Server works

The Cosmo MCP Server is a small extension added to the Cosmo CLI.
It's using STDIO to communicate with the IDE, so it's operating in the same context as if you were using the CLI directly from your terminal.
We're not starting an SSE server or anything like that, which could lead to security issues.

## Setting up Cosmo MCP in your IDE

Before we get started, we need to configure our IDE to use Cosmo MCP.
Get an API key in [Cosmo Studio](https://cosmo-docs.wundergraph.com/cli/mcp#1-create-a-new-api-key) and add the following configuration to your IDE.

```json
{
  "mcpServers": {
    "cosmo": {
      "command": "npx wgc",
      "args": ["mcp"],
      "env": {
        "COSMO_API_KEY": "cosmo_<redacted>"
      }
    }
  }
}
```

We're all set up and ready to go!
Let's dive into some examples.

## Using Cosmo MCP to explore your Supergraph Schema

There are several options for exploring the schema of a GraphQL API.
You can use tools like Cosmo Studio to look through the SDL or click through the Schema Explorer.
GraphiQL can also be used to search through the schema or use autocomplete to find the right fields.

With Cosmo MCP, you can now integrate schema exploration into your IDE.

For example, you could add a file containing a React component to your Agent Mode context and then ask the following question:

```
Supergraph: mygraph
Namespace: default

Look into the Supergraph Schema and update the "Employee" Query to add information about the employee's department.
Use the verify_query_against_remote_schema tool to verify that the query is correct.
Update the component to show this information.
```

The model can now look into the latest version of the Supergraph Schema, update the Query, make sure it's correct, and then update the user component to show the new information.
There is no need to manually synchronize the latest schema or search through the Schema Explorer for the exact naming of the fields.
By having the "verify_query_against_remote_schema" tool in the loop, the model will fix problems as it goes.

## Using Cosmo MCP to automatically propose changes to your Supergraph Schema

Making a change to your Supergraph Schema is typically a complex task.
First, you need to understand the overall structure of the schema and how it's composed from multiple underlying Subgraphs.
If you want to add a new field to a type in your Supergraph Schema, you need to choose a Subgraph to own that new field.

Once you've made the decision, you can start making changes to the Subgraph.
This is an iterative process, as you need to use the "check" command to verify that the changes are composable with all of the other Subgraphs, non-breaking, following the linting rules, etc.

With Cosmo MCP, you can access several tools to automate this process.
You can use the following prompt as a blueprint:

```
Supergraph: mygraph
Namespace: default

Use the schema_change_proposal_workflow
to add the field "age: Int!"
to the "Employee" type
in this Supergraph.
```

The "schema_change_proposal_workflow" gives instructions to the model to run the following steps:

1. download the supergraph schema
2. explore the schema to find the right places to make changes
3. download all relevant subgraph schemas
4. modify the subgraph schemas to make the changes
5. run composition checks to verify that the changes are valid

As a result, you'll get a diff of the proposed changes on your Supergraph Schema and the Subgraph Schemas.
You can review the proposed changes, iterate on them with more instructions, or proceed to the implementation phase.

Even for someone with limited knowledge of the schema or GraphQL Federation, this can be a great way start with schema development.
By having "checks" in the loop, the model will automatically correct itself and apply the rules of Federation.

## Using Cosmo MCP for the Dream Query Workflow

I "borrowed" the idea of the dream query workflow from Mark Larah's post on the [Yelp Engineering Blog](https://engineeringblog.yelp.com/2020/10/dream-query.html).

The core idea is to start with a query that isn’t possible to run yet.
This "dream query" helps guide the schema design, instead of creating the schema first and then telling frontend developers how to use it.

This workflow makes a lot of sense, especially in GraphQL Federation, because frontend developers often don't know much about Subgraphs and how they're composed.
They only want to add some fields to their Query to implement a new feature.

With Cosmo MCP, we're able to enhance this workflow by automating the process of going from a dream query to a valid schema change proposal.
In fact, the dream query workflow is an extension of the schema change proposal workflow.

We're already capable of turning an idea for schema changes into a concrete proposal.
As such, the dream query workflow simply adds two more steps in front of the schema change proposal workflow:

1. run validation of a query against the current supergraph schema
2. use the validation result to build a prompt for the schema change proposal workflow

Let's look at an example:

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

If we assume that the field "department" does not currently exist, the model will first run the validation of the query against the current supergraph schema.
This will return a list of errors and a description of the problem, which the model can then use to build a prompt for the schema change proposal workflow.

You can then use the end result of the workflow to make the changes to your Subgraphs.
Going from a dream query to a schema change proposal is now a one-click process.

## Using Cosmo MCP for Router Configuration

Another area where we always get questions from our users is how to configure the Router properly or simply how to achieve a goal without knowing if it's possible.

To make this easier, we've added multiple tools to Cosmo MCP to assist with Router Configuration.

With the "cosmo_router_config_reference" tool, the model can bring the JSON Schema of the Router Configuration into the context of the conversation.
Many models can use this to suggest configuration options.
However, models can hallucinate and suggest invalid configurations.
To enure the suggestions are valid, you can use the "verify_router_config" tool, which will check the configuration against the JSON Schema.
In case of errors, the response will be very verbose, helping the model to understand the problem and suggest a fix.

Finally, you can use the "search_docs" tool to make full text searches through the entire Cosmo Documentation.
For broader questions that aren’t easily answered by just looking at the JSON Schema, this approach gives the model a better chance of finding the right answer—or at least a useful starting point for continuing the conversation.

Here's an example prompt that will help you enable CORS on your Router:

```
Look into the cosmo documentation
and help me to properly configure CORS
in my Router config: router.yaml
```

## Conclusion

We believe that MCP and Agent Mode will help developers to be more productive.
It's a great way to automate tasks and allow the developer to focus on the high level thinking, while the model takes care of the low level details.

We'll continue our work on MCP and Agent Mode to make it even more powerful and helpful.

For more on how we're ensuring quality and reliability in GraphQL Federation, read last weeks blog about [Query Plan Regression Testing in GraphQL Federation](/blog/adventure_in_neverending_quest_for_quality).

If you've got any feedback or ideas for additional workflows we could automate, please let us know on [Discord](https://wundergraph.com/discord) or open an issue on [GitHub](https://github.com/wundergraph/cosmo/issues).

---

{% faq /%}

---