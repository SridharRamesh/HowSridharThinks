---
title: "Lambek's lemma, Knaster-Tarski, Adamek"
date: 2019-11-28
---
Let $$F$$ be an endofunctor and let $$A : FX \to X$$ be an algebra for that endofunctor. $$A$$ gives rise to another F-algebra $$FA : FFX \to FX$$, and this has a "tautological" F-algebra homomorphism back into $$A$$ with underlying map $$A$$ itself (the relevant commutative square is just $$A \circ FA = A \circ FA$$).

Now suppose there is some F-algebra homomorphism $$: A \to FA$$ which is a section of the tautological homomorphism $$: FA \to A$$.

Lambek's lemma (although not usually phrased in such generality) tells us that this section is actually an isomorphism; that is, even in the other order of composition, the tautological homomorphism followed by its section comes out to identity.

Why is this? Let $$m : X \to F X$$ be the underlying morphism of this section. Then we have $$m \circ A = F(A) \circ F(m) = F(A \circ m) = F(1) = 1$$, establishing the lemma.

In particular, if $$A$$ is an initial object in some full subcategory of the F-algebras closed under $$F$$, then this category will contain the tautological morphism into $$A$$, and also a section for it (as an initial object readily provides a section of every map into it), allowing us to apply this lemma to conclude that $$A$$ is in fact an isomorphism.

This is closer to the way Lambek's lemma is usually presented (while still general enough for our purposes below!).

Of course, just as well dually, we find that a terminal coalgebra for any full subcategory of F-coalgebras closed under F must also be an isomorphism.

***

Note that F-algebras and F-coalgebras comprise a category together (the morphisms from coalgebras to algebras being ["hylomorphisms"](@/Hylomorphism.md)). Also, for any diagram of F-algebras, if its forgetful functor has a limit, then its inclusion functor into the category of F-algebras and F-coalgebras also has a limit, and the former limit is the forgetful functor applied to the latter limit. And dually of course for colimits of coalgebras.

We can consider the notion of an F-algebra-initial F-coalgebra: those F-coalgebras with unique homomorphisms into each F-algebra. This class is closed under the natural action of F (as a special case of the ["rolling rule"](@/Hylomorphism.md)) and under colimits within the category of coalgebras together with algebras (insofar as the colimits exist).

\[Apparently, many use the term "recursive coalegbra" rather than "algebra-initial coalgebra" here. Or in the same way, they speak of "corecursive algebra" rather than "coalgebra-terminal algebra".\]

By Lambek's lemma above, an initial algebra is the same thing as a terminal algebra-initial coalgebra (since any terminal such coalgebra will have to be an isomorphism). A sufficient (though not necessary) condition for this to exist is for the forgetful functor from algebra-initial coalgebras into the underlying category to have a colimit (because then this colimit must itself comprise a colimit within the algebra-initial coalgebras, and thus be a total colimit, which is to say, terminal; see ["Total Limits Are Empty Colimits"](@/TotalLimits.md)).

This is the bottoms up approach to the initial algebra given by Knaster-Tarski.

The top down approach to the initial algebra given by Knaster-Tarski is more straightforward, but less computational: the initial object for the F-algebras is their total limit \[again by ["Total Limits Are Empty Colimits"](@/TotalLimits.md)\]. And again, if the forgetful functor from the the F-algebras to the underlying category has a limit, then it creates a corresponding limit in the F-algebras (and indeed, in the category of algebras together with coalgebras), giving us the desired object.

The bottoms up approach doesn't actually require us to use the full subcategory of all algebra-initial coalgebras. In general, suppose we want to find a coalgebra which satisfies some specialness property preserved by applying F and by some special kind of colimits, and which also happens to be an isomorphism. It suffices to find some subcategory of special coalgebras which is closed under the tautological maps and which contains a total colimit. In particular, we can inductively build a subcategory of special coalgebras closed under the tautological maps, and closed under special colimits, and hope it happens to contain a total colimit (this will work just in case the object we wish to build is "well-founded" in some sense).

For the purposes of building a initial algebra this way, the specialness property for coalgebras is being algebra-initial, and a suitably special kind of colimit preserving this property is one induced from colimits in the underlying category. So we can consider the full subcategory of coalgebras inductively buildable via tautological maps and all colimits induced from the underlying category that happen to exist. (This is sort of like the cumulative hierarchy, which is inductively built from singleton and union operators, except instead of just union, we have all kinds of non-posetal colimits in play as well)

We can be even more narrow than this. No one is forcing us to use a full subcategory. We can inductively build a subcategory of coalgebras buildable via tautological maps and very particular colimits induced from the underlying category. We can think of the stages of this construction as indexed by ordinals. At successor ordinal stages, we add in F(the last coalgebra we added) and the tautological map between them. At limit ordinal stages, we add in a colimit for everything produced in previous stages.

At every point, there will be a unique map from coalgebras at lower stages to coalgebras to higher stages ...except it may at some point be that the next new coalgebra we add is isomorphic to a coalgebra already included at some lower stage (perhaps isomorphic via the map we've added between those two stages, but perhaps isomorphic in some completely different way). That's alright, this doesn't matter. If this ever happens, though, to keep things actually a subcategory per se (which we wish to do for size reasons I'll explain in a second), we must choose an arbitrary such isomorphism and add it in as well, identifying the coalgebras at those two stages.

(Incidentally, if two different stages happen to be not accidentally isomorphic but isomorphic through the ordinary morphisms of our diagram itself, then there's no problem, the coalgebra of such a stage is already an isomorphism and thus the terminal object we're looking for. For having stage $$\alpha$$ be isomorphic in this way to some later stage means that the tautological map on stage $$\alpha$$ is followed by a coalgebra map resulting in identity, which by our initial version of Lambek's lemma means that the tautological map was itself an isomorphism. So it's only isomorphic coalgebras at different stages whose isomorphisms don't arise in this natural way which should bother us.)

This ordinal-indexed bottoms-up approach is called Adamek's construction, although people usually do not do it paying such attention to the last detail about accidental isomorphisms (instead, they cross their fingers and hope for F to preserve the big colimit in the end, making things work out anyway).

Basically, the free category with an endofunctor and directed colimits is the poset of all ordinals, and we could map it into our underlying category in a directed colimit-preserving way (to the extent the colimits exist) such that successor becomes F. The result's image is almost a subcategory of our category, but there may be accidentally isomorphic objects at different stages, which isn't allowed for a subcategory as such. So we modify the construction along the way to take care of this as well (though this has the effect that now, some of the colimits we take may not be directed colimits as such, because they have parallel morphisms in the diagram).

Zorn's lemma then tells us that we can get a maximal such subcategory of the algebra-initial coalgebras; some subcategory which is closed under tautological maps and these colimits-of-everything-so-far insofar as they exist, and thus whose only obstacle to having a terminal object could be the failure of such a colimit to exist. If said colimit exists, then we get a terminal object within this category, which will be an initial algebra.

The reason we had to restrict ourselves to using subcategories (i.e., diagrams D on some domain such that whenever D(x) and D(y) are isomorphic, x and y were already equal or at least isomorphic objects in the domain) is for formal issues around "size" and the antinomies that can arise in naively invoking Zorn's lemma (consider how it would be paradoxical to use Zorn's lemma to produce a maximal ordinal; the Burali-Forti paradox). We might wish to apply Zorn's lemma to the collection of _all_ well-ordered diagrams into our category, but in standard set theories, there is no such collection; there is a large collection of small well-ordered diagrams, and a superlarge collection of large well-ordered diagrams, and so on, but no one collection of all well-orderings including those it itself "impredicatively" introduces. However, standard set theory _does_ allow us to consider the collection of all subcategories of a given category, so we can apply Zorn's lemma to that poset without problem.

We COULD use an inductively built non-subcategory diagram as well, closed under tautological maps and colimits, without bothering to toss in any "accidental isomorphisms". In some sense, this is the most natural thing to do. In this case, the diagram has shape corresponding to all ordinals. This is "paradoxically large", so we cannot actually conclude this diagram has a total colimit (that is, we can only inductively build such a diagram with closure under colimits of shape not defined with reference to this diagram itself); after all, we cannot conclude there is a largest ordinal, equal to its successor. But if we luck out, the ordinal-indexed diagram still stabilizes at some well-defined point; this will happen if the functor F we are dealing with preserves the colimit at some limit ordinal stage. This often follows from arity considerations in the definition of F (e.g., finitary functors will preserve the colimit at $$\omega$$). But I don't know of a guarantee that _every_ functor will stabilize in this way.

[TODO: The ordinal-indexed part of the above ended up becoming a bit of a confusing mess in the rewrite paying attention to subcategory status/accidental isomorphisms. See if this can be cleaned up.]

[TODO: Can these accidental isomorphisms ever actually happen? Construct an example or clean everything up by proving it impossible.]

[TODO: Relate Knaster-Tarski proved from below by Adamek to the Banach and Caristi fixed point theorems. Perhaps this involves thinking about Cauchy completeness of categories?]

***

See also: "On Well-Founded and Recursive Coalgebras" by Adamek et al, and the related work mentioned therein (such as by Paul Taylor). Also "Initial Algebras, Terminal Coalgebras, and the Theory of Fixed Points of Functors" by the same authors.