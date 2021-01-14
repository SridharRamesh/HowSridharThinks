---
title: "Alternating Series, Generalized Summation, and the Dirichlet Eta Function"
date: 2021-1-7
---
A standard observation is that, if $$f$$ is a monotonically decreasing function from some point on, approaching zero asymptotically, then the alternating series $$f(0) - f(1) + f(2) - f(3) + f(4) - f(5) + \ldots$$ converges. This is easy to see: the partial sums jump up and down and then up a little less and then down a little less, and so on, so that we get a decreasing series of upper bounds on the lim sup alternating with an increasing series of lower bounds on the lim inf. The distance between any two adjacent of these is given by the corresponding value of f, and as this approaches zero in the limit, the lim sup matches the lim inf.

***

I wish to record another point of note: The alternating series $$f(0) - f(1) + f(2) - f(3) + \ldots$$, for any $$f$$, is equal to the alternating series $$g(0) - g(1) + g(2) - g(3) + \ldots$$, where $$g(x) = (f(x) - f(x - 1))/2$$ with $$f(-1)$$ taken to be zero.

Removing the alternation, this is the observation that $$p(0) + p(1) + p(2) + \ldots = \frac{1}{2} [(0 + p(0)) + (p(0) + p(1)) + (p(1) + p(2)) + (p(2) + p(3)) + \ldots]$$. But the alternation gives it particularly good properties, like so:

The terms of the series for g are essentially the differential of the series for f. This means, even if f itself does not vanish asymptotically, as long as its differential vanishes asymptotically (and decreases monotonically), we can use this series in terms of g to give an account of the alternating sum of f.

Iterating this process, it suffices for any iterated differential of f to vanish asymptotically (again, as long as the appropriate monotonicity properties work out).

In particular, with $$f(x) = x^p$$, the alternating series converges only when $$\Re(p) < 0$$. But we automatically have that each differential essentially knocks the power down by 1, so that sufficiently iterated differentials will yield a convergent series. In this way, we can interpret the Dirichlet eta function for arbitrary powers. And from this, straightforwardly, we can interpret the Riemann zeta function as well.

(Note that this establishes the Dirichlet eta function as Abel summable, by establishing it as suitably generalized/iterated Cesaro summable. We see that the Dirichlet eta function's summability is quite easy to handle!)

This is another simple approach to the analytic continuation of the Riemann zeta function. Perhaps simpler than the one we've seen before for [difference equations in general]({{ site.baseurl }}{% link _math/DifferenceEquationZeta.md %}))], though I like that as well. Actually, perhaps there is some connection between this and that method? There is a similar fixation on an iterated differential which vanishes asymptotically. But there, the differentials are over arbitrary intervals, and used to sum f straight, while here, they are all over unit intervals, and used to sum f alternating. Hm... (TODO: Work this out!)

***

Indeed, nevermind about alternating series in particular. We can apply this same idea to $$\sum_n \lambda^n n^s$$ for $$\abs{\lambda} \leq 1$$ with $$\lambda \neq 1$$. By bundling together $$\lambda$$ times the series plus some shift of the series, get that the series comes to $$(\lambda - 1)^{-1} \lambda$$ times $$\sum_n \lambda^{n} \qty(n^s - (n + 1)^s)$$. Thus, by iteration, we can iterate the differential, till the effective exponent has come down so far that we are in the realm of absolute convergence. Thus, all such nontrivially periodized zeta series or even the Lerch transcendent (periodized Hurwitz zeta from arbitrary starting point) for each $$\lambda$$ of the sort noted above are generalized/iterated Cesaro summable (and thus Abel summable as well).

When dealing with the regular zeta and not the Hurwitz zeta from a different starting point, we can then compute the value for $$\lambda = 1$$ (the Riemann zeta function) in the usual way from the rest of these; for example, by considering all $$N$$-th roots of unity $$\lambda$$, we know that the corresponding series sum to $$N \times N^s = N^{s + 1}$$ times just the series for $$\lambda = 1$$, from which we can derive the value for the series for $$\lambda = 1$$ as $$(1 - N^s)^{-1}$$ times the sum of the series for the other $$N$$th roots of unity.

In this way, we do not even have to worry about the removable discontinuities at roots of $$1 - N^{s + 1}$$ other than $$s = -1$$ (the unremovable pole of the Riemann zeta function): We can compute this series for both $$N = 2$$ and $$N = 3$$, say, which beacuse of the irrational ratio between $$2$$ and $$3$$ will have no divisions by zero in common except at $$s = -1$$.

***

See also the Euler transform.