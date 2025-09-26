---
type: podcast-chunk
title: Schema Slicing and Optimizing LLM Context Usage
slug: ep09-05-schema-slicing-llm-optimization
series: The Good Thing
episode: 9
chunk: 5
segment: LLM optimization strategies
timecode: 00:17:04:26 – 00:21:03:29
start_time: 00:17:04:26
end_time: 00:21:03:29
speakers:
  - Jens
  - Cameron
topics:
  - Schema Slicing
  - LLM Token Limits
  - Performance Optimization
  - Cost Scaling
tags:
  - llm
  - ai
  - benchmarking
entities:
  - GitHub
  - GraphQL
summary: Cameron explains the challenges of using large GraphQL schemas with LLMs,
  including speed, cost, and accuracy issues. He discusses schema slicing techniques
  to optimize performance by reducing context size, preventing token limit overflows,
  and improving query generation accuracy while managing costs at organizational scale.
---

00:17:04:26 - 00:17:30:23
Cameron
Yeah, there are several challenges to think of. So the first large challenge that I see to do it
quickly is especially when you get to the GitHub size schemas or you get to, you know, any
large GraphQL schema, you don't want to be putting that into the model every single time you
want to query it, you know, you want to figure out how to slice it and only give the model access
to the data it needs to generate that query.
Jens
why?
00:17:30:26 - 00:17:54:05
Cameron
So you want to do that because of speed, cost, You know, you can also hit the limit of the
maximum number of tokens that the model can actually process and context. And once that
happens, you know, it will lose parts of that memory. And for all you know, it might be that very,
very top line that it actually needs.
00:17:54:08 - 00:18:03:05
Cameron
query.
So you need to figure out what it needs in order to, in order to allow it to accurately generate the
00:18:03:08 - 00:18:14:10
Jens
You said speed, you said cost. is cost. Really? Like, are we talking about cost here or is it like
an artificial problem that you think it exists?
00:18:14:12 - 00:18:36:22
Cameron
It's in the current state of the market. It's not as large of a problem as I think it will be in the
future. As models get more and more stable and more and more accurate and more and more
able to do things, I think we'll see the cost rise. However, right now, you know, you're it's you're
constantly querying git all day.
00:18:36:22 - 00:19:01:12
Cameron
You're still not looking at, you know, if you're, constantly uploading 400,000 tokens, you're not
looking at a super nominal cost, like it's still something that will add up over, you know, a month
or two months or something. You know, it's not going to be tens of thousands of dollars, but it's
still, you know, if you have 20 engineers querying it, it still could be thousands of dollars.
00:19:01:15 - 00:19:13:16
Cameron
And that is something to kind of think about when you're looking at an organization. And how an
organization can implement a tool like this, at scale, is that scaling factor of cost?
00:19:13:18 - 00:19:35:06
Jens
Yeah. And and the other problem you mentioned performance. So let's say a schema has
hundreds of thousands of, of tokens. Do we always have to stick that into the, into the context
or, or like is that necessary. And also does it lead to good results or what. What is a better
approach.
00:19:35:08 - 00:20:00:05
Cameron
Yeah. So it when you just stick the entire schema in it leads to a very slow time to actually
generate, a query and generate the response. But it also is not necessarily the most accurate
because you're overloading the model with data. So you're giving it way too much information
for it to try to parse through all of it and know exactly what's happening.
00:20:00:08 - 00:20:51:09
Cameron
Because, you know, there could be like a user could be returned from both a search result and
from a viewer field or from a me field on the schema on the query type. So, you know, having it
identify the difference in those things is a little it it's not the greatest. You get some weird queries
out of that. And so by slicing up the schema into basically what I call like the root types, you're
able to do some very interesting things in order to actually calculate and figure out the vector
distance between the query and the and the different slices of the schema, allowing us to only
inject pieces and parts of the schema
00:20:51:09 - 00:21:03:29
Cameron
as opposed to the entire schema as a whole, which produces better performance, lower context
usage, and it also allows for better accuracy.