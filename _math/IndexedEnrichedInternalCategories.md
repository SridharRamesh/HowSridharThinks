---
title: "Indexed, Enriched, and Internal Categories"
date: 2021-10-2
---
In general, there are many things to say about these. I just wanted to record for myself some thoughts I realized today. (There's things to say about indexed, enriched, and internal STRUCTURES in general, but the particular observation I want to make involves some aspects that are specific to CATEGORIES in particualr.)

Recall that a $$T$$-indexed category $$C$$ is a category internal to $$Psh(T)$$, the category of presheaves over $T$. If $$Mor(C)$$ and $$Ob(C)$$ are "small" in the sense of being representable presheaves, then this is the same as being internal to $$T$$.

On the other hand, if $$Ob(C)$$ is a constant set (a copower of the constantly 1 presheaf), and the Hom map $$Mor(C) \to Ob(C)^2$$ has "small" fibers (in the sense that its pullback along any map out of a small set is itself small), then we say this is a $$T$$-enriched category (with respect to the cartesian product on $$T$$; we are not considering non-cartesian notions of enrichment here).

Now, suppose given a functor $$f : T \to S$$. Under what situations does this take a $$T$$-indexed/enriched/internal category to an $$S$$ category of the same respective sort?

If $$f$$ is a lexfunctor between lexcategories, then its Yoneda extension $$: Psh(T) \to Psh(S)$$ (the one given by left Kan extension of presheaves along $$f$$, which turns out to indeed match the behavior of $$f$$ on representable presheaves) also preserves finite limits (see Diaconescu's theorem). Thus, automatically, it takes $$T$$-indexed categories to $$S$$-indexed categories, and in the same way, takes $$T$$-internal categories to $$SS$-internal categories.

But what if $$f$$ merely preserves finite products? There's a direct way to see that this is good enough to take $$T$$-enriched categories to $$S$$-enriched categories, by looking at the traditional account of enrichment. But we can also see it indirectly. The Yoneda extension of $$f$$ now preserves finite products (see https://mathoverflow.net/questions/255282/yoneda-extension-preserving-finite-products). Yoneda extensions also always preserve all colimits (as they are left adjoints, or just as well, as they correspond to the free cocompletion functor). It thus takes a constant set to the corresponding constant set. The local smallness conditions are also easy enough. But what's not necessarily obvious is that it takes the structure of an internal category to the structure of an internal category, as this structure involves general finite limits (such as pullbacks or equalizers), and we don't have a general guarantee of preserving finite limits.

However, it will indeed preserve the particular finite limits we need. We just need those which define strings of N many composable morphisms. These are given by an equalizer between Mor(C)^N and Ob(C)^(N - 1) \[the limit of a diagram with N many copies of Mor(C) sitting as fence slats with domain and codomain mappings back and forth into N + 1 many fence post copies of Ob(C). Of these latter, only N - 1 induce equalizer conditions\].

But as Ob(C) is a constant set, so is any power of it. And the claim I wish to make is that we automatically preserve equalizers into any constant set K. Why is that? We can rewrite this as a pullback of the diagonal map $$K \to K^2$$ along the corresponding product map into $$K^2$$. All the structure here is automatically preserved by our preserving constant sets and products, except for possibly the pullback. But now my claim is that we in fact automatically preserve all pullbacks over constant sets. Why is that? By the extensivity properties of a Grothendieck topos, preserving pullbacks over (1 + 1 + 1 + ...) just reduces to preserving pullbacks over 1. And these we preserve, because we preserve binary products.

----

TODO: This is all unreadable to anyone except me, but at least I've written it for my own reference and reconstruction.