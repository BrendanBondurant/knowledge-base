---
type: blog
title: Safeguarding APIs: How K Health Ensures Security While Scaling with Cosmo
slug: 2025-03-11-safeguarding-apis-k-health-ensures-security-scaling-cosmo
series: WunderGraph Blog
date: 2025-03-11
author: Brendan Bondurant
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - API Security
  - GraphQL Federation
  - Healthcare Compliance
  - Scalability
tags:
  - graphql
  - federation
  - api-management
  - security
  - healthcare
entities:
  - K Health
  - WunderGraph Cosmo
  - GraphQL Federation
  - HIPAA
  - Schema Validation
summary: |
  K Health streamlined its API architecture with GraphQL Federation and Cosmo, enhancing security, scalability, and collaboration across teams. By self-hosting the Cosmo router to meet HIPAA requirements and leveraging schema checks for breaking change detection, K Health achieved better API stability, improved performance, and enabled non-engineers to query the graph directly.
faqs:
  - q: How does K Health catch breaking changes in their GraphQL schema?
    a: K Health uses Cosmo's schema checks to detect breaking changes early in CI/CD. These checks catch issues like missing fields, unexpected type changes, and null pointer risks before they reach production.
  - q: Why did K Health choose to host the Cosmo router themselves?
    a: To meet HIPAA requirements, K Health hosts the Cosmo router inside their own infrastructure. This ensures that sensitive healthcare data never leaves their environment, and that WunderGraph has no access to any traffic or payloads.
  - q: What does Cosmo's Config Validation and Signing do?
    a: Cosmo's Config Validation and Signing ensures that only verified router configurations are applied. Signatures are checked during deployment, and webhooks confirm authenticity before updates go live, which helps prevent unauthorized or corrupted changes.
  - q: How did Federation improve K Health's API stability?
    a: By using Cosmo for GraphQL Federation, K Health eliminated the need for multiple OpenAPI clients and redundant middleware. Schema validation ensures data consistency across services, and unified types reduce runtime serialization and deserialization errors.
  - q: Can non-engineers query the graph directly?
    a: Yes. With Cosmo Playground, non-engineers at K Health can generate tokens and run their own queries. This allows them to verify data independently and provide more accurate bug reports to engineering.
  - q: What performance improvements did K Health see with Cosmo?
    a: Large queries that previously required multiple round trips now resolve internally within the Cosmo router. This reduces latency and makes the experience feel faster to consumers, even if backend execution times are unchanged.
canonical_url: https://wundergraph.com/blog/safeguarding-apis-k-health-ensures-security-scaling-cosmo
---

## TLDR;
### Challenge
K Health needed a way to scale securely while keeping their microservices connected and API stable.

### Solution
They adopted GraphQL Federation with Cosmo, leveraging schema checks to catch breaking changes early and hosting the router internally to maintain security and control.

### Results
Queries now resolve more efficiently, reducing unnecessary round trips, while schema validation prevents disruptions.
Engineers can work faster with more reliable data, and non-engineers can verify information independently, making collaboration smoother across teams.

{% partial file="blog-callout.md" /%}

## How K Health Ensures Security While Scaling with Cosmo

Security is always a challenge in the healthcare industry.
With strict HIPAA regulations, companies must maintain current standards while scaling to meet new ones without letting existing security measures become outdated.

K Health currently uses the Cosmo router as a proxy between subgraphs while relying on their own security protocols.
By hosting the router within their infrastructure, sensitive data never leaves their environment, and WunderGraph has no access to the information being processed.

## Why Federation? 

A few years ago, K Health pivoted to a new business model, which required phasing out several existing microservices while introducing new ones.
To avoid disruptions, both old and new services needed to coexist during the transition.

The previous architecture relied on services communicating through OpenAPI specs and generating client libraries in multiple languages, such as TypeScript and Python.
Each service often required numerous foreign clients—sometimes up to 10—leading to additional middleware for authorization, language handling, and more.

> *"Every service would have more than 1, 2, or sometimes up to 10 foreign clients installed. You would have to add middleware into each and every client."*

— *Maksym Komarychev, Principal Engineer at K Health*

With teams distributed globally, building a unified API surface was critical to improving communication and collaboration.
The main challenge was ensuring the system was easy to understand and manage across teams.

Leadership identified GraphQL Federation as a potential solution, influenced partly by the CTO’s prior experience with Federation.
As Maksym (Principal Engineer) said, “*We wanted to use it as an abstraction layer on top of our microservices*”, which would make integrating new services into the graph easier.

## Why Cosmo?

After exploring various federated solutions, K Health ultimately chose Cosmo.
But how did they get there?

At the beginning of this process, they built a basic router and schema management service to test GraphQL Federation and determine its feasibility.
Because Cosmo is open source, they could experiment with it before formally engaging with WunderGraph.
While K Health ultimately preferred a professionally managed service to avoid maintenance overhead, this hands-on phase allowed them to confirm that Cosmo was the right choice.


Cosmo proved easy to set up, whether on a local machine or in a Kubernetes pod.
With no contract or trial limitations, K Health could thoroughly experiment with the router.
This flexibility made internal buy-in easier, as developers could experience and test its capabilities before committing to adoption.

### Impact
API stability is a top priority for K Health, and Cosmo’s schema checks have significantly improved this.
Before adopting Cosmo, breaking changes were more challenging to catch and occurred more frequently.

Some of the consequences included:
- Null pointer exceptions and similar runtime issues
- Missing fields or unexpected type changes (e.g., a string becoming a boolean)
- Errors arising from requests fanning out to multiple backend services
- Corrupted or inconsistent data requiring additional validation
- JavaScript objects that can't be trusted at runtime, even with TypeScript interfaces, requiring extra runtime checks

Cosmo’s schema checks help catch these issues early.
While breaking changes are still possible, they are much easier to identify. 


> *"The checks that Cosmo does is a super great thing to have. I’m referring to actual checks on the real traffic."*

— *Maksym Komarychev, Principal Engineer at K Health*

The Cosmo router ensures data integrity, giving developers confidence that it will work at runtime if the code compiles locally.
With schema checks, automated testing becomes more efficient and reliable while requiring fewer redundant checks.
Serialization and deserialization no longer require double testing because they trust the graph’s structure.

## Config Validation and Signing

K Health uses Cosmo’s [Config Validation and Signing](https://cosmo-docs.wundergraph.com/router/security/config-validation-and-signing) to enhance security by ensuring only validated configurations are applied.
Config files are signed, and the router verifies these signatures during deployment to prevent unauthorized changes.
Signature Webhooks add another layer by sending signed payloads during updates, ensuring authenticity before applying changes.
Together, these features catch errors early, protect against tampering, and maintain a secure, stable GraphQL infrastructure.

{% video autoPlay=true loop=true src="/videos/config_validation.mp4" /%}

## Business Impact
One of K Health's most significant improvements has been handling large queries.
Before Cosmo, large queries required multiple round trips to gather all necessary data.
Now, with query resolution handled internally within the router, responses feel faster to consumers, even if the component-level execution times remain the same.

> *"When we do one large query, we avoid doing round trips. From the consumer perspective, it's faster because all the resolution is happening internally behind the router."*

— *Maksym Komarychev, Principal Engineer at K Health*

Cosmo has dramatically improved internal workflows, especially for non-engineering teams.
Non-engineers can now log into Cosmo Playground, generate tokens, and run queries, allowing them to verify data discrepancies independently and produce more accurate bug reports.

> *"This means better bug reports from non-engineers because they can now verify data discrepancies themselves."*

— *Maksym Komarychev, Principal Engineer at K Health*

Having a unified API surface has also improved communication.
Previously, different services handling the same entity (e.g., “patient”) often used different field names and structures.
Now, every team references the same entity in the same format, saving time and reducing errors.

On the technical side, tracking upgrades and breaking changes is much easier.
If an update breaks something, the affected service’s pipeline fails immediately, making issues easier to catch and fix without digging through logs.

## The Future of WunderGraph and K Health
K Health continues to expand its infrastructure.
What began with only 3–4 subgraphs has now grown to nearly 10, with more to come.
GraphQL Federation has become a crucial component of their architecture as they phase out legacy services and integrate new ones.

Through their collaboration with WunderGraph, K Health has gained more than just a tool—they've gained a partner.
The ability to quickly reach out for support and receive meaningful, actionable guidance has been instrumental in their success.
As their needs evolve, K Health is well-positioned to continue leveraging Cosmo’s capabilities for stability, security, and future growth.


If you like the problems we're solving and want to learn more about Cosmo Router, check out our [GitHub repository](https://github.com/wundergraph/cosmo).
Interested in exploring GrahpQL Federation?
Let’s connect and explore the most efficient approach for your team—[book a time with us!](https://cal.com/team/wundergraph-sales/introduction-call)


---

{% faq /%}

---