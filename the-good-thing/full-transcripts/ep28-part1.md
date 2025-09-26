00:00:10:09 - 00:00:18:21
type: podcast-chunk
Stefan Avram
You.

00:00:18:23 - 00:00:36:18
Stefan Avram
And we're live. Welcome back, ladies and gentlemen. I know it has been a while, but we are back. And we're back to our regular scheduling posts of the good thing today. What better way to start our welcome back that had a special guest today. Thank you so much for joining us. We have Daniel Kocot, A principal API consultant at Code Centric.

00:00:36:18 - 00:00:41:23
Stefan Avram
So today we're going to talk all things APIs. But Daniel thank you so much for joining us. How are you doing today?

00:00:41:25 - 00:00:46:15
Daniel Kocot
Yeah. Thank you for the invitation. Yeah I'm I'm quite relaxed because it's Friday as we know it.

00:00:46:15 - 00:00:49:13
Stefan Avram
So no that's nothing.

00:00:49:13 - 00:01:06:09
Daniel Kocot
I think nothing to really to really think about. So having, having closing the week the, the week and looking for for next week because next week I’m traveling some, some, some of some things around. So this might be become very interesting.

00:01:06:11 - 00:01:28:20
Stefan Avram
Okay. Very cool. Well thank you so much for joining us. A little background on Daniel is that he's the principal API consultant and head of API consulting at Code Centric. He has a deep background in APIs and application lifestyle management. He also serves as an advocate ambassador for team topologies and async API. You started your career right at code centric at 2016 as an Agile Solutions consultant.

00:01:28:27 - 00:01:45:22
Stefan Avram
Since then, you've done four different roles until you're at your current position in 2022, two, correct? Yeah. Correct. Okay. Okay. Awesome. So we have a lot of topics to discuss today. Jens. Hasn't. Yeah. Yeah I was going to say Jens hasn't said anything. So Jens. How are you doing today.

00:01:45:25 - 00:01:49:22
Jens Neuse
Yeah. You were only talking about our special guest.

00:01:49:24 - 00:01:51:14
Stefan Avram
He gets jealous sometimes.

00:01:51:14 - 00:01:59:03
Jens Neuse
Had a break. You had a break, but the show went on. We had a great show last time with Amazing people.

00:01:59:05 - 00:02:04:02
Stefan Avram
Yeah, it's true, but I wasn't there. I didn't bring the energy. But I'm back now, guys. Nobody worry because. Jens.

00:02:04:06 - 00:02:07:12
Jens Neuse
How are you? Life is not just centered around you, Stefan?

00:02:07:15 - 00:02:09:12
Stefan Avram
Well, in my world it is. But how are you Jens?

00:02:09:19 - 00:02:13:10
Jens Neuse
Who's chair is completely broken. Is it? Is it Daniel's?

00:02:13:13 - 00:02:15:09
Daniel Kocot
Oh, I'm standing.

00:02:15:11 - 00:02:16:09
Stefan Avram
Yes. Then be then.

00:02:16:09 - 00:02:21:09
Jens Neuse
Hold up. Yeah. Is that mean? Is that the chair or is it your bones?

00:02:21:11 - 00:02:28:20
Stefan Avram
Yeah, that's a good point. I need to get a new chair. Okay. I'm going to try to sit very still so we don't hear it at all. So hold up.

00:02:28:23 - 00:02:51:02
Jens Neuse
But. Yeah. How are you doing? Take a breath of the stream. You know, like today Jacob has vacation or. I'm not sure what he's doing, but he he can't let go of us. We today we have Brendan in the in the background. He's responsible for clicking the button to start and stop the stream. So thank you, Brendan, for taking that responsibility.

00:02:51:04 - 00:03:03:09
Jens Neuse
Okay. We have Daniel today here. This is cool. Daniel and I, we actually know each other in person. We met many years ago in, I think it was Sweden. It was.

00:03:03:09 - 00:03:04:15
Stefan Avram


00:03:04:15 - 00:03:09:00
Jens Neuse
Where was it again? Oh, platform summit. I think platform summit. Yes.

00:03:09:02 - 00:03:09:13
Stefan Avram
Yeah.

00:03:09:15 - 00:03:10:24
Daniel Kocot
2 Years or something like that.

00:03:10:24 - 00:03:12:15
Jens Neuse
So yeah, it was.

00:03:12:15 - 00:03:15:19
Stefan Avram
A while ago. Do you remember. Yeah I think 2023 maybe.

