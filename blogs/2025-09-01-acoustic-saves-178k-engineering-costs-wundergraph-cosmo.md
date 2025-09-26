---
type: blog
title: Acoustic saves $178K in engineering costs with WunderGraph Cosmo
slug: 2025-09-01-acoustic-saves-178k-engineering-costs-wundergraph-cosmo
series: WunderGraph Blog
date: 2025-09-01
author: Brendan Bondurant
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - API Management
  - GraphQL Federation
  - Developer Experience
  - Cost Optimization
tags:
  - graphql
  - federation
  - api-management
  - developer-experience
  - cosmo
  - schema-registry
  - performance
entities:
  - Acoustic
  - WunderGraph Cosmo
  - GraphQL Federation
  - Karol Krogulec
  - Kira Shatskyi
  - Blake Reed
  - Stefan Hepper
summary: |
  Acoustic saved nearly $178,000 in engineering costs by migrating from a complex Rust-based GraphQL gateway to WunderGraph Cosmo. The migration eliminated 30-minute build times, brittle rollbacks, and the need for custom Rust plugins, while adding visual schema exploration, built-in traffic controls, and isolated endpoints for public/private API separation.
faqs:
  - q: How much did Acoustic save by moving to Cosmo?
    a: Acoustic saved nearly $178,000 in engineering effort by replacing Rust plugins and brittle rollbacks with Cosmo's schema-aware router and visual tooling.
  - q: What challenges did Acoustic face with their old GraphQL gateway?
    a: Their Rust-based router took up to 30 minutes to build, every subgraph change triggered a full supergraph rebuild, schema conflicts caused deployment issues, and rollbacks required CI-heavy coordination.
  - q: How easy was it to migrate from the Rust router to Cosmo?
    a: According to Acoustic, "The migration was just updating the DNS record from the old router to the Cosmo Router."
  - q: What new capabilities did Cosmo provide Acoustic?
    a: Cosmo added a visual schema explorer, schema registry, built-in traffic controls, and taggable, isolated endpoints that separated public/private APIs and enabled customer-specific interfaces.
canonical_url: https://wundergraph.com/blog/acoustic-saves-178k-engineering-costs-wundergraph-cosmo
---
## TL;DR:
By moving to Cosmo, [Acoustic](https://www.acoustic.com/) saved nearly ***$178,000*** in engineering effort.
What once meant brittle builds, Rust plugins, and CI-heavy rollbacks is now handled by a faster, schema-aware [router](https://wundergraph.com/router-gateway).
---
## Acoustic’s $178K Shift to Cosmo

[Acoustic](https://www.linkedin.com/company/goacoustic/) is a marketing and customer engagement platform that helps global brands create personalized, data-driven experiences across email, mobile, SMS, and social channels.
Serving more than 3,500 brands, including [Fortune 500 companies](https://fortune.com/ranking/global500/), the company provides an integrated marketing cloud with AI-powered tools for campaign management, personalization, analytics, and customer journey optimization.

Maintaining Acoustic’s [GraphQL](https://graphql.org/learn/federation) gateway was on track to consume **$178,000** in engineering time.
The system had grown too complex to evolve efficiently.

Their marketing tech platform powered big brands, but schema conflicts caused regular deployment issues, and rollbacks required coordination with the DevOps team.
The Rust-based router took up to 30 minutes to build, and every subgraph change triggered a full supergraph rebuild.

What had worked in the past was now dragging down development.
Fixing it meant building out missing infrastructure around the GraphQL layer; features like authentication, rate limiting, and public/private endpoint separation that required custom workarounds just to keep things running.

They needed an exit before the maintenance cost outweighed the value.

## The Limits of Rust Plugins in GraphQL Gateways

The team’s gateway stack had grown complex.
Authentication lived in Lambdas. 
All the subgraphs were managed in a single GitHub repository, with no [schema registry](https://wundergraph.com/cosmo/features#Schema-Registry) or UI to inspect changes.

Understanding how changes would affect the graph could mean digging through 10,000+ lines of code.
Custom features like authentication had been written in Rust, which slowed development and limited who could contribute.
Rollbacks weren’t simple; they required CI support and often took hours to resolve.
As Karol Krogulec, Senior Engineering Manager at Acoustic, explained, "With Rust, we would still be writing plugins instead of writing code."

That friction added up fast.

{% quote author="Karol Krogulec, Senior Engineering Manager at Acoustic" %}
“Each time a new plugin had to be written, we were losing two weeks of an engineer’s time. It was very limiting. We had to become creative with our architecture just to avoid writing plugins—adding infrastructure components we didn’t really want. The result was a more complex, harder-to-maintain system.”
{% /quote %}

Rate limiting, usage tiers, auth enforcement, and endpoint filtering were all missing.
Building them in Rust would have eaten months of engineering time and tied the team even tighter to a system they already wanted to escape.

{% quote author="Karol Krogulec, Senior Engineering Manager at Acoustic" %}
“With Cosmo, we saved an estimated $178,000 just on building those features. That doesn’t even include the cost of maintaining or supporting them long term.”
{% /quote %}

## What Acoustic Needed in Their GraphQL Gateway

Three priorities stood out.

**First**, they needed better separation between public and private APIs, with built-in rate limiting and throttling.
Their platform served multiple customer tiers, so this was non-negotiable.

**Second**, they needed to move faster. Router builds took 30 minutes, and schema inspection happened through GitHub.
Developing in Rust was slowing down engineers while simultaneously limiting who could contribute.
Acoustic needed visibility, developer-friendly tooling, and a real UI.

{% quote author="Kira Shatskyi, Senior Software Engineer" %}
“Thinking about it now, I cannot imagine how we were able to work on the supergraph schema and subgraphs without Cosmo Studio.”
{% /quote %}


**Third**, they needed a pricing model that fit their business.
Rigid licensing models didn’t match their unpredictable usage patterns or team structure.
Cosmo’s support-based model gave them the flexibility to scale traffic and services without tracking headcount or renegotiating contracts.

That flexibility mattered. It let the platform team stay focused on architecture—not approvals—and kept business decisions aligned with engineering reality.

## How Cosmo Transformed Acoustic’s GraphQL Developer Experience

### **A New Option: Cosmo**

An engineer on the team suggested trying WunderGraph Cosmo.
It was open source, with the core Federation features they’d been piecing together themselves. 
The [docs](https://cosmo-docs.wundergraph.com/) were solid, the setup felt clean, and running it on their own infrastructure gave them full control from day one.

What surprised the team was how smooth the early testing felt.
Pre-prod trials showed real improvements to developer UX, not just rough parity with their existing system, but a noticeably better experience.

The open-source and enterprise offerings shared the same foundations.
That gave Acoustic confidence that they weren’t locking themselves into another brittle vendor setup.

## A Smooth Migration from Rust Router to Cosmo

They didn’t rush. Acoustic ran Cosmo in pre-production for about a month, using the same schema and subgraphs as their legacy system. 
As Kira Shatskyi explained, “The migration was just updating the DNS record from the old router to the Cosmo Router.”

There were edge cases and bugs early on, but support landed fast. 

When the team asked about support for the `@exclude` directive, it was live within three weeks. [Jens Neuse](https://www.linkedin.com/in/jens-neuse-706673195/) even joined the Slack thread.
As Karol Krogulec recalled, “the issue was quickly addressed by the Cosmo team, with the CEO himself writing the code, and we received a PR after just a couple of hours.”

## A Partnership That Delivered Results

{% quote author="Blake Reed, Vice President of Engineering at Acoustic" %}
“The WunderGraph team—and [Stefan Avram](https://www.linkedin.com/in/stefan-avram-62696713a/), their CCO, in particular—has been amazing to work with. They were engaged in our issues, resolved them quickly, and collaborated on best practices. That built a lot of confidence in WunderGraph, especially since this was a new technology for our team.”
{% /quote %}

## The Payoff: A Simpler, Faster System

Cosmo helped them cut complexity fast.
They no longer needed Rust plugins, auth Lambdas, Jenkins pipelines, or manual CI rollbacks.
Platform engineers can now view the full schema visually, eliminating the need to grep through thousands of lines of GraphQL.

"Every subgraph change used to require building and deploying the entire supergraph," said Stefan Hepper, Distinguished Architect from Acoustic. "It was brittle—failures could cost us a full day just to reconcile. With Cosmo, all of that went away."

The Go-based router was fast and familiar.
Cosmo’s support for `@include` and `@exclude` made routing patterns cleaner and more maintainable, especially for legacy and client-specific APIs.

Cosmo didn’t just improve performance, it restored confidence.

{% quote author="Kira Shatskyi, Senior Software Engineer" %}
"Sometimes we forget it exists because it just works."
{% /quote %}


The federated graph was no longer a daily concern—it faded into the background.

The partnership was just as important as the platform.
WunderGraph’s support team answered quickly. Roadmap discussions turned into working features in weeks.
Acoustic didn’t just adopt a new tool; they helped shape it.

{% quote author="Karol Krogulec, Senior Engineering Manager at Acoustic" %}
“I haven’t been so impressed with support from any other provider I’ve worked with.”
{% /quote %}


## Unlocking New API Capabilities with Cosmo

They can now run customer-specific APIs on isolated routers.
Endpoints are taggable and access is controlled; each client sees only what they’re supposed to. Schema rollbacks no longer require CI pipelines; they’re faster, simpler, and safer.

These weren’t bonus features.
They were blockers—and now they’re gone.

Cosmo’s route isolation lets Acoustic ship tailored interfaces without compromising their public APIs.

As Stefan Hepper explained, “the ability to tag methods and deploy them to specific routers—public, private, or for a single client—let us build a one-off interface for a customer without touching our public APIs.”

## Before and After: Acoustic’s GraphQL Federation with Cosmo

| Before Cosmo | After Cosmo |
| :---- | :---- |
| 30-minute builds on Rust router | Fast Go-based router builds |
| 10k+ lines of schema to parse manually | Visual schema explorer via Cosmo UI |
| One GitHub repo for schemas | Clear subgraph separation via schema registry |
| No rate limiting or throttling | Built-in traffic controls |
| Risky public/private overlap | Taggable, isolated endpoints |

## Lessons for Platform Teams Considering GraphQL Federation

Acoustic’s advice to other platform teams: don’t just validate Federation.
Validate everything.
Can you roll back easily?
Is auth built in?
Can you inspect diffs before a schema hits production?

With Cosmo, Acoustic didn’t just sidestep $178K in engineering costs.
They got their time back.
They got simplicity.
And they got a graph that just works.

{% partial file="blog-callout.md" /%}

---

{% faq /%}

---