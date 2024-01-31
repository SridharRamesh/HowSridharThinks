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

Furthermore, this $$F(p, x)$$ is complex-differentiable with respect to $$p$$ as well. We define the Hurwitz zeta function $$\zeta(-p, x)$$ for $$p \neq -1$$ as $$F(p, x)/(p + 1)$$. The Riemann zeta function is defined as the special case $$\zeta(-p) = \zeta(-p, 1)$$.

For the Hurwitz zeta function, the above conditions entail:

* $$\displaystyle \lim_{n \to +\infty} \zeta(-p, x + n) = 0$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} \zeta(-p, x) = p \zeta(-(p - 1), x)$$.
* $$\int_{x}^{x + 1} \zeta(-p, x) \; dx = x^{p + 1}/(p + 1)$$.

\[To be pedantically unambiguous, in our domain of interest, we interpret $$x^p$$ for arbitrary $$p$$ via $$\log(x^p) = p \log(x)$$, where $$\log$$ is a logarithm assuming real values on positive inputs and then analytically continued to $$\Re(x) \geq 0$$, $$x \neq 0$$. (We could continue it to even larger domains for $$x$$, but will have no need for this. This punctured closed half-plane is the domain of $$x$$ for our purposes). When $$\Re(p) > 0$$ or $$p = 0$$, we also define $$0^p$$ as $$\lim_{x \to 0} x^p$$ (which is $$0$$ when $$\Re(p) > 0$$ and $$1$$ when $$p = 0$$) and define $$\zeta(-p, 0)$$ as $$\lim_{x \to 0} \zeta(-p, x) = \zeta(-p, 1) + 0^p$$.\]

Each of the conditions which together uniquely define $$F(p, x)$$ is such that $$n^p \sum_{k = 0^}^{n - 1} F(p, (x + k)/n)$$ inherits the same condition. Thus, these two are equal. This is the duplication/multiplication formula. Similarly, $$n^p \sum_{k = 0^}^{n - 1} \zeta(-p, (x + k)/n) = \zeta(-p, x)$$.

## Defining the gamma functions
Although we here at How Sridhar Thinks often prefer to define [the generalized factorial](./FactorialGeneralized.html) by other means, for our purposes here, the following will be the most relevant approach to take:

TODO

## Fourier series for the Hurwitz zeta

