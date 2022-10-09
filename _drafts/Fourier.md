---
title: "The Fourier Transform"
date: 2022-7-5
---
UNPOLISHED: Eventually I will record all my thoughts on the Fourier transform here. For now, I just want to record some thoughts about the Fourier inversion theorem.

The Fourier transform is characterized by the fact that the Dirac delta as input is turned into the constantly 1 function as output (or some other constant, but from hereon out I will assume it has been chosen to be 1 for convenience), as well as the property that translation of inputs turns into multiplication by suitable exponentials on the outputs.

It is straightforwardly seen from the definition of the Fourier transform that also, conversely, multiplication by suitable exponentials on inputs turns into translation on the inputs. Note that the translations corresponding to a given exponential are opposite in these two correspondences.

The translation of inputs -> multiplication by exponentials of outputs property immediately generalizes into the property that F(x convolved with y) = F(x) times F(y), by thinking of convolution with x as a linear combination of various translations. Similarly, the multiplication of inputs -> translation of outputs property tells us that F(F(x) times y) = (x reversed) convolved with F(y), again by thinking of convolution with x as a linear combination of suitable translations. (The reversal here comes from the last sentence of the previous paragraph).

If we wish to show that F(F(x)) is proportional to (x reversed), it thus suffices to show that when y is proportional to the unit of multiplication (the constantly 1 function), we have that F(y) is proportional to the unit of convolution (the Dirac delta).

A constant function is characterized by being translation-invariant. To be invariant under any increment of translation is (by the usual global/local correspondence) the same as being invariant under arbitrarily small increments of translation. In a discrete context, there are actually smallest increments available. In a continuous context, invariance under arbitrarily small translations amounts to having zero derivative.

\[We need to be careful here. This sounds like we will be saying that totalling a function is translation-invariant, thus totalling any derivative is zero. But this is only the case on addition reordering grounds when the total of the original function is well-definedly finite; put another way, this is only the case precisely when the original function has the same asymptotic value at -infinity and infinity (in the 1d case). So actually, it is important that we work with something like Schwartz functions, for which we know the relevant Fourier transforms will decay to zero at every extreme. See https://personal.math.ubc.ca/~cass/research/pdf/FT.pdf which gives the exact argument we are giving, but makes sure to use Schwartz functions.\]

The Fourier transform of a constant function is therefore invariant under multiplication by suitable exponentials. In the discrete context, we have some slowest exponentials to be invariant under multiplication by. In the continuous context, having zero derivative turns under the Fourier transform into vanishing when multiplied by the identity function $$x \mapsto x$$.

So what we must show is that the only distributions which are invariant under the conditions of the last paragraph are proportional to the Dirac delta. In the discrete context, this is straightforward. In the continuous context, we need to know that the only distributions which vanish when multiplied by $$x \mapsto x$$ are proportional to the Dirac delta. 

Choose a space of test functions which take finite values everywhere, are smooth, are closed under secants, and have Fourier transforms which have finite total integral (e.g., Schwartz space). Observe that a test function vanishes at the origin if and only if it is divisible by $$x \mapsto x$$ (in the trivial direction, this follows from the fact that our test functions have well-defined finite values at the origin which vanish when multiplied by zero. In the less trivial direction, this follows from the fact that our test functions have secants). Thus, the Fourier transform of a constant function, construed as a functional on such test functions, only depends on the value of the test function at the origin. This is precisely what it is to be proportional to the Dirac delta.

(Note that there are distribution whose support is just the origin (or rather, an infinitesimal neighborhood of the origin) which aren't the Dirac delta; the derivative of the Dirac delta, for example! Our argument makes use of a property which is stronger than just having support constrained to the origin.)

Finally, we may wish to show that this constant of proportionality is in fact positive. This is easy in the discrete case again (easily seen to be N for the order N discrete Fourier transform). In the continuous case, this can be handled by some specific calculation. We just need to find any test function which is positive at the origin, and show that its Fourier transform has a total value which is positive. If we take any nonzero input which is real-valued and even, then convolve it with itself, we will obtain some function which is positive at the origin, and whose Fourier transform is everywhere positive (as the square of a real-valued even function), thus with positive total.

An example of this is the Fejer kernel. Note that the Fejer kernel is positive because it is a square of a real-valued even function; that is, on the other side of the Fourier transform, it is a convolution-square of a real-valued even function. It's very nearly the square of the Dirichlet kernel, in fact: a Fejer kernel is like taking the odd index terms only from a Dirichlet kernel and squaring that.

Perhaps a simpler example, which is similar but more continuous rather than discrete in flavor, is by considering a continuous compact triangle wave, which is the self-convolution of a continuous compact rectangle wave. Its Fourier transform is thus the square of the sinc function.

***

We could instead think of the Fourier transform as a particular bilinear functional on two spaces: It sends $$f$$ and $$g$$ to $$\int f(x) g(y) R^{xy} \; dx \; dy$$. This makes translation on either side correspond to multiplication by a corresponding exponential on the other side. This is probably the better way to think of it.

Note that even though the Dirac delta is not a proper function, it still acts like a functional in a straightforward way in this framework. E.g., $$\int_{y = -\infty}^{\infty} \int_{x = -\infty}^{\infty} e^{2 \pi i x y} g(y) \; dx \; dy = g(0)$$ for sufficiently nice (e.g., smooth fast-decaying) $$g$$.

***

When a function is Fourier transformed, and then Fourier transformed back, the units of its output change. The output multiplies by a product of a width in the function's domain and a width in the Fourier transform's domain.

The specific product of these widths by which it multiplies is (in the case of a Fourier transform in any of the familiar 1D senses using periodic exponentials on domains modulo the period) the period of the exponential.

We can also think of this constant as $$\int R^{x, y} \; dx \; dy$$. Note that this comes out straightforwardly to N in a typical discrete Fourier transform of order N. Even in the case of $$\int e^{2 \pi i x y} \; dx \; dy$$, which is not convergent in the standard sense, we can make this convergent by Abel summation (that is, looking at $$\lim_{a \to \infty} \int m(x/a, y/a) e^{2 \pi i x y} \; dx \; dy$$ for sufficiently smooth $$m(x, y)$$ such as $$m(x, y) = e^{-x^2 - y^2}$$. Presumably some sort of Cesaro summation also works already.

We can also re-parametrize this as a Gauss sum.

***

Gauss sums: Let $$\mathbb{Z}_n = \mathbb{Z}/(n \mathbb{Z})$$ and let $$R = e^{2 \pi i}$$.

Suppose we want to compute $$\sum_{index \in \mathbb{Z}_n} R^{index^2/n}$$. We can do this by Poisson summation, letting $$f(x) = R^{x^2/n}$$ on the interval $$[0, n]$$ and zero elsewhere. Omitting some details, the Fourier transfom of $$f$$ summed at integer points becomes $$(1 + R^{-n/4}) \sqrt{n} \int_{-\infty}^{\infty} R^{x^2} \; dx$$. The last integrand here is the Fresnel integral. By considering $$n = 1$$, we see that this integral is $$\frac{1}{1 - i}$$. Thus, the sum in general comes out to $$\frac{1 + R^{-n/4}}{1 - i} \sqrt{n}$$.

There is also a purely algebraic proof that works to establish the square of the Gauss sum (thus, the Gauss sum up to sign) in favorable circumstances (e.g., in $$\mathbb{Z}_n$$ for odd $$n$$). Consider the sum of $$R^{xy}/n$$ over all $$x, y \in \mathbb{Z}_n$$. By doing an order 2 DFT, we have $$x' = (x + y)/2, y' = (x - y)/2, xy = x'^2 - y'^2$$. So we are looking at the sum of $$R^{x'^2/n} R^{-y'^2/n}$$, and the two factors can be separately summed and then multiplied together by Fubini's theorem.

Thus, the Gauss sum times the conjugate Gauss sum equals the sum of $$R^{xy}/n$$. But we know the latter is $$n$$ (the sum for any fixed nonzero $$x$$ cancels out, while the sum for zero $$x$$ contains $$n$$ many terms of value $$1$$).

This tells us the magnitude of the Gauss sum is $$\sqrt{n}$$. The fact that the Gauss sum is purely real or purely imaginary according as to the residue of $$n$$ modulo $$4$$ is also easy to establish (at least when $$n$$ is prime; TODO).

We can also establish algebraically that when $$n = 2 \pmod{4}$$, the Gauss sum is zero (TODO). But the case where $$n = 0 \pmod{4}$$ seems tricky to handle by purely algebraic means (TODO).

***

We can decompose $$\int R^{xy} \; dx \; dy$$ as $$2(\int R^{x'^2} \; dx')(\int R^{-y'^2} \; dy')$$ in the same way over the full real plane and real lines. The factor of 2 is because in this continuous context (as opposed to a counting measure context), we have that $$2 dx' dy' = dx dy$$. As we already saw, the Fresnel integral comes out to $$\frac{1}{1 - i}$$, so its conjugate is $$\frac{1}{1 + i}$$, and twice the product of these is $$1$$.

We can also find this same constant for the scaling factor in double-applying the Fourier transform on the real line by considering the action on a Poisson comb (and how this relates to Fourier series for periodic functions).

***

Particularly unpolished:

Legendre transform: Note with the Legendre transform (defined as L(f) = sup_{y}(y * x - f(x)), which is the Fourier transform in a tropical semiring, except for this negation instead of addition sign change convention), we have that L is order reversing (increasing f decreases L(f)) and L^2(f) ≤ f. Thus, L^3(f) = L(f), and L^2(f) is the largest fixed point of L^2 below f.

Note that the output of L is always a convex function, as it is a supremum of convex functions. Conversely, any convex f satisfies f = L^2(f). Thus, the fixed points of L^2 are precisely the convex functions.

Put another way, let Linf(f) = Inf_y(f(x) - x * y), while Lsup(f) = Sup_y(f(x) + x * y). Then Lsup(Linf(f)) = L^2(f). And it's easy to see that Lsup(Linf(f)) is the convex hull of f. Linf sends each potential slope to the smallest value at the origin with which a line of such slope could intersect the graph of f. Lsup(Linf(f)) then takes the supremum of all these tangent lines to the graph of f.

***

Alternative argument for inversion theorem (extracted from Theorem 1.5.1 in Rudin's Fourier Analysis on Groups):

Recall the property F(x convolved with y) = F(x) times F(y).

Recall also the property F(F(x) times y) = (x reversed) convolved with F(y) from above.

Finally, keep in mind that F(reverse x) = reverse F(x), and reverse similarly threads through multiplications and convolutions.

Let x, y, and z be arbitrary. We have F(x) convolve (reverse z) convolve F(y) = F( F((reverse F(x)) convolve z) times y) = F( (reverse FF(x)) times F(z) times y). Evaluating this at 0, we get the total integral of (reverse FF(x)) times y times F(z).

But by symmetry, our starting point was also F(y) convolve (reverse z) convolve F(x), and so our ending point is also the total integral of (reverse FF(y)) times x times F(z).

Thus, as long as the range of values of F(z) is dense enough with respect to this dot product, we may conclude that (reverse FF(x)) times y = (reverse FF(y)) times x for arbitrary x and y. In other words, the multiplicative ratio of reverse F(F(x)) to x does not depend on x.

In particular, this means that this ratio stays the same even when x is translated, which also translates F(F(x)), and thus also translates the multiplicative ratio. Thus, this multiplicative ratio is a constant.

Thus, reverse F(F(x)) is proportional to x in general, concluding the inversion theorem. [Modulo concerns about dividing by zero in producing this ratio]