---
type: blog
title: SoundCloud and WunderGraph Cosmo Cut Computing Costs by 86%
slug: 2025-03-04-soundcloud-wundergraph-cosmo-cut-computing-costs-86-percent
series: WunderGraph Blog
date: 2025-03-04
author: Brendan Bondurant
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - Cost Optimization
  - GraphQL Federation
  - Performance Improvement
  - Infrastructure Efficiency
tags:
  - graphql
  - federation
  - api-management
  - performance
  - cost-optimization
entities:
  - SoundCloud
  - WunderGraph Cosmo
  - GraphQL Federation
  - Infrastructure Costs
summary: |
  SoundCloud achieved an 86% reduction in computing costs by migrating from a third-party GraphQL gateway to WunderGraph Cosmo. The migration reduced CPU usage from 600 vCPUs to 80, saving an estimated $265,000 annually while improving query performance and providing the flexibility of an open-source solution.
faqs:
  - q: What led SoundCloud to migrate away from their previous GraphQL gateway?
    a: SoundCloud's third-party gateway worked initially but introduced high infrastructure costs and risk of lock-in due to enterprise-only features. They needed more flexibility and control over their GraphQL infrastructure without restrictive licensing.
  - q: How did WunderGraph Cosmo help SoundCloud reduce infrastructure costs?
    a: Cosmo reduced CPU usage by 86%, from 600 vCPUs to 80, saving an estimated $265,000 annually. Their overall infrastructure spend dropped from ~$14,000 to ~$9,750 per month even after accounting for other infrastructure components.
  - q: What performance improvements did SoundCloud see after switching to Cosmo?
    a: One high-traffic query related to reactions dropped in latency from 171ms to 94ms (P95). Routing became more efficient, reducing bottlenecks and improving responsiveness across views like track waveforms and comment counts.
  - q: How did SoundCloud approach the Cosmo migration process?
    a: They ran Cosmo alongside their existing gateway to validate schema checks and measure performance. Once confident, they phased out the old gateway and fully transitioned to Cosmo Router.
  - q: Why did SoundCloud prefer an open-source federation router?
    a: Cosmo's open-source model gave SoundCloud full control without enterprise restrictions. They could inspect the codebase, avoid vendor lock-in, and maintain flexibility in how they manage their GraphQL architecture.
  - q: What are SoundCloud's next steps for optimizing GraphQL efficiency?
    a: They plan to implement persisted queries and rate limiting. These changes are expected to reduce query overhead, lower compute costs, and improve security while maintaining performance.
canonical_url: https://wundergraph.com/blog/soundcloud-wundergraph-cosmo-cut-computing-costs-86-percent
---

### TLDR;
#### Challenge
[SoundCloud](https://soundcloud.com/) needed to optimize its GraphQL infrastructure to reduce costs and improve query performance while maintaining scalability and flexibility.
#### Solution
They  migrated to WunderGraph Cosmo, utilizing its open-source model for cost-effective GraphQL Federation without restrictive licensing.
#### Results
Cosmo reduced infrastructure costs by 86%, leading to an estimated annual savings of $265,000. 
It also improved query latency by 45%, enabling a leaner, more scalable system while enhancing performance and developer efficiency.

{% partial file="blog-callout.md" /%}

## SoundCloud & WunderGraph Cosmo Cut Computing Costs by 86%

SoundCloud took a proactive approach to optimize its GraphQL infrastructure, lowering latency for one key query by 45%—from 171ms to 94ms—and CPU usage by 86%—from 600 to 80. 
Based on AWS Fargate pricing in the US-EAST region, this CPU optimization is estimated to save **$265,000** annually in computing costs. 
By refining its architecture and transitioning to Cosmo Router, SoundCloud built a leaner, more scalable system that supports long-term growth while maintaining high performance.

## Choosing the Right GraphQL Strategy
SoundCloud initially relied on a third-party GraphQL Gateway for query execution and API traffic management.
While enterprise features like co-processing and persisted queries were available through the same provider’s enterprise router, adopting it would have increased their dependence on that ecosystem.

When SoundCloud introduced its own gateway, the enterprise router became less critical.
However, the team still avoided migrating, knowing that relying on enterprise-locked features would make future changes more restrictive. 
Instead, they built a schema reporting plugin to track usage metrics while they assessed alternatives.

As they evaluated their options, it became clear that their previous solution would further entrench them in its ecosystem, making future changes more difficult.
They needed a scalable, cost-effective solution that provided full control over their GraphQL infrastructure.

## Evaluating Cost-Saving Alternatives
Building an in-house GraphQL framework seemed like an option. 
On paper, it offered independence and potential cost savings—but the long-term development and maintenance costs outweighed the benefits.

> *Building it ourselves was something we talked about, but the amount of effort required to build and maintain it long term just wasn't worth it.*

— *Tim Caplis, Principal Software Engineer at SoundCloud*

Open-source solutions like The Guild had some of the right components, but it didn’t feel fully integrated for large-scale enterprise needs. 
They also had concerns about the additional support responsibilities required to maintain everything outside the router—something SoundCloud wanted to avoid.


## Decision to Migrate to Cosmo Router
SoundCloud’s original third-party solution worked, but it was proving to be an imperfect long-term fit.
They needed more flexibility—something that wouldn’t lock them into enterprise licensing or restrict their ability to scale.

Seeking alternatives, they evaluated WunderGraph and Cosmo Router, testing whether an open-source alternative could deliver the flexibility and cost savings they needed.
A Proof of Concept (POC) confirmed that Cosmo offered significant performance improvements while reducing infrastructure demands. 
Cosmo’s open-source model ensured SoundCloud retained control over its infrastructure without restrictive licensing requirements.

Beyond the technology, WunderGraph’s collaborative approach stood out. 
They felt more like partners than vendors. 
Confident in both performance and partnership, they made the transition to Cosmo Router.

>*Working with WunderGraph felt like working with another team inside SoundCloud versus having that tension with a vendor*

— *Tim Caplis, Principal Software Engineer at SoundCloud*


## Migration Process

SoundCloud didn’t make the switch overnight. 
They took an incremental approach, running Cosmo alongside their existing federated gateway to test schema checks and track performance.

Early signs were promising: lower infrastructure demands and better efficiency. 
As confidence in the results grew, the old gateway was gradually phased out and replaced with Cosmo’s lightweight alternative.

## Results and Impact

The move to Cosmo delivered exactly what SoundCloud needed—lower costs and better performance. 
Infrastructure costs for computing dropped from ~$14,000 with the original gateway to ~$9,750 with Tyk and Cosmo combined.
More importantly, they achieved this without sacrificing speed or flexibility.

> *Our infrastructure costs went from $14,000 with our previous provider down to $9,750 with Cosmo, even with some extra infra costs.*

— *Tim Caplis, Principal Software Engineer at SoundCloud*

Additionally, optimizing AWS ECS usage reduced infrastructure costs by 86%. 
The new setup runs 10 router containers with 4 vCPUs and 8 GiB memory each, totaling 40 vCPUs and 80 GiB memory. 
Previously, they required up to 600 vCPUs, as it also handled session management, geo lookups, and subscriptions—workloads that have since been offloaded to other services.

By removing unnecessary overhead,  SoundCloud has made its GraphQL routing layer leaner, more efficient, and fully scalable.

The migration reshaped their delivery pipeline.
With a unified graph and reduced operational complexity, teams began shipping features dramatically faster.

> **They now ship features more than three times faster.**  

What started as an infrastructure optimization became a company-wide multiplier for delivery speed and product momentum.



## Improved Performance and Efficiency

Beyond cost savings, migrating to Cosmo delivered significant performance gains. 
Queries now execute faster with lower latency, thanks to more efficient routing and resource allocation. 
With a leaner infrastructure and fewer bottlenecks, SoundCloud has improved response times while reducing the overall computational overhead.

For instance, one reactions-related query saw latency drop from an average of 171ms to just 94ms (P95) in Cosmo.
Because reactions load with every public track, optimizing their query performance directly impacts the responsiveness of high-traffic views like track waveforms and comment counts.
This gives the user a seamless experience and keeps them actively engaged with the content.

> *We knew the router would be more performant, but we didn’t know how much. Now we’re proving that hunch.*

— *Tim Caplis, Principal Software Engineer at SoundCloud*

## Next Steps: Cost-Optimizing Query Handling

Migrating to Cosmo was a significant step forward, but SoundCloud isn’t stopping there. 
With a leaner, more cost-efficient architecture in place, they’re now refining their approach—reducing query overhead, optimizing API traffic, and implementing caching for even greater efficiency.

> *We are really excited to start taking advantage of persistent queries - we expect this to improve efficiency while also making our graph more secure.*

— *Tim Caplis, Principal Software Engineer at SoundCloud*

### Key Initiatives Include:

* [**Persisted Queries**](https://cosmo-docs.wundergraph.com/router/persisted-queries) **:** Lower compute costs by pre-validating and optimizing queries before execution.

* [**Rate Limiting**](https://cosmo-docs.wundergraph.com/router/configuration#rate-limiting) **:** Prevent excessive API traffic, ensuring efficient infrastructure scaling.

These improvements will extend cost savings beyond infrastructure migration by further optimizing request handling and reducing redundant compute cycles.

### Conclusion

Migrating to Cosmo Router allowed SoundCloud to eliminate costly inefficiencies and maintain control over its GraphQL infrastructure. 
By reducing CPU usage, they lowered overall infrastructure costs by 86%, translating into an estimated **$265,000** in annual savings.

Beyond cost reductions, SoundCloud's move away from enterprise-locked features freed it from restrictive licensing models, giving them the flexibility to scale on their terms. 
With ongoing optimization efforts in query handling and caching, SoundCloud is positioned to reduce spending further and improve efficiency without compromising performance.

{% partial file="blog-callout.md" /%}

If you like the problems we're solving and want to learn more about Cosmo Router, check out our [GitHub repository](https://github.com/wundergraph/cosmo)
and take a look at our [open positions](https://wundergraph.com/jobs) if you're interested in joining our team.

---

{% faq /%}

---