---
title: "Galois Theory 101"
date: 2026-04-06
---
Though generally presented as specific to the context of fields, Galois theory can be formulated much more abstractly (which generally helps me understand things better, removing the irrelevant details, at least until just the moment when they are relevant). My eyes in this regard were first opened by reading "An invitation to model-theoretic Galois theory" by Alice Medvedev and Ramin Takloo-Bighash, based on work by Bruno Poizat. But I have an easier time thinking about it even more abstractly, shorn of the specific model-theoretic context of first-order theories, etc.

The starting category-theoretic/order-theoretic observation is this: Suppose given a binary relation on sets X and Y. This induces a contravariant adjunction (i.e., a Galois connection) between the powerset of X and the powerset of Y, in which each set is sent to to the set of its common relatives, so to speak (that is, for relation R, each subset S of X is sent to the set {y in Y | R(x, y) for all x in S}, and symmetrically for sending subsets of Y to subsets of X). This adjunction is contravariant in the direction that, letting F : X -> Y and G : Y -> X be the two contravariant functors so defined between the powersets of X and Y, we get both x ≤ GF(x) and y ≤ FG(y). As with any adjunction, this then restricts to an equivalence between the fixed points of the adjunction (or rather, an order-reversing equivalence, in this contravariant case). In the order-theoretic context, these fixed points are specifically the range of F and G (noting that F ≤ FGF ≤ F by the triangle identity, and thus the range of F is the same as the fixed points of FG, and symmetrically for the range of G being equivalent to the fixed points of GF).

Now specialize to the case where Y is a subgroup of Aut(X) (the bijections of X), and the binary relation is that y fixes x; i.e., y(x) = x. In this case, every value in the range of F : P(X) -> P(Y) is a subgroup of Y.

Given an indexing set K, let us say a subset Z of X^K (i.e., a set of K-tuples) is "coded" if the set of g permuting Z (when acting on it in the obvious way) is in the range of F (equivalently, there is some subset S of X such that, for each g, Z equals its image under g iff g fixes each element of S).

Say also that a subset B of X is a "basis" if GF(B) = X (equivalently, F(B) = {id}; equivalently, elements of Y are fully determined by what they do on B).

Suppose Gr is a subgroup of Y. We can take K = B for any basis B of X and consider the subset of X^K = X^B consisting of actions of elements of Gr. Observe that the set of g permuting this X^K is precisely Gr; thus, this X^K is "coded" just in case Gr is in the range of F.

In particular, if every finite subset of X^K with a finite indexing set K is "coded", and X has a finite basis, and Y is finite (in the context where X has a finite basis, this is equivalent to each element of the basis having a finite orbit under Y), then the range of F comprises all subgroups of Y.

Now consider the context where X is a field, and Y is some group of field automorphisms of X. In this case, every finite subset of X^K with a finite indexing set K is "coded". Why is this? We can code {(a_1, a_2, ..., ), (b_1, b_2, ...), ...} by the polynomial (z - a_1 x_1 - a_2 x_2 - ...)(z - b_1 x_2 - b_2 x_2 - ...)... in the polynomial ring $$X[z, x_1, x_2, ...]$$ (i.e., we can use elementary symmetric polynomials). That this accomplishes the desired coding amounts to that we have a unique such factorization of this polynomial (i.e., this is an injection from K-tuples of size n to polynomials). This follows from that $$X[z, x_1, x_2, ...]$$ is an integral domain and each value (z - a_1 x_1 - a_2 x_2 - ...) is a prime element within it (to see that it is a prime element, note that quotienting by this yields a ring isomorphic to $$X[x_1, x_2, ...]$$, which is itself an integral domain).

If we furthermore suppose that X is a finite algebraic extension of some subfield X' which is fixed by all of Y, then X has a finite basis each of whose elements has a finite orbit under Y. Thus, the range of F is all subgroups of Y.

Let us now suppose Y = Gal(X/X') comprises ALL field automorphisms of X fixing X'. Under what conditions is the range of G all subfields of X?

Well, for one thing, to even have the base field X' in the range of G, we need that every element of X which is algebraic over X' has a minimal polynomial over X' which splits into distinct linear factors over X (that is, the algebraic part of the extension is normal and separable). Why is that? Let x be an element of X algebraic over X'. By algebraicity, its orbit in X is a finite set; this finite set is coded by a polynomial with distinct linear factors. Every element of Y fixes this finite set, which means the coefficients of this polynomial lie in the field fixed by all of Y. If the field fixed by all of Y is X' itself (that is, if X' is in the range of G), these coefficients thus lie in X'.

Conversely, suppose X is an algebraic extension normal and separable over X'. It will also be normal and separable over any intermediate extension (TODO), and so to show that every intermediate field is in the range of G, it suffices to show this fact for X' itself. Let x be some value in X outside of X'; by normality and separability, there is some x2 in X outside of x' with the same minimal polynomial as x over X'; thus, there will be an isomorphism between X'(x) \[i.e., the field generated by X' and x\] and X'(x2) fixing X'. This extends to an automorphism of all of X (indeed, of all of the algebraic closure of X) by the homogenity of X (as a normal separable extension), which completes our proof. Note that this homogenity fact (an instance of homogenity of Fraisse limits in general) depends in general on the Axiom of Choice; however, for finite extensions, we only require finitely many choices, so there is no difficulty.

Putting this all together, for finite normal separable extensions, we get the range of G is all subfields and the range of F is all subgroups, the fundamental theorem of Galois theory.

----

TODO: Clean up.

Relate degree of extensions defined in terms of orbit sizes to degree defined in terms of dimensions of vector spaces. This is as they both multiply in the same way, and for simple extensions where we augment a field with one element of degree n, they both come to n.

Link to post on cyclic extensions.