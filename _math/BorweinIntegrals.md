---
title: "Borwein Integrals"
date: 2019-12-19
---
A result sometimes observed as surprising, shocking, etc, is that $$\int_{0}^{\infty} \mathrm{sinc}(x) dx = \pi/2$$, and indeed $$\int_{0}^{\infty} \mathrm{sinc}(x) \mathrm{sinc}(x/3) dx = \pi/2$$ and $$\int_{0}^{\infty} \mathrm{sinc}(x) \mathrm{sinc}(x/3) \mathrm{sinc}(x/5) dx = \pi/2$$ and $$\int_{0}^{\infty} \mathrm{sinc}(x) \mathrm{sinc}(x/3) \mathrm{sinc}(x/5) \mathrm{sinc}(x/7) dx = \pi/2$$ and so on, but once we get up to $$\int_{0}^{\infty} \mathrm{sinc}(x) \mathrm{sinc}(x/3) \ldots \mathrm{sinc}(x/15) dx$$, the result is $$q \pi$$ for a rational $$q$$ strictly less than $$1/2$$.

This has a simple explanation in terms of the fact that this is the point at which the sum of the series $$\frac{1}{3} + \frac{1}{5} + \ldots$$ first crosses past $$1$$.

It will be cleaner to explain this with some reparametrizations.

Observe that all of our integrands are even functions, so the bounds on all our integrals might as well be taken from $$-\infty$$ to $$\infty$$, only doubling the results up to $$\pi$$ rather than up to $$\frac{\pi}{2}$$.

Simultaneously, let us actually replace $$\mathrm{sinc}(x)$$ with the rescaled $$f(x) = \mathrm{sinc}(\pi x)$$, which change of variable only shrinks the results by a factor of $$\pi$$, to $$1$$.

Thus, $$\int_{-\infty}^{\infty} f(x) dx = 1$$, $$\int_{-\infty}^{\infty} f(x) f(x/3) dx = 1$$, etc, but $$\int_{-\infty}^{\infty} f(x) f(x/3) \ldots f(x/15) dx < 1$$.

Next, note that $$\sinc$$, $$\f$$, etc, are Fourier transforms of rectangle functions; specifically, $$f$$ is the Fourier transform of the probability density function of a uniformly random variable in $$[-1, 1]$$. And therefore each rescaled $$x \mapsto f(kx)$$ is the Fourier transform of the probability density function of a uniformly random variable in $$[-k, k]$$. (Fourier transforms of probability density functions are also called characteristic functions, by the way, which is simply the moment-generating function turned on its side, so to speak. But this is just jargon.)

Multiplying these integrands together amounts to convolution on the other side of the Fourier transform, and convolution of probability density functions amounts to independent addition of random variables. And the integral over all inputs on one side of the Fourier transform amounts to evaluation at 0 on the other side of the Fourier transform.

Thus, these integrals are the probability densities that the sum of independent uniform random variables with bounds corresponding to the rescaling factors comes out to precisely 0.

This is the probability density that all the random variables other than the first one sum to the negation of the first one; since the first variable is uniformly random, this amounts to just the probability that all the other random variables sum to a value in the range for the first variable to cancel.

In other words, the probability that uniformly random variables in the ranges [-1/3, 1/3], [-1/5, 1/5], etc, all sum to a value of magnitude at most 1.

This is guaranteed when 1/3 + 1/5 + ... + our stopping point is itself at most 1. But it stops being guaranteed once we pass that. Hence, the results we've seen.

Incidentally, there's absolutely nothing special about our using reciprocals of odd numbers in order here. Any values will display the same phenomenon: when the bounds of all the factors other than the first sum to $$\leq$$ the first factor, our computation yields a guaranteed 1 probability, and otherwise it yields something smaller.

That's all there is to it.

[TODO: Add graphics displaying the convolutions of the relevant probability density functions?]

[TODO: LaTeXify with proper \frac notation, I guess]