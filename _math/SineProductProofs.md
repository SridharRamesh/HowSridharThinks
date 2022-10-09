---
title: "Proofs of The Sine Product Formula"
date: 2019-05-18
---
In this post, I will accumulate (and perhaps relate) several different proofs of the sine product formula $$\sin(\pi x) = \pi x \prod_{n \geq 1} \left(1 + \frac{x}{n}\right) \left(1 + \frac{x}{-n}\right)$$, or the essentially equivalent (by logarithmic differentiation) cotangent sum formula $$\pi \cot(\pi x) = \frac{1}{x} + \sum_{n \geq 1} \frac{1}{n + x} + \frac{1}{-n + x}$$, or the essentially equivalent squared cosecant series obtained by differentiating once more (thus obtaining an absolutely convergent sum of $$(n + x)^{-2}$$ over ALL integers $$n$$, which can also be interpreted in terms of the Hurwitz zeta function at $$s = 2$$).

Of course, these differentiations lose information about a constant, so to establish the right to left directions of the aforementioned equivalences, we need to see that the constants work out appropriately. In obtaining $$\sin(\pi x) = \pi x \prod_{n \geq 1} \left(1 + \frac{x}{n}\right) \left(1 + \frac{x}{-n}\right)$$ once we know the logarithmic derivatives of the two sides are equal, this is established by noting that both sides have the same derivative at $$0$$ (i.e., the same coefficient of $$x$$ in their Taylor expansions). In obtaining $$\pi \cot(\pi x) = \frac{1}{x} + \sum_{n \geq 1} \frac{1}{n + x} + \frac{1}{-n + x}$$ once we know the derivatives of the two sides are equal, this is established by noting that both sides are odd functions, a property destroyed by the addition of any nonzero constant.

Ok, now on to the proofs:

# Calc 101 Proof. Aka, Fourier series proof. Aka, the best proof.

This is the Calc 101 proof, proceeding along the exact same lines as [Solving the Basel Problem With Calc 101]({{ site.baseurl }}{% link _math/BaselProblemCalc101.md %}), but for now I will word it as though the reader is familiar with the theory of Fourier transforms. (The reader is always presumed to be me, at whatever stage of my previous self I prefer to be talking to)

Recall that the Fourier transform of the function $$x \mapsto 1/x$$ is essentially the signum function (this is by considering how both sides react under rescaling the input by positive factors or -1).

Multiplying this by a Dirac comb, we get essentially the Dirac comb restricted to values at least zero, minus the Dirac comb restricted to values at most zero.

This difference of two unidirectional Dirac combs must therefore be the Fourier series of $$x \mapsto 1/(x + n)$$ summed over all integers $$n$$ [with appropriate scaling on all the inputs and outputs; I'm not being very specific right now in which parametrization of the Fourier transform/series I'm using, but it will be obvious as you turn this prose into the math; unit period if you like or $$2\pi$$ period if you like, etc, etc].

But also, this is clearly the Fourier series of $$(1 + R^x + R^{2x} + R^{3x} + \ldots) - (1 + R^{-x} + R^{-2x} + R^{-3x} + \ldots) = 1/(1 - R^x) - 1/(1 - R^{-x})$$, where $$R$$ is the base of exponentiation for rotation in the appropriate units. Which can be rewritten as something like $$(1 + R^x)/(1 - R^x) = \cot(x)$$.

*[Note also that both terms here individually act like half of $$\cot(x)$$ as well, except they should be understood as having made a particular choice about its non-convergent average value, to be 1 or -1, as though the appropriate Dirac delta were added in to take care of this regardless of facts on the ground otherwise; adding these two terms together amounts to the symmetric choice of average value of 0, as though all our averaging is on regions centered at the origin. All the trickiness about having only conditional convergence of the ultimate cotangent series using appropriately balanced positive and negative terms presumably corresponds to this.]*

And thus we get the cotangent series desired. As far as I am concerned, this is the Book proof/God's proof/Sridhar's proof [equivalent notions]. It is the most direct, in some sense; this is the direct generating function type way that I would go about summing $$1/(x + n)$$ over all integers $$n$$, it illustrates a power general technique for adding up all translation shifts of a given function (multiplying its Fourier transform by a Dirac comb; i.e., retaining just the appropriately periodic components; this is known as "Poisson summation"), and furthermore, this series is the simplest and most uniform of the three equivalent series we could here consider.

*[TODO: Write out how the above can also essentially be done in the same way using the Fourier transform of $$\log(\abs{x})$$ as $$\frac{1}{\abs{x}}$$ plus some multiple of the Dirac delta. Thus, $$\sum_{n \in \mathbb{Z}} \log(x + n)$$ is, up to a constant term, given by the sum of $$R^{nx}/\abs{n}$$, which comes to $$-\log(1 - R^x) - \log(1 - R^{-x}) = -\log(2 - 2\cos(x))$$ which is some simple affine transform of $$\log(\sin(x/2))$$, thus directly establishing the sine product. Something like that, with more care about the actual scaling factors at various points.

Of course, this is just the previous argument carried out integrated, in that $$\log(\abs{x})$$ is the integral of $$1/x$$ and $$\frac{1}{\abs{x}}$$ is the division by $$x$$ of the signum function. So actually, this is no different.]*

# Sridhar's 3blue1brown proof (the Sailor and the Keeper)

I am fond of this proof as well, because I discovered it and it is nice, even though I do not think this is as Book as the previous one. I will write this up in text form eventually, but [here's the video](https://www.youtube.com/watch?v=8GPy_UMV-08). See further details [here](./3b1bSineProduct.html).

In short, we analyze the function $$f_N(x) = x^{N/2} - x^{-N/2}$$ for natural number $$N$$, noting that this is $$x^{-N/2} \prod_{r^N = 1} (x - r) = \prod_{r^N = 1} (x - r) x^{-1/2}$$ as $$r$$ ranges over all the $$N$$-th roots of unity. The $$N$$th roots of unity can be expressed as $$R^{k/N}$$ for integer $$k$$ where $$R = e^{2 \pi i}$$, so this is $$\prod_{k \in (-N/2, N/2]} (x - R^{k/N}) x^{-1/2}$$. Since we also have $$f_1(x) = f_N(x^{1/N})$$, and $$\sin(\pi x) = f_1(R^x)/(2i)$$ we find that $$\frac{\sin(x)}{\sin(y)} = \prod_{k \in (-N/2, N/2]} \frac{R^{x/N} - R^{k/N}){R^{y/N} - R^{k/N} R^{(y - x)/(2N)}$$. In the limit as $$N \to \infty$$, we find that $$\frac{R^{x/N} - R^{k/N}){R^{y/N} - R^{k/N} \to \frac{x - k}{y - k}$$ for any fixed $$k$$, while $$R^{(y - x)/(2N)} \to 1$$. Thus, if we could commute limits suitably, we could conclude that $$\frac{\sin(x)}{\sin(y)} = \prod_{k \in \mathbb{Z}} \frac{x - k}{y - k}$$. Finally, we use a dominated convergence argument, as noted [here](./3b1bSineProduct.html), to commute the limits (at least as far as magnitude is concerned. TODO: Work this out for phase as well.)

# Euler's original proof

Euler is often said to have glibly moved from "$$\sin(x)/x$$ has roots at nonzero integer multiples of $$\pi$$" to "$$\sin(x)/x$$ is the product of $$(1 - x/(k\pi))$$ over each nonzero integer $$k$$" in solving the Basel problem, simply ignoring the problem of the fact that many other functions have precisely the same zeros.

But Euler was not, in fact, always so glib in presenting this argument! For example, in Volume 1, Chapter 9 of his Introductio in Analysin Infinitorum (translation by Ian Bruce available [here](http://www.17centurymaths.com/contents/introductiontoanalysisvol1.htm)), we see that Euler argues for the product formula by noting (what would in modern notation be) that $$\sin(x) =$$ the imaginary part of $$e^{ix} =$$ the imaginary part of $$(1 + ix/N)^N$$ for infinitely large $$N$$, so that a factorization of $$\sin(x)$$ can be extracted from a factorization of the polynomial $$\Im[(1 + ix/N)^N]$$ for large $$N$$.

I'll write out in modern style the extraction of that factorization, but all the ideas are already present in the Euler:)

Let us denote $$\Im[(1 + ix/N)^N]$$ by $$f_N(x)$$. Note that $$f_N$$ is a polynomial of degree either $$N - 1$$ (if $$N$$ is even) or $$N$$ (if $$N$$ is odd), whose degree 1 term is 1. Furthermore, its roots occur where $$x/N$$ is the tangent of a multiple of $$\pi/N$$. Putting these together, we get that $$f_N(x)/x =$$ the product of $$1 - x/(N \tan(k\pi/N))$$ over the nonzero integers $$k$$ in $$(-N/2, N/2)$$.

As $$N$$ approaches infinity, $$N \tan(k\pi/N)$$ approaches $$k\pi$$. Thus, we have that $$\sin(x)/x =$$ the product of $$1 - x/(k\pi)$$ over the nonzero integers $$k$$.

[This last step is slightly glib, in that we've commuted limits without justification. We can rectify that by bundling together the factors where k differs only in sign, saying $$f_N(x)/x =$$ the product of $$1 - (x/[N \tan(k\pi/N)])^2$$ over $$k$$ in $$(0, N/2)$$. Now we note that the movement of the size of the factors toward their limit is monotonic in $$N$$ (considering the $$k$$-th factor to be 1 when $$N/2 \leq k$$), which yields sufficient justification for commuting the limits.]

[TODO: This is substantively distinct from, yet still reminiscent of, the 3blue1brown proof above; discuss the relation between these]

# Weierstrass-Hadamard Factorization Theorem

[TODO; note that people often cite the mere Weierstrass factorization theorem in this connection, but we really need the Hadamard one]

We observe with analysis fiddling that the product $$\pi x \prod_{n \geq 1} \left(1 + \frac{x}{n}\right) \left(1 + \frac{x}{-n}\right)$$ establishes a function which is $$O(e^{\abs{x} + \epsilon})$$ with zeros of multiplicity $$1$$ at each integer. As $$\sin(\pi x)$$ also has the same order and same zeros, their ratio is thus also of this order with no zeros [TODO: Hm, we need to bound the reciprocal of one of these away from zero, except at its zeros, hm]. Thus, as every nonzero entire function has a well-defined logarithm (unique up to additive constant), their ratio is $$e^{g(x)}$$ for some $$g(x) = O(\abs{x} + \epsilon)$$. But any entire function which is $$O(\abs{x} + \epsilon)$$ is in fact of the form $$a_0 + a_1 x$$, by calculating its Taylor series coefficients using Cauchy's integral theorem (this is a strengthened form of Liouville's theorem). By the fact that sine is odd, we see that $$a_1 = 0$$, and by comparing values at $$x = 0$$, we see that $$e^{a_0} = 1$$, and thus we are done.

# The Herglotz trick

Let $$f(x) = \frac{1}{x} + \sum_{n \geq 1} \frac{1}{n + x} + \frac{1}{-n + x}$$. Morally, this is $$\sum \frac{1}{n + x}$$ over ALL integers $$n$$, and modulo appropriate fiddling, we can therefore see that this is a periodic function with period $$1$$. Also, with appropriate analysis fiddling which I shall take as granted for now, we see that this is continuous and finite, except for the poles at the integers.

These properties match $$g(x) = \pi \cot(\pi x)$$, and the two have matching residues at their poles; thus, their difference is also a function of period $$1$$, and is in fact finite and continuous everywhere, with value zero at the integers.

We now establish that $$f(x)$$ and $$g(x)$$ both have the property that their value at a given $$x$$ is the average of their values at all N choices of $$x/N$$ in mod 1 world (i.e., $$x/N, (x + 1)/N, (x + 2)/N \ldots, (x + N - 1)/N$$).

*[For f, this fact is basically immediate; for g, TODO; it corresponds to the mutatis mutandis fact about the product of $$\sin(x)$$ taken at an even number of regularly spaced intervals around its half-period, or just as well, to the corresponding fact about $$\mathrm{Chord}(x) = 2 \sin(x/2)$$, for which we have that the product of this chord function at n equally spaced angles around a full revolution is equal to its value at n times any of those individual angles (this is demonstrated in the 3blue1brown video above!)]*

This property descends to their difference, and also means that, from the limit as N goes infinite, this function's value at $$x$$ is equal to its average over the entire continuous interval from $$x$$ to $$x + 1$$; by periodicity, this is unchanged by adding any real value to $$x$$. (This works for the difference but not for the original $$f$$ and $$g$$ because the difference is finite everywhere (in addition to being continuous), and thus has a well-defined such average (approachable in this way), which fails for $$f$$ and $$g$$). Since the difference was 0 at the integers, we see that it is in fact 0 at all reals, and thus $$f = g$$ for real inputs.

More generally, our analysis fiddling that establishes g to be continuous apart from its poles should actually be carried out to establish that g is meromorphic; then the difference becomes meromorphic as well, and its being constantly 0 along reals then establishes it as constantly 0 for all complex numbers. [Maybe there's some generalized averaging property that gives this directly as well; averaging over n imaginary in some sense?]

# Eisenstein series

[TODO: See http://www.math.ucla.edu/~vsv/fullnotes.pdf ]

# Nyquist-Shannon-Whittaker sampling and interpolation theorem
Note that the cotangent series we are interested in is equivalent to the observation that $$\mathrm{sinc}(\pi x)$$, when summed as an alternating series over all its integer translations, yields $$\cos(\pi x)$$. This is an instance of the general observation that a frequency-limited signal [such as $$\cos(\pi x)$$] can be reconstructed as a weighted sum of translated sincs at regular intervals. [TODO: Expand on this]. It's clear that the weighted sum of translated sincs gets the appropriate values at the sample points, so what remains is only to observe that a frequency-limited signal cannot be zero at every sample point without being zero simpliciter (the uniqueness argument; the Nyquist theorem).

Essentially, if f and F are Fourier transforms of each other, then f being frequency-limited means F being band-limited in its support. And f being limited to a regular-spaced-points in its support means F being periodic. We can go back and forth between band-limited and periodic functions in an obvious bijection, and this corresponds to going back and forth on the other side of the Fourier transform by either throwing away the values outside regular-spacing or performing sinc convolution to recover them.

It may be easier to show that the NON-alternating sum of sincs is constantly 1, and then deriving the alternating sum result from this in suitable fashion. Things are a little complicated by the cosine being right on the cusp of the critical frequency. But the non-alternating sum of sincs being 1 tells us that $$\ldots + 1/x - 1/(x + 1) + 1/(x + 2) - \ldots = \pi/\sin(\pi x)$$. 

Perhaps we should really just cite the Poisson summation formula here and be done with it.

# Odds and ends
Note that we can think of our fundamental formula as $$\sin(\pi x) \propto x(x + 1)(x - 1)(x + 2)(x - 2) \ldots$$. A note of caution is that this would seem to be periodic with period 1, but actually, a limit calculation concerning this conditionally convergent product shows that it negates whenever $$x$$ is increased by 1, so it is actually periodic with period 2.