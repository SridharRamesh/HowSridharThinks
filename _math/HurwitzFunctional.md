---
title: "The Hurwitz and Riemann functional equations"
date: 2024-1-29
---
Where the celebrated "functional equation" for the Riemann zeta function comes from, as well as for the Hurwitz zeta function more generally. I believe the approach here is cleaner and better motivated than either the contour integration or theta function approaches people usually give, which seem to me a long mess of magic calculation. I think the approach here should make the functional equation even obvious, in hindsight.

## Defining the zeta functions

Recall from our previous discussion of [difference equations](./DifferenceEquationZeta.html) that there is a unique function $$F(p, x)$$ such that we have: $$\newcommand{\nat}{\mathbb{N}}$$
* $$\displaystyle \lim_{n \to +\infty} F(p, x + n) = 0$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} F(p, x) = (p + 1)F(p - 1, x)$$.
* $$\int_{x}^{x + 1} F(p, x) \; dx = x^{p + 1}$$.

<!-- Periods included above to get the typesetting to not do weird things with math in a bulleted list where some items are mixed with non-math and others aren't. -->

Furthermore, this $$F(p, x)$$ is complex-differentiable with respect to $$p$$ as well. We define the Hurwitz zeta function $$\zeta(-p, x)$$ for $$p \neq -1$$ as $$F(p, x)/(p + 1)$$. The Riemann zeta function is defined as the special case $$\zeta(-p) = \zeta(-p, 1)$$.

For the Hurwitz zeta function, the above conditions entail:

* $$\displaystyle \lim_{n \to +\infty} \zeta(-p, x + n) = 0$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} \zeta(-p, x) = p \zeta(-(p - 1), x)$$.
* $$\int_{x}^{x + 1} \zeta(-p, x) \; dx = x^{p + 1}/(p + 1)$$.

\[To be pedantically unambiguous, in our domain of interest, we interpret $$x^p$$ for arbitrary $$p$$ via $$\log(x^p) = p \log(x)$$, where $$\log$$ is a logarithm assuming real values on positive inputs and then analytically continued to $$\Re(x) \geq 0$$, $$x \neq 0$$. (We could continue it to even larger domains for $$x$$, but will have no need for this. This punctured closed half-plane is the domain of $$x$$ for our purposes). When $$\Re(p) > 0$$ or $$p = 0$$, we also define $$0^p$$ as $$\lim_{x \to 0} x^p$$ (which is $$0$$ when $$\Re(p) > 0$$ and $$1$$ when $$p = 0$$) and define $$\zeta(-p, 0)$$ as $$\lim_{x \to 0} \zeta(-p, x) = \zeta(-p, 1) + 0^p$$.\]

## Defining the zeta functions
Although we here at How Sridhar Thinks often prefer to define [the generalized factorial](./FactorialGeneralized.html) by other means, for our purposes here, the following will be the most relevant approach to take:

Consider the integral $$\Gamma(p + 1, start, end, s) = \int_{start}^{end} t^p s^{p + 1} e^{s t} \; dt$$. Note how, for any positive rescaling factor $$k$$, by basic change of variables from $$t$$ to $$kt$$, we have that $$\Gamma(p + 1, start, end, sk) = \Gamma(p + 1, start/k, end/k, s)$$.

## Fourier series for the Hurwitz zeta

