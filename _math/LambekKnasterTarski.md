---
layout: post
title:  "Lambek's lemma, Knaster-Tarski, Adamek"
date: 2019-11-28
---
[TODO: LaTeXify the following]

Let $$F$$ be an endofunctor and let $$A : FX \to X$$ be an algebra for that endofunctor. $$A$$ gives rise to another F-algebra $$FA : FFX \to FX$$, and this has a "tautological" F-algebra homomorphism back into $$A$$ with underlying map $$A$$ itself (the relevant commutative square is just $$A \circ FA = A \circ FA$$).

Now suppose there is some F-algebra homomorphism $$: A \to FA$$ which is a section of the tautological homomorphism $$: FA \to A$$.

Lambek's lemma (although not usually phrased in such generality) tells us that this section is actually an isomorphism; that is, even in the other order of composition, the tautological homomorphism followed by its section comes out to identity.

Why is this? Let $$m : X \to F X$$ be the underlying morphism of this section. Then we have $$m \circ A = F(A) \circ F(m) = F(A \circ m) = F(1) = 1$$, establishing the lemma.

In particular, if $$A$$ is an initial object in some full subcategory of the F-algebras closed under $$F$$, then this category will contain the tautological morphism into $$A$$, and also a section for it (as an initial object readily provides a section of every map into it), allowing us to apply this lemma to conclude that $$A$$ is in fact an isomorphism.

This is closer to the way Lambek's lemma is usually presented (while still general enough for our purposes below!).

Of course, just as well dually, we find that a terminal coalgebra for any full subcategory of F-coalgebras closed under F must also be an isomorphism.

--

Note that F-algebras and F-coalgebras comprise a category together. For any diagram of F-algebras, if its forgetful functor has a limit, then its inclusion functor into the diagram of F-algebras and F-coalgebras also has a limit, and the former limit is the forgetful functor applied to the latter limit. And dually of course for colimits of coalgebras.

We can consider the notion of an F-algebra-initial F-coalgebra: those F-coalgebras with unique homomorphisms into each F-algebra. This class is closed under the natural action of F and under colimits within the category of coalgebras together with algebras (insofar as the colimits exist).

By Lambek's lemma above, an initial algebra is the same thing as a terminal algebra-initial coalgebra (since any terminal such coalgebra will have to be an isomorphism). A sufficient (though not necessary) condition for this to exist is for the forgetful functor from algebra-initial coalgebras into the underlying category to have a colimit (because then this colimit must itself comprise a colimit within the algebra-initial coalgebras, and thus be a total colimit, which is to say, terminal; see https://howsridharthinks.wordpress.com/2019/11/17/total-limits-are-empty-colimits/).

This is the bottoms up approach to the initial algebra given by Knaster-Tarski.

The top down approach to the initial algebra given by Knaster-Tarski is more straightforward, but less computational: the initial object for the F-algebras is their total limit [again by https://howsridharthinks.wordpress.com/2019/11/17/total-limits-are-empty-colimits/ ]. And again, if the forgetful functor from the the F-algebras to the underlying category has a limit, then it creates a corresponding limit in the F-algebras (and indeed, in the category of algebras together with coalgebras), giving us the desired object.

The bottoms up approach doesn't actually require us to use the full subcategory of all algebra-initial coalgebras. In general, suppose we want to find a coalgebra which satisfies some specialness property preserved by applying F and by some special kind of colimits, and which also happens to be an isomorphism. It suffices to find some subcategory of special coalgebras which is closed under the tautological maps and which contains a total colimit. In particular, we can inductively build a subcategory of special coalgebras closed under the tautological maps, and closed under special colimits, and hope it happens to contain a total colimit (this will work just in case the object we wish to build is "well-founded" in some sense).

For the purposes of building a initial algebra this way, the specialness property for coalgebras is being algebra-initial, and a suitably special kind of colimit preserving this property is one induced from colimits in the underlying category. So we can consider the full subcategory of coalgebras inductively buildable via tautological maps and all colimits induced from the underlying category that happen to exist. (This is sort of like the cumulative hierarchy, which is inductively built from singleton and union operators, except instead of just union, we have all kinds of non-posetal colimits in play as well)

We can be even more narrow than this. No one is forcing us to use a full subcategory. We can inductively build a subcategory of coalgebras buildable via F and tautological maps and directed colimits induced from the underlying category. We can think of the stages of this construction as indexed by ordinals. At successor ordinal stages, we add in the tautological map for the last coalgebra we added. At limit ordinal stages, we add in a colimit for everything produced in previous stages.

At every point, there will be a unique map from coalgebras at lower stages to coalgebras to higher stages ...except it may at some point be that the next new coalgebra we add is isomorphic to a coalgebra already included at some lower stage (perhaps isomorphic via the map we've added between those two stages, but perhaps isomorphic in some completely different way). That's alright, this doesn't matter. If this ever happens, though, to keep things actually a subcategory per se (which we wish to do for size reasons I'll explain in a second), we must choose an arbitrary such isomorphism and add it in, identifying the coalgebras at those two stages.

This ordinal-indexed bottoms-up approach is called Adamek's construction, although people usually do not do it paying such attention to the last detail about accidental isomorphisms (instead, they cross their fingers and hope for F to preserve the big colimit in the end, making things work out anyway).

Basically, the free category with an endofunctor and directed colimits is the poset of all ordinals, and we could map it into our underlying category a directed colimit-preserving way such that successor becomes F. The result's image is almost a subcategory of our category, but there may be accidentally isomorphic objects at different stages. So we modify the construction along the way to take care of this as well.

Zorn's lemma then tells us that we can get a maximal such subcategory of the algebra-initial coalgebras; some subcategory which is closed under tautological maps and these colimits-of-everything-so-far insofar as they exist, and thus whose only obstacle to having a terminal object could be the failure of such a colimit to exist. If said colimit exists, then we get a terminal object within this category, which will be an initial algebra.

The reason we had to restrict ourselves to using subcategories (i.e., diagrams D on some domain such that whenever D(x) and D(y) are isomorphic, x and y were already equal or at least isomorphic objects in the domain) is for formal issues around "size" and the antinomies that arise in invoking Zorn's lemma. Zorn's lemma only applies to "small" posets (consider how it would be paradoxical to use Zorn's lemma to produce a maximal ordinal; the Burali-Forti paradox). But the collection of ALL diagrams into a category can have unbounded size. However, the collection of subcategories of a "small" category is itself "small", and so we are alright as long as we make sure we are only considering subcategories in this way.

[TODO: The ordinal-indexed part of the above ended up becoming a bit of a confusing mess in the rewrite paying attention to subcategory status/accidental isomorphisms. See if this can be cleaned up.]

[TODO: Relate Knaster-Tarski proved from below by Adamek to the Banach and Caristi fixed point theorems. Perhaps this involves thinking about Cauchy completeness of categories?]