# ep07-13-batching-entities-and-federation-evolution

**Time Range:** 01:08:14 - 01:14:15

**Topic:** Tradeoffs of batching, entities field, and federation evolution

---

01:08:14:09 - 01:08:25:22
David
2019 sorry. 2019 was the earliest sort of made public. And then 2020. So it probably existed a
bit before that. But yeah, 2019 2020.
01:08:25:25 - 01:09:07:06
Jens
Yeah. What one one like you mentioned Sergiy, one, one idea of this new spec is it you can just
have a regular GraphQL server and the router will figure out stuff and query planner. But at the
same time, if you if you look at these early designs, one thing that immediately caught my eye is
batching, because I would say the, the, the one thing that I, I have like a love and hate
relationship with in Federation is we have this entity underscore entities field that gets an array
of any which is representations.
01:09:07:08 - 01:09:33:17
Jens
And we have no clue what that is. It's just JSON. But the the good thing about this approach is,
we have automatic support for batching, as bad as it is, but that's like the upside, if we go away
from this approach and we just have, like, regular GraphQL fields in the root, and we want to
batch load, entities or something.
01:09:33:17 - 01:09:37:00
Jens
How how will that work?
01:09:37:02 - 01:10:06:20
Sergiy
There's ongoing discussions and that's, how it could be done. There is, multiple possible options
like, you could just have like kind of kind of batch root fields like get product and get products,
for example. Then all the possible way that it will be somehow uploaded, to their top level of
GraphQL spec, there is some concepts, of batch execution of variables and queries.
01:10:06:22 - 01:10:37:16
Sergiy
And I'm not fully aware of this option. Yeah. But it will just offload some work, probably to the
execution pipeline that you will need to more carefully, plan what you will be, doing and to my
opinion that you just need to have some kind of batch endpoint because currently it's frequent
problem, even with, reference resolvers that you anyway need to have some kind of data loader,
even if something subgraph to not have.
01:10:37:16 - 01:10:41:01
Sergiy
n plus one problem.
01:10:41:04 - 01:10:42:07
David
Yeah.
01:10:42:10 - 01:11:37:05
Jens
Okay. Yeah. Very very interesting. Another another development we've seen in the, in the
community is the, benchmarks and audits that try to benchmark and and verify the
implementation of, of, GraphQL routers. And I'm curious to, to hear what you, what you think
about benchmarking and auditing, and different approaches how to do it and, and yeah, just like
in general we do we do a lot of benchmarkING internally and we do a lot of testing and, and like
what I said earlier, we have a batch query planner that's like a headless router that can build
query plans, you can compare them, etc. if you look at this ecosystem and
01:11:37:05 - 01:11:54:02
Jens
the different ways where, where, other parties, try to, to bring tooling to verify and benchmark,
like how, how do you think about these, these approaches and maybe you see some, some,
some good things about it, but also some drawbacks.
01:11:54:04 - 01:12:42:19
Sergiy
Any given benchmark. And there's always questionable topic because the benchmarks could be
biased. Like you could, have some kind of, a particular conditions under which, you will
degradation performance or, you will get high end performance. And sometimes it is, not like a
feasible to, to have a one single benchmark for every possible scenario because there actually
is federation, like bunch of possible scenarios you could benchmark, just a router, gateway, just
make sure that you are not, testing actual throughput of your subgraph, because it also could be
a case that just your subgraph is not not so fast.
01:12:42:19 - 01:13:09:06
Sergiy
Right. Then you could, sometimes benchmark like, a full life cycle of the query, like, and it will
involve, query planning, and you will, of all kinds, for example. Right. Just to measure like how
fast you could find the query and, typically you should spend that time in. planning just the first
time when you reach the query and then after that it will be cached and just like negligible.
01:13:09:09 - 01:13:47:11
Sergiy
But at the same time, if your cold query takes like a lot of time to just fetch so some for the first
time, it also could be a problem, then it could be a complexity benchmark and like how fast you
will be able to transform some query, which requires a lot of transformation. But yeah, all these
different parts, it will have an influence on the, results of benchmark and just, typical benchmark
around the gatewayt involves, like throughput, like requests per second and, some other data.
01:13:47:11 - 01:14:15:10
Sergiy
P95. Yeah, something like that. But, it is really just a bit more about that in this case. And, yeah,
you should be just careful when you're creating benchmarks or I believe we should be careful,
even if you, publishing our own benchmarks, because maybe we could also be a bit biased, a
bit. And, yeah.