---
title: "The Fourier Transform"
date: 2022-7-5
---
Eventually I will record all my thoughts on the Fourier transform here. For now, I just want to record some thoughts about the Fourier inversion theorem.

The Fourier transform is characterized by the fact that the Dirac delta as input is turned into the constantly 1 function as output (or some other constant, but from hereon out I will assume it has been chosen to be 1 for convenience), as well as the property that translation of inputs turns into multiplication by suitable exponentials on the outputs.

It is straightforward seen from the definition of the Fourier transform that also, conversely, multiplication by suitable exponentials on inputs turns into translation on the inputs. Note that the translations corresponding to a given exponential are opposite in these two correspondences.

The translation of inputs -> multiplication by exponentials of outputs property immediately generalizes into the property that F(x convolved with y) = F(x) times F(y), by thinking of convolution with x as a linear combination of various translations. Similarly, the multiplication of inputs -> translation of outputs property tells us that F(F(x) times y) = (x reversed) convolved with F(y), again by thinking of convolution with x as a linear combination of suitable translations. (The reversal here comes from the last sentence of the previous paragraph).

If we wish to show that F(F(x)) is proportional to (x reversed), it thus suffices to show that when y is proportional to the unit of multiplication (the constantly 1 function), we have that F(y) is proportional to the unit of convolution (the Dirac delta).

A constant function is characterized by being translation-invariant. To be invariant under any increment of translation is (by the usual global/local correspondence) the same as being invariant under arbitrarily small increments of translation. In a discrete context, there are actually smallest increments available. In a continuous context, invariance under arbitrarily small translations amounts to having zero derivative.

The Fourier transform of a constant function is therefore invariant under multiplication by suitable exponentials. In the discrete context, we have some slowest exponentials to be invariant under multiplication by. In the continuous context, having zero derivative turns under the Fourier transform into vanishing when multiplied by the identity function $$x \mapsto x$$.

So what we must show is that the only distributions which are invariant under the conditions of the last paragraph are proportional to the Dirac delta. In the discrete context, this is straightforward. In the continuous context, we need to know that the only distributions which vanish when multiplied by $$x \mapsto x$$ are proportional to the Dirac delta. Observe that a test function in Schwarz space vanishes at the origin if and only if it is divisible by $$x \mapsto x$$ (in the trivial direction, this follows from the fact that our test functions have well-defined finite values at the origin which vanish when multiplied by zero. In the less trivial direction, this follows from the fact that Schwarz space is closed under differentiation). Thus, the Fourier transform of a constant function, construed as a functional on test functions in Schwarz space, only depends on the value of the test function at the origin. This is precisely what it is to be proportional to the Dirac delta.

(Note that there are distribution whose support is just the origin (or rather, an infinitesimal neighborhood of the origin) which aren't the Dirac delta; the derivative of the Dirac delta, for example! Our argument makes use of a property which is stronger than just having support constrained to the origin.)

Finally, we may wish to show that this constant of proportionality is in fact positive. This is easy in the discrete case again (easily seen to be N for the order N discrete Fourier transform). In the continuous case, this can be handled by some specific calculation. We just need to find any test function which is positive at the origin, and show that its Fourier transform has a total value which is positive. If we take any nonzero input which is real-valued and even, then convolve it with itself, we will obtain some function which is positive at the origin, and whose Fourier transform is everywhere positive (as the square of a real-valued even function), thus with positive total.

An example of this is the Fejer kernel. Note that the Fejer kernel is positive because it is a square of a real-valued even function; that is, on the other side of the Fourier transform, it is a convolution-square of a real-valued even function. It's very nearly the square of the Dirichlet kernel, in fact: a Fejer kernel is like taking the odd index terms only from a Dirichlet kernel and squaring that.

Perhaps a simpler example, which is similar but more continuous rather than discrete in flavor, is by considering a continuous compact triangle wave, which is the self-convolution of a continuous compact rectangle wave. Its Fourier transform is thus the square of the sinc function.