---
type: blog
title: How PemPem Accelerates Product Development with a Custom GraphQL Federation Approach
slug: 2024-02-28-pempem-accelerates-product-development-custom-graphql-federation-approach
series: WunderGraph Blog
date: 2024-02-28
author: Stefan Avram
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - Product Development
  - Scalability
  - Observability
tags:
  - graphql
  - federation
  - apollo
  - wundergraph
  - hasura
entities:
  - PemPem
  - WunderGraph Cosmo
  - GraphQL Federation
  - Apollo GraphQL
  - Hasura
  - José Rose
summary: |
  PemPem, a mobile-based trading platform for smallholder farmers, scaled faster by migrating to WunderGraph Cosmo. The migration provided GraphQL Federation capabilities, endpoint control, and full observability in a single secure router, enabling the company to serve multiple endpoints without restrictions while maintaining low costs and comprehensive monitoring.
canonical_url: https://wundergraph.com/blog/pempem-accelerates-product-development-custom-graphql-federation-approach
---
{% partial file="blog-callout.md" /%}


Believe it or not, but **~60%** of the global food calories are produced by **~500** million farmers who own plots of land not much bigger than 2 hectares and trade through a dynamic network of non-transparent traders. These farmers are known as smallholder farmers. 

The supply chain from the farm to the factory largely depends on word-of-mouth information, using personal memory or pen & paper as only records. This leads to lost revenues and a lack of traceability, contributing significantly to illegal deforestation.

[PemPem](https://www.pempem.io/) has built a mobile-based trading platform with embedded financing for smallholder farmers producing commodities worldwide. Their platform is like a digital exchange, with integrated logistics and financing and 100% traceability from farm to factory.


## The journey to federation begins 

> Our previous provider had some limitations on customization that we hit early when we started to scale. GraphQL Federation with WunderGraph Cosmo allowed us to serve multiple endpoints without restrictions with a single router.
-José Rose, Senior developer at PemPem

Like any startup, you'll know when you hit product market fit. Customers are signing up, usage is skyrocketing, and things around you are breaking. This is precisely what PemPem started to experience earlier this year. Their commodity market trading platform had lifted off! 

While they started to scale very quickly, they also realized that their old solution and vendor could not scale as soon as they could and needed more customization in various areas. José and his team started looking for a solution that would allow them to scale while keeping costs low and introducing observability across their entire stack. 

With their previous approach, they hit limits quickly on custom visible endpoints for their clients and started looking into GraphQL federation solutions.

### The Transition to GraphQL Federation

> We're relatively new to GraphQL Federation. Still, the transition from our old solution to Cosmo was very smooth, and we like the direction WunderGraph Cosmo is going for federation vs our previous provider.  
-José Rose, Senior developer at PemPem

While looking for a solution and scaling rapidly, José and his team learned about GraphQL Federation and WunderGraph Cosmo. With the WunderGraph router, they could place it in front of their architecture and serve multiple endpoints through Cosmo's performant router as a single point of truth. This quickly alleviated the concern with their previous provider because they would have had to hack together a custom solution. 

### Embracing Federated GraphQL with WunderGraph Cosmo

While scaling the usage of their platform, José and his team noticed they were having issues with clients and permission issues across their stack. With multiple client stacks, such as web and mobile applications, they needed a way to observe all of them and improve development time for endpoints.

With the Cosmo Router, they can now serve multiple clients with a single entry point versus having to stitch together multiple managed services. Scaling with Federation and Cosmo allows José and his team to choose the data they want from various data sources and harness it into a single place of truth. 

With the Cosmo Studio, José and his team can now get end-to-end observability on their client's stacks and increase security permissions for their clients. They can understand who is using what client and if fields need to be included or are used across all their clients. PemPem is a heavy user of DataDog and wanted to have all their analytics in one place. With Cosmo Studio's [OTEL Exporter](https://cosmo-docs.wundergraph.com/router/open-telemetry#can-i-export-otel-data-from-my-application), they were quickly able to sync Cosmo Studio and DataDog.


## Key features highlighted by PemPem

### Maintained Productivity and Expanded Possibilities with Studio:
PemPems's productivity level, achieved through federation, has been successfully maintained with [Cosmo's Studio](https://wundergraph.com/cosmo/features). Additionally, the studio's detailed analytics dashboard and Advanced Request Tracing have allowed PemPem to have observability across their entire platform and quickly identify bottlenecks across clients.


### Migration process
[Migrating to WunderGraph Cosmo](https://cosmo-docs.wundergraph.com/studio/migrate-from-apollo) proved to be a trivial and enjoyable journey for the PemPem team; They were able to set up the router within a day and have moved fully into production in less than 30 days.

### Team support
[WunderGraph Support](https://wundergraph.com/services) was enjoyable for both parties. With a shared Slack connection and access to our development team, PemPem could ask any questions during their migration and about the latest news in GraphQL Federation. José highlighted the speed at which we could help him with questions and issues.

## Final Thoughts

Cosmo's graphql federation solution allowed PemPem to quickly migrate away from their old solution while adding GraphQL Federation to their tech stack. The highlighted benefits included improved performance, enhanced observability, cost savings, and more. [To experience WunderGraph Cosmo, sign up for Cosmo's free tier and start building (no credit card needed)](https://cosmo.wundergraph.com/login)

> We learned about WunderGraph Cosmo and deployed it into production in about ten days. I highly recommend WunderGraph Cosmo; they helped us pivot quickly when we needed a solution ASAP! Everything now is working perfectly.
-José Rose, Senior developer at PemPem

### Video testimony 
If you prefer watching to reading, you also have the option to view this case study as a video.
{% youtube videoId="UhIgBghCVk0" /%}

