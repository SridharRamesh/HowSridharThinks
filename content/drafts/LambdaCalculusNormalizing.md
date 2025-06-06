---
title: "The Typed Lambda Calculus Is Normalizing"
date: 2022-7-11
---
UNPOLISHED: Some proofs of some facts about normalization in the typed lambda calculus (terms in the simply typed lambda calculus with products, possibly with NNO as well, are normalizing, or possibly strongly normalizing, with unique normal form):

A) We can use [confluence](@/Confluence.md) with "parallel reduction", to prove the Church-Rosser property. See https://en.wikipedia.org/wiki/Church%E2%80%93Rosser_theorem. It seems Martin-Loef and Tait used this approach? But I wonder how it differs from Church and Rosser's own argument?

B) We can do the following to prove normalization (a categorical account of Tait's method to proven normalization; i.e., the method of "logical relations"):

Consider the comma category (f, g) where f is some arbitrary functor between finite product categories while g is a finite product preserving functor between finite product categories. This comma category is also a finite product category and its two projections preserve these finite products. \[This is a special case of the "Comma-Kan lemma" in the preliminaries of my thesis-in-progress\]

If furthermore f preserves an NNO, and the domain of g has an NNO, we have that the comma category has an NNO as well, with both projections preserving this. This again follows from the "Comma-Kan lemma".

Alternatively, if furthermore f is a logical functor between toposes (or maybe just a lex-and-cartesian functor between CCCs with finite limits?), while the domain of g is a CCC as well, then the comma category has exponentials as well and they are preserved by the second projection, or something like this. I forget the exact details here, how this part goes. Something like this is true. This is the part where I'm fuzzy, constructing exponentials in comma categories. This doesn't follow from the Comma-Kan lemma, alas.

So all together, if the domains and shared codomain of f and g are CCCs with NNO, and f preserves all this structure, while g preserves finite products and NNO, then the comma category (f, g) also has all this structure, and the second projection preserves all of it, I think? Something like that.

So for a ccc T with NNO, we can consider also the comma category (identity on Set, global sections functor on T), which I'll call Scone(T) and it has all this same structure as well.

Now take T to be the initial (i.e., term) model of this structure. Because Scone(T) has all this structure as well, we have a structure preserving map from T to Scone(T). Conversely, Scone(T) has a projection back into T which I think preserves all this structure as well? I forget, I may have gotten wrong how the exponentials are dealt with in comma categories. But if that's true, then T -> Scone(T) -> T preserves all this structure and is the identity, and therefore every global section of the NNO in T is equivalent to one which comes from a global section of the NNO in Scone(T), and those are all sent to standard numerals, completing the proof.

It's possible I've gotten something wrong in here. I need to remember how exponentials in comma categories work.

This is something like normalizing under beta/eta equality. For normalization in a directed way, using only reductions, I forget the details, but this probably can be handled by the Seely (is it Seely?) stuff on ordered cccs. It also follows from our Church-Rosser property above.

This shows weak normalization, but how to show strong normalization?

****

Some further scratch notes I discovered, about the fact that the free cartesian closed category on a category with finite products contains the latter fully and faithfully:

We take a starting category with finite products C, and let C' be the corresponding free CCC. The map C → C' induces also a map C' → Psh(C) (its profunctor right adjoint; this will be product-preserving, though not exponential-preserving). Note that this is different from the ccc map C' → Psh(C) which exists by the universal property of C'. Whenever we write C' → Psh(C), we mean the profunctor right adjoint to C → C', not the ccc map.

This gives us a comma category K = (Psh(C), C' → Psh(C)). On general comma category grounds, this K is ccc, the projection K → Psh(C) preserves finite products (though NOT exponentials!), and the projection K → C' is a ccc functor.

From the universal property of K as a comma category (indeed, a comma object even within the 2-category of categories with finite products), and the straightforward natural transformation from the Yoneda embedding C → Psh(C) to the composite C → C' → Psh(C), we obtain a map C → K such that the composite C → K → Psh(C) is the Yoneda embedding, while the composite C → K → C' matches our original map C → C'. Since C → K → Psh(C) is faithful, we have that C → K must itself be faithful. Furthermore, by considering what the morphisms in K are between objects in the range of C → K, and then applying some Yoneda lemma business, we find that C → K must be full [TODO: expand on this. This is where it's important we use the particular C' → Psh(C) that we used].

By the universal property of C', the map C → K factors as C → C' → K. Thus, our map C → C' = C → K → C' further factors as C → C' → K → C'. The C' → K → C' are ccc functors, and thus compose to identity on C' by the universal property of C'. It follows that C' → K is faithful. But also C → K = C → C' → K was previously noted to be a full and faithful functor. It follows that C → C' is full and faithful (if a bijection is given by f followed by an injection, then f must itself be bijective).

****

To write up:

Comma category exponentials
Comma category subobject classifier
Comma category general representation theorem?
Representability for subcategories of presheaf categories
The above full faithfulness theorem for CFP -> lambda calculus