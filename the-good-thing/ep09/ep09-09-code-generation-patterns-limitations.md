# ep09-09-code-generation-patterns-limitations

**Time Range:** 00:33:27 - 00:36:34

**Topic:** Patterns and edge cases when using AI for code generation

---
00:33:27:04 - 00:33:55:05
Cameron
But, you know, doing, you know, doing all of the things that are time consuming is just super
simple, like writing SQL migrations, writing comments, helping to write tests, helping to, you
know, build out data models like those types of things. It is super powerful and it's a very helpful
tool for, you know, an engineer to have in their back pocket to be able to move extremely
quickly.
00:33:55:07 - 00:34:15:07
Jens
Yeah. But what I've found where it works really well is if you give it a pattern and you, you want
to replicate this pattern for other things. So let's say you create like, like a design of a new
solution. And you, you make the design for queries and then you tell it, okay, can you do the
same thing for mutations?
00:34:15:09 - 00:34:39:29
Jens
Because it's kind of almost the same. But it would be nice to have also a spec for mutations. But
you are lazy and it's very good at that. One use case where where I found it to be dangerous is.
So let's say you have an AST in one language and you want to make some transformation and
create an AST in another language.
00:34:40:01 - 00:35:02:12
Jens
So what I have found cursor doing and this like you need to be extremely careful with this kind
of stuff. So you add a simple use case. So I'm, I'm the way I try to approach it is I try to start with
something super simple so that I bootstrap like one function that does one thing, and then I add
another test case.
00:35:02:12 - 00:35:28:29
Jens
So I go like very test driven. So I start by writing one test and an empty function. And then I tell it
to implement this okay. And then I write a second function where I add one more feature. So I
make this test a little bit more complex. And for example there one one pattern I already
observed is you need to be thinking about do I want to stick all tests in one file or one file per
test?
00:35:28:29 - 00:35:52:15
Jens
Because like these files, they can quickly go super large. And then the model might get
confused by so much context. So these are things you need to to consider. But what I have
found is so you start with a simple use case. It it implements it. Then you add a more complex
one. It figures it out and then you add like a really complex one.
00:35:52:17 - 00:36:35:03
Jens
And what I have observed there is. So again this use case is AST transformation. So you have
one nasty, you turn it into another. And what's, what's so I was using 3.7 solid agent model and
what it kept trying to do is instead of writing a function that looks at my AST and tries to
dynamically or tries to write code that dynamically derives something from the AST, it kept
hardcoding AST literals into the implementation for a specific use case.