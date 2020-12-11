---
title:  "The Y Combinator (aka, diagonalization)"
date: 2020-12-08
---
TODO: Rewrite the following into the post I want it to be, about how diagonalization in the Cantor/Russell/Gödel/Lawvere/Yanofsky sense is the same as the Y combinator and also the Y combinator is obvious in retrospect. For now, this post is taken from an old Quora thing I once wrote, in response to the prompt "What is the Y combinator?" or some such thing.

***

Suppose you wanted to write a program that referred to its own source code at some point.

You could try to write it in BASIC (or Java or Haskell or English or whatever your favorite programming language is [^FavoriteLanguage]). But, you might find that to be too tricky at first. So nevermind BASIC; you decide to instead simply invent a hypothetical new programming language BASIC++, which is just like BASIC, but augmented with built-in support for programs to be able to access their own source code: this language has a basic keyword "myOwnSourceCode" within it, which is to be interpreted as just what you'd think from the name.
How does one actually run a BASIC++ program? Well, one thing you might do with a BASIC++ program (let's call it P) is compile it into an ordinary BASIC program, by going through its source code and replacing every instance of the keyword "myOwnSourceCode" with, of course, the expression of the actual source code for P.

[^FavoriteLanguage]: In other words, there's nothing special about BASIC. All the times I say "BASIC", it's just a placeholder for any arbitrary language.

Great. So we know how to compile BASIC++ programs into ordinary BASIC programs. (Indeed, this compilation process is so simple, we can presumably go ahead and write such a compiler in BASIC). And we also know how to write BASIC++ programs which refer to their own source code (it's trivial by the design of the BASIC++ language).

But perhaps now you'd like to return to the original quest of achieving such self-reference in ordinary BASIC instead of BASIC++. Well, BASIC++ can help us do this too, like so: By combining the two abilities in the last paragraph, you can write BASIC++ programs which refer to the compilation of their own source code into BASIC.

And then, by actually compiling such a program into BASIC, you're left with, in fact, an ordinary BASIC program which refers to its own ordinary BASIC source code. Ta-da!

In summary, we've outlined here a general technique for writing BASIC programs which refer to (which is to say, do whatever you as a programmer want them to do with) their own source code.

(If you can furthermore write (or, even better, have primitively available) an interpreter in BASIC which executes whatever BASIC source code is passed to it as input, then this technique lets you write programs which refer to the result of interpreting/executing their own source code. That is, you would have the ability to write code which refers at various points to (i.e., does whatever you like with) its own return value, a phenomenon more familiarly known by the name "recursion". Even if you're working in a language which doesn't have built-in, primitive support for recursion, as long as you can carry all this out, it is still possible to implement recursion.)

The structure of this whole technique can be mathematically formalized, and "the Y combinator" is the name given to that formalization in "the lambda calculus" (the abstract study of things like this [^YLambda]). But nevermind the formalization; the above is the idea.

[^YLambda]: For those who are familiar with the notation of the lambda calculus, the Y combinator is defined by Y f = compile ($$\lambda$$ myOwnSourceCode. f (compile myOwnSourceCode)), where compile p = p(p). This just expresses the same idea as was given in words above.

***

Footnotes: