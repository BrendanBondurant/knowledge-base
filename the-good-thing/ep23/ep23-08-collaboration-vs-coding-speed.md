# ep23-08-collaboration-vs-coding-speed

**Time Range:** 00:45:01 - 00:50:04

**Topic:** AI-generated libraries, collaboration bottlenecks, and dev workflows

---

00:45:01:08 - 00:45:17:17
Stefan
I think you're spot on with that. Also, recently we were working with a very big company and,
they submitted a PR. And what did you say today? You're like, what the hell? This is just cursor
garbage or something. And we had to go back and review it. And I think we're starting to see a
lot of that.
00:45:17:17 - 00:45:40:25
Stefan
Like we work with some pretty big companies and they're starting to use cursor. But if you
remember, I think a year and a half ago Klarna that big like pay later company. They said we've
replaced 80% of our customer support and customer success with AI. It's all going to be AI year
later. We messed up. We're sorry, and they've hired back all the customer success people.
00:45:40:25 - 00:45:57:18
Stefan
I think we haven't seen the repercussions yet at a large scale of writing garbage code. I really
don't think so. And I'll give you a thing like for example, yesterday I was messing with cursor and
I'm like building like some small like, if you remember Skyrim, they have this like constellation
where you can like uplevel. And I was just building that for myself.
00:45:57:18 - 00:46:17:28
Stefan
Maybe I can like, track my progress and are there and it's great at that. It's great at building very
simple, fun stuff, but I cannot see it building complex where code bases, where you ever see the
notes where it's like, please don't remove this. I don't know why, but this function makes sure
that our company runs. Please don't remove it.
00:46:18:03 - 00:46:28:19
Stefan
It's like, if we cannot understand it, how do you expect cursor to be like, oh, this function does
this like the guys literally like, if we remove this, the entire website will break. We don't know
why. Please don't remove.
00:46:28:19 - 00:46:32:06
Stefan
This. Like what? Yeah, I don't know. Oh.
00:46:32:06 - 00:46:57:21
Jens
Also in a in a similar direction, one thing I observed in the GraphQL subreddit, and you might
see it in other subreddits as well, I haven't checked, but there was recently there was a guy who
posted in like 24 hours. He posted two new repositories that solved different problems, and you
always see the same pattern. It's like you see from the description.
00:46:57:23 - 00:47:02:14
Jens
It has like emojis and it's like.
00:47:02:16 - 00:47:04:09
Stefan
Yeah, you know, immediately.
00:47:04:09 - 00:47:30:13
Jens
Okay, this is AI generated. And I, we see this new trend and I really hate it honestly, that people
are like, oh, there's a little problem. I created a library with it. I cursor together and then they,
they publish it. So I think we currently see a lot of like low quality things. And then under one of
such repositories there was a comment like, hey, are you are you implementing like the full
GraphQL spec?
00:47:30:13 - 00:47:39:16
Jens
And then the response was kind of like, I don't know. It's working for these cases here. I have
tests and.
00:47:39:18 - 00:47:40:19
Stefan
Yeah, you.
00:47:40:19 - 00:47:48:14
Jens
cursor.
Can you can clearly see that there's there's not just positive effects of of having tools like like
00:47:48:17 - 00:48:06:19
Stefan
Yeah. And I think we'll definitely start to see more and more. It's an interesting environment that
we're in right now. I'm always wondering like I'm seeing it also in film, like people are starting to
add AI into film and like if, if you can add AI to help edit faster. So that way you can make
movies faster, that's great.
00:48:06:21 - 00:48:20:20
Stefan
But if you start adding AI actors and you start killing that essence of film, like film is an art,
programing is an art. Like you should use tools that speed it up. But if you kill the very essence
of that art, like what you have kind of sucks.
00:48:20:22 - 00:48:48:07
Jens
Which which leads a little bit into the direction that we're going with WunderGraph as a, as a
company, because look what we kind of figured out is that cursor and AI coding tools. They are
great. They are great at solving some problems, but we believe like the real problem and we get
a lot of positive feedback from the market where we are showing our new product.
00:48:48:09 - 00:49:11:29
Jens
We get a lot of, of, of feedback that, the, the real problem is collaboration. Like, I think what is
going to happen with AI is that we will see like more and more parts of software or more or
more. Yeah, more and more parts of of software development. We will we will automate them,
we will make them faster and so on, so forth.
00:49:12:01 - 00:49:14:27
Jens
But, the, the real.
00:49:14:29 - 00:49:15:24
Stefan
I.
00:49:15:25 - 00:49:39:18
Jens
Think the like the real bottleneck is, is better collaboration. So for example, if you if you take the
whole journey of creating, creating software, and going from like I have a product owner, they
have new requirements, they go to the designer, they now have a design from this design, you
have to figure out, like, what kind of APIs do I need to to solve that problem.
00:49:39:18 - 00:50:04:15
Jens
Then you have the the API definition. You need to figure out like what services should
implement that. Then, you kind of block the frontend team because there is no service running
yet. So you need to think about how can I provide mocks that can take, a lot of time on the, on
the backend guys. So this whole journey, we kind of figured out that, it's, it's very hard to
actually go through that.