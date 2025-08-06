# ep26-03-federation-ownership-negotiation

**Time Range:** 0:08:50 - 0:13:03

**Topic:** Federation adds complexity: ownership, negotiation, alignmen

---

00:08:53:26 - 00:09:08:10
Stefan
Who is saying we got to get the background first? Oh, I'm boring to the Sam. How did we get
into databases like that? Just for the audience. So they know, like, how did you get into
databases? And then we're going to get into the nitty gritty details of tech, like how did you end
up at planet Scale? How did you start it?
00:09:08:10 - 00:09:09:13
Stefan
Just like that part.
00:09:09:16 - 00:09:31:18
Sam
So I I got into databases the same way I think most people do, which is it's the worst problem at
most tech companies they work at, and they kind of gravitate to those issues and start fixing
them. I was doing that of, like various different companies. And then I went up, went to a small
but growing company called GitHub to be their first sort of database engineering hire.
00:09:31:21 - 00:09:56:01
Sam
Worked there, eventually became VP of engineering, running like the platform infrastructure
teams there, which, you know, basically everything below the web app. And, you know, took that
to being like the 40th largest website on the planet, then worked at meta on the traffic
engineering team, which is a significant portion of the internet's traffic, and obviously running at
extreme stream scale.
00:09:56:03 - 00:10:15:21
Sam
And then I came to planet scale, you know, planetscale was founded out the back of the Vitess
project, leaving Google. It was it was really more of a consultancy and not really a business
with, with a web product, with like a hosted product. So I came to like, kind of join and build that
hosted product and then took over running the company.
00:10:15:23 - 00:10:36:03
Sam
A little while after joining. Yeah, we became very successful. I mean, the we went from having
just a tiny, user base to now just a very, very large user base in some of, the largest relational
databases in the world running on the platform, as well as a ton of very large scale kind of
consumer platforms that run on top of us.
00:10:36:03 - 00:10:50:07
Sam
It was really fun to know that, you know, pretty much every working adult in America or, you
know, in the tech industry will interact with products built on top of that scale every single day,
which is really cool, No well said.
00:10:50:12 - 00:10:56:24
Stefan
Jens over to you now on the tech questions. Now we got, we got the background out.
00:10:56:26 - 00:11:25:17
Jens
Okay. Well, one thing I'm interested in and, I'm not a database expert, but a user, but I, I read
about planet scale metal. Yeah. And it's it's very interesting. The graphs you're showing, the
performance and everything, like, in very simple terms, why is planet scale metal so much more
performant than other database solutions?
00:11:25:19 - 00:11:47:29
Sam
So the reason it's more performant is a very simple one. And it's the same thing anyone could
achieve on a local server, you know, a server that they rack themselves is that it just uses, the
NVMe drives that are inside the server, which sounds like when you say it like that, it sounds
silly and, unimpressive. Like obviously you should use the disk inside your server, but in the
cloud that doesn't happen.
00:11:48:01 - 00:12:10:09
Sam
The main reason is really impressive that we do it. The way we do it is because we, we, we're
running those bare metal inside AWS and inside Google by using the machines that they use to
build their services on top of. And and these machines are ephemeral, so the the disks don't
stick around. If you're racking your own servers in a data center, you have rate arrays inside
those servers, and you can go and access them if you really needed to to get access to the
data.
00:12:10:09 - 00:12:32:27
Sam
We can if we provision a server, it's gone forever. If it fails, it's gone forever. So we handle all of
this state, running on ephemeral machines that happen to be extremely fast and much cheaper
than the other hosts that you get inside Amazon. And it means that we get this huge
performance increase, like, you know, Aurora and some of the other databases, they they just
aggregate storage and compute.
00:12:32:27 - 00:12:49:13
Sam
They separate those things, which means they put a network layer, in some form between the
the server process and the disks, which adds a significant amount of latency, to each query. We
don't do that and it makes it a lot faster.