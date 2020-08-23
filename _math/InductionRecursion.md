---
layout: post
title:  "Induction and Recursion"
date: 2020-4-26
---
It is often thought that induction only applies to well-founded orderings, not to structures like the reals. But actually, it is very common in mathematics to do induction arguments over the reals, only people do not recognize them as such when they do so.

The principle in play is this: Suppose you want to prove something is true of all semipositive reals (the interval $$[0, \infty)$$). Then it suffices to prove that whenever it is true all values less than $$x$$, it also true of all values less than $$y$$, for some $$y > x$$.

Note that this is essentially the same principle as what is sometimes called "strong induction" over the natural numbers.

We can also split this into: It suffices to prove that whenever it is true of all values less than $$x$$, it is also true of $$x$$, and furthermore whenever it is true of all values less than or equal to $$x$$, it is also true of all values less than $$y$$, for some $$y > x$$.

Indeed, we can now see that principle is just the special case for reals of this most general principle which holds of all partially ordered sets:

Suppose you want to prove something is true of all values (in some partially ordered set). Then it suffices to prove that whenever it holds of all values in downwards closed proper subset $$D$$, it is also true of all values in downwards closed set $$E$$, for some $$E$$ which is not a subset of $$D$$.

Why does this principle hold, of any poset? Well, consider the union of all downwards closed sets where the predicate in question holds. This is the largest downwards closed set where the predicate holds. But our induction hypothesis tells us that no such set can be maximum, unless it is the set of everybody. Ergo, the predicate holds everywhere.

The phrasings for the reals take advantage of the special form of downwards closed sets within the reals, given its completeness properties. And the phrasings for well-founded sets similarly take advantage of the special form of downwards closed sets within them. But the above is a phrasing which works for any partial order whatsoever.

[TODO: Relate above to recursion, not just induction]

[TODO: Give examples of arguments in math which are instances of this pattern of induction over the reals]

This real induction principle is actually the implicit undergirding of a lot of analysis arguments, just not framed explicitly as such. For example, let us prove that any analytic functions which agree on an open set agree everywhere:

By reparametrization, it suffices to prove that any analytic functions on the ray $$[0, \infty)$$ which agree on a neighborhood of $$0$$ agree everywhere.

Well, if they agree on all points $$< x$$, for any positive $$x$$, then they have the same continuous derivatives of all orders at $$x$$ and thus the same power series expansion around $$x$$. There is also some positive radius $$\epsilon$$ around $$x$$ within which they both match this power series expansion, and so they must furthermore agree at all points $$< x + \epsilon$$.

This establishes our induction hypothesis for all positive $$x$$. And the one remaining case of our induction hypothesis, at $$x = 0$$, is what we took as our presumption of agreement on a neighborhood of $$0$$.

Thus, as we have established our induction hypothesis, we can invoke our induction principle, to conclude that these functions indeed agree everywhere. QED.

[TODO: Relate strong induction on partially ordered sets to regular induction on sets not presumed to come with such an ordering]

[TODO: Build this into a much larger post on induction/recursion in general, as special cases of each other, in terms of initial algebras, in the transfinite, induction over the reals and its unification with a form of strong induction]