# ep26-12-educating-teams-on-schemas

**Time Range:** 0:48:30 - 0:52:56

**Topic:** Educating teams on schema best practices

---
00:48:17:25 - 00:48:34:27
Jens
And like a while ago there was like in the situation between Cncf and, the guys behind NATs and
a, what's the company called? Something with s.
00:48:34:29 - 00:48:43:18
Sam
Oh, I vaguely recall this. Yeah, I know I didn't pay much attention. Yeah, there was some drama,
I think. No, I can't remember.
00:48:43:18 - 00:49:08:06
Jens
Yeah. So they, they, they, they somehow they wanted to pull out the, the, the project out of the
Cncf and get more control over it. I don't even want to talk about that, but what I'm interested in
this. What's your relationship with, with the Cncf and, Well, is it good that vitess is a Cncf project
or is it neutral or.
00:49:08:07 - 00:49:10:15
Jens
I don't know, is it anything.
00:49:10:17 - 00:49:30:03
Sam
I think it's a good thing. I believe in open source. I believe if you're going to be open source, you
should be you should be really open source. You know, like there's types of licensing that I don't
like. When they pretend they're open source, when they're not or whatever. But there's also
licensing that I think is great and defends companies against companies like Amazon.
00:49:30:03 - 00:49:49:23
Sam
And yeah, like there would be a downside if Amazon just stole our tech and went and started
using it. Right. And that was not a good thing. But that's kind of what you throw into when you
do open source. And I think it's good to have these foundations in these bodies that protect
open source and allow some purity to these projects.
00:49:49:25 - 00:50:06:23
Sam
There is downsides generally from the model, but they're not specific to Cncf at all. And they're
a great crew. Chris and the team over there are just fantastic. And they do something that's very
difficult to do and wrangle a lot of the complexities that come with open source. And so, yeah, I
don't see it really as a downside.
00:50:06:23 - 00:50:12:23
Sam
I think it's the goods that keeps us honest. As an open source company.
00:50:12:26 - 00:50:28:09
Stefan
And what are some open source licenses that you don't like? So like for us, just for context,
we're licensed under Apache 2.0. Some of our competitors do BSL. I think BSL was created
because of Mongo right Amazon went and took it. Yeah okay. So what are some licenses that
you like or and don't like.
00:50:28:12 - 00:50:48:13
Sam
There's lot like I guess I should have I but I don't dislike the license I dislike the pretense. Right.
So yeah BSL for example. Right. It's not an open source license. It is officially not recognized as
an open source license. But there's companies that will do BSL and refer to themselves as open
source. And I don't like that.
00:50:48:15 - 00:51:13:17
Sam
Like your code is open. That's fine. But you can't I mean, you've blocked any contributors to that
going and starting a rival company to you that's not open source. That is not how that works.
And so I don't like the kind of layering on top of, you know, I think if there's a lot of people that
have one way relationships with open source and it's very take, take, take, and I don't like that.
00:51:13:19 - 00:51:36:29
Sam
If you're going to use the glow and the incredible branding of what is the most in one of the most
amazing human achievements, which is the open source, like you think the open source
community is just a phenomenal human achievement to be able to, like, bask in the glory of that
and use open source in terms of your branding and furthering your company.
00:51:37:01 - 00:52:01:08
Sam
But holding back the actual license from being an open source license, I think is very wrong. So
yeah, I don't really have a Beef for the specific, like there's some licenses that are just more.
The GPL is annoyingly like niche and well, has like niche ramifications that GitHub would always
just suggest people use their MIT license because it's the most simple and most open.
00:52:01:10 - 00:52:10:23
Sam
But yeah, it's no no specific license problems. It's more like the approaches people take by
taking these non open source licenses and claiming to be open source. I think it's very cheeky.
00:52:10:25 - 00:52:19:28
Jens
Do you have like like a fork of like an internal fork of of vitess or is it just you use the open
source. We test. That's what you deploy.
00:52:20:01 - 00:52:40:22
Sam
We do have an internal fork and it's really for simplicity. Right. Like rather than there's no we're
not trying to do like a kind of premium thing where you, there's like a ton of features hidden.
There's some stuff that's platform specific to us, which we don't even want to bend the, vitess
project out of shape too much to be specific to planet scale.