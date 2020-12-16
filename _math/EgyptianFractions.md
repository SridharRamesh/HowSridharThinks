---
title: "Egyptian Fractions"
date: 2020-12-16
---

Any rational in $$[0, 1)$$ can be written as a finite sum of reciprocals of natural numbers. For zero, this is trivial, as an empty sum. As for other such values, specifically, if $$\frac{x}{y}$$ is the fraction to be represented (whether in lowest terms or not, we can apply this same procedure), we let $$n$$ be the smallest whole number such that $$nx \geq y$$ (i.e., $$\frac{x}{y} \geq \frac{1}{n}$$), and then rewrite $$\frac{x}{y}$$ as $$\frac{1}{n}} + \frac{nx - y}{ny}$$.

Note that the numerator of $$\frac{nx - y}{ny}$$ is less than $$x$$. We now recursively expand it in the same way, and so on and so on. As the numerators keep shrinking, this must eventually terminate in a numerator of zero, at which point we are done.

Note that $$0 \leq \frac{nx - y}{ny} < \frac{x}{y} < 1$$. This establishes that the new fraction to be recursively expanded is in the relevant range.

Not only that, but this expansion produces a series $\frac{1}{n_1} + \frac{1}{n_2} + \frac{1}{n_3} + \ldots$$ where the denominators are strictly increasing. To see this, take a second step of the expansion: What is the smallest $$m$$ such that $$\frac{nx - y}{ny} \geq \frac{1}{m}$$? Well, as $$\frac{nx - y}{ny} < \frac{x}{y}$$, such an $$m$$ must be at least as large as $$n$$. Can $$m = n$$? This would mean $$n^2x - ny \geq ny$$, i.e., $$nx \geq 2y$$, i.e., the smallest multiple of $$x$$ which upper-bounds $$y$$ also upper-bounds $$2y$$, i.e., $$\lceil \frac{x}{y} \rceil \geq 2$$. But this can't happen by our presumption that our fractions lie in the range $$[0, 1)$$ to begin with.

This is called an Egyptian fraction expansion.

Note now that ANY positive rational $$R$$ has an Egyptian fraction expansion using exclusively arbitrarily large denominators, by taking the harmonic series starting from whatever arbitrarily large denominator, and taking as many values as it takes to cross from below to above $$R$$. Consider this crossing point, such that the partial sums up through $$\frac{1}{n}$$ are below $$R$$ but up through $$\frac{1}{n + 1}$$ are above $$R$$. This means that the partial sum up through $$\frac{1}{n}$$ is less than $$\frac{1}{n + 1}$$ below $$R$$. Whatever that remaining error is, as a rational in $$[0, 1)$$, it has its own Egyptian fraction representation by the above, which must use denominators which are all strictly higher than $$n + 1$$ and thus distinct from those in our partial sum so far, completing what we want.