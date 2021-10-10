---
title: "Non-Elementary Prime Counting with the Riemann Zeta Function"
date: 2021-10-10
---
This is a much more advanced follow-up to our post on [elementary prime counting]({{ site.baseurl }}{% link _math/Primes/PrimeCounting.md %}).

I will define $$Z(s)$$ to be $$1^s + 2^s + 3^s + 4^s + \ldots = \sum_{n \in \mathbb{N}^+} n^s$$. This is missing a negation sign from the usual convention for the Riemann zeta function (which is $$Z(-s)$$), but I find it easier sometimes to think without that negation sign, and this is How Sridhar Thinks.

The Fundamental Theorem of Arithmetic is the observation that $$Z(s) \prod_p (1 - p^s) = 1$$, or put another way, $$Z(s) = \prod_p (1 - p^s)^{-1}$$. Note that both the existence AND the uniqueness of prime factorizations are used here; each term from $$Z(s)$$ needs to be accounted for precisely once by some prime factorization.

If we take $$Z(s) = \prod_p (1 - p^s)^{-1}$$ and calculate logarithmic derivatives of both sides, we get on the right hand side $$\sum_{n \in \mathbb{N}^+} \Lambda(n) n^s$$, where $$\Lambda(n)$$ is the von Mangoldt function (such that $$\Lambda(p^k) = \log(p)$$ at prime $$p$$ and positive integer $$k$$, and $$\Lambda$$ is everywhere else zero). The left hand side is $$\frac{Z'(s)}{Z(s)}$$, where $$Z'(s) = \sum_{n \in \mathbb{N}^+} \log(n) n^s$$. This is just a generatingfunctionology way in Dirichlet series land of expressing something we could just as well directly express about the series in themselves. It's just another way of expressing our Fundamental Theorem of Arithmetic (in log scale additive world and generatingfunctionology Dirichlet series terms): Every number is the product, over all of its prime power factors, of the corresponding prime.

But this means the von Mangoldt function arises naturally out of something very regular and nice that makes no mention of the prime numbers (the series of values 1 at every positive integer, corresponding to the Dirichlet series for $$Z(s)$$, is as regular as could be hoped for). $$Z(s)$$ is therefore very tractable to study, but will yield for us insights about the von Mangoldt function, which then makes it easy to do von Mangoldt weighted "prime counting" (as in, the Chebyshev function $$\psi(x) = \sum_{n \leq x} \Lambda(n)$$).

We can eventually massage $$\psi(x)$$ to get ordinary prime counting $$\pi(x) = $$ the number of primes $$\leq x$$. But we'll worry about that massaging later. Let's focus on getting an explicit formula for $$\psi(x)$$ now.

Let's say $$L(s)$$ for our $$\frac{Z'(s)}{Z(s)} = \sum_{n \in \mathbb{N}^+} \Lambda(n) n^s$$. How do we extract a formula for $$\psi(x) = \sum_{n \leq x} \Lambda(n)$$ from this?

Well, both functions (the former of $$s$$ and the latter of $$x$$) are $$\sum_{n \in \mathbb{N}^+} \Lambda(n) \times something(n)$$. In the former, the $$something(n)$$ is $$n^s$$, and in the latter, the $$something(n)$$ is the indicator function for $$n \leq x$$.

Note that, as a function of $$x$$, this indicator function is just the Heaviside step function (the indicator function for $$x \geq 0$$) translated by $$n$$. Similarly, each $$n^s$$ is just the original $$1^s$$ (the constant $$1$$) multiplied by an exponential function of $$s$$.

When we want a linear correspondence where translation on one side corresponds to multiplication on the other side, we are looking at some kind of Laplace-Fourier(-Mellin-Z-etc) transform. We want the transform which sends the constant $$1$$ to the Heaviside step function and which turns multiplication by $$n^s$$ into translation by $$n$$ (in the direction of $$(x \mapsto f(x)) \mapsto (x \mapsto f(x - n))$$).

Actually, we can't turn multiplication by $$n^s$$ into translation by $$n$$. Because multiplication by $$n^s$$ followed by multiplication by $$m^s$$ is multiplication by $$(nm)^s$$, not $$(n + m)^s$$. So instead, we should think of the indicator function for $$n \leq x$$ in a different way: this is the indicator function for $$1 \leq x$$ dilated by a multiplicative factor, rather than the indicator function for $$0 \leq x$$ translated by an additive factor. Put another way, if we set $$x = \log(t)$$, then multiplicative dilations of functions of $$x$$ correspond to additive translations of functions of $$t$$. We want multiplication by $$n^s$$ to correspond to dilation of functions of $$x$$ by $$n$$, which means translation of functions of $$t$$ by $$\log(n)$$.

