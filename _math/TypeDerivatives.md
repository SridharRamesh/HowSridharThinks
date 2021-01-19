---
title: "Type Derivatives"
date: 2019-1-3
---

An often observed fact in type theory/functional programming/etc is that that, given a type constructor T(X) [a type T parametrized by an input type X], the corresponding type with one "hole" acts like the derivative of T(X). (See "The Derivative of a Regular Type is its Type of One-Hole Contexts", discussions of "zippers", etc.)

For example, X^3 is the type of triples of Xs. And then 3X^2 is the type of triples of Xs with one X replaced by a hole: either an X on the left and right and a hole in the middle, or an X on the left and middle and a hole on the right, or an X on the middle and right and a hole on the left.

This is just a baby example, but the same is true even with much more complicated recursively defined types; for example, with Tree(X) = 1 + X * Tree(X)^2 [a binary tree with internal nodes labelled and leaf nodes unlabelled], we can differentiate both sides and get Tree' (X) = Tree(X)^2 + X * 2 * Tree(X) * Tree' (X) [thus, a one-hole context for such a tree a is either a pair of left and right child trees (the case where we've put our hole at the root) or a root X, a child tree, a child one-hole context, and a Boolean specifying which of these is the left and which is the right child].

It may seem a magic coincidence that the rules of differentiation should line up with the rules of one-hole contexts. Well, it's not such a coincidence. You can get a fair way to understanding it just by thinking about why particular differentiation rules like the product rule and sum rule should work, but this is still slightly ad hoc; it doesn't quite explain why they should ALL line up the right way. Instead, this is how I think of it, as a unified phenomenon:

A good way to think about this (or, at least, what I consider a good way to think about this) is that often, but not always, for a type constructor [i.e., function from types to types] T(X), we have an equation of the form T(X + Y) = T(X) + Y * Secant(X, Y), for some other type constructor Secant(X, Y).

Here, T(X + Y) on the left-hand side is like instances of T where the "points" can be either Xs or Ys, and on the right-hand side, T(X) is those instances using only Xs, while Y * Secant(X, Y) is those instances using at least one Y.

Furthermore, the latter is broken down so that Secant(X, Y) is those instances using at least one Y, with the "first" (or some canonically selected one, canonically selected in a way which doesn't depends on its own contents) replaced by a hole, so that Y * Secant(X, Y) plugs the hole.

Then the derivative of T(X) is Secant(X, 0).[^continuity] And this is the same as the instances of T(X) using at least one Y, the first replaced by a hole, the rest unfillable; i.e., the instances of T(X) using precisely one hole, and no other stray Ys.

[^continuity]: One needs some principle that tells us Secant is uniquely determined, for this to work. In analysis, this principle is continuity; at most one continuous selection can be made. But in lots of contexts, there is some analogous principle constraining the avaiable functions that has nothing to do with infinitesimal limits per se.

All of this falls apart if we cannot make the equation T(X + Y) = T(X) + Y * Secant(X, Y) for some Secant(X, Y); thus, it falls apart for, for instance, T(X) = 2^X.

And indeed, I don't know of any sense in which there is some type ln(2) * 2^X acting like "the type of functions from X to Booleans with one hole where the datum of an X would normally go".

So by thinking about the correspondence of type differentiation the way I like, not only do we understand the correspondence with one-hole contexts in nice cases, but we also understand clearly the limitations of this phenomenon!

[Note to self: 2^X is a contravariant endofunctor, while the other examples given so far are covariant endofunctors. Are there natural examples of type derivatives on things which are not covariant? Perhaps not. What happens for covariant 2^(2^X)?

What we're really interested in is endofunctors on the category of coproduct injections (in the context of Booleanness, these are precisely the monics). This let us decompose T(X + Y) into T(X) + Something(X, Y), where Something(X, 0) = 0.

The fundamental further principle that lets us do differentiation is that if F(0) = 0, then F(X) = X * G(X) for some G (and then F'(0) = G(0)). This isn't always true even for injection-preserving endofunctors, though; consider, e.g., the functor which reflects sets into propositions (so it sends 0 to 0 and everything else to 1). Thus, just as in analysis class, not everything is differentiable.]

TODO: Rewrite all this. Consider F(Y) to be o(Y) just in case every instance of F(Y) uses more than one instance of an Y. Then T(X + Y) = T(X) + Y * T'(X) + o(Y), with a unique decomposition, and this of course lines up with how we think of derivatives. The key thing about o(Y) is that it's closed under linear combinations and contains Y * o(1) [where o(1) means F(0) = 0].

[TODO: See https://en.wikipedia.org/wiki/Combinatorial_species#Differentiation ]