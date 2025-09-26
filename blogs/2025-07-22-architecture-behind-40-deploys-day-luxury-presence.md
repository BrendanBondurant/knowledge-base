---
type: blog
title: The Architecture Behind 40 Deploys a Day at Luxury Presence
slug: 2025-07-22-architecture-behind-40-deploys-day-luxury-presence
series: WunderGraph Blog
date: 2025-07-22
author: Brendan Bondurant
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - API Modernization
  - GraphQL Federation
  - Developer Velocity
  - Microservices Architecture
tags:
  - graphql
  - federation
  - api-management
  - bff-pattern
  - supergraph
  - microservices
  - developer-experience
entities:
  - Luxury Presence
  - WunderGraph Cosmo
  - GraphQL Federation
  - BFF Pattern
  - Microservices
  - Nick Tsianos
summary: |
  Luxury Presence scaled from 70+ engineers to 100+ in R&D while increasing deployment frequency to 40 times per day by replacing backend-for-frontend (BFF) layers with GraphQL Federation using WunderGraph Cosmo. The architectural shift eliminated duplication, reduced code reviews from 3 PRs to 1-2 per feature, and enabled faster delivery of a major product launch that would have required additional engineers and sprints under the old system.
faqs:
  - q: How did Luxury Presence increase deployment frequency?
    a: By replacing BFF layers with GraphQL Federation using WunderGraph Cosmo, they eliminated duplication and reduced coordination overhead, enabling up to 40 production releases per day.
  - q: What was the impact on code reviews?
    a: Code reviews shrank from 3 PRs per feature to just 1 or 2, significantly reducing review overhead and accelerating development cycles.
  - q: How did the architecture change affect new engineers?
    a: New engineers now start in the unified graph layer rather than legacy BFFs, with Cosmo's visual tools helping build shared understanding of the federated system.
canonical_url: https://wundergraph.com/blog/architecture-behind-40-deploys-day-luxury-presence
---
## **TL;DR:**

[Luxury Presence](https://www.luxurypresence.com/) outgrew its backend-for-frontend (BFF) layers as the team scaled past 70 engineers. To eliminate duplication and move faster, they adopted WunderGraph Cosmo. Now they share logic across teams, review changes in one place, and deploy up to 40 times a day, launching features faster with fewer engineers.

{% currentcallout title="One Graph, Shared Velocity" %}
Luxury Presence is unifying its architecture on WunderGraph Cosmo to support faster delivery across 50,000+ customer sites.
{% /currentcallout %}


## **Scaling Teams, Splintering Architecture**

Luxury Presence powers over 50,000 websites for real estate agents through a sophisticated, multi-tenant platform tailored to the real estate industry. Its application model was built around a three-tiered structure: Frontend applications (web and mobile), backend-for-frontends (BFFs), and domain services accessed via REST. Originally coined at SoundCloud, the [BFF pattern](https://philcalcado.com/2015/09/18/the_back_end_for_front_end_pattern_bff.html) gives each frontend a custom backend layer to tailor logic and fetch data efficiently.

BFFs were originally tailored to each application’s unique needs, but over time, their divergence made coordination harder. Different teams adopted different GraphQL implementations—some used Yoga, others Nexus. The layering once helped isolate frontend concerns, but as product scope grew, logic spread with similar features appearing in multiple applications, and duplication increased. For example, chat message creation involved three duplicated mutations across the client mobile app, the real estate dashboard, and internal tooling, all with the potential for slight differences. “*The BFF started to feel like this unnecessary transformation layer,*” said Nick Tsianos.

{% quote author="Nick Tsianos, Chief Architect at Luxury Presence" %}
There really was no such thing as application business logic anymore, just domain business logic.
{% /quote %}

As the team grew past 70 engineers and over 100 in R\&D, new challenges emerged. Working across the frontend, BFF, and domain layers slowed developers down. Meanwhile, customer expectations continued to rise.

## **The Breaking Point: Three Forces Converge**

By early 2025, three pressures collided.

First came a high-stakes deadline. Luxury Presence was preparing to launch into a brand new product space. The new features would be rolled out to all of their customers, and also required a rewrite of the homepage that all customers interface with. That made it a special opportunity to build something new from the ground up to test new ideas. For a new product, internal quality, including the ability to rapidly iterate on the code, scalability, limited bugs, and security, was paramount. 

The second was an ongoing shift toward engineering efficiency. Developers were spending too much time wiring systems instead of shipping features. However, the architecture, although once effective, made even routine tasks harder.

{% quote author="Nick Tsianos" %}
We were duplicating effort, reviewing three PRs instead of one.
{% /quote %}


The third force was the rise of AI in the engineering workflow. Luxury Presence was actively experimenting with internal AI agents to automate boilerplate work from their backlog. However, the stack’s complexity added friction, even for internal AI agents. 

> *"AI now needs to know how to write for the frontend, the BFF, the domain … and each of those has different rules and build steps."*


Together, these forces made inaction more costly than change. The team began simplifying its architecture to reduce friction and move more quickly.

---

## **Re-Architecting for Velocity: Why Cosmo Made the Difference**

The team’s goal was to unify frontend and backend development under a single graph. But they didn’t want a full rewrite. They needed an approach that supported progressive migration, not a sudden shift.

That’s where WunderGraph Cosmo came in. “*I just liked the approach from WunderGraph*,” said Tsianos. “*It felt optimized for the kind of development we were trying to do.*” Discovered through AI-assisted research, Cosmo quickly stood out for its developer-first tooling and clear documentation.

> *"At the start, we had a Slack channel to call out the new subgraphs as we published them by service. Allowing the team to see the supergraph take shape on Cosmo Studio in real time."*

Even with initial apprehension, the learning curve was manageable.

{% quote author="Nick Tsianos" %}
It was remarkably easy to get off the ground.
{% /quote %}


Cosmo allowed them to pursue an in-place migration, moving module by module without needing to fork or proxy services. They’re progressively replacing REST endpoints with GraphQL interfaces using shared [TypeScript](https://www.typescriptlang.org/) types across services. Each BFF operation was audited individually. The team determined whether the logic involved data access, policy enforcement, or transformation and routed it accordingly to domain services, reusable middleware, or UI formatting helpers.

{% partial file="blog-callout.md" /%}

## **Solving Technical and Organizational Challenges**

The architecture shift unlocked broader consistency. In parallel, the team rolled out a monorepo strategy, standardized tooling, and revamped their release process. The infrastructure improvements, combined with reduced friction, let teams reach up to 40 production releases per day.

Cosmo’s visual schema tools made subgraph relationships immediately clear. This helped teams reason about how their parts of the system connected, without needing deep experience in GraphQL internals.

{% quote author="Nick Tsianos" %}
You log in, click on a graph, and see the supergraph with the subgraphs and the dotted lines.
{% /quote %}

Luxury Presence also extended Cosmo’s CORS support in Go to meet the needs of its multi-tenant setup. When the migration is complete, Cosmo will act as the GraphQL gateway serving federated traffic for over 50,000 customer websites. Traces are piped into Datadog for visibility into routing and performance.


## **Outcomes: Measurable Gains Across the Stack**

The new product was launched in July 2025\. Tsianos credits the faster delivery to architectural improvements that avoided the BFF layer. Under the old model, it would have needed at least one more engineer and at least an extra sprint. “*Everything had to go right,*” said Tsianos. “*And it did.*”

Developer velocity improved noticeably, especially in reviews and releases, based on onboarding feedback and team observation. Code reviews now involve one or two PRs instead of three. Feedback loops shortened across the board as a result. Review and release paths converged, allowing full-stack engineers to own features from end to end.

{% currentcallout title="Fewer PRs, faster merges" %}
Code reviews shrank from 3 PRs per feature to just 1 or 2.
{% /currentcallout %}

Cosmo is already reshaping onboarding. New engineers now start in the unified graph layer, rather than the legacy BFFs.

> *"It’s extremely rare for somebody to be familiar with federated GraphQL. Visualization helps build shared understanding."*


Migration work became an opportunity to pay down technical debt. Query by query, the team fixed legacy quirks that had piled up over time. “*It’s not a full rewrite,*” said Tsianos. “*But every query, you’ll find some strange implementation detail that now you have a chance to revisit. We thought we had rigor around details like dataloaders, but found situations still requiring up to 10 API calls. Those are now a single GraphQL query*”.

{% currentcallout title="Unified onboarding path" %}
New engineers skip legacy BFFs and start in the federated graph layer.
{% /currentcallout %}


## **Reflections and Takeaways**

For Luxury Presence, Cosmo didn’t just fix the stack. It reinforced the culture behind it. While other platforms felt built for architects and removed from practical development challenges, Cosmo felt purpose-built for product teams.

{% quote author="Nick Tsianos" %}
It felt optimized for full-stack feature developers. That’s who we were choosing our technologies to support.
{% /quote %}

As a bonus, using Cosmo for the supergraph unifies GraphQL tooling and ensures that only backward-compatible changes are published by subgraphs, ultimately reducing the surface area of change risk.

Visualization helped make federation real. Cosmo [Studio](https://cosmo-docs.wundergraph.com/studio/overview-page) gave teams a shared view of the supergraph, subgraphs, and their relationships. It turned abstract concepts into operational clarity.

And throughout the process, the support stood out. “*When Viola, the Customer Success Manager at WunderGraph, said I could send feedback, I felt like she genuinely meant it,*” Tsianos said. “*It wasn’t just a sales pitch. It was legitimate care about the product and about the space.*”

Luxury Presence entered the year facing three core challenges: a complex launch, growing operational friction, and a development model that no longer scaled. They shipped the launch, reduced friction, and began unifying their stack on their terms.

{% quote author="Nick Tsianos" %}
By the end of the year, I’m aiming for a significant overhaul—where new engineers won’t have to touch the BFF at all.
{% /quote %}

By simplifying coordination, Cosmo gave the team back its speed—and its focus.

---

**Note:** All quotes in this case study are from Nick Tsianos, Chief Architect at Luxury Presence.

