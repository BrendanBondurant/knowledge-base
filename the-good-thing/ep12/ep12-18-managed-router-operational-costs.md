# ep12-18-managed-router-operational-costs

**Time Range:** 01:08:23 - 01:12:03

**Topic:** Why WunderGraph avoids managed routers and Apollo’s misstep

---

01:08:23:13 - 01:08:42:28
Jens
But on the other hand you can kind of see like I'm not just ranting, but it also guides our own
decisions because, Apollo built a service to host routers for customers. This is ridiculous. Like.
01:08:43:00 - 01:08:43:19
Stefan
why
01:08:43:21 - 01:08:47:07
Jens
I don't know, have they killed it already or is it still alive?
01:08:47:10 - 01:08:53:09
Stefan
It's still a thing. I was talking to somebody the other day about it. Like the whole sit around with
solution and wrapper on a wrapper.
01:08:53:09 - 01:09:28:25
Jens
So, so like given our experience with the SDK and our learnings from like how hard it is to run
to, to run compute at scale, like why do you why on earth like I know they have more than 100
developers, but why on earth do you want to run routers for people? Because what it means is
you have to have people on call like you.
01:09:28:25 - 01:09:47:25
Jens
You have to make sure everything works. If a router doesn't work, it can be your fault. It can be
the customer's fault, I don't know. And then at the end of the day, how are you charging so you
can find some sort of proxy metric, for example, you can invent, I don't know, TPS or whatever.
01:09:47:25 - 01:09:50:19
Stefan
Or something like a graph, some something, your.
01:09:50:19 - 01:10:14:03
Jens
Compute unit, whatever. Yeah. And this is, this is all bullshit because what you're doing is you
you take the compute from AWS and you put something on top, and now I can, I can. So you
put your margin on top and now I can I can draw a line if I put, you know, I can draw a graph.
01:10:14:07 - 01:10:57:25
Jens
And if I, if I put big enough numbers into this graph, I can now calculate if I use the managed
service versus I build a team to run routers. And then you can see the the graphs of the cost.
And you can see exactly at which point you should stop doing stop using such a service. And
and here's a problem, because, in most cases it never makes sense because if you have
subgraphs, it means you have a platform team that operates the infrastructure to run subgraphs.
01:10:57:28 - 01:11:34:24
Jens
So it means the company that uses federation, they already have people on call that the
subgraphs don't break, because if they break, you're offline. So let's say you are, I don't know,
big company Coinbase. If your subgraphs are down, nothing works. So if you now use a
managed router, what happens is if the if the super graph doesn't work in production, two
companies now need to collaborate to fix the problem.
01:11:34:29 - 01:11:53:13
Jens
like.
So you don't just buy a managed router. You also need people on call internally in case of an
incident to figure out why. Is it broken? Is it us? Is it them? Yeah. And you're paying extra for
01:11:53:15 - 01:12:03:04
Stefan
It doesn't make sense. What? It doesn't make sense. Now, I'll leave you in there, but, one sec
my dog is, like, freaking out. But if you guys haven't seen.