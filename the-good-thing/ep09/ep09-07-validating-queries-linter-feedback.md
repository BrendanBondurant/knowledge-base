---
title: Validating AI-Generated Queries and Linter-Like Feedback Loops
slug: ep09-07-validating-queries-linter-feedback
series: The Good Thing
episode: 9
chunk: 7
participants:
- Jens
- Cameron
segment: Query validation and feedback loops
timecode: 00:25:32:11 – 00:30:07:10
start_time: 00:25:32:11
end_time: 00:30:07:10
speakers:
- Jens
- Cameron
topics:
- Vector similarity search process
- Query validation techniques
- Hallucination prevention
- Multi-step validation approach
- Linter-style feedback loops
- Cursor AI development patterns
tags:
- ai
topic_tags:
- query-validation
- feedback-loops
- hallucination-prevention
- ai-development
- linting
- cursor
entities:
- GraphQL
- GitHub
- Cursor
mentions:
- WunderGraph repository stars query
- validate query tool
- AST parsing and validation
- linter feedback integration
- 60% accuracy rate
- cursor code generation
summary: Cameron and Jens discuss the technical implementation of query validation,
  including vector similarity search, multi-step validation processes, and preventing
  AI hallucinations. They explore using linter-style feedback loops, similar to Cursor's
  approach, to improve query accuracy and provide immediate validation feedback.
---

00:25:32:11 - 00:26:05:27
Jens
So, so that means so, frankly speaking, you read a lot of books, and from these books you kind
of learn that human and user somehow they are correlated. And so they are nearer, or whatever
you would say. And so this is then what what's in the in the embeddings model, if you put user
like I assume like an embeddings model, let's say it's a function you put in whatever and it gives
you a vector kind of right.
00:26:06:00 - 00:26:07:16
Cameron
Yep. It gives you the token which is a vector.
00:26:07:16 - 00:26:46:04
Jens
And so the vector of human and, and person would be closer or more similar than a vector
between human and car, okay. And now we have our query. We have or we have our prompt
like hey, I want to get the stars of the WunderGraph repository. So you take this text and you,
you also make it a vector or and then, then, then you search for, for your slices in the graph that
are most similar to that.
00:26:46:06 - 00:26:48:05
Cameron
Yeah. Exactly.
00:26:48:08 - 00:27:12:28
Jens
Okay. So on the high level you're kind of saying “I have a question. Take a look at all the parts of
the schema that you have indexed that are most similar. And then and then load those into the
context. And I give you then the prompt again, maybe in some other format. And then you,
you're telling me how to write the query to do that.”
00:27:13:00 - 00:27:14:12
Cameron
Exactly.
00:27:14:14 - 00:27:41:06
Jens
Okay. And then if you do that, we know there is this topic of hallucinations. Okay. So how do I
know that the query that it generates like, or how can I somehow force it to create a graphql
query, or will it just create text? Or how do I get to the point where it actually makes me a
GraphQL query and that is actually valid?
00:27:41:08 - 00:27:56:28
Cameron
Yeah. So we I did handle that in two different ways. So the first way is actually by, in the
prompting, which is it works most of the time. I actually.
00:27:56:28 - 00:27:59:12
Jens
60% Of the time, yeah.
00:27:59:13 - 00:28:03:16
Cameron
Require, You know, that's why. It's why it's two steps, not just one.
00:28:03:18 - 00:28:05:17
Jens
Okay.
00:28:05:20 - 00:28:42:06
Cameron
But I, I provide it with a tool, the validate query tool that allows it to actually verify and validate
queries against the full, the full graph. So, you know, it'll actually run a validation on the full
GitHub query or not query the full GitHub schema and it'll return back to the model, the validity
of it, or if there are errors, any errors that happen so that, that kind of acts as like a feedback
loop almost to give the model context and information about that graph and where it's going
wrong.
00:28:42:09 - 00:29:14:05
Cameron
And then the second thing that happens is actually verifying the query and parsing out the
response. After the model says, hey, I'm finished. I think this is a valid query. I actually validate
and verify the query post response. So I will parse through the returned values and I will find the
query, and I will revalidate it and triple check it against that that schema again to ensure that it is
accurate.
00:29:14:07 - 00:29:49:19
Jens
Yeah. One one one pattern I have seen with using cursor is and I think this, this is really smart.
We, we also we will also talk about what are good languages for for vibe coding. But one thing I
saw is when you have like cursor write code for you, it immediately uses a linter, which I think is
really smart because if you if you have an AI write something and then you run a linter over it,
Linters give you very good information about the thing that you just tried.
00:29:49:19 - 00:30:07:10
Jens
It's actually wrong. It's broken. So if you do that, you can immediately feedback the linter result
to have it properly form, the query or whatnot. Or maybe it's even not parseable because it's
broken. Then you can fix that. So are you are you using like a similar technique?