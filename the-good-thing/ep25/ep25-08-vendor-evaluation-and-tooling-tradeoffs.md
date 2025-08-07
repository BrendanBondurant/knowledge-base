
---
title: Vendor Evaluation and Tooling Tradeoffs
slug: ep25-08-vendor-evaluation-and-tooling-tradeoffs
series: The Good Thing
episode: 25
chunk: 8
participants:
  - Stefan Avram
  - Jens Neuse
  - Kevin Swiber
segment: Tool Recommendations and Evaluation Criteria
timecode: 00:31:06:18 – 00:35:12:21
start_time: 00:31:06:18
end_time: 00:35:12:21
speakers:
  - Stefan
  - Jens
  - Kevin
topics:
  - CTO decision-making and risk management
  - Analyst shortlist benefits for vendor evaluation
  - Kevin's tool recommendations and approach
  - Open source vs commercial gateway options
  - SaaS control plane with distributed data plane architecture
tags:
  - cto-decisions
  - risk-management
  - tool-recommendations
  - open-source-gateways
  - saas-control-plane
  - distributed-architecture
  - gitops-approach
entities:
  - Fortune 100 companies
  - Kong
  - Tyk
  - Gravitee
  - Zuplo
  - GitOps
  - SaaS control plane
  - Data plane
  - RBAC (Role-Based Access Control)
mentions:
  - Three vendor shortlist strategy
  - Risk management in tool selection
  - Open source gateway options
  - Customer managed products
  - Centralized control plane comfort
  - Distributed data plane hosting
  - Git ops workflow preferences
  - More recommended than avoided tools
summary: |
  Stefan and Jens discuss the value of analyst recommendations for CTOs making vendor decisions, emphasizing risk management over just good decisions. Kevin shares his approach to tool recommendations, mentioning Kong, Tyk, and Gravitee for open source options. He explains the growing trend toward SaaS control planes with distributed data planes, and highlights Zuplo's GitOps approach for specific market segments. Kevin notes he's recommended more tools than he's advised against.
---

00:31:06:18 - 00:31:07:17
Stefan
Yeah, I think that's super well said.
00:31:07:18 - 00:31:31:29
Jens
1 of the big, benefits of, of analysts I see is let's say you're you're a CTO of a fortune 100
company. You want to you want to start an API initiative, and you, you you don't know what is
the right thing. You can go to an analyst and say, hey, here's my requirements. What's your
recommendation? They give you a shortlist of three vendors.
00:31:32:02 - 00:31:57:17
Jens
You evaluate them and that's that's probably a very good starting point. And if you pick any of
the three it will probably and be an okay solution. And that's ultimately in in in that kind of roles.
It's also a lot about like risk management. It's not just like making a decision but not making a
bad decision because it can it can, affect your job.
00:31:57:17 - 00:32:01:21
Jens
So I, I think the model makes sense. Right.
00:32:01:24 - 00:32:16:04
Stefan
It's a very fair model. Like I think I would agree. I mean, Gartner, what they do is they provide
you a service just based on like what you said, like you do pay to get in and if you are a big
company, but that doesn't necessarily mean you're going to be put in the quadrant. The
quadrant has rules.
00:32:16:06 - 00:32:34:17
Stefan
And also the analysts stay very fair, which I appreciate. They put smaller vendors into there.
They put bigger vendors into there. My my question though is knowing that and now your
background is I mean, just given your your entire experience. But now as a consultant, what are
some tools that you recommend? If people come to you and they're like, hey, like I'm looking for
a gateway.
00:32:34:24 - 00:32:44:09
Stefan
Like, what are some of the tools that you go top of mind where you're like, hey, I'd work with
these three or this type, but tools that you recommend in the API space.
00:32:44:12 - 00:33:07:00
Kevin
Yeah. You know, there are tools that I definitely do not recommend. I don't think I should call
those folks out necessarily. But, you know, I think there are, there are a lot of great tools out
there, and I think that there are good open source tools out there as well, for, for folks who want
to get started.
00:33:07:02 - 00:33:35:06
Kevin
You know, typically, I, I look at, what their requirements are. If it's just like one small project that
they need to to stand up and get running, I'll typically do an evaluation between, you know, like,
kong and tyk, maybe, maybe gravity who is open source, at least their open source version, and
kind of see where that's going to fit for them.
00:33:35:08 - 00:34:07:21
Kevin
Of course, looking at, you know, are their needs going to grow and expand? And what does that
look like to a lot of open source projects? Have vendors associated with them as well. You
know, so they have they have hosted products. They have, customer managed products, all
sorts of things. What a lot of folks are kind of leaning towards now, especially with kind of cloud
deployments, is, there's a bit more comfort with having like a centralized control plane that that's
hosted as a SaaS.
00:34:07:24 - 00:34:27:12
Kevin
And then a distributed data plane that, that they host themselves. So having all the gateway
runtimes running their own infrastructure essentially, but then doing management of all of those
gateways through a centralized place. So, you know, they log into the SaaS and they can set
permissions and sort of RBAC stuff for, for other folks logging in there.
00:34:27:19 - 00:34:52:21
Kevin
And then manage who has sort of control over that. And then there are, you know, folks who are
looking for things like, a cleaner sort of git ops, approach to it. Right. And so, there are vendors
like, like Zuplo that, serve a particular section of the market really well, and have a decent kind
of git ops flow to them.
00:34:52:21 - 00:35:12:19
Kevin
So, I mean, it really it really depends. I would say there are probably, there are probably more
vendors that I've recommended, depending on the specific use cases and the needs of the
customer. There's, there's more that I've recommended than I've said stay away from, you know.