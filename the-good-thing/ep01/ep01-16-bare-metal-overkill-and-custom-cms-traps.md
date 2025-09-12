---
title: Bare Metal Overkill and Custom CMS Traps
slug: ep01-16-bare-metal-overkill-and-custom-cms-traps
series: The Good Thing
episode: 1
chunk: 16
segment: Self Hosting Distractions and the Real Customer
timecode: 00:49:40 – 00:53:29
start_time: 00:49:40
end_time: 00:53:29
speakers:
  - Jens
topics:
  - Kubernetes on Bare Metal
  - Overengineering
  - Custom CI/CD
  - Developer Distractions
  - Ignoring Business Priorities
  - Custom CMS Trap
tags:
  - kubernetes
  - startup
  - ai
  - database
  - go
entities:
  - Jens Neuse
  - Kubernetes
  - GitLab
  - Azure
  - CI CD
  - CMS
  - AWS
  - Kubernetes on bare metal
summary: Jens recounts how his team built a bare metal Kubernetes cluster, self-hosted GitLab, and custom CI/CD pipelines, prioritizing engineering fun over business outcomes. They neglected core goals like attracting readers and improving ad targeting, focusing instead on technical pride projects. He describes rejecting all commercial CMS solutions to build their own, assuming their needs were unique, illustrating a common corporate trap
---


00:49:40:24 - 00:50:14:01

Jens

So it was very clear, if you have this stuff and you're, you're it's on a lease, then you have to use

it. So the first actual decision we made this we we built up a team to run our own Kubernetes

platform on bare metal. And that makes a lot of sense, because if you are, an online news

website, the most important thing you should be concerned about is how do I run my own

Kubernetes cluster?

00:50:14:03 - 00:50:43:29

Jens

That's so obvious because, all your customers, they every morning they open the website, they

want to see the news. And this isn't only possible with your own Kubernetes cluster like just

using AWS, just outsourcing the hard things and focusing on how could you make news better.

That would be such a boring thing, but building your own Kubernetes cluster on bare metal that

that's exciting, right?

00:50:44:05 - 00:51:15:25Jens

And we we could spend so much time and it was so much fun. We built our own CI CD pipelines

like even I have a contribution as a repository from from from Azure. They have like a thing

where you can run your own CI like CI, CD runner on Kubernetes with GitLab. So we had

obviously we had our own self-hosted GitLab because you, you would not use something like

GitHub.

00:51:15:25 - 00:51:41:15

Jens

You you run your own GitLab with your own database. So we had our own Kubernetes with

GitLab runners on our own, Kubernetes on bare metal and everything, and our own data center.

And yeah, it was a lot of fun, but we didn't do much for the for the business. And, that that's

that's a typical corporate thing.

00:51:41:15 - 00:52:06:28

Jens

You know, you you have developers. They are very far away from, from from the customer like

our we had like a two sided marketplace. We had the, the people who want to see the news.

And we had the advertisers who want to put, advertisements on the news website. That is what

we should be concerned about. We should be concerned about how can we make the website

faster?

00:52:07:05 - 00:52:30:11

Jens

How can we make the offerings on the website better to attract more users? And how can we

build better systems for advertisers to to make more money to address the right people and to

to show the right ads for the right people? Because if you're like 20 years old, you you don't

need like, things for 60 year old.

00:52:30:11 - 00:53:01:22

Jens

So something that that should have been things we should be concerned about. But we didn't

care about that. We cared about our bare metal. And the other thing is, we we if you are a news

website, you need a content management system. And, we did, a very thorough, thorough

market analysis. And we figured out that there's absolutely no content management system that

can, satisfy our requirements.

00:53:01:25 - 00:53:29:19

Jens

And obviously, we had to build our own content management system. And, I mean, I built I built

shake, an app where you can shake your phone, and it had, app and the front end and the

backend, so I can I can also build my own content management system. And so we had, a team

