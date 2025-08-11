---
title: Telemetry Pipeline Architecture
slug: ep03-07-telemetry-pipeline-architecture
series: The Good Thing
episode: 3
chunk: 7
participants:
- Stefan
- Dustin
segment: Deep dive into Cosmo's telemetry pipeline architecture and data processing
timecode: 00:26:46:25 - 00:32:26:12
start_time: 00:26:46:25
end_time: 00:32:26:12
speakers:
- Stefan
- Dustin
topics:
- Telemetry Pipeline
- Data Processing
- ClickHouse
- Kafka
- Scalability
tags:
- telemetry
- data-pipeline
- clickhouse
- kafka
- scalability
- architecture
topic_tags:
- telemetry
- data-pipeline
- clickhouse
- kafka
- scalability
- architecture
entities:
- Stefan
- Dustin
- Cosmo
- ClickHouse
- Kafka
- ClickHouse Cloud
mentions:
- telemetry pipeline
- schema usage data
- batching
- collectors
- back pressure
- Click Pipes
summary: Dustin explains the telemetry pipeline architecture he built for Cosmo, including
  batching at the router level, using Kafka as a buffer between collectors and ClickHouse,
  and implementing back pressure mechanisms to handle high-scale data processing efficiently.
---

00:26:46:25 - 00:27:07:05
Stefan
Yeah, it's getting better, but no, it's a good point. And then I kind of want to transition into kind of
what we've been talking about this week. So I just released a, broadcast to all of our customers.
And so we made some really cool changes. And Dustin worked on something pretty cool, which
is a blog post coming out soon.

00:27:07:07 - 00:27:18:26
Stefan
But talk to me a little bit about the telemetry pipeline and maybe for some of the viewers, kind of
explain, like what that was, why you built it, and what it's going to do to cosmos as a platform.

00:27:18:28 - 00:27:55:14
Dustin
Yeah. It's a yeah. I think it's a very technical, very interesting, interesting technical issue. It's not
so, amazing, but it's it's it's. Yeah, I would say it's still pretty interesting. So you need to imagine
that when, a customer runs a router and, a graphql requests, hits the router, we analyze what
types and fields has been used, and this, this usage data is then, pushed to our cloud
infrastructure and need to be ingested into our clickhouse cluster.

00:27:55:16 - 00:28:26:14
Dustin
So now you can assume that when, a customer with a lot of traffic, we also produce a lot of,
schema usage data. So first step is to batch the data inside the router. So assuming, someone,
someone sent the graphql. Always the same operation until it hits 500,000 times. The router. So
we don't have to send, we don't have to send 500,000 operations, schema usage operation to to
to cosmo.

00:28:26:16 - 00:28:57:15
Dustin
We will batch it and we will, then send a counter of 500,000 to our cloud. So that was the first
optimization step. So in other words, we we batch at the router level and then periodically push
the schema usage data to our cloud. And what I mean with cloud is like we maintain, a fleet of
metrics, collect collectors, which are responsible of ingesting this data directly to clickhouse.

00:28:57:18 - 00:29:29:17
Dustin
And, if you're familiar with, data pipelines, you know, that the more traffic we will produce on the
router side, the more traffic it will push. It will generate and push to our collector fleet and if the
collector fleet will directly ingest the data to a click cluster, the the we will have at some point,
we will hit a wall because, clickhouse cannot.

00:29:29:20 - 00:29:51:00
Dustin
Yeah. Click house, will not be able to keep up with the load. And we would need to, need to,
scale clickhouse and that is, expensive. So what can we do? When you have to, you have to
instead of pushing the data, we have to pull the data from, from and from a queue.

00:29:51:01 - 00:30:13:18
Dustin
For example, for example, Kafka. So what we what we did was to implement, like, we could say
a buffer or the buffer structure between the collectors and clickhouse. So clickhouse is able to
pull the data at his own pace. And then that way we don't have to over scale the clickhouse
cluster just to to to keep up.

00:30:13:20 - 00:30:25:11
Dustin
With a load we can, we can yeah. Have, implement like a back pressure mechanism between
the collectors and clickhouse.

00:30:25:14 - 00:30:44:07
Stefan
Yeah. That's super cool. So, like, if I understand it from, like, so, we always joke around, so, like,
I'm non-technical. I have, like, very limited experience as a software engineer, but I did
implement some cool stuff, but I didn't work with clickhouse. I didn't work with redis, I didn't I
have nowhere near the experience with you, but if I'm understanding this correctly, so cosmos
growing.

00:30:44:12 - 00:31:04:19
Stefan
We have some customers that do billions of requests per day, and what that would do is once it
goes through the router and it heads over to click house, it would kind of overload clickhouse
and it would kind of, have to scale up super fast. It also isn't super performant. And it would not
only just drive the cost up like crazy, it also wouldn't be performant for the customer.

00:31:04:19 - 00:31:27:04
Stefan
And so what you've implemented with this telemetry pipeline is a system that basically kind of
we still take in the same amount of requests, like you said, like 500,000 requests, but we kind of
spread it out and kind of put it in a queue, and then it's processed into clickhouse on a schedule.
And what that does is it allows clicks to scale up slowly and it doesn't actually overload
clickhouse.

00:31:27:04 - 00:31:27:24
Stefan
Right.

00:31:27:27 - 00:32:02:16
Dustin
Exactly. And also interesting is because we're using clickhouse cloud, they're they have an
offering called Click Pipes that allows you to connect, click your clickhouse cluster with any third
party, database, which includes Kafka, which includes, BigQuery. And they're, they maintain, the
worker fleet that pulls the data from your data source, for example, Kafka and imports the data
into the right, clickhouse tables.

00:32:02:19 - 00:32:26:12
Dustin
So that way we don't have to maintain the worker fleet. We don't have to be an expert in that
area. And the only the only responsibility we have is to push the data into the Kafka cluster,
taking care of it, that, retention policies are properly configured, that the kafka clusters are
healthy and, yeah. 