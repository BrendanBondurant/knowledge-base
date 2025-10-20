---
type: podcast-chunk
title: Business Impact of Performance and Conversion Rates
slug: ep02-08-business-impact-performance-conversion
series: The Good Thing
episode: 2
chunk: 8
segment: Performance Impact on Business
timecode: 00:30:01 – 00:33:43
start_time: 00:30:01
end_time: 00:33:43
speakers:
  - Stefan
  - Jens
topics:
  - Business Impact of Performance
  - Conversion Rates
  - Customer Abandonment
  - Federation vs REST
tags:
  - startup
  - ai
  - api-design
  - benchmarking
  - bff-pattern
  - cache-warming
  - cosmo-router
  - federation
  - go
  - graphql
  - graphql-federation
  - microservices
  - rest
  - rest-apis
entities:
  - WunderGraph
  - Coinbase
  - Super Bowl
  - GraphQL Federation
  - REST APIs
summary: Stefan and Jens discuss the business impact of slow performance, using examples
  like Coinbase's Super Bowl ad crash. Jens explains how federation provides organizational
  benefits over REST APIs, highlighting how federation enforces schema transparency
  and enables better team collaboration. They discuss the difference between federation
  and REST approaches in terms of complexity management and organizational structure.
---

00:30:01:06 - 00:30:19:05

Stefan

What is the impact of slow performance on the company. So for example, they launched this ad

on the Super Bowl. And if you guys remember and Jens you might not remember this but coin

Coinbase they did an ad with just a floating QR code. And that was the entire ad. And a bunch

of people scanned it.

00:30:19:05 - 00:30:33:18

Stefan

And so many people at the Super Bowl scan it that they crashed the website. Let's say the

website doesn't crash, but it's slow. Like, what are the business impacts of slow performance

times that the pre warming cache offers for like the business impact?

00:30:33:20 - 00:31:00:27

Jens

I think I don't have to to teach business people that especially if you're in in areas like e-

commerce or something like every second counts in terms of yeah, people abandoning the

website or something. So yeah, latency or or high latency means you, you lose sales as as

simple as that. You lose customer conversion.

00:31:00:27 - 00:31:33:12

Jens

So it's it's super important and thus sorry to drift back to the technical side, but I want to

emphasize on, on one thing because I keep seeing discussions around REST versus GraphQL

and, REST versus federation and, other things. And well, one thing that that is, I think it's very

important to talk about because sometimes I hear people say like, yeah, but we can do it with

with REST and it will be faster and so on and so forth.

00:31:33:14 - 00:32:05:24

Jens

The reality is, and this is like it took me very, very long to to kind of conclude this, but if you have

a website that does what we just described and it's using REST APIs, it is very likely that you

are not fully aware what kind of Rest API calls this website does until it's fully functional versus

you have a federated GraphQL query and you're now complaining about like, hey Jens, why

does it take 10s to plan?

00:32:05:26 - 00:32:43:25

Jens

And the thing is, with Federation, we are fully aware of the complexity to load this page and, the

computation to load the data from, from all these, from all these subgraphs, from all the

microservices. This computation, it happens when we start up the router when we warm up the

cache, we compute this once and then we have a description of how do we get the data for this

page versus if you have a rest API, the front end starts up and it starts firing all these rest API

calls.

00:32:44:02 - 00:33:18:19

Jens

So with a rest API approach, this whole computation of getting all the data to make the the the

the website work, it's the federation in the sense it's happening in the browser and it's

happening at runtime when the user waits. And now the question is like you have latency

between the front end and all your microservices. And this means going back and forth between

the front end and all those microservices.

00:33:18:19 - 00:33:43:24

Jens

It's much slower than doing. It's on the backend. So now you could say, okay, Jens, let's solve

this problem with rest. We move this computation, we move it into the backend, we create a

backend for front end, which creates a single rest API that federates the data from my

microservices. You can do this now you make a single rest API call to this BFF. 