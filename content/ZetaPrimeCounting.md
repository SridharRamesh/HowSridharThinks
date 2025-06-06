---
title: "Non-Elementary Prime Counting with the Riemann Zeta Function"
date: 2021-10-10
---
This is a much more advanced follow-up to our post on [elementary prime counting](@/PrimeCounting.md).

<!-- more -->

I will define $$Z(s)$$ to be $$1^s + 2^s + 3^s + 4^s + \ldots = \sum_{n \in \mathbb{N}^+} n^s$$. This is missing a negation sign from the usual convention for the Riemann zeta function (which is $$\zeta(s) = Z(-s)$$), but I find it easier sometimes to think without that arbitrary negation sign, and this is How Sridhar Thinks.

The Fundamental Theorem of Arithmetic is the observation that $$Z(s) \prod_p (1 - p^s) = 1$$, or put another way, $$Z(s) = \prod_p (1 - p^s)^{-1}$$, over prime $$p$$. (This is an instance of general [Möbius inversion](@/MoebiusInversion.md)). Note that both the existence AND the uniqueness of prime factorizations are used here; each term from $$Z(s)$$ needs to be accounted for precisely once by some prime factorization.

If we take $$Z(s) = \prod_p (1 - p^s)^{-1}$$ and calculate logarithmic derivatives of both sides, we get on the right hand side $$\sum_{n \in \mathbb{N}^+} \Lambda(n) n^s$$, where $$\Lambda(n)$$ is the von Mangoldt function (such that $$\Lambda(p^k) = \log(p)$$ at prime $$p$$ and positive integer $$k$$, and $$\Lambda$$ is everywhere else zero). The left hand side is $$\frac{Z'(s)}{Z(s)}$$, where $$Z'(s) = \sum_{n \in \mathbb{N}^+} \log(n) n^s$$. This is just a generatingfunctionology way in Dirichlet series land of expressing something we could just as well directly express about the series in themselves. It's just another way of expressing our Fundamental Theorem of Arithmetic (in log scale additive world and generatingfunctionology Dirichlet series terms): Every number is the product, over all of its prime power factors, of the corresponding prime.

But this means the von Mangoldt function arises naturally out of something very regular and nice that makes no mention of the prime numbers (the series of values 1 at every positive integer, corresponding to the Dirichlet series for $$Z(s)$$, is as regular as could be hoped for). $$Z(s)$$ is thus very tractable to study, but will yield for us insights about the von Mangoldt function, which then makes it easy to do von Mangoldt weighted "prime counting" (as in, the Chebyshev function $$\psi(x) = \sum_{n \leq x} \Lambda(n)$$).

We can eventually massage $$\psi(x)$$ to get ordinary prime counting $$\pi(x) = $$ the number of primes $$\leq x$$. But we'll worry about that massaging later. Let's focus on getting an explicit formula for $$\psi(x)$$ now.

Let's say $$L(s)$$ for our $$\frac{Z'(s)}{Z(s)} = \sum_{n \in \mathbb{N}^+} \Lambda(n) n^s$$. How do we extract a formula for $$\psi(x) = \sum_{n \leq x} \Lambda(n)$$ from this?

Well, both functions (the former of $$s$$ and the latter of $$x$$) are $$\sum_{n \in \mathbb{N}^+} \Lambda(n) \times something(n)$$. In the former, the $$something(n)$$ is $$n^s$$, and in the latter, the $$something(n)$$ is the indicator function for $$n \leq x$$.

Note that, as a function of $$x$$, this indicator function is just the Heaviside step function (the indicator function for $$x \geq 0$$) translated by $$n$$. Similarly, each $$n^s$$ is just the original $$1^s$$ (the constant $$1$$) multiplied by an exponential function of $$s$$.

When we want a linear correspondence where translation on one side corresponds to multiplication on the other side, we are looking at some kind of Laplace-Fourier(-Mellin-Z-etc) transform. We want the transform which sends the constant $$1$$ to the Heaviside step function and which turns multiplication by $$n^s$$ into translation by $$n$$ (in the direction of $$(x \mapsto f(x)) \mapsto (x \mapsto f(x - n))$$).

