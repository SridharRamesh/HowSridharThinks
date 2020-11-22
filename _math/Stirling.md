---
title:  "Stirling's approximation"
date: 2020-09-05
---
Where does Stirling's approximation $$n! \sim \sqrt{2\pi n} \left(\frac{n}{e}\right)^n$$ come from?

Well, $$n! = \prod_{t = 1}^{n} t$$, a discrete product. One obvious way to try to approximate a solution for $$n!$$ is to switch from discrete series to continuous series. People don't like to talk about multiplicative integrals (though it would be perfectly fine), they like to put things into additive terms, so let's go ahead and apply a logarithm to turn all our multiplications into additions. Define $$L(n) = \log(n!) = \sum_{t = 1}^{n} \log(t)$$. Now, if we approximate the discrete summation with a continuous integral, we're looking at the integral of the natural logarithm from $$0$$ (or just as well from $$1$$; from anywhere we want our logarithmic factorial to be zero) up through $$n$$. This comes out to $$n (\log(n) - 1)$$. Undoing the logarithm, this gives us an approximation of $$A(n) = \left(\frac{n}{e}\right)^n$$ for $$n!$$.

How good is this approximation? Does it even satisfy the recurrence defining the factorial? Well, $$\frac{A(n + 1)}{A(n)} = \left(1 + \frac{1}{n}\right)^n (n + 1) e^{-1}$$. This isn't quite the same as $$(n + 1)$$, but it's close. Put another way, $$\frac{A(n + 1)/(n + 1)!}{A(n)/n!} = \left(1 + \frac{1}{n}\right)^n e^{-1}$$.

For large $$n$$, this of course approaches $$1$$. But in general, this tells us that $$\frac{A(n)}{n!} = e^{-1} \prod_{t = 1}^{n - 1} \left(1 + \frac{1}{t}\right)^t e^{-1}$$.

What is the asymptotic behavior of this series? Well, again, people like to talk about things summatively rather than multiplicatively, so let's apply a logarithm. This turns our series into $$-1 + \sum_{t = 1}^{n - 1} [t \log \left(1 + \frac{1}{t} \right) - 1] = -1 + \sum_{t = 1}^{n - 1} [-\frac{1}{2t} + \frac{1}{3t^2} - \frac{1}{4t^3} + \ldots]$$, using the Mercator series expansion of the logarithm.

Asymptotically, we have that $$\sum_{t = 1}^{n - 1} -\frac{1}{2t} \approx -\frac{1}{2} \log(n) = \log(n^{-1/2})$$, while all the further summations of $$\sum_{t = 1}^{n - 1} [\frac{1}{3t^2} - \frac{1}{4t^3} + \ldots]$$ converge as $$n \to \infty$$. The $$\approx$$ here represents a difference which also converges as $$n \to \infty$$ (this amounts to the existence of the Euler-Mascheroni constant). Thus, overall, we find that $$\frac{A(n)}{n! n^{-1/2}}$$ approaches a constant as $$n$$ grows large.

In other words, $$n! \sim F \sqrt{n} \left(\frac{n}{e}\right)^n$$, for some constant $$F$$. This is Stirling's approximation.

What is the value of that constant $$F$$? Well, this can be determined by using the duplication formula for the factorial.

# Duplication Formula
Let $$f_M(x) = \prod_{T = 0}^{M - 1} [\left(x - \frac{T}{M}\right)!]$$. Note that $$f_M(x/M) M^{x}$$ clearly satisfies the same "pseudopolynomiality" and recurrence as a function of $$x$$ that $$x!$$ does. So the two are equal up to a constant of proportionality, which is readily determined. [TODO: Link to Generalized Factorial.]

That is, there is some $$\lambda(M)$$ such that $$f_M(x/M) M^{x} = x! \lambda(M)$$. Put another way, $$f_M(x) = (Mx)! M^{-Mx} \lambda(M)$$.

This is the "multiplication theorem"; when $$M = 2$$, people call it the "duplication theorem".

But what is $$\lambda(M)$$? Well, plugging in $$x = 0$$, it's clear that $$\lambda(M)$$ is $$f_M(0)$$, the product of $$x!$$ over all rational $$x$$ in $$(-1, 0]$$ with denominator $$M$$. In particular, $$\lambda(2)$$ is $$(-1/2)!$$. But we can say more about the general behavior of this $$\lambda(M)$$ as a function of $$M$$.

Observe that $$f_{MN}(x)$$ can be decomposed as $$\prod_{T = 0}^{N - 1} f_M \left(x - \frac{T}{MN} \right)$$. By our multiplication theorem, the left-hand side here is $$(MNx)! (MN)^{-MNx} \lambda(MN)$$. And the right-hand side is $$\prod_{T = 0}^{N - 1} [\left(Mx - \frac{T}{N} \right)! M^{-Mx + \frac{T}{N}} \lambda(M)] = M^{-MNx} M^{(N - 1)/2} \lambda(M)^N f_N(Mx)$$, which by applying the multiplication theorem again, is $$(MNx)! (MN)^{-MNx} M^{(N - 1)/2} \lambda(M)^N \lambda(N)$$.

Identifying our two sides, we find $$\lambda(MN) = M^{(N - 1)/2} \lambda(M)^N \lambda(N)$$. If we now write $$g(M) = \lambda(M) M^{1/2}$$, we find that $$g(MN) = g(M)^N g(N)$$. Symmetrically, we also have $$g(MN) = g(N)^M g(M)$$ then. Identifying these two and setting $$N = 2$$, we have that $$g(M)^2 g(2) = g(2)^M g(M)$$, and by dividing by $$g(M)$$ [manifestly nonzero], we see $$g(M) = g(2)^{M - 1}$$. Thus, $$\lambda(M) = g(2)^{M - 1} M^{-1/2}$$.

In particular, recall we have that $$(-1/2)! = \lambda(2)$$, and thus we must have in general that $$\lambda(M) = \left((-1/2)! \sqrt{2}\right)^{M - 1} M^{-1/2}$$.

Going back and plugging this into our multiplication theorem, we have that $$f_M(x) = (Mx)! M^{-Mx - 1/2} \left( (-1/2)! \sqrt{2} \right)^{M - 1}$$.

[TODO: Observe how the M = infinity case viewed logarithmically is like the integral of $$log(x!)$$ from $$-1$$ to $$0$$, as a Riemann sum]

Now, looking at the Stirling asymptotics on any particular case (perhaps most easily the M = 2 or M = infinity cases) of the multiplication theorem as we replace $$x$$ by $$x + n$$ with $$n$$ large, we conclude that $$F = \left(-\frac{1}{2}\right)! \sqrt{2}$$. But what is $$\left(-\frac{1}{2}\right)!$$? Well... [TODO: Link to Donvolution, or to Wallis Product]

# Another Way To Determine The Constant
By applying the Stirling formula to $$\binom{2n}{n} = \frac{(2n)!}{n!^2}$$, we automatically get $$\binom{2n}{n} \sim \frac{4^n}{F \sqrt{n/2}}$$. Note that we can read the Wallis Product in these terms as well. $$ \frac{2}{1} \times \frac{4}{3} \times \frac{6}{5} \times \ldots \times \frac{2n}{2n - 1} = \frac{2^n n!}{\frac{(2n)!}{2^n n!}} = \frac{4^n}{\binom{2n}{n}} \sim F \sqrt{n/2}$$. And $$ \frac{2}{3} \times \frac{4}{5} \times \frac{6}{7} \times \ldots \times \frac{2n}{2n + 1}$$ in the same way comes out to $$\frac{4^n}{\binom{2n}{n}} \times \frac{1}{2n + 1} \sim F \sqrt{n/2} / (2n)$$. Multiplying these together gives us that the Wallis Product comes to $$\frac{F^2}{4}$$.

If we happen to know that the Wallis Product comes to $$\frac{\pi}{2}$$ (see [Wallis Product proved by higher-dimensional geometry]({{ site.baseurl }}{% link _math/WallisProductGeometric.md %}) and [Wallis Product as instance of sine product]({{ site.baseurl }}{% link _math/SineProductProofs.md %})), then we can conclude that $$F = \sqrt{2 \pi}$$.

Actually, this just amounts to using the two-factor multiplication formula implicitly again to relate the Stirling constant to (-1/2)!, and then using the Wallis product to compute (-1/2)!. It's not actually different from the previous. But some may enjoy seeing it presented in this language, instead of in terms of the multiplication formula language.

# TODO
[TODO: Talk about the full Stirling series and how to derive it as a non-convergent asymptotic expansion]

[TODO: Note we can also derive the Stirling approximation from the infinite-factor multiplication formula, by considering (x + N)! as (N * (x/N + 1))!]