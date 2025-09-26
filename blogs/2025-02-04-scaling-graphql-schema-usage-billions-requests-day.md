---
type: blog
title: Scaling GraphQL Schema Usage to billions of requests per day
slug: 2025-02-04-scaling-graphql-schema-usage-billions-requests-day
series: WunderGraph Blog
date: 2025-02-04
author: Dustin Deus
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Observability
  - High-Scale Architecture
  - Data Pipeline Design
  - Enterprise Reliability
tags:
  - graphql
  - observability
  - telemetry
  - kafka
  - clickhouse
entities:
  - GraphQL Federation
  - Cosmo
  - Kafka
  - ClickHouse
  - ClickPipes
  - Cloudflare
  - WunderGraph
summary: |
  Cosmo's cloud architecture scales GraphQL observability to handle billions of requests per day using Kafka, ClickHouse, and regional load balancing. This enterprise-grade telemetry pipeline provides real-time schema usage analytics with sub-10ms ingestion latency, enabling teams to prevent breaking changes and optimize API performance at massive scale.
faqs:
  - q: What is GraphQL schema usage data and why is it important?
    a: Schema usage data shows how clients interact with fields, types, and arguments in your GraphQL API. This insight helps prevent breaking changes, identify unused fields, and understand client behavior—especially critical in a federated architecture with multiple subgraphs and services.
  - q: How does Cosmo collect GraphQL schema usage data?
    a: Cosmo collects usage data during the normalization and planning phases of request execution in the Router. The Router exports field and argument level metrics to the Metrics Collector, which then processes and forwards them to ClickHouse for analysis.
  - q: Why does Cosmo use Kafka in its telemetry pipeline?
    a: Kafka acts as a buffer between the Metrics Collector and ClickHouse. It absorbs traffic spikes, decouples ingestion, and enables reliable, high-throughput streaming without overloading ClickHouse. Kafka's batching and retention policies also support fault tolerance and replayability.
  - q: What are ClickPipes and how do they help?
    a: ClickPipes are a native ClickHouse Cloud feature that read from Kafka, transform the data, and write it to ClickHouse tables. This enables a real-time ETL pipeline with ingestion latency under 10ms—no custom transformation or loading code needed.
  - q: How does Cosmo ensure high availability and low latency across regions?
    a: Cosmo deploys regional Metrics Collector clusters in the US and EU, each connected to its own Kafka cluster. A Cloudflare Global Load Balancer routes data to the nearest region, ensuring failover, horizontal scalability, and the lowest possible latency.
  - q: Can small teams use this architecture?
    a: Yes. The open-source Metrics Collector works well for small or self-hosted workloads. Cosmo Cloud is designed for enterprise-scale deployments needing real-time analytics, high availability, and global ingestion, but the same principles apply at all scales.
canonical_url: https://wundergraph.com/blog/scaling-graphql-schema-usage-billions-requests-day
---

If you're running a GraphQL API in production,
it's very likely that you've asked yourself the following questions:

1. If we introduce a change to our GraphQL Schema,
will it break any existing clients and if so, which ones?
2. Which exact fields are being used by the client "Android App" version "1.3.4"?
3. Which clients are using the field "email" on the "User" type?

Especially when running and operating a federated GraphQL Architecture,
where multiple services (Subgraphs) are contributing to the overall schema,
detailed Schema Usage data is crucial to understand how the schema is being utilized and to ensure that changes don't break existing clients.

In this article, we will explore the challenges of managing GraphQL Schema Usage at scale.
We'll be taking a deep dive into handling high data volume, throughput, and latency,
batching, queuing, and regional deployment to build a robust system for scalable and reliable GraphQL observability.

{% partial file="blog-callout.md" /%}

## Introduction

GraphQL is a versatile query language for APIs that empowers clients to request precisely the data they need. While it offers significant flexibility and power for API development, managing GraphQL at scale poses unique challenges. As the number of requests grows,
understanding how the schema is being utilized becomes increasingly complex.

At the same time, scaling out API development across multiple teams and services only works efficiently if you're able to prevent breaking changes and ensure that changes are backward-compatible. This is where GraphQL schema usage data comes into play.

To address these issues, we need to collect schema usage data from all GraphQL API Gateways,
typically called Routers. This information is then aggregated into materialized views to gain insights into GraphQL Schema usage over time.

## High level overview of the architecture to collect GraphQL Schema usage information

Before we start talking about our architectural challenges, let's first understand what GraphQL schema usage is and how we collect it.

When a GraphQL request hits the Cosmo Router, it undergoes several steps:

1. Parsing
2. Validation
3. Normalization
4. Planning
5. Execution

Most relevant for schema usage data collection are the normalization and planning phases.
The normalization phase transforms the query into a canonical form,
which is not just a requirement for the planning phase,
but it also simplifies the process of collecting schema usage data,
e.g. by removing duplicate fields or by exporting arguments into variables,
making them easier to analyze.

During the planning phase,
the normalized GraphQL query is traversed to gather detailed information about the fields, types, and arguments being used.
Once the operation executes, this data is exported asynchronously to a service we call the "[GraphQL Metrics Collector.](https://github.com/wundergraph/cosmo/tree/main/graphqlmetrics)"

Collecting schema usage data introduces a small overhead to the request pipeline.
To minimize this overhead, we're doing this step alongside the planning phase.
This gives us the ability to cache not just the query plan but also the schema usage data for this specific query.

The Metrics Collector is responsible of ingesting the data and forwarding it to our analytics warehouse, [ClickHouse](https://clickhouse.com/).
ClickHouse is a columnar database that excels at handling large volumes of data with high throughput and low latency.
By storing schema usage data in ClickHouse,
we can store terrabytes of data and query it efficiently in [Cosmo Cloud](https://cosmo.wundergraph.com/), our GraphQL API management platform.

Let’s walk through an concrete example to clarify how this process works.

## Example

Consider a GraphQL query:

```graphql
query {
  findEmployees(criteria: { nationality: AMERICAN }) {
    id
    details {
      forename
      surname
    }
  }
}
```

This operation is of type `Query` and contains the `findEmployees` field,
which returns a list of `Employee` objects.
Each `Employee` object has an `id` and a `details` field,
where `details` is a `Details` object containing `forename` and `surname` fields.
After execution, we export the following data to the GraphQL Metrics Collector:

```json
{
  "RequestCount": 10,
  "SchemaUsage": {
    "RequestDocument": "query($a: SearchInput){findEmployees(criteria: $a){id details {forename surname}}}",
    "TypeFieldMetrics": [
      {
        "Path": ["findEmployees"],
        "TypeNames": ["Query"],
        "SubgraphIDs": ["ee958eb9-6e08-4a1c-a985-3c5e491a4d4f"],
        "NamedType": "Employee"
      },
      {
        "Path": ["findEmployees", "id"],
        "TypeNames": ["Employee"],
        "SubgraphIDs": ["ee958eb9-6e08-4a1c-a985-3c5e491a4d4f"],
        "NamedType": "Int"
      },
      {
        "Path": ["findEmployees", "details"],
        "TypeNames": ["Employee"],
        "SubgraphIDs": ["ee958eb9-6e08-4a1c-a985-3c5e491a4d4f"],
        "NamedType": "Details"
      },
      {
        "Path": ["findEmployees", "details", "forename"],
        "TypeNames": ["Details"],
        "SubgraphIDs": ["ee958eb9-6e08-4a1c-a985-3c5e491a4d4f"],
        "NamedType": "String"
      },
      {
        "Path": ["findEmployees", "details", "surname"],
        "TypeNames": ["Details"],
        "SubgraphIDs": ["ee958eb9-6e08-4a1c-a985-3c5e491a4d4f"],
        "NamedType": "String"
      }
    ],
    "OperationInfo": { "Hash": "6974980016622698804" },
    "SchemaInfo": { "Version": "d20c18cf-9497-496d-b951-da2dd0903d60" },
    "ClientInfo": { "Name": "unknown", "Version": "missing" },
    "RequestInfo": { "StatusCode": 200 },
    "ArgumentMetrics": [
      {
        "Path": ["findEmployees", "criteria"],
        "TypeName": "Query",
        "NamedType": "SearchInput"
      }
    ],
    "InputMetrics": [
      {
        "Path": ["SearchInput", "nationality"],
        "TypeName": "SearchInput",
        "NamedType": "Nationality",
        "EnumValues": ["AMERICAN"]
      },
      { "NamedType": "SearchInput" }
    ]
  }
}
```

This document encapsulates all necessary details to comprehend schema usage:

- **`TypeFieldMetrics`**: Details about the fields.
- **`ArgumentMetrics`**: Information on the arguments.
- **`InputMetrics`**: Data about the input types.
- **`RequestCount`**: The frequency of the operation within the batch window.

## Batching GraphQL Schema Usage Info at the Router level

By aggregating request counts in the Router,
we can batch these documents rather than sending them multiple times.
This saves resources on both the Router and the collector and reduces the overall data volume.

This small design decision has a huge impact on the overall performance of the system.
It is very likely, even in a dynamic query language like GraphQL,
that certain operations are called thousands of times within a short period of time.

After gaining a basic understanding of what schema usage data is and how it is collected,
let's dive into the architectural challenges we faced and how we addressed them.

## Ingesting GraphQL Schema Usage Info: The Naive approach

Make it work, make it right, make it fast (scalable).
Premature optimization is the root of all evil,
and as such, we started with a simple architecture that worked well for small to medium workloads.

When we introduced the first version of the GraphQL Metrics Collector,
we focused on simplicity and operational efficiency.
Our initial architecture was straightforward:
The Metrics Collector gathered schema usage data from Routers and forwarded it directly to ClickHouse.

This design was simple,
making it ideal for small to medium workloads.
However, as our user base grew, we encountered challenges related to data volume, throughput, and latency.

Something you need to understand when working with ClickHouse is that it doesn't like accepting many small batches frequently.
Each write produces a part on the cluster that must be merged with other parts.
This process is resource-intensive and can lead to performance degradation or even outages if the cluster cannot keep up with the load.

This exact problem surfaced in our system recently.
Our collector was writing directly to ClickHouse without batching the data at the collector level.

After identifying the issue, we began implementing data batching at the collector level.
This reduced the number of parts created and improved the cluster's throughput.
While this was an effective solution for small to medium workloads, it wasn't sufficient for larger workloads.

As more and more Routers pushed data to the collectors,
we horizontally scaled them to handle the increased load.
While this approach worked for a time, it was just a band-aid solution.

The real problem was that we didn't handle backpressure correctly.
The collector was pushing data to ClickHouse as fast as it could,
which increased the load on the database cluster and led to performance issues.
Instead of scaling the cluster, we needed to throttle the ingestion rate to match the cluster's processing capacity.

This ultimately led us to a new architecture where we decoupled ingestion into ClickHouse from the collector and introduced an asynchronous queuing system.

## Comparison of the old and new Architecture

{% image caption="Cosmo GraphQL Metrics Collector Architecture Diagram" alt="A comparison of the old GraphQL Metrics collector Architecture vs the new asynchronous setup" src="/images/blog/telemetry_pipeline/enterprise_architecture.png" /%}

The most significant change in the new architecture is how we're using Kafka as a buffer to absorb client side traffic spikes while being able to ingest data into ClickHouse at a constant rate in large batches.
By making database writes asynchronous with polling,
backpressure is handled effectively and we're not overloading the ClickHouse cluster.

## Kafka: Distributed, persistent Streaming Platform for scalable data Ingestion

To address the challenges of data volume, throughput, and latency, we introduced a streaming pipeline using Kafka that sits between our collectors and ClickHouse.

This setup allows us to accept data at a much higher rate than ClickHouse can ingest while consuming it at a rate that ClickHouse can handle.
We solved our backpressure problem as described earlier.

Kafka acts as a buffer, absorbing the data and ensuring it is processed reliably.
The collector batches the data and writes it to the right Kafka topic.
Kafka is able to handle spikes in data volume and ensures that no data is lost.
At the same time, it allows us to independently scale the first step of the ingestion process without having to scale the ClickHouse cluster.

### Kafka Partitioning

Kafka topics are divided into partitions.
Each partition is an ordered, immutable sequence of records that is continually appended to.
Partitions allow us to parallelize the data ingestion process and distribute the load across multiple consumers.
Because the order is not important for our use case, we didn't have to worry about how kafka handles it.
We can simply scale the number of partitions to increase the throughput of the system.

### Kafka Retention Policy

A Kafka topic can be configured to retain data for a specific period or size. We made use of it to limit how much and how long data is stored in Kafka.

This can be adjusted based on the ingestion rate and the processing rate of ClickPipes.
In our case, we keep the last 3 hours or max 30GB of data in Kafka.
This means that if ClickPipes is offline,
it can catch up on the last 3 hours of data once it comes back online,
which is a good compromise between storage cost and availability.

### Kafka Consumer

Every queue has consumers that read data from the queue and process it.
In our case, we have ClickPipes, which reads data from Kafka topics, transforms it, and writes it to ClickHouse tables.

### Go Kafka Client

I'd like to shot out to [twmb](https://github.com/twmb) who maintains the fantastic Kafka Go client library [franz-go](https://github.com/twmb/franz-go).
Without this library, we would have had a much harder time implementing this solution.
The library is very well maintained and comes with builtin batching and partitioning support that we leveraged to build our collector.

## Below 10ms ingestion: ClickHouse ClickPipes with Kafka for real-time ETL

We have been ClickHouse Cloud customers since the beginning and are very happy with the performance and reliability of the service.
The problem we faced is quite common and aligns with the ETL pattern.
We need to extract data from the Routers, transform it, and load it into ClickHouse.
The transformation is handled by the collector, while the loading is managed by ClickPipes.

{% image caption="ClickHouse ClickPipes (Test environment)" alt="ClickHouse ClickPipes (Test environment)" src="/images/blog/telemetry_pipeline/clickpipes.png" /%}

Fortunately, ClickHouse Cloud offers a feature called [ClickPipes](https://clickhouse.com/cloud/clickpipes),
which allows us to define a _`DataSource`_ that performs this exact function.
With ClickPipes, we can define a source that reads data from a Kafka topic, transforms it, and writes it to the appropriate ClickHouse table.
This feature works seamlessly and eliminates the need for implementing and maintaining a custom ETL pipeline from scratch.

The only change we needed to make was to extend the collector to write data to the Kafka topic. Not only did this resolve our reliability problem, but it also enabled us to create a real-time ETL streaming pipeline.
The average latency from ingestion to availability in ClickHouse is now under 10 milliseconds.

This architecture also lies the foundation for future investments in real-time analytics and monitoring.
We already have plans to move our OpenTelemetry pipeline to Kafka.

## Horizontal Scaling and High Availability with Regional Deployment and Global Load Balancing

{% image caption="Global Network Architecture of the Cosmo GraphQL Metrics Pipeline" alt="Global Network Architecture of the Cosmo GraphQL Metrics Pipeline" src="/images/blog/telemetry_pipeline/network_architecture.png" /%}

When you take a step back and look at the new architecture, you will notice that we have now the following components:

- **Client**: Sends schema usage data to the router.
- **Router**: Responsible for collecting schema usage data and sending it to the collector.
- **Global Load Balancer**: Routes traffic to the nearest collector cluster.
- **Metrics Collector**: Responsible for collecting schema usage data from Routers and writing it to Kafka topics.
- **The Kafka Cluster**: Acts as a buffer between the collector and ClickPipes.
- **ClickPipes**: Reads data from Kafka topics, transforms it, and writes it to ClickHouse tables.


All components are horizontally scalable. In order to scale the collector, we can simply deploy more replicas.
The Kafka cluster can be scaled by adding more brokers.
ClickPipes replica count can be increased on _`DataSource`_ level to speed up ingestion.
This architecture is highly available and can handle billions of requests per day.

We benchmarked the new architecture to ensure it meets our performance requirements.
Our tests showed that the system can handle ingesting schema usage data from more than 100k deployed Routers exporting data every 10 seconds.

For ClickHouse, we still operate a single cluster to simplify querying and data migration from Cosmo Cloud.
Because ClickHouse can dictate the ingestion rate (backpressure),
we don't have to scale even if our throughput increases significantly.
It becomes a flexible decision between cost and performance (time when data is available).

From a availability perspective, we wanted to ensure that the system is resilient to regional failures.
If the Kafka cluster goes down, the collector can't push data,
and the workers can't poll it. To mitigate this risk, we deployed multiple Metrics Collector Clusters across multiple regions:

- US - SFO, and WAS
- EU - FRA, and PAR 

Each zone (EU, US) operates its own Kafka cluster.
Collectors in EU are connected to the EU Kafka cluster,
and collectors in the US are connected to the US Kafka Cluster.
We also enabled fail-over.
If one zone or region goes down, the other zone can take over the ingestion process.

Ultimately, we wanted to prevent that users has to deal with regional ingestion endpoints.
For that reason, we leverage Cloudflare Global Load Balancer to route the traffic to the nearest Collector Cluster.
Each Collector is connected to the nearest Kafka cluster.
This way we can ensure that traffic is fairly distributed and processed with the lowest latency possible.
It also gives us the flexibility to scale the collector and Kafka cluster independently based on the regional demand.

## Observability and Monitoring

Ensuring the health and performance of our system is paramount.
We instrumented our Metrics Collector using OpenTelemetry, which allows us to collect critical metrics related to process health and Kafka producer activity. This includes:

- **Collector Health**: CPU, memory usage.
- **Kafka Producer Metrics**: Batch Size, Message Size, and Write Latency, Connection Errors.

These metrics are exported to our observability platform, where we set up alerting rules to notify us of any anomalies or issues. This enables us to respond proactively and maintain high availability.

Additionally, we monitor all logs and errors to identify potential issues and troubleshoot them effectively. ClickPipes also maintains an error table for each data source, which we observe to pinpoint issues with data processing.

{% image caption="Collector Observability (Test environment)" alt="Collector Observability" src="/images/blog/telemetry_pipeline/collector_observability.png" /%}

## Conclusion

Ingesting GraphQL schema usage data at scale requires a robust, resilient, and efficient system.
Through a series of architectural changes like batching, queuing, and regional deployments,
we’ve built a system capable of handling scalable workloads while maintaining a high level of availability.
However, these advancements come with trade-offs in terms of cost and complexity.

For smaller workloads, like personal projects or small on-premises deployments the open-source version of our Metrics Collector is a cost-effective and efficient solution.
For enterprise-grade demands, Cosmo Cloud offers a scalable and reliable system that ensures low latency and high availability.
By tailoring solutions to meet the unique needs of our users, we’re able to provide a comprehensive platform for GraphQL schema observability.

If you're looking to scale your GraphQL API and need help with observability, we're here to help.
Feel free to [reach out to us](https://wundergraph.com/contact/sales) if you need assistance or have any questions.

If you find our challenges interesting and you're looking for a job, we're hiring! Check out our [open positions](https://wundergraph.com/jobs) and join our team.
If you have any questions or feedback, feel free to reach out to me on [Twitter](https://x.com/dustindeus) or join our [Discord Community](https://wundergraph.com/discord).

---

{% faq /%}

---