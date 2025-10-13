00;38;15;03 - 00;38;42;22
Jens
Stefan, question for you. If you have something that is very simple, a very simple interface, and it can contain custom logic and this custom logic, it can contain whatever we want. It is very simple to implement. It is very easy to test. And it's very quickly to, to actually write that just a little bit of code because there's no framework, nothing.

00;38;42;22 - 00;38;53;13
Jens
It's really just gRPC. What, what kind of modern cool solution could we hand this to do nice things?

00;38;53;15 - 00;38;57;29
Stefan
Sounds like AI maybe an LLM. Cursor.

00;38;58;01 - 00;39;29;21
Jens
This and this is intentional. So what we were thinking of at the very beginning is what is the next wave of building graphs, and how can we add more capabilities to our graph and one big blocker we found is everybody has a lot of legacy. They have Rest, API, Soap, APIs, databases, whatever, like just old services. Nobody wants to touch them and somehow we want to onboard them to the graph.

00;39;29;23 - 00;40;03;02
Jens
So what we did is we intentionally created Cosmo Connect as a system where the interface is so insanely simple, so dumb. It's just a gRPC proto that an LLM can easily, with a little bit of system prompting and guidance, an LLM can easily implemented if you take an Apollo Federation subgraph. I tried to to implement subgraphs with LLMs.

00;40;03;04 - 00;40;26;10
Jens
Yeah. The the results are mixed. Sometimes it works. Most of the time something is wrong. So I have to iterate. So that means me as the driver. I have to understand federation. And I want to create a system where the the driver, the integrator doesn't have to understand federation. So ideally I can just take a schema, run it through a compiler and then ask cursor to to implement that.

00;40;26;13 - 00;41;00;16
Jens
And this is how we designed, how we designed Cosmo Connect because with with the approach of what, what what Apollo did with, Apollo connectors. So you have these directives in the schema, and there's very, very few, like in the, in the global, in the global scheme of text available online, like the the amount of GraphQL schemas with Apollo Connect directives is like like zero like it.

00;41;00;19 - 00;41;26;13
Jens
You will not find it in the training data. So that means LLMs will never really understand how how Apollo connectors work because it's a custom solution. So the only way you got to an LLM to, to do, to do Apollo connect right. Or Apollo connect to to to to do it right is through system prompting and iteration and other things.

00;41;26;13 - 00;41;54;09
Jens
And it's never going to be efficient. So our approach here is with, with Cosmo connect we just have gRPC. So we, we remove GraphQL, we remove entities and everything. We just have a proto and we tell the lamb, hey, here's a protocol. And in this handler we want to make a call to a rest API. Here's the open API spec.

00;41;54;12 - 00;42;19;28
Jens
Implement this. So I, I'm saying the future of federation is that you will tell an LLM that you want to add a new capability to the graph. It will decide the graph for you. And the second step is you tell it that here's a proto and there's the rest API. And it will implement that. It will run a test.

00;42;19;29 - 00;42;51;08
Jens
It will verify everything. And so the user, the architect, they will be responsible for iterating and designing the schema and telling an LLM to implement it. But and I think like gRPC is, is quite an old technology LLMs know a lot of content about gRPC. They understand how to how to write code for that. And so we, we, we think that is the superior solution.

00;42;51;10 - 00;42;52;24
Jens
Well said, well said

00;42;52;27 - 00;43;14;11
Stefan
And one of the other topics I wanted to talk about is it's interesting, Apollo Summit was a couple days ago, and funny enough, we didn't do any pranks this time. I think we should have. But maybe next time, we'll see, even if there is a next time. But Apollo announced some things and. Jens  what is your unfiltered take on what they announce?

00;43;14;11 - 00;43;27;21
Stefan
If I'm completely honest with you, I was a little bit underwhelmed and some of their announcements wasn't thoroughly impressed. But from your point of view, what are some of the things that you thought were interesting or did you think anything was interestin From the summit?

00;43;27;24 - 00;43;31;08
Jens
There was a blog post, do you have like a link or something?

00;43;31;11 - 00;43;34;22
Stefan
Let me get it one sec.

