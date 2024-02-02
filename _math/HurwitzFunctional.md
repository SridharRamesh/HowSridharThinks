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

Observe that, when $$\Re(p) > 0$$, we have that $$\zeta(-p, 0) = \zeta(-p, 1)$$. Thus, we can make a continuous periodic function $$x \mapsto \zeta(-p, x')$$ on real $$x$$, where $$x'$$ is the unique value in $$(0, 1]$$ which differs from $$x$$ by an integer. This function will furthermore be differentiable in both directions at every point (though these two derivatives won't match at integer inputs).

Such bidifferentiable periodic functions admit Fourier series which converge everywhere to them. That is, extracting Fourier coefficients in the usual way as $$c_n = \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i n x} \; dx$$ and then stringing them together as the Fourier series[^FourierConditional] $$f(x) = \sum_{n \in \mathbb{Z}} c_n e^{2 \pi i n x}$$, we will have that $$\zeta(-p, x) = f(x)$$.

[^FourierConditional]: Where the infinite sum is interpreted in case of conditional convergence via partial sums extending equally into negative and positive indices.

\[
In a naive sense, $$\zeta(-p, x) \approx \sum_{m \in \mathbb{N}} (x + m)^p$$, and thus $$\int_{0}^{1} \zeta(-p, x) e^{-2 \pi i n x} \; dx \approx \sum_{m \in \mathbb{N}} \int_{m}^{m + 1} (x + m)^p e^{-2 \pi i n x} \; dx = \int_{0}^{\infty} x^p e^{-2 \pi i n x} \; dx $$. Taking these as the coefficients of the Fourier series for $$\zeta(-p, x)$$ over $$x \in (0, 1)$$ would amount to applying Poisson summation to $$x \mapsto u(x) x^p$$, where $$u$$ is the Heaviside step function. The Hurwitz zeta function is only actually this sum where $$\Re(p) < -1$$, and unfortunately, we will find that this integal and thus the Fourier coefficient computations over $$x \in (0, 1)$$ fail to converge for $$\Re(p) < -1$$. But this perhaps gives a useful perspective on what we are doing with our Fourier methods at other $$p$$ all the same, or on what is being done when we take the Fourier series for $$\zeta(-p, x)$$ over some other unit interval not starting at zero.
\]

The computation of $$c_0$$ is straightforward: $$\int_{0}^{1} \zeta(-p, x) dx = 0^p/(p + 1) = 0$$, given our presumption that $$\Re(p) > 0$$ (indeed, this holds even if $$\Re(p) > -1$$).

Also, for positive integer $$n$$, by change of variables and the multiplication formula $$\zeta(-p, x) = n^p \sum_{k = 0}^{n - 1} \zeta(-p, (x + k)/n)$$, we have that $$\int_{0}^{1} \zeta(-p, x) e^{\mp 2 \pi i n x} \; dx$$ $$= n^{-1} \int_{0}^{n} \zeta(-p, x/n) e^{\mp 2 \pi i x} \; dx$$ $$= n^{-1} \sum_{k = 0}^{n - 1} \int_{k}^{k + 1} \zeta(-p, x/n) e^{\mp 2 \pi i x} \; dx$$ $$= n^{-1 - p} \int_{0}^{1} \zeta(-p, x) e^{\mp 2 \pi i x} \; dx$$. Thus, $$c_{\pm n} = c_{\pm 1} n^{-1 - p}$$. [The reasoning of this paragraph applies for arbitrary $$p$$, not just $$\Re(p) > 0$$. It also applies equally well to the analogous Fourier coefficients for $$F(p, x)$$ including at $$p = -1$$.]

Thus, we have that $$\zeta(-p, x) = (c_1 + c_{-1}) \sum_{n \in \mathbb{N}} n^{-1 - p} e^{2 \pi i n x}$$ for $$x \in [0, 1]$$. In particular, at the endpoints, we have $$\zeta(-p) = (c_1 + c_{-1}) \zeta(-(-1 - p))$$. These are the Hurwitz and Riemann zeta functional equations. We've established this in the regime $$\Re(p) > 0$$, but presuming the expressions for $$c_1$$ and $$c_{-1}$$ extend meromorphically to all $$p$$, the Riemann functional equation will then extend by meromorphic continuation to hold for all $$p$$.

What remains is only to find formulas for $$c_1$$ and $$c_{-1}$$, in terms of $$p$$. (By conjugation symmetry, the value of $$c_{-1}$$ for a given $$p$$ will just be the conjugate of $$c_1$$ for the conjugate of $$p$$, so our remaining task in establishing the functional equation is really just to find a formula for $$c_1$$ in terms of $$p$$, in the range where $$\Re(p) > 0$$ or even just any interval within that range.)

Note also that, when $$\Re(p) > 0$$ so that $$0^p = 0$$, we have by integration by parts that $$-2 \pi i \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i x} \; dx = -p \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i x} \; dx$$. Thus, $$k (2 \pi i)^{-p} \ZetaCoeff{p}{1}{0}$$ satisfies the factorial recurrence, for any constant $$k$$.

