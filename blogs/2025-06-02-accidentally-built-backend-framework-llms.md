---
type: blog
title: We accidentally built a backend framework for LLMs
slug: 2025-06-02-accidentally-built-backend-framework-llms
series: WunderGraph Blog
date: 2025-06-02
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - LLM Development
  - API Orchestration
  - Backend Frameworks
  - GraphQL Federation
tags:
  - graphql
  - graphql-federation
  - llm
  - api-orchestration
  - grpc-plugins
  - automation
entities:
  - Cosmo Plugins
  - GraphQL Federation
  - gRPC
  - LLMs
  - WunderGraph
  - Apollo Connectors
summary: |
  While simplifying API orchestration, WunderGraph accidentally built a backend framework for LLMs powered by Cosmo Plugins and GraphQL Federation. This framework enables LLMs to generate mapping code between gRPC interfaces and underlying services, transforming them from assistive tools into first-class backend development agents that can automate API integration and extension.
faqs:
  - q: What are Cosmo Plugins and how does they relate to LLMs?
    a: Cosmo Plugins is a plugin-based framework that allows you to build gRPC-backed modules for your Supergraph. It leverages LLMs—via agentic tools like Cursor—to generate the mapping code between gRPC interfaces and underlying services, enabling API orchestration without manual boilerplate.
  - q: How do Cosmo Plugins simplify GraphQL Federation?
    a: They eliminate the need to write Subgraphs for every backend system manually. Instead, you define a schema, auto-generate gRPC interfaces, and use LLMs to create adapters to non-GraphQL services like REST or gRPC. The plugin runs as an isolated subprocess, and the Cosmo Router handles composition and execution.
  - q: Why is this considered a backend framework for LLMs?
    a: Cosmo Plugins let LLMs "build the backend" by breaking tasks into agent-friendly steps: defining schemas, generating code, and composing modules. This transforms LLMs from assistive tools into first-class backend development agents—automating API integration and extension.
  - q: Can I build both monoliths and microservices with Cosmo Plugins?
    a: Yes. Cosmo Plugins let you start with a modular monolith, multiple plugins in one process, and later split them into separately deployed services if needed. The Federation layer handles cross-plugin dependencies declaratively, keeping runtime orchestration seamless.
  - q: How do I get started building with Cosmo Plugins?
    a: Run `npx wgc@latest router plugin init <name>` to scaffold a plugin, open the directory in Cursor, and let the LLM implement the logic. You can edit the schema, recompose modules, and deploy instantly. Full instructions are in the Cosmo Plugins docs.
canonical_url: https://wundergraph.com/blog/accidentally-built-backend-framework-llms
---

