---
title: "Mac Lane \"Parameters\" Theorem"
date: 2020-2-3
---
Suppose given an isomorphism square in Cat; that is, categories A, B, C, and D, functors e : A -> B, f: A -> C, g : B -> D, and h : C -> D, and a natural isomorphism between the two paths from A to D.

Suppose furthermore that e is essentially surjective on objects (i.e., essentially surjective on 0-cells) and h is fully faithful (i.e., essentially surjective on positive-cells).

Then this isomorphism square decomposes as two isomorphism triangles along some diagonal functor : B -> C. \[TODO: Proof\] \[TODO: Speak of to what extent this decomposition is canonical or unique up to higher isomorphism\]

I call this the “Parameters” Theorem because it has as a corollary the result that adjoints which exist pointwise for all objects are automatically further equipped as full-on functors (by taking e to be the inclusion of the set of objects of B, taking D to be a presheaf category so that g amounts to a profunctor, and taking h to be the Yoneda embedding showing that possessing an adjoint at a particular object is property-like), which in turn has as a corollary the result Mac Lane describes in Categories for the Working Mathematician as being about “limits with parameters” (section V.3). Perhaps I should instead call it something like the Pointwise Functor Theorem.

[TODO: Derive, as Mac Lane does, the result that limits in functor categories may be calculated pointwise, presuming the pointwise limits exist]