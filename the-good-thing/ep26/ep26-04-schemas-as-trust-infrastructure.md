# ep26-04-schemas-as-trust-infrastructure

**Time Range:** 0:13:03 - 0:17:29

**Topic:** Thinking long-term: schemas as trust infrastructure

---


00:12:49:15 - 00:13:12:17
Jens
So if I have, planet scale metal database, it it runs on a computer. The computer has a local
drive that makes it super fast. But what if the computer or the drive fails like my database? Is it
then down, or do you have some sort of like H.A. or. Yeah.
00:13:12:19 - 00:13:32:10
Sam
There is no non ha configuration for this. It's all highly available. By default. You get given three
nodes when you spin up. So you have two replicas in the in the instance that you would if you
say lost a primary node, we very, very quickly detect that failure. We throw that node out we
promote the node that's furthest ahead.
00:13:32:10 - 00:13:58:18
Sam
We have say semi synchronous replication, which means that by the time you write, we know
that the write has left to another machine. We then promote whichever of those machines put
the replicas underneath and then add a replacement node for that, for that primary. And that's all
done very, very quickly. In the time of failure, a proxy will buffer and hold off the queries and wait
for that to happen, and then send them through to the database when it's done.
00:13:58:18 - 00:14:08:25
Sam
So we basically, we handle all of that for you to give you high availability without the kind of
trade offs of disaggregating storage and compute.
00:14:08:28 - 00:14:43:25
Jens
Okay. And then do you, do you have to deal with, with problems like you make a write on like a
master chair and then you, you get you get it back, it's working fine. And then you make a read
request and it wasn't replicated or something or like, you know, there's like different guarantees
you can get from a database or like, is that like, does it behave like a singular Postgres or
MySQL or other differences and guarantees?
00:14:43:25 - 00:14:45:14
Jens
I can go from such a setup.
00:14:45:17 - 00:15:16:19
Sam
Nope. It it does. It works like the storage engine below. It's supposed to work with replication.
That's a core principles. We don't fake out the storage system like, you know, there's other
scaling solutions for these products that basically re-implement a different storage solution
under the hood to allow stronger consistency with significant trade offs there. But, yeah, you if
you read, write to a master and you require the the row on the replica for the same request, if
there's replication delay, it may not be there.
00:15:16:22 - 00:15:33:21
Sam
That's fine. And kind of normal. And that's an edge case to, to deal with any of these types of
systems. It's more like to, to do that kind of guarantee, you then pay a different penalty, which is
a penalty that we don't pay because it doesn't really scale. That's not really what our users are
looking for.
00:15:33:24 - 00:16:12:21
Jens
Okay. So you're at that scale. Your users, they have like database usage patterns, like for
example, like massive writes or something where you you don't immediately read it. Like for
example, I, I saw another, another podcast you did where you were talking about how how
planet scale benefits from, from the AI boom. And so I, I could assume, for example, that you
have, or you could have a customer where, where people have conversations with an AI, and
then you would write the conversation to the database, and that would be like quite write.
00:16:12:21 - 00:16:15:18
Jens
Heavy, but not so many reads in that scenario.
00:16:15:20 - 00:16:33:25
Sam
We do have that. Yes. And we have we do. We're very good at write works, write bound
workloads. We have a lot of very high scale, write bound workloads, whether or not they're AI or
not. They they store a lot of data. You find that in the consumer space, right? Like most
consumer apps. You know, the only thing that makes them specific to you is the data behind it,
right?
00:16:33:25 - 00:17:13:08
Sam
So they log a lot of things, a lot of transactions, transaction volumes, log lists, or just, you know,
data that they're ingesting from other platforms to do training on. That's all stuff that we're very,
very good at. And, you know, having the consistency model we have allows you for a much
higher writes. We also allow you when you shard to have multiple writer nodes, which means
you can actually scale up writes like one way that people give you that kind of consistency is
they do things like serialized isolation or have, single writer threads that mean you kind of
enqueue everything behind, those that kind of, isolation patterns, meaning it's slower,
00:17:13:08 - 00:17:27:15
Sam
but you get that consistency. We don't have that, consistency we have. We go for the
performance. That's different to durability. Your data is always there. We've never lost a
customer's data that, it's just that kind of trade off in terms of the multi-node consistency issue
there.