Actually, we can't turn multiplication by $$n^s$$ into translation by $$n$$. Because multiplication by $$n^s$$ followed by multiplication by $$m^s$$ is multiplication by $$(nm)^s$$, not $$(n + m)^s$$. So instead, we should think of the indicator function for $$n \leq x$$ in a different way: this is the indicator function for $$1 \leq x$$ dilated by a multiplicative factor, rather than the indicator function for $$0 \leq x$$ translated by an additive factor. Put another way, if we set $$t = \log(x)$$, then multiplicative dilations of functions of $$x$$ correspond to additive translations of functions of $$t$$. We want multiplication by $$n^s$$ to correspond to dilation of functions of $$x$$ by $$n$$, which means translation of functions of $$t$$ by $$\log(n)$$.

Now everything is easy enough: Given a function $$F(s)$$, let us say that $$\hat{F}(x)$$ is the Laplace-Fourier transform of $$F(s)/s$$, as a function of $$t$$, then evaluated at $$t = \log(x)$$, using the Laplace-Fourier transform that sends $$1/s$$ to the Heaviside step function $$u(t)$$ and under which multiplication by $$\exp(ks)$$ is turned into translation of functions of $$t$$ by $$k$$. \[Keep in mind that, as with Laplace-Fourier transforms in general, we must also therefore have correspondingly that translation by $$k$$ turns into multiplication by $$\exp(-kt)$$.\]

Thus, $$\hat{L}$$ will become $$\psi$$.