Now everything is easy enough: Given a function $$F(s)$$, let us say that $$\hat{F}(x)$$ is the Laplace-Fourier transform of $$F(s)/s$$, as a function of $$t$$, then evaluated at $$x = \log(t)$$, using the Laplace-Fourier transform that sends $$1/s$$ to the Heaviside step function $$u(t)$$ and under which multiplication by $$\exp(ks)$$ is turned into translation of functions of $$t$$ by $$k$$. \[Keep in mind that, as with Laplace-Fourier transforms in general, we must also therefore have correspondingly that translation by $$k$$ turns into multiplication by $$\exp(-kt)$$.\]

Thus, $$\hat{L}$$ will become $$\psi$$.

To go further, we now must find a linear decomposition of $$L(s) = \frac{Z'(s)}{Z(s)} = \log(Z(s))'$$ that will help us calculate explicitly what $$\hat{L}$$ comes out to. Put another way, we need a good multiplicative decomposition of $$Z(s)$$.

This is where the Hadamard product comes in. In general, given a nice enough function $$f(s)$$ (one which is meromorphic everywhere), we can first take care of expressing its zeros at $$k$$ of integer multiplicity $$z$$ \[including negative $$z$$ to express poles\] via simple $$(s - k)^z$$ factors (or anything proportional to this; it is common to speak of $$(1 - s/k)^z$$, for example, but then $$k = 0$$ requires a different form). Then, the remaining difference to account for is an entire function with no zeros and no poles, which can be expressed as $$\exp(g(s))$$ for some entire function $$g(s)$$, which will thus have a Taylor series expansion with infinite radius of convergence. If we can bound the rate of growth of $$f$$ in the complex plane suitably, we also get that $$g$$ is bounded to be a polynomial of known degree. \[TODO: Expand on this. It is basically by the observation that an entire function which is $$o(1)$$ in the complex plane must be zero; i.e., every analytic function from the Riemann sphere to the complex plane is constant. Note that the analogous fact fails for the reals; e.g., consider $$s \mapsto \exp(-s^2)$$\]

This amounts to saying that, under nice conditions, a function $$f(s)$$ has some expression in terms of factors which are all either affine functions of $$s$$ (or reciprocals of such), accounting for the zeroes/poles, or which are $$\exp(k s^n)$$ for various constants $$k$$ and natural number $$n$$, with these exponentiated polynomial factors dying off after $$n$$ gets large enough if we can bound the rate of growth of $$f$$ in the complex plane suitably.

We can take the logarithmic derivative and then divide by $$s$$ and then take the Laplace-Fourier transform for all of these factors easily enough.

Actually, it's even easier if we account for zeros/poles not by using factors proportional to $$(s - k)$$, but by bundling in some exponential-linear factors here too, accounting for a zero at $$k$$ using a factor proportional to $$(s - k) e^{s/k}$$. [Here, it really is important that we use $$e$$ as the base of the exponentiation, rather than some arbitrarily based $$\exp$$]. The natural logarithm of this is $$\ln(s - k) + s/k$$, and thus its natural logarithmic derivative is $$\frac{1}{s - k} + \frac{1}{k} = \frac{s}{(s - k)k}$$, which conveniently already has a factor of $$s$$ in its numerator.

When we divide out by $$s$$, we get $$\frac{1}{k} \times \frac{1}{s - k}$$. Taking the Laplace-Fourier transform, this is a scaled and translated version of $$\frac{1}{s}$$, and thus becomes a similarly scaled version of $$u(t)$$, multiplied by $$\exp(-kt)$$. We find that each $$(s - k) e^{s/k}$$ factor turns under our Laplace-Fourier transform into $$\frac{\exp(-kt)}{k}$$, which given $$x = \log(t)$$ amounts to $$\frac{x^{-k}}{k}$$.

Thus, each zero of $$Z(s)$$ at $$k$$ of multiplicity $$z$$ gives us a term of $$z \frac{x^{-k}}{k}$$ in the expansion of $$\psi(x)$$ (presuming from now on that we use the natural logarithm and not some other base in defining $$\psi$$). That is, each zero gives us a term $$\frac{x^{-k}}{k}$$ and each pole gives us a negated term $$-\frac{x^{-k}}{k}$$, and we must count these with multiplicity.

What about the remaining factors in $$Z(s)$$, of the form $$e^{k s^n}$$ \[again, it will be easiest to express these with base $$e$$ as we're about to take derivatives\]? The natural logarithmic derivative of such a factor is $$k n s^{n - 1}$$. Dividing this by $$s$$, we get $$k n s^{n - 2}$$. The Laplace-Fourier transform of this would become something proportional to $$k n t^{-1 - n}$$ by some factorial factor, times $$u(t)$$ or $$\mathrm{sgn}(t)$$. I'm too lazy to figure out the exact details right now. \[TODO\]. The key thing is that it goes to zero when $$n = 0$$ and it goes to $$k$$ when $$n = 1$$ and $$t > 0$$ (i.e., $$x > 1$$). 

For our $$Z(s)$$, it turns out that we can study the order of growth in the complex plane and confirm that these die off at $$n > 1$$. But even if we didn't know that, what we would have more generally from these exponential-polynomial factors is some Taylor series in $$\frac{1}{t} = \frac{1}{\log(x)}$$ becoming part of the series for $$\psi$$.

So that's it. At $$x > 1$$, we have that $$\psi(x)$$ is the sum of terms $$z \frac{x^{-k}}{k}$$ for each zero of $$Z$$[^zeronegate] at $$k$$ of integer multiplicity $$z$$ (including poles as negative multiplicity), plus some polynomial function of $$\frac{1}{\log(x)}$$ that we can determine from the rate of growth of $$Z$$ in the complex plane is actually just a constant[^TheConstant]. Also, this series is conditionally convergent and needs to have it terms bundled just so, and also this series dosn't converge exactly to $$\psi(x)$$ at its jump discontinuities, but to the halfway point, as is typical for Fourier series decomposition, but nevermind such formalities for now.

In particular, the rate of growth for $$\psi(x)$$ will thus be controlled by the zeros or poles of $$Z(s)$$ of most negative real component. There are none with real component below $$-1$$ (as this is where $$Z(s)$$ is absolutely convergent to a nonzero value), and there is a pole of multiplicity $$1$$ at $$s = -1$$ (from the harmonic series) but no other zeroes or poles with real component $$-1$$[^criticalline]. This means $$\psi(x) \approx x$$. The Riemann Hypothesis asserts that the next most negative real component of a critical point of $$Z$$ is at real component $$-\frac{1}{2}$$, so that the next terms in the expansion of $$\psi(x)$$ grow of order comparable to $$\sqrt{x}$$[^ordertechnicality].

How does this relate to the ordinary prime counting function $$\pi(x)$$? TODO, I will have to write the details more later. But the key thing is that almost all prime powers $$\leq x$$ are in fact primes which are very nearly $$x$$, so that $$\psi(x)/\pi(x)$$ is very nearly $$\ln(x)$$, asymptotically. Hence, asymptotically, $$\pi(x) \approx \frac{x}{\ln(x)}$$.

****
For what it's worth, another site that discusses this rather nicely is <http://empslocal.ex.ac.uk/people/staff/mrwatkin/zeta/encoding2.htm>.

****
Footnotes:

[^zeronegate]: Note that the zeros of $$Z(s) = \zeta(-s)$$ are the negations of the zeros of $$\zeta$$ as traditionally defined, so we can also say that $$\psi(x)$$ has a term $$-\frac{x^k}{k}$$ for each zero at $$k$$ of $$\zeta$$ and a term $$\frac{x^k}{k}$$ for each pole at $$k$$ of $$\zeta$$, counted with multiplicity.

[^criticalline]: I haven't proven in this post that there are no other zeroes or poles of $$Z$$ with real component $$-1$$, other than the pole from the harmonic series. I've just shown that this is morally equivalent to the Prime Number THeorem. Actually proving the absence of other such zeroes or poles on the critical line comes from an argument I will have to spell out in another post another time: any such point could be bundled with its conjugate, and the combined effect of the two on the distribution of the primes is something strong enough that we could rule it out. TODO.

[^ordertechnicality]: If you care about such technicalities, the remainder term would not be $$O(\sqrt{x})$$, but would be $$O(x^{\frac{1}{2} + \epsilon}$$ for every $$\epsilon > 0$$.

 [^TheConstant]: Specifically, the constant is $$L(0) = Z'(0)/Z(0)$$, which we can with some work relate to the [factorial constant]({{ site.baseurl }}{% link _math/Stirling.md %}) and thus show is $$-\ln(2\pi)$$.