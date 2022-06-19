---
title: "Abelian Categories"
date: 2022-6-19
---
Here, we give a manifestly self-dual presentation of the concept of abelian categories.

(We previously discussed abelian categories in terms of their relationship to [regular categories](./InternalLogicRegular.html).)

Consider the following properties a category may have:

1. Has finite limits and finite colimits.
    1. Has finite products and finite coproducts.
        1. Has terminal object and initial object.
        2. Has binary products and binary coproducts.
    2. Has equalizers and coequalizers.
2. Every map which is both a monomorphism and an epimorphism is an isomorphism.
    1. Every monic is regular monic.
    2. Every epic is regular epic.
3. The finite products and finite coproducts are in fact biproducts.
    1. The map from the initial object to the terminal object is an isomorphism.
        1. Any parallel maps into the initial object are equal.
        2. Any parallel maps out of the terminal object are equal.
    2. The map from A + B to A x B given by (TODO) is an isomorphism.
4. Every object has a negation endomorphism (TODO).

All of these conditions are manifestly self-dual, except for 2.1 and 2.2 being each others' duals, and 3.1.1 and 3.1.2 being each others' duals.

Clearly 1 is equivalent to 1.1 + 1.2, while 1.1 is equivalent to 1.1.1 + 1.1.2.

Condition 2 is called being a "balanced category". Either of 2.1 or 2.2 entails 2; conversely, in the context of 1, I believe 2 entails both of 2.1 and 2.2 (TODO: Check this).


The combination of 1 and 2 entails, among other things, the structure of an effective regular category (indeed, I believe simply finite limits, coequalizers of congruences, and being balanced entails being an effective regular category). Given the structure of 1 alone, any morphism canonically decomposes into the coequalizer of its kernel pair, followed by a monic-epic, followed by the equalizer of its cokernel pair. 2 is then the demand that the middle monic-epic be an isomorphism, giving us the usual image factorization. (TODO: I think this is all correct, but I should check on how this interacts with the pullback stability condition in the definition of a regular category, and also on how the definition of a regular category may not entail being balanced because epics need not be regular epic.)

Condition 3 is straightforwardly equivalent to 3.1 + 3.2, in the usual way that we get results for arbitrary finite arity from arities 0 and 2.

For interpreting condition 3.1, note that we have a unique map from the initial object to the terminal object (granted both by the terminality property, and also separately by the initiality property). In the context of 1.1.1 and 2, we have that 3.1 is equivalent to 3.1.1 + 3.1.2, since 3.1.1 says this map is monic, and 3.1.2 says this map is epic. 


In the context of 1.1.1, condition 3.1 is equivalent to having "zero morphisms"; that is, being enriched over pointed sets.

In the context of 1.1, condition 3 is equivalent to being enriched multilinearly over abelian monoids (see [nLab](https://ncatlab.org/nlab/show/biproduct#BiproductsImplyEnrichment)). Adding in condition 4 then makes these abelian monoids into abelian groups.

I believe effective regular category structure + zero morphisms already entails that the subobjects of A are a retract of the congruences on A (i.e., subobjects of A x A which satisfy the equivalence relation conditions). Any congruence on A, though of as a subobject of A x A, induces a subobject of A by pulling back along $$\langle identity, zero \rangle : A \to A \times A$$, and conversely, any subobject of A induces a congruence on A by coequalizing against the parallel zero morphism and then taking the kernal pair. (TODO: Show this is a retraction; i.e., the induced endomorphism on subobjects of A is identity). I believe 5 then makes this retraction into a 1 : 1 correspondence. This has something to do with being a Malcev category.

The conjunction of all these conditions is the definition of an abelian category. Thus, an abelian category is a balanced category with finite biproducts, equalizers, coequalizers, and negation.

***

The category of abelian groups is of course the canonical abelian category.

Note that Set satisfies 1, 2, and 3.1.1, but does not satisfy 3.1.2, and thus does not satisfy 3.1. We cannot even interpret 3.2 and 4 in Set, since 3.2 depends on 3.1 to be interpreted, and 4 depends on 3 to be interpreted.

Note that the category of abelian monoids satisfies 1 and 3, but does not satisfy 2 or 4. That it does not satisfy 4 is unsurprising, but that it does not satisfy 2 is very worthy of note! Consider the inclusion from N into Z. This is both monic and epic, but not an isomorphism. I believe the category of abelian monoids (as with any category monadic over Set) satisfies 2.1; however, it does not satisfy 2.2.

***

1.597 and also 1.598 of Categories, Allegories by Freyd and Scedrov suggest that simply having finite limits and colimits with all monics and epics being regular, plus having the initial and terminal object coincide (thus, 1, 2.1 + 2.2, and 3.1), is enough to ensure being an abelian category? Essentially, if we consider the cokernel of the diagonal map from A into A x A, we find that A maps into this cokernel both monically and epically, and thus this cokernel is isomorphic to A. This essentially means A is the same as the Grothendieck group on A. So we get a subtraction operation for free. From this we also get negation (since we have zero already), and thus we get addition as well (now that we have subtraction and negation). So we are enriched over abelian monoids with negation, which gives us 3.2 and 4.