While solving the problem of simplifying API Orchestration for our customers,
we accidentally built a backend framework for LLMs-and it's a joy to use.
We unpacked the thinking behind it [in this blog on Generative API Orchestration](https://wundergraph.com/blog/generative-api-orchestration).

It's like v0 from Vercel, Lovable, or Bolt...but for the backend.

You can use it to **build modular monoliths**, **microservices**, or a **mix of both**.
And if you want to, you can move from one to the other.
If you like the idea of vibe coding complete backend applications,
you will love it.
If that sounds like nails on a chalkboard,
you might lose your job.

## Why all digital enterprises build graphs of APIs

We're working with companies like eBay, SoundCloud, Procore, and others to help them build great APIs.

By talking to them about their workflows and
how they build software to solve customer problems,
we've started to notice consistent patterns.

One such pattern is that all **digital enterprises build graphs of APIs**.
Intentionally or not,
organizations tend to split their projects into teams,
each owning part of the overall domain.
These teams build APIs to provide capabilities to other teams or to enable products to be built.

Typically, the APIs built by individual teams are somewhat related to each other.
Nothing in a business is fully isolated from the rest.
A customer buys products,
that product needs to be shipped,
payment needs to be processed,
and different teams present the buying experience through different channels:
like a website, a mobile app, or a chatbot.

Our customers have **not only acknowledged this**,
they are actively **embracing it**.
Instead of creating a graph of APIs by accident,
they are doing it intentionally.
They are building *on top of* the Supergraph concept,
also known as Federated Graph or [GraphQL Federation](https://graphql.org/learn/federation/).

A Supergraph is an API that combines multiple Services (Subgraphs) into a single API.
The public API of the Supergraph looks like a GraphQL monolith,
but on the inside it's composed of multiple Services.

An **alternative** would be to build fully isolated REST or gRPC services,
publish them in a **registry like [Backstage](https://backstage.io/)**,
and have product teams manually integrate them into their applications,
e.g., through a backend-for-frontend ([BFF](https://learn.microsoft.com/en-us/azure/architecture/patterns/backends-for-frontends)) pattern.

The problem with the BFF approach is that instead of creating NxM connections between frontend and backend services,
you've just moved the problem to the BFF layer, creating NxM connections between frontend and BFF services.

The Supergraph approach, on the other hand, unifies all APIs into a graph.
This serves as a single entry point for all applications,
including web apps, mobile, chat applications, and now LLM agents using the Model Context Protocol (MCP).

Compared to the Backstage approach,
**the Supergraph makes API discovery, integration, and extension much easier**.
With a traditional Microservices architecture,
you have to find the right service to solve your problem,
then manually integrate each one into your product, similar to managing dependencies.
With a Supergraph, all you have to do is search through the Schema and write a query.
With the help of LLMs, that means that you write a single prompt and get a query back.
In terms of extending the graph,
you add new fields to the schema,
implement them, and publish the changes to the Schema Registry (WunderGraph Cosmo).
Once published, other users can use a prompt to build a query that includes the new field.

But—and this is a big but—
until now,
the **cost of creating a Supergraph was simply too high**.

{% partial file="blog-callout.md" /%}

## The problem: Unifying all your APIs ~~is~~ was impossible

A **Supergraph** is an abstraction layer on top of existing internal and external APIs.
While it's **proven to be very beneficial** for serving many different applications with many backend services,
most of these **services don't speak GraphQL**, nor do they understand the **Federation** protocol.

If you have to implement and deploy a new Subgraph for every handful of fields,
you end up with a lot of Subgraphs,
even though all they do is **proxy** between the Supergraph and the existing underlying services.

There must be a better way!
Could we build a framework that leverages LLMs to generate the code needed to proxy between the Supergraph and non-GraphQL, non-Federation services?
This is exactly what we've been working on for the last few months.

One of our customers has a huge legacy of **thousands of REST APIs**,
or let's just say JSON-over-HTTP APIs,
because who really builds truly RESTful APIs?
They want to adopt the Supergraph approach,
but it's simply **too expensive to rewrite** all of their existing APIs to GraphQL.
If they could **reduce the number of API calls** for a single page from 20 to one,
it would be a huge win.

## The solution: Cosmo Plugins leverage LLMs to generate the code to proxy between the Supergraph and non-GraphQL, non-Federation services

As simple as it sounds,
solving this problem was anything but trivial.
It's not possible to tell an LLM to generate proxy code for thousands of REST API endpoints.
You have to split the problem into small chunks,
give the LLM very specific constraints and instructions,
and only then can you leverage its strengths without overloading it.

As a side effect, like I mentioned earlier,
this led us to build a **backend framework for LLMs**.

## The framework: Cosmo Plugins

Here's how it works:

1. You define a Schema for each module or service you'd like to add to the Supergraph.
2. Through a process of **composition**, we ensure that all modules/services fit together and that all fields in the Supergraph schema can be resolved.
3. For each module, we generate a **gRPC protobuf file** that describes the features the module provides.
4. With predefined prompts, we can instruct an LLM code-gen with agentic capabilities like [Cursor](https://www.cursor.com/) to generate the mapping/adapter code between gRPC call and the underlying service.
5. The module gets bundled into a plugin file, which the Router manages as a sub-process.

For the plugin lifecycle management,
we're using [go-plugin](https://github.com/hashicorp/go-plugin) from Hashicorp.
It is a battle-tested library being used by projects like Terraform, Consul, and Vault.
Because each plugin runs as a separate subprocess,
panics are isolated and don't affect the main process.

Another huge benefit of this approach is that it allows you to build **truly modular monoliths**.
Since each plugin is isolated in its own subprocess,
multiple plugins can form a modular monolith,
but each plugin is completely independent.
One of the big issues with monoliths is that it's hard to split them into smaller parts when the business requires it.
This comes down to the fact that oftentimes,
code between different parts of the monolith is tightly coupled.

With Cosmo Plugins,
you can build a graph of APIs,
but the deployment strategy is completely up to you.
You can deploy everything as a single monolith,
keeping all plugins in a single codebase,
but you could also deploy each plugin as a separate service,
distributing the code base across multiple repositories.

The beauty of this approach is that you can start with a monolith,
and if you really really need to,
there's an easy path to move some functionality to a separate service.

You might be wondering how this approach could handle dependencies between plugins.
What if one service needs some data from another one?
Such a problem is already solved by the underlying Federation protocol.
You can define **dependencies between services in a declarative way**,
composition will ensure that the dependencies are valid and resolvable,
and the Router will take care of resolving them at runtime.

## An example: How to use Cosmo Plugins and leverage LLMs to build an API

First, you need to initialize a new project:

```sh
npx wgc@latest router plugin init hello-world
```

This will create a complete setup including Router and a plugin that implements a `hello-world` module.
Next, you have to open Cursor in the plugin directory (./cosmo/plugins/hello-world).
If you're in the right directory,
it will automatically pick up the generated Cursor Rules we've prepared to make AI-coding as easy as possible.

Finally, tell Cursor to implement your plugin.
You can also modify the `schema.graphql` file if you'd like to add more fields or types.

For more in-depth instructions on how to use Cosmo Plugins,
check out the [Cosmo Plugins documentation](https://cosmo-docs.wundergraph.com/router/plugins#grpc-plugins).

If you'd like to add another module,
just run the init command again,
add a second module with a different name,
and update the Router configuration to compose it with the first one.
That's it, you've just built your first modular monolith with LLMs.

## Conclusion

We believe that frameworks focused on leveraging LLMs will continue to grow in usage.
LLMs are very powerful for code generation,
but they also have limitations.
Not every problem is a good fit for LLMs,
especially when the scope of each individual problem is too large.

With Cosmo Plugins,
we're just scratching the surface of what's possible.
So we're really excited to see what you'll build with it.
Please share your thoughts and feedback with us on [Discord](https://wundergraph.com/discord).

If you'd like to learn more about Cosmo Plugins,
check out the [Cosmo Plugins documentation](https://cosmo-docs.wundergraph.com/router/plugins#grpc-plugins).

If you'd like to learn more about the Router,
check out the [Router documentation](https://cosmo-docs.wundergraph.com/router).

---

{% faq /%}

---