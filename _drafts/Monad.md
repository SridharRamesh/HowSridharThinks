---
title: "Assorted facts about monads to write up somewhere"
date: 2021-7-19
----

If a monad has a left adjoint, then this left adjoint is a comonad with the same Kleisli category and same inclusion of the pure category into the Kleisli category. If a monad has a right adjoint, then this right adjoint is a comonad with the same Eilenberg-Moore category and the same forgetful functor out of the Eilenberg-Moore category.
----
More assorted facts about monads: A monoid in the general sense in a 2-category always induces a corresponding monad (monoid in the 2-category of categories), via the appropriate Hom(\*, -) functor. This takes the monoid M with respect to monoidal structure x to the monad M x -. Dually, a comonoid is taken to a comonad, of course.

For any category, the category is equivalent to its category of comonads with respect to Cartesian product.

Morphisms from comonad M to comonad N induce also functors from the category of M-coalgebras to the category of N-coalgebras (whereas with monad algebras, we use the other direction; morphisms from monad N to monad M induce a functor from the M-algebras to the N-algebras. This makes comonads act covariantly and monads act contravariantly in this sense, where this apparent asymmetry is because we are talking about functors as morphisms oriented as though they live inside Cat instead of oriented as in Cat^{op}, which we could perfectly well do.).

The Eilenberg-Moore category for the c x - comonad, when x is Cartesian product, is the slice category over c.

Putting the above all together, in a category C with Cartesian products, we get a covariantly-indexed category where C[c] is the Eilenberg-Moore category for the c x - comonad, equivalently the slice category C/c. If these covariant re-indexings all have right adjoints, we can reread this as a contravariantly-indexed category accordingly; this happens when C has pullbacks, and then this contravariant indexing is the standard self-indexing of C. The Kleisli category for the c x - comonad, on the other hand, is the simple self-indexing (only constant, aka projection, slices, whose pullbacks automatically exist by virtue of product structure).
----
Is the Kleisli category C' for a monad M on C something like the universal map F: C to C' such that there is a natural transformation from FM to F? Is the Eilenberg-Moore category something like the universal map G : C' to C such that there is a natural transformation from MG to G?