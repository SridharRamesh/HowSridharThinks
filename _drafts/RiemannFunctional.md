[TODO: Markup]

Recall that there is a one-dimensional space of even homogenous distributions of degree -s, for each complex s. (Similarly for odd homogenous distributions, but we will not be concerned with these). When s is not a positive odd integer, these are the constants times |x|^-s. (When s is a positive odd integer, these are the constants times the s-th derivative of the signum function. But we will not be concerned with these either.)

On evenness and homogenity grounds, we may conclude that the Fourier transform (which for us will always mean the Fourier transform sending x |-> f(x) to y |-> to the integral of f(x) e^(2 π i x y) dx) of an even homogenous distribution of degree -s is an even homogenous distribution of degree -1 + s. (Again, similarly for odd distributions, but nevermind.)

Thus, for s which is neither a positive odd integer nor a nonnegative even integer [but otherwise may be any complex number], we may define a function k(s) such that the Fourier transform of |x|^(-s) is k(s) |x|^(-1 + s).

By re-applying this rule, we will have that k(s) * k(1 - s) = 1.

The exact nature of k(s) is not important to us right now, though we will see its form later.

(Incidentally, one corollary of this is that k(1/2) = 1 and |x|^(-1/2) is its own Fourier transform. Or rather, we can quickly see that either this is true or that k(1/2) = -1 and |x|^(-1/2) is the negation of its Fourier transform. I suppose a bit more work is involved to see that its Fourier transform is specifically positive.)

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

This is manifestly meromorphic (with only the given poles at s = 0 and s = -1), and invariant under replacing s with -1 - s. [TODO: Why is it manifestly meromorphic? Presumably because Mellin transforms are meromorphic interior to their region of convergence. That this Mellin transform is convergent everywhere presumably depends on f.]

Thus we get the functional equation that the integral of q(x) x^s dx from 0 to infinity [meromorphically extended to the entire complex plane] is invariant under replacing s with -1 - s.

This was the sum of the integral f(nx) x^s dx over all real x and all positive integers n. By rescaling x by a factor of n, this is the sum of the integral f(x) x^s dx n^(-s - 1) over all positive integers n. Thus, ζ(s + 1) times the Mellin transform of a fixed point f of the Fourier transform (or rather, M(-s) where M is the Mellin transform as defined with integration kernel |x|^(-s) as before). So ζ(s + 1) M(-s) is invariant under replacing s with -1 - s. Thus, ζ(s + 1) M(-s) = ζ(-s) M(1 + s). Or put another way, ζ(1 - s) M(s) = ζ(s) M(1 - s). Since M(s) = k(s) M(1 - s), we have ζ(1 - s) k(s) M(1 - s) = ζ(s) M(1 - s). Dividing by M(1 - s), we have ζ(s) = k(s) ζ(1 - s).

This is the functional equation we sought. This also gives the analytic continuation of ζ as ζ(s + 1) M(-s) / M(-s). Of course, different choices of f give different choices of M here. [TODO: Presumably, it is important to pick an f such that the numerator and denominator here are both convergent on the entire complex plane]

----

TODO: By Poisson summation reasoning, letting Rexp(x) = e^(2πix) and letting Z(a, b, s) = the sum of Rexp(an) |n + b|^(-s) over all integers n, we find a relationship between Z(a, b, s) and Z(-b, a, 1 - s). [First in the range 0 < Re(s) < 1, so these series are actually convergent, then extended to arbitrary s by meromorphic continuation.]

Since Z(a, b, s) only depends on the values of a or b mod 1, we can also write this as a relationship between Z(a, b, s) and Z(1-b, a, 1 - s), which will be convenient for reasons which will become apparent in a second.

More specifically, let L(a, b, s) = the sum of Rexp(an) |n + b|^(-s) over all POSITIVE integers n. Then we have that Z(a, b, s) = L(a, b, s) + Rexp(-a) L(-a, 1 - b, s) for b in [0, 1]. (The absolute value in |n + b| is what leads to this particular restriction on b in this formula.)

From now on, presume both a and b to be real and in (0, 1) (avoiding the endpoints so that we don't have to think about 0^(-s) or 0^-(1 - s)).

Now our relationship between Z(a, b, s) and Z(1 - b, a, 1 - s) can be seen as a relationsip between four L terms.

TODO: Derive from this the three L term functional equation for real non-integer a and b, as in the proof of (1.4) from (2.4) in "ON THE LERCH ZETA FUNCTION" by Apostol. (This seems to involve considering the analogue of our existing Z relationship where we use |n + b|^(-s) * sgn(n + b) instead of just |n + b|^(-s). Perhaps we can directly reason about this with Poisson summation type reasoning again. We get the same four L terms but with different coefficients. Then we add our two Z relationships together, which cancels away one of the L terms and leaves us with a three L term relationship. Perhaps this is also like using Poisson summation on u(x) * x^s.)

By continuity, presume this three L term functional equation continues to hold for integer a or b as well, whenever we have Re(s) < 0 such that we can ignore the 0^(-s) term on one side. (The advantage of this three L term functional equation is that we only have the one 0^(-s) term show up, without any 0^(-(1 - s)) term to also worry about.) Then generalize this to arbitrary s by meromorphic continuation.

Then the Hurwitz zeta functional equation is a special case of that, and the Riemann zeta functional equation is a special case of that.

---------

Better approach to everything:

Let ζ(s, a) be the sum of (n + a)^(-s) over natural numbers n. This is the Hurwitz zeta function.

Let P(s, a) be the sum of f(n + a) over all integers n, where f(x) = u(x) * x^(-s). This is clearly periodic in a.

Note that P(s, a) = ζ(s, a) for 0 < a < 1.

By Poisson summation, P(s, a), viewed as a function of a with s fixed, has a Fourier series whose coefficients are given by the Fourier transform of f, evaluated at the integers. This Fourier series will converge back to P wherever P is, say, differentiable (again, as a function of a), or even just left and right differentiable (in the sense of being continuous and having directional derivatives in both directions, possibly not matching; if the function is otherwise continuously differentiable, this amounts to a jump discontinuity in the derivative).

As ζ(s, a) is differentiable in a, so is P(s, a) as a ranges over (0, 1). Furthermore, if ζ(s, 0) = ζ(s, 1) [i.e., if 0^(-s) = 0; i.e., if Re(s) < 0], then the left and right limits of P(s, a) as a approaches any integer will match and equal this as well.

One remaining hitch is that when Re(s) < 0, our definitions of ζ(s, a) and P(s, a) don't actually converge. But rather, we will interpret P(s, a) as the unique periodic function whose average value is zero and whose sufficiently high derivatives are given by the appropriate convergent series. TODO

We can split ζ(s, a) into ζ(s, a + 1) + a^(-s). Now suppose we want to take the Fourier series corresponding to evaluating this over 0 < a < 1. The regime where we can handle ζ(s, a + 1) as a sum, with furthermore convergent integrals for its Fourier series, is with Re(s) > 1 (note in particular that we will not have difficulty with the integrand a^(-s) blowing up at a = 0, because these integrals will be of (a + 1)^(-s) exp(i * whatever) from a = 0 to 1 instead). The regime where we can handle a^(-s) with convergent integrals for its Fourier series will be with Re(s) < 1 (so that a^(-s + 1) approaches 0 at a = 0). These are different regimes, but both ζ(s, a + 1) and a^(-s) satisfy nice properties relating shifting s to differentiating wrt a. Thus, we will be able to obtain their Fourier series in the separate nice s regimes for each, then hopefully turn this into their Fourier series in some overlapping s regime of interest, thus obtaining a Fourier series for ζ(s, a) in that regime.

***

Some resources:

https://dept.math.lsa.umich.edu/~lagarias/TALK-SLIDES/ucsd-starkconf2013sep.pdf
https://msp.org/pjm/1951/1-2/pjm-v1-n2-p01-s.pdf
https://www.jstor.org/stable/2031757?read-now=1&seq=2#page_scan_tab_contents
https://fixedpointtheoryandalgorithms.springeropen.com/articles/10.1186/1687-1812-2013-70
https://sci-hub.st/https://doi.org/10.1186/1687-1812-2013-70
https://www.jstor.org/stable/2032062?read-now=1&seq=1#page_scan_tab_contents

***

## Defining the zeta functions

Recall from our previous discussion of [difference equations](./DifferenceEquationZeta.html) that there is a unique function $$F(p, x)$$ such that we have:
1. $$F(p, x) = (p + 1) \sum_{n \in \nat} x^p$$ whenever $$\Re(p) < -1$$
2. $$\frac{d}{dx} F(p, x) = (p + 1) F(p - 1, x)$$
3. $$\int_{x = \beta + 1}^{\beta} F(p, x) \; dx = \beta^(p + 1)$$, for all values of $$\beta$$.

Furthermore, this unique function $$F(p, x)$$ is complex-differentiable with respect to $$p$$ as well.

Note that given condition (2) at exponent $$p - 1$$, we find that condition (3) at exponent $$p$$ is equivalent to saying $$F(p, x) - F(p, x + 1) = (p + 1) x^p$$.

Where $$s \neq 1$$, we define the Hurwitz zeta function as $$\zeta(s, x) = F(-s, x)/(-s + 1)$$ and the Riemann zeta function as $$\zeta(s) = \zeta(s, 1)$$. The factor $$(p + 1)$$ was included in the conditions above just to make $$F(p, x)$$ nicely defined and finite at $$p = 1$$, whereas these zeta functions will have a pole at their corresponding $$s = - 1$$.

Our conditions on $$F(p, x)$$ straightforwardly yield corresponding conditions on $$\zeta(s, x)$$. (TODO)

To be pedantically unambiguous, in the above definition of $$F$$, we interpret $$x^p = \exp(p \log(x))$$ by taking $$\log$$ as the natural logarithm assuming real values on positive inputs and then analytically continued to $$\Re(x) \geq 0$$, $$x \neq 0$$. (We could continue it even further, but will have no need for this. This punctured closed half-plane is the domain of $$x$$ for our purposes.)

For those not interested in reading the previous link (or thinking in any abstraction beyond this specific difference equation, though that abstraction makes things cleaner), the unique existence argument for $$F$$ is like so:

Suppose we weaken condition (3) to the condition (3') only demanding this hold at a particular value of $$\beta$$ (call this particular value $$\beta_0$$). Then, for any constant $$\alpha$$ (fix any choice of $$\alpha$$ you like, it doesn't matter), the conjunction of conditions (2) and (3) is equivalent to demanding that $$F(p, x) = F^*(p, x)$$, where $$F^*(p, x)$$ is defined as $$G(p, x) + \beta_0^{p + 1} - \int_{t = \beta_0 + 1}^{\beta_0} G(p, t) \; dt$$, with $$G(p, x)$$ defined as $$\int_{t = \alpha}^{x} (p + 1) F(p - 1, t) \; dt$$. Note furthermore that this definition of $$x \mapsto F^*(p, x)$$ is defined at all choices of $$p$$ such that the function $$x \mapsto F(p - 1, x)$$ is defined.

Thus, starting with a function $$F(p, x)$$ defined for $$\Re(p) < p_0$$ which satisfies conditions (2) and (3') throughout this domain, we may use this definition of $$F^*$$ to uniquely extend $$F$$ in such a way as to satisfy conditions (2) and (3') for all $$p$$ with $$\Re(p) < p_0 + 1$$.

Note also that the explicit definition of $F^*$$ yields an explicit definition of $$\frac{d}{dp} F^*(p, x)$$ in terms of $$\frac{d}{dp} F(p - 1, x)$$. Thus, this unique extension process preserves differentiability in the first argument.

By repeatedly applying this unique extension process to the function described in condition (1) \[which by termwise consideration manifestly satisfies conditions (2) and (3), while furthermore being complex-differentiable in its first argument\], we find a unique function $$F(p, x)$$ defined over all complex $$p$$ satisfying conditions (1), (2), and (3').

Finally, let $$H(p, \beta)$$ be the difference between the two sides of condition (3). By invoking condition (2), we soon find that $$\frac{d}{dx} H(p, \beta) = (p + 1) H(p - 1, \beta)$$. So if condition (3) [which says that $$H$$ vanishes at all $\beta$] holds for exponent $$p - 1$$, and condition (3') [which says that $$H$$ vanishes at $$\beta_0$$] holds for exponent $$p$$, then condition (3) holds for exponent $$p$$. Thus, inductively, we may conclude that condition (3) holds for our $$F$$ at all exponents $$p$$.