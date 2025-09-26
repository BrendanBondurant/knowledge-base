Episode 3
type: podcast-chunk
00:00:15:27 - 00:00:22:02
Stefan
I was.
00:00:22:05 - 00:00:26:16
Stefan
And. Wait a minute. You're not Jens. Who are you?
00:00:26:19 - 00:00:31:19
Dustin
Hi. Dustin. Go!
00:00:31:22 - 00:00:47:07
Stefan
Everybody, welcome back to another episode of The Good Thing. As you've noticed already,
this is Dustin. This isn't Jens. So, Dustin, who are you? You're kind of. Maybe for the people that
don't know, you maybe get a little quick introduction of yourself. Because I know you very well,
but introduce yourself.
00:00:47:10 - 00:00:58:04
Dustin
Yeah. If you would follow the Covert history of wundergraph, you would already know who I am.
So, But, yeah, my name is Dustin, CTO co-founder of wundergraph. And. Yeah.
00:00:58:06 - 00:00:59:07
Stefan
Yeah. Fantastic.
00:00:59:12 - 00:01:03:06
Dustin
e first time being on the podcast, so.
00:01:03:09 - 00:01:22:05
Stefan
Yeah, it's exciting. So Dustin, thanks for joining us. And as you mentioned, if you follow the
changelog or the commit history on our repo, you'll see Dustin's name pop up a lot. So Dustin is
our CTO and co-founder. He's an absolute beast. We joke around that he's a machine and
yeah, Jens is out this week. So I invited Dustin for his first podcast and all.
00:01:22:05 - 00:01:30:07
Stefan
We're going to do is literally just talk about the technology, talk about Dustin's role here, and just
kind of the things that he's been in charge of. But, yeah. Dustin, thanks for joining me today.
00:01:30:09 - 00:01:32:01
Dustin
Awesome. Thank you.
00:01:32:03 - 00:01:50:10
Stefan
Yeah. So let's kind of just kick it off with a little introduction of yourself. So I know your history,
but I think you have a pretty cool history of companies that you've worked that. So where you
studied, where you started out with, you started off pretty early in the tech journey. And I think
you have like, what is it, ten, 11 years of experience now?
00:01:50:12 - 00:02:15:03
Dustin
Yeah, roughly around that. So, I studied computer science. But very soon I figured out that,
that's not my it's not not my career path. I wanted to to, to do so. I, I spent a lot of time on, on
freelancing, and also educating myself in different technologies. I spent a lot of time in open
source communities.
00:02:15:05 - 00:02:48:21
Dustin
And then I found, my way into, several different companies, for example, high graph, where I
worked at and, high growth as a, like a content management system, which has a focus on
graphql content federation. And I did very, exciting stuff there. We have, implemented, a graphql
proxy written and written in rust that takes care of caching.
00:02:48:23 - 00:03:21:26
Dustin
Which was driven by fastly, the content delivery network deployed on on edge, on the edge. It
was a pretty exciting project, back then. And then I started another career, at RTL, which is, one
of the biggest television companies in Germany and, yeah, the, the, the, they needed, a way to,
to consolidate, to hydrate data sources together.
00:03:21:26 - 00:03:52:18
Dustin
And so the obvious solution was graphql, the didn't invest in graphql federation, back then, but, I
have built with, my, my team, graphql gateway that, aggregated the data, which was more or
less a monolith, graph. And I think, the last I think today they're, they're already, migrating from
the architecture to a federated graph architecture.
00:03:52:21 - 00:03:53:09
Stefan
Which is a very cool.
00:03:53:12 - 00:03:54:29
Dustin
Intense,
00:03:55:01 - 00:04:09:22
Stefan
Yeah. And then so you were working at High Graph and the story of how, Dustin joined us is
actually kind of funny. So you had an open source project which was kind of like, like an OSS
schema registry, right? Like very early on. What was that project?
00:04:09:25 - 00:04:19:00
Dustin
for workers.
I think what you're referring to was, a graphql, cache proxy, for, written in TypeScript for cloud,
00:04:19:02 - 00:04:29:21
Stefan
Yeah, yeah. And, I think you were working on that. And then how did you, like, meet jens? It was
like you guys were working on open source or, like, you start out contributing to a wundergraph.
What was it?
00:04:29:23 - 00:04:57:04
Dustin
Or I think it was on discord. Back then, or. Yeah, I was super. I mean, today you are very busy
as a founder, but back then I was, very active in the community. Also discord. And I don't know
how, but, Jens. Saw what I did in several open source project and wrote me a message, a nice
message like, hey, I'm interested in your stuff.
00:04:57:07 - 00:05:09:24
Dustin
You're doing some stuff with graphql. Yeah. Let's let's talk. Let's. Are you interested in my
startup idea? And, I said, why not?
00:05:09:27 - 00:05:20:01
Stefan
Let's go. That Was three years ago. Yeah, yeah, I remember, and then you joined us. This is
before the original WunderGraph. It wasn't open source. Do you remember? We open sourced it
together?
00:05:20:03 - 00:05:21:21
Dustin
Yeah.
00:05:21:23 - 00:05:42:00
Stefan
Yeah, that was a good time. And then. So you joined us, and then you have this crazy
experience, which is cool, but, talk to me a little bit about, like, how your role has changed. So
you mentioned that as a founder, no more free time, which is true. But like from you going from
an architect, high graph to CTO and co-founder.
00:05:42:05 - 00:05:46:14
Stefan
But first, you weren't CTO, right? You remember when we were small enough, you were a tech
lead, right?
00:05:46:16 - 00:06:17:09
Dustin
Yeah, I think it was yesterday. I, saw a YouTube video from J Combinator where the discuss, the
the relevance of a technical founder. And you cannot outsource, your startup, idea that you
cannot assume that someone has the same passion like you to implement your, your vision or
at least your poc, that that some, some sort of proofs that your idea fits the market.
00:06:17:12 - 00:06:22:21
Dustin
So, yeah. And like. Yeah, yeah.
00:06:22:24 - 00:06:44:15
Stefan
I was gonna say it helps that we have two really technical co-founders. So you and Jens but to
expand a little bit on that because I see it all the time, I see like Y Combinator non-technical
folks, they're saying, oh like now with cursor and with AI you can just build your MVP. But I
totally disagree. I think if you want to build a tech company, you need a technical person, which
is you and Jens.
00:06:44:18 - 00:07:13:07
Dustin
Yeah. One of the person agree. I think it will shift a little bit in terms of you need to hire people.
You don't have to hire on the mass. You're you're hiring on quality. Because I will will be able to
replace or automate certain things that today I think people that there are people who do a lot
of, repetitive stuff.
00:07:13:09 - 00:07:30:24
Dustin
And I think some sort of some of the things can be replaced by AI. But if it comes to like a
someone who has a, needs to be an expert in a specific domain, yeah, I think that that's not
replaceable, at least not in the in the near future.
00:07:30:27 - 00:07:57:15
Stefan
Yeah, yeah, I would agree. I think AI is going to be helpful. It's going to help with the repetitive
tasks. But if you want to build what we're building. So an extremely technical platform for
technical folks and platform teams, I don't think you can build an MVP with cursor. I really don't
think so, because just looking at the engine code of our router, I don't think AI would be able to
make the decisions that you, Sergey and Jens make.
00:07:57:15 - 00:08:00:01
Stefan
What do you think?
00:08:00:03 - 00:08:24:25
Dustin
I, I think it's all about the people. If you I mean, I mean, I think today I could use a cursor to
maybe automate some sort of things that I have built manually. But again, AI needs an operator.
Like, I need to know what to build. I need to know what what should be the end result and what
is good, what is what is bad.
00:08:24:27 - 00:08:30:12
Dustin
And I think AI or claude or whatever can help me to, to speed up the process.
00:08:30:15 - 00:08:50:03
Stefan
And in your current workflow, the CTO so people think like and this is funny, I'll tell you a funny
story, is, at my last job, we had a CTO and he wasn't technical like like he had some technical
experience, but it was like 20 years ago and he was more into a management role. That's not
the case here.
00:08:50:03 - 00:09:06:08
Stefan
Like you're obviously we're small enough, but you're still very hands on coding, implementing,
helping out with the customers, things like that. Do you use any AI in your workflow? Do you use
cursor? What kind of AI tools do you use?
00:09:06:10 - 00:09:36:22
Dustin
I think nothing super special. I use Copilot daily as an integration in my IDE. We have created,
several ChatGPTs for the company to, for example, to, to write technical documentation in a
specific, format to align on the tone or the style. That helps a lot, because not everyone is is
able to write good technical, technical content, which is absolutely fine.
00:09:36:25 - 00:09:55:02
Dustin
It's super hard to write good documentation. Yeah. And I mean, we already using it, I think in
every meeting to, to translate, to a transcript, our customers sessions and, let's say so.
00:09:55:05 - 00:10:13:13
Stefan
I would agree with that. Like the LLMs, that we use to, like, go through the transcripts and find
the important stuff with customer feedback. I think it's useful when you're using copilot or how
do you use it? You still go and write the code. Or do you like, write like what you want it to be
like? For example, I want a function that does this and then it goes in it.
00:10:13:15 - 00:10:19:26
Stefan
Autocompletes it for you, are you actually writing out the function and you're just hitting tab for it
to complete.
00:10:19:28 - 00:10:46:15
Dustin
And more more the more the more the later part. I think haven't yet utilized that to the fullest, to
the fullest. But, yeah. I think there's absolutely room for improvement in that, to improve my
workflow, but I usually, usually just to complete, code and. Yeah.
00:10:46:17 - 00:11:03:10
Stefan
Yeah, I've been messing around a little bit with cursor, like some side projects. And what I don't
like is sometimes like, like I know what I want to implement in my head, like, say this function.
And then I start writing a little bit of it and cursor goes ahead and jumps and it implements the
whole function, but it's not right.
00:11:03:10 - 00:11:15:23
Stefan
And so then it confuses me. And then like it's still there on the screen. So then as I'm like
implementing it, it's a little bit of annoying. Do you run into the same things kind of like that a
little bit or. I don't know, like sometimes the autocomplete bothers me a little bit.
00:11:15:26 - 00:11:40:09
Dustin
Honestly. I haven't used the cursor yet. I heard heard a lot about it. I didn't use it to write, whole
whole components. I'm more on the on the, on the, on the path or more on the side of complete
my existing code. And not let not, not let anything. write. My whole application to.
00:11:40:11 - 00:11:41:15
Dustin
Yeah.
00:11:41:17 - 00:11:58:06
Stefan
I’d agree with that crazy story though. So my little sister, she's, she's about to be a senior in
college. She's finishing up her junior year. So third year of college. And, for one of her classes,
she had to make a personal blog. And, the teacher was like, hey, you guys can use WordPress.
00:11:58:06 - 00:12:18:05
Stefan
You can use a Wix. You know, those, like, website like that help you like create templates, a
blog. And I was like, hey, if you want to be different, like go get cursor like the free plan, go look
up Next.js. Go look up like, like a content delivery system, like all that stuff. And just download
cursor and just start asking questions.
00:12:18:05 - 00:12:42:23
Stefan
How to build a blog and, using cursor and, like, just asking like, claude questions and things like
that. In a week she built, like a fully functional, like blog with Next.js, and she has no programing
experience. And so, I don't know, I thought that was crazy, that like with AI, she was able to build
a blog like on Next.js without ever having any programing experience.
00:12:42:26 - 00:12:54:13
Stefan
But then like, like, does that make somebody an engineer? Is she an engineer now? It's like she
was able to develop a whole front end application with no programing experience using AI.
00:12:54:16 - 00:13:04:07
Dustin
You know, it would be nice if during that workflow, during the journey, the AI would explain her
what she actually did.
00:13:04:09 - 00:13:12:17
Stefan
So you can prompt it to do that. You can be like, hey, let's make a blog site, but teach me the
steps of what we're doing. Like, what are we actually doing?
00:13:12:19 - 00:13:26:21
Dustin
Then I think then it's, I think, a great learning experience. If not, then it's why not? Why not,
using a blog platform to to to create your. Yeah, your content.
00:13:26:23 - 00:13:53:15
Stefan
Yeah. It's a fair point. And then, so right now we're hiring like crazy, and Dustin's doing a lot of
interviews and, he's like the first quality control gate for technical people. Have you noticed, like,
since the introduction of AI and like, open AI, have you noticed that, like, there's some AI
generated code in the applications, maybe care like some hallucinations and then you catch it
on the interview or like, has it just been like the same?
00:13:53:18 - 00:14:19:12
Dustin
Honestly, I do not really care if someone use AI if they're able to achieve the end result. I mean,
we will always have a peer review meeting where we discuss the code, where I wish he should
explain his thought process, why? Why he did this and that. And, if he used some AI to to speed
up his workflow, why not?
00:14:19:15 - 00:14:33:06
Dustin
Assuming he understands what he did, and, Yeah, I mean, it wouldn't it wouldn't be fair. I mean,
I use AI every day, all our developers use every day. And why not using it as an exercise?
00:14:33:09 - 00:14:51:02
Stefan
I think it's fair. Like it's weird. Some companies like that, my friends are out there, like, No, AI like
you can use ChatGPT for, like, stuff like that, but no AI in the code base and then other ones,
which is crazy. They made every developer use cursor because they're like it's going to increase
productivity. And I was like, I don't know if that's true.
00:14:51:02 - 00:15:12:11
Stefan
So I don't know this whole AI thing. And like with developers, it's interesting. And then I asked
Jens this question last week, but yes. Explained to us like what we're looking for. Like we're
pretty well aligned on the core values of the graph that we're looking for in new hires. But like
from a CTO point of view, what is like what do you want a new hire to do when they come into
wundergraph?
00:15:12:11 - 00:15:23:02
Stefan
Are they more like they they pass a technical bar, but what kind of attitude are you looking for?
Like what would make a good person to join us? And like, what do you look for as a CTO?
00:15:23:04 - 00:15:56:04
Dustin
I always looking for for people who are super passionate about what they're doing and they
need to be they need to be open for new things. They're always trying to put things into
question. If something doesn't make sense, people who are not shy to ask questions and, yeah,
I think this, this, this, this, this mindset of of of of,
00:15:56:06 - 00:16:23:01
Dustin
Yeah. This open mindset about about, yeah, this is super important. Other than that, yeah. You
need to be doing you need to be good at at your domain. If it's if it's a platform engineer role or
is it a full stack developer role? But those things, we will probably figure them out, during
interviews, during the exercise, and.
00:16:23:01 - 00:16:34:06
Dustin
But if you're super keen to, to learn new things and your. Yeah, you love what you're doing, I
think this is this is the core principle. Yeah.
00:16:34:08 - 00:16:58:00
Stefan
I agree. So I think it's a good transition to kind of like let's get a little bit into the tech. So I want
to talk about a mistake that we made. Pretty early in our journey at Startup Founders. So for
those of you that don't remember, we had Wunder Graph SDK and we decided to create
Wonder Graph Cloud, which were you could think of is Wunder graph was this great framework
for building applications.
00:16:58:02 - 00:17:19:24
Stefan
And we built a cloud on top of that. And one of the key decisions I remember this, where we
were sitting in the room, we said we're going to use fly.io. They're a startup, but we're going to
bet on them. We're not going to do AWS. They have this great firecracker. You can you can talk
a little bit more on that part, but and if you guys saw the news, Tercer is also migrating.
00:17:19:24 - 00:17:40:27
Stefan
Our Tercer is migrating also away from fly io. A lot of people are leaving fly io. But walk me
through, like, kind of like that decision that we made to use fly io and like what we experienced
and then like kind of like as a CTO, like how that affected us, why we moved away and just kind
of like how reliability is, is king in a cloud hosting company, if you will.
00:17:41:00 - 00:17:45:08
Stefan
You know, we'll just talk a little bit about like what with fly.io, what happened with fly.IO?
00:17:45:10 - 00:18:19:05
Dustin
Yeah, I think that's, that's, I would say a funny and a sad story. So if you're building a startup,
you want to be fast, you want to prototype very quickly. You want to figure out if this is a fit. And,
everything that that yeah, that can support you. You will probably also utilize. And for us, fly was
a great candidate of deploying custom, custom, custom CI custom containers worldwide.
00:18:19:07 - 00:18:23:22
Dustin
With little cost. with little steps. Oh.
00:18:23:23 - 00:18:24:26
Stefan
So easy.
00:18:24:28 - 00:18:51:26
Dustin
Yeah. He's the provider I they provide a great API to, I would say an easy, an easy enough API
to, that was worth to explore. And, yeah. And, but the more and more, traction you get, from,
from your product and people beginning to, to rely on you, you also need to be reliable as a
service.
00:18:51:26 - 00:19:18:13
Dustin
And, and then, we figured out that, the yeah, the service that fly provides in terms of support,
even paid support or, API stability. Yeah. They couldn't provide, the right guarantees to us. And
after several incidents, we had to make a cut and, yeah.
00:19:18:16 - 00:19:43:08
Stefan
It's difficult because what fly is building is amazing. Like, if it works like to provide that service as
APIs, though so easy to spin up a container. The firecracker VMs were really cool and they were
really fast. But the reliability part is hard. People don't understand and this actual industry
scares me. So the cloud like just to give you like an understanding of how big the cloud market
is.
00:19:43:08 - 00:20:06:18
Stefan
So, Vercel did 100 million in ARR AWS did like what was it like 100 billion or like some ridiculous
number? And then you have Azure doing like 60 billion ARR. Like they're just doing that in ARR.
So you can imagine how big is the cloud market. And I was talking about this with Dax actually
this week.
00:20:06:20 - 00:20:30:18
Stefan
Any company that builds like on top of the cloud. So meaning like Vercel, you know, they
provide a great front end experience. But it's built on AWS. Eventually they have to become the
same price as AWS because any consumer like us, like you'll get to a point where you're paying
so much just for the experience and you're like, why is there such a margin on top of a cloud?
00:20:30:18 - 00:20:43:00
Stefan
You know what I mean? So like eventually that provider will have to bring their price down to be
equal as AWS, and then they have to provide value on top of that. I don't know, just something
we were talking about. Do you have any thoughts on that?
00:20:43:03 - 00:21:08:28
Dustin
No, I think I think that's right. And the reason why, AWS, is, is the most popular and the first, first
candidate in choosing reliable, reliable infrastructure and. Yeah, as, as I said, like, as a startup.
And you don't you don't have any customers. You have to count any cents. It's you can rely on
fly until you have proven.
00:21:08:28 - 00:21:40:10
Dustin
Proven your point. Your product. But as soon as you get serious, you want to have uptime, you
want to have guarantees. And, I would never choose a fly or any other provider again if I if if my
goal is to to build a reliable foundation for my, for my company. So then I would, I would rather
spend a little bit more money than trying to trying out new things that are unproven.
00:21:40:13 - 00:22:00:20
Stefan
And so with that learning, so we, we, we chose fly for wundergraph cloud. And then when we
started building Cosmo, we pivoted all going and all in on Federation, we built an extremely
reliable piece of software. So what were some of the decisions that you chose? Like what do we
host on what. And we it's boring tech.
00:22:00:20 - 00:22:11:09
Stefan
It's extremely boring. It's not like exciting like fly with firecracker VMs and all this stuff. We chose
boring tech this time. So what do we choose for Cosmo? And like, why do we make those
decisions?
00:22:11:11 - 00:22:31:29
Dustin
Yeah, I think all comes back to the to to to our learnings from wundergraph cloud. We no longer
rely on fancy tech. So right now we use GCP. There are Kubernetes is offering to, to run our
platform, or to run our reference architecture. You also find on Cosmo docs.
00:22:32:02 - 00:22:37:13
Stefan
And yeah, you can actually bring it up when you bring a
00:22:37:15 - 00:23:06:04
Dustin
What else. We also rely on cloud for workers to, to distribute our, routing configs, which, which
are super reliable. Yeah. I think 1 or 1 of the core values of our architecture, but also in general
for smaller startups is mind your own business. So we never try to be an expert in, in any
technology here except our own product.
00:23:06:07 - 00:23:30:08
Dustin
So for clickhouse for example, we rely on click clickhouse cloud. You don't want to run
clickhouse clusters, at least not at this. At this point, we, we use, managed databases as is,
where we can and this also includes, for example, for key cloak, which you see in in the middle,
which is our identity provider.
00:23:30:15 - 00:23:46:12
Dustin
For authentication and federated auth, we also use cloud IAM, which is a managed solution for
for keycloak. And yeah, front end is running on the next.js. So yeah.
00:23:46:15 - 00:24:08:19
Stefan
Yeah, it's very simple, very boring. But I think you have to go through what we did with, like,
relying on a provider. And then imagine telling your customers like, yeah, our service is down,
but there's absolutely nothing we can do about it because our provider is down. And so we
made decisions to go boring with Cosmo. And I think that's like, that's the thing you're paying for
with AWS or GCP.
00:24:08:19 - 00:24:29:09
Stefan
You're not paying for an amazing experience, which is why there's so many companies that
build on top of AWS to make it better. But two things on that is one, when you look at AWS and
you look at how clunky everything is, there's a reason they made those decisions. They've
thought about it extensively, and there's a reason why some things are clunky and it's because
of reliability.
00:24:29:09 - 00:25:02:10
Stefan
They made those decisions because they want to make sure that the platform is reliable, and
it's kind of slow on purpose and which you have companies build on top of that to make it better,
make AWS not a pain. And then the second one is it's such an interesting space because it if
you think about it, I just going to unshare if you think about it, if a company were to come in and
make AWS ten times better, but they also provided the reliability, like, like what I'm trying to say
is like, do you ever think somebody could overtake AWS?
00:25:02:10 - 00:25:20:02
Stefan
Like, I'm like a big guy for like, like David versus Goliath stories like, I like, for example, Deep
Seek can OpenAI. OpenAI is a giant and then Deep Seek destroyed them for a little bit. We
don't know what'll happen in the future, but do you think somebody could ever do that to AWS?
00:25:20:04 - 00:25:30:17
Dustin
I would say for sure. But, even let's say someone is doing that, it needs to be proven. It needs to
be proven for years. And,
00:25:30:19 - 00:25:40:05
Stefan
But how do you do that, like AWS? Like, has the reliability, AWS has the logos and AWS is the
cheapest. Like how do you compete against that?
00:25:40:07 - 00:25:59:03
Dustin
I wouldn't say its the cheapest, but I think there's there's definitely room for competitors on the
market, but yeah, it's tough. It's. Yeah I.
00:25:59:05 - 00:26:17:24
Stefan
I'm telling you, you can't like I'm huge on David versus Goliath stories, but and I hopefully I'm
wrong in my lifetime. But I don't think you can compete against AWS, even me. And Jens say
this all the time, like AWS wins every single time simply because it's AWS. It's too big to fail.
00:26:17:27 - 00:26:44:19
Dustin
Yeah, I think you can build a optimized solution to pull some percentage from the market. But,
when it comes to really reliability infrastructure, and there were and they were the, they become
better and better. It's no longer that shitty UI. It's, I think the last time I checked AWS, it's. Yeah,
it is no longer that bad as it was before.
