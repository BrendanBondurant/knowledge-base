---
title: Benchmarks, Performance, and Real-World Use Cases
slug: ep05-08-benchmarks-performance-realworld
series: The Good Thing
episode: 5
chunk: 08
participants:
  - Stefan
  - Jens
segment: The pitfalls of benchmarks, performance considerations, and the importance
  of real-world use cases
timecode: 00:45:06:11 - 00:51:27:12
start_time: 00:45:06:11
end_time: 00:51:27:12
speakers:
  - Stefan
  - Jens
topics:
  - Benchmarks
  - Performance
  - Real-world use cases
  - Synthetic benchmarks
  - Cache warming
  - Super Bowl traffic
  - Autoscaling
  - Cold starts
  - Customer needs
  - Product improvement
  - Macro vs. micro benchmarks
  - Code optimization
  - Developer experience
  - Product marketing
tags:
  - graphql
  - startup
topic_tags:
  - benchmarks
  - performance
  - real-world-testing
  - graphql
  - technical-validation
  - customer-education
entities:
  - Stefan Avram
  - Jens Neuse
  - GraphQL
  - Super Bowl
  - WunderGraph
mentions:
  - benchmark pitfalls
  - synthetic vs real-world performance
  - cache warming
  - Super Bowl traffic
  - autoscaling challenges
  - cold starts
  - macro vs micro benchmarks
  - customer-driven optimization
summary: Stefan and Jens discuss the pitfalls of benchmarks, the difference between
  synthetic and real-world performance, and how customer needs drive product improvement.
  They share stories about cache warming for Super Bowl traffic, the importance of
  macro vs. micro benchmarks, and why focusing on real-world use cases is more valuable
  than synthetic performance tests.
---

00:45:06:11 - 00:45:24:16
Stefan
I agree. For me. What I don't understand with benchmarks is like early in the journey is people
would ask us for benchmarks against a competitor, and me and Jens hated that question
because it's first of all, I honestly thought it was kind of lazy. Like, do the benchmarking yourself.
Like, here's how you can do it, spin it up on yourself and run the benchmarking yourself.

00:45:24:18 - 00:45:47:08
Stefan
But also we always said this a customer never complained about performance. Like it's very
fast. It's trusted by some of the biggest enterprises in the world, but they're like, oh, but this
one's a little bit faster. And for me, I don't know, it kind of annoys me with benchmarks because
it's exactly what you said. Every benchmark, the vendor can manipulate it to make themselves
always look the best it can use.

00:45:47:08 - 00:46:06:21
Stefan
cold starts. It can use a outdated version of the gateway. I don't understand even why there's
any relevance to benchmarks, and why do developers like it so much. And the biggest thing for
me about performances, you think of these things at scale, but the second you start thinking
about it, before you even have any users or any customers about it, I think that's waste of time.

00:46:06:21 - 00:46:11:25
Stefan
Like, why are you worrying about the performance when you should be worrying about the
customer? What do you think?

00:46:11:28 - 00:46:18:14
Jens
Yeah, and that's another thing. So benchmarks are very concerned. What's the right way to test.

00:46:18:18 - 00:46:20:07
Stefan
synthetic.

00:46:20:07 - 00:46:53:19
Jens
Synthetic. Yes. Synthetic. Because so we just recently built a new feature cache warmer. It's it's
so cool. So you run routers, they send telemetry data to our telemetry collector, and they tell us
which queries is this your router planning and how long does it take. So we put that into a click
house and we create a top end list of queries that take a long time to plan.

00:46:53:21 - 00:47:26:04
Jens
And we we every day we rebuild this list, put it on the cdn. And when the router starts or gets a
new config, we have to invalidate all caches. We have a query plan, a cache normalization,
cache validation cache. So we invalidate all these caches. Then we take this list and we pre
warm based on this list, based on the traffic you had yesterday and the queries that were worst
to plan based on that we warm up the caches.

00:47:26:06 - 00:47:51:05
Jens
And now when you get these requests that are really bad in planning time they hit the cache. So
that means we take we get the request, we parse it and then we execute it. We don't plan and
plan. It can take milliseconds. It can take sometimes seconds. In really bad cases it and it takes
CPU time. Io is cool I o means router waits.

00:47:51:08 - 00:48:19:28
Jens
Awesome. We can wait. We have go. We have goroutines we can wait. So like thousands of
requests we can write but CPU it's limited. We don't want to wait for a CPU because like we can
only have so many CPUs. So with this approach, in the real world scenario, we were able to
help the company go through Super Bowl without crazy flakiness on the router setup.

00:48:20:01 - 00:48:58:15
Jens
However, if you run your synthetic benchmark, you you will never see this kind of stuff because
you you're benchmarking like how much RPS can I hammer the router with one single curry
where the subgraphs are just returning static data? Like what actually are you testing? Like
that's not realworld, and in real world scenarios, when we talk about benchmarking, what we
actually need to do is let's say you are Super Bowl and you get traffic or you have Black Friday,
you get a lot of traffic.

00:48:58:17 - 00:49:26:29
Jens
So you have to ramp up your routers. You need to autoscale your router so more routers, if you
deploy new routers and the caches are cold, it means you have spikes in latency, spikes in CPU
time. So the reality is you need a solution that can cope with these kind of situations like scaling
up, scaling down, reloading the config.

00:49:27:01 - 00:49:48:14
Jens
And then if you look at the benchmarks, is anybody reloading the config during the benchmark?
Yeah, of course not. Because I don't know what they are testing. It's and the thing is if you ask a
customer like hey what are your need? Like listen to the customer, you know, it's always the
same thing. Listen to your customer doesn't say, oh, we want to hammer the router with the
same query.

00:49:48:15 - 00:50:14:18
Jens
No customer says, guys, we have a problem. When we scale up our routers, the caches are
cold and we have latency spikes. Can you solve that? So this is like a real world problem versus
just hammering a router with the same static query like it's yes, you can benchmark it and the
benchmarks can say something. But it doesn't mean in the end that this router will work.

00:50:14:21 - 00:50:17:26
Jens
On Super Bowl. I don't know.

00:50:17:29 - 00:50:34:15
Stefan
You hit so many good points there. So for one, the only people that do these benchmarks, the
synthetic ones, are the ones that feel threatened or they want to kind of do a little performance
thing, you know, like AWS doesn't run benchmarks. They don't have to. They're AWS. Who are
they going to like run a benchmark for?

00:50:34:15 - 00:50:57:17
Stefan
And so for me, benchmarks are synthetic. But to wrap this point home, what I think is interesting
is that if you collaborated with the companies on that use case for a Super Bowl, that's a good
benchmark because it's an actual customer one, but you kind of can't because it's your
customer that's the only way that a benchmark would work, because all these use cases are
complex.

00:50:57:17 - 00:51:15:25
Stefan
And, you know, with the pre warming cache and the traffic spike, that's important. But what's
synthetic about just hammering the router is that that's actually not a good benchmark because
it's not even a real life use case. You're not just going to hammer with the static query 150 times
and then measure the difference between Cosmo and whatever the other routers are in.

00:51:15:25 - 00:51:27:12
Stefan
And for basically benchmarks are just kind of BS. They kind of always are. If we could do them
collaboratively, I think it'd be great. But I also, I don't know if you can do them collaborative. Do
you think you could.