00:03:15:21 - 00:03:17:07
Jens Neuse
Did you go as well Stefan.

00:03:17:10 - 00:03:22:29
Stefan Avram
No, but I remember you had to go because we got like a last minute conference talk. So I think that's when it was 2023. Yeah.

00:03:22:29 - 00:03:25:00
Jens Neuse
Yeah. We, we did a talk that then.

00:03:25:00 - 00:03:27:15
Daniel Kocot
It's only two years. So.

00:03:27:18 - 00:03:48:04
Jens Neuse
Yeah. Awesome. And Daniel, you you mentioned you you will be traveling. I just saw a picture from Eric W, who's currently at some conferences. I think there's some. What is it? API world is going on currently. Yeah. And what are your plans for next week?

00:03:48:07 - 00:03:51:27
Daniel Kocot
Customers visiting customers.

00:03:51:29 - 00:03:53:22
Stefan Avram
So being an interesting.

00:03:53:24 - 00:03:59:03
Daniel Kocot
It's the normal way in to not be remote all the time. So really really talk with customers.

00:03:59:03 - 00:04:02:14
Jens Neuse
You need to say with more enthusiasm that that's.

00:04:02:14 - 00:04:05:04
Stefan Avram
Yeah customers.

00:04:05:06 - 00:04:29:20
Daniel Kocot
It's not it's I will give a talk that's at a customer on site. So it's a more relaxed thing. And then we have several days when our customer will be dipping into, into integration platforms and doing doing this. We maybe hit later. So so this is what what's really strikes me at the moment.

00:04:29:22 - 00:04:48:04
Stefan Avram
Fantastic. And Jens, we were just talking about this, yesterday we took out some of our customers to lunch and me and Jens were strategizing. We're like going forward into 2026. We need to go. Oh. Just kidding. Can't tell you guys, right? Basically, we might be around your neck of the woods is what I'm trying to say.

00:04:48:07 - 00:05:09:21
Jens Neuse
Yeah. No, that that's, like, you know, in this, I don't know, like Daniel we’re a vendor. You're a consultant. So. So it's also interesting to see a different perspective in the market, but, we started our company after, or right in the middle of COVID. And so it was kind of like the normal thing to not visit people.

00:05:09:24 - 00:05:31:18
Jens Neuse
And, it can be a huge downside, like, you can build relationships in a different way if you if you meet people. And I guess if you're doing consulting in the in the API segment, it's it's probably much easier to do like a webinar or something on site versus doing it virtually. And you can't really meet people.

00:05:31:18 - 00:05:40:00
Jens Neuse
And how do you think from a consulting perspective about being remote versus being onsite?

00:05:40:02 - 00:06:05:01
Daniel Kocot
Oh, being remote is good when you have these deep type of tasks. So you really know what what what you have to do because you you have to write a concept. You have to go very deep discussions with other people where it's just fair enough to be using teams or whatever, or Zoom or Google Meet, whatever is in place there.

00:06:05:01 - 00:06:37:23
Daniel Kocot
And but really to to have conversations about problems, challenges, whatever, it's it's really important to be on site because sometimes you, you met somebody on accident. It was not planned to meet there. So you, you you meet people you don't normally have meetings with because with this remote thing, you always have to set up a meeting. It's you always it's quite it's quite boring to to really ask, oh do you have some time for coffee.

00:06:37:23 - 00:07:04:29
Daniel Kocot
And we can do it virtually when you are really working remote and in different city and different countries. We have this with customers. It's totally fine because it's not the other way possible, but being onsite at a customer and and talking with the people there, it's it's for for me, it's a boost to, to to really go more into into the project again because before COVID you were always on site.

00:07:04:29 - 00:07:29:14
Daniel Kocot
It was the normal thing to be on site and not to say, okay, I work from home or I work from the office and do stuff remotely, it was really like, be there, listen to the people, have lunch. If you stay overnight, have a dinner together or something like this. And it's, it's now it's, it's a, it's a sometimes a new experience for some people.

00:07:29:14 - 00:07:50:05
Daniel Kocot
So, so because most of them are still. Oh I don't go to the office. It's not worth but but in the end it's, it's more or the for me the results are better when you when you work with people on site because you have them. Yeah. They can't leave. You can book a room for a whole day again.

00:07:50:07 - 00:07:51:13
Stefan Avram
Yeah. Yeah.