00;43;34;24 - 00;44;01;00
Jens
Because like in general, I think, there were some interesting topics. 111 interesting topic. was like templates for, for for observability tooling so that you can easily see or easily set up like new New Relic and Datadog. It's actually a problem that we have as well. We we keep teaching our customers how to do it.

00;44;01;03 - 00;44;23;16
Jens
Then they announce, but this is like a small, like, incremental thing. Then they announced, an operator very interesting concept, actually, in the Kubernetes space. It's quite an old concept. I think like five years ago or something, we, we started seeing, operators. Someone sent me something. Right? Did you?

00;44;23;18 - 00;44;29;04
Stefan
Yeah, I just sent it to you. So I sent you, everything that they announced in the blog post.

00;44;29;06 - 00;45;00;05
Jens
Okay, let me see. So MCP server. Yeah, we have MCP then graph runtime APM templates I think that's a that's a good thing. It, improves the, it improves the developer experience for, for platform teams. Also the operator, that that's also very interesting to to make deployments better. Like operator kind of goes hand in hand with graph artifacts where you publish, you publish an artifact and it contains the schema and everything.

00;45;00;08 - 00;45;24;03
Jens
That's super funny because it's actually something we, we also looked into in the past we haven't executed yet. But one thing we we figured out is that some of our customers, when they build the subgraph, they take the schema, stick it into the OCI, into the Docker image, and then when they deploy the service, they kind of use OCI tooling or Docker commands to pull it out again.

00;45;24;03 - 00;45;57;04
Jens
So that's that's kind of interesting. We, we will also add something very similar in the future. Yeah. Apollo connectors enhancement. We talked a bit about connectors. Let me see MCP tools. Yeah we, we have MCP for, for quite a long time. I think one of the biggest, differences in, of Apollo and Wunder Graph is they, they do marketing a bit louder, but okay, that's, that's, that's, fine.

00;45;57;06 - 00;46;24;08
Jens
And, other than that, you know, when, when when people tell like and I answered, that's in the beginning. But when people say like, oh, wundergraph is, is not bullish on on federation anymore, like who is bullish on federation. And I, I don't see the improvements like what we're building with eBay. And we have more more things to go.

00;46;24;10 - 00;46;58;13
Jens
I don't know. There's there's features like defer for example, if you, if you look into into defer like Apollo is really good at marketing things that they have, but they actually don't really have them. Because if you compare the implementation of like, there's this old it's a, it's a Node.js gateway from the guild, which I guess it kind of has like one of the best, implementations of, of federation, actually, or the most complete.

00;46;58;15 - 00;47;23;19
Jens
Like it's not like super fast because it's, it's Node.js, but it's quite complete. And if you compare how they do defer versus Apollo router like Apollo router support for the defer, it's like very dumb. And it cannot really split complex queries. It doesn't really defer. But they have it in the, in the marketing. And I think that's like a theme that I see with Apollo.

00;47;23;21 - 00;47;35;18
Jens
They add a feature, they market the hell out of it, but they never really complete the, the, the things. And yeah, it's a yeah, that's I don't know.

00;47;35;20 - 00;47;40;29
Stefan
What's funny is you had a little Freudian slip defer deburg  DeBergalis.

00;47;41;02 - 00;47;55;07
Jens
Defer derfbulous. So did you know that like a while ago, I did an interview with Matt debug of this. I have it still on on my camera. I never published it.

00;47;55;10 - 00;47;58;29
Stefan
Should we should we publish it? It was from GraphQL conf 2023, I think. Right.

00;47;59;00 - 00;48;40;28
Jens
I'm not sure like how, how interesting it is. It's it's in the vault. I have to say, I like I can differentiate it. Okay. So when when, when some people talk negatively about our company, I, I don't like that. And at the same time, I can respect Matt because I think he's a smart person and, and a good engineer and, yeah, we had we had conversations in the, in the past, not so many just, recently and, like, leadership at Apollo also changed, a little bit.

00;48;40;28 - 00;49;06;04
Jens
But, yeah, like, I in general, the I think the ethos inside WunderGraph is that we are a very engineering focused company. And, by the way, we have a lot of open roles, like very, very interesting roles. For example, you can you can help us work on, on, algorithms on improving the Federation tooling and everything.

00;49;06;04 - 00;49;38;13
Jens
But what I'm trying to say is, like, we're very engineering focused and we respect other engineers, like, we're we're probably not the best marketers or we're not known for our sales strategies or something. But in terms of engineering, the companies that work with us, we have very close relationships. When you are a customer, it is very rare that you don't talk to engineers, that you don't talk to founders.

00;49;38;16 - 00;49;59;03
Jens
Whenever a topic gets more interesting, it's typically like, I'm I'm the like the product owner of wundergraph. So I'm, I'm typically, involved. But if you don't know me I'm also like an engineer. Sometimes I, I code on wunder graph, but it's becoming less and less just because we have a lot of people and, and stuff to do.

00;49;59;03 - 00;50;44;06
Jens
And, everybody has a question but yeah. So we're, we're very engineering focused and we really respect engineers and yeah, I think, on on that you are my. Yeah. I'm, I'm, I'm testing for, for Nithin, for example, where we're working on, on on hub together actually next week we meet in, in Cologne. So if you're an engineer, if you want to join a rocket ship, if you want to, to, work with a cool crew of people like Nithin or David, and if you sometimes want to meet in person, then Wunder Graph is a is a really nice place to join.

00;50;44;08 - 00;51;06;17
Jens
Later this year, we will all meet in, in Gran Canaria, where we have our, our last retreat for this year. And then for next year, we have some very big plans. We just hired a field marketer, so we will be much more in person. We will come to to conferences and, we will have a lot to, to talk about.

00;51;06;19 - 00;51;23;27
Stefan
Cool. Well said, really want to emphasize on the hiring. So we're hiring all across roles. I know you said that we're stronger on engineering. Yes, I totally agree. We're an engineering first company, but we're hiring on the marketing because we want to improve and we're hiring on the sales team. So if you want to come join us, there's a lot of opportunity, a lot of pipeline for you guys to join us.

00;51;23;27 - 00;51;40;05
Stefan
But also on the engineering thing, there's so much ownership. One of the things I love about Wunder Graph is everybody owns something and you can come work with Nithin. And, I know he would love a little bit more help on hub, but okay, fantastic. And then the Jens I think I kind of covered to all my points.

00;51;40;05 - 00;51;54;14
Stefan
I mean, we, we went through every single thing. And I think you addressed it pretty well from your end. Do you have any questions or anything that you want to add? We have a quite a decent amount of viewers today. So guys, thank you so much for joining us this Friday morning. We're definitely going to keep it coming.

00;51;54;14 - 00;52;05;07
Stefan
We are going to a bi monthly or every two weeks. But who knows maybe Jacob, if this keeps going we go back to every week. We'll see. But we should have some guest coming on to the pod but Jens. Anything from your end?

00;52;05;07 - 00;52;24;10
Jens
It yeah, we we have, 53 people currently on the stream, so it's, Jacob, David and Nithin, and then, 50 annoyed salespeople from Apollo. Our Stefan.

00;52;24;13 - 00;52;27;29
Stefan
Three just left, by the way. Three just left. Oh, you said that. Okay.

00;52;28;02 - 00;52;37;14
Jens
Yeah, that that that was too much. Stefan. Question for you. How how do you like, as a junior developer?

00;52;37;17 - 00;52;55;23
Jens
No. But for real, from from your perspective, I mean, you you ask quite a few questions. How how do you currently feel about the, the the climate and then what do you think about, like, API space versus AI space and how do you where do you see us in the next year?

00;52;55;25 - 00;53;19;27
Stefan
It's a great question. So like there's two hats from the founder point of view like the AI space. It's the only thing investors will talk about. I fundamentally believe I actually you told me this. So there's a great book that Jens recommended, which was The Rise and Fall of Empires. And what it means is that everything that's happening in your life a pandemic, a war or AI or a technology boom, it's already happened.

00;53;20;00 - 00;53;39;16
Stefan
You just weren't alive when it happened. And so you can see the rise and fall of empires through history by reading a lot of books and Jens recommended this book, and I read it. And one of the things I did as I pieced together the timeline of technology and when the internet came in, the 90s, like actually came, we had a.com boom, and it completely changed everything.

00;53;39;16 - 00;53;57;00
Stefan
And everybody knew that it was here to stay. But you also had the naysayers that were like, oh, it's just a fad. It's going to pass. If we go forward into history, we're going through the exact same thing right now. 90% of these AI companies are either going to get killed by OpenAI, or they're just not going to find product market fit after their initial boom.

00;53;57;00 - 00;54;16;11
Stefan
So we're in this period right now where everything's trying. What that means from the founder point of view is that money is cheap. If you're riding on that, boom. So AI is definitely something as a founder. But two, from a technology point of view, AI is going to make a difference. It's absolutely here to stay and it's going to make a difference into every single thing.

00;54;16;15 - 00;54;34;08
Stefan
For example, I was telling Jens today, I booked my flight for Gran Canaria by talking to somebody on WhatsApp. And it wasn't somebody. It was an LLM. Yeah, it was an LLM. They answered nearly. They booked my flight. They knew all my passport information. They booked. They're using my credit card. And it was done by texting my own personal concierge.

00;54;34;08 - 00;54;57;03
Stefan
So I think from an AI point of view, what we're building is super exciting, which translates to my next point on APIs. But AI from a founder point of view, if you want to get money, you have to do something with AI or at least wait until it crashes. But a very wise man once told me, he said with with fads or with trends, you either watch from the side or you join them, but don't go against them.

00;54;57;06 - 00;55;15;17
Stefan
And I typically think that's actually quite a true thing to say. So with the AI angle and the founders, I think it's important. And I really like the approach that we're taking with APIs. If you know about the space, it's it's tough. And I'll go actually one point because as a junior developer, AI has made my life so much better.

00;55;15;17 - 00;55;28;12
Stefan
So I'm building small projects on the side, and I can just talk to it in English. Like I made a stupid project and I put it on Hacker News, and I had a couple people sign up for it, and I was able to do that in 30 minutes just because I was just building something stupid. On the weekend.

00;55;28;14 - 00;55;48;09
Stefan
I was like, oh, okay. Like that's amazing. I think AI for a developer, it's a joy. Like all that boring monotone stuff that you would do now you can kind of automate and focus on the stuff that really matters, which is requirements engineering, context engineering, and thinking more about problems versus thinking more about the tools you're going to use, which is the code.

00;55;48;12 - 00;56;09;29
Stefan
And so I think from an engineering point of view, it's exciting. From our point of view with AIs and APIs. The API market is super weird, and I think we're probably the most uniquely positioned to disrupt. The reason why is if you look in the API space, the number one is Kong. That's for Rest APIs. But Kong is an old company if you don't know about their history.

00;56;09;29 - 00;56;31;13
Stefan
They came from mash API like I think 10 or 15 years ago, and they sold it and then they pivoted because they had this cool engine around the gateway, which was open source. There hasn't been an AI company or an API company in a while. You have these other kongs? competing in today. And I think this space, if you focus on collaboration, if you focus on, collaboration.

00;56;31;19 - 00;56;49;08
Stefan
Sorry, I said that one twice. But if you focus on that and if you focus on adding an AI angle and then three, if you focus on the graph underneath and connecting everyone's APIs together, I think we're in a very unique position about it. I really do, end of my monologue but Jens. What do you think? Do you agree with some of those points?

00;56;49;11 - 00;57;22;01
Jens
I agree 100%. And I would add one thing I think. So like you mentioned, we're we're in an absolute hype cycle of, of AI LLMs and we're, we're probably still haven't reached peak. But what I believe were the where the true winners will come out is if they don't, if they don't do like, like there will be like very, very few I would say shovel sellers like open AI.

00;57;22;01 - 00;57;53;22
Jens
But actually, for example, I think like the true winner will will probably be someone like Google because of Google with Gemini they are not burning cash or funding to to create Gemini. They have customers and what's, what's what's OpenAI currently is doing is they, they buy electricity for ten bucks and they sell it as ChatGPT for $1 or even less, I think.

00;57;53;24 - 00;58;15;27
Jens
I think they buy it for 20 bucks and sell it for one like it's 20 to 1 or something. It's absolutely crazy, how they lose money on every like every time you use ChatGPT openAI. They, they lose money because they, they want to take market share. And so, I think very, very few will survive on that end.

