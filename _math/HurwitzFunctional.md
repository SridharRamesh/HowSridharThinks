---
title: "The Hurwitz and Riemann functional equations"
date: 2024-1-29
---
Where the celebrated "functional equation" for the Riemann zeta function comes from, as well as for the Hurwitz zeta function more generally. I believe the approach here is cleaner and better motivated than either the contour integration or theta function approaches people usually give, which seem to me a long mess of magic calculation[^ProofEquivalence]. I think the approach here should make the functional equation even obvious, in hindsight.

[^ProofEquivalence]: Though our argument for the functional equation is probably equivalent to the theta function argument in some sense I have not yet worked out, given that it also uses an integral from 0 to infinity split apart at 1. I might imagine the contour integral approach is similar as well, on the general heuristic that often there is only one real proof of a thing presented many different ways, but I'm not currently fluent with how the contour integral argument goes.

## Defining the zeta functions

Recall from our previous discussion of [difference equations](./DifferenceEquationZeta.html) that there is a unique complex-valued function $$\zeta(-p, x)$$ defined at all complex $$-p \neq -1$$ and all complex $$x$$ with $$\Re(x) \geq 0$$, $$x \neq 0$$ such that we have: $$\newcommand{\nat}{\mathbb{N}}$$
* $$\lim_{n \to +\infty} \zeta(-p, x + n) = 0$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} \zeta(-p, x) = p \zeta(-(p - 1), x)$$.
* $$\zeta(-p, x) - \zeta(-p, x + 1) = x^p$$.

<!-- Periods included above to get the typesetting to not do weird things with math in a bulleted list where some items are mixed with non-math and others aren't. -->

Furthermore, this $$\zeta(-p, x)$$ is complex-differentiable with respect to $$p$$ as well. The Riemann zeta function is defined as the special case $$\zeta(-p) = \zeta(-p, 1)$$.

\[To be pedantically unambiguous, in our domain of interest, we interpret $$x^p = \exp(p \log(x))$$ by taking $$\log$$ as the natural logarithm assuming real values on positive inputs and then analytically continued to $$\Re(x) \geq 0$$, $$x \neq 0$$. (We could continue it to even larger domains for $$x$$, but will have no need for this. This punctured closed half-plane is the domain of $$x$$ for our purposes). We may occasionally in the following also speak of $$0^p$$ or $$\zeta(-p, 0)$$ when $$\Re(p) > 0$$ or $$p = 0$$, as abuse of notation for the corresponding limit as $$x$$ approaches $$0$$.\]

## Fourier series for the Hurwitz zeta

