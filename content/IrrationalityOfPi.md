---
title: "The Irrationality of π^2, and Therefore of π"
date: 2018-06-27
---
There are many “different” proofs of the irrationality of $$\pi$$ which are all based on the same underlying idea. The proof I describe in this post is also based on the same underlying idea as all the other ones you'll find in the wild, but in a different presentation, one I personally find clearest for helping me understand what is going on and in what directions it generalizes. Incidentally, this simple proof shows not only the irrationality of $$\pi$$ but also the irrationality of $$\pi^2$$.

*[Throughout the following, I'll intersperse the pithy argument with bracketed comments giving further details in case the unbracketed gist is too elliptic.]*

Let $$f(x) = \cos(\sqrt{x})$$, and, as is conventional, let $$f'$$ denote its first derivative and more generally $$f^{(N)}$$ denote its $$N$$-th derivative (with respect to $$x$$).

Note that $$f^{(N)} = P(y)f + Q(y)f'$$, where $$y = \frac{1}{4x}$$ and $$P$$ and $$Q$$ are integer coefficient polynomials of degree growing at rate at most linear in $$N$$.

*[This follows inductively from $$f^{(2)}$$ having this form, which is just the fact that $$\cos'' = -\cos$$, translated to this reparametrization. The one other thing to observe for the inductive step is that $$y'$$ is itself an integer coefficient polynomial function of $$y$$ (specifically, $$y' = -4y^2$$). Armed with those two observations, we find that mechanically differentiating $$P(y)f + Q(y)f'$$ once more just yields something else of the same form, with the degrees of the polynomials having gone up by no more than some constant. This establishes the claim right before these brackets.]*

But, for any given $$x$$, we have that $$\abs{f^{(N)}(x)} \sim \abs{f^{(N)}(0)} = \frac{N!}{(2N)!}$$ as $$N$$ grows large.

*[This can be seen from the easy Taylor series expansion of $$f^{(N)}(x)$$. Specifically, by starting with the Taylor series for cosine $$\cos(x) = \sum_{M = 0}^{\infty} (-1)^M \frac{x^{2M}}{(2M)!}$$ (itself a consequence of the aforementioned differential equation $$\cos'' = -\cos$$) and then transforming it accordingly, we find the Taylor series expansion $$f^{(N)}(x) = \sum_{M = 0}^{\infty} (-1)^M \frac{x^{M} (M + N)!}{M!(2(M + N))!}$$. The observation $$\abs{f^{(N)}(0)} = \frac{N!}{(2N)!}$$ is then immediate, and the $$\abs{f^{(N)}(x)} \sim \abs{f^{(N)}(0)}$$ follows from each term in the Taylor series dominating the next as $$N$$ grows large, so that the whole series is dominated by its first term. I've glibly commuted limits in this last sentence's dominance reasoning, but it's justified by Dominated Convergence.]*

Given this super-exponential rate of decay\*, it cannot be that both $$y$$ is rational and $$f$$ and $$f'$$ are in rational ratio.

*[If $$y$$ were rational with lowest-terms denominator $$d$$, then the smallest nonzero\* value integer polynomials of degree $$O(N)$$ in $$y$$ could produce is $$\frac{1}{d^{O(N)}}$$, which is a merely exponential decay rate; any fixed linear combination of such polynomials with weights in rational ratio (i.e., integer multiples of some common weight) would also therefore have a merely exponential decay rate.*

*(\*: One minor pedantic point is that we are presuming here that $$f^{(N)}(x)$$ is nonzero, or at least nonzero for sufficiently large $$N$$, but this is justified by our rate of decay, which is $$\sim$$ a never-zero function).]*

In particular, plug in $$\sqrt{x} = \frac{\pi}{2}$$, at which $$f$$ vanishes, to conclude $$y = \frac{1}{\pi^2}$$ is irrational, which is to say, $$\pi^2$$ is irrational.

More generally, this establishes that wherever $$\cos(z)$$ and $$\mathrm{sinc}(z)$$ are in rational ratio to each other, we must have that $$\frac{1}{z^2}$$ is irrational, which is to say for nonzero such $$z$$ that $$z^2$$ is irrational. (This includes, for what it's worth, the case of complex $$z$$; indeed, the whole thing might as well have been phrased in terms of $$\cosh$$, but people find $$\cos$$ more familiar.)

Of course, the corollary people talk about most is that thus $$\pi$$ itself is irrational.

As it happens, we know even more than this; we know that $$\pi$$ is not merely the square root of an irrational, but is in fact a transcendental number (that is, it is not a root of ANY nonzero polynomial with rational coefficients). The proof of that, and many further transcendentality results, is actually along similar lines as seen here, but worked out to greater extent and sophistication. I shall hope to digest and write that up to my satisfaction as well, some later time.