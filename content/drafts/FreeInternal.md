---
title: "Free Theory With An Internal X"
date: 2021-1-12
---
Consider the free theory with an internal X extending x. When we externalize its internal X, we get some X extending x. But is it x on the dot, or might it be changed from x to have more in it? It seems obvious but not obviously obvious that, when Set itself is an X, we should get back x on the dot. Here, I want to write out the reasoning, to make it obviously obvoius.

I'm phrasing this very abstractly, because I mean for it to apply very broadly. Whatever Xes are, they should form a category. And whatever theories with an internal X are, they should form a category. From the latter to the former, we should have a functor G which sends any theory with an internal X to the externalization of its designated internal X. To say that we have, for any given x : X, a free theory with internal X extending x, is to say that this functor we just noted has a left adjoint F. And to ask for the externalization of this free structure's internal X to be x again, in the desired way, is to ask for the unit of this adjunction to be an isomorphism.

By abstract nonsense, the unit of an adjunction is an isomorphism just in case its left adjoint is fully faithful (because the condition for y to be isomorphic to GFy via the unit is by Yoneda the same as the condition that maps from x to y are in isomorphism with maps from x to GFy via the unit, which is by the adjunction the condition that maps from x to y are in isomorphism with maps from Fx to Fy via applying F, which is what it is for F to be fully faithful).

So how do we see that F is fully faithful?

First of all, note that for any x : X, there is the particular theory Set with internal x : X. Call this theory Kx. Though K may not be a functor as such, we know that GKx = x for any object x. Thus, G is essentially surjective on objects.

From G to GFG by unit, then back to G by counit, is identity, by the zig-zag law for an adjunction. Thus, the unit is at least a split monomorphism at each object in the range of G. But every object is in the range of G by the previous paragraph, so the unit is a split monomorphism at every object.

If we can now show that the monad is idempotent, we are done, by https://ncatlab.org/nlab/show/idempotent+monad#Properties.

TODO

***
This goes off the rails with scratch notes now:

GFGK to GK back up to GFGK.

GFx to x back up to GFx.

From GFx, we map to x, because the free theory introduces whatever crap, but all that crap maps into the Set model, which is me. And then from me I map back up into the free theory.


Anyone with a value in it gets a shadow value. In Set, we have the particular rule that shadow values collapse.

Free theory where all sets have a designated involution.

In Set, the designated involution is always identity.

GFx to GKx should be identity?

G(Fx to Kx)

Ok, suppose we have theories T, and a functor from Ts to Cat taking each T to its category of internal Xes. An X internal to T is any map into T from some designated free T on the initial X, call this R.

And there's a particular theory T called Set, and the claim is that we have an adjunction between T-with-an-internal-X

So maps from R to t induce maps from R to Set.

unit at Kx, taken through adjunction, then G applied.

Kx to GFKx

x -> GKx
FGKx -> Kx is such that G applied to me is a monic.
GFx -> GKx

G(counit)K is monic

Fx = FGKx

G x to GFG x

Gx = GFy.

Maybe something about sconing will help here.

Given a T with internal X, we (X, T, function from X to G(T))

An X internal to T is a T-indexed X. A functor from T to (Theory of X) lexly to Set. A lex functor from Theory of X to Set^T. The free lex theory with an internal T
***

The salient thing is actually how Hom(1, -) produces free models of lex theories.