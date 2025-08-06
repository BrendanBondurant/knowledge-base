# ep22-09-learn-to-code-llms-and-dev-evolution

**Time Range:** 00:46:23 - 00:54:20

**Topic:** Learn to code debate, LLMs, and developer role evolution

---

00:46:23:07 - 00:46:54:08
Jens
You just write a regular schema, you don't do any special thing, and we just compile it into a
protobuf spec where for each field, like an entity field where you need an entity resolver or a
root field where you need like, root query resolver or mutation for each such field we generate in
the proto definition, we generate a schema where like an arbitrary entry.
00:46:54:10 - 00:47:26:05
Jens
And then you, you can implement this, compile it as a plugin and run it as a side sidecar like a
co-process to the router. And that's it. So we were thinking about it okay. That's that like cool
approach. Seems simple enough. And then we started playing and we were quite lucky with the,
with the timing because, like, I don't know, like half a year ago we didn't have tools like, cursor
with the capabilities they have today.
00:47:26:05 - 00:47:53:22
Jens
But today, if you have cursor and you give it the right, the right, the right rules and, the right,
system prompts, you can tell cursor that here is a protobuf file. Here's the the current
implementation in go, and I have an existing REST API. Here's the open API. Spec. Can you
generate me an adapter?
00:47:53:24 - 00:48:34:03
Jens
And that is all it takes. And, after a couple of minutes, maybe 1 or 2 other prompts, Curser can
write you an adapter that fills the gap between federation contract and rest API. This schema is
just a regular subgraph schema. There's nothing special, no special directive, just federation.
And you don't even have to understand gRPC or anything because we generate the protobuf
file and then we implement it with with, cursor.
00:48:34:06 - 00:49:06:01
Jens
And that kind of lets us to the, to the question, like from from a developer experience, you have
a demand driven schema. We have a complete abstraction because the schema, it has no
influence from the rest API. It's just what the client side wants. And in the implementation we
can write any code we want. So that means we can we can map this to a rest API today, but
tomorrow we can map it to a database.
00:49:06:01 - 00:49:24:16
Jens
So swift whatever we want which everything is possible. And so yeah this this is the like the
principle of number ten. And I think, I don't know, maybe we're following the principles more than
anybody else.
00:49:24:18 - 00:49:40:24
Stefan
No well said. And then we get that actually a lot that we do follow the specification of GraphQL a
little bit more stricter and that we do follow the principles. But I like the approach. We do have
ten minutes left and I do want to bring up one more topic which let me share my screen. And I
think this one is interesting, especially for you.
00:49:40:24 - 00:49:55:27
Stefan
Jens. So for those of you that don't know, Jens is a self-taught developer. I studied computer
science and economics. Yen studied business psychology. Psychology, statistics. What else did
you study? That's the joke.
00:49:55:27 - 00:49:59:04
Jens
But I don't go to the.
00:49:59:06 - 00:50:13:21
Stefan
We have a internal joke with Jens. Every time he wants to prove a point, he's like, well, I studied
statistics. And here's the answer I studied psychology. Here's why this is the answer. So Jens
actually has, how many degrees you have? 15, 16 or something.
00:50:13:24 - 00:50:16:13
Jens
All of them. Exactly.
00:50:16:15 - 00:50:38:07
Stefan
But this article, I read it. I thought it was ridiculous. So learn to code backfire spectacularly as
comp sci majors suddenly have a sky high unemployment rate. Also, I think this quote is
ridiculous. Every kid with the laptop thinks they're the next Zuckerberg. I don't know who wrote
this, but it looks like learn to code push is backfire spectacular for those who bought in.
00:50:38:13 - 00:51:18:22
Stefan
So there's a recent increase and went up from the recent grads over about 5.8%. It went up by
11, by 7.5%. Unemployment rate in the computer engineering field are 9.4 and 7. 8%. This
article kind of annoyed me. Apparently our field is dying. It's kind of ridiculous, which I can't
understand a little bit why somebody would write that, but the whole point of the article is just
basically saying how with AI and everything, that everything is kind of sky high and learning to
code is now back firing.
00:51:18:25 - 00:51:35:23
Stefan
I wanted to get your your feedback on this, especially being a self-taught developer. Do you
think learning to code is the wrong thing to do for the new generation? People that are studying
now? Should they get into technology? Will AI wipe away their opportunities? What is your take
on it?
00:51:35:25 - 00:52:04:28
Jens
Yeah. I also read the article. I didn't like much of it. I also think every kid with the laptop thinks
they are the next Zuckerberg. I think these days are long, long gone. Like, it's it's not like this,
this kind of gold rush mentality anymore. And then the, the whole point is is AI destroying the
jobs.
00:52:05:01 - 00:52:35:22
Jens
And is it taking away the, the jobs? If I look at our own company, we're all leveraging AI. And we
also had people come in and find their way out again with and without AI. And I would say what
AI has changed is and by the way, I don't even like the term AI. Let's just be more specific.
00:52:35:22 - 00:53:15:25
Jens
Let's say LLMS, LLMS generating tokens. I think they are getting much, much, much better
every day in generating code. But what what I think it's it's proven multiple times now, also, for
example, underscored by a recent article, a research paper, from Apple. Stating that reasoning
models don't really have reasoning. If you, if you give them a problem that they haven't
memorized in their learning data, they will not be able to reason about it.
00:53:15:25 - 00:53:47:13
Jens
They they will simply fail with the problem which it it. I think this this is the most important point
you need to take away, when you, when you listen to this podcast or, or think about this thing
here, this article, I think the biggest takeaway is, if you're a very good developer with LLMS, you
you can focus more on on strategic parts.
00:53:47:16 - 00:54:20:11
Jens
You focus, you can focus more on, on high level coding and less low level coding. But if you if
you are not good at doing good architecture, good high level thinking, good problem thinking,
then also AI is not able to help you and AI is not replacing jobs or something. AI is probably or
LLMS they are probably replacing or killing like extremely boring jobs.