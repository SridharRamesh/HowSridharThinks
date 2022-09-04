---
title: "Presheaf Categories Are Toposes"
date: 2022-05-19
---
The category Psh(C) of presheaves on a small category C is a topos (presuming Set itself is one). Why is this? I keep forgetting the cleanest proofs of these facts. I record them here for myself for posterity.

For our purposes here, a topos is a category with finite limits, cartesian closure, and a subobject classifier. Sometimes people add to the definition finite colimits, though this can be deduced already from the former structure by Pare's theorem (that is, from the fact that the self-adjunction of the contravariant powerset endofunctor can be shown to be monadic, thus creating colimits from limits). We can conclude also that all this structure is pullback stable, that pullbacks have right adjoints (thus we have local cartesian closure as well), etc, but nevermind all that.

The question is, why does this structure transfer to presheaf categories? The existence of finite limits in presheaf categories is obvious: these are computed componentwise, as in any functor category whose codomain has such limits. Indeed, in the same way, we see that the category Set^C for any C (whether or not C is small) in fact has componentwise set-sized limits and set-sized colimits (and because these are componentwise, these set-sized colimits will be pullback-stable, disjoint, etc, just as in Set itself). So what we need to see beyond this is why the presheaf categories have exponentials and why they have a subobject classifier.

Both of these occur for the same reason: For small C, using the Yoneda lemma and the fact that each object in Psh(C) is a set-sized colimit of representables, a contravariant functor from Psh(C) to Set is representable just in case it turns set-sized colimits into limits. \[When C is large but locally small, we still have a Yoneda embedding of C into Psh(C), but what goes awry is that Psh(C) is no longer comprised only of set-sized colimits of representables\]

Thus, exponentials exist because any set-sized colimit-preserving functor F out of C has a right adjoint: Hom(F(-), d) will necessarily take set-sized coimits to limits. And we know that for any object p in Psh(C), the functor p x - is set-sized colimit-preserving because this is true componentwise, because of the existence of the existence of exponentials in Set itself.

Similarly, the subobject functor is representable because being a subobject is a limit-definable condition (a map is monic in case its kernel pair is trivial), and thus can be checked componentwise in Psh(C). Thus, subobject functor on Psh(C) turns set-sized colimits into limits, and thus is representable.