---
title:  "Stirling's approximation"
date: 2020-09-05
---
Where does Stirling's approximation $$n! \sim \sqrt{2\pi n} \left(\frac{n}{e}\right)^n$$ come from?

Well, $$n! = \prod_{t = 1}^{n} t$$, a discrete product. One obvious way to try to approximate a solution for $$n!$$ is to switch from discrete series to continuous series. People don't like to talk about multiplicative integrals (though it would be perfectly fine), they like to put things into additive terms, so let's go ahead and apply a logarithm to turn all our multiplications into additions. Define $$L(n) = \log(n!) = \sum_{t = 1}^{n} \log(t)$$. Now, if we approximate the discrete summation with a continuous integral, we're looking at the integral of $$\log(t) dt$$ from $$0$$ (or just as well from $$1$$; from anywhere we want our logarithmic factorial to be zero) up through $$n$$. This comes out to $$n (\log(n) - 1)$$. Undoing the logarithm, this gives us an approximation of $$A(n) = \left(\frac{n}{e}\right)^n$$ for $$n!$$.

How good is this approximation? Does it even satisfy the recurrence defining the factorial? Well, $$\frac{A(n + 1)}{A(n)} = \frac{\left(1 + \frac{1}{n}\right)^n (n + 1)}{e}$$. This isn't quite the same as $$(n + 1)$$, but it's close. Put another way, $$\frac{A(n + 1)/(n + 1)!}{A(n)/n!} = \frac{\left(1 + \frac{1}{n}\right)^n}{e}$$.

For large $$n$$, this of course approaches $$1$$. But in general, this tells us that $$\frac{A(n)}{n!} = \prod_{t = 1}^{n - 1} \frac{\left(1 + \frac{1}{t}\right)^t}{e}$$.

What is the asymptotic behavior of this series? Well, again, people like to talk about things summatively rather than multiplicatively, so let's apply a logarithm. This turns our series into $$\sum_{t = 1}^{n - 1} [t \log \left(1 + \frac{1}{t} \right) - 1] = \sum_{t = 1}^{n - 1} [-\frac{1}{2t} + \frac{1}{3t^2} - \frac{1}{4t^3} + \ldots]$$, using the Mercator series expansion of the logarithm.

Asymptotically, we have that $$\sum_{t = 1}^{n - 1} -\frac{1}{2t} \approx -\frac{1}{2} \log(n) = \log(n^{-1/2})$$, while all the further summations of $$\sum_{t = 1}^{n - 1} \sum_{d = 2}^{\infty} \frac{1}{(d + 1)t^d}$$ converge as $$n \to \infty$$. The $$\approx$$ in the first line of this paragraph also represents a difference which converges as $$n \to \infty$$ (this amounts to the existence of the Euler-Mascheroni constant). Thus, overall, we find that $$\frac{A(n)}{n! n^{-1/2}}$$ approaches a constant as $$n$$ grows large.

In other words, $$n! \sim K \sqrt{n} \left(\frac{n}{e}\right)^n$$, for some constant $$K$$. This is Stirling's approximation.

What is the value of that constant $$K$$? Well, this can be determined by using the duplication formula for the factorial. [TODO!]

[TODO: Talk about the full Stirling series and how to derive it as a non-convergent asymptotic expansion]