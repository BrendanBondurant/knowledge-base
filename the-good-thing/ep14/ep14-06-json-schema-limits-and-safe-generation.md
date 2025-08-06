# ep14-06-json-schema-limits-and-safe-generation

**Time Range:** 00:22:00 - 00:27:17

**Topic:** JSON schema limitations and deterministic schema generation

---

00:22:00:21 - 00:22:44:12
Dustin
But this can get much more complex. You could have recursive input types. You could, in a later
a demo, we will show you, and find employees, tool that allows you to filter for employees by
nationality, moods, etc.. So what we have to do is we take the, the input, type, we convert that
into, JSON schema and then provide this schema to the, to the tool so the LLM can understand
what the how does the call has to look like in order to fulfill the user request in the LLM session.
00:22:44:14 - 00:23:17:06
Dustin
And this sounds very easy, but if you read the documentation of all the models, you will figure
out that they do not support the full specification of JSON schema, they only support a subset of
it. So for example, the the don't allow the don't support recursive, for the, the recursive
structures. For example you if you, if you would build this from scratch, you would, you would
detect recursion and you would replace and for example definitions references.
00:23:17:08 - 00:23:44:03
Dustin
And yeah, there were there were a lot of edges cases where we had to optimize that for LLM
usage. So instead of, providing definitions like at a dollar depth definition or as part of JSON
schema, we just, limits limiting the recursion at the specific depth. So to have to, to produce a
valid Json schema. And then you need to understand that, yeah.
00:23:44:03 - 00:24:17:26
Dustin
All these nuances of when is a field nullable, we have to provide all the values in case of you
using enums, required needs to be, correctly implemented, when at least one argument is
required. Then the, the object is required of the input, and so on and so forth. And one comment
I or I know I, we will I think we when we, when you scroll a little bit more we will come to the
okay.
00:24:17:29 - 00:24:55:01
Jens
But let's stay here for a second because that's there's more to it. I could just create my own
MCP server. I, I, I guess I would vibe code it and I would just put no, like, for real. I mean, who,
who writes code today. So you vibe code, it, you just give it this query or you tell it like, here's a
schema and put and put this query and, would this just work or what kind of problems can I run
into if I built my own MCP server and just tell like, hey, put this get product query.
00:24:55:01 - 00:24:59:26
Jens
What, what what's, how will the outcome look like?
00:24:59:29 - 00:25:10:04
Dustin
I mean, I mean, you would like to to pass the, the, the exercise to generate the JSON schema
for the, for instance, is the right.
00:25:10:06 - 00:25:29:02
Jens
Yeah. So if you so you let's say you, you vibe code the JSON schema for the, for the query. You
vibe code this how how confident would you be that this is that this is correct.
00:25:29:04 - 00:25:37:19
Dustin
I would say it really depends on on your proficiency in the domain, but it's I would say.
00:25:37:22 - 00:25:53:00
Dustin
It's I would say it's pretty. It's pretty pretty pretty. Difficult because you would need to understand
how the GraphQL specification works and how it will be or how it can be mapped to JSON
schema. In that case. Yeah.
00:25:53:00 - 00:25:54:06
Stefan
Yeah.
00:25:54:09 - 00:26:15:18
Jens
I think so. I think what would happen is you have this ID, which is mandatory. AI will probably
figure out, okay, JSON schema needs to be a string and it needs to be not optional. And we can
look at it as a human because we need to review the vibe code stuff. And we will say, okay, this
this looks about right.
00:26:15:20 - 00:26:43:17
Jens
But then later I think you will show us an example of a more complex query and data structure,
and it will very easily reach the point where our input variable, it is so complex that a. we are not
100% sure if every field the LLM has actually translated in the right pattern. And second, I think
it can easily get to, level of complexity where we're we're not 100% certain anymore.
00:26:43:24 - 00:26:50:20
Jens
would yeah.
Like, even if you look at it, you will not immediately see it's wrong. It could be wrong. So and I
00:26:50:22 - 00:27:17:00
Dustin
I would even say this is like the perfect example by not using LLMS for because this is like a
deterministic, task to convert something from A to B. If you would use LLMS for that, it is not
even it is super costly, but also that you wouldn't leverage the power of LLMS in this case,
because LLMS, are good at being creative, finding patterns.