00:07:51:18 - 00:08:15:25
Daniel Kocot
It's it's it sounds funny, but when, when you have remote meetings I can switch the camera off. Sometimes we work with customers that don't even have the camera on all the time. So you don't see what they're really doing at all. If we give trainings or, do enablement with, with, customers, it's actually quite hard because you don't know who's really listening.

00:08:15:25 - 00:08:40:24
Daniel Kocot
And so on and so on. And even if you have workshops or deep sessions, it's sometimes better to do it, to do it really on site. So that's why you have to tell, because it's consultancy. So it's not sitting in somewhere as you maybe do do it when when you do more do the product work, you can you can stay at home and be remote all the time if you would like to do so.

00:08:40:26 - 00:08:47:07
Daniel Kocot
For the for the consultancy, it's important to be there where where actually the people are.

00:08:47:10 - 00:08:49:09
Stefan Avram
Yeah. I would add to Stefan.

00:08:49:12 - 00:09:17:04
Jens Neuse
Do you remember. So we have an angel investor from meta Facebook and we once we went to, to San Francisco, we visited the office and, like, not not talking about Facebook, like, it's not like, doesn't matter what you think about them, but what I found interesting is the whole environment at meta, like the campus, it's it enables you to to run into random people and to be like, hey, what are you working on?

00:09:17:04 - 00:09:27:17
Jens Neuse
What what product are you doing? And, and you can build those connections online They would never actually happen because you cannot run into people. And, no, that's so.

00:09:27:19 - 00:09:47:03
Stefan Avram
I want to add to that, though, Jens every time we do a retreat and we're like doing stuff with strategy or anything or in person, Hen's always has guys laptops down. And it's the same thing when we visit customers as we put the laptops down and you can see people are engaged, but when someone doesn't have the camera on and you're consulting with them, the worst is cameras off, okay?

00:09:47:03 - 00:10:03:10
Stefan Avram
And then you go through it you tell them how to set up cosmos or whatever, not even a week later in the slack. Hey, how do you set this up? And it's like we went over that in the meeting, so I'm 100% with you. I like it much better. Also, you do a little bit of work after work.

00:10:03:10 - 00:10:16:21
Stefan Avram
You go get a beer, you get to know this person. And now it's not just a consultant from another company. It's Daniel who I had a beer with. And I know that he's traveling and I know his hobbies. So that way when I ask a question or something's broken, I'm not yelling at Daniel. I'm saying, hey, Daniel, could you help me out?

00:10:16:21 - 00:10:20:21
Stefan Avram
Because we built that relationship. But I would say you've kind of nailed it on the head there. Yeah.

00:10:20:23 - 00:10:44:20
Daniel Kocot
That's that's that's that's actually the thing around. So to really get into conversations with people maybe outside of of of of the whole topic, it's also quite important to, to really have, have some kind of bonding or something there to, to really see if you, if you can really work together. Because when you do projects, we are doing stuff in the, in the bigger enterprises, there's always politics.

00:10:44:20 - 00:11:14:23
Daniel Kocot
You really have to know people good. know what, what, what games are being played and so on and so on. So it's, it's it's that kind of thing also. And you, the more you are related to a person, it's it's so easy. Within COVID it was sometimes quite, quite hard because you have 2d the people faces up front, but you don't really see what what is, what is happening with them.

00:11:14:25 - 00:11:43:21
Daniel Kocot
And sometimes they just drop off the camera and then say, oh yeah, I'm, I'm angry about this and that, and you can't really see the face and anything like that. The real reaction. So it's really for me, it's absolutely the max, the, the minimum to, to be with a customer from nearly one time in a quarter to really see what is happening on site.

00:11:43:24 - 00:12:05:26
Daniel Kocot
How are the people feeling about the things, that happened over, over the period of time and so on and so on. So this is this is most important because remote work and consulting so, so not just do the programing stuff. So really bringing architectures to work and and so on and so on. You need this conversations.

00:12:05:29 - 00:12:30:03
Jens Neuse
You remind me of an all hands like before WunderGraph at another company. So my, my office is direct. I can look into our garden straight and, we had this all hands I put on my headphones, and then camera off like everybody else. And I went to the garden and did some leaf blowing and that that's.

00:12:30:09 - 00:12:33:06
Stefan Avram
Well, yeah, I, I.

00:12:33:07 - 00:12:55:03
Jens Neuse
Have to say, I have, I have a high quality leaf blower from Makita, which has, it's, it's, battery driven. It has two batteries. It's extremely powerful. The batteries only last 30 minutes, but it's, it's a lot of fun, and it has a lot of power.

00:12:55:06 - 00:12:55:22
Stefan Avram
And, you.

00:12:55:22 - 00:13:20:03
Jens Neuse
Know, as a as someone who who works in tech doing some gardening or some leaf blowing or like, you know, we we have, pumpkins in the garden and we have tomatoes and stuff, and gardening is is fun. It's it's it's something where you where you put the phone to the side for a moment and just cut the hedge or do whatever.

00:13:20:05 - 00:13:34:25
Stefan Avram
My favorite there though, you know, the, the memes where it's like you're out your stand up in a remote company and it's like, here we go, here we go. You've been preparing all day doing the exercises, and then you unmute. Nothing from my end. Thanks. Boom. Done day. Oh.

00:13:34:26 - 00:13:49:14
Jens Neuse
Okay, Daniel, let's take a step back. Yeah. You're a consultant. You're in the API space for a lot of people. The API space couldn't be more boring. How did you get into that space? And what kept you there?

00:13:49:16 - 00:13:50:26
Stefan Avram


00:13:50:29 - 00:14:20:21
Daniel Kocot
Long story short, when you do Atlassian consulting and you are not living in the green field, you have to integrate. So you see a lot of not the best API's in the world. And you think about, okay, how we can make this actually better. And why are people not really understanding the needs of the other side to, to, to really go into this?

00:14:20:29 - 00:15:14:02
Daniel Kocot
This is how it actually started, because I started as an Atlassian consultant, at code centric, upfront. I was doing technical, product development and, and so on. So really the, the groundwork to really have the development skills and so on and so on. And then happened something I was in a mulesoft project, so doing doing, plumping and understanding why people don't really understand what is what is all about with, with API's actually at some level, see what what is actually happening when you when you see posts from Kim, from Kim Lane and at that time and, and then I read a book about API economy and so on and on.

00:15:14:04 - 00:15:43:23
Daniel Kocot
And then it was clear for me, okay, there is something more then I do. I did a little exercise doing kong consultancy at Code Centric for for a period of time within COVID, but that didn't really reflect. So we ended up in doing real consultancy with no tooling in the background. So really do this API thinking stuff we have here or think about this capability thinking.

00:15:43:26 - 00:16:11:11
Daniel Kocot
I'm published this week and it's it's really about yeah, bringing disciplines together. So looking at architectures, looking at people. So that's why I'm also doing a lot of in the team topologies environment. So it's really a lot of things that come together because in the end the tooling or the technology is not the problem, the problems or the intelligence.

00:16:11:11 - 00:16:37:07
Daniel Kocot
Are the people involved into this. And this is what we are, what we are heavily triggering it. It was a long process to to really get there because you have to do big projects that maybe fail or not work as expected to to to really get there and see, okay, what's the benefit? And then maybe you have possibilities to find customers that that had the same in the past and want to do it better.

00:16:37:09 - 00:16:55:26
Daniel Kocot
And with this we, we go into into the scene like having the idea of APIs or products doing this thinking stuff to be more on the scene, to really understand what consumers want to have. And so this is this is actually the story. It's a long process.

00:16:55:28 - 00:16:58:18
Jens Neuse
So APIs is the people problem.

00:16:58:20 - 00:17:02:11
Daniel Kocot
Yeah definitely. It's it's not it's not a problem.

00:17:02:13 - 00:17:09:09
Jens Neuse
It's not about REST. It's not about SOAP. It's not about GraphQL. No. It's about people.

00:17:09:11 - 00:17:11:02
Daniel Kocot
Definitely. And the scale.

00:17:11:04 - 00:17:15:20
Jens Neuse
That sounds a bit abstract. Like you can't just blame it on the people, right?

00:17:15:22 - 00:17:46:11
Daniel Kocot
No, it's, it's actually the, one of the biggest problems is these little tutorials you find all over. Yeah. How to create a REST API with spring. Technology. It should be possible if this framework is not not capable of creating, rest APIs you can't use it. Really? And all the other stuff involved. Yeah. So you see a lot of fast API stuff when you go on, on, on the Python scene.

00:17:46:11 - 00:18:17:24
Daniel Kocot
So it's always tech related. The problem is then the abstraction layer. So having a tutorial is something different than doing it in the wild because once you have a tutorial it's really, really abstract. So it's not clear how you deal with the data. Normally when you do such tutorials, it's like I'll just go into the database and drop out this table to be a rest API.

