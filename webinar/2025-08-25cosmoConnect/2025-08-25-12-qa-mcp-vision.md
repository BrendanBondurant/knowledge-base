---
title: "Q&A: MCP Vision, Router as MCP Server"
start_time: "00:57:04"
end_time: "00:58:51"
tags: [mcp, router, ai]
---
00:57:04:08 - 00:57:24:04
Jens
And so in the in the future, you will see that we're, we're currently focusing on, on the backend
part. And in the future we will focus more on the on the front end part, because we, we think, the
graph is super powerful, but we don't want to force you into into how you consume it or what API
style you're, you're using.
00:57:24:04 - 00:57:27:07
Jens
Just use whatever fits your use case. I.
00:57:27:07 - 00:57:54:05
Dustin
Want to, can I say something? I want to emphasize emphasize one point. I think it's a little bit of
hidden. And Jnes mentioned that already. You can actually build MCP servers as a gRPC plugin
and expose that through, our MCP gateway without dealing with MCP specification at all. I think
this is a very underrated, feature we got for free here.
00:57:54:07 - 00:58:18:15
Dustin
And, you know, it's, it's very powerful. So, you build your plugin, you expose, for instance, on
API endpoints, you design your subgraph schema, you define, define your persistent operation
that you want to make accessible as a tool to your AI tooling. And that's that's pretty much it
without ever getting in touch with MCP. Internals.
00:58:18:17 - 00:58:25:18
Jens
What you say is the cosmo router is can also be used as an MCP server. Right. It can expose
MCP tools.
00:58:25:20 - 00:58:26:18
Dustin
Exactly.
00:58:26:20 - 00:58:51:08
Jens
And cosmo router can run plugins. So you can put stuff in the plugin, create the query. And now
you have an MCP tool right? Yep. Okay. Cool. What other questions do we have?