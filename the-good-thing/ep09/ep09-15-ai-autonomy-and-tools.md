# ep09-15-ai-autonomy-and-tools

**Time Range:** 00:54:05 - 00:58:12

**Topic:** Limitations of AI autonomy and the role of tools and protocols

---

00:54:05:18 - 00:54:46:10
Jens
But now with this MCP thing, what you're saying is I don't have to define tools over and over and
over again and send them back and forth, but instead I can say kind of like, hey, here's here's
an API. I follow a contract and you can you can tell if you do this in the MCP spec, you can, you
can essentially like, yeah, you can prepare those tools, package them maybe, and then
someone else can just use the tool so someone else can say, okay, I have cursor and I want to
use, one example I saw there, someone built a tool that uses the Docker, the Docker daemon
so it
00:54:46:10 - 00:54:58:18
Jens
can talk to the Docker daemon and start containers. And so now if you enable this thing then
your cursor can now use Docker over JSON, RPC kind of.
00:54:58:21 - 00:55:22:16
Cameron
Yeah, exactly. So it allows just a really easy way to package up those tools that we, you know,
have already used. And it provides a way to package them and extrapolate them out so that,
you know, you're not having to write extensions for cursor, to in order to get it access to Docker.
You can just say, hey, add this to that model.
00:55:22:18 - 00:55:25:11
Cameron
Cool. Now I can access Docker.
00:55:25:14 - 00:55:54:13
Jens
Yeah. What I find kind of interesting is, you know, I'm, I, I would consider myself an observer, of
the hypermedia world, you know, there's, there's this group of. And do you know what
hypermedia is
Cameron
somewhat.
Jens
Okay. So I can only answer this in the, in the wrong way because depending on who you ask,
they will always say you're wrong.
00:55:54:16 - 00:56:24:08
Jens
But on a very high level, hypermedia is kind of like the web works. So you go to a website, it
returns hypertext, and in the hypertext you have URLs and you can follow them and it can
somehow, for example, return using using JSON LD or whatever schema. It can tell you there
are certain actions. And if you send a Post request to this URL, you can add something to the
shopping cart.
00:56:24:10 - 00:56:52:16
Jens
So that's kind of like hypermedia APIs. And what I find so interesting is now we have these
super smart models and everything and they are advancing. And still we, we go back to RPC
and hard coding tools because AI is not able to navigate the internet or like, like, is it really
necessary that we now map out the world in MCP?
00:56:52:16 - 00:56:56:15
Jens
Or where do you think this is going?
00:56:56:17 - 00:57:24:17
Cameron
Yeah, I think I think it's going to take steps. I think that I think MCP is a step towards making the
tools easier for the model to use. I think, you know, I think we'll continuously see, AI evolve into
where it eventually can, process the, you know, the hypermedia can process, you know, RSS
feeds. It can process, you know, even GraphQL schemas.
00:57:24:17 - 00:57:47:08
Cameron
Getting back to that, like being able to take that in and actually execute on it, based off of what it
can scrape and what it can find. But I think today it's still kind of we're still limited by the fact that
even beyond it's just it's a cloud thing, it's still just the end of the day.
00:57:47:08 - 00:58:12:10
Cameron
It's still just attention heads and a feed for or for a neural network or for mixture, for a lot of the
mixture of experts models, you know, you'll have a router and then you'll have multiple different,
feeds, like different wow words. Multiple different models behind that router. But at the end of
the day, it's just it's still just a model.