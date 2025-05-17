---
title: "The Hurwitz and Riemann functional equations"
date: 2024-2-5
---
Where the celebrated "functional equation" for the Riemann zeta function comes from, as well as for the Hurwitz zeta function more generally. I believe the approach here is cleaner and better motivated than either the contour integration or theta function approaches people usually give, which seem to me a long mess of magic calculation. I think the approach here should make the functional equation even obvious, in hindsight.

## Defining the zeta functions

Recall from our previous discussion of [difference equations](@/DifferenceEquationZeta.md) that there is a unique function $$F(p, x)$$ such that we have: $$\newcommand{\nat}{\mathbb{N}}$$
* $$\displaystyle \lim_{n \to +\infty} F(p, x + n) = 0$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} F(p, x) = (p + 1)F(p - 1, x)$$.
* $$\int_{x}^{x + 1} F(p, x) \\; dx = x^{p + 1}$$.
<!-- Periods included above to get the typesetting to not do weird things with math in a bulleted list where some items are mixed with non-math and others aren't. -->

Furthermore, this $$F(p, x)$$ is complex-differentiable with respect to $$p$$ as well.

Note that the second and third conditions together entail that $$F(p, x) = (p + 1)x^p + F(p, x + 1)$$. Together with the first condition, this entails that $$F(p, x) = (p + 1) \sum_{n = 0}^{\infty} (x + n)^p$$ whenever $$\Re(p) < -1$$.

We define the Hurwitz zeta function $$\zeta(-p, x)$$ for $$p \neq -1$$ as $$F(p, x)/(p + 1)$$. The Riemann zeta function is defined as the special case $$\zeta(-p) = \zeta(-p, 1)$$.

For the Hurwitz zeta function, the corollaries of the above properties are:

* $$\displaystyle \lim_{n \to +\infty} \zeta(-p, x + n) = 0$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} \zeta(-p, x) = p \zeta(-(p - 1), x)$$.
* $$\int_{x}^{x + 1} \zeta(-p, x) \\; dx = x^{p + 1}/(p + 1)$$.
* $$\zeta(-p, x) = x^{p + 1}/(p + 1) + \zeta(-p, x + 1)$$.
* $$\zeta(-p, x) = \sum_{n = 0}^{\infty} (x+n)^p$$ whenever $$\Re(p) < -1$$.

\[To be pedantically unambiguous, in our domain of interest, we interpret $$x^p$$ for arbitrary $$p$$ via $$x^p = \exp(p \log(x))$$, where $$\log$$ is a logarithm assuming real values on positive inputs and then analytically continued to $$\Re(x) \geq 0$$, $$x \neq 0$$. (We could continue it to larger domains for $$x$$, but will have no need for this. This punctured closed half-plane is the domain of bases of exponentiation for our purposes). When $$\Re(p) > 0$$ or $$p = 0$$, we also define $$0^p$$ as $$\lim_{x \to 0} x^p$$ (which is $$0$$ when $$\Re(p) > 0$$ and $$1$$ when $$p = 0$$) and define $$\zeta(-p, 0)$$ as $$\lim_{x \to 0} \zeta(-p, x) = \zeta(-p, 1) + 0^p$$.\]

Each of the conditions which together uniquely define $$F(p, x)$$ is such that $$n^p \sum_{k = 0}^{n - 1} F(p, (x + k)/n)$$ inherits the same condition. Thus, these two are equal. This is the "duplication/multiplication formula". Similarly, $$\zeta(-p, x) = n^p \sum_{k = 0}^{n - 1} \zeta(-p, (x + k)/n)$$.

## Naive approach to the functional equation
$$\zeta(-p, x)$$ naively equals $$\sum_{n \in \mathbb{N}} (x + n)^p$$. For $$x \in (0, 1)$$ (with some fuzziness about whether this includes the endpoints), this equals $$\sum_{n \in \mathbb{Z}} f(x + n)$$, where $$f(x) = u(x) x^p$$, where $$u$$ is the Heaviside step function. So by naive Poisson summation, we get that $$\zeta(-p, 0)$$ (or perhaps $$\zeta(-p, 1)$$, or perhaps the halfway value between them) is $$\sum_{n \in \mathbb{Z}} \int_{0}^{\infty} x^p e^{-2 \pi i n x} \\; dx$$.

The difference between $$\zeta(-p, 0)$$ and $$\zeta(-p, 1)$$ is $$0^p$$, which let's ignore as it would vanish when $$\Re(p) > 0$$. So we'll take our Fourier series to sum to $$\zeta(-p, 1) = \zeta(-p)$$.

Similarly, the $$n = 0$$ term is $$\int_{0}^{\infty} x^p \\; dx = \left( \infty^{p + 1} - 0^{p + 1} \right)/(p + 1)$$. When $$\Re(p) < - 1$$, the $$\infty^{p + 1}$$ vanishes. When $$\Re(p) > -1$$, the $$0^{p + 1}$$ vanishes. So let's just ignore both.

Also, by naive rescaling of variables from $$x$$ to $$x/(-2 \pi i n)$$ for nonzero $$n$$ (even though this change of variables by an imaginary factor actually changes the integration path, going out now to a different infinity, so to speak), we get that $$\int_{0}^{\infty} x^p e^{-2 \pi i n x} \\; dx = (-2 \pi i n)^{-1 - p} \int_{0}^{\infty} x^p e^{-x} \\; dx$$. For $$\Re(p) > -1$$, this converges to $$(-2 \pi i n)^{-1 - p} \Gamma(1 + p)$$. So let's just say that's what it is, regardless of other incompatible constraints we've used on $$p$$.

So we have $$\zeta(-p) = \sum_{n \in \mathbb{N}^+} \sum_{i^2 = -1} (2 \pi n)^{-1 - p} (-i)^{-1 - p} \Gamma(1 + p)$$. Naively taking $$i^{\theta} = \left( e^{i \pi/2} \right)^{\theta} = e^{i \pi \theta/2} = \cos(\pi \theta/2) + \sin(\pi \theta/2) i$$ (even though $$i$$ has multiple logarithms), then $$\sum_{i^2 = -1} (-i)^{-1 - p} = 2 \cos(\pi (1 + p)/2) = -2 \sin(\pi p/2)$$.

Thus, $$\zeta(-p, x) = -2 \sin(\pi p/2) (2 \pi)^{-1 - p} \Gamma(1 + p) \zeta(-(-1 - p))$$.

Can we make this naive derivation work? Yes, with a bit more care:

## Proper derivation of Fourier series for the Hurwitz zeta
Observe that, when $$\Re(p) > 0$$, we have that $$\zeta(-p, 0) = \zeta(-p, 1)$$. Thus, we can make a continuous periodic function $$x \mapsto \zeta(-p, x')$$ on real $$x$$, where $$x'$$ is the unique value in $$(0, 1]$$ which differs from $$x$$ by an integer. This function will furthermore be differentiable in both directions at every point (though these two derivatives won't match at integer inputs).
$$\newcommand{\ZetaCoeff}[3]{c_{#2}^{#1}(#3)}$$
$$\newcommand{\FCoeff}[3]{d_{#2}^{#1}(#3)}$$
$$\newcommand{\start}{\mathrm{start}}$$

Such bidifferentiable periodic functions admit Fourier series which converge everywhere to them. That is, extracting Fourier coefficients in the usual way as $$c_n = \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i n x} \\; dx$$ and then stringing them together as the Fourier series[^FourierConditional] $$f(x) = \sum_{n \in \mathbb{Z}} c_n e^{2 \pi i n x}$$, we will have that $$\zeta(-p, x) = f(x)$$.

[^FourierConditional]: Where the infinite sum is interpreted in case of conditional convergence via partial sums extending equally into negative and positive indices.

The computation of $$c_0$$ is straightforward: $$\int_{0}^{1} \zeta(-p, x) dx = 0^p/(p + 1) = 0$$, given our presumption that $$\Re(p) > 0$$ (indeed, this holds even if $$\Re(p) > -1$$).

\[
For $$c_{\pm n}$$ for positive integer $$n$$, we can reason directly from the multiplication formula $$\zeta(-p, x) = n^p \sum_{k = 0}^{n - 1} \zeta(-p, (x + k)/n)$$ that $$c_{\pm n} = c_{\pm 1} n^{-1 - p}$$, for arbitrary $$p$$. This makes the shape of the functional equation relating $$\zeta(-p)$$ and $$\zeta(-(-1-p))$$ apparent, leaving only the computation of $$c_{\pm 1}$$. Similarly, the value $$c_{-1}$$ for a given $$p$$ is automatically the complex conjugate of the value for $$c_1$$ for the complex conjugate of $$p$$, by conjugation symmetry, so we only need to establish the value of $$c_1$$. 

we need not dwell on these ways of looking at them, as the method by which $$c_{1}$$ is computed works just as well to directly compute $$c_{\pm n}$$ and observe the same scaling/conjugation properties. But for now, the rest of this is written in terms of calculating $$c_1$$.
\]

Note that, when $$\Re(p) > 0$$ so that $$0^p = 0$$, we have by integration by parts that $$-2 \pi i \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i x} \\; dx = -p \int_{0}^{1} \zeta(-(p - 1), x) e^{-2 \pi i x} \\; dx$$. (This integration by parts amounts to the differentiation rule for Fourier series applied to the fact $$\frac{d}{dx} \zeta(-p, x) = p \zeta(-(p - 1), x)$$.)

So we just need to determine the Fourier series for $$\Re(p) \in (-1, 0)$$ and this will then extend by this recurrence to telling us the Fourier series for all $$\Re(p) > -1$$ with $$\Re(p)$$ not an integer. [We can presumably also get the values at $$\Re(p)$$ an integer by continuity/meromorphic continuation arguments, if we want them.].

Now, let us observe in the other direction that when $$\Re(p) < 0$$, we can evaluate $$c_1 = \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i x} \\; dx$$ like so: Defining the function $$G(m) = \left( \int_{0}^{m} x^p e^{-2 \pi i x} \\; dx \right) + \left( \int_{m}^{m + 1} \zeta(-p, x) e^{-2 \pi i x} \\; dx \right)$$, we see by differentiating with respect to $$m$$ that $$G(m)$$ is constant across all values of $$m$$, while $$c_1 = G(0)$$. Integration by parts turns $$(-2 \pi i) \int_{m}^{m + 1} \zeta(-p, x) e^{-2 \pi i x} \\; dx$$ into $$-m^p + p \int_{m}^{m + 1} \zeta(-(p - 1), x) e^{-2 \pi i x} \\; dx$$. When $$\Re(p) < 0$$, this vanishes in the limit as $$m \to \infty$$, keeping in mind how $$\zeta(-(p - 1), x)$$ vanishes in the limit and how it is being integrated against a function with bounded magnitude over a bounded region. Thus, we get that $$c_1 = G(0) = G(m) = \lim_{m \to \infty} G(m) = \int_{0}^{\infty} x^p e^{-2 \pi i x} \\; dx$$. Furthermore, by choosing $$0 < m < \infty$$, we see this value $$G(m)$$ is convergent for $$\Re(p) > -1$$, as $$\int_{0}^{m} x^p e^{-2 \pi i x} \\; dx$$ is absolutely convergent for $$m < \infty$$ and $$\Re(p) > -1$$, while $$\int_{m}^{m + 1} \zeta(-p, x) e^{-2 \pi i x} \\; dx$$ is the integral of a continuous function on a closed interval for $$m > 0$$ and thus convergent for such $$m$$ regardless of $$p$$.

***

Our goal now is to study $$\int_{0}^{\infty} x^p e^{-2 \pi i x} \\; dx$$ as a function of $$p$$.

By Abel integration (the continuous analogue of Abelian summation, saying that if the Laplace transform of a function converges at 0, then its value there is the limit of its value at positive reals), where this is convergent (which we've seen occurs when $$\Re(p) > -1$$), this is equal to $$\lim_{s = 2 \pi i + \epsilon, \epsilon > 0, \epsilon \to 0} \int_{0}^{\infty} x^p e^{-sx} \\; dx$$.

By the rescaling properties of the Laplace transform (i.e., by the change of variables replacing $$x$$ with $$x/s$$), we have that $$\int_{0}^{\infty} x^p e^{-sx} dx = s^{-1 - p} \int_{0}^{1} x^p e^{-sx} dx$$ for positive $$s$$. When $$\Re(p) > 0$$, where this integral is absolutely convergent, this is $$s^{-1 - p} \Gamma(1 + p)$$ by the definition of $$\Gamma(1 + p)$$. By the analyticity of the Laplace transform through its region of absolute convergence, we get that $$\int_{0}^{\infty} x^p e^{-sx} dx = s^{-1 - p} \Gamma(1 + p)$$ even for complex $$s$$ with $$\Re(s) > 0$$, again with the condition that $$\Re(p) > 0$$. (Here, we interpret $$s^p = \exp(p \log(s))$$ using the analytic continuation of the natural logarithm taking real values on the real axis, to the half-plane $$\Re(s) > 0$$. In other words, $$s$$ is treated as having argument in $$(-\pi/2, \pi/2)$$ for the purposes of determining $$\log(s)$$.)

By the famous integration by parts under which the Gamma function acquires its hallmark recurrence relation, we have for $$\Re(p) > 0$$ that $$\int_{0}^{\infty} x^p e^{-sx} dx = (p/s) \int_{0}^{\infty} x^{p - 1} e^{-sx} dx$$. The $$s = 1$$ case of this is the recurrence $$\Gamma(1 + p) = p \Gamma(1 + (p  - 1))$$, which is used to analytically continue the definition of $$\Gamma(1 + p)$$ to all inputs other than negative integers $$p$$. In particular, we now have that $$\int_{0}^{\infty} x^p e^{-sx} dx = s^{-1 - p} \Gamma(1 + p)$$ for $$\Re(s) > 0$$ and $$\Re(p) > -1$$ (with conditional convergence, as opposed to the absolute convergence with $$\Re(p) > 0$$).

Thus, we can compute $$\lim_{s = 2 \pi i + \epsilon, \epsilon > 0, \epsilon \to 0} \int_{0}^{\infty} x^p e^{-sx} \\; dx$$ as the continuously varying value of $$s^{-1 - p} \Gamma(1 + p)$$ at $$s = 2 \pi i$$, and conclude that $$\int_{0}^{\infty} x^p e^{-2 \pi i x} \\; dx = (2 \pi i)^{-1 - p} \Gamma(1 + p)$$, with exponentiation with base $$\pm i$$ treated as having argument $$\pm \pi/2$$.

This gives us the Fourier series for $$\Re(p) \in (-1, 0)$$ but it then automatically extends by our previous recurrence to give us the Fourier series for general $$\Re(p) > -1$$ with $$\Re(p)$$ not an integer.

In particular, as we noted before, where $$\Re(p) > 0$$, the Fourier series will indeed converge to $$\zeta(-p)$$ at the endpoints of the interval. Thus, in the region with $$\Re(p) > 0$$ and $$\Re(p)$$ not an integer, we can now conclude that $$\zeta(-p) = -2 \sin(\pi p/2) (2 \pi)^{-1 - p} \Gamma(1 + p) \zeta(-(-1 - p))$$ as desired. As this is an equation beteween meromorphic functions on a region with an accumulation point (indeed, on an inhabited open set), it holds at all $$p$$ by continuation.

***

TODO: Clean up the above

TODO: Also discuss the Hurwitz zeta function Fourier coefficients at all other powers $$p$$ or over other unit intervals.

***

Footnotes: