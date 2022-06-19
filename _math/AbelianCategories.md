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
3. The finite products and finite coproducts are in fact biproducts.
    1. The map from the initial object to the terminal object is an isomorphism.
        1. Any parallel maps into the initial object are equal.
        2. Any parallel maps out of the terminal object are equal.
    2. The map from A + B to A x B given by (TODO) is an isomorphism.
4. Every object has a negation endomorphism (TODO).

All of these conditions are manifestly self-dual.

Clearly 1 is equivalent to 1.1 + 1.2, while 1.1 is equivalent to 1.1.1 + 1.1.2.

Condition 2 is called being a "balanced category". The combination of 1 and 2 entails, among other things, the structure of an effective regular category whose dual is also effective regular. Given the structure of 1 alone, any morphism canonically decomposes into the coequalizer of its kernel pair, followed by a monic-epic, followed by the equalizer of its cokernel pair. 2 is then the demand that the middle monic-epic be an isomorphism, giving us the usual image factorization. (TODO: I think this is all correct, but I should check on how this interacts with the pullback stability condition in the definition of a regular category, and also on how the definition of a regular category may not entail being balanced because epics need not be regular epic.)

Condition 3 is straightforwardly equivalent to 3.1 + 3.2, in the usual way that we get results for arbitrary finite arity from arities 0 and 2.

For interpreting condition 3.1, note that we have a unique map from the initial object to the terminal object (granted both by the terminality property, and also separately by the initiality property). In the context of 1.1.1 and 2, we have that 3.1 is equivalent to 3.1.1 + 3.1.2, since 3.1.1 says this map is monic, and 3.1.2 says this map is epic. 

Note that Set satisfies 1, 2, and 3.1.1, but does not satisfy 3.1.2, and thus does not satisfy 3.1. We cannot even interpret 3.2 and 4 in Set, since 3.2 depends on 3.1 to be interpreted, and 4 depends on 3 to be interpreted.

In the context of 1.1.1, condition 3.1 is equivalent to having "zero morphisms"; that is, being enriched over pointed sets.

In the context of 1.1, condition 3 is equivalent to being enriched multilinearly over abelian monoids. Adding in condition 4 then makes these abelian monoids into abelian groups.

The conjunction of all these conditions is the definition of an abelian category. Thus, a balanced category with finite biproducts, equalizers, coequalizers, and negation.