---
title: "Q&A: Publishing Plugins to Cosmo Cloud, OCI Registry, Docker Builds"
start_time: "00:58:51"
end_time: "01:02:11"
tags: [plugins, cosmo-cloud, deployment]
---
00:58:51:10 - 00:59:22:24
Jens
I have a question for Jesse. If I build a plugin like what Dustin just did, Dustin did his make
pnpm thing and then he had a binary. So if I'm building my gRPC plugin and I want it to, I have
my my router running in some Kubernetes cluster. How do I get this binary. Which by the way,
probably my my MacBook architecture is the wrong architecture.
00:59:23:01 - 00:59:32:04
Jens
cluster?
How do I get the plugin built in the right way into the, router that's running on my Kubernetes
00:59:32:06 - 00:59:52:04
Jesse
Right. So what we're doing right now with the flow for publishing to Cosmo Cloud and having it
pulled down by the router is what we provide is a Docker file. It's not quite the kind of normal
Dockerfile you would write to package your application into, a Linux container. It, the very last
layer, instead of, like from Debian or whatever.
00:59:52:04 - 01:00:22:02
Jesse
It's from scratch. And that's because we actually just use the image that the Docker file
produces as a container for the working directory of your plugin, including, anything it might
need resources to run. And of course, the binary that is already been compiled for its target
architecture. We do support multi architecture builds just via docker which can use Qemu, or it
can use native cross compilation support in your language which is a big strong point of go and
a couple other modern languages.
01:00:22:02 - 01:00:52:13
Jesse
But if you're using something older like C++ and you're using a compiler that doesn't support
cross compilation on different operating systems, then you can use the native Qemu support in
Docker to do your cross-platform building. And then we publish it up to our OCI registry, which is
backed by Cloudflare, storage R2 to which can then be pulled down by a native OCI client
inside the router and unpacked, sort of the same way that you do inside of a container runtime
to like a var directory.
01:00:52:13 - 01:01:14:04
Jesse
If you might have seen that inside your Docker internals. We do that process, except it's not
being run in a C group or a namespace or anything else container like at the moment it's, purely
just being run as a sibling of the router. The OCI format is just a packaging construct for us. It
doesn't, it doesn't drag in the the container dependency.
01:01:14:06 - 01:01:42:21
Jens
So for dumb people like me, I, I do what Dustin did with his plugin bootstrapping. Then I run a
WGC command and it does some cool magic server S3 things. And then somehow the the
image, the, the plugin gets downloaded by my router and the router schedules, the plugin runs
the process and everything. So I don't really have to do much.
01:01:42:21 - 01:01:53:02
Jens
I just built my plugin and run a WGC command, just like I would publish a subgraph. Somehow it
just does a little bit more of things.
01:01:53:04 - 01:02:11:10
Jesse
Yep. For for sure. From the developer's perspective, this is all completely under the hood. We
provide the Docker file. When you initialize a plugin, we will eventually support more languages.
Then go for that as well. And it's all handled for that. From there, the only thing you need is
Docker support on your building OS.