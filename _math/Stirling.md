---
title: "Stirling's approximation"
date: 2020-09-05
---
Where does Stirling's approximation $$n! \sim \sqrt{2\pi n} \left(\frac{n}{e}\right)^n$$ come from?

Well, $$n! = \prod_{t = 1}^{n} t$$, a discrete product. One obvious way to try to approximate a solution for $$n!$$ is to switch from discrete series to continuous series. People don't like to talk about multiplicative integrals (though it would be perfectly fine), they like to put things into additive terms, so let's go ahead and apply a logarithm to turn all our multiplications into additions. Define $$L(n) = \log(n!) = \sum_{t = 1}^{n} \log(t)$$. Now, if we approximate the discrete summation with a continuous integral, we're looking at the integral of the natural logarithm from $$0$$ (or just as well from $$1$$; from anywhere we want our logarithmic factorial to be zero) up through $$n$$. This comes out to $$n (\log(n) - 1)$$. Undoing the logarithm, this gives us an approximation of $$A(n) = \left(\frac{n}{e}\right)^n$$ for $$n!$$.

How good is this approximation? Does it even satisfy the recurrence defining the factorial? Well, $$\frac{A(n + 1)}{A(n)} = \left(1 + \frac{1}{n}\right)^n (n + 1) e^{-1}$$. This isn't quite the same as $$(n + 1)$$, but it's close. Put another way, $$\frac{A(n + 1)/(n + 1)!}{A(n)/n!} = \left(1 + \frac{1}{n}\right)^n e^{-1}$$.

For large $$n$$, this of course approaches $$1$$. But in general, this tells us that $$\frac{A(n)}{n!} = e^{-1} \prod_{t = 1}^{n - 1} \left(1 + \frac{1}{t}\right)^t e^{-1}$$.

What is the asymptotic behavior of this series? Well, again, people like to talk about things summatively rather than multiplicatively, so let's apply a logarithm. This turns our series into $$-1 + \sum_{t = 1}^{n - 1} [t \log \left(1 + \frac{1}{t} \right) - 1] = -1 + \sum_{t = 1}^{n - 1} [-\frac{1}{2t} + \frac{1}{3t^2} - \frac{1}{4t^3} + \ldots]$$, using the Mercator series expansion of the logarithm.

Asymptotically, we have that $$\sum_{t = 1}^{n - 1} -\frac{1}{2t} \approx -\frac{1}{2} \log(n) = \log(n^{-1/2})$$, while all the further summations of $$\sum_{t = 1}^{n - 1} [\frac{1}{3t^2} - \frac{1}{4t^3} + \ldots]$$ converge as $$n \to \infty$$. The $$\approx$$ here represents a difference which also converges as $$n \to \infty$$ (this amounts to the existence of the Euler-Mascheroni constant $$\gamma$$). Thus, overall, we find that $$\frac{A(n)}{n! n^{-1/2}}$$ approaches a constant as $$n$$ grows large.

In other words, $$n! \sim F \sqrt{n} \left(\frac{n}{e}\right)^n$$, for some constant $$F$$. This is Stirling's approximation.

What is the value of that constant $$F$$? Well, this can be determined by using the duplication formula for the factorial.

# Duplication/Multiplication Formula
Let $$f_M(x) = \prod_{T = 0}^{M - 1} [\left(x - \frac{T}{M}\right)!]$$. Note that $$f_M(x/M) M^{x}$$ clearly satisfies the same "pseudopolynomiality" and recurrence as a function of $$x$$ that $$x!$$ does. So the two are equal up to a constant of proportionality, which is readily determined. See this discussion of the [generalized factorial](./FactorialGeneralized.html).

That is, there is some $$\lambda(M)$$ such that $$f_M(x/M) M^{x} = x! \lambda(M)$$. Put another way, $$f_M(x) = (Mx)! M^{-Mx} \lambda(M)$$.

This is the "multiplication theorem"; when $$M = 2$$, people call it the "duplication theorem".

But what is $$\lambda(M)$$? Well, plugging in $$x = 0$$, it's clear that $$\lambda(M)$$ is $$f_M(0)$$, the product of $$x!$$ over all rational $$x$$ in $$(-1, 0]$$ with denominator $$M$$. In particular, $$\lambda(2)$$ is $$(-1/2)!$$. But we can say more about the general behavior of this $$\lambda(M)$$ as a function of $$M$$.

Observe that $$f_{MN}(x)$$ can be decomposed as $$\prod_{T = 0}^{N - 1} f_M \left(x - \frac{T}{MN} \right)$$. By our multiplication theorem, the left-hand side here is $$(MNx)! (MN)^{-MNx} \lambda(MN)$$. And the right-hand side is $$\prod_{T = 0}^{N - 1} [\left(Mx - \frac{T}{N} \right)! M^{-Mx + \frac{T}{N}} \lambda(M)] = M^{-MNx} M^{(N - 1)/2} \lambda(M)^N f_N(Mx)$$, which by applying the multiplication theorem again, is $$(MNx)! (MN)^{-MNx} M^{(N - 1)/2} \lambda(M)^N \lambda(N)$$.

Identifying our two sides, we find $$\lambda(MN) = M^{(N - 1)/2} \lambda(M)^N \lambda(N)$$. If we now write $$g(M) = \lambda(M) M^{1/2}$$, we find that $$g(MN) = g(M)^N g(N)$$. Symmetrically, we also have $$g(MN) = g(N)^M g(M)$$ then. Identifying these two, dividing by $$g(M) g(N)$$, and taking $$(M - 1)(N - 1)$$th roots, we find that there is a constant value $$g(M)^{1/(M - 1)} = g(N)^{1/(N - 1)} = b$$ such that in general $$g(M) = b^{M - 1}$$.

We could derive $$\lambda(M)$$ also like so (essentially the infinite N case of the above): Consider the integral from $$-1$$ to $$0$$ of $$\log(x!)$$. By breaking this up into $$M$$ many intervals, this is equivalently the integral from $$-1/m$$ to $$0$$ of $$\log(f_M(x)) = \log((Mx)!) - M\log(M)x + \log(\lambda(M))$$. The first term here integrates to $$\frac{1}{M}$$ times the whole value, and the second term here integrates to $$\frac{\log(M)}{2M}$$, so we ultimately find $$\left(\int_{-1}^{0} \log(x!) dx\right)(M - 1) - \frac{\log(M)}{2} = \log(\lambda(M))$$. This replicates our formula given above, with $$\int_{-1}^{0} \log(x!) dx$$ as the magic constant $$b$$.

Going back and plugging this all into our original multiplication theorem, we have that $$f_M(x) = (Mx)! M^{-Mx - 1/2} b^{M - 1}$$. As for the actual value of $$b$$, it follows, of course, that $$b = g(2) = \lambda(2) \sqrt{2} = (-1/2)! \sqrt{2}$$, as well as that $$b = \int_{-1}^{0} \log(x!) dx$$ as we just saw.

Now, looking at the Stirling asymptotics on any particular case (perhaps most easily the $$M = 2$$ or $$M = \infty$$ cases) of the multiplication theorem as we look at $$(x + N)!$$ with $$N$$ large, we conclude that the Stirling theorem constant $$F$$ is the same as the multiplication theorem constant $$b$$.

Indeed, just as well, we could've concluded Stirling's theorem directly from the multiplication theorem like so: By the trapezoid rule, we know that $$\int_{0}^{1} \log(x!) dx$$ is equal to $$\log(f_N(1))/N$$ plus an error term which is $$O(N^{-2})$$. But $$\int_{0}^{1} \log(x!) dx = \int_{0}^{1} \log((x - 1)!) + \log(x) dx = b - 1$$, and our multiplication theorem tells us that $$\log(f_N(1)) = \log(N!) - N\log(N) + (N - 1)b - \log(N)/2$$. Thus, $$N (b - 1) = \log(N!) - N\log(N) + (N - 1)b - \log(N)/2 + O(N^{-1})$$, which means $$\log(N!) = b + \log(N)/2 + N(\log(N) - 1) + O(N^{-1})$$, which is Stirling's approximation.

[TODO: If you know the reflection formula $$z!(-z)! = 1/sinc(\pi z)$$, then the multiplication theorem for the factorial is equivalent to a multiplication theorem for sine, by pairing up each (k/M)! with (1 - k/M)! = (-k/M)!(1 - k/M). This multiplication theorem for sine should be the same as what I illustrated in my 3blue1brown video on the sine product. Is there a natural calculus way to turn the gamma function integral into the reflection formula? There's a clear way to get the reflection formula once one has both the infinite products for sine and factorial, of course.]

# How does this relate to $$\pi$$?
But what is $$\left(-\frac{1}{2}\right)!$$? Well...

By applying the Stirling formula to $$\binom{2n}{n} = \frac{(2n)!}{n!^2}$$, we automatically get $$\binom{2n}{n} \sim \frac{4^n}{F \sqrt{n/2}}$$. Note that we can read the Wallis Product in these terms as well. $$ \frac{2}{1} \times \frac{4}{3} \times \frac{6}{5} \times \ldots \times \frac{2n}{2n - 1} = \frac{2^n n!}{\frac{(2n)!}{2^n n!}} = \frac{4^n}{\binom{2n}{n}} \sim F \sqrt{n/2}$$. And $$ \frac{2}{3} \times \frac{4}{5} \times \frac{6}{7} \times \ldots \times \frac{2n}{2n + 1}$$ in the same way comes out to $$\frac{4^n}{\binom{2n}{n}} \times \frac{1}{2n + 1} \sim F \sqrt{n/2} / (2n)$$. Multiplying these together gives us that the Wallis Product comes to $$\frac{F^2}{4}$$.

If we happen to know that the Wallis Product comes to $$\frac{\pi}{2}$$ (see [Wallis Product proved by higher-dimensional geometry]({{ site.baseurl }}{% link _math/WallisProductGeometric.md %}) and [Wallis Product as instance of sine product]({{ site.baseurl }}{% link _math/SineProductProofs.md %})), then we can conclude that $$F = \sqrt{2 \pi}$$.

Actually, this just amounts to using the two-factor multiplication formula implicitly again to relate the Stirling constant to (-1/2)!, and then using the Wallis product to compute (-1/2)!. It's not actually different from the previous. But some may enjoy seeing it presented in this language, instead of in terms of the multiplication formula language.

See also [Donvolution]({{ site.baseurl }}{% link _math/Donvolution.md %}), whose general formula tells us that in particular, the area of a quarter-circle of unit radius is given by $$\left(\frac{1}{2}\right)!^2$$, so that $$\left(\frac{1}{2}\right)! = \sqrt{\pi}/2$$ and thus $$\left(-\frac{1}{2}\right)! = \sqrt{\pi}$$.

# TODO
[TODO: Talk about the full Stirling series and how to derive it as a non-convergent asymptotic expansion. This should be viewed as a series for the trigamma function, as trigamma(z) = sum of B_n/z^(n + 1), using the +1/2 convention (B_n(1)). This can be seen be seeing that G(z) = sum of B_n z^n satisfies the formal recurrence that G(z/(1 - z)) - G(z) = z^2. See Proposition A.1 on page 241 of https://people.mpim-bonn.mpg.de/zagier/files/doi/10.1007/978-4-431-54919-2/curious-bernoulli.pdf. We can also see this just by using the full Euler-Maclaurin formula for integrating log(x!) from 0 to 1 using N steps, or for integrating log(x) from 0 to N using N steps.]

[TODO: Note we can also derive the Stirling approximation from the infinite-factor multiplication formula, by considering (x + N)! as (N * (x/N + 1))!, maybe? This is sort of analogous to the step in the Stirling approximation where we approximate the discrete summation with a continuous integral. Well, some of the stuff we've written above about the relationship between the Stirling approximation and the multiplication theorem is already in this vein.]