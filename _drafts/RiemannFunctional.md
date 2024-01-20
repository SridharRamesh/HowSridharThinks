[TODO: Markup]

Recall that there is a one-dimensional space of even homogenous distributions of degree -s, for each complex s. (Similarly for odd homogenous distributions, but we will not be concerned with these). When s is not a positive odd integer, these are the constants times |x|^-s. (When s is a positive odd integer, these are the constants times the s-th derivative of the signum function. But we will not be concerned with these either.)

On evenness and homogenity grounds, we may conclude that the Fourier transform (which for us will always mean the Fourier transform sending x |-> f(x) to y |-> to the integral of f(x) e^(2 π i x y) dx) of an even homogenous distribution of degree -s is an even homogenous distribution of degree -1 + s. (Again, similarly for odd distributions, but nevermind.)

Thus, for s which is neither a positive odd integer nor a nonnegative even integer [but otherwise may be any complex number], we may define a function k(s) such that the Fourier transform of |x|^(-s) is k(s) |x|^(-1 + s).

By re-applying this rule, we will have that k(s) * k(1 - s) = 1.

The exact nature of k(s) is not important to us right now, though we will see its form later.

----

Observe that if f is any function which is its own Fourier transform, then the integral f(x) |x|^(-s) dx over the entire real line is equal [by the unitarity of the Fourier transform, and thinking of this as a dot product between f and the other function] to k(s) times the integral of f(x) |x|^(-1 + s) dx over the entire real line.

Thus, we have obtained a function F(s) = the integral f(x) |x|^(-s) dx over the entire real line = the Mellin transform of f, such that F(s) = k(s) F(1 - s).

Note how we find that this F(s)/F(1 - s) ratio is the same function k(s) whenever F is the Mellin transform of ANY fixed point of the Fourier transform.

----

If we think of the Riemann zeta function ζ(s) as roughly 1/2 * (DiracComb(x) - Dirac(x) - 1) integrated against |x|^-s dx over the entire real line [everything here makes sense except the -1, but maybe(??) we can think of -1 integrated against |x|^-s dx as, with a change of variables x = e^y, something like Dirac(si) and thus ignorable for s ≠ 0??], then by observing that 1/2 * (DiracComb(x) - Dirac(x) - 1) is a fixed point of the Fourier transform, we have by the above ζ(s) = k(s) ζ(1 - s).

This is the Riemann functional equation. However, we may wish to remove any doubt (given the handwaving over the "-1" term here, for example, or concerns about the inability to have both Re(s), Re(1 - s) ≥ 1 so that ζ(s), ζ(1 - s) are both given by the naive sum converging) with a more rigorous approach:

----

Let f be any fixed point of the Fourier transform and define p(x) = the sum of f(nx) over all integers n [including 0 and negatives].

By Poisson summation of the function y |-> f(xy), whose Fourier transform is y |-> 1/x * f(y/x), we have that p(x) = 1/x * p(1/x). Put another way, p(1/x) = x * p(x).

Now presume f furthermore even [WLOG, we may restrict f to its even component] and let q(x) = (p(x) - f(0))/2 = the sum of f(nx) over all POSITIVE integers n.

Note that q(1/x) = (x * p(x) - f(0))/2 = x * q(x) + f(0) (x - 1)/2.

Let us now integrate q(x) x^s dx from 0 to infinity. We get the integral from 1 to infinity of q(x) x^s dx + the integral from 0 to 1 of q(x) x^s dx. [Note to self: I suppose I should've done x^(-s) here instead of x^s to keep with convention, but whatever…]

In the latter integral, let us do a change of variables, with y = 1/x and thus dx = (-1/y^2) dy. Thus we may re-express this integral as the integral from 1 to infinity of q(1/y) y^(-s - 2) dy = the integral from 1 to infinity of q(y) y^(-s - 1) dy + f(0)/2 * [y^(-s - 1) - y^(-s - 2)] dy.

The integral of the [y^(-s - 1) - y^(-s - 2)] dy part from 1 to infinity comes out to 1/s + 1/(-s - 1), presuming Re(s) > 0.

So we get overall the integral from 1 to infinity of q(x) [x^s + x^(-s - 1)] dx + f(0)/2 * [1/s + 1/(-s - 1)].

This is manifestly meromorphic (with only the given poles at s = 0 and s = -1), and invariant under repalcing s with -1 - s.

Thus we get the functional equation that the integral of q(x) x^s dx from 0 to infinity [meromorphically extended to the entire complex plane] is invariant under replacing s with -1 - s.

This was the sum of the integral f(nx) x^s dx over all real x and all positive integers n. By rescaling x by a factor of n, this is the sum of the integral f(x) x^s dx n^(-s - 1) over all positive integers n. Thus, ζ(s + 1) times the Mellin transform of a fixed point f of the Fourier transform (or rather, M(-s) where M is the Mellin transform as defined with kernel |x|^(-s) as before). So ζ(s + 1) M(-s) is invariant under replacing s with -1 - s. Thus, ζ(s + 1) M(-s) = ζ(-s) M(1 + s). Or put another way, ζ(1 - s) M(s) = ζ(s) M(1 - s). Since M(s) = k(s) M(1 - s), we have ζ(1 - s) k(s) M(1 - s) = ζ(s) M(1 - s). Dividing by M(1 - s), we have ζ(s) = k(s) ζ(1 - s).

This is the functional equation we sought.