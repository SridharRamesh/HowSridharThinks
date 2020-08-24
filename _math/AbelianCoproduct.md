---
title:  "Coproducts of Abelian Monoids"
date: 2020-2-1
---
Two classic facts are:

1. For symmetric (aka commutative, or abelian, or whatever term you like) monoids, finitary coproducts and finitary products coincide (thus, the underlying set of the finitary coproduct is the Cartesian product of the underlying sets of the individual monoids), but this correspondence does not hold infinitarily. *[This is often phrased as the finitary coincidence and infinitary distinction between "free" and "direct" products.]*

2. For commutative associative algebras with unit over a semiring R [henceforth, "symmetric R-monoids"], the underlying R-module of a finitary coproduct is the tensor product of the underlying R-modules of the individual symmetric R-monoids, but this correspondence does not hold infinitarily.

These (or at least, the observations about underlying structures, ignoring the further observation of being a categorical product in the first case) are both instances of the same very general fact: Coproducts of symmetric monoids enriched over a symmetric monoidal category have, as their underlying object, the tensor product of the individual monoids' underlying objects.

Specifically, a monoid enriched over a symmetric monoidal category is an object $$M$$ in that category, along with maps $$M \otimes M \otimes \ldots \to M$$ satisfying the obvious properties.

Given finitely many monoids $$M_1, M_2, \ldots$$ [in usual abuse of language, I'm naming just the underlying objects of the monoids here], we can combine them into a new monoid with underlying object $$M_1 \otimes M_2 \otimes \ldots$$, where the multiplication maps $$(M_1 \otimes M_2 \otimes \ldots) \otimes (M_1 \otimes M_2 \otimes \ldots ) \otimes \ldots \to M_1 \otimes M_2 \otimes \ldots$$ are given by using the symmetry of the tensor product to rewrite the domain as $$(M_1 \otimes M_1 \otimes \ldots) \otimes (M_2 \otimes M_2 \otimes \ldots) \otimes \ldots$$ (preserving the ordering of $$M_i$$ factors for any fixed $$i$$), and then applying the monoid multiplication on each top-level factor to bring this down into $$M_1 \otimes M_2 \otimes \ldots$$.

There's a notion of homomorphism between such monoids, which is a morphism between their underlying object making the appropriate diagrams commute.

There's also a notion of when such monoids are symmetric (aka, commutative, abelian, etc), which of course just means that the multiplication morphisms are invariant under first permuting arguments using the symmetry of the tensor product.

And we can observe that the above construction of the monoid $$M_1 \otimes M_2 \otimes \ldots$$ is symmetric whenever each factor monoid is symmetric.

We can then observe that, within the category of symmetric monoids, this construction yields the coproduct, by noting that given homomorphisms $$\{f_i : M_i \to N\}_i$$, we can take the tensor product of all the $$f_i$$ to get a morphism from the object $$M_1 \otimes M_2 \otimes \ldots$$ to $$N \otimes N \otimes \ldots$$; we can then postcompose the multiplication on $$N$$ to turn the codomain into $$N$$ simpliciter, and this result is a homomorphism between the relevant monoids. Conversely, we have injections from each $$M_i$$ into $$M_1 \otimes M_2 \otimes \ldots$$ by tensoring with the unit maps $$: 1 \to M_j$$ for each other $$M_j$$; this gives us a way take a homomorphism from $$M_1 \otimes M_2 \otimes \ldots$$ to $$N$$, and turn it into homomorphisms from each individual $$M_i$$ to $$N$$. It's straightforward to now verify that these two processes are inverses, establishing the coproduct universal property.

[In less categorical language, we are noting that homomorphisms $$f_1, f_2, \ldots$$ on factor monoids can be combined into $$F(m_1, m_2, \ldots) = f_1(m_1) f_2(m_2) \ldots$$ on the tensor product monoid, and conversely, given an arbitrary homomorphism $$F$$ defined on the tensor product monoid, we have the decomposition $$F(m_1, m_2, \ldots) = F(m_1, 1, \ldots) \cdot F(1, m_2, \ldots) \cdot \ldots$$, with these two processes inverse to each other].

Note that this correspondence fails infinitarily because monoids do not have in their definition an infinite product, to force an equation $$F(m_1, m_2, \ldots) = F(m_1, 1, \ldots) \cdot F(1, m_2, \ldots) \cdot \ldots$$ in the infinitary case.

***

Incidentally, observe this bonus fact: Our general theorem dualizes to tell us that products of symmetric comonoids enriched over a symmetric monoidal category also have underlying objects which are tensor products. A special case of this is the dual of our second fact above: in the context of modules over semirings, this tells us that coalgebras correspond to tensor product as well.