# ep26-02-schemas-reflect-org-structure

**Time Range:** 0:04:45 - 0:08:50

**Topic:** Why schemas drift toward reflecting org charts

---


00:04:42:27 - 00:05:02:27
Sam
Yeah. Basically. Is that right? Yeah. And definitely not anti Postgres. Very excited by working
with Postgres and the companies that build on Postgres most specifically, I mean, we can dig
into like the core differences that we've already observed between mysql and Postgres, if you, if
you are interested. But yeah, basically we're kind of the database company now, right?
00:05:03:00 - 00:05:20:08
Sam
In fact, shipping Postgres meant that so many more people reached out asking for us to do
other database services. We won't be doing that for a while, maybe one day. But right now we,
we've got a long road ahead in the Postgres world. So we're building building that and enjoying
ourselves so far.
00:05:20:11 - 00:05:49:20
Jens
No, absolutely. Sorry. There were there were so many like, players before who did Postgres with
sharding. Some were acquired, others were not super successful. Why? Why are you doing
this? Like what? Why is it now the right time to do the same thing that others were okay ish
successfully like, why now?
00:05:49:23 - 00:06:12:09
Sam
So many reasons. Yeah. So you're really good. Why now? Question. So there's the like the
broader pieces that like kind of the Postgres community, and market is getting ready for
sharding. There's now companies that are running Postgres at some significant scale. It's
actually very interesting. I see people even yesterday I was reading someone talking about an
at scale Postgres workloads.
00:06:12:11 - 00:06:31:27
Sam
I know how large that workload is. I've seen it under NDA and it's not very big, in compared to
the size of the MySQL workloads that we see. But they're starting to grow. We've seen a few
large ish, but nothing that's anywhere near the size of the MySQL workloads that we've seen.
But it's happening and, and all and every company builds on Postgres.
00:06:31:27 - 00:06:57:11
Sam
Right. So it's coming. Postgres is probably going to go through the same era of the tens that that
MySQL went through from like 2010 to, 2020 in terms of very large and successful companies
building on Postgres, and it needing to mature and scale to make that happen. But it's like very
exciting. And so that's one why now question.
00:06:57:13 - 00:07:45:04
Sam
So the other is, we're doing it very simply, that we've done we have built the only generally
available large scale sharding solution that's out there, like there were attempts in the Postgres
world before, architecturally, they were misguided. And weren't built to support any large, really
large workloads. And so what we're doing is building from the first principles that we've learned
through sharding, databases, at very extreme scale, applying that to the world of Postgres,
building it into the ecosystem that Postgres has, which has some like bits that make that easier
bits that make that harder.
00:07:45:07 - 00:08:06:00
Sam
And it's just about the, the way we'll deliver it. And the other side of the coin being the hosting of
that. Right. So you can build an open source sharding solution. And people are and people have
it's very different than building a solution to run large scale workloads, then open sourcing it.
Right. And that's what we're doing.
00:08:06:00 - 00:08:28:25
Sam
We are working with design partners, to build sharded Postgres for the scale theyre at and then
once it's and then we get that loop of us directly seeing it and hosting it for them, and then we
will open source the byproduct of that meaning it will be very robust and resilient. We don't I'm
following along kind of a couple of open source sharding solutions right now.
00:08:28:27 - 00:08:40:19
Sam
And they're kind of achieving, the kind of spec of what you need to do. But that's very different
from battle hardening, at scale, which is what we are working on right now.
00:08:40:22 - 00:08:41:12
Stefan
No, also.
00:08:41:12 - 00:08:46:20
Jens
Not the database expert. Stefan, can I contribute?
00:08:46:21 - 00:08:47:11
Sam
Sorry.
00:08:47:13 - 00:08:52:10
Stefan
You're you're hijacking. We got to follow the agenda. The thing is, what agenda?
00:08:52:10 - 00:08:53:26
Jens
We're just talking. Who?