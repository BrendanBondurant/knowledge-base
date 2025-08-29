---
title: Robert Farr's Journey to Procore
slug: ep19-01-robert-farr-journey-to-procore
series: The Good Thing
episode: 19
chunk: 1
participants:
  - Stefan
  - Robert Farr
segment: Introduction and Guest Background
timecode: 00:00:09 – 00:05:01
start_time: 00:00:09
end_time: 00:05:01
speakers:
  - Stefan
  - Robert Farr
topics:
  - Robert Farr Career Journey
  - Cerner to Procore Transition
  - Kansas City Tech Scene
  - Distributed Systems Experience
tags:
  - kansas-city
  - ai
  - federation
  - founder
  - go
  - graphql
  - graphql-federation
  - rest
  - startup
topic_tags:
  - kansas-city
entities:
  - Robert Farr
  - Procore
  - Cerner
  - Kansas City
  - Missouri
  - Stefan Avram
  - WunderGraph
  - Milo
mentions:
  - Kansas City geography spanning two states
  - Stefan's previous work at Milo in Kansas City
  - Robert's background in distributed systems
  - Career transition from healthcare to construction tech
summary: Stefan introduces Robert Farr, Principal Architect at Procore, discussing
  his background in Kansas City and career journey from Cerner to Procore. The conversation
  covers Robert's experience in distributed systems and site reliability engineering.
---
Episode 19
00:00:09:26 - 00:00:27:17
Stefan
Oh, cool. And we're live. Thanks for joining us for another episode of The Good Thing. Today we
have a very special guest, someone we've been working very closely with. But Robert Farr, a
principal architect at Procore. And as always, I'm joined by my co-founder and co-host, Robert.
How are you doing today?
00:00:27:19 - 00:00:36:11
Robert Farr
Doing great. Doing great. It's a beautiful morning. So a little overcast, but, you know, it's bright
out. So enjoying the day.
00:00:36:11 - 00:00:40:11
Stefan
hear again.
Fantastic. And where are you calling off from? Is a, You've told me before, but I'm curious to
00:00:40:14 - 00:00:47:02
Robert Farr
Yeah, we're, I'm out of, well, north of Kansas City, Missouri. So right in the central, United
States.
00:00:47:02 - 00:01:09:23
Stefan
So awesome. And I don't know if you know this, but I used to go there often last year or. No,
three years ago before we started WunderGraph, because I worked for a company called Milo,
which was literally, like on the line of Kansas City and Missouri. So you can go back and forth
between the two, which kind of threw me off a little bit, because you would see the you would
see the different license plates, but it was a good it was a good place to be.
00:01:09:23 - 00:01:24:14
Robert Farr
I loved it. Yeah, yeah. No, it's an interesting city. And we're right on the border between two
states. Their state line drive is probably, right in that range of where you were. So. Exactly. A lot
of a lot of culture.
00:01:24:17 - 00:01:41:12
Stefan
So awesome. Well, thanks for joining us today. So today we're going to be talking about is just
kind of your role and experience. So first you roll out procore. You're leading overview of your
experience. And then we're going to dive a little bit into the kind of the conversations that we've
been having, you know, things that you've seen and your years of experience.
00:01:41:12 - 00:02:00:08
Stefan
For example, with delivery pipelines, GraphQL, GraphQL, Federation, AI, how AI is coming into
organizations and things like that. It would just be like an ad hoc discussion like this. But to kind
of kick things off, Robert, tell us a little bit about your experience. So we've been working with
you as you've been a procore but where did your journey begin?
00:02:00:10 - 00:02:27:26
Robert Farr
Yeah, yeah. So I've, you know, my procore journey has been the last, I would say three and a
half years. But prior to that, I spent, really got my start, at my company. So 22 years at a,
enterprise healthcare IT company, that that companies now part of Oracle Health. So for those
that are curious, but I started out there as a software engineer, right.
00:02:27:26 - 00:03:02:09
Robert Farr
Junior software engineer and, got to experience, building an enterprise company that ultimately
became an enterprise SaaS company, over those years. So, learned a lot, learned a lot from a
lot of very knowledgeable architects, over those years and got to see how you can transform an
industry, with software, in this case, it was very, you know, health care focused, and now I find
myself kind of doing the same thing in the construction industry.
00:03:02:12 - 00:03:06:26
Stefan
Very cool. And this company, what was it called before it became Oracle Health?
00:03:06:28 - 00:03:11:19
Robert Farr
It was called Cerner. Cerner, so certainly operation. Yeah.
00:03:11:26 - 00:03:14:12
Stefan
They they just recently became, Oracle Health.
00:03:14:12 - 00:03:18:25
Robert Farr
Right. Yeah. In the past couple of years I believe. Yeah.
00:03:18:28 - 00:03:26:26
Stefan
So I had a lot of friends that worked at Cerner. And then they went to Milo, which is where I was,
because Cerner has a good headquarters out where you're based, right?
00:03:26:29 - 00:03:53:24
Robert Farr
Yeah, yeah, Cerner headquarters was here in Kansas City. It was, founded in Kansas City back
in 1979. So, I had the privilege of getting to work for the the founding CEO or the founders for,
the majority of that time. And, the, it's really, you know, I would say a lot of my, my colleagues
and coworkers, they have spread out into a number of different startups and companies.
00:03:53:26 - 00:03:58:17
Robert Farr
In this area, some of those are working remote, but some are really right here in Kansas City.
00:03:58:19 - 00:04:10:11
Stefan
Kansas City has a decent tech hub. From what I remember when I was there, there's some
decent startups and just kind of established companies. I worked at Lockton, but Cerner is
there. There's Procore, I have an office there now.
00:04:10:14 - 00:04:34:11
Robert Farr
We we have a, we have a, wework, so procore, shortly after I joined, we, we, acquired a
company called Labor Chart, which had a office in Overland Park. So there is a number of
procore, employees and engineers that, live here in the Kansas City area. That's awesome. Just
go ahead.
00:04:34:14 - 00:04:50:14
Robert Farr
Oh, no. Yeah. You said, you know, in terms of its tech hub. Yeah, I think Kansas City is is it's got
a really interesting tech hub. There's the the Kaufman Institute downtown that really helps
startups get going. So it's fostering a lot of innovation.
00:04:50:16 - 00:05:01:15
Stefan
You know, I can attest to I've seen when I visited, it was awesome. And then you started off your
career at Cerner and you said you spent 20 years there, or how did you make the jump to pro
core?