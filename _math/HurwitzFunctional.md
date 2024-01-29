---
title: "The Hurwitz and Riemann functional equations"
date: 2024-1-26
---
Where the celebrated "functional equation" for the Riemann zeta function comes from, as well as for the Hurwitz zeta function more generally. I believe the approach here is cleaner and better motivated than either the contour integration or theta function approaches people usually give, which seem to me a long mess of magic calculation[^ProofEquivalence]. I think the approach here should make the functional equation even obvious, in hindsight.

[^ProofEquivalence]: Though our argument for the functional equation is probably equivalent to the theta function argument in some sense I have not yet worked out, given that it also uses an integral from 0 to infinity split apart at 1. I might imagine the contour integral approach is similar as well, on the general heuristic that often there is only one real proof of a thing presented many different ways, but I'm not currently fluent with how the contour integral argument goes.

## Defining the zeta functions

Recall from our previous discussion of [difference equations](./DifferenceEquationZeta.html) that there is a unique complex-valued function $$\zeta(-p, x)$$ defined at all complex $$-p \neq -1$$ and all complex $$x$$ with $$\Re(x) \geq 0$$, $$x \neq 0$$ such that we have: $$\newcommand{\nat}{\mathbb{N}}$$
* $$\zeta(-p, x) = \sum_{n \in \nat} (x + n)^p$$ whenever $$\Re(p) < -1$$.
* $$\frac{d}{dx} \zeta(-p, x) = p \zeta(-(p - 1), x)$$.
* $$\zeta(-p, x) - \zeta(-p, x + 1) = x^p$$.

<!-- Periods included above to get the typesetting to not do weird things with math in a bulleted list where some items are mixed with non-math and others aren't. -->

Furthermore, this $$\zeta(-p, x)$$ is complex-differentiable with respect to $$p$$ as well. The Riemann zeta function is defined as the special case $$\zeta(-p) = \zeta(-p, 1)$$.

\[To be pedantically unambiguous, in our domain of interest, we interpret $$x^p = \exp(p \log(x))$$ by taking $$\log$$ as the natural logarithm assuming real values on positive inputs and then analytically continued to $$\Re(x) \geq 0$$, $$x \neq 0$$. (We could continue it to even larger domains for $$x$$, but will have no need for this. This punctured closed half-plane is the domain of $$x$$ for our purposes). We may occasionally in the following also speak of $$0^p$$ or $$\zeta(-p, 0)$$ when $$\Re(p) > 0$$ or $$p = 0$$, as abuse of notation for the corresponding limit as $$x$$ approaches $$0$$.\]

## Fourier series for the Hurwitz zeta

Note that, for $$\Re(p) > 0$$, we have $$\zeta(-p, 0) = \zeta(-p, 1)$$ as their difference is $$0^p = 0$$.

Suppose now that we wish to find the Fourier series for the function $$\zeta(-p, x)$$ restricted to $$x \in [0, 1]$$. That is, the Fourier series for the periodic function $$x \mapsto \zeta(-p, x')$$ where $$x'$$ is the unique value in $$(0, 1]$$ which differs from $$x$$ by an integer.

The coefficients of the Fourier series are obtained in the usual way, by evaluating $$c_n = \int_0^1 \zeta(-p, x) e^{-2 \pi i n x} \; dx$$ at each integer $$n$$. We will then obtain the Fourier series $$f(x) = \sum_{n \in \mathbb{Z}} c_n e^{2 \pi i n x}$$. If $$\zeta(-p, x)$$ is differentiable with respect to $$x$$ throughout $$x \in (0, 1]$$, with $$\zeta(-p, 1) = \lim_{x \to 0} \zeta(-p, 0)$$, then $$f(x)$$ will match $$\zeta(-p, x)$$ for each $$x in (0, 1]$$.

(For $$\Re(p) < -1$$, expressing $$\zeta(-p, x) = \sum_{n \in \mathbb{N}} (x + n)^p$$ for $$x \in in (0, 1]$$ as a Fourier series can be seen also as applying Poisson summation to $$x \mapsto u(x) x^p$$, where $$u$$ is the Heaviside step function.)

When $$\Re(p) \in (-1, 0)$$, we may reason as follows:

The $$c_0$$ coefficient for $$\zeta(-p, x)$$ is easy: This is $$\int_{0}^{1} \zeta(-p, x) \; dx = \frac{\zeta(-(p + 1), 1) - \zeta(-(p + 1), 0)/(p + 1)} = \frac{-0)}{p + 1} = 0$$. But figuring out the $$c_n$$ for $$n \neq 0$$ will require a different approach.

Let $$n \neq 0$$ be an integer. We will observe that $$\int_{t = m}^{\infinity} t^p e^{-2 \pi i n t} \; dt$$ and $$\int_{t = m}^{m + 1} \zeta(-p, t) e^{-2 \pi i n t} \; dt$$ agree for all values of $$m$$. Observe that differentiating either of these with respect to $$m$$ yields $$-m^p e^{-2 \pi i n m} = (\zeta(-p, m + 1) - \zeta(-p, m)) e^{-2 \pi i n m}$$. Having the same derivative, these expressions differ by a constant (with respect to $$m$$). Now consider the limit as $$m \to \infty$$. $$\int_{t = m}^{\infinity} t^p e^{-2 \pi i n t} \; dt$$ manifestly goes to zero in this limit, by definition of such an improper integral. On the other hand, TODO.

 We can apply integration by parts to both sides to derive their values from differentiating the $$t^p$$ or $$\zeta(-p, t)$$ terms. In either case, we get the same discrepancy in the integration by parts when dealing with the value of the integrand at the bounds (as $$m^p - \infinity^p = m^p = \zeta(-p, m) - \zeta(-p, m + 1)$$, which then multiplies by $$e^{-2 \pi i n m} / (-2 \pi i n}$$ to become the discrepancy). Apart from that, the integration by parts brings us to considering the equation $$(p + 1) \int_{t = m}^{\infinity} t^(p - 1) e^{-2 \pi i n t} \; dt = (p + 1)\int_{t = m}^{m + 1} \zeta(-p - 1, t) e^{-2 \pi i n t} \; dt$$, which is manifestly true by expanding $$\zeta(-p - 1, t)$$ as an absolutely convergent series.

Adding to either integrand $$\int_{t = m - 1}^{m} t^p e^{-2 \pi i n t} \; dt$$ now effectively reduces $$m$$ by one (this is obvious for the left hand side, while on the right hand side, we can re-index $$\zeta(-p, t)$$ from $$m$$ to $$m + 1$$ into $$\zeta(-p, t + 1)$$ from $$m - 1$$ to $$m$$, and then use the relation $$\zeta(-p, t) = $$\zeta(-p, t + 1)$$ + t^p$$). This works even if $$m$$ was $$1$$ to begin with, so we can get all the way down to $$m = 0$$ by this technique (the reason we could not start with $$m = 0$$ above is because we had to invoke $$m^p$$ in dealing with the integration by parts' discrepancy at the bounds, which will not be defined when $$m = 0$$).

Thus, at $$m = 0$$, we may conclude that $$\int_{t = 0}^{1} \zeta(-p, t) e^{-2 \pi i n t} \; dt = \int_{t = 0}^{\infinity} t^p e^{-2 \pi i n t} \; dt$$ (again, this only for $$n \neq 0$$, while for $$n = 0$$ we get a zero result). This completes the calculation of the Fourier coefficients.

Note that by rescaling, this value $$\int_{t = 0}^{\infinity} t^p e^{-2 \pi i n t} \; dt$$ is $$n^(-1 - p)$$ times the value at $$n = 1$$.

***

To be deleted:

We shall show that for $$n \neq 0$$, we have that $$\int_{x = 0}^{1} \zeta(-p, x) e^{-2 \pi i n x} \; dx = \int_{x = 0}^{\infinity} x^p e^{-2 \pi i n x} \; dx$$. This is what we might have naively expected from thinking of the Hurwitz zeta function as an infinite sum, even though it is not strictly an infinite sum in this regime (and indeed, this equation would not be true for $$n = 0$$, where the integral on the left goes to zero while the integral on the right diverges to infinity).

We split $$\int_{x = 0}^{\infinity} x^p e^{-2 \pi i n x} \; dx$$ into integrals from $$0$$ to $$1$$ and from $$1$$ to $$\infinity$$.

We then study $$\int_{x = 1}^{\infinity} x^p e^{-2 \pi i n x} \; dx$$ by integration by parts TODO

$$\zeta(-p, x) = x^p + \zeta(-p, x + 1)$$. So the Fourier series for $$\zeta(-p, x)$$ is the sum of those for $$x^p$$ and $$\zeta(-p, x + 1)$$.

The $$\zeta(-p, x + 1$$ part would be easier to handle if we replaced $$p$$ by $$p - 1 \in (-2, -1)$$. We can carry out this switch via the rule for Fourier series of antiderivatives/derivatives (equivalently, integration by parts).

By decomposing $$x \mapsto \zeta(-(p - 1), x)$$ as an infinite sum, we see that the $$c_n$$ coefficient for $$p \zeta(-(p - 1), x + 1)$$ is given by the integral $$p \int_{t = 1}{^\infinity} t^(p - 1) e^(-2 \pi i n t) \; dt$$.

For $$n \neq 0$$, integration by parts tells us that the $$c_n$$ coefficient for $$\zeta(-p, x + 1)$$ over $$x \in (0, 1]$$ will be that for its derivative $$p \zeta(-(p - 1), x + 1)$$, plus the discrepancy $$\zeta(-p, 2) - \zeta(-p, 1) = -1^p = -1$$, all divided by $$-2 \pi i n$$.

Note that this is the same as the integration by parts for $$\int_{t = 1}^{\infinity} t^p e^(-2 \pi i n t) \; dt$$. Here again, we are faced with a discrepancy, which is that between $$t^p e^(-2 \pi i n t)$$ at $$t = 1$$ and $$t = \infinity$$, again working out to $$0 - 1^p = -1$$.

The $$c_n$$ coefficient for $$x^p$$ is given by the integral $$\int_{t = 0}^{1} t^p e^(-2 \pi i n t) \; dt$$. Integration by parts tells us that TODO

So everything works out nicely, because the discrepancy in going from $$x = 0$$ to $$x = 1$$ in $$\zeta(-p, x + 1)$$, which is $$-1^p$$, is the negation of that for $$x^(p + 1)$$, which is $$1^(p + 1) - 0^(p + 1)$$.

***

In the same manner, one can derive also functional equations for the Lerch zeta function, but I do not care to write that out right now. I do not think it will be any more illuminating than what has already been shown above.

***

Footnotes: