---
title: Plugin Packaging and OCI Storage
slug: ep27-12-plugin-packaging-and-oci-storage
series: The Good Thing
episode: 27
chunk: 12
segment: Plugin distribution and artifact management
timecode: 00:51:17 – 00:54:02
start_time: 00:51:17
end_time: 00:54:02
speakers:
  - Jesse
  - Jens
  - Dustin
topics:
  - Plugin Packaging
  - OCI Storage
  - Artifact Management
tags:
  - plugin-architecture
  - oci
  - artifact-management
entities:
  - Cloudflare
  - WunderGraph
summary: Jens and Stefan detail how plugins are packaged and distributed, exploring OCI storage, Cloudflare registry usage, and artifact management workflows.
---
00:51:17:17 - 00:51:40:18
Jesse
Well, if you're using the if you're not using Cosmo Cloud, like, if you're self-hosting, you can
directly include the plugins code in the file system next to the router. You can do this via a PVC
in Kubernetes, or you can include it directly in the image. You can use sef, whatever, just put it
there in the file system.
00:51:40:20 - 00:52:17:08
Jesse
However, if you are using our cloud product, you're able to use the publish and pull workflow
that's built into WGC, which uses Docker to package up your plugin into, uses the Docker
builder to package your plugin up into an OCI image and ship it off to our registry, which can
then be pulled down by the router alongside your updated, execution config that includes the
new version of the plugin, and it's schema, and the router can automatically, unpack that image
into a working directory and run it, as it would a local plugin.
00:52:17:11 - 00:52:26:00
Jens
So you're abusing, OCI storage to, to upload plugins and download them?
00:52:26:03 - 00:52:54:20
Jesse
I wouldn't say I'm abusing it. I would say that we're one of the pioneers in the new space of
using OCI stores as generic artifact stores. There's other projects in this space like, helm uses
OCI specifically not to contain container images. And there's a couple new projects that are
being started up, like generic image registries that don't have any of the Docker Mime types in
them, which are a real detriment to this process.
00:52:54:20 - 00:53:23:11
Jesse
Is having your Mime type stuck as like tar. Docker.image or some other nonsense like that,
because the OCI spec as it exists right now is really derivative of the Docker image spec. But
the whole, the whole, underneath them. What's it called? Cloud Computing Foundation with
Linux Foundation. They're really trying to move it away from that and into just a real nice content
addressable, it has SHA checking all kinds of other nice features that you would want out of an
artifact store.
00:53:23:13 - 00:53:35:29
Dustin
I also have a question to Jesse. I think, or maybe you wanted to ask. I'm not sure, but, we didn't
we didn't build or deploy or maintain our own, Docker registry. Right.
00:53:36:01 - 00:54:02:23
Jesse
We did. It's, it's based on it's based on Cloudflare workers, and it uses R2 as the backing
storage. This allows us to deploy it, in all the regions where our customers are and provide fast
service without depending on an external service like Docker Hub or GHCR. In the future we
might have some sort of option for using your own registry, but that's, on the horizon now.