00;58;16;00 - 00;58;45;18
Jens
But where I see the true value and this is something where except us, I don't think like so many people invest into that topic. And I call it vertical integration. So instead of doing like, like models, AI, whatever, use AI in a vertical way. And by that what I mean is one of our biggest topics is API integration and API governance.

00;58;45;25 - 00;59;19;19
Jens
This is something where we currently build a whole product around, and we're leveraging AI for that product in a way that enables workflows that was never possible before. So that means we we take API design, API governance and collaboration. We take that to the next level through the use of AI. I still think like Federation is is a really good thing to to integrate APIs and to put AI on top.

00;59;19;19 - 00;59;47;24
Jens
So it can also benefit from that, AI trend directly. But I think the, the real value is because, before the AI boom, we had people who wanted to do Federation, who wanted to have microservices because the company needs them to grow. And even if the whole bubble bursts, people will still have APIs, because if you go to the eBay website, you want to see listings.

00;59;47;26 - 01;00;12;02
Jens
And that has nothing to do with AI like Bubble burst or not, people will continue shopping or people will still go to SoundCloud and and do things there, or they will go to Paramount and and get info about sports or whatever. So all these things, they will continue. What's going to happen to AI? We don't know. What will AI cost in the future?

01;00;12;08 - 01;00;52;12
Jens
We don't know what what will happen to companies like OpenAI and their products when funding dries up. We don't know. But I can, I can I can tell you like 1,000%. In the future, you will have people who design APIs and who need better tooling for governance and collaboration. And that's what we're what we're focusing on. So there's I just recently saw a post from someone working for, Andreessen Horowitz, and they were asking on Twitter, if you're working on something super, super boring, I want to talk to you.

01;00;52;15 - 01;00;53;22
Jens
Oh, the enterprise one.

01;00;53;24 - 01;00;54;15
Stefan
I saw it too.

01;00;54;15 - 01;01;24;04
Jens
Yeah, yeah. And, collaborative API design. Microservice governance is probably one of the most boring things you can think of, like go, go to your friends and, tell them, like, it's a bit like, you know, PHP, like, you know, these, these guys with their with the Lamborghinis, who, who, who put on them, like, paid by, PHP.

01;01;24;04 - 01;01;27;02
Jens
But the point I'm trying to make is.

01;01;27;04 - 01;01;27;23
Stefan
Or graphql in the future.

01;01;27;25 - 01;02;00;26
Jens
A feature AI will peak and whatever, but, GraphQL Federation or more specifically, microservices APIs, collaborative schema design and governance, these kind of things stay. They will stay forever. And we're, we're working on on making them much, much, much better with AI. So I don't know, we're we're insanely excited for for that. And maybe the we will in some way benefit and ride the AI wave.

01;02;00;29 - 01;02;28;28
Jens
But even even if we don't at some point, I think, every company will need a strategy. How do we build APIs across ten, 20, 50, 100 teams? And currently I don't see anything that even comes close to Federation. And with what we're building today, I think, it, it will take it to the next level. So yeah.

01;02;29;04 - 01;03;07;16
Jens
I don't know Stefan I, I'm excited for next year and I'm excited for, for joining API conferences and talking about like, new concepts and, and, really, really helping people to design better APIs and, and to, to govern them, in better ways with, with great workflows. And ultimately, if you want to like I said earlier, if you want to enable AI, you need to have a well-designed API and it needs to be well documented and there needs to be meaning and use cases, otherwise AI can't do can't do anything with it.

01;03;07;16 - 01;03;11;19
Jens
So yeah, I think that's that's where we are.

01;03;11;22 - 01;03;27;03
Stefan
Well said, it's that I think it's a great place to end the podcast. Guys, thank you so much for joining us today. This might be a record count, but we're we're happy that you guys are here. We'll be here next week or the week after, but there's definitely going to be guests. More coming on and Jens. I love what you said about A16.

01;03;27;03 - 01;03;45;18
Stefan
Like what we're working on. It might be boring, but it's critical. And if someone from A16 is watching, we are. We were open to having a conversation with you, you know? But Jens always a pleasure. Thanks for watching everybody enjoy the weekend. And I think we have a holiday on Monday. So enjoy your holiday. Enjoy the long weekend and we will see you next week.
