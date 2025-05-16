---
title: "The Yoneda Lemma"
date: 2021-1-26
---
The Yoneda Lemma is considered one of the most important observations of category theory. Well, I don't know who decides what things are to be considered important, but it is certainly good to understand. There are multiple perspectives worth understanding it from, even.

We already outlined one perspective at ["Total Limits Are Empty Colimits"](@/TotalLimits.md). Here, I will outline another.

***

If you have basic experience with abstract algebra, the ideas in the Yoneda lemma should be quite familiar and even intuitive. The apparent difficulty is only in recognizing them in this new presentation.

You can think of "category" as meaning the same thing as "algebraic theory in a multisorted language with only unary functions"—the objects of the category being the sorts of the language, the morphisms being the definable functions, and the equalities between (composites of) morphisms being the laws of the theory. From this perspective, a functor from $$C$$ to $$\mathrm{Set}$$ is simply a model of the theory corresponding to $$C$$, and natural transformations of such functors are homomorphisms of models.

The Yoneda lemma then is about free models. Specifically, it says that for every sort $$s$$, the "term model" of terms with a single variable, of sort $$s$$ (equivalently, definable functions with domain $$s$$) is the free model on a single generator of sort $$s$$. It may be unfamiliar when expressed as "$$\mathrm{Nat}(\mathrm{Hom}(s, {-}), M) \cong M(s)$$ naturally in $$M$$", but that is indeed all this categorical expression is saying.

The so-called co-Yoneda lemma also has a nice interpretation from this perspective, amounting to the demonstration that every model can be specified by generators and relations.

I wouldn't say this is The One Right Way to think about the Yoneda lemma, because it's useful to view it from many different perspectives, but this is certainly One Right Way to think about the Yoneda lemma.

***

[TODO: Actually state the Yoneda and co-Yoneda lemmas at the top of this post]

[TODO: Make a post on functorial semantics more generally]