Suppose we wish to find the Fourier series for the function $$\zeta(-p, x)$$ restricted to $$x \in (0, 1)$$. That is, the Fourier series for the periodic function $$x \mapsto \zeta(-p, x')$$ where $$x'$$ is the unique value in $$(0, 1)$$ which differs from $$x$$ by an integer (we needn't for now define a value for this periodic function when $$x$$ is itself an integer, though we'll come back to this point later).

The coefficients of the Fourier series are obtained in the usual way, by evaluating $$\int_{0}^{1} \zeta(-p, x + start) e^{-2 \pi i n x} \; dx$$ at each integer $$n$$.

More generally, it will be useful to us to consider $$\int_I \zeta(-p, x + start) e^{-2 \pi i n x} \; dx$$ over a general interval $I = (start, start + 1)$. These will be proportional to 

Let us call this $$c(n, start)$$. We will use $$c_n$$ as shorthand for $$c(n, 0)$$.

We will then obtain the Fourier series $$f(x) = \sum_{n \in \mathbb{Z}} c_n e^{2 \pi i n x}$$. As $$\zeta(-p, x)$$ is differentiable with respect to $$x$$ throughout $$x \in (0, 1)$$, this $$f(x)$$ will converge to $$\zeta(-p, x)$$ for such $$x$$. If, furthermore, we have that $$\zeta(-p, 1) = \lim_{x \to 0} \zeta(-p, 0)$$ (as happens when $$\Re(p) > 0$$, because then their difference is $$0^p = 0$$), then $$f(x)$$ will furthermore match $$\zeta(-p, x)$$ at $$x = 0, 1$$ as well.

(For $$\Re(p) < -1$$, expressing $$\zeta(-p, x) = \sum_{n \in \mathbb{N}} (x + n)^p$$ for $$x \in (0, 1)$$ as a Fourier series can be seen also as applying Poisson summation to $$x \mapsto u(x) x^p$$, where $$u$$ is the Heaviside step function.)

The computation of $$c(0, start)$$ is easy: This is $$\int_{0}^{1} \zeta(-p, x + start) \; dx = \frac{\zeta(-(p + 1), start + 1) - \zeta(-(p + 1), start)}{p + 1} = \frac{-start^{p + 1}}{p + 1}$$. In particular, when $$\Re(p) > -1$$, we get $$c(0, 0) = 0$$.

When $$\Re(p) < 0$$, we may reason as follows to compute $$c(n, start)$$ for $$n \neq 0$$:

For any natural number $$m$$, we may re-express $$\zeta(-p, x)$$ as $$x^p + (x + 1)^p + \ldots + (x + m - 1)^p + \zeta(-p, x + m)$$, and in this way find $$c_n = \int_{0}^{1} \zeta(-p, x + start) e^{-2 \pi i n x} \; dx = \left( \int_{0}^{m} (x + start)^p e^{-2 \pi i n x} \; dx \right) + \left(\int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx \right)$$. Thus, if we can show that $$\lim_{m \to \infty} \int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$, we may conclude that $$c(n, start) = \int_{0}^{\infty} (x + start)^p e^{-2 \pi i n x} \; dx $$.

We now take on this task. Note that, via integration by parts or equivalently the product rule for differentiation (specifically, as applied to $$\frac{d}{dx} \zeta(-p, x) e^{-2 \pi i n x}$$), we have that $$\int_{0}^{1} -2 \pi i n \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = -m^p + 2 \pi i n p \int_{0}^{1} \zeta(-(p - 1), x + m) e^{-2 \pi i n x} \; dx$$. Recalling that $$\Re(p) < 0$$, we have that $$\lim_{m \to \infty} m^p = 0$$ and $$\lim_{m \to \infty} \zeta(-(p - 1), x + m) = 0$$. Together with the bounded magnitude of $$e^{-2 \pi i n x}$$, we may conclude that $$\lim_{m \to \infty} \int_{0}^{1} -2 \pi i n \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$. For $$n \neq 0$$, this lets us conclude $$\lim_{m \to \infty} \int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$ as desired.

We have now successfully determined the Fourier coefficients for $$\zeta(-p, x)$$ construed as a function over $$x \in (0, 1)$$, for $$\Re(p) \in (-1, 0)$$: To recap, these are $$c_0 = 0$$ and $$c_n = \int_{0}^{\infty} x^p e^{-2 \pi i n x} \; dx$$ for $$n \neq 0$$.

Let $$\Gamma(p + 1) = \int_{0}^{\infty} x^p e^{-x} \; dx$$. Note that by rescaling change of variables \[TODO: Invoking analyticity of the Laplace transform throughout its region of absolute convergence, as this an imaginary rescaling factor\], we have that $$c_n$$ is $$(2 \pi i n)^{-(p + 1)} \Gamma(p + 1)$$, for $$n \neq 0$$.

TODO: Extend now these same $$c_n$$ formulas to the Fourier series for $$\Re(p) \in (0, 1)$$ [and indeed, $$\Re(p) > -1$$ in general], via the differentiation rule for Fourier series or equivalently integration by parts (this gives us the Fourier series at $$\Re(p) > - 1$$ when $$\Re(p)$$ is not an integer; we presumably may use continuity arguments to handle the case where $$\Re(p)$$ is an integer). Conclude by looking at any particular interval where $$\Re(p) > 0$$ (so that the Fourier series actually converges at the boundary of its interval) that we have the Hurwitz functional equation, of which the Riemann functional equation is a special case.