---
title: "Alternating Series, Generalized Summation, and the Dirichlet Eta Function"
date: 2021-1-7
---
A standard observation is that, if $$f$$ is a monotonically decreasing function from some point on, approaching zero asymptotically, then the alternating series $$f(0) - f(1) + f(2) - f(3) + f(4) - f(5) + \ldots$$ converges. This is easy to see: the partial sums jump up and down and then up a little less and then down a little less, and so on, so that we get a decreasing series of upper bounds on the lim sup alternating with an increasing series of lower bounds on the lim inf. The distance between any two adjacent of these is given by the corresponding value of f, and as this approaches zero in the limit, the lim sup matches the lim inf.

***

I wish to record another point of note: The alternating series $$f(0) - f(1) + f(2) - f(3) + \ldots$$, for any $f$, is equal to the alternating series $$g(0) - g(1) + g(2) - g(3) + \ldots$$, where $$g(x) = (f(x) - f(x - 1))/2$$ with $$f(-1)$$ taken to be zero.

Removing the alternation, this is the observation that $$p(0) + p(1) + p(2) + \ldots = \frac{1}{2} [ (p(0) + p(1)) + (p(1) + p(2)) + (p(2) + p(3)) + \ldots]$$. But the alternation gives it particularly good properties, like so:

The terms of the series for g are essentially the differential of the series for f. This means, even if f itself does not vanish asymptotically, as long as its differential vanishes asymptotically (and decreases monotonically), we can use this series in terms of g to give an account of the alternating sum of f.

Iterating this process, it suffices for any iterated differential of f to vanish asymptotically (again, as long as the appropriate monotonicity properties work out).

In particular, with $$f(x) = x^p$$, the alternating series converges only when $$\Re(p) < 0$$. But we automatically have that each differential essentially knocks the power down by 1, so that sufficiently iterated differentials will yield a convergent series. In this way, we can interpret the Dirichlet eta function for arbitrary powers. And from this, straightforwardly, we can interpret the Riemann zeta function as well.

(Of course, the Dirichlet eta function is Abel summable anyway. It is in general quite easy to handle.)

This is another simple approach to the analytic continuation of the Riemann zeta function. Perhaps simpler than the one we've seen before for [difference equations in general]({{ site.baseurl }}{% link _math/DifferenceEquationZeta.md %}))], though I like that as well. Actually, perhaps there is some connection between this and that method? There is a similar fixation on an iterated differential which vanishes asymptotically. But there, the differentials are over arbitrary intervals, and used to sum f straight, while here, they are all over unit intervals, and used to sum f alternating. Hm... (TODO: Work this out!)