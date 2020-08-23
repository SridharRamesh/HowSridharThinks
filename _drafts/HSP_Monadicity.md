---
layout: post
title:  "Birkhoff’s HSP Theorem and Beck’s Monadicity Theorem"
date: 2020-1-18
---
This is all TODO notes for a post not yet actually written, but scratch thoughts I want to keep archived for myself to write with.

Let’s start with just the SP theorem, naively without size considerations. In categorical terms, this essentially states that if a category has arbitrary limits, then it can be seen as arising from a limit theory (and vice versa, though the vice versa direction is trivial).

[TODO: Explain how S is substructure (not necessarily just equalizer substructure, but that’s ok, equalizer substructure is all we’ll need), P is products, and the two of these together give limits. H is quotients (not necessarily just U-split coequalizers, but that’s ok, U-split coequalizers is all we’ll need).]

[TODO: Observe that the representable covariant functors into Set on a category T with all limits are precisely those which are limit-preserving, by taking such a functor’s category of elements/Grothendieck construction, considering this as a diagram into T, and taking its limit, to get the representing element. (Note that a special case of this is when T is a presheaf category, in which case we can also give an easier argument for the same result, based on the Yoneda lemma and the fact that presheaf categories are free cocompletions.). Specifically, if the category has all limits and the functor to Set is limit-preserving, then I think the category of elements will have all limits as well, and thus an absolute initial object. To have an initial object in the category of elements is precisely what it means for a functor to be representable. Indeed, https://math.stackexchange.com/questions/3065521/the-forgetful-functor-from-a-category-of-elements-strictly-creates-limits-and-co confirms that a category of element’s forgetful functor creates all limits preserved by the Set-valued functor on the base category.]

[TODO: Beware: theories embed into their categories of models CONTRAVARIANTLY!]

[TODO: Observe that limits of functors can be constructed pointwise (when the pointwise limits exist, of course), and that limit-preserving functors are closed under such limits. (N.B.: Regular functors out of regular categories are NOT closed under limits)]

[TODO: Explain how to recover not just the categories of models, but their concrete realizations as structures over Set]

[TODO: Explain the correspondence between multisorted Lawvere theories in the sense of categories where objects are product-powers with arity indexed by C, and monads on C; thus, product-theories are the same as monadic theories.]

[TODO: Explain how HSP theorem is Beck’s Monadicity Theorem]

[TODO: Generalize for multisorted Lawvere theories with relations / Pi_1 theories with relations, to whatever generalization of monads is necessary]

[TODO: Put this in comparison with the limit theory result, by observing that what we are doing is taking the big limit theory as a category and finding a suitable Lawvere sub-category that generates the whole thing in the appropriate way, with the appropriate lifting property with respect to maps in the whole thing. This should be the same general plan for dealing with quasivariety theories, etc. Once we start dealing with Pi_2 theories and regular categories or whatever, then we need our big category to be not just a limit category but a regular category, and the plan may shift a bit.]

[TODO: Put in size considerations, both in bringing us down from naive to small/set-sized arity, and also in dealing with questions of when we have finite arity. These are the “bounded” and “finitary” considerations, in terminology of https://ncatlab.org/nlab/show/algebraic+category. Monadic has to do with product theories as noted above. I believe the terminology of “algebraic” on the linked nLab page isn’t quite about limit theories in full generality, but rather, about theories with horn clause axioms, but no partial operators (thus, the theory of cancellative monoids is algebraic in this sense, but not the theory of categories); this is also what is called there a “quasivariety”. Consider also the 1-arity case of theories just given by categories simpliciter.]

[TODO: Possibly consider the size considerations of being not just finite language, but also, finite axiomatization?]

[TODO: Consider whether this generalizes to capturing the observation about Pi_2 theories being precisely those whose categories of models are closed under directed colimits (in the concrete sense; the colimits inherited from structures over Set)?]

[TODO: Note that the moment we know a theory is a full subcategory of the category of structures (over a particular language), closed under arbitrary limits, then it is in fact a reflective subcategory (by the adjoint functor theorem, with naivete about size)]

[TODO: Keep in mind, the category of structures over a particular language is the category of appropriate-arity-product-and-whatever preserving functors from some C to Set; that is, the category of models for some extremely plain theory. When we speak of a class of structures, we mean a full subcategory of this category. This is the way to translate all these results as phrased categorically, into the traditional context.]