Suppose we wish to find the Fourier series for the function $$\zeta(-p, x)$$ restricted to $$x \in (0, 1)$$. That is, the Fourier series for the periodic function $$x \mapsto \zeta(-p, x')$$ where $$x'$$ is the unique value in $$(0, 1)$$ which differs from $$x$$ by an integer (we needn't for now define a value for this periodic function when $$x$$ is itself an integer, though we'll come back to this point later).

The coefficients of the Fourier series are obtained in the usual way, by evaluating $$c_n = \int_{0}^{1} \zeta(-p, x) e^{-2 \pi i n x} \; dx$$ at each integer $$n$$. [We will then obtain the Fourier series $$f(x) = \sum_{n \in \mathbb{Z}} c_n e^{2 \pi i n x}$$, whose properties in terms of convergence to $$\zeta(-p, x)$$ we will discuss later.]

[
As $$\zeta(-p, x)$$ is differentiable with respect to $$x$$ throughout $$x \in (0, 1)$$, this $$f(x)$$ will converge to $$\zeta(-p, x)$$ for such $$x$$. If, furthermore, we have that $$\zeta(-p, 1) = \lim_{x \to 0} \zeta(-p, 0)$$ (as happens when $$\Re(p) > 0$$, because then their difference is $$0^p = 0$$), then $$f(x)$$ will furthermore match $$\zeta(-p, x)$$ at $$x = 0, 1$$ as well.

(For $$\Re(p) < -1$$, expressing $$\zeta(-p, x) = \sum_{n \in \mathbb{N}} (x + n)^p$$ for $$x \in (0, 1)$$ as a Fourier series can be seen also as applying Poisson summation to $$x \mapsto u(x) x^p$$, where $$u$$ is the Heaviside step function.)
]

More generally, it will be useful to us to consider $$\int_I \zeta(-p, x) e^{-2 \pi i n x} \; dx$$ over a general interval $I = (start, start + 1)$. Let us call this $$c(n, start)$$, with $$c_n$$ as $$c(n, 0)$$. Note that $$c(n, start) / e^{-2 \pi i n start}$$ is the $$n$$-th coefficient of the Fourier series for $$\zeta(-p, x)$$ over the interval $$I$$.

The computation of $$c(0, start)$$ is easy: This is $$\int_{start}^{start + 1} \zeta(-p, x) \; dx = start^{p + 1)/(p + 1)$$. In particular, when $$\Re(p) > -1$$, we get $$c(0, 0) = 0$$.

(The analogous $$c(0, start)$$ for $$F(p, x)$$ instead of $$\zeta(-p, x)$$ is of course $$start^{p + 1}$$ simpliciter by the exact same reasoning. In particular, in the $$p = -1$$ case, it comes out to $$1$$ regardless of $$start$$.)

Also, by change of variables and the multiplication formula $$\zeta(-p, x) = n^p \sum_{k = 0^}^{n - 1} \zeta(-p, (x + k)/n)$$ for positive integer $$n$$, we have that $$\int_{start}^{start + 1} \zeta(-p, x) e^{\mp 2 \pi i n x} \; dx$$ $$= n^{-1} \int_{n * start}^{n * start + n} \zeta(-p, x/n) e^{\mp 2 \pi i x} \; dx$$ $$= n^{-1} \sum_{k = 0}^{n - 1} \int_{n * start + k}^{n * start + k + 1} \zeta(-p, x/n) e^{\mp 2 \pi i x} \; dx$$ $$= n^{-p - 1} \int_{n * start}^{n * start + 1} \zeta(-p, x) e^{\mp 2 \pi i x} \; dx$$. Thus, $$c(\pm n, start) = c(\pm 1, n * start) n^{-p - 1}$$. In particular, $$c_{\pm n} = c_{\pm 1} n^{-p - 1}$$.

What remains is only to compute $$c(\pm 1, start}$$. Also, on conjugation-symmetry grounds (i.e., interchanging $$i$$ and $$-i$$ everywhere), it is clearly the case that $$c(-1, start)$$ for a particular power $$p$$ is the conjugate of $$c_1$$ for the conjugate power and conjugation of $$start$$. So really, we only need to figure out a formula for $$c(1, start)$$.

When $$\Re(p) < 0$$, we may reason as follows to compute $$c(n, start)$$ for $$n \neq 0$$:

For any natural number $$m$$, we may re-express $$\zeta(-p, x)$$ as $$x^p + (x + 1)^p + \ldots + (x + m - 1)^p + \zeta(-p, x + m)$$, and in this way find $$c_n = \int_{0}^{1} \zeta(-p, x + start) e^{-2 \pi i n x} \; dx = \left( \int_{0}^{m} (x + start)^p e^{-2 \pi i n x} \; dx \right) + \left(\int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx \right)$$. Thus, if we can show that $$\lim_{m \to \infty} \int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$, we may conclude that $$c(n, start) = \int_{0}^{\infty} (x + start)^p e^{-2 \pi i n x} \; dx $$.

We now take on this task. Note that, via integration by parts or equivalently the product rule for differentiation (specifically, as applied to $$\frac{d}{dx} \zeta(-p, x) e^{-2 \pi i n x}$$), we have that $$\int_{0}^{1} -2 \pi i n \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = -m^p + 2 \pi i n p \int_{0}^{1} \zeta(-(p - 1), x + m) e^{-2 \pi i n x} \; dx$$. Recalling that $$\Re(p) < 0$$, we have that $$\lim_{m \to \infty} m^p = 0$$ and $$\lim_{m \to \infty} \zeta(-(p - 1), x + m) = 0$$. Together with the bounded magnitude of $$e^{-2 \pi i n x}$$, we may conclude that $$\lim_{m \to \infty} \int_{0}^{1} -2 \pi i n \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$. For $$n \neq 0$$, this lets us conclude $$\lim_{m \to \infty} \int_{0}^{1} \zeta(-p, x + m) e^{-2 \pi i n x} \; dx = 0$$ as desired.

We have now successfully determined the Fourier coefficients for $$\zeta(-p, x)$$ construed as a function over $$x \in (0, 1)$$, for $$\Re(p) \in (-1, 0)$$: To recap, these are $$c_0 = 0$$ and $$c_n = \int_{0}^{\infty} x^p e^{-2 \pi i n x} \; dx$$ for $$n \neq 0$$.

Let $$\Gamma(p + 1) = \int_{0}^{\infty} x^p e^{-x} \; dx$$. Note that by rescaling change of variables \[TODO: Invoking analyticity of the Laplace transform throughout its region of absolute convergence, as this an imaginary rescaling factor\], we have that $$c_n$$ is $$(2 \pi i n)^{-(p + 1)} \Gamma(p + 1)$$, for $$n \neq 0$$.

TODO: Extend now these same $$c_n$$ formulas to the Fourier series for $$\Re(p) \in (0, 1)$$ [and indeed, $$\Re(p) > -1$$ in general], via the differentiation rule for Fourier series or equivalently integration by parts (this gives us the Fourier series at $$\Re(p) > - 1$$ when $$\Re(p)$$ is not an integer; we presumably may use continuity arguments to handle the case where $$\Re(p)$$ is an integer). Conclude by looking at any particular interval where $$\Re(p) > 0$$ (so that the Fourier series actually converges at the boundary of its interval) that we have the Hurwitz functional equation, of which the Riemann functional equation is a special case.