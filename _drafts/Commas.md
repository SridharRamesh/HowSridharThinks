---
title: "Commas"
date: 2022-9-4
---
Various random facts about comma categories I wished to record somewhere:

***

The Comma-Kan lemma from my thesis: TODO

***

Exponentials in comma categories: TODO

***

Subobject classifiers in comma categories: TODO

***

The following argument establishes that if $C \rightarrow C'$ is the free extension of a category with finite products C into a cartesian closed category C', then this $C \rightarrow C'$ is a full and faithful functor. Many similar facts can be established in the same way. This is by following Theorem 4.10.7 in Categories for Types by Crole:

The map C → C' induces also a map C' → Psh(C) (its profunctor right adjoint; this will be product-preserving, though not exponential-preserving). Note that this is different from the ccc map C' → Psh(C) which exists by the universal property of C'. Whenever we write C' → Psh(C), we mean the profunctor right adjoint to C → C', not the ccc map.

This gives us a comma category K = (Psh(C), C' → Psh(C)). On general comma category grounds, this K is ccc, the projection K → Psh(C) preserves finite products (though NOT exponentials!), and the projection K → C' is a ccc functor.

From the universal property of K as a comma category (indeed, a comma object even within the 2-category of categories with finite products), and the straightforward natural transformation from the Yoneda embedding C → Psh(C) to the composite C → C' → Psh(C), we obtain a map C → K such that the composite C → K → Psh(C) is the Yoneda embedding, while the composite C → K → C' matches our original map C → C'. Since C → K → Psh(C) is faithful, we have that C → K must itself be faithful. Furthermore, by considering what the morphisms in K are between objects in the range of C → K, and then applying some Yoneda lemma business, we find that C → K is full \[TODO: expand on this. This is where it's important we use the particular C' → Psh(C) that we used\].

By the universal property of C', the map C → K factors as C → C' → K. Thus, our map C → C' = C → K → C' further factors as C → C' → K → C'. The C' → K → C' are ccc functors, and thus compose to identity on C' by the universal property of C'. It follows that C' → K is faithful. But also C → K =  C → C' → K was previously noted to be a full and faithful functor. It follows that C → C' is full and faithful (if a bijection is given by f followed by an injection, then f must itself be bijective).

(Note that the faithfulness of C → C' is obvious anyway, since the faithful Yoneda embedding C → Psh(C) factors through C → C' via the universal property of C'. The fullness is the more sophisticated thing.)

This is a kind of normalization by gluing argument. This same kind of argument also shows that global elements of coproducts or NNOs in a free ccc with such structure always come uniquely from one of the disjuncts/from a standard numeral, etc. This is by considering again the C' → K → C' decomposition of the identity on C', so that we can analyze homsets in C' via considering the corresponding homsets in K.

(Instead of dealing with a full CCC all at once, we could conceivably deal with just adding a single exponential at a time. This may make the argument easier to internalize?)