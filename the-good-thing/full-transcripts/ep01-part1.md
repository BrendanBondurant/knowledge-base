Episode 1
type: podcast-chunk
00:00:01:18 - 00:00:19:19
Stefan
Ladies and gentlemen, welcome to an episode of The Good Thing, episode one, where we're
gonna be interviewing Jens Neuse. For those of you that don't know, Jens is my co-founder
CEO. And what I like to say on the call is the technical co-founder of, wunder graph. And most of
you don't know Jens.
00:00:19:20 - 00:00:40:04
Stefan
Maybe you know him from Twitter or from LinkedIn. And it's kind of interesting because he has
actually an amazing background. And I don't think a lot of people know about it or know how he
got into technology, into APIs, and why he's such a big advocate for GraphQL. So, Jens, thank
you so much for joining me. And also, Jens will be my co-host going forward onto these podcast
that we're going to be having guests.
00:00:40:07 - 00:00:48:18
Stefan
We're going to be talking a lot. Just so kind of about the good things in software development,
GraphQL API and what's going on at wonder graph. But Jens, thank you so much for joining me.
00:00:48:21 - 00:00:54:03
Jens
Okay. Can you do the the intro we do in the sales call. Like when when you intro me.
00:00:54:05 - 00:01:06:15
Stefan
Yeah I can hi guys. My name is Stefan. I'm the co-founder chief customer officer here I'm joined
by Jens he is our CEO and technical founder. Any technical questions you have Jens will be
able to address.
00:01:06:17 - 00:01:14:04
Jens
Yeah. I'm it's it's always funny that I'm. I'm just here to answer your technical questions
essentially.
00:01:14:07 - 00:01:27:02
Stefan
Yeah. Basically. And that's what you'll be doing on this podcast as well. So I'll just be talking to
you. And when there's a technical question about Federation or composition, I'll just default it to
you just the same way we do in the sales calls.
00:01:27:04 - 00:01:44:06
Stefan
Amazing. But yeah guys, so happy New Year and what we'll be doing on this podcast. And the
reason why it's called the good thing is, is we have another co-founder. His name is Bjorn. He's
a very positive guy already, and we just talk a little bit about the story, which is that.
00:01:44:11 - 00:01:44:20
Jens
Okay.
00:01:44:20 - 00:02:03:13
Stefan
Every time something bad happened, he would somehow say, the good thing is and he would
find the good thing. And what I realized with my background of working at wundergraph and
working with such talented engineers is that software engineering is all about trade offs. And the
reason we decided with the good thing is, is because with every trade off, there is a good thing.
00:02:03:20 - 00:02:19:09
Stefan
And so that's why we named the podcast The Good Thing, because we want to talk about what
are the trade offs that we have to make in engineering. What are the trade offs you have to
make when you choose GraphQL? What are the trade offs you have to make just in life? And
today we're going to be talking about Jens and just kind of like your background.
00:02:19:11 - 00:02:32:04
Stefan
Some of the things that people don't know is that you're an avid dancer. They don't know that
you enjoy really good techno music. They don't know about your story. They don't also know
that you're almost a professional mono skier. Would you say you're a professional or not at that
level?
00:02:32:04 - 00:03:21:15
Jens
Yeah, it depends on who you ask. But yeah, mono skiing is is one I would say one. One big part
of, of my private life, which also has kind of like, a little bit of a back story because I should have
been a carpenter, and at age 18, I was, on, kind of like a motorbike, scooter, whatever thing,
with, 125 CCM and I was on the on the way to the carpentry, and I, happened to be in the
corner that was cut by a truck, and.
00:03:21:17 - 00:03:51:00
Jens
Yeah, I got run over by a truck. And then over the next two years, I had to relearn how to walk
because I had, like, like, very complicated, or many, many very complicated surgeries with my
left knee. And, at age 18, I was very, very unsure and very insecure about my future if I would
ever walk again and everything.
00:03:51:03 - 00:04:20:21
Jens
And, yeah, I had to, to relearn that. And then after a while, I realized that, I, I wouldn't be a
carpenter anymore because as a carpenter, you have to carry, like, heavy doors and stuff like
that, more than 20 kilos. And I just couldn't carry that with, with my injured knee. These days, I
can walk again, but not so much like running or skiing or anything.
00:04:20:21 - 00:04:48:22
Jens
And then a couple of years ago, my my wife figured out that there is, something that, people in
wheelchairs do a lot, in winters sports, they have mono skis, which is you could also say sit ski.
It's kind of like you have a, like a seat where you strap yourself in and under the seat there's a
single ski, which is why we call this thing.
00:04:48:22 - 00:05:14:07
Jens
A mono ski. And then, you can imagine how hard it is to balance, like a seat on top of, like a little
chair on top of, a single ski and try to balance that down, down the hill. It's a very complicated
thing. But after a couple of years of falling over and over and over, I.
00:05:14:07 - 00:05:38:10
Jens
I kind of, stuck with it, and it's it's, it's a lot of fun. And it if you are someone with a disability and
you, you, you you can get back to these kind of things. It gives you a different level of freedom
just because it's an activity that you you cannot really do. You know, we're we're knowledge
workers.
00:05:38:13 - 00:06:07:03
Jens
And in IT, you can do so many things, even though you have disabilities, like, even if you have,
problems with hearing or visibility or you might not have your full control over your arms or
whatever, there's always some sort of solution and you can somehow use a computer and, you
can use your head and you can write programs, but you cannot participate in the, in the rest of
the life.
00:06:07:05 - 00:06:42:11
Jens
And, yeah, for me sit ski or mono ski is just it's kind of like freedom. I can I can do something
that I'm typically not doing. And, it's, it's, very enjoyable thing. And one just one thing I want to
point out is that I, I have a feeling that my, my, my, accident at, at age 18 and, the years after, it
kind of helped me to, to learn how to fail and stand up again.
00:06:42:11 - 00:07:08:16
Jens
And, just a while ago, we had a discussion with, with, venture capitalists, and they had a dinner
with us and they wanted to know about us. And one thing I mentioned is, if you almost lose your
leg and you have to re learn to walk and all that kind of stuff, and then you have a bad day in
your startup, it's not a never going to be as bad as almost losing your leg.
00:07:08:16 - 00:07:36:16
Jens
So it's kind of okay if you lose a deal or something, or if something goes wrong because you,
you kind of have learned that there are things that are much worse, and then somehow you
figured out how to how to walk again, and somehow you figured out your life with, with a broken
leg and whatever. So we will also figure out how to how to move on with with WunderGraph if
we lose a deal or something.
00:07:36:16 - 00:07:42:16
Jens
So I think this really helped me to, to build some, some good resilience.
00:07:42:18 - 00:07:59:25
Stefan
Yeah. And I would totally agree. We'll dive a little bit later because I think that's a commonality
between founders. I also have an injury story. Not as bad as Jens, but it completely changed the
trajectory of my life. But what's really interesting is, yeah, and let's go back in time a little bit. So
you how old were you?
00:07:59:25 - 00:08:18:10
Stefan
You were about 18 when that accident happened and you were about to be a carpenter. Yep. So
18. You know, the world is your oyster. You just you know, you're out there in this horrible
accident, happens to you. And I remember you told me this when we first started out is, you had
no programing experience. Nothing. So you were bedridden.
00:08:18:10 - 00:08:35:13
Stefan
You had to wait for your surgery, and you told me that you started watching some YouTube
videos on programing, and you were like, that seems pretty cool. And then you just started
building. Can you talk to us a little bit about how you started your engineering or programing,
experience in based off of your accident? What happened?
00:08:35:16 - 00:09:00:06
Jens
Yeah. So after the accident theres like. And so I'm, I'm born and living in Germany, so there's,
there's a, like, like a program in Germany. We call this,, I don't know what's the right terminology
in, in English, but essentially that's like an official program that helps you get from one job that
you cannot do anymore into another job.
00:09:00:08 - 00:09:05:12
Jens
So it's kind of like doing, doing, like,
00:09:05:15 - 00:09:07:13
Stefan
The career rehabilitation.
00:09:07:16 - 00:09:32:21
Jens
Right? Yeah. Yeah, you could say, you could say that. And I did that for two years. And then I,
retrained. And then I was like a systems administrator. So now I could administrate Windows
Server 2003 or something like. Not bad. I know I don't want to offend anybody, but it wasn't the
the the dream job.
00:09:32:24 - 00:10:02:17
Jens
And, after that, I worked for, government agency and, kind of one thing that that, happened after
my accident, like, before the accident, I had, like, extremely bad grades. I, I was fighting with my
with my dad all the time, and I just wanted to to leave our, our house and, our relationship
wasn't so good like, these days.
00:10:02:17 - 00:10:29:14
Jens
It's great. But I had to figure out some some stuff for myself, and. Yeah, essentially, after the
accident, I kind of woke up. I was like, okay, life is real. I have to I have to start something like, I
cannot stay a Systems administrator. That's that's not my thing. And so I went to night school.
And in night school, this was like, five evenings per week.
00:10:29:14 - 00:10:55:24
Jens
And, Saturdays, couple hours. And so every, like, for two years, every evening I went to night
school from, I think 5 p.m. until eight or whatever, and then even on the weekends. So it was, it
was really hard, but I, I wanted to do it. And what was interesting in school, like in, in like regular
school, I completely fucked it up.
00:10:55:24 - 00:11:17:05
Jens
Like, I like my grades were, were so bad and in night school all I did was I, I, I went there and I
actually listened and I participated. And then I, my, I had like, one point, one grade, like 1.0 is
the best. 1.1 is, is kind of like second best.
00:11:17:07 - 00:11:19:13
Stefan
I was going to say that's just horrible in the United States.
00:11:19:13 - 00:11:40:01
Jens
By the way. Yeah. No, but by German standards. So that's the second best grade you can have.
And I had that by actually going there and listening and paying attention. And then that like, you
know, there were like like, courses like, like for the physics and other things and maths and I just
enjoyed it and it was great.
00:11:40:01 - 00:11:59:09
Jens
And everybody was a bit more, you know, there's typically like just adult adults and so people
didn't bully you or something. You could just yeah, do school. And it worked great for me. So I
then, had my, my degree there, there after two years. And then I.
00:11:59:09 - 00:12:02:24
Stefan
Tell us about the degree, because it wasn't a technical degree. Right.
00:12:02:26 - 00:12:15:01
Jens
No. That was just like the, the, the school degree we call this. I don't know, it's not like, what's it
called in, in in the, us, I think.
00:12:15:06 - 00:12:21:27
Stefan
door right.
I think in the US, it's an associate. So just like general studies, just to kind of get your foot in the
00:12:22:00 - 00:12:26:17
Jens
Yeah. But how do you do you call it high school or something.
00:12:26:19 - 00:12:30:22
Stefan
Well high school is before college and so you like, you can I.
00:12:30:22 - 00:12:33:23
Jens
Think it's kind of like a college degree or something.
00:12:33:25 - 00:12:38:26
Stefan
Yeah. So I think you did like, what we would call community college or like, an associate's
degree to start with some.
00:12:38:28 - 00:13:06:28
Jens
Yeah, maybe. Maybe something. And then after that, I went to, to, like, private university where I
could, study, bachelor's degree. And I again, I did this beside the, the, the job because I wanted
to have an income. So again, it was in the, in the evenings and on the weekends for two years.
And then I had, bachelor's degree of, business psychology.
00:13:07:01 - 00:13:23:14
Stefan
Yeah, that's what I'm saying. Like, your life is so interesting because you had this traumatic
accident and we didn't talk a little bit about your past, but Jens was an active raver, so he loved
going to the discotheque, especially in his teens. He would stay there till six in the morning. We
would always joke like, you had to be doing drugs.
00:13:23:14 - 00:13:39:23
Stefan
No, he just liked the music and he was there till 6:00 pounding beers. But after the accident you
woke up, you start working as a systems administrator, and then you go to college and you don't
even get a degree in technology. But you got a business psychology degree, correct?
00:13:39:25 - 00:14:07:19
Jens
Well, I, I never really thought about working in IT or anything. I, I didn't like it. I mean, being a
systems administrator, it's it's very boring. And I keep remembering there was like, well, one of
my bosses, he was a very smart guy, and, he, he kind of told me Jens, if you ever want to, to
get somewhere, with your career, you need to learn to program.
00:14:07:19 - 00:14:29:10
Jens
You can't just administrate servers. You need to write programs to administrate servers. That's
much more interesting. You need to automate the things. He he was writing Perl scripts, and,
you know, like, a very smart guy writing Perl, whatever. Like, nobody will do this today. But he
was very smart. And, I looked at some Perl. It just didn't make sense to me.
00:14:29:10 - 00:14:40:08
Jens
I couldn't figure out how to how to program. And I, I just gave up and accepted that, I will
probably never be a programmer.
00:14:40:10 - 00:15:02:20
Stefan
And that's so weird. And I think there's a really important lesson here is that, so for those of you
that don't know my background, I studied computer science and economics, and we have a joke
at wundergraph that I was probably the worst engineer you've ever met. I had a technical
background, but all of the engineers at wundergraph most of them, I would say, or even self-
taught or they just have some formal training.
00:15:02:23 - 00:15:19:11
Stefan
But for me, I fundamentally believe this is that the best engineers are self-taught and at that
point in your life Jens you were trying to go with Perl, you were kind of struggling with a little bit
of it. What changed? Because you do have a programing background and you're one of the
best engineers that I know, but what changed at that moment?
00:15:19:11 - 00:15:26:11
Stefan
You tried it out, you couldn't do it. But then what did you do to actually learn programing?
00:15:26:14 - 00:15:44:05
Jens
So I was, I was, I was working full time. I studied business psychology and, I was dating all the
time. Of course you're.
00:15:44:07 - 00:15:44:23
Stefan
Okay.
00:15:44:23 - 00:16:18:09
Jens
You're you're dating, and, I am. I met a, very interesting girl, that, was studying, in, So I was
living in Frankfurt, and she was studying in Giessen, which is, I don't know, 20, 30, 40km away,
which is by German standards, not so far. And I met her in Frankfurt, and, she's now my my
wife, Alexandra, and we,
00:16:18:12 - 00:16:46:15
Jens
Yeah, we we we started a relationship together. And after a while, together with one other,
colleague, which I studied with, business psychology, we we started a startup because we we
always thought it's exciting to build our own company, and that that company, was, Yeah, it was
a weird company, but, it was a cool experience.
00:16:46:15 - 00:17:11:25
Jens
So we we built an app, and this app, we called it Shakealert because, you could go to local
shops and if you want to have, like, super nice deal from that shop, you had to open the app
and activate the QR code scanner, to redeem the deal. And we thought, okay, let's build
something super fancy and cool.
00:17:11:27 - 00:17:41:27
Jens
So there's no button to activate the QR code scanner, but you have to shake the phone and we
use like the shake sensor. So that's why the app was called Shakealert. And, yeah. Like,
somebody had to and we can talk a little bit more how this, startup failed, but, the, the
interesting bit is so we, we we wanted to build this app, and somebody had to program the app.
00:17:41:29 - 00:18:11:09
Jens
Yeah. So for that, we needed like an iOS app and an Android app, and we needed some sort of
a backend. And I had, like an, an old friend who knew some PHP, and he was kind of like a little
bit out of the game, but it was the best bet to just work with him. And he wrote some PHP, and
then we had some some backend, but I wasn't really happy with with how that worked.
00:18:11:09 - 00:18:38:14
Jens
And it wasn't like the the pace I wanted to go. So I kind of figured, okay, I, I think I need to do it
on my own. And then I had my, my, colleague who I studied with, and we tried to, to split it up,
like where he would build like the iOS app, and I would build, the Android app, and I would build
the backend, and somehow he couldn't get his head around programing.
00:18:38:14 - 00:19:02:07
Jens
And I kind of realized, okay, if we ever want to make this startup work out, somebody needs to
write the code. Then this somebody, it's going to be me. And, so I found, and I can, I can, I can
talk about some, some weird anecdotes here, but, that so I needed to learn to program. So
there was a YouTube channel.
00:19:02:10 - 00:19:37:26
Jens
You can you can actually look it up. I think it's still there. There's a YouTube channel, and, it's
called Slide nerd. This is a guy from India who was teaching how to program, Android apps with,
with, Java and, yeah, it was kind of cool because if you can program an Android app with Java,
you can also write, a backend in Java and so now you have one language for the backend and
the frontend and yeah.
00:19:37:26 - 00:20:07:14
Jens
After, a little while of doing that, I kind of got my, my head around, how programing works. And
then later on I also learned Swift and then I could also program, I could program iOS apps.
Yeah. And then after some other while I figured that, like, Java is cool, but it's not by my it's a bit
verbose and it's a bit hard to to do it.
00:20:07:14 - 00:20:39:29
Jens
And you the, the frameworks like spring and others, it's a bit heavyweight. So I, I also I, I found
go and then I learned the go programing language which was much more lightweight and I, I
kind of enjoyed that. And you know, one, one funny anecdote I still remember is so in the early
days of, of Shakealert, so my wife was studying and after my accident I had like a lot of free
time and I couldn't do so many things.
00:20:39:29 - 00:21:07:11
Jens
So I, I, I, was living a while in the, in the house of the parents of my now wife, and I still
remember my wife was was away. Think she was working or something? My wife's mother was
at the house, and I kind of set my space up in the living room, and there was, like, a big wooden
table.
00:21:07:11 - 00:21:34:21
Jens
And that was kind of like my working place. And I had a laptop, and I pretended to be
programing, but actually I was playing like, strategy game. It's called, NO1600. I don't know if
you if, you know, I know it's it's, very famous in Germany because I, you know, I had like, fear of
not understanding programing.
00:21:34:28 - 00:22:00:20
Jens
So for like a month or something, I really had a lot of fear that I would not make it. And so
instead of trying to learn how to program, I, I kept falling back into gaming because that
somehow, I don't know, it's helped me get through the day. And oh, but whenever my wife's
mother came around, I was like, fuck, let's I need to, I need to move the game to the side.
00:22:00:20 - 00:22:21:04
Jens
And, I need to get back to programing. And yeah, I think it took me like a month or something.
And suddenly it it clicked and, and I think, when, when I got my, my head around programing
and debugging and these kind of things, I. Yeah, I started a very interesting career.
00:22:21:06 - 00:22:41:08
Stefan
And that's the most amazing thing if you've been seeing recently like on social media with like,
Sam Altman and like all these successful entrepreneurs, they've been saying this, saying which
is you can just do things. And when I was in college, we had this professor. He was only there
for a year, but he was amazing. And he said the programing is a lot like soccer.
00:22:41:08 - 00:22:59:04
Stefan
Like, you can read about it, you can go to games and you can watch it. You can go on YouTube.
But the only way you're actually going to get good at it is by kicking the ball around. And I like
your story because you didn't go and read about it. You watched a little bit of SlideNerd, but you
you had a problem and you needed a solution to it, which involved programing.
00:22:59:04 - 00:23:12:17
Stefan
And so you just jumped right into it and you were like, you know what? We need a back end. We
need to build for. And you just kind of just did it. And so you really can just do things. And then
now you kind of built this foundation of programing that came from a problem that you really
wanted to solve.
00:23:12:20 - 00:23:18:24
Stefan
Originals?
I like that. And then the second point I wanted to make is, have you read the book The
00:23:18:26 - 00:23:20:10
Jens
I don't think so.
00:23:20:12 - 00:23:41:26
Stefan
So it's, it's an amazing book and it's about, like, original thinking and what you were actually
doing with, the procrastinating with the video games. It's actually very positive. Usually when
you're learning something and you procrastinate, it can help you retain more information in a
better way because of what you were doing. So you were programing when your mom was,
when your mother in law was walking around, and then you were video gaming.
00:23:41:26 - 00:23:53:25
Stefan
And so that, like, mix between procrastinating and programing, you were helping retain
knowledge. So I wonder if that's how, like, you were able to learn within a month or a half. But
it's definitely an interesting antidote. I really like that. And then.
00:23:53:25 - 00:23:58:08
Jens
LinkedIn would say fascinating information.
00:23:58:10 - 00:24:01:07
Stefan
Or good insight. Good insight. I think they would say.
00:24:01:09 - 00:24:03:06
Jens
Good insight, yes.
00:24:03:08 - 00:24:21:08
Stefan
But to all the, let's say like junior engineers or people just starting out their career, the best way
to get started with programing is you really can just do things, just start building things. And now
with chat, GPT and cursor, you can use it as a I guess partner. You could ask it to help teach
you things, help explain things to you.
00:24:21:13 - 00:24:40:26
Stefan
And I think that's super beneficial. And something that AI is going to help change is how we
learn programing. With that though, I want to transition into something that you kind of taught
me. So yes, you're a self-taught programmer. I've met a lot of self-taught programmers, but
there's something fundamentally different about you. It's that exact word right there.
00:24:40:26 - 00:25:02:09
Stefan
Fundamentally, you stressed that the most important thing about learning is that you went deep
into topics. You went deep into understanding how things worked, like compilers, runtime
computers in general and networks and things like that. Can you talk to us a little bit about like
what that process was like, especially learning on you went deep into topics and you understood
it from the ground up and then it helped build your foundation.
00:25:02:09 - 00:25:07:16
Stefan
Can you can you explain a little bit more what you meant by that? When you explain that to me?
00:25:07:19 - 00:25:41:27
Jens
I think one of the problems we or I often see these days with, with, younger developers is they,
they look into some tutorials or say they look into some, some YouTube stuff. They see react
and they build some react and they deploy it on Vercel. And then they are like, okay, I'm a
developer. And I think what what is fundamentally missing in this path is understanding the
fundamentals.
00:25:41:27 - 00:26:23:19
Jens
Like how does the web work, how do programing languages work and all this kind of stuff. And I,
I don't know if everybody's like that, but for me, it was always important. If I do something, I truly
understand it. Like, I, I, you know, like ChatGPT it, it just gives you the next possible character.
And it's sometimes it's really great in suggesting some code, but I think it's still important even in
the, in the age of, of AI, it's still very important to understand what is going on and, and what is
happening and why is this happening.
00:26:23:19 - 00:26:46:04
Jens
And yeah. Like how does Http work? How do headers work and all these kind of things and, and
what is it TCP connection. What is TLS and why do we need encryption and all these. I think it's
useful to understand the, the, the basics. And I think if you, if you leverage like leveraging AI is
great.
00:26:46:07 - 00:27:09:08
Jens
But it's very important to understand the fundamentals. And at the same time AI is so good at
helping you to understand the fundamentals. You can you can ask possibly any questions like if
you have VS code for example, you can just you can you can mark some code. You can ask
copilot to explain it to you.
00:27:09:11 - 00:27:13:10
Jens
So yeah, yeah. Well said.
00:27:13:12 - 00:27:35:08
Stefan
And I'm reading an interesting book right now. It's like the history of engineering and science.
And one of the key points from the story is that every 17 years, libraries need to double up on
their knowledge. They need to bring double the amount of books that they had within the 17
years. And then with technical knowledge, they say every 15 years, half of it becomes obsolete.
00:27:35:10 - 00:27:56:08
Stefan
And so if you keep that in mind, it's especially important to understand the fundamentals,
because if you understand the fundamentals, technology is ever changing. It's changing every
single year, especially with AI. But the fundamentals rarely change. We're still using Http, we're
still using the internet. We're still using all these type of foundations that we've set from the 90s
up until this point.
00:27:56:10 - 00:28:14:06
Stefan
But from the 90s to now, things have dramatically changed. We have framework works. We
don't have to write, compiler code. Everything is just completely changed. But the fundamentals
stay the same. And I really think that's important. And, for the audience, there was a book that
you recommended to me when you were starting out your journey. For self-taught programmers.
00:28:14:06 - 00:28:18:12
Stefan
What was that book? Do you remember?
00:28:18:14 - 00:28:21:17
Jens
Good question.
00:28:21:20 - 00:28:34:20
Stefan
I think it was like engineering for self-taught or it was a book that, like a self-taught developer
created. And you said it really helped your career. If you don't remember, we can also posted in
the comments later.
00:28:34:22 - 00:28:38:21
Jens
Yeah, I need to think about it.
00:28:38:24 - 00:29:00:21
Stefan
No worries, we'll post it in the comments later for you guys. But this is a book that Jens really
recommended that helped him with his journey, kind of help them with the foundations. And then
it's actually a book he still references to this day. But, okay, cool. So interesting enough, in
Germany you started a startup, which, if you guys know anything about Europe, not very
forward focused, you know, decided to start a startup.
00:29:00:21 - 00:29:13:28
Stefan
But Shakels eventually failed. Walk us through your first, I guess, startup failure and what you
decided to do after that. And I think you're looking up the book, aren't you?
00:29:14:00 - 00:29:15:29
Jens
Yeah. I just found the book.
00:29:16:01 - 00:29:19:08
Stefan
Okay. Backtrack. What was the book called?
00:29:19:10 - 00:29:55:17
Jens
Okay. So here. Wait, I send you an. So this is a link. Big machine. And it's it's so funny because
the the book is the imposters handbook, and I, I really like the, the title because for a very long
time in my career, I felt like an imposter because, you can grow a career in programing very fast
and you feel like, holy shit, I know absolutely nothing.
00:29:55:17 - 00:30:29:05
Jens
And you, you keep. I don't know, like, depending on how long your career is, but, I had this, this
big moment where where I ran into someone who was much, much, much smarter than me. In
one area, and I was like, making, you know, when you're young, you learn something, you're on
this. What's it called? The like this Dunning-Kruger curve where you're on this learning path
where you're like, okay, I, I know a little bit about something that means I'm a master.
00:30:29:07 - 00:30:57:01
Jens
And then you run into like a real master in that area and they absolutely crush you and you kind
of realize, okay, I need to because I was making like very, very bold statements. And that's that's
typically, you know, you you can see someone is not yet a senior if they are making very bold
statements because you kind of learn that if you're too bold, eventually you run into someone,
they absolutely kill you.
00:30:57:01 - 00:31:22:20
Jens
And then you're like, you start, you know, this typical sentence like every, every senior does it
like, hey, what what is this? What is that? And they the, the typical answer is it depends because
you the more senior you are this this answer of saying it depends. It comes from you're so
senior that you know what you don't know or you know how much you don't know.
00:31:22:22 - 00:31:53:07
Jens
So you're you're kind of adjusting. You're you're the strongest of your opinion and, and and and
the likelihood that you don't know everything. And so you kind of calm down a lot. And I think
that's, it's, for me, it was a very important, learning to run into that person. And from that point
on, I, I always kind of try to better understand the topic I'm talking about.
00:31:53:07 - 00:31:58:16
Jens
Or if I don't just calm down a little bit.
00:31:58:19 - 00:32:25:21
Stefan
And I think that's really good advice, especially for junior. And I mean, developers starting out
like bold statements, you know, it's important it's important to kind of like show your mark,
especially in a company you want to get, you know, promoted. But there's so much that you
don't know. And then when you have that realization of that, like, wow, there's so much that I
actually don't know, it changes your thinking fundamentally because now you start looking at
problems like, yes, this is the approach I want to take, but it also depends.
00:32:25:21 - 00:32:44:28
Stefan
And I think it's a really good transition with,. So was your first start up. That's where you learned
programing because it had to be done. What were some of the bold statements that you had,
like what was the general thesis like? You told us, the general thesis of that company you can
shake to get discounts, but why did it ultimately fail?
00:32:44:28 - 00:32:55:17
Stefan
And don't use the experience that you have now with a successful startup? Why back then did
you think that it failed and why do you think it wasn't successful?
