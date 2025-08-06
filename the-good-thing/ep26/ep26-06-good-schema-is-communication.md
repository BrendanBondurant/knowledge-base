# ep26-06-good-schema-is-communication

**Time Range:** 0:21:21 - 0:25:28

**Topic:** A good schema is good communication

---

00:21:18:12 - 00:21:40:24
Sam
I mean, we've got multiple public case studies out there of people moving from Aurora or
wherever, and becoming much, much more reliable, on top of our platform, we specialize in
databases, engineers some of our engineers have worked on. But there's no secret, like, they
have a lot of money. They can put a lot of people on these problems.
00:21:40:24 - 00:22:02:25
Sam
But at the end of the day, right, there's expertise. At companies like ours, that far exceeds what
they have, current, current Amazon specifically. And you look at the current tools, they've,
they've, they've built like limitless. We've moved their largest customer over to, to, to us because
it wasn't reliable. I, you know, literally this morning spoke to another limitless customer.
00:22:02:25 - 00:22:21:27
Sam
That's not a very large scale. That's also having problems on these platforms. So them just I'm
sure they've had they've had access to the vitess code base for years. It hasn't really improved
anything they do. They could just take the technology and host it. It's only half the problem for
them. I don't think their problem is writing the code that could look like vitess to go and do the
stuff.
00:22:21:27 - 00:22:35:13
Sam
It's a load of other tail factors that impact whether or not they can hurt your business. But there's
just plus there's also just much more coarse grained, brutal ways Amazon can can hurt you than
just take the code of what you're doing.
00:22:35:15 - 00:22:38:01
Jens
Yeah. What's your current headcount?
00:22:38:03 - 00:22:39:17
Sam
55.
00:22:39:19 - 00:22:58:13
Jens
55. And how does this distribute across like database operators or let's say like infra people or
what do you call it like like platform engineering versus like engineers working on the on the
vitess product or like proprietary products.
00:22:58:15 - 00:23:08:12
Stefan
And Sam real quick 55 with 100% uptime, reliability. That is insane. I mean, that is an insane
stat. Oh yeah. We're deep into this.
00:23:08:14 - 00:23:30:20
Sam
We're very proud of being a small company. We're doing some hiring. We're not going crazy. But
yeah, like this startup, like two other very popular Postgres startups like host hosts have their
engineering teams are three times the size of ours. And we're very proud of having a very small
company and team. These are exceptional people that we have working for us.
00:23:30:20 - 00:23:48:04
Sam
And we know like it's it's a known thing about our culture that we behave that way. Pretty much
every engineer at Planet Scale could be a principal engineer at any other company. We don't
really have any engineering titles that way, or it's just everyone's just an exceptionally good
engineer that's had a long career at scale. And that's how we achieve this.
00:23:48:07 - 00:24:16:02
Sam
And if you build good infrastructure, you shouldn't need to throw tons of headcount. Or
infrastructure team itself is very small. It's like four people. The vitess team is around ten. The
rest break up between what we would call orchestration, which is a large amount of what we do,
which is kind of orchestrating. Database failurover is happening like there's no there's nothing in
terms of how we handle our operations that require human to be around.
00:24:16:02 - 00:24:23:06
Sam
Otherwise we wouldn't have the high uptime that we have.
00:24:23:09 - 00:24:39:16
Sam
And then we have a small team of people that build the what they call the surfaces team, and
they build the surfaces that you interact with. They bring the build the the app, web app, the CLI,
and all the other tooling that you interact with to go and use the platform there is like five of
them. So it's mainly all in orchestration.
00:24:39:16 - 00:24:53:25
Sam
There's no sysadmin style people, right? Like that. It's all writing automation that manages the
fleet, continually. Otherwise it would it would not scale. Basically.
00:24:53:28 - 00:24:57:12
Jens
Well, what's your what's your headcount in marketing and sales?
00:24:57:15 - 00:24:58:09
Stefan
Yeah, I was going to ask.