# ep13-08-mcp-vulnerabilities-and-vibe-coding

**Time Range:** 00:29:20 - 00:32:18

**Topic:** MCP misuse risks, vibe coding vulnerabilities, real-world hacking story

---

00:29:21:05 - 00:29:52:16
Jens
Is that is that what you want to do? So, yeah. And combine this with Vibe coding. And it's now so
easy to vibe code on MCP server. I think it's a super dangerous time because now everybody
can. Yeah. With with a couple of prompts, they can write, an MCP server. I don't know. On the
one side, I'm super excited about the possibilities of MCP.
00:29:52:18 - 00:30:24:18
Jens
On the other side, there are there are many possibilities. How how MCP can be exploited. If you
want to be on the safe side. Yeah. Build MCP servers with standard IO, because then, yeah, if
you can do stupid things on your, on your terminal, then MCP can also do these stupid things on
your terminal like it's, it's not worse than if you type some, some stuff into your terminal.
00:30:24:18 - 00:30:28:04
Jens
So yeah, long story short.
00:30:28:06 - 00:30:46:14
Stefan
I know, but have you seen, it's actually kind of funny. This guy, he vibe coded like a startup over
the weekend. Something like simple. But he was using MCP or whatever, and he vibe coded it,
so he didn't have very technical knowledge, and he released it on Twitter, and he's like, yellow,
like building in public. This is what I've built.
00:30:46:14 - 00:31:05:08
Stefan
Building people are like, wow, that's awesome. And he's like, I completely vibe coded it. So it
was really, really tough. And this pretty experienced developer, he went in very quickly and he
identified that vulnerability like that. He can get access to the application. And so he just started
messing with him like he would, take away the stripe payments because the guy was making
money from this app.
00:31:05:08 - 00:31:19:02
Stefan
So he removed stripe, and then he would mess up with the app or whatever. And he, like, the
guy goes back on to Twitter. He's like, help! I'm being like, hacked. I don't know how he's
hacking me. Like, whatever. I just vibe coded it. And the hacker himself, you wrote him. You
have a week before I come back.
00:31:19:07 - 00:31:35:14
Stefan
I'm hope I'm teaching you a lesson that you cannot just vibe code. Things need to understand
how they work. And people were like, I kind of respect him. Like, he's teaching you a very
valuable lesson. Like, he could destroy you right now, but instead he's like removing buttons or
doing some simple stuff because he got access to your application.
00:31:35:14 - 00:31:55:02
Stefan
But he's like, you're handling people's money. You're handling people's information. You should
at least know the basics of how to safeguard these things. And it came from this exact thing for
me right here with the MCP is that there was a portal open. He gained access. Eventually he
released a report of how he did it. It was anonymous because he didn't want to get in trouble,
but the guy ended up deleting his app.
00:31:55:02 - 00:32:14:03
Stefan
And I think you're spot on with that is that we're going to see a lot and a lot more unsecure apps.
Maybe it'll get better from just like vibe coding in that it in, you know, it puts in the correct
security protocols into place. But you're absolutely right. With vibe coding, you're opening up a
whole bucket, I guess, of attacks.
00:32:14:03 - 00:32:18:10
Stefan
If you don't really know what you're doing.