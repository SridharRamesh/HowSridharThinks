---
title: "Sophomore's Dream"
date: 2020-12-28
---
Here are a couple little curiosities in calculus (known since at least 1697 by Johan Bernoulli). They are sometimes called "sophomore's dream", because they feel too good to be true, like the kind of glib substitution of one thing by another somewhat similar thing that a naive student might make, and because something else already took the name freshman's dream [TODO: Write about and link to freshman's dream].

The two observations are that $$\int_{0}^{1} x^{-x} \dd{x} = \sum_{1}^{\infty} n^{-n}$$ and that $$\int_{0}^{1} x^x \dd{x} = -\sum_{1}^{\infty} (-n)^{-n}$$. In other words, the unified observation is that $$\int_{0}^{1} x^{\pm x} \dd{x} = \mp \sum_{1}^{\infty} (\mp n)^{-n}$$.

The first step in seeing this is rewriting $$x^{\pm x}$$ as $$e^{\pm x \log(x)} = \sum_{n = 0}^{\infty} \frac{(\pm x \log(x))^n}{n!}$$. Now we wish to integrate from 0 to 1. This requires us to understand the integral of $$(x \log(x))^n$$ from 0 to 1.

Well, it's easy to see that the integral of $$x^p \log^n(x)$$ in general, where $$p$$ is arbitrary and $$n$$ is a natural number, will be $$x^{p + 1}$$ and $$q$$ are natural numbers, is the sum of a bunch of similar terms where each term has the same power $$p$$ on $$x$$, but some power $$q \leq Q$$ [TODO. Write out a post on just integrating x^p log^q(x), since it comes up so often. See https://twitter.com/RadishHarmers/status/1330420725988139010 for a discussion of canonical antiderivatives.]