To go further, we now must find a linear decomposition of $$L(s) = \frac{Z'(s)}{Z(s)} = \log(Z(s))'$$ that will help us calculate explicitly what $$\hat{L}$$ comes out to. Put another way, we need a good multiplicative decomposition of $$Z(s)$$.

This is where the Hadamard product comes in. In general, given a nice enough function $$f(s)$$ (one which is meromorphic everywhere), we can first take care of expressing its zeros at $$k$$ of integer multiplicity $$z$$ \[including negative $$z$$ to express poles\] via simple $$(s - k)^z$$ factors (or anything proportional to this; it is common to speak of $$(1 - s/k)^z$$, for example, but then $$k = 0$$ requires a different form). Then, the remaining factor to account for is an entire function with no zeros and no poles, which can be expressed as $$\exp(g(s))$$ for some entire function $$g(s)$$, which will thus have a Taylor series expansion with infinite radius of convergence. If we can bound the rate of growth of $$f$$ in the complex plane suitably, we also get that $$g$$ is bounded to be a polynomial of known degree. \[TODO: Expand on this. It is basically by the observation that an entire function which is $$o(1)$$ in the complex plane must be zero; i.e., every analytic function from the Riemann sphere to the complex plane is constant. This is known as Liouville's theorem. Note that the analogous fact fails for the reals; e.g., consider $$s \mapsto \exp(-s^2)$$\]

This amounts to saying that, under nice conditions, a function $$f(s)$$ has some expression in terms of factors which are all either affine functions of $$s$$ (or reciprocals of such), accounting for the zeros/poles, or which are $$\exp(k s^n)$$ for various constants $$k$$ and natural number $$n$$, with these exponentiated polynomial factors dying off after $$n$$ gets large enough if we can bound the rate of growth of $$f$$ in the complex plane suitably.

We can take the logarithmic derivative and then divide by $$s$$ and then take the Laplace-Fourier transform for all of these factors easily enough.

The logarithmic derivative of $$(s - k)$$ is proportional to $$\frac{1}{s - k}$$. Indeed, it's exactly equal to this if we use the natural logarithm, rather than some other base, so from now on for convenience, let us presume it is the natural logarithm that we use in defining $$\psi$$. After dividing by $$s$$, this $$\frac{1}{s - k}$$ becomes $$\frac{1}{(s - k)s} = \frac{1}{k} \left( \frac{1}{s - k} - \frac{1}{s} \right)$$.

Our Laplace-Fourier transform of $$\frac{1}{s}$$ is $$u(t)$$. And the Laplace-Fourier transform of $$\frac{1}{s - k}$$ (which is just a translation of $$\frac{1}{s}$$) will then become this same $$u(t)$$ multiplied by $$\exp(-kt)$$. Keeping in mind that $$t = \log(x)$$, this amounts to $$x^{-k}$$ (for $$t > 0$$, where we can ignore the $$u(t)$$ factor; we will from now on always presume $$x > 1$$ accordingly). So ultimately, we will get $$\frac{x^{-k} - 1}{k}$$ as the term in the expansion of $$\psi(x)$$ corresponding to this factor in $$Z(s)$$. That is, up to an additive constant, each zero at $$k$$ gives us a term $$\frac{x^{-k}}{k}$$ and each pole at $$k$$ gives us a term $$\frac{x^{-k}}{-k}$$, and we must count these with multiplicity.

\[We should think of as $$\frac{x^{-k} - 1}{k}$$ as really -$$\int_{0}^{x} x^{-k - 1} \\; dx$$. In the usual way, the limiting value at $$k = 0$$ is then seen to be $$-\ln(x)$$. Thus, if there were zeros or poles of $$Z$$ at $$0$$, we would then get $$\ln(x)$$ terms in the expansion of $$\psi(x)$$ at $$x > 1$$. Luckily, $$Z(0) = -\frac{1}{2}$$ (see the analytic continuation constructed [here](@/DifferenceEquationZeta.md) or [here](@/AlternatingSeries.md)), so we don't actually have any zero or pole there to worry about.\]

What about the remaining exponential-polynomial factors in $$Z(s)$$, of the form $$e^{k s^n}$$? The natural logarithmic derivative of such a factor is $$k n s^{n - 1}$$. Dividing this by $$s$$, we get $$k n s^{n - 2}$$. At $$n = 0$$, this vanishes. At $$n = 1$$, this is $$k s^{-1}$$, whose Laplace-Fourier transform is $$k u(t)$$; that is, an additive constant (for $$t > 0$$). At higher $$n$$, this Laplace-Fourier transform becomes $$k n$$ times some iterated derivative of $$u(t)$$; that is, the Dirac delta or its derivatives. All of these higher $$n$$ terms can thus be ignored for $$t > 0$$, i.e., for $$x > 1$$.

For our $$Z(s)$$, it turns out that we can study the order of growth in the complex plane and confirm that these factors in $$Z(s)$$ die off at $$n > 1$$. But even if we didn't know that, we could ignore these terms at $$x > 1$$ anyway.

So that's it. At $$x > 1$$, we have that $$\psi(x)$$ is the sum of terms $$z \frac{x^{-k}}{k}$$ for each zero of $$Z$$ [^zeronegate] at $$k$$ of integer multiplicity $$z$$ (including poles as negative multiplicity), plus an additive constant [^TheConstant].

Also, this series is conditionally convergent and needs to have it terms bundled just so, and also this series doesn't converge exactly to $$\psi(x)$$ at its jump discontinuities, but to the halfway point, as is typical for Fourier series decomposition, but nevermind such formalities for now. Similarly, we've been commuting limits all over the place (e.g., commuting infinite sums and the integrals defining Laplace-Fourier transforms) and whatnot. All sorts of things which a rigorous treatment would pay more care to. But here, we only care about the moralities and not the formalities.

In particular, the rate of growth for $$\psi(x)$$ will thus be controlled by the zeros or poles of $$Z(s)$$ of most negative real component. There are none with real component below $$-1$$ (as this is where $$Z(s)$$ is absolutely convergent to a nonzero value), and there is a pole of multiplicity $$1$$ at $$s = -1$$ (from the harmonic series) but no other zeros or poles with real component $$-1$$ [^criticalline]. This means $$\psi(x) \approx x$$. The Riemann Hypothesis asserts that the next most negative real component of a critical point of $$Z$$ is at real component $$-\frac{1}{2}$$, so that the next terms in the expansion of $$\psi(x)$$ grow of order comparable to $$\sqrt{x}$$ [^ordertechnicality].

# Other prime counting functions

How does this relate to the ordinary prime counting function $$\pi(x)$$? The key thing is that almost all prime powers $$\leq x$$ are in fact primes which are nearly $$x$$, so that $$\psi(x)/\pi(x)$$ is nearly $$\ln(x)$$, asymptotically. Hence, asymptotically, $$\pi(x) \approx \frac{\psi(x)}{\ln(x)} \approx \frac{x}{\ln(x)}$$. But we can derive in more detail an exact formula for $$\pi(x)$$, like so:

As we work towards moving from $$\psi(x)$$ to $$\pi(x)$$, let us first consider another weighted prime power counting function. One of the bothers with $$\psi$$ (the summatory function for $$\Lambda$$) is that it assigns primes different weights, logarithmically. Let us try to cancel this out, by saying that $$weight(p^k) = \frac{\Lambda(n)}{\log(n)}$$. Now all primes are counted equally. But remember, $$\Lambda$$ also counted prime powers. What will happen now is that $$weight(p^k) = \frac{1}{k}$$ for prime $$p$$ and positive integer $$k$$ and is otherwise zero. So we count all primes equally, but we also count prime squares as half of a prime, prime cubes as a third of a prime, and so on. Still, this is progress towards our goal. Let us now derive an explicit formula for $$\Pi(x) = \sum_{n \leq x} weight(n)$$ from our explicit formula for $$\psi(x)$$.

Essentially, the derivative of $$\Pi$$ is the derivative of $$\psi$$ divided by $$\log$$. Since $$\psi$$ is a stepwise function with jump discontinuities, its derivative is a linear combination of a bunch of translated Dirac deltas, instead of ordinary functions, but we can still reason about this in the usual way. So let us take our series for $$\psi$$ up to an additive constant, differentiate it, divide by $$\log$$, and then reintegrate it, to get a series for $$\Pi$$ up to an additive constant.

Apart from the additive constant, the general terms of our series for $$\psi$$ were of the form $$\frac{x^k}{k}$$ counted with multiplicity. When we differentiate, this becomes $$x^{k - 1}$$. If we now divide by $$\log(x)$$, we get $$\frac{x^{k - 1}}{\log(x)}$$. Now, what does $$\int \frac{x^{k - 1}}{\log(x)} \\; dx$$ come to?

Let us define $$\newcommand{\Li}{\mathrm{Li}}\Li(x)$$ as an antiderivative of $$\frac{1}{\log(x)}$$. I don't care which antiderivative (it is common to make a particular choice with the notation $$\mathrm{li}$$ and another choice with the notation $$\Li$$ but I don't mean to imply any particular choice for now. I will use $$\Li$$ as meaning a function determined only up to an additive constant). Note that the derivative of $$\Li(x^k)$$ is $$\frac{k x^{k - 1}}{\log(x^k)} = \frac{x^{k - 1}}{\log(x)}$$. Thus, $$\Li(x^k)$$ is the antiderivative we sought.

Our series for $$\psi$$ has now turned into a series for $$\Pi$$: We have that $$\Pi(x)$$ is, up to an additive constant, the sum, over all zeros $$k$$ of $$Z$$ counted with multiplicity (and poles counted as negative zeros as always), of $$-\Li(x^{-k})$$. Put another way, an additive constant plus the sum over all poles $$\rho$$ of $$\zeta$$ counted with multiplicity (and zeros counted as negative poles) of $$\Li(x^{\rho})$$.

\[We might wish to choose our additive constant in the definition of $$\Li$$ such that $$\Li(1) = 0$$, to make this last series manifestly convergent at $$x = 1$$, but alas, it is readily seen that $$\Li(x) - \Li(1) = \int_{1}^{x} \frac{1}{\log(x)}$$ is infinite for other $$x$$, so that we can't bother normalizing it in this way. We must give up hope for using this series at $$x = 1$$ and only use it at $$x > 1$$. Instead, we can make our series convergent by picking some arbitrary value $$x > 1$$, taking every term in the series and adding to that term a constant to make the term come out to zero at this particular $$x$$, and finally adding $$\Pi(x)$$ as a constant to the entire series. Put another way, we have a good formula for $$\Pi(B) - \Pi(A)$$, where $$1 < A, B$$, with this formula being the integral between $$A$$ and $$B$$ of our $$x^{k - 1}/\log(x)$$ series.\]

How do we finally get from $$\Pi(x)$$ to $$\pi(x)$$? Well, keep in mind, $$\Pi(x) = \sum_{n \in \mathbb{N}^+} \frac{\pi(x^{1/n})}{n}$$. This relationship has such a nice form that we can recover $$\pi$$ from $$\Pi$$ using [Möbius inversion](@/MoebiusInversion.md). From this, we find that $$\pi(x) = \sum_{n \in \mathbb{N}^+} \frac{\mu(n) \Pi(x^{1/n})}{n}$$, where the Möbius function $$\mu$$ takes the value $$-1$$ at primes and zero at higher prime powers, and the Möbius function at a general positive integer is the product of the Möbius function at its prime power factors.

And that does it. We now have a series for the ordinary prime counting function, all in terms of the zeros and poles of $$Z$$.

****

Our insights came in two parts: First, after setting $$L(s) = \log(Z(s))' = \frac{Z'(s)}{Z(s)}$$, we know that $$\psi$$ is $$L(s)$$ divided by $$s$$, Laplace-Fourier transformed, and evaluated at $$t = \log(x)$$; that $$\Pi$$ is $$\psi'$$ (aka, a $$\Lambda$$-weighted Dirac comb) divided by $$\log$$ and integrated; and that $$\pi$$ is obtained from $$\Pi$$ by Möbius inversion.

And secondly, we had the Hadamard product representation of a meromorphic function like $$Z$$ in terms of its zeros and poles (and an additional Taylor series which turns out not to matter beyond one term, both because of the rate of growth of $$Z$$ in the complex plane and independently also not mattering in our $$x > 1$$ range of interest because all the higher degree terms just become derivatives of the Dirac delta after our Laplace-Fourier transform above).

****
For what it's worth, another site that discusses this rather nicely is <http://empslocal.ex.ac.uk/people/staff/mrwatkin/zeta/encoding2.htm>.

****
Footnotes:

[^zeronegate]: Note that the zeros of $$Z(s) = \zeta(-s)$$ are the negations of the zeros of $$\zeta$$ as traditionally defined, so we can also say that $$\psi(x)$$ has a term $$-\frac{x^k}{k}$$ for each zero at $$k$$ of $$\zeta$$ and a term $$\frac{x^k}{k}$$ for each pole at $$k$$ of $$\zeta$$, counted with multiplicity.

[^criticalline]: I haven't proven in this post that there are no other zeros or poles of $$Z$$ with real component $$-1$$, other than the pole from the harmonic series. I've just shown that this is morally equivalent to the Prime Number Theorem. We can rule out that there are any other poles anywhere in $$Z$$ by the constructions of its analytic continuation given [here](@/DifferenceEquationZeta.md) or [here](@/AlternatingSeries.md). But proving the absence of any zeros on the critical line comes from an argument I will have to spell out in another post another time: any such point could be bundled with its conjugate, and the combined effect of the two on the distribution of the primes would be something strong enough that we can rule it out. TODO.

[^ordertechnicality]: If you care about such technicalities, the remainder term would not be $$O(\sqrt{x})$$, but would be $$O(x^{\frac{1}{2} + \epsilon})$$ for every $$\epsilon > 0$$.

 [^TheConstant]: Specifically, the constant is $$L(0) = Z'(0)/Z(0)$$, which we can with some work relate to the [factorial constant](@/Stirling.md) and thus show is $$-\ln(2\pi)$$.