Suppose we wish to find the Fourier series for the function $$\zeta(-p, x)$$ restricted to $$x \in [0, 1]$$. That is, the Fourier series for the periodic function $$x \mapsto \zeta(-p, x')$$ where $$x'$$ is the unique value in $$(0, 1]$$ which differs from $$x$$ by an integer.

The coefficients of the Fourier series are obtained in the usual way, by evaluating $$c_n = \int_0^1 \zeta(-p, x) e^{-2 \pi i n x} \; dx$$ at each integer $$n$$. We will then obtain the Fourier series $$f(x) = \sum_{n \in \mathbb{Z}} c_n e^{2 \pi i n x}$$. As $$\zeta(-p, x)$$ is differentiable with respect to $$x$$ throughout $$x \in (0, 1)$$, this $$f(x)$$ will converge to $$\zeta(-p, x)$$ for such $$x$$. If, furthermore, we have that $$\zeta(-p, 1) = \lim_{x \to 0} \zeta(-p, 0)$$ (as happens when $$\Re(p) > 0$$, because then their difference is $$0^p = 0$$), then $$f(x)$$ will furthermore match $$\zeta(-p, x)$$ at $$x = 0, 1$$ as well.

(For $$\Re(p) < -1$$, expressing $$\zeta(-p, x) = \sum_{n \in \mathbb{N}} (x + n)^p$$ for $$x \in in (0, 1]$$ as a Fourier series can be seen also as applying Poisson summation to $$x \mapsto u(x) x^p$$, where $$u$$ is the Heaviside step function.)

When $$\Re(p) \in (-1, 0)$$, we may reason as follows:

The $$c_0$$ coefficient for $$\zeta(-p, x)$$ is easy: This is $$\int_{0}^{1} \zeta(-p, x) \; dx = \frac{\zeta(-(p + 1), 1) - \zeta(-(p + 1), 0)}{p + 1} = \frac{-0}{p + 1} = 0$$. But figuring out the $$c_n$$ for $$n \neq 0$$ will require a different approach.

For any natural numbers $$m$$, we may re-express $$\zeta(-p, x)$$ as $$x^p + (x + 1)^p + \ldots + (x + m - 1)^p + \zeta(-p, x + m)$$, and in this way find $$\int_{0}^{1} \zeta(-p, x) e^{-2 \pi i n x} \; dx = \left( \int_{0}^{m} x^p e^{-2 \pi i n x} \; dx \right) + \left(\int_{m}^{m + 1} \zeta(-p, x) e^{-2 \pi i n x} \; dx \right)$$. Thus, if we can show that $$\lim_{m \to 0} \int_{m}^{m + 1} \zeta(-p, x) e^{-2 \pi i n x} \; dx = 0$$, we may conclude that $$c_n = \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i n x} \; dx = \int_{0}^{\infty} x^p e^{-2 \pi i n x} \; dx $$.

We now take on this task. Note that, via integration by parts or equivalently the product rule for differentiation (specifically, as applied to $$\frac{d}{dx} \zeta(-p, x) e^{-2 \pi i n x}$$), we have that $$\int_{m}^{m + 1} -2 \pi i n \zeta(-p, x) e^{-2 \pi i n x} \; dx = -m^p + 2 \pi i n p \int_{m}^{m + 1} \zeta(-(p - 1), x) e^{-2 \pi i n x} \; dx$$. Recalling that $$\Re(p) < 0$$, we have that $$\lim_{m \to \infty} m^p = 0$$ and $$\lim_{m \to \infty} \zeta(-(p - 1), x + m) = 0$$. Together with the bounded magnitude of $$e^{-2 \pi i n x}$$, we may conclude that $$\lim_{m \to \infty} \int_{m}^{m + 1} -2 \pi i n \zeta(-p, x) e^{-2 \pi i n x} \; dx = 0$$. For $$n \neq 0$$, this lets us conclude $$\lim_{m \to \infty} \int_{m}^{m + 1} \zeta(-p, x) e^{-2 \pi i n x} \; dx = 0$$ as desired.

We have now successfully determined the Fourier coefficients for $$\zeta(-p, x)$$, construed as a function over $$x \in (0, 1]$$, with $$\Re(p) \in (-1, 0)$$: To recap, these are $$c_0 = 0$$ and $$c_n = \int_{0}^{\infty} x^p e^{-2 \pi i n x} \; dx$$ for $$n \neq 0$$.

Let $$\Gamma(p + 1) = \int_{0}^{\infty} x^p e^(-x) \; dx$$. Note that by rescaling change of variables \[TODO: Invoking analyticity of the Laplace transform throughout its region of absolute convergence, as this a complex rescaling factor\], we have that $$c_n$$ is $$(2 \pi i n)^(-1 - p) c_1$$, for $$n \neq 0$$.

TODO: Extend now to the Fourier series for $$\Re(p) \in (0, 1)$$ [and indeed, $$\Re(p) > -1$$ in general]. Conclude by looking at any particular interval where $$\Re(p) > 0$$ (so that the Fourier series actually converges at the boundary of its interval) that we have the Hurwitz functional equation, of which the Riemann functional equation is a special case.

***

In the same manner, one can derive also functional equations for the Lerch zeta function, but I do not care to write that out right now. I do not think it will be any more illuminating than what has already been shown above.

***

Footnotes: