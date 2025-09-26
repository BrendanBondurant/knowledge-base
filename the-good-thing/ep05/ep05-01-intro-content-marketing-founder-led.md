---
type: podcast-chunk
title: Intro, Content Marketing, and Founder-Led Content
slug: ep05-01-intro-content-marketing-founder-led
series: The Good Thing
episode: 5
chunk: 1
segment: Introduction, content marketing, and the rise of founder-led content
timecode: 00:00:25:16 - 00:07:12:22
start_time: 00:00:25:16
end_time: 00:07:12:22
speakers:
  - Stefan
  - Jens
topics:
  - Podcast Introduction
  - Content Marketing
  - Founder-Led Content
  - Authenticity in Marketing
  - Brand Building
tags:
  - founder
  - authenticity
  - ai
  - benchmarking
  - cosmo
  - federation
  - go
  - graphql
  - graphql-federation
  - rest
  - rust
  - startup
entities:
  - Stefan
  - Jens
  - Sergei
  - WunderGraph
  - Cosmo
summary: Stefan and Jens introduce the episode, discuss the importance of content
  marketing and the rise of founder-led content, and reflect on how authenticity and
  personal stories help build a brand. They share thoughts on podcasting, developer
  tools, and the value of showing the people behind the product.
---

00:00:25:16 - 00:00:34:28
Stefan
And we're live. Welcome back, everyone, to another episode of The Good Thing, hosted by
myself, Stefan and my co-founder Jens. Jens how are you doing today?

00:00:35:01 - 00:00:42:08
Jens
Like with the words of Sergei. It's okay. For those of you that don't.

00:00:42:08 - 00:00:58:10
Stefan
Know, Sergei is our first, engineer ever. I wunder graph, and he was a founding engineer and he
doesn't speak much. He delivers like crazy, but he just says it's okay if something's not bad. It
it's okay if something's great. It's okay if something's bad, it's okay.

00:00:58:13 - 00:01:03:23
Jens
He has this Eastern European style. It's okay.

00:01:03:26 - 00:01:25:09
Stefan
What do you think about Eastern Europeans? I mean, me being from Serbia, like, I don't know,
we're known for not showing too much emotion, but. Which is weird because I'm American and
we like emotion. But, yeah , you should meet my dad one day Jens you would laugh. We're
completely different guys. Cool. But yeah. Yeah. Thanks for, I guess, joining me.

00:01:25:09 - 00:01:27:16
Stefan
I mean, you have to join me. This is our podcast.

00:01:27:21 - 00:01:33:15
Jens
You forced me to. Hey, Jens we need to do marketing. Come on the podcast with me.

00:01:33:18 - 00:01:51:18
Stefan
Yeah, it's true, but the people, the people like it, which was fun. But, I mean, we got some cool
topics today. So guys, today we're going to be talking about founder mode is it scalable versus a
founding team. Rest versus GraphQL is outdated. We're also going to talk about some drama
that we saw on Twitter, but also that we're facing with copycat competitors and benchmarking.

00:01:51:18 - 00:02:14:06
Stefan
And just calling out developer tooling in a like respectable way, which I think is BS because
developers like to hide behind, you know, calling each other out on technology. It's interesting,
but I think that's going to be a good content today. And then the last one is just the rise in
content. So yesterday, AVC invested into two content creators, $60 million.

00:02:14:08 - 00:02:29:03
Stefan
And one of their statements in the announcement piece was that founder led content and just
content from companies where it's not like about the company and it's just about the founders is
on the rise and we've seen it. So many other founders are posting more content like this, and it's
good that we're a little bit ahead of the curve Jens.

00:02:29:09 - 00:02:32:03
Stefan
But yeah, I'm excited to chat tday.

00:02:32:05 - 00:03:07:06
Jens
Yeah. I mean, wundergraph it's a it's a you could say dev tool like we don't we have a special
relationship with the word dev tool, but we're, we're, we have a product that that attracts
developers and traditional marketing is dead you need to go different ways and you cannot I
don't know, I think building the brand these days, it's it's very important to stay authentic and to
not actively push the product.

00:03:07:06 - 00:03:34:02
Jens
But rather say, you know, like a while ago, I said, the, the vendor like us. So we should be we
should be advocating the category, not the solution, the category. So we speak about federation
and how it's great. And then we let our customers with their stories speak about how they use
Cosmo. So that's kind of I think that's that's the, the modern, trustful marketing.

00:03:34:02 - 00:04:00:19
Jens
So let people decide with their credit card and talk about what they have decided and let us talk
about, how the how the category works and what you can do with it. And then people can,
decide if they if they like that or not. And, yeah, I think a podcast, podcast, like what we're doing,
I think that's, that's, a good way.

00:04:00:21 - 00:04:32:16
Stefan
I would agree. And the other day I, I watched this video, which was about creating content. And
the thing about creating content is that anybody can create content. It doesn't matter what age
you are. And I think everybody should create content because everyone has unique life
experiences and everybody is experience something that maybe other people havent. And this
analogy that I saw was really helpful, which is that imagine you're in a line of people when you
create content, you're sharing your experiences for all the people behind you that are not where
we're there are not where you are.

00:04:32:20 - 00:04:47:04
Stefan
And so you're helping them get to where you are because they would love to be where you are.
And then you obviously want to get ahead of the line, and there's 50 people ahead of you and
they're creating content. And so you want to get to that point. And so if we all created content
and just passed it back, it's just a unique learning experience.

00:04:47:04 - 00:05:04:18
Stefan
And I think this founder led content that we're doing is super helpful because I'll be honest,
Jens, three years ago, I don't think you would have done a podcast. You you were not very, you
know, you were more like traditional developer. You were great with customers, but I don't think
you would have done a podcast three years ago.

00:05:04:20 - 00:05:29:09
Jens
At least not on my own. I think even today I wouldn't do it on my own because I think there's just
like different types of characters. I, I'm, I'm the type of character. If you start the conversation, I
will happily join the conversation. If there's no conversation and I'm there, there's still no
conversation. Just I don't know, some some characters are not starting conversation.

00:05:29:12 - 00:05:51:07
Jens
But if I go to a party and you don't start the conversation with me, I will drink one beer after
another until I'm drunk and I don't talk to anybody. Just, I don't know, I don't do it. But if you
come to me and say, hey Jens let's talk about Federation, then we can talk all night. But yeah,
it's like people are people are different.

00:05:51:09 - 00:06:06:24
Stefan
Yeah. And I'm the opposite way. Like, you could put me anywhere. And at the end of the night,
there will be people surrounding me. And I'm keeping that conversation alive. My, my wife is
always joking about that. She's like, wherever I bring you, I bring you to like, an influencer event
with nobody in technology. And like, you're just talking to them about stuff.

00:06:06:24 - 00:06:25:03
Stefan
And I was like, well, you can always relate to people about random stuff. Like, for example. Jens
always laughs whenever we meet a company in Europe or, I don't know, just somewhere based
out of like maybe London. I'm like, oh, do you guys support football? 99% of them say no
because they're developers. But eventually we do get 1 or 2 and then we talk about football and
it's honestly, it's a good bonding moment.

00:06:25:03 - 00:06:46:20
Stefan
That's why I like, like being able to do this podcast and create content. And then honestly, it's
fun too, because we brought Dustin on the podcast two episodes ago. And, you could you could
see him getting out of his shell. Like, Dustin is typically like an architect, CTO, but when you get
him to talk about stuff like this, you can see how much more fun it is to get to know the people
behind the product.

00:06:46:20 - 00:07:06:14
Stefan
And our customers have said the same thing. They're like, I really enjoy your episodes of the
podcast. Which one makes us keep doing it, Because customers are saying that they like it, but
also to it's cool to see the people like again behind the product. And I think that's what's really
important about content from founders is that behind wundergraph Cosmo, there's actually
people with personal lives.

00:07:06:14 - 00:07:12:22
Stefan
There's people that are doing this with a passion, and you don't traditionally see that from big
companies, right?