Let us determine an initial value for this too. What is $$\ZetaCoeff{0}{1}{0}$$? TODO.

Thus, our goal now is to study $$\int_{0}^{1} \zeta(-p, x) e^{-2 \pi i x} \; dx$$ as a function of $$p$$.

As noted above, this is naively something like $$\int_{0}^{\infty} x^p e^{-2 \pi i x} \; dx$$. But this doubly improper integral is a pain. For example, there are no $$p$$ for which it is absolutely convergent. This integral is absolutely convergent near $$x = 0$$ just in case $$\Re(p) > - 1$$, but absolutely convergent near $$x = \infty$$ just in case $$\Re(p) < -1$$.

It is convenient therefore to split this $$\int_{0}^{\infty} x^p$$ into $$\int_{0}^{m} x^p + \int_{m}^{\infty} x^p$$ for some arbitrary $$0 < m < \infty$$, so that we could hope to use integration by parts in separate directions on these, to bring $$p$$ up or down into the range where it has good behavior.

In keeping with this spirit, using the recurrence $$\zeta(-p, x) = x^p + \zeta(-p, x + 1)$$, let us reinterpret $$\int_{0}^{1} \zeta(-p, x) e^{-2 \pi i x} \; dx$$ as $$\left( \int_{0}^{1} x^p \; e^{-2 \pi i x} \; dx \right) + \left( \int_{1}^{2} \zeta(-p, x) e^{-2 \pi i x} \; dx \right)$$. This is a special case of $$\left( \int_{0}^{m} x^p \; e^{-2 \pi i x} \; dx \right) + \left( \int_{m}^{m + 1} \zeta(-p, x) e^{-2 \pi i x} \; dx \right)$$, but by differentiating this last expression with respect to $$m$$, we find it is constant; that is, the choice of $$m$$ does not matter.

Let us now write $$\gamma_m(p) = \int_{0}^{m} x^p e^{-2 \pi i x} \; dx$$ and $$\Gamma_m(p) = \int_{m}^{m + 1} \zeta(-p, x) e^{-2 \pi i x} \; dx$$, for $$0 < m < \infty$$, and study the behavior of these two as functions of $$p$$, both separately and summed together.

\[
These are closely related to what are called the lower and upper incomplete gamma functions, but though their forms are clearly related, the simple equation relating them is not entirely straightforward to prove!
\]

Observe that integration by parts gives us $$-2 \pi i \Gamma_m(p) = -m^p - p \Gamma_m(p - 1)$$. (This holds for all $$p \neq 0, -1$$. More generally, we have for all $$p$$ that $$-2 \pi i \int_{0}^{1} F(p, x) e^{-2 \pi i x} \; dx = -(p + 1)m^p - (p + 1) \int_{0}^{1} F(p - 1, x) e^{-2 \pi i x} \; dx$$.)

Similarly, when $$\Re(p) > 0$$ so that $$0^p = 0$$, integration by parts gives us $$-2 \pi i \gamma_m(p) = m^p - p \gamma_m(p - 1)$$.

This motivates defining $$G(p) = k (2 \pi i)^{-p} (\gamma_m(p) + \Gamma_m(p))$$ for an as yet unspecified constant $$k$$ and observing that, when $$\Re(p) > 0$$, we have that $$G(p) = p G(p - 1)$$. I.e., $$G$$ satisfies the factorial recurrence.

Let us choose $$k$$ such that $$G(0) = 1$$ like the factorial too. Note that, for positive integer $$m$$, we have $$\gamma_m(0) = \int_{0}^{m} e^{-2 \pi i x} \; dx = 0$$. On the other hand, we can quickly establish that $$\zeta(-0, x) = -x + 1/2$$, and thus $$\Gamma_m(0) = \int_{0}^{1} (-x + 1/2) e^{-2 \pi i x) \; dx$$. By integration by parts differentiating TODO.

Finally, let us investigate the asymptotics of this $$G$$. TODO

TODO: Also discuss the Hurwitz zeta function coefficients at all other $$p$$ or for all other $$\start$$ values.

***

Footnotes: