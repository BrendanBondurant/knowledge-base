# ep14-07-benefits-of-mcp-for-graphql

**Time Range:** 00:27:17 - 00:31:08

**Topic:** Why you need MCP for your GraphQL API

---

00:27:17:03 - 00:27:21:07
Dustin
In that case, this is pure. This is an algorithm.
00:27:21:09 - 00:27:44:07
Jens
Yeah. This is what I actually wanted to to get at that some problems, they are deterministic and
you can parse the query, take the AST and generate the JSON schema with an algorithm. This
algorithm can have tests. And now we are very much certain that the JSON schema is is right.
Or even if it's if it's wrong, we know we have a bug.
00:27:44:07 - 00:27:50:16
Jens
We can we can fix it. If you if you do this task with an LLM, it might be right, it might be wrong.
00:27:50:19 - 00:28:08:12
Stefan
But isn't it kind of? What I mentioned though, is that like with the schema checks, that you kind
of get the security that it'll work, so you get to the 80% vibe coded, but the 20% now with MCP,
with Cosmo, and with Federation in general, it makes sure that you're making the right
decisions, even though you, vibe, coded it.
00:28:08:14 - 00:28:17:11
Dustin
I would say it's a little bit different. I think the point here was you should not use LLM at all to do,
to solve this puzzle here.
00:28:17:13 - 00:28:39:29
Stefan
Okay. well said? And then, so if I scroll down a little bit I want to understand this part here. So
why you need MCP for your GraphQL API. And you listed these four points AI discovery,
operation control, rich metadata and instant integration. Can you walk us through each of the
points? Dustin. And then yeah. And also feel free to jump in and just kind of explain to us why do
we need MCP for our GraphQL APIs?
00:28:40:01 - 00:29:18:12
Dustin
Yeah, I think the first point ai discovery means it or it is more or less inherits the benefit of the
MCP protocol so that mcp allows to list tools and resource and so on. And this gives essentially
the the the power to, to to to list what is what is your MCP gateway capable of. On the other
hand, I think that's something about Jens mentioned like if you if you're building and or if you
have a route, a gateway which is connected by GraphQL federation, and you can integrate any
type of, of service.
00:29:18:14 - 00:30:07:26
Dustin
So essentially you can expose anything to AI because you can by the nature of GraphQL
federation, you can just write query that spans across multiple services and aggregate data. And
this this is yeah. No, this is more more about the operation control, where you can create trusted
documents on your file system, write the operation in a way that you only want to expose the
that the data you will, you want to expose to LLM, for example, let's say someone want you
want to expose, the list of employees so you can build dashboards or you can boost a report,
but you usually don't want to export the, the location, the
00:30:07:26 - 00:30:24:03
Dustin
h age. Yeah. Bank information. But the the way how you approach this, you just you do not
include this particular field in the trusted document. That's everything you have to do to limit
access to the, LLM
00:30:24:06 - 00:30:25:02
Stefan
Information.
00:30:25:05 - 00:30:52:09
Dustin
Rich metadata, which is really important. So I think this is also like a super, super power of
GraphQL. Because we have a unified, super graph schema, you can just add comments to the
type definitions to the root fields, and we will incorporate those information into the JSON
schema definition. Also the tool definition to to give the LLM everything to make the right
decisions.
00:30:52:11 - 00:31:08:10
Stefan
Okay. Yeah. And and then the last one is pretty explanatory. So you can connect with any of the
tools that you guys are using. ChatGPT claude cursor with minimal configuration. Yeah. What
kind of benefits do you want to add to. Kind of just like the benefits of MCP for your GraphQL
API.