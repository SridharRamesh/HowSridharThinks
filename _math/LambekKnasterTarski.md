---
layout: post
title:  "Lambek's lemma, Knaster-Tarski, Adamek"
date: 2019-11-28
---
[TODO: LaTeXify the following]

Let F be an endofunctor and let A : FX -> X be an algebra for that endofunctor. A gives rise to another F-algebra FA : FFX -> FX, and this has a "tautological" F-algebra homomorphism back into A with underlying map A itself (the relevant commutative square is just $$latex A \circ FA = A \circ FA$$).

Now suppose there is some F-algebra homomorphism : A -> FA which is a section of the tautological homomorphism : FA -> A.

Lambek's lemma (although not usually phrased in such generality) tells us that this section is actually an isomorphism; that is, even in the other order of composition, the tautological homomorphism followed by its section comes out to identity.

Why is this? Let $$$$m : X \to F X$$ be the underlying morphism of this section. Then we have $$m \circ A = F(A) \circ F(m) = F(A \circ m) = F(1) = 1$$, establishing the lemma.

In particular, if $$latex A$$ is an initial object in some full subcategory of the F-algebras closed under $$latex F$$, then this category will contain the tautological morphism into $$latex A$$, and also a section for it (as an initial object readily provides a section of every map into it), allowing us to apply this lemma to conclude that $$latex A$$ is in fact an isomorphism.

This is closer to the way Lambek's lemma is usually presented (while still general enough for our purposes below!).

Of course, just as well dually, we find that a terminal coalgebra for any full subcategory of F-coalgebras closed under F must also be an isomorphism.

--

Note that F-algebras and F-coalgebras comprise a category together. For any diagram of F-algebras, if its forgetful functor has a limit, then its inclusion functor into the diagram of F-algebras and F-coalgebras also has a limit, and the former limit is the forgetful functor applied to the latter limit. And dually of course for colimits of coalgebras.

We can consider the notion of an F-algebra-initial F-coalgebra: those F-coalgebras with unique homomorphisms into each F-algebra. This class is closed under the natural action of F and under colimits within the category of coalgebras together with algebras (insofar as the colimits exist).

By Lambek's lemma above, an initial algebra is the same thing as a terminal algebra-initial coalgebra (since any terminal such coalgebra will have to be an isomorphism). This will exist just in case the forgetful functor from algebra-initial coalgebras into the underlying category has a colimit (because then this colimit must itself comprise a colimit within the algebra-initial coalgebras, and thus be a total colimit, which is to say, terminal; see https://howsridharthinks.wordpress.com/2019/11/17/total-limits-are-empty-colimits/).

This is the bottoms up approach to the initial algebra given by Knaster-Tarski.

The top down approach to the initial algebra given by Knaster-Tarski is more straightforward, but less computational: the initial object for the F-algebras is their total limit [again by https://howsridharthinks.wordpress.com/2019/11/17/total-limits-are-empty-colimits/ ].

The bottoms up approach is usually done using not the full subcategory of all algebra-initial coalgebras, but rather, a particular ordinal-indexed diagram of them. This is what is called Adamek's construction. It goes like so:

Consider the free category with an endofunctor and all colimits. This is the category of ordinals. (There are "size issues" involved in this definition, but so it goes. Specifically, it is paradoxical in the Burali-Forti way; it is a preorder both with and without a maximal object, as we can prove that the endofunctor satisfies f(x) > x for all x, but the colimit of everyone will be a maximal object [an instance of https://howsridharthinks.wordpress.com/2019/11/17/total-limits-are-empty-colimits/ ]. We can make this category non-paradoxical by only going up to some ordinal; the free category with an endofunctor and all colimits of a certain length.).

Thus, there is a unique cocontinuous map from ordinals into these F-algebra-initial coalgebras, on which the successor action is that of F. The colimit of this entire diagram should exist within this diagram (as the class all ordinals should itself be an ordinal), and thus will be [by https://howsridharthinks.wordpress.com/2019/11/17/total-limits-are-empty-colimits/ ] a terminal algebra-initial coalgebra, which will have to be an isomorphism by Lambek's lemma, and thus will be an initial algebra.

[This last step relies on the paradoxical reasoning that there is an ordinal which is the colimit of all ordinals. We can be more rigorous in this regard, and say simply that we get an ordinal-indexed chain of algebra-initial-coalgebras, extending as far as we are able to take colimits, and if at any point the coalgebra structure becomes an isomorphism, it at that point becomes an initial algebra. Beyond such a point, the chain can automatically be continued with isomorphisms (which might as well be taken to be identity) for all further maps, through all remaining ordinals.

Indeed, if this chain contains an isomorphism between stages $$latex \alpha$$ and $$latex \beta$$ for any $$latex \beta > \alpha$$, then it already stabilizes at stage $$latex \alpha$$. For, letting $$latex s$$ be the coalgebra map from $$latex \alpha$$ to $$latex \alpha + 1$$, which is also the tauutological coalgebra map for $$latex \alpha$$, the isomorphism establishes that $$latex s$$ can be followed by a coalgebra map resulting in identity. By the first form of Lambek's lemma we gave above (a tautological algebra map has a section just in case it is an isomorphism), this means that $$latex s$$ is an isomorphism, which is to say, the chain stabilizes at stage $$latex \alpha$$.

We can thus conclude that this chain has to stop producing new coalgebras at SOME point, like so: By the previous paragraph, we know that prior to the chain stabilizing, its values at any two distinct ordinals are non-isomorphic (TODO: Actually, we don't know this! We only know that the map within the chain is not itself an isomorphism). But a "small" category has only a "small" cardinality of non-isomorphic coalgebras within it, so this process cannot iterate productively all the way up through the first "small" ordinal exceeding that cardinality. It must stop before then either through a colimit failing to exist or through stabilizing at an initial algebra.]

[For an if-and-only-if statement, we can say that there is an initial algebra iff there is an algebra which is also an algebra-initial coalgebra iff there is a terminal algebra-initial coalgebra iff there is a subcategory of the algebra-initial coalgebras which is closed under F and contains its total colimit (i.e., has a terminal object).]

[TODO: Relate Knaster-Tarski proved from below by Adamek to the Banach and Caristi fixed point theorems. Perhaps this involves thinking about Cauchy completeness of categories?]