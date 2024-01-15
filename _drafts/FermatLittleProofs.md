---
title: "Proofs of Fermat's Little Theorem"
date: 2024-1-14
---
What I'd like to say about proofs of Fermat's little theorem (or the Euler-Fermat theorem more generally) is going to be annoying to write on Twitter with its character count restrictions, lack of editing, etc, but here is the gist of it:

I've been interested for a long time in cataloguing the sense in which various proofs of this theorem are or are not related to each other. It seems to me every proof I am aware of can be seen as one of the following:

A1) For prime p and natural number x, construct a permutation of a set with x^p many elements, with x fixed points, with every other orbit having size p. Thus, p divides x^p - x. Which is to say, x^p = x mod p.

A2) For prime p and positive integer x, construct a permutation of a set with x^p - 1 many elements, with x - 1 fixed points, with every other orbit having size p. Thus, p divides (x^p - 1) - (x - 1) = x^p - x. Which is to say, x^p = x mod p.

B) For prime p and integer x co-prime to p, construct a permutation of a set with p many elements, with 1 fixed point, with every other orbit having size ord_p(x) = the smallest e such that x^e = 1 mod p. Thus, ord_p(x) divides p - 1. Which is to say, x^(p - 1) = 1 mod p.

A typical example of an A1 proof is "necklace counting": Take the structure of interest to comprise the cyclic rotation operator on the x^p many strings of length p over an alphabet of size x (equivalently, the shift operator on the x^p many bidirectionally infinite strings over an alphabet of size x which are periodic with period dividing p; equivalently, the shift-and-drop operator on the unidirectionally infinite periodic strings).

A typical example of an A2 proof: Take the structure of interest to comprise the "multiplication by x" operator acting on the integers mod x^p - 1 (equivalently, acting on the rationals of the form n/(x^p - 1), modulo its additive subgroup of integers).

A typical example of a B proof [really, the only example anyone considers]: Take the structure of interest to comprise the "multiplication by x" operator acting on the integers mod p.

Note that in each case, the structure by which we carry out the proof is uniquely determined up to isomorphism (within the category of sets equipped with an endofunction, by the information about the number of orbits of various sizes). Thus, any two proofs of type A1 (or of type A2, or of type B) are in some sense equivalent, though just how natural their equivalence is depends on how natural an isomorphism can be chosen between their differing presentations of isomorphic structures.

That proofs along the lines of A1) or A2) are also closely related to each other is straightforward to see [one can straightforwardly modify the number of fixed points by identifying, removing, or adding some].

Indeed, once we become aware that the multiplicative group of the integers modulo p is cyclic (which of course is a stronger statement than Fermat's little theorem), we can quite naturally relate our archetypal A1 proof to our archetypal A2 proof like so: By interpreting unidirectionally infinite strings over an alphabet of size x as base x representations of numbers, we see that the x^p many such strings which are periodic with period p describe the x^p - 1 many rationals of the form n/(x^p - 1) modulo integers. This mapping gives a homomorphism from the shift operator on the unidirectionally infinite strings, to the multiplication by x operator on the rationals n/(x^p - 1) modulo integers. This homomorphism is surjective and almost injective, except for that it identifies the all zero digit string with the all highest digit string. Thus, we see these two structures are almost the same, except for this identification of two fixed points into one.

An unusual example of an A1 proof would be where we take the structure of interest to be the x^p many solutions in y to y^(x^p) = y in an algebraically closed field where x^p ≠ 1 (this is the condition characterizing there being no repeated roots). By dropping the zero solution and considering only the x^p - 1 many (x^p - 1)th roots of unity, we get an unusual example of an A2 proof. That this is equivalent to our previous example of an A2 proof amounts to the fact that the multiplicative group of these roots of unity is cyclic.

But as far as I can tell, there is no close relationship between A1/A2 proofs and B proofs, except for that these happen to prove the same thing.

In this sense, I say there are precisely two distinct proofs of Fermat's little theorem, as best I am aware.

Incidentally, all of these proofs (A1/A2 and B) generalize easily to showing that x^(p^n) = x mod p^n, and from there we can derive the Euler-Fermat theorem more generally.

The A1 necklace counting proof generalizes to showing that, given any function f : D^p -> M where M is an abelian monoid, such that the sum of f over all p cyclic shifts of an argument vector always vanishes (as happens for example if f is invariant under cyclic shifts of its arguments and its codomain has characteristic p, so to speak), we have that the equivalence relation induced by f on the p-th tensor power of the free abelian monoid on D is such that (a + b + c + …)^p = a^p + b^p + c^p + …. [TODO: Reword this]. Aka, "freshman's dream".

The B proof generalizes to showing that the order of any group element divides the order of the group. More generally, the order of any subgroup divides the order of the group. Aka, Lagrange's theorem.

See also https://twitter.com/RadishHarmers/status/1746692047069704262