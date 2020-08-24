---
title:  "Möbius Inversion"
date: 2019-11-25
---
Let $$\leq$$ be an arbitrary binary relation (not necessarily transitive or reflexive, despite the notation). We will impose one condition: $$\{y \mid y \leq x\}$$ should be finite for every $$x$$ (this finiteness condition can maybe be relaxed in some form for what we're doing here, but for now we'll impose it).

Let $$f$$ be an arbitrary function whose domain is this same set and whose codomain is some abelian monoid (it may as well be the mapping into the free abelian monoid upon this set), which we will describe using additive language.

We can take such $$f$$ to a corresponding "summatory function" $$F(x) = \sum_{y \leq x} f(y)$$.

Conversely, given an arbitrary such function $$F$$ (which is to say, we could now take $$F$$ to be the free abelian monoid mapping), we may seek some $$f$$ from which it arises in this way.

In general, there may be none or multiple such $$f$$. However, if we now suppose that $$\leq$$ is the reflexive closure of an irreflexive relation $$<$$, we can decompose our summatory relation as $$F(x) = f(x) + \sum_{y < x} f(y)$$. If now suppose our abelian monoid is an abelian group, we can re-arrange this as $$f(x) = F(x) - \sum_{y < x} f(y)$$. If we now suppose the $$<$$ relation is well-founded, this gives us a recursive definition of the unique $$f$$ from which $$F$$ arises as its summatory function.

This is called Moebius inversion.

[TODO: Discuss special cases of linear orders, products of orders, inclusion-exclusion, the divisibility relation on positive integers/Dirichlet series, chromatic polynomials, and necklace polynomials (including with respect to arbitrary groups).]