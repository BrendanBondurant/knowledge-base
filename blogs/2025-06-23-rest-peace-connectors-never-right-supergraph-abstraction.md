---
type: blog
title: REST in Peace—Connectors Were Never the Right Supergraph Abstraction
slug: 2025-06-23-rest-peace-connectors-never-right-supergraph-abstraction
series: WunderGraph Blog
date: 2025-06-23
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - API Orchestration
  - GraphQL Federation
  - LLM Automation
  - gRPC Plugins
tags:
  - graphql
  - graphql-federation
  - llm
  - api-orchestration
  - grpc-plugins
  - apollo-connectors
entities:
  - GraphQL Federation
  - Apollo Connectors
  - gRPC Plugins
  - LLMs
  - WunderGraph
  - Cosmo
summary: |
  Declarative connectors like Apollo's @connect directive fail as Supergraph abstractions due to N+1 problems, implementation leakage, and poor LLM compatibility. gRPC Plugins provide a better solution by separating schema from implementation, enabling batching, and allowing LLMs to generate type-safe integration code that cuts implementation costs by 99%.
faqs:
  - q: Why don't declarative connectors work well for Supergraph orchestration?
    a: Declarative connectors like Apollo's `@connect` directive leak implementation details into the schema, create N+1 problems, and are hard to test or debug. They're also too verbose, untyped, and not LLM-friendly, making them a poor fit for modern workflows.
  - q: What's the N+1 problem in this context?
    a: With declarative connectors, each entity resolution (e.g., fetching `hostReview` for each `Booking`) triggers a separate API call. This leads to unscalable behavior when resolving many items—e.g., 50 bookings = 50 review calls. The Router cannot batch these calls.
  - q: How do gRPC Plugins solve these issues?
    a: gRPC Plugins separate the schema from implementation, enable batching, and use a gRPC interface for communication. The plugins are written in Go (or any language), tested independently, and run as isolated processes, making them debuggable and CI/CD-friendly.
  - q: Can LLMs generate plugin code automatically?
    a: Yes. With Cosmo's plugin system and Cursor Rules, LLMs can generate, test, and build gRPC Plugins from schema definitions. The human-in-the-loop workflow ensures high developer productivity with minimal boilerplate.
  - q: What makes this better than a declarative mapping DSL?
    a: There's no need to learn a custom DSL. You define the GraphQL schema, and the LLM generates readable Go code. Plugins are real programs-easy to extend, test, and debug—unlike declarative connectors which are hardcoded and inflexible.
  - q: Do I need Go to use gRPC Plugins?
    a: No. While the initial implementation targets Go, the system is language-agnostic. Any language that supports gRPC can be used to write plugins, with Node.js and Python support planned.
canonical_url: https://wundergraph.com/blog/rest-peace-connectors-never-right-supergraph-abstraction
---

Companies like Apollo, StepZen (now IBM), Tailcall, and others tried the same declarative approach to API orchestration over and over again. The problem? It simply doesn't work with complex use cases, especially not with REST.
I'll explain why in the next section.
But first, I think this quote, which seems to be attributed to Albert Einstein, sums up the situation quite well:

{% quote author="Albert Einstein" %}
Insanity is doing the same thing over and over again and expecting different results.
{% /quote %}

I have to admit that I've been guilty of this myself.
In 2018, long before starting WunderGraph,
I built my first GraphQL API Gateway with a [declarative approach](https://github.com/jensneuse/graphql-gateway/blob/f027e5a200a39d9a6506be30473877335255c4a2/schema.graphql#L131).

Since then, people have kept copying the idea, but the problems never went away.
It looks simple in a hello world example,
but it doesn’t scale to enterprise use cases.

## What are the problems with declarative API Orchestration styles like Apollo Connectors?

To understand why declarative API Orchestration, especially connectors, breaks down, let's take a look at the following example:

```graphql
type Booking {
  id: ID!
  checkInDate: String!
  checkOutDate: String!
  status: BookingStatus!
  hostReview: Review
    @connect(
      source: "listings"
      http: { GET: "/review?bookingId={???}" }
      selection: """
      id
      text
      rating
      """
    )
}
```

Some connector frameworks are gated behind enterprise-only plans, but more importantly,
there are several fundamental technical problems with this approach.

{% partial file="blog-callout.md" /%}

### GraphQL Directives are not a good fit for infrastructure as code

One fundamental flaw of using GraphQL Directives as the foundation to define Connectors is that they are not designed to be used for infrastructure as code. This limitation is baked into the abstraction, it wasn’t designed for this kind of work.

GraphQL Directives are not generic; you cannot extend them, and they are more or less not type-safe.
You can express that a directive is allowed to be used on a field,
but you cannot say that it's only allowed to be used on fields of a certain type.

Another flaw in GraphQL SDL is that you cannot use maps within the Schema.
It's not possible to map the response of an API call to fields of different names,
which led to the creation of the `selection` field in the `@connect` directive,
which only works with an LSP that understands that the "multiline string" value has a special meaning.

### Declarative API Orchestration is verbose and obscures the GraphQL SDL

The `@connect` directive requires a certain level of verbosity to allow the configuration of mappings,
selections, paths, URL parameters, HTTP Verbs, and more.

When looking at more complex scenarios with multiple connected fields,
it'll be hard to understand the GraphQL SDL and the intent of the Connector.
Ideally, the GraphQL SDL would be purely focused on describing the data model and the relationships between the entities,
and the Connector would live elsewhere.

In a sense, the `@connect` directive mixes the declaration of a contract with its implementation,
which leads to another problem.

### Declarative API Orchestration often leaks implementation details into the GraphQL SDL

When using the `@connect` directive,
you're somewhat forced to define the GraphQL SDL in a way that ensures "mappability" between the two contracts.
If an API returns data in a weird shape,
it might not be possible to map it into idiomatic GraphQL fields.

An ideal solution would allow us to define the contract completely decoupled from the underlying services.
This would not just keep the GraphQL SDL clean 
but would also ensure that we can easily change the implementation of the Connector without having to change the GraphQL SDL.

### Declarative API Orchestration suffers from N+1 problems

As illustrated in the example above,
we add the `hostReview` field to the `Booking` type and use the `@connect` directive to load the review for a booking from a REST API.
If we need to fetch a review for 50 bookings,
we'll have to make 50 API calls to the `reviews` endpoint to fetch this data.

This problem is known as the [N+1](https://www.freecodecamp.org/news/n-plus-one-query-problem/) problem,
and it's directly inherited from the declarative nature of the approach.
We're running into this issue because we can't express the relationship between `Booking` and `Review` in a way that would allow the Router to "batch" the requests.

The solution to this problem is to find a more generic approach that would allow the Router to implement the [Dataloader pattern](https://www.youtube.com/watch?v=vWQYI5fNytM).
Instead of requesting a single review for a booking,
the Dataloader pattern creates a function that loads a list of reviews for a list of bookings.

### Declarative API Orchestration are hard to debug & test

A declarative approach works great when all participating services follow very strict rules
and we have full control over their implementation.
If the services "compose" into a resolvable Supergraph,
we know that every possible Query can be resolved by the Router.
This assumes all services behave correctly and strictly follow the Federation Specification.

Unlike some declarative approaches,
the "correct" use of the `@connect` directives cannot predict if the Supergraph is resolvable.
While Federation directives can be evaluated at build time,
we only know if our Connectors are "correct" at runtime.

As described in the [Apollo documentation](https://www.apollographql.com/docs/graphos/connectors),
the proposed workflow to test and verify Connectors is to start the Router,
open the GraphQL Playground,
and try out all possible Queries.

This approach is not just manual and error-prone,
but it also doesn't align with the way we test and verify the correctness of our implementation.

For us, the minimum bar for a Connectors-like solution is as follows:

- We must be able to define tests that we can run against mocks
- Testing of an Adapter (Connector) should not require the Router to be running
- We must be able to attach a debugger to the Adapter to find issues in the mapping logic

These declarative connector models meet none of these requirements.
As such, it can only be seen as a toy solution for small use cases.

## Summary of the problems with declarative API Orchestration

As noted at the beginning of this article,
we tried to use a declarative approach in 2018.
In a [previous post](https://wundergraph.com/blog/graphql-federation-connectors), we explored the risks of relying on Connectors in Federation, especially around N+1, testing, and input validation.

Among the many reasons,
not being able to test and debug Connectors and the inability to solve the N+1 problem were the main reasons why we stayed away from this approach.

As it turns out,
sometimes it's best to park an idea on the shelf for a while to see if advancements in technology allow us to solve it in a better way.
In this case, this is exactly what happened.

With the recent advancements in Generative AI,
LLMs are now capable of enabling us to solve the problem of API Orchestration in a much better way.
Paired with some new ideas on how to structure the problem,
we've been able to build a solution that completely changes the way we think about API Orchestration.

## Introducing WunderGraph's new API Orchestration solution: gRPC Plugins

What sounds quite simple on the surface,
almost boring,
was an effort that took us several months to reach the MVP state.
However, you'll see that some key decisions we made have led to the simplicity and elegance of the solution.

When designing a solution to a problem like API Orchestration,
it's important to understand the constraints we're working with.
For example, when looking at existing connector frameworks,
it's clear that the approach is designed around a human-centric workflow.
The intention of Connectors is to have developers write GraphQL SDL with the `@connect` directive.

With [gRPC](https://grpc.io/) Plugins,
we're taking a completely different approach.
We've designed the solution to align with an up-and-coming workflow that's rapidly becoming the new standard for software development.

## gRPC Plugins: LLM-centric API Orchestration with human-in-the-loop interaction

The idea behind gRPC Plugins is to simplify the process of integrating APIs into a Supergraph to the point where each step can be solved by an LLM.
Engineers can focus on the high-level architecture of the plugin;
they define the GraphQL SDL and "own" the contract,
and the LLM takes care of generating the code,
which the Engineer can then review and deploy.

To achieve this,
we had to find a solution that works under the following constraints:

1. The solution must be easy to test & debug
2. The developer experience should be fast
3. LLMs must be able to easily generate the necessary code
4. The solution must be low overhead and highly scalable
5. The solution must not require external deployments

Based on these constraints,
we came up with the following approach:

1. The GraphQL SDL defines the contract
2. A compiler generates a gRPC Protobuf Plugin definition from the GraphQL SDL
3. The Router can dynamically load plugins and "talk" to them using gRPC
4. We're relying on the Hashicorp go-plugin library, which allows for high performance leveraging Unix Domain Sockets
5. The plugin implementation is a vanilla Go service that can be tested and debugged with the standard tools
6. We've come up with a set of [Cursor](https://www.cursor.com/) Rules that help an LLM perform the right steps in a focused manner

The developer experience is as follows:

1. The Engineer manually defines the GraphQL SDL or uses the LLM to generate it, e.g., from an OpenAPI specification
2. Once the Engineer is happy with the SDL, they prompt the LLM to "implement the updated Schema"
3. The LLM will now go through all steps in one pass, running the compiler, updating the implementation, adding tests with mocks, compiling the plugin
4. The Engineer can review the changes and re-prompt the LLM to change the implementation as needed
5. The Engineer can then deploy the Router with the new plugin

## Why we've chosen Hashicorp's go-plugin library over other options

When we started working on this project,
we looked at several options for implementing the plugin system.

One solution we evaluated was to use WebAssembly to run the plugin code in the Router.
In the end, we've decided against this approach because of the immaturity of the WebAssembly ecosystem.
We weren't confident that WASM could satisfy our testing and debugging constraints.
In addition, we were afraid that dependency management would be much harder compared to "just use Go".

Another solution we evaluated was to embed a scripting engine into the Router.
This would be more lightweight in terms of implementation
but would come with some serious drawbacks.
The performance would be much worse compared to a native Go implementation,
even if we consider the overhead of gRPC.

In the end, we've decided to use the [go-plugin library](https://github.com/hashicorp/go-plugin) from Hashicorp.

> go-plugin is a Go (golang) plugin system over RPC. It is the plugin system that has been in use by HashiCorp tooling for over 4 years. While initially created for Packer, it is additionally in use by Terraform, Nomad, Vault, Boundary, and Waypoint.
>
> This plugin system has been used on millions of machines across many different projects and has proven to be battle hardened and ready for production use.

The go-plugin library is mature and battle-tested.
It allows us to use vanilla Go code to implement the plugin.
We can easily test and debug the code.
The go-plugin library makes it easy to manage the plugin lifecycle,
so we're not reinventing the wheel.

The go-plugin library makes it easy for us to run plugins as a co-processor for the Router.
This keeps the architecture simple because the additional complexity of running a plugin in a separate pod is not needed.

In addition, the go-plugin library comes with another powerful feature.
We're well aware that Go is not the number one language for everyone.
Go comes with a very fast runtime, compiles super quickly,
and LLMs are very capable of generating Go code.
For us as a Go-focused company,
it's a great fit.

However, we know our users are not all Go experts.
That's not a problem because the go-plugin library supports plugins in any language.
The only requirement is that the plugin implements a specific gRPC interface.
So, while we're starting with Go,
you can expect to see support for additional languages
like Node.js, Python, and more.

## Cursor Rules: A key to the success of guiding LLMs to the right steps

When working with LLMs,
it's important to understand what they are good at and where they struggle.
If you want to develop an approach that allows LLMs to consistently perform the right steps,
you need to provide them with guidance.

Tools like Cursor allow you to define a set of rules that will be added to each prompt,
kind of like "extending" the system prompt.
To make this whole process as easy for a developer as possible,
we've created a CLI command that sets up a new plugin project with all the necessary files,
including the Cursor Rules.

All you have to do is run the following command:

```sh
wgc router plugin init hello-world
```

If you then open the plugin directory in Cursor,
a single prompt is enough to get you started.

Here's the gist of the Cursor Rule:

```text
## Development Workflow

1. When modifying the GraphQL schema in `src/schema.graphql`, you need to regenerate the code with `make generate`.
2. Look into the generated code in `generated/service.proto` and `generated/service.pb.go` to understand the updated API contract and service methods.
3. Implement the new RPC methods in `src/main.go`.
4. Add tests to `src/main_test.go` to ensure the plugin works as expected. You need to run `make test` to ensure the tests pass.
5. Finally, build the plugin with `make build` to ensure the plugin is working as expected.
6. Your job is done after successfully building the plugin. Don't verify if the binary was created. The build command will take care of that.

**Important**: Never manipulate the files inside the `generated` directory yourself. Don't touch the `service.proto`, `service.proto.lock.json`, `service.pb.go`, or `service_grpc.pb.go` files.
```

## Rethinking Connectors: Cosmo gRPC Plugins vs the Declarative Approach

Finally, here's a quick head-to-head comparison of Cosmo gRPC Plugins vs Declaritive Connectors:

| Feature | Cosmo gRPC Plugins | Declarative Connectors |
|---------|-------------------|-------------------|
| License | Apache 2.0 | GraphOS Enterprise |
| Supported Upstream Services | HTTP APIs / REST, gRPC, GraphQL, SOAP, Databases, S3, etc. | HTTP APIs / REST |
| Supported Languages | Go, Node.js, Python, etc. | `@connect` directive |
| Mappings | LLM generates mappings | Custom Mapping Language |
| Developer Experience | Fast, LLM-centric, human-in-the-loop | Verbose, human-centric, slow, repetitive |
| Testability | Easy to test with mocks | Requires Router to be running |
| CI/CD | Unit tests, mocks, and integration tests | manual testing |
| Debugging | Easy to debug with standard tools | Requires Router to be running, no debugger support |
| N+1 Problem | Solved | Inherited |
| Performance | High | Native |

## Conclusion

With declarative connector approaches,
it's always been a challenge to solve all real-world edge cases, because the abstraction doesn't fit the problem.
Once you've implemented a Connector,
another user might need something slightly different.
Eventually, you'll end up creating some kind of virtual machine and your own DSL.
Then you realize that you've just invented a new programming language.
And it's a bad one.

I think it's time to rethink software development.
When a company creates Connectors with a custom DSL for mappings, developers have to learn how to use it.
There are entire classes and webinars dedicated to teaching users how to use this new syntax.

With gRPC Plugins,
we're leveraging LLMs to abstract away the complexity of API Orchestration.
You don't have to learn a new DSL,
and we also didn't invent a new programming language for mappings or adapters.
There's no course needed because we're just generating a bunch of code which is very easy to read and understand.

When building tools for developers,
we have to adopt this new reality.
We should build frameworks with LLMs in mind.

To get started, take a look at the [Router Plugins documentation](https://cosmo-docs.wundergraph.com/router/plugins).

---

{% faq /%}

---