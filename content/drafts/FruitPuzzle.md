---
title: "Fruit Puzzle"
date: 2025-05-15
---

Consider the fruit puzzle, where we try to solve a/(b + c) + b/(a + c) + c/(a + b) = 4. After moving everything to one side and clearing the denominators, this becomes f(a, b, c) = 0 where f(a, b, c) = a^3 + b^3 + c^3 - 3(a^2 b + a b^2 + a^2 c + a c^2 + b^2 c + b c^2) - 5 a b c.

This will define an elliptic curve, once we know there are no singularities (i.e., f and its gradient are never simultaneously zero except at (a, b, c) = (0, 0, 0)), which further implies irreducibility (i.e., no entire plane is a solution).

In fact, even more strongly, just in itself, the gradient of f is only zero at (a, b, c) = (0, 0, 0). How do we prove this?

There's hopefully a nicer approach but here's the Mickey Mouse algebra approach: We can directly calculate that (d/da - d/db) f(a, b, c) = (6(a + b) - c) (a - b). Of course, we get analogous results for any permutation of {a, b, c}.

Therefore, (a, b, c) is such that all the partial derivatives of f(a, b, c) are equal just in case any two of these values are either equal or have a sum equal to the other value divided by 6.

So either a = b = c, or a + b = c/6, a + c = b/6, b + c = a/6, or (a, b, c) is some permutation of a value of the form (x, x, y) where x + y = x/6.

Tackling these three cases in order:

When (a, b, c) = (x, x, x), the gradient of f(a, b, c) works out to -20(x, x, x).

The system of linear equations a + c = b/6, b + c = a/6, b + c = a/6 has unique solution a = b = c = 0.

If x + y = x/6, then 6y = -5x, so we are looking at (a, b, c) as a multiple of a permutation of (6, 6, -5). The gradient of f(a, b, c) works out here to (39, 39, 39).

So the gradient is never nontrivially zero.

Put another way, the combination of a = 6(b + c) and c = 6(b + a) leads by subtraction to (a - c) = 6(c - a), thus 0 = 7(c - a), thus a = c. So even just two conditions of this sort ensure an equality. We thus have that the gradient is zero only in cases where at least two coordinates are equal. We can readily see that there are only three nontrivial roots, up to symmetry, of this sort for our original f, and none have the gradient being zero.

----

But actually, what we really want is that (a, b, c) and grad f(a, b, c) are never collinear (at non-zero roots of f). I.e., their cross product should never be zero (at non-zero roots of f). How do we ensure this?

By direct calculation, we can see that (a, b, c) crossed with grad f(a, b, c) has its first coordinate as (b - c) * \[Symmetric function of (a, b, c) + nonzero constant times bc\].

(On pure symmetry grounds, we already know that when any two coordinates of (a, b, c) are equal, so are the corresponding two coordinates of grad f(a, b, c), which ensures that the other coordinate in their cross product is zero. This ensures that (b - c) divides the first coordinate of the cross product. The remaining factor will have to be symmetric in b and c and of degree 2; in general, the difference between this and a fully symmetric function of (a, b, c) will be a linear combination of a^2 and of bc. It's a stroke of luck that we don't have an a^2 term here to worry about but do have a bc term to take advantage of.)

It follows that, for all three coordinates of the cross product to be zero, there must be at least two valus among (a, b, c) which are equal. There are essentially three nonzero roots (up to permutation and scaling) of f with this symmetry, readily solved for (one is (1, 1, -1) and the other two are (1, 1, k) for the two solutions k of a particular quadratic equation irreducible over the rationals, thus algebraically indistinguishable), and we can test each of these and see that none result in f cross grad f == 0.

----

Note that (a, b, c) dot grad f(a, b, c) is zero at roots of f, so the only way grad f(a, b, c) could be a multiple of (a, b, c) is to either be zero or for (a, b, c) to be a null vector in the sense of dotting with itself to zero. The latter cannot nontrivially happen over the reals, and so our first proof above works perfectly fine over the reals. But the second proof is better for generalizing to complex numbers.

\[Actually, for any homogenous polynomial f of degree d, we have that (a, b, c) dotted with grad f(a, b, c) is d * f. So, in characteristic not dividing d, it's also the case that wherever the gradient is zero, we are at a root of f. \]

----

A plane containing root (a, b, c) as a double root must also contain a vector non-collinear to (a, b, c) and orthogonal to grad f(a, b, c). The space of vectors orthogonal to grad f(a, b, c) is either (3 - x)-dimensional where x is 0 if grad f(a, b, c) is 0 and 1 otherwise. This space contains (a, b, c) itself, and thus the remaining choice is within a (2 - x)-dimensional space. Thus, the plane is uniquely determined just in case grad f(a, b, c) is nonzero. We've already seen it to be nonzero via either argument above. So even the first argument above establishes that there is a unique plane containing root (a, b, c) as a double root; it just doesn't give a formula for this plane via (a, b, c) cross grad f(a, b, c).

I'm not sure, but I think this cross product will be useful to us as a 1-form in invoking Riemann-Roch (as we use for establishing the desired group structure).

-----

Note that once we know we can generate roots as angles nθ for an irrational θ, while the positive solutions correspond to angles in some nontrivial range, we know a positive solution exists. So we know a positive solution exists once we know any non-torsion root (or rather, a non-torsion root along with a root on the appropriate component of real solutions; the "egg" in the terminology of "An unusual cubic representation problem").

-----

It may be easier to show the gradient is never zero by using the fact that (b, c, a) combines with (c, a, b) to give the same point as should be (a, b, c) combined with itself. I'm not quite sure how to fully formalize this [invoking the associativity proof before we know the gradient is never zero?] but it may be possible.

We can also show the curve is irreducible from the fact the gradient is never zero, since if the curve is divisible by plane P, the remainder of the curve is a degree 2 polynomial on plane P, thus with a simultaneous root in plane P and the rest of the curve (at least, in an algebraic closure), and this simultaneous root would have to be a point where the gradient is zero.

---------

Alternatively, we know that any two distinct points on the curve with gradient zero would define a plane on which the curve vanishes (since they give multiplicity 4 to the curve on this plane). So, once we know the curve is irreducible, there is at most one such point; but then, by symmetry, this point would have to be (1, 1, 1), and this doesn't lie on the curve. \[Or the one nonsingular point would have to be (1, k, k^2) for k a third root of unity more generally; but actually, if this held for any such root of unity, it would also hold for its conjugate, which would be too many nonsingular points unless k is equal to its conjugate, which will force k = 1 (even in a mod 3 field...) \]