00:18:17:26 - 00:18:42:18
Daniel Kocot
That's nice, but it's not efficient in the end. So it's really also about to really think, okay, what is really needed to to create a good environment or a good experience for, for the users to really think about. And this is where it's lacking because people didn't understand in the past what rest rest means. They heard somewhere that SOAP is bad.

00:18:42:20 - 00:19:13:04
Daniel Kocot
Maybe it isn't bad for some use cases might be helpful. Then they they heard other things. So it's really always on technology side. But the understanding is still missing because when you ask, have you ever read a book about enterprise integration patterns? Most of the people leave the fingers down. Yeah, if I'm in the integration space, I have to really read and understand the basic literature.

00:19:13:06 - 00:19:46:00
Daniel Kocot
So if I don't get this enterprise integration patterns or I really understand what I would like to do, it's quite hard. So it's somehow a people problem. It's an enablement problem. Because when people are used to build APIs, they do it as their normal development routine, but they don't really think about if there is a strategy. So they don't ask maybe questions and they don't really understand.

00:19:46:02 - 00:19:47:21
Stefan Avram
Where.

00:19:47:23 - 00:20:15:12
Daniel Kocot
The company or the organization wants to go with that. They just have these features. Oh, they want an API that delivers customer data, but there is nobody questioning it why they want to have it. And what is the impact of this? Is it going outside of the organization? Is it going outside of the department and being inside the organization and so on and so on.

00:20:15:12 - 00:20:40:10
Daniel Kocot
A lot of questions aren't asked. And this is this is the people problem there. So it's not just saying it's the people problem. It's really the understanding, what should I do there. Because technically everything is actually solved. I have different styles to to get the data there. I have different patterns to, to get what, what I actually want.

00:20:40:10 - 00:20:53:11
Daniel Kocot
But there is what is really missing is the connection in between, because normally nobody talks to the business side. And this is also something which is which is really hard in the end.

00:20:53:13 - 00:21:02:27
Stefan Avram
But well said. Jens I have one question, but, I want to pass it to you first. Do you have a question based on what Daniel said already?

00:21:02:29 - 00:21:04:21
Jens Neuse
We have a question from David.

00:21:04:24 - 00:21:06:07
Stefan Avram
Yeah, that's the one I wanted to bring up.

00:21:06:07 - 00:21:34:08
Jens Neuse
I would love to go through the through the flow. Like what is? Because you you you you you mentioned like a bunch of topics like patterns. So, so maybe we can talk about, what what's are good patterns or principles everybody should know like use. You talk about the important books. Maybe there are some standard literature we should all look into.

00:21:34:10 - 00:21:57:09
Jens Neuse
And then in general, how can an organization like think strategically about APIs and, and, what I hear when I listen, I kind of hear that developers often jump the gun. You say, here's a problem. They build a rest API. They haven't even thought about, this, this API in the more broader sense. So I think that that's one thing you say.

00:21:57:11 - 00:22:14:01
Jens Neuse
But here we have a question from, David's question for Daniel. How do you navigate consultancy when the client / customer thinks they know better or refuse to listen to advice?

00:22:14:03 - 00:22:18:22
Stefan Avram


00:22:18:25 - 00:22:40:22
Daniel Kocot
There are different answers to to to the question actually personally, I will drop the customer. Because it's my nerves. It's nerve wracking when there is no, no no respect to to really to really understand why the consultant or the consultancy is doing several things.

00:22:40:24 - 00:22:42:15
Stefan Avram


00:22:42:18 - 00:23:15:13
Daniel Kocot
And. Maybe sometimes people are not willing to, to let other opinions really get into their mind because they are so focused on doing things the way they ever did. So when you talk to somebody who's 25 years doing software development in an insurance company, they have their own way to go. Maybe it's good, but maybe it's not good because something changed in the organization.

00:23:15:16 - 00:23:55:14
Daniel Kocot
So then it's not a part of the the part of the consultant or the consultancy to, to move these people. It's actually part of the, of the organization at itself to say, okay, be more flexible, do this stuff. The others are bringing in, appreciate what they are doing because they have the knowledge. But to be honest, I had a situation like that and I dropped the client because it doesn't make sense to, to to to work with somebody who is not willing to, to, to really understand what, what what it means or what are the differences between and so on and so on.

00:23:55:16 - 00:24:02:27
Daniel Kocot
Because, because in the end they will come back. Normally, or you.

00:24:03:01 - 00:24:03:26
Jens Neuse
Know, we.

00:24:03:28 - 00:24:23:18
Daniel Kocot
does the same thing to them and then say, okay, they were right because we had this in the past, we had a customer that wasn't wasn't, wasn't aware and not willing to take training sessions. We don't need this our people are skilled enough.

00:24:23:21 - 00:24:25:17
Stefan Avram
Yeah, yeah.

00:24:25:19 - 00:25:06:02
Daniel Kocot
It took it took some time. But then they bought the training and saw. Okay. It was really needed because they hadn't had a problem in understanding and a problem in wording. So the people name things differently and don't really understand what the other person means by that. So it's also the things what we saw always when we talk with customers because is this password API is so misused in these days because in the end it's just an application programing interface.

00:25:06:04 - 00:25:40:09
Daniel Kocot
And that could be everything. So it's not quite clear what what what it really is. So REST is not is not only an API, it's some kind of an architectural. So it's really hard to, to, to, to really bring this people to, to the right place in at some point so that the to, to to answer the question, it depends on the customer if he wants to deal with politics and stress or drops the customer, it's, it's really it's really that that kind of thing.

00:25:40:11 - 00:26:09:25
Daniel Kocot
Because the things we do well with, what we call API consulting is really on trust. People have to trust us because we do things. We did them several times. So it's not that we just invented something. We did it always with customers. This is this is the approach behind it. So we don't propose anything that is not be done with a customer or relates to work with customer.

00:26:09:28 - 00:26:27:15
Daniel Kocot
So this is this is mostly important. So it's nothing that that somebody was sitting in a room and, and had this whiteboard after him and just putting boxes together and say, okay, this is the solution. This is what we go into the market with. And this will work. So it's it's really related to, to to yeah. To customer challenges.

00:26:27:15 - 00:26:28:22
Daniel Kocot
There.

00:26:28:24 - 00:26:35:09
Jens Neuse
Do you know this famous video from Steve Jobs on consultants.

00:26:35:12 - 00:26:36:21
Stefan Avram


00:26:36:24 - 00:27:08:04
Jens Neuse
Where Steve Jobs says consultants they, they can't do well because they come to your company. They tell you what to do and they will not stay long enough to see the long term effects of the suggestions they gave. So they will never really learn like two years after. What what they did was actually a mistake. How do you how do you think about that?

00:27:08:06 - 00:27:37:10
Daniel Kocot
To be honest, API consultancy is a long term thing. So we work with customers for more than for nearly five years with customers right now. So it's not nothing. You go in and be there for six months and you move out. This can happen if there is a lot of understanding already, and there's just the idea of getting the last bits of pieces to really get your own initiative running.

00:27:37:13 - 00:28:02:29
Daniel Kocot
This is also what we have with customers. But the normal thing is you stay as long as possible to really see what what is, what is happening behind the scenes, what is happening in in the whole definition of, of enterprise politics. And so on and so on. And this really helps you to to engage and really also grow with the customer, not just to say, okay, I'm in.

00:28:03:01 - 00:28:30:11
Daniel Kocot
Oh yeah. Six month. I'm not interested anymore in this. I have to leave. This is not this is not really working. When you when you really do some kind of I would say it's more related to enterprise architecture, what we do. So you you need some time to see. Yeah. That that it really works out. So it's nothing that that that is placed and comes up after 2 or 2 weeks or something like that.

00:28:30:11 - 00:28:33:12
Daniel Kocot
It takes time.

00:28:33:15 - 00:28:45:03
Stefan Avram
Yeah. thats fair. And I would tend to agree with that. It's good that you guys stay on for the long part of that journey. The ends are funny enough. I knew you were going to bring that up. Really? Yeah that video I know.

00:28:45:05 - 00:29:14:02
Jens Neuse
No not not not in a negative way. I'm just curious about your your your take. I have no strong opinion on the on the craft in general, but. Okay. You mentioned REST is not just an API. Some people would say it's an architectural style or pattern or, how would you say the understanding of APIs and REST over the years has changed?

00:29:14:02 - 00:29:41:20
Jens Neuse
Because we recently had Kevin Swiber on the On the Stream. You probably know Kevin and also the one, one one of the, known names in the, in the API space. And he also kind of, kind of said like, in the past when people said REST, they might meant like hypermedia or something. But today it can be anything, it can be JSON over HTTP.

00:29:41:21 - 00:30:07:08
Jens Neuse
And he also said like, it's it's not so important how we call the things like, because MCP and hypermedia have actually quite a lot in common. And he's like, yeah, like the patterns are all the same. It's just a bit different. And we name things differently today. But but hypermedia was never really gone. It's just yeah, the styles they, they changed.



