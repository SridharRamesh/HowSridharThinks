---
title: "The Hurwitz and Riemann functional equations"
date: 2024-1-29
---
TODO: Ignore this post. It's gone live too early. I'm still editing it.

Where the celebrated "functional equation" for the Riemann zeta function comes from, as well as for the Hurwitz zeta function more generally. I believe the approach here is cleaner and better motivated than either the contour integration or theta function approaches people usually give, which seem to me a long mess of magic calculation. I think the approach here should make the functional equation even obvious, in hindsight.

## Defining the zeta functions

Recall from our previous discussion of [difference equations](./DifferenceEquationZeta.html) that there is a unique function $$F(p, x)$$ such that we have: $$\newcommand{\nat}{\mathbb{N}}$$
* $$\displaystyle \lim_{n \to +\infty} F(p, x + n) = 0$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} F(p, x) = (p + 1)F(p - 1, x)$$.
* $$\int_{x}^{x + 1} F(p, x) \; dx = x^{p + 1}$$.
<!-- Periods included above to get the typesetting to not do weird things with math in a bulleted list where some items are mixed with non-math and others aren't. -->

Furthermore, this $$F(p, x)$$ is complex-differentiable with respect to $$p$$ as well.

Note that the second and third conditions together entail that $$F(p, x) = (p + 1)x^{p + 1} + F(p, x + 1)$$. Together with the first condition, this entails that $$F(p, x) = (p + 1) \sum_{n = 0}^{\infty} (x + n)^p$$ whenever $$\Re(p) < -1$$.

We define the Hurwitz zeta function $$\zeta(-p, x)$$ for $$p \neq -1$$ as $$F(p, x)/(p + 1)$$. The Riemann zeta function is defined as the special case $$\zeta(-p) = \zeta(-p, 1)$$.

For the Hurwitz zeta function, the corollaries of the above properties are:

* $$\displaystyle \lim_{n \to +\infty} \zeta(-p, x + n) = 0$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} \zeta(-p, x) = p \zeta(-(p - 1), x)$$.
* $$\int_{x}^{x + 1} \zeta(-p, x) \; dx = x^{p + 1}/(p + 1)$$.
* $$\zeta(-p, x) = x^{p + 1}/(p + 1) + \zeta(-p, x + 1)$$.
* $$\zeta(-p, x) = \sum_{n = 0}^{\infty} (x+n)^p$$ whenever $$\Re(p) < -1$$.

\[To be pedantically unambiguous, in our domain of interest, we interpret $$x^p$$ for arbitrary $$p$$ via $$x^p = \exp(p \log(x))$$, where $$\log$$ is a logarithm assuming real values on positive inputs and then analytically continued to $$\Re(x) \geq 0$$, $$x \neq 0$$. (We could continue it to larger domains for $$x$$, but will have no need for this. This punctured closed half-plane is the domain of bases of exponentiation for our purposes). When $$\Re(p) > 0$$ or $$p = 0$$, we also define $$0^p$$ as $$\lim_{x \to 0} x^p$$ (which is $$0$$ when $$\Re(p) > 0$$ and $$1$$ when $$p = 0$$) and define $$\zeta(-p, 0)$$ as $$\lim_{x \to 0} \zeta(-p, x) = \zeta(-p, 1) + 0^p$$.\]

Each of the conditions which together uniquely define $$F(p, x)$$ is such that $$n^p \sum_{k = 0}^{n - 1} F(p, (x + k)/n)$$ inherits the same condition. Thus, these two are equal. This is the "duplication/multiplication formula". Similarly, $$\zeta(-p, x) = n^p \sum_{k = 0}^{n - 1} \zeta(-p, (x + k)/n)$$.

## Fourier series for the Hurwitz zeta

