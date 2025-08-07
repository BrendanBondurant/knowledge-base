
---
title: LLM Accessibility and Enterprise Stickiness
slug: ep25-13-llm-accessibility-and-enterprise-stickiness
series: The Good Thing
episode: 25
chunk: 13
participants:
  - Stefan Avram
  - Jens Neuse
  - Kevin Swiber
segment: AI Attribution and Ethics Discussion
timecode: 00:54:27:11 – 00:58:02:20
start_time: 00:54:27:11
end_time: 00:58:02:20
speakers:
  - Kevin
  - Stefan
  - Jens
topics:
  - AI attribution and data source transparency
  - Content scraping monetization ethics
  - Cloudflare scraper blocking considerations
  - GraphQL vs REST with LLM query capabilities
  - Technology adoption lifecycle and persistence
tags:
  - ai-attribution
  - data-scraping-ethics
  - cloudflare-blocking
  - graphql-rest-llm
  - technology-persistence
  - ai-ethics
entities:
  - OpenAI
  - Cloudflare
  - GraphQL
  - REST APIs
  - LLMs
  - MCP (Model Context Protocol)
  - Technology adoption lifecycle
mentions:
  - Data source attribution problems
  - Money filtering to original sources
  - Scraper blocking strategies
  - OpenAI charging considerations
  - AI bias and ethical issues
  - GraphQL roller coaster adoption
  - LLM as additive technology
  - Natural language GraphQL querying
summary: |
  Kevin discusses the attribution problem in AI, where data sources can't be traced back for revenue sharing, leading OpenAI to capture all advertising revenue. This raises ethical questions about scraper blocking and charging AI companies for data access. The conversation shifts to GraphQL's future with LLMs, where Kevin explains that GraphQL won't be replaced but will become additive, similar to how MCP complements rather than replaces existing technologies. He notes that GraphQL can now be queried through natural language interfaces via MCP.
---

00:54:27:11 - 00:54:44:14
Kevin
And like, they're really just getting started. So all this stuff is, is brand new. I think it will be in a
much different place in five years, on on the enterprise side, I think on sort of the cutting edge
side, we're in a new place every three months. So.
00:54:44:16 - 00:54:57:28
Stefan
Well, so very well. So and Jens, by the way, to your point about the ads thing, I was thinking that
exactly when Kevin was saying I was like, wait till you're here on ChatGPT. And it's like, well,
this is loading. Please take a look at an ad from our sponsor. And I'm like, oh my God, when is
that?
00:54:57:28 - 00:54:58:19
Stefan
They're going to come.
00:54:58:19 - 00:55:26:03
Kevin
Yeah, but the difficult part of that is like attribution, right? Like you don't even know where the
data came from at that point. And so like there's no money filtering back to the source. It's just
OpenAI taking your money at that. At that point. Right. And so that that creates a whole other
issue there of do I try to block the, the scrapers that are coming to my site like Cloudflare is
looking at, at some of this as well?
00:55:26:05 - 00:55:50:06
Kevin
Do I charge, do I try to charge OpenAI for, for coming to take my data? Right. It's a there are a
lot of things we still need to figure out. There's certainly a lot of ethical things we still need to
figure out with AI and biases. So yeah, I think I think it's going to be, it's going to be a really long
decade of, of really trying to get our hands around this technology now.
00:55:50:06 - 00:55:57:07
Stefan
Well said. And I was laughing one one go ahead Jens. Because I actually forgot my question.
00:55:57:10 - 00:56:32:28
Jens
Okay. So we're we're we're, a GraphQL vendor, and I think this, this wouldn't be a good podcast
without, a GraphQL, roast. So I'm curious from, from your perspective, if you take REST APIs
and we add an LLM, we we have a query language, right. We can query the REST API. So in
the and the age of LLMs do we, do we actually need GraphQL or is it, is it like like a dead thing?
00:56:33:01 - 00:56:57:27
Kevin
You know, well, like I said, I don't think this technology actually dies after it reaches a certain
level of, you know, widespread adoption. It sticks around forever. I think we we've gone on a
roller coaster with GraphQL, where you know, it comes out and that a lot of people are saying
this is the only thing I ever need for the rest of my life is GraphQL.
00:56:57:27 - 00:57:19:19
Kevin
I don't need anything else. And then I think we've we've kind of settled down to a point of saying,
okay, here are GraphQL strengths. And here's where I need GraphQL. And here's where I need
other kinds of APIs. Right. Instead of being a complete replacement for everything, it became
additive. And LLMS I think are similar.
00:57:19:19 - 00:57:46:28
Kevin
Like, we're not going to an MCP is similar. Like we're not going to replace everything. Or with
this new technology, it's going to be additive. And we just need to figure out where it really fits in.
There are certainly, you know, folks who are exposing GraphQL through MCP now. And so you
can like, you know, do queries and mutations, through a natural language interface.
00:57:47:01 - 00:58:02:20
Stefan
Yeah. Also, I also like you could tell very well that you're a very good consultant because you're
always like, it depends. Let me understand the use case first. And you go in first by saying, well
it always depends. And like whenever, like we talk to a consultant who has a very strong opinion
on something. I'm like, you don't know the full use case.