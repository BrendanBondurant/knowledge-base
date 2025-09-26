---
type: blog
title: From Custom Code to Cutting-Edge: On The Beach Adopts WunderGraph Cosmo for GraphQL Federation
slug: 2025-02-03-custom-code-cutting-edge-beach-adopts-wundergraph-cosmo-graphql-federation
series: WunderGraph Blog
date: 2025-02-03
author: Stefan Avram
co_author: Brendan Bondurant
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - Performance Improvement
  - Developer Velocity
  - Observability
tags:
  - graphql
  - federation
  - api-management
  - performance
  - developer-experience
entities:
  - On The Beach
  - WunderGraph Cosmo
  - GraphQL Federation
  - Event-Driven Federated Subscriptions
  - Schema Registry
summary: |
  UK travel giant On The Beach replaced their custom GraphQL Federation setup with WunderGraph Cosmo, dramatically improving performance, observability, and developer velocity. The migration automated schema composition, enabled real-time subscriptions through EDFS, and provided advanced request tracing capabilities that helped optimize queries and reduce latency.
faqs:
  - q: Why did On The Beach move away from their custom Federation setup?
    a: Their schema stitching and Apollo Rover–based setup became hard to maintain as the graph grew. It introduced operational overhead, bottlenecks, and slow rollouts, prompting the shift to WunderGraph Cosmo.
  - q: How did Cosmo improve performance and developer velocity?
    a: Cosmo automated schema composition and validation, reducing manual overhead. Tools like the Schema Registry and Cosmo Studio helped teams own their subgraphs independently, speeding up development and reducing conflicts.
  - q: What is Event-Driven Federated Subscriptions (EDFS), and how does On The Beach use it?
    a: EDFS lets the Cosmo router push real-time GraphQL subscription updates efficiently using a publish-subscribe model. On The Beach uses it for time-sensitive data like booking confirmations and pricing updates.
  - q: What benefits did On The Beach see from self-hosting the Cosmo router?
    a: Self-hosting gave them more control over networking, performance tuning, and cost. They reported faster response times and better resource efficiency compared to managed federation routers.
  - q: How does Advanced Request Tracing help On The Beach?
    a: Cosmo's Advanced Request Tracing visualizes query execution paths and performance metrics. It helped the team optimize slow queries, debug production issues faster, and improve conversion by reducing latency.
  - q: What role did open source play in their decision?
    a: Cosmo's open-source model allowed On The Beach to audit the codebase, contribute features, and deeply understand how federation worked. This transparency gave them confidence and flexibility in adoption.
canonical_url: https://wundergraph.com/blog/custom-code-cutting-edge-beach-adopts-wundergraph-cosmo-graphql-federation
---

{% partial file="blog-callout.md" /%}

## TLDR;
### Challenge
On The Beach’s monolithic GraphQL API became a performance bottleneck as travel demand surged post-COVID, making it difficult to scale and iterate efficiently.
### Solution
To improve scalability, they initially built a custom GraphQL Federation but found it difficult to maintain. Adopting WunderGraph Cosmo enable a more streamlined and efficient Federation strategy, simplifying API management and reducing operational complexity.
### Results
WunderGraph Cosmo improved scalability, reduced infrastructure costs, and enhanced developer experience with streamlined schema management and advanced request tracing. The Cosmo router also delivered noticeable performance gains, making real-time features more reliable. 

---

## On the Beach 
Founded in 2004, On The Beach has established itself as a leading force in the UK travel industry. 
By offering a wide array of travel services, the company provides a comprehensive solution for holidaymakers seeking convenience and quality. 
Specializing in Europe’s most popular beach destinations, On The Beach ensures exceptional value for its customers by leveraging its self-contracted hotel network to secure premium accommodations at competitive rates.

On The Beach’s dedication to transparency and trust has made it a household name in the travel sector. 
As a publicly listed company on the London Stock Exchange, its financial stability and credibility are matched by a secure booking platform, transparent pricing, and 24-hour resort support—building confidence and loyalty among travelers.

With an intuitive online platform that simplifies holiday planning and customization, On The Beach prioritizes customer experience through continuous innovation. 
Averaging 4 billion monthly clicks, the company continuously evolves to ensure a seamless, stress-free travel experience, offering peace of mind on every journey.


## Challenge: Modernizing On The Beach and Overcoming Bottlenecks with GraphQL Federation

As digital demand soared during the COVID-19 pandemic, On The Beach embarked on a platform overhaul, adopting a microservices architecture with GraphQL at its core. 
The transition coincided with a global halt in travel, giving the team a unique opportunity to experiment with new technologies. 

Initially, GraphQL was used in a limited capacity for backend communication between services. 
It served as a tool to facilitate data sharing, but its potential for broader application was not fully realized.
GraphQL was chosen to be the core of their Universal API for its natural-language-like structure, making it more accessible to both engineers and non-technical stakeholders.

The modernization effort was led by Stephen Wootten, Senior Software Engineer, and Craig Bradley, Principal Software Engineer. 
The team set out to integrate their services into a single GraphQL API, aiming to replicate existing functionality. 

> The Graph API slowly started to form into a monolith API which introudced a lot of pain points and bottlenecks for our team. With that in mind, we started to look into GraphQL Federation.

- Stephen Wootten, Senior Software Engineer, OnTheBeach.com

The engineering team quickly built a strong foundation for the company’s GraphQL API, integrating existing services and defining domain objects with a thoughtful approach. 
As the graph grew, so did the complexity of its design, requiring decisions across diverse business areas such as Flights, Hotels, and Transfers. 
Without deep domain knowledge in every area, the team adapted by collaborating with experts and iterating on their models. 
However, as the API became central to new feature development, some changes—like modifying search functionality or introducing new filters—required extensive coordination with upstream teams. 
These experiences shaped the team’s understanding of GraphQL at scale and reinforced the importance of aligning API design with domain expertise.

> Initially, we struggled to even document requirements because we couldn’t get all three teams in the same room—each had different priorities. Now, when a new feature is proposed, we simply bring in the frontend team and the domain team, define the requirements, draft a schema, and if everyone agrees, we begin development. This process has dramatically reduced the time required to release new features.

- Stephen Wootten, Senior Software Engineer, OnTheBeach.com

Recognizing these limitations, On The Beach turned to GraphQL Federation as a solution. 
However, existing federation tools lacked the flexibility they needed, prompting the team to initially build their own solution, which introduced its own set of challenges.

## Initial Solution: Schema Stitching and Its Limitations

On The Beach’s first attempt at federation relied on schema stitching, supported by Apollo Rover and a schema registry hosted in GitLab. 
The federated schema was exposed via a custom gateway application. 
Initially, this solution allowed the team to connect services and structure their API as needed.

However, as the graph expanded, the system struggled to keep up. 
Managing multiple schemas became increasingly complex and error-prone, leading to scalability issues. 
Dependencies between schemas created bottlenecks, forcing engineers to spend significant time resolving inconsistencies rather than building new features.

> We started building our own Federation Solution. We ended up implementing a home baked solution utilizing Apollo Rover and schema stitching. It worked for a while, but as we grew, it became more and more difficult to maintain, and harder for teams to adopt. We decided to look for a better solution.

-Stephen Wootten, Senior Software Engineer, OnTheBeach.com

The homebrewed setup also introduced operational overhead. Each addition to the graph increased complexity, slowing progress and making feature rollouts difficult. 
While workable in the short term, it became clear that this solution could not support long-term scalability. 
The team recognized the need for a more robust and maintainable federation strategy.

## Transition to WunderGraph Cosmo

> The initial attractions around WunderGraph were due to the fact that it was open source. It was useful and transparent that we were able to see exactly how Cosmo was implemented and how it worked. If we had any problems or questions, we were able to look at the code and understand it.

-Stephen Wootten, Senior Software Engineer, OnTheBeach.com

Unlike their homebrewed schema stitching solution, Cosmo offered automated schema composition and management, reducing complexity and operational overhead. 
Additionally, Cosmo’s open-source nature provided full transparency, allowing engineers to review and understand the codebase. 
This transparency enabled the team to actively contribute to Cosmo’s development, fixing bugs, adding features, and refining documentation to suit their needs.

The migration to Cosmo was carried out incrementally over a month, with subgraphs transitioned one at a time. 
This step-by-step approach minimized risks and ensured that core functionality remained intact throughout the process. 
By migrating in stages, the team was able to iteratively refine their federation strategy and address issues as they arose, reducing the likelihood of disruptions.

### Why Cosmo?
Cosmo's suite of tools, including the Schema Registry and Cosmo Studio, transformed how teams collaborated by providing a centralized and intuitive interface for schema management. 
This enabled teams to version, validate, and update schemas independently while ensuring consistency across the graph. 
As a result, domain-specific teams could take ownership of their subgraphs, reducing reliance on a central bottleneck and fostering a more decentralized and efficient workflow.

Cosmo’s feature-rich toolkit addressed many of On The Beach’s challenges:
- **Event-Driven Federated Subscriptions** enabled efficient real-time data handling, critical for time-sensitive interactions like booking confirmations and pricing updates.
- **Advanced Request Tracing (ART)** provided deep visibility into query execution, helping engineers identify and resolve performance bottlenecks quickly.
- **Schema Registry** centralized schema management, streamlining validation and updates, and reducing errors.
- **Cosmo CLI** simplified routine tasks like schema validation and API updates, empowering developers to focus on innovation.

A significant benefit of Cosmo’s open-source model was the ease of conducting security audits. 
On The Beach could thoroughly examine the codebase and provide feedback, fostering a stronger partnership with WunderGraph. 

The WunderGraph team played an active role throughout the migration process.
They worked alongside On The Beach’s engineers to refine their federation strategy, providing hands-on guidance to resolve technical challenges and ensure smooth integration. 
WunderGraph’s responsiveness and expertise allowed On The Beach to adapt quickly and gain confidence in the platform’s ability to meet both immediate and long-term goals.

> Self Hosting the cosmo router allows us to have more control over our performance, the running costs, networking, tuning of the self hosted router gives us better response times and performance for our website, vs if we used a managed router

-Stephen Wootten, Senior Software Engineer, OnTheBeach.com

{% image caption="WunderGraph Cosmo Hybrid Reference Architecture" width="360" height="183" alt="" src="/images/blog/otb_case_study/hybrid_ref_architecture.png" /%}

### Event-Driven Federated Subscriptions: A Game Changer for On The Beach
[Event Driven Federated Subscriptions](https://wundergraph.com/cosmo/features#Event-Driven-Federated-Subscriptions-EDFS) has revolutionized how On The Beach handles real-time data, making it more scalable and efficient than ever before. 
By leveraging a powerful publish-subscribe pattern, the Cosmo router acts as a central broker, seamlessly pushing subscriptions to the relevant services as they are created. 
This architecture allows On The Beach to distribute GraphQL subscriptions more efficiently across their ecosystem.

For On The Beach, this feature has been a game changer, enabling them to scale their operations effortlessly while powering the success of their real-time features. 
The impact has been nothing short of transformative, allowing them to innovate faster and deliver better experiences to their customers. 

{% image caption="EDFS Diagram" width="360" height="183" alt="" src="/images/blog/otb_case_study/edfs.png" /%}

### Advanced Request Tracing: Boosting Performance and Profitability for On The Beach
Advance Request Tracing allows for faster and more accurate debugging of production issues. 
With ART, the Cosmo router traces each request and provides developers with a clear view of the query plan within the Cosmo Studio, allowing for a deeper understanding of how queries are executed. 
This insight is crucial for optimizing queries, improving data loading strategies, and preventing both over-fetching and under-fetching of data.

For a high-traffic e-commerce site like On The Beach, this is invaluable. 
By eliminating slow queries and improving loading times, ART has helped boost overall performance and reliability, ensuring a smoother experience for customers. 
This, in turn, directly impacts revenue, as faster and more efficient query execution means less friction for users and higher conversion rates. 
In short, ART isn’t just a performance tool—it’s a profit-driving asset.

> Now, Cosmo presents all the relevant stats—how many queries run, their response times, and key performance metrics—making it much easier to communicate what's happening under the hood. This improved observability not only enhances request tracing but also helps teams understand how their queries run in a federated system. Ultimately, Cosmo has made it much easier for teams to buy into Federation.

-Stephen Wootten, Senior Software Engineer, OnTheBeach.com


**Advanced Request Tracing in WunderGraph Cosmo:**

{% video autoPlay=true loop=true src="/videos/ART.mp4" /%}



### Schema Registry: Streamlining API Development and Unlocking Efficiency for On The Beach
With the introduction of a [schema registry](https://wundergraph.com/cosmo/features#Schema-Registry), On The Beach transformed how they manage their GraphQL schemas. 
By centralizing schema management, they gained the ability to version schemas more efficiently, maintain them in a single location, and have a clear, comprehensive view of their entire API ecosystem. 
Paired with the [Cosmo Studio](https://cosmo-docs.wundergraph.com/studio/intro) and [Cosmo CLI](https://cosmo-docs.wundergraph.com/cli/intro), this setup streamlined the entire process of building and maintaining GraphQL APIs, eliminating the bottlenecks they faced with their previous home-built solution.

For an e-commerce platform, this level of efficiency is vital. 
By simplifying schema management and accelerating development workflows, On The Beach could deploy new features faster, ensuring their platform stayed responsive and adaptable to market demands—ultimately driving better customer experiences and higher revenue potential.

**The WunderGraph Cosmo Schema Registry in action:**

{% video autoPlay=true loop=true src="/videos/SchemaRegistry.mp4" /%}

## Results
The migration to WunderGraph Cosmo brought transformative improvements to On The Beach’s platform. 
Technically, the switch reduced latency by tens of milliseconds, ensuring faster response times during peak traffic periods. 
The hybrid federated architecture proved scalable, allowing the platform to handle significantly higher traffic with fewer resources. 
Features like Event-Driven Federated Subscriptions enabled near-instant booking confirmations and dynamic pricing updates without adding complexity to backend operations.

One of the most impactful results was the elimination of technical debt accumulated during the monolithic GraphQL API era. 
The monolithic architecture had centralized control over schemas, which created bottlenecks as teams needed to coordinate changes across domains. 
By transitioning to a federated approach, On The Beach delegated responsibility for specific domains—such as Flights, Hotels, and Transfers—to the appropriate teams. 
This not only distributed ownership but also empowered domain teams to iterate independently, reducing the bottlenecks that previously delayed feature rollouts. 
By breaking apart the monolith, the team achieved a cleaner, more maintainable architecture that aligned with long-term scalability goals.

Operationally, developer workflows were streamlined significantly with Cosmo’s suite of tools. 
Cosmo Studio, in particular, improved cross-team collaboration by offering a shared view of the entire graph. 
Teams could track schema changes in real time, identify potential conflicts, and resolve issues collaboratively before deployment. 
This transparency not only reduced delays but also increased confidence across teams, enabling faster and more coordinated feature rollouts. 
The introduction of the Cosmo CLI simplified routine tasks like schema validation, API updates, and deployment processes, empowering engineers to focus on building features rather than troubleshooting inconsistencies.
Additionally, Cosmo’s Schema Registry centralized schema management, eliminating bottlenecks and reducing the time spent resolving dependencies between teams.

{% image caption="Workflow Before and After Cosmo" width="360" height="183" alt="" src="/images/blog/otb_case_study/workflow_diagram.png" /%}

From a business perspective, these changes made user interactions smoother and faster, which led to higher engagement and conversion rates. 
By optimizing infrastructure, the company reduced operational costs while maintaining high performance. 
These outcomes positioned On The Beach for long-term scalability and competitiveness in the travel industry.

Beyond the immediate technical and operational gains, Cosmo’s observability features provided engineers with deeper insight into query performance and execution. 
This increased transparency improved debugging processes and made it easier for new teams to understand and adopt GraphQL Federation. 
By lowering the barrier to entry, On The Beach accelerated the pace of onboarding and collaboration, ultimately driving innovation across the organization.

> The barriers to adoption have significantly decreased with Cosmo. Now, instead of trying to explain the graph, we can simply point people to a product that visualizes it, provides real-time checks in a user-friendly UI, and offers clear insights.

- Stephen Wootten, Senior Software Engineer, OnTheBeach.com

By offloading outdated functionality and distributing responsibilities to domain-specific teams, On The Beach also improved scalability and reduced maintenance burdens. 
Teams could now work independently on their areas of expertise, leading to faster development cycles and fewer cross-team dependencies. 
This shift not only increased efficiency but also laid a foundation for sustained innovation and growth.

>As we engineer new features, the product team has started mapping out user journeys in greater detail. For example, they’re designing a roadmap where customers have a wallet that holds vouchers, each containing specific attributes and functionality. In doing so, they’re essentially defining the structure of our GraphQL schema for us. These product-driven models naturally translate into our domain models, allowing engineers to focus on implementation rather than interpretation.

-Stephen Wootten, Senior Software Engineer, OnTheBeach.com

## Partnership Value
One of the most crucial aspects of On The Beach’s decision to choose WunderGraph was the exceptional support they received. 
The WunderGraph team provided hands-on guidance, ensuring that On The Beach's transition to federation was smooth. 
Their responsiveness allowed the On The Beach engineering team to focus on innovation rather than troubleshooting, accelerating the platform’s transformation.

> We've got a really good relationship with the WunderGraph team. They've been incredibly responsive, often addressing our concerns within minutes. They're always on hand to help and provide guidance, genuinely interested in the solutions we are building and always open to sit down and discuss our graphql federation strategy. Anytime we've spotted an issue or had a question, the WunderGraph team acted instantly and kept us up to date with the progress. One of the biggest benefits is that their is a lot of new features being developed and it's exciting to be involved in that through their RFC process.

-Stephen Wootten, Senior Software Engineer, OnTheBeach.com

The collaboration between On The Beach and WunderGraph was instrumental in the success of their platform transformation. 
WunderGraph’s open-source framework provided the flexibility and transparency needed to tailor the solution to On The Beach’s unique requirements. 
This approach empowered the engineering team to maintain complete control over their infrastructure while benefiting from a robust and scalable architecture.

By working closely with WunderGraph, On The Beach not only resolved immediate technical challenges but also laid the groundwork for sustained innovation. 
This collaboration exemplifies how a flexible and cooperative approach can empower businesses to overcome complex problems, ensuring they remain competitive in a rapidly changing landscape.

## Strategic Benefits and Future Plans

The transition to WunderGraph Cosmo marked a turning point for On The Beach, transforming their GraphQL architecture into a scalable, efficient, and future-ready solution. 
By addressing key challenges like schema complexity and operational bottlenecks, Cosmo improved both developer productivity and customer experience.

Looking ahead, On The Beach plans to deepen their use of Cosmo’s features to continue enhancing real-time data capabilities. 
Event-Driven Federation Subscriptions will support more dynamic and personalized customer interactions, while ongoing optimizations in query execution and schema management will ensure the platform remains adaptable to evolving business needs. 
The team is also exploring ways to extend Cosmo’s hybrid architecture, balancing self-hosted infrastructure with managed services for scalability and cost efficiency.

As WunderGraph evolves, On The Beach continues to play an active role in shaping GraphQL Federation enhancements. 
On The Beach was instrumental in helping develop [Graph Pruning](https://cosmo-docs.wundergraph.com/studio/graph-pruning) and Garbage Collection, features that streamline the API development process further.

With Cosmo as a foundation, On The Beach is well-positioned to continue innovating rapidly, meeting growing customer expectations and expanding into new markets. 
Their hybrid setup provides the flexibility and reliability needed for sustained growth, ensuring their platform remains a competitive edge in the travel industry.


## Video testimony
If you prefer watching to reading, you also have the option to view this case study as a video: 

{% youtube videoId="_ERP1Kq9h1A" /%}


---

{% faq /%}

---