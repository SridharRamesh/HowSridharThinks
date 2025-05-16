---
title: "Commas"
date: 2022-9-4
---
Various random facts about comma categories I wished to record somewhere:

***

The Comma-Kan lemma from my thesis: TODO

The Comma-Kan lemma decomposes as the result of some fact about products and some fact about inserters (from which comma objects can be constructed), at least in a context where we have products and inserters (perhaps this then extends to arbitrary contexts by embedding C into Cat^{C^{op}} or some such thing). We also have the corresponding fact about equifiers. See for example much of the discussion about inserters and equifiers at https://mathoverflow.net/questions/352902/conceptual-reason-that-monadic-functors-create-limits. Note that functor categories, i.e. powers, i.e. cotensors, can themselves be built up out of products, inserters, and equifiers (see 4.1.6 at http://www.math.uchicago.edu/~may/IMA/Incoming/Lack/lack.pdf).

***

Exponentials in comma categories: TODO (perhaps this can be understood by thinking about exponentials in inserters, and perhaps we should also separately think about equifiers).

Or perhaps this really is very specific to comma categories of the form (id, gamma) where id acts on a ccc with pullbacks and gamma is a finite product functor. See 4.10.3 in Categories for Types by Crore for the construction of exponentials here.

But it shouldn't be quite so specific, because there should be some similarity to the construction of exponentials in presheaf categories. See also 2.12 at http://www.tac.mta.ca/tac/volumes/23/3/23-03.pdf, noted also at https://ncatlab.org/nlab/show/cartesian+closed+category#exponentials_of_cartesian_closed_categories and https://ncatlab.org/nlab/show/closed+monoidal+category#functor_categories.

Or perhaps the useful thing is relating this kind of gluing to an Eilenberg-Moore category for a comonad, as at https://ncatlab.org/nlab/show/Artin+gluing?

***

Subobject classifiers in comma categories: TODO (perhaps this can be understood by thinking about subobject classifiers in inserters, and perhaps we should also separately think about equifiers).

***

The following argument establishes that if $C \rightarrow C'$ is the free extension of a category with finite products C into a cartesian closed category C', then this $C \rightarrow C'$ is a full and faithful functor. Many similar facts can be established in the same way. This is by following Theorem 4.10.7 in Categories for Types by Crole:

The map C → C' induces also a map C' → Psh(C) (its profunctor right adjoint; this will be product-preserving, though not exponential-preserving). Note that this is different from the ccc map C' → Psh(C) which exists by the universal property of C'. Whenever we write C' → Psh(C), we mean the profunctor right adjoint to C → C', not the ccc map.

This gives us a comma category K = (Psh(C), C' → Psh(C)) \[this is like scones of C', but we replace the role of single sets (and the single set of global points) by families of sets as probed by each domain of definition drawn from C\]. On general comma category grounds, this K is ccc, the projection K → Psh(C) preserves finite products (though NOT exponentials!), and the projection K → C' is a ccc functor.

From the universal property of K as a comma category (indeed, a comma object even within the 2-category of categories with finite products), and the straightforward natural transformation from the Yoneda embedding C → Psh(C) to the composite C → C' → Psh(C), we obtain a map C → K such that the composite C → K → Psh(C) is the Yoneda embedding, while the composite C → K → C' matches our original map C → C'. Since C → K → Psh(C) is faithful, we have that C → K must itself be faithful. Furthermore, by considering what the morphisms in K are between objects in the range of C → K, and then applying some Yoneda lemma business, we find that C → K is full \[TODO: expand on this. This is where it's important we use the particular C' → Psh(C) that we used\].

By the universal property of C', the map C → K factors as C → C' → K where C' → K is a ccc functor. Thus, our map C → C' = C → K → C' further factors as C → C' → K → C'. The C' → K → C' are ccc functors, and thus compose to identity on C' by the universal property of C'. It follows that C' → K is faithful. But also C → K = C → C' → K was previously noted to be a full and faithful functor. It follows that C → C' is full and faithful (if a bijection is given by f followed by an injection, then f must itself be bijective).

(Note that the faithfulness of C → C' is obvious anyway, since the faithful Yoneda embedding C → Psh(C) factors through C → C' via the universal property of C'. The fullness is the more sophisticated thing.)

This is a kind of normalization by gluing argument. This same kind of argument also shows that global elements of coproducts or of NNOs in a free ccc with such structure always come uniquely from one of the disjuncts/from a standard numeral. This is by considering again the C' → K → C' decomposition of the identity on C', so that we can analyze homsets in C' via considering the corresponding homsets in K.

(Instead of dealing with a full CCC all at once, we could conceivably deal with just adding a single exponential at a time. This may make the argument easier to internalize?)