In the following, when we write $$\int_{p}^{\infty} f(x) \; dx$$ for complex $$p$$, this means $$\int_{0}^{\infty} f(p + x) \; dx$$ where $$x$$ ranges over the real interval $$(0, \infty)$$. Similiarly, when we refer to a function being defined on an interval $$(p, p + 1)$$, this means the set $$\{p + x \mid x \in (0, 1)\}$$ where again $$(0, 1)$$ is interpreted as the familiar real interval.
$$\newcommand{\ZetaCoeff}[3]{c_{#2}^{#1}(#3)}$$
$$\newcommand{\FCoeff}[3]{d_{#2}^{#1}(#3)}$$
$$\newcommand{\start}{\mathrm{start}}$$

Observe that, when $$\Re(p) > 0$$, we have that $$\zeta(-p, 0) = \zeta(-p, 1)$$. Thus, we can make a continuous periodic function $$x \mapsto \zeta(-p, x')$$, where $$x'$$ is the unique value in $$(0, 1]$$ which differs from $$x$$ by an integer. This function will furthermore be differentiable in both directions at every point (though these two derivatives won't match at integer inputs).

Such bidifferentiable periodic functions admit Fourier series which converge everywhere to them. That is, extracting Fourier coefficients in the usual way as $$c_n = \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i n x} \; dx$$ and then stringing them together as the Fourier series[^FourierConditional] $$f(x) = \sum_{n \in \mathbb{Z}} c_n e^{2 \pi i n x}$$, we will have that $$\zeta(-p, x) = f(x)$$.

[^FourierConditional]: Where the infinite sum is interpreted in case of conditional convergence via partial sums extending equally into negative and positive indices.]

The computation of $$c_0$$ is straightforward: $$\int_{0}^{1} \zeta(-p, x) dx = 0^p/(p + 1) = 0$$, given our presumption that $$\Re(p) > 0$$ (indeed, this holds even if $$\Re(p) > -1$$).

Also, for positive integer $$n$$, by change of variables and the multiplication formula $$\zeta(-p, x) = n^p \sum_{k = 0}^{n - 1} \zeta(-p, (x + k)/n)$$, we have that $$\int_{0}^{1} \zeta(-p, x) e^{\mp 2 \pi i n x} \; dx$$ $$= n^{-1} \int_{0}^{n} \zeta(-p, x/n) e^{\mp 2 \pi i x} \; dx$$ $$= n^{-1} \sum_{k = 0}^{n - 1} \int_{k}^{k + 1} \zeta(-p, x/n) e^{\mp 2 \pi i x} \; dx$$ $$= n^{-1 - p} \int_{0}^{1} \zeta(-p, x) e^{\mp 2 \pi i x} \; dx$$. Thus, $$c_{\pm n} = c_{\pm 1} n^{-1 - p}$$. [The reasoning of this paragraph applies for arbitrary $$p$$, not just $$\Re(p) > 0$$. It also applies equally well to the analogous Fourier coefficients for $$F(p, x)$$ including at $$p = -1$$.]

Thus, we have that $$\zeta(-p, x) = (c_1 + c_{-1}) \sum_{n \in \mathbb{N}} n^{-1 - p} e^{2 \pi i n x}$$ for $$x \in [0, 1]$$. In particular, at the endpoints, we have $$\zeta(-p) = (c_1 + c_{-1}) \zeta(-(-1 - p))$$. These are the Hurwitz and Riemann zeta functional equations. We've established this in the regime $$\Re(p) > 0$$, but presuming the expressions for $$c_1$$ and $$c_{-1}$$ are meromorphic in $$p$$, the Riemann functional equation will then extend by meromorphic continuation to hold for all $$p$$.

What remains is only to find formulas for $$c_1$$ and $$c_{-1}$$, in terms of $$p$$. (By conjugation symmetry, the value of $$c_{-1}$$ for a given $$p$$ will just be the conjugate of $$c_1$$ for the conjugate of $$p$$, so our remaining task in establishing the functional equation is really just to find a formula for $$c_1$$ in terms of $$p$$, in the range where $$\Re(p) > 0$$ or even just any interval within that range.)

We will actually tackle the more general question of $$\int_I \zeta(-p, x) e^{-2 \pi i n x} \; dx$$ for arbitrary $$p$$ over a general interval $$I = (\start, \start + 1)$$, as this is not much more work. Let us call this $$\ZetaCoeff{p}{n}{\start}$$, with $$c_n$$ as $$\ZetaCoeff{p}{n}{0}$$ for an implicit $$p$$. Note that $$\ZetaCoeff{p}{n}{\start} / e^{-2 \pi i n \start}$$ is the $$n$$-th coefficient of the Fourier series for $$\zeta(-p, x)$$ over the interval $$I$$.

\[
(For $$\Re(p) < -1$$, expressing $$\zeta(-p, x) = \sum_{n \in \mathbb{N}} (x + n)^p$$ for $$x \in (0, 1)$$ as a Fourier series can be seen also as applying Poisson summation to $$x \mapsto u(x) x^p$$, where $$u$$ is the Heaviside step function. We will unfortunately find that the Fourier coefficient computations over $$x \in (0, 1)$$ fail to converge for $$\Re(p) < -1$$, but this perhaps gives a useful perspective on what is being done with these Fourier methods at other $$p$$ all the same, or on what is being done when we take the Fourier series for $$x \in (\start, \start + 1)$$.)


We'll also define $$\FCoeff{p}{n}{\start}$$ to be $$\int_I F(p, x) e^{-2 \pi i n x} \; dx$$, the analogous formula for $$F$$ rather than $$\zeta$$. Of course, $$\FCoeff{p}{n}{\start}/(p + 1) = \ZetaCoeff{p}{n}{\start}$$ whenever $$p \neq -1$$, so the only reason to bring up $$\FCoeff{p}{n}{\start}$$ is to also be able to discuss $$\FCoeff{-1}{n}{\start}$$. Even this is somewhat pointless, as it is trivial to show that $$F(-1, x) = 1$$ and thus $$\FCoeff{-1}{n}{\start}$$ is zero for nonzero $$n$$, and $$1$$ for $$n = 0$$.
\]

Our previous computation of $$c_0$$ generalizes immediately: For any $$p$$ and $$\start$$, we have $$\ZetaCoeff{p}{0}{\start} = \int_{\start}^{\start + 1} \zeta(-p, x) \; dx = \start^{p + 1}/(p + 1)$$.

(Analogously, $$\FCoeff{p}{0}{\start} = \start^{p + 1}$$ by the exact same reasoning. In particular, in the $$p = -1$$ case, it comes out to $$1$$ regardless of $$\start$$. Note that $$\start^{p + 1}$$ is well-defined for all nonzero $$\start$$ in our domain of bases of exponentiation, but when $$\start = 0$$, this will only be well-defined for $$\Re(p) > -1$$ or $$p = -1$$.)

When $$\Re(p) < 0$$, we may reason as follows to compute $$\ZetaCoeff{p}{n}{\start}$$ for $$n \neq 0$$:

For any natural number $$m$$, we may re-express $$\zeta(-p, x)$$ as $$x^p + (x + 1)^p + \ldots + (x + m - 1)^p + \zeta(-p, x + m)$$, and in this way find $$c_n = \int_{0}^{1} \zeta(-p, x + \start) e^{-2 \pi i n x} \; dx = \left( \int_{0}^{m} (x + \start)^p e^{-2 \pi i n x} \; dx \right) + \left(\int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx \right)$$. Thus, if we can show that $$\lim_{m \to \infty} \int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$, we may conclude that $$c(n, \start) = \int_{0}^{\infty} (x + \start)^p e^{-2 \pi i n x} \; dx $$.

We now take on this task. Note that, via integration by parts or equivalently the product rule for differentiation (specifically, as applied to $$\frac{d}{dx} \zeta(-p, x) e^{-2 \pi i n x}$$), we have that $$\int_{0}^{1} -2 \pi i n \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = -m^p + 2 \pi i n p \int_{0}^{1} \zeta(-(p - 1), x + m) e^{-2 \pi i n x} \; dx$$. Recalling that $$\Re(p) < 0$$, we have that $$\lim_{m \to \infty} m^p = 0$$ and $$\lim_{m \to \infty} \zeta(-(p - 1), x + m) = 0$$. Together with the bounded magnitude of $$e^{-2 \pi i n x}$$, we may conclude that $$\lim_{m \to \infty} \int_{0}^{1} -2 \pi i n \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$. For $$n \neq 0$$, this lets us conclude $$\lim_{m \to \infty} \int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$ as desired.

We have now successfully determined the Fourier coefficients for $$\zeta(-p, x)$$ construed as a function over $$x \in (0, 1)$$, for $$\Re(p) \in (-1, 0)$$: To recap, these are $$c_0 = 0$$ and $$c_n = \int_{0}^{\infty} x^p e^{-2 \pi i n x} \; dx$$ for $$n \neq 0$$.

For $$\Re(p) > 0$$ and $$n \neq 0$$, we can reason as follows to inductively determine $$\ZetaCoeff{p}{n}{\start}$$ from $$\ZetaCoeff{p - 1}{n}{\start}$$:

By integration by parts, $$\int_{0}^{1} -2 \pi i n \zeta(-p, x) e^{-2 \pi i n x} \; dx = 0^p - \int_{0}^{1} \zeta(-(p - 1), x) e^{-2 \pi i n x}$$. Thus, $$\ZetaCoeff{p}{n}{0} = \ZetaCoeff{p - 1}{n}{0}/(2 \pi i n)$$.

We now have the full Fourier series for $$\zeta(-p, x)$$ for any non-integer value for $$\Re(p)$$. In particular, when $$\Re(p) \in (0, 1)$$, we have that $$\ZetaCoeff{p}{n}{0} = (2 \pi i n)^{-1} \int_{0}^{\infty} x^p e^{-2 \pi i n x}$$ for $$n \neq 0$$ and $$\ZetaCoeff{p}{0}{0} = 0$$.

The last thing we might like to do is to analyze the function $$\int_{0}^{\infty} x^p e^{-2 \pi i n x}$$. TODO: Relate this to the Gamma function. Discuss also how this converges just for $$\Re(p) \in (-1, 0)$$ by splitting it in two, and using integration by parts to turn $$x^p$$ into $$x^{p + 1}$$ on the integral containing $$x = 0$$.

TODO: Also discuss the Hurwitz zeta function coefficients at $$\Re(p) = 0$$, finising off determining their values at all $$p$$.

***

Footnotes: