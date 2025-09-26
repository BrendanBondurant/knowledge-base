---
type: blog
title: How TravelPass Group manages PCI compliance with GraphQL and WunderGraph Cosmo
slug: 2024-02-12-travelpass-group-manages-pci-compliance-graphql-wundergraph-cosmo
series: WunderGraph Blog
date: 2024-02-12
author: Stefan Avram
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - PCI Compliance
  - GraphQL Federation
  - Security
  - Self-Hosted Solutions
tags:
  - graphql
  - federation
  - apollo
  - wundergraph
  - security
entities:
  - TravelPass Group
  - WunderGraph Cosmo
  - PCI Compliance
  - Apollo GraphQL
  - Tyler Hawkins
summary: |
  TravelPass Group ensures PCI compliance and secure GraphQL usage at scale using WunderGraph Cosmo's self-hosted router and namespace filtering. This approach allows them to contain all data and services within a federated graph while selectively determining which graphs are available to different groups, maintaining security and compliance for sensitive payment data.
canonical_url: https://wundergraph.com/blog/travelpass-group-manages-pci-compliance-graphql-wundergraph-cosmo
---
{% partial file="blog-callout.md" /%}

> Utilizing Cosmo's self-hosted router empowers us with direct control over our data. This enables necessary scalability according to our requirements and ensures absolute PCI compliance, a crucial aspect of our operations.  -Tyler Hawkins, Backend Tech Lead at Travelpassgroup.com

Let's examine GraphQL's fundamental promise:

With a single query, receive precisely what you require and avoid excess data.

Amazing concept, right? However, if you've attempted to incorporate GraphQL across an entire engineering team, you might've quickly realized that achieving this objective is more complex than it sounds. For every developer in the organization to get everything they need in a single query, all possible required data must exist within one graph.

A single graph enveloping all data might seem implausible, especially from a compliance standpoint. This was one of Travel Pass's most significant obstacles when they expanded their use of GraphQL. As a travel booking platform catering to millions of global customers, their backend services handle a substantial amount of PCI data that can't be available to our client applications.

One graph = equals one endpoint, meaning client apps could access everything, including cardholder details and other sensitive data, right?

Surprisingly, not necessarily. With a Federated Graph and a self-hosted router, we can contain all our data and services, including the sensitive ones, within our federated graph, yet selectively determine which graphs are available to different groups, such as app developers. In this post, we'll guide you on how Travel pass achieved PCI compliance, and how you can replicate it employing namespaces with Cosmo Studio and the self-hosted cosmo router! 

It's important to note that Travel Pass group were early adopters of GraphQL and were using Apollo GraphQL before WunderGraph Cosmo.

### Company background

[Travel Pass Group](https://www.travelpassgroup.com/) is a company dedicated to enhancing the travel booking experience. They specialize in connecting travelers with a wide range of travel options, enabling them to explore new places and cultures with ease. TravelPass Group has been acknowledged for its rapid growth and workplace culture by several prestigious lists and awards.

They've always been at the forefront of technology adoption, even being an early adopter of GraphQL before it gained widespread popularity. They embraced GraphQL and Apollo GraphQL as their preferred tools for data management and API development. 


## 	Let's take a step back

To understand how Travel Pass Group (TPG) was able to achieve total data sovereignty and remain PCI compliant. It's important we understand how [Cosmo's architecture works](https://cosmo-docs.wundergraph.com/architecture) and what information is shared between the studio and the router. 

{% image caption="WunderGraph Architecture" width="1666" height="1299" alt="WunderGraph Architecture" src="/images/blog/travelpass/wundergraph_hosted_diagram.png" /%}

The architecture diagram displays our [Hybrid SaaS model](https://www.wundergraph.com/pricing). This model comprises of the customer-hosted router and our hosted studio. To detail, everything below the red line, namely the router, is under your management and hosting. Conversely, we at Wundergraph take care of everything above the red line, which includes hosting the studio.

But even though this is a SaaS model, how was Travel Pass Group able to achieve total data sovereignly and remain PCI Compliant? 

By default, your sensitive information is segregated from the Cosmo Managed Service.

Cosmo in its hybrid set-up (Router hosted by you, analytics and tracing data stored in Cosmo Managed Service) means that we receive and store nothing but request metadata. This metadata cannot be linked to or reverted into your actual request payloads, and is used solely to provide the tracing and analytics insights of Cosmo Studio.

Any information (i.e. request / response data) exchanged between different APIs through your Cosmo Router never leaves your infrastructure where the Router is being hosted. WunderGraph is without any access to your Cosmo Router instance.

This privacy safeguard is implemented with WunderGraph Cosmo by design and not dependent on configuration or individual customization, which means that it cannot be - intentionally or by accident - circumvented or switched off. 

There also is no scenario where WunderGraph would need to host or access your Router. These measures ensure you stay compliant with data privacy regulations and regulatory requirements, e.g. GDPR, PCI, HIPAA etc.

WunderGraph Studio is also SOC2 compliant.

##  WunderGraph Cosmo: The Open-Source GraphQL Federation Solution

> It's very important that we have a solution that gives us a secure environment, where we can stay PCI compliant as well as have control over our traffic  -Tyler Hawkins, Backend Tech Lead at Travelpassgroup.com

Now that we have a clear understanding of Cosmo and its architecture. Let's talk about how Travel Pass Group uses its federated graph as a single point of truth but can expose certain graphs to customers without exposing sensitive data. 

### Namespaces 

As a single source of truth, our federated graph schema contains everything, including sensitive data. So, we can’t just directly have every customer application query our GraphQL endpoint for the entire federated graph. Instead, we need to define which federated graph specific applications can access. We can create [Namespaces](https://cosmo-docs.wundergraph.com/cli/namespace) in Cosmo Studio.

Namespaces are a way to isolate your federated graphs and subgraphs. They are the way to group graphs in different environments, such as production and staging.

### Using Namespaces to filter out PCI data

By using Namespaces and label matchers, we can ensure we expose the correct federated graph and subgraphs to our customers. This eliminates touchpoints with sensitive information, which is better for all parties involved. We can expose different GraphQL schemas to different parties based on a policy that we set. 

That's it. You can apply [Namespaces](https://cosmo-docs.wundergraph.com/cli/namespace) through the CLI.


## An Easy migration from Apollo to Cosmo

> With Cosmo we were able to get things up and running pretty smoothly. Cosmo was very similar to our old provider so there wasn't much of a learning curve. It only took us about a day to reconfigure everything and get started with Cosmo. -Tyler Hawkins, Backend Tech Lead at Travelpassgroup.com

[Transitioning from Apollo to Cosmo](https://cosmo-docs.wundergraph.com/tutorial/switch-from-apollo-to-cosmo) took us around one day. The reason for this relatively quick process was the resemblance between the two products, with many of Cosmo's features mirroring those in Apollo. This resulted in minimal disruption due to a reduced learning curve, as only some elements were unfamiliar.

One feature of Cosmo that we found pretty valuable and relished was the [**labels**](https://cosmo-docs.wundergraph.com/cli/essentials#labels) aspect. This feature provides a systematic way to fragment and comprehend our complex graph better, making it much simpler for us to utilize internally. By using labels, we can tear down the complexity of our graphQL schema into more manageable parts, enhancing our efficiency and comfort in using the system.

We now have cosmo running in production and so far are very happy with the migration and results.


## Final Thoughts

Cosmo's self-hosted router allowed Travel Pass group to stay PCI compliant while separating the complex schema into more manageable sections. The migration process only took Travel Pass about a day to migrate and use Cosmo. [To experience WunderGraph Cosmo, sign up for Cosmo's free tier and start building (no credit card needed)](https://cosmo.wundergraph.com/login)


### Video testimony 
If you prefer watching to reading, you also have the option to view this case study as a video.
{% youtube videoId="4XxcW4uKMSg" /%}