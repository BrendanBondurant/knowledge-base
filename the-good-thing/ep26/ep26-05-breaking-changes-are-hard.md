# ep26-05-breaking-changes-are-hard

**Time Range:** 0:17:29 - 0:21:21

**Topic:** The pain of breaking changes and downstream coordination

---
00:17:27:16 - 00:17:47:04
Stefan
So, when you kind of explain it like this, it's it sounds pretty easy, like you're like the way you
explain in the beginning, like, anybody could have done this, but why is nobody else doing this
the way you explained it? Like it seems like from first principles, like, why did no one else think
of this? But when you guys came along, you guys did like, why is no one else replicating it or
trying to copy it?
00:17:47:06 - 00:18:12:17
Sam
I think they definitely are. Whether or not they're doing it as well. We didn't invent anything like
we we, I said on Twitter a while back that I don't think theres very much IP in the database
world, like we're all looking at papers that are from the 60s. The rules of computers have really
not changed either. Or physics, like the constraints that we're dealing with in most computer
science problems of physics, latency, the speed of light.
00:18:12:19 - 00:18:36:27
Sam
You know, all of these failure rates, all of these various factors, we just provide we apply a very
pragmatic approach to how we deal with these things. And through experience, we've seen the
ways that fail. A lot of databases have a kind of high hopes of reinventing the wheel when it
comes to these kind of architectures, and it just never really works.
00:18:36:28 - 00:19:02:26
Sam
The history of most large scale database applications end up in the same way, looking the same
way in similar ways. And we've provided that in a very generalized manner, which is itself which
is a really hard task. I mean, operations and good operations, it's not about being kind of fancy
and crazy, like you're just not going to you're not going to kind of crack the nut on, like, okay, I
don't have airplane advances in airplanes.
00:19:02:26 - 00:19:22:22
Sam
Right? Like the physics of how a wing creates lift is like, it's written, it's done. But now the the
operations of making sure there's no single points of failure in that process, and it can continue
and it can do the process over and over again is the bit that's difficult and takes a lot of
knowledge and sedimentary knowledge and layers built up.
00:19:22:22 - 00:19:27:02
Sam
And that's what we have. That makes us pretty different.
00:19:27:04 - 00:19:52:18
Jens
Also one, one, one thing I'm interested in is so planet scale it, at least from the outside, it looks
like you're you're largely basing on top of vitess, which is an open source project. Yep. Like you
said, coming from from Google, Google or my understanding is it was something it was used for,
for YouTube. Right? Yes.
00:19:52:21 - 00:20:00:26
Jens
And so being an open source project and you are a company hosting that open like obviously
you're doing more than just hosting a project you were the.
00:20:00:26 - 00:20:02:16
Sam
We are the Maintainers as well. Yeah.
00:20:02:19 - 00:20:30:03
Jens
Okay. But one of the biggest fears of like startups with open source projects is like, yeah,
Amazon could just take vitess and and hosted like they they can probably do it cheaper. They
have data centers etc., etc.. Like you probably saw like all this back and forth between like, like,
like OpenSearch and Elasticsearch and other database companies.
00:20:30:03 - 00:20:35:03
Jens
Like how, how are you thinking about this, this topic.
00:20:35:05 - 00:20:56:12
Sam
I think that, you know, there's a this is a world where that's true, that can happen. vitess is like
half, half of our offering, right? A lot of the the stuff that makes planet scale really special is not
open source. And vitess is like it's a code base for the engine of our product. And it's incredibly,
incredibly important to us.
00:20:56:14 - 00:21:18:07
Sam
And yes, it would be a big step up, like it would be a big benefit to certain companies to go and
just take that and use it. And there's people that self host vitess at very, very large scale, and it
works for them. It's more like, can they replicate how well we operate databases and they
haven't.