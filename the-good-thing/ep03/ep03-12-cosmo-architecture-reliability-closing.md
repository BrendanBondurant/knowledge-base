---
title: "Cosmo Architecture Reliability and Closing"
slug: "ep03-12-cosmo-architecture-reliability-closing"
series: "The Good Thing"
episode: 3
chunk: 12
participants: ["Stefan", "Dustin"]
segment: "Final discussion about Cosmo's architecture reliability and episode closing"
timecode: "00:53:01:19 - 00:56:45:00"
start_time: "00:53:01:19"
end_time: "00:56:45:00"
speakers: ["Stefan", "Dustin"]
topics: ["Cosmo Architecture", "Reliability", "Self-Hosting", "Infrastructure", "Closing"]
tags: ["cosmo-architecture", "reliability", "self-hosting", "infrastructure", "closing"]
entities: ["Stefan", "Dustin", "Cosmo", "Cloudflare", "CDN"]
mentions: ["self-hosted router", "control plane", "CDN", "uptime", "SLAs", "autonomous"]
summary: "Stefan and Dustin discuss Cosmo's architecture where customers self-host the router while interacting with the control plane. They explain the benefits of this design where customers' infrastructure isn't affected if Cosmo goes down, and discuss the two deployment options for router configuration."
---

00:53:01:19 - 00:53:26:20
Stefan
Yeah, basically. And it works pretty well. One of the biggest things I hear with like, our
customers. So for example, we we have a great uptime. Obviously, since we provide Cosmo
managed, we have to adhere to certain SLAs. And, since customers self-host the router. So
they sell post a router on their infrastructure and then they interact through our studio on our
platform with a, oh, are we almost at time?

00:53:26:20 - 00:53:32:27
Stefan
this, right?
I just realized that's okay. I just realized we're almost that time. And you have an interview after

00:53:33:00 - 00:53:34:03
Dustin
Yeah.

00:53:34:06 - 00:53:53:11
Stefan
Okay. So I will ask this last question, and then we're going to have to end a little bit early
because we started late. But Dustin is interviewing and so we're actively hiring. But the router is
self-hosted. It interacts through the control plane, which is a Cloudflare, like you said, what
happens if our infrastructure goes down?

00:53:53:13 - 00:54:09:29
Stefan
The customer has the router self-hosted on their infrastructure, but their customers won't be
affected. Right? The only things that will be affected is they maybe can't log in to the Cosmo
studio and stress a little bit on why we made that architectural decision and like, what would be
the impact if we go down.

00:54:10:01 - 00:54:50:14
Dustin
Yeah. So first of all, we didn't want to, enforce people or to opt in our cloud because there are a
lot of use cases where people don't want to use cosmo router. And because we have integrated
opentelemetry, it's their choice if they want to push the data, for example, to Datadog to New
Relic. So, yeah. And also it's very, very important that we can say that they're there, that the that
our infrastructure is not a critical factor for being operational on their end.

00:54:50:16 - 00:55:04:18
Dustin
So it's it's it's it's a huge benefit also for us that we don't you can can't break customers will be
we are yeah. We are not the de facto when, when there, have issues.

00:55:04:20 - 00:55:10:18
Stefan
So I think this comes from our learning as well from Cosmos Cloud. You remember like when
flag would go down, our customers were affected.

00:55:10:21 - 00:55:37:00
Dustin
Yeah. So right now, there are two ways to, to deploy the super graph configuration. So you can,
you can build it locally and pass it directly to, to the, rather than the routers completely,
autonomous. It has no connection at all to the control plane and to, to Cosmo, except for
analytics purposes. But this is, handled gracefully when something goes wrong.

00:55:37:02 - 00:55:58:28
Dustin
And then there's the option that, you can issue a graph token, and the router will pull that
configuration from the CDN. And even in case of the CDN is down, by the way, we provide like
six nine on the, on the kind of ability even in that case, the router would be still function.

00:55:59:01 - 00:56:08:08
Dustin
It would just not be able to pick up the latest graph configuration that has been recently pushed,
to our control plane. Yeah.

00:56:08:11 - 00:56:21:05
Stefan
No, it's a good explanation. So I know we're a little bit over, but Dustin, thanks for joining me
today since Jens is out of town and, really appreciate you kind of just talking into it for your first
podcast. You did a good job. I mean, I told you, it's very chill. We just relax. We talk a little bit.

00:56:21:05 - 00:56:22:19
Stefan
Tech. What do you think?

00:56:22:22 - 00:56:28:15
Dustin
No, it was a great experience. A little bit of a time, but, Yeah, I'll.

00:56:28:15 - 00:56:41:00
Stefan
Let you get to it then. You got to get to your interview, right? Yeah. As long as you enjoyed it. We
had a good time. But Dustin, thanks so much for joining us. I'm going to clip this up. You'll see it
on LinkedIn. So make sure you share. And then yeah thanks so much I'll see you soon.

00:56:41:03 - 00:56:44:11
Dustin
Thank you. But.

00:56:44:13 - 00:56:45:00
Stefan
Later. 