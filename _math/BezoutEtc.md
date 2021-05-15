---
title: "Partial Fractions, Jordan, Bezout, Euclid, and the Chinese"
date: 2020-5-1
---
There are a number of results which are all essentially the same:

1\. Jordan decomposition of linear operators.

2\. Partial fraction decomposition.

3.1. The Chinese Remainder Theorem.

3.2. Bezout's theorem expressing GCDs as linear combinations

3.3. The Euclidean algorithm for calculating GCDs

It seems to me that everyone who is familiar with the topics recognizes 3.2 as the same as 3.3, and most recognize 3.1 as the same as well. Tons of undergrads use 2 without recognizing that it is the same as 3, but at least occasionally mathematicians acknowledge this. I've never seen anyone acknowledge that 1 is the same as the rest, which is a shame.

Anyway, enough about what others do or don't recognize. Here's what you should understand:

[TODO]

# Jordan decomposition

Suppose you have a linear operator $$T$$ on a vector space over a field, which satisfies a polynomial equation $$P(T) = 0$$ [as, for example, every linear operator on a finite-dimensional space is forced to eventually do].

As the polynomials over a field comprise a Euclidean domain (a fortiori, a principal ideal domain, equivalently, a unique factorization domain which happens to also be a Bezout domain), we can factorize $$P(T)$$ as a product of coprime factors, each of these factors in turn a power of an irreducible polynomial. If the field is algebraically closed, these irreducible polynomials will be linear, but there is no need for us to restrict our attention to this case.

Letting these coprime factors be $$F_i$$ for various $$i$$, we have that the gcd of $$\frac{P}{F_i} = \prod_{j \neq i} F_j$$ over all $$i$$ is $$1$$. We can therefore write $$1$$ as a linear combination of the various $$\frac{P}{F_i} = \prod_{j \neq i} F_j$$. [This is the same as doing the partial fraction decomposition of $$\frac{1}{P}$$, then multiplying both sides through by $$P$$].

We can now instantiate this polynomial equation at $$T$$. Each of these $$\frac{P(T)}{F_i(T)}$$ terms is such that it is annihilated by $$F_i(T)$$, since $$P(T) = 0$$. This means each such term has a range, as an operator on vectors, which is in the null space of $$F_i(T)$$. Thus, this demonstrates that every vector is a sum of "generalized eigenvectors", in the sense of vectors in the null space of $$F_i(T)$$ for the various $$i$$.

On the other hand, if $$v$$ is a vector which is already in the null space of $$F_i(T)$$, then our factorization tells us that $$1v = \frac{P(T)}{F_i(T)} v$$, as all the other terms contain a factor of $$F_i(T)$$ already, which annihilates against our $$v$$. Thus, we see that each $$\frac{P(T)}{F_i(T)}$$ acts as a retraction onto the nullspace of $$F_i(T)$$, which sends all the other generaliezd eigenspaces to zero. Among other things, this tells us that the representation of a vector as a sum of generalized eigenvectors is unique; the entire vector space is the coproduct of the generalized eigenspaces corresponding to each of our prime power polynomial factors.

This is the Jordan decomposition. If we were working over an algebraically closed field, the prime power polynomials would each be of the form $$(T - \lambda)^n$$, and so these generalized eigenspaces take the form of familiar Jordan blocks [TODO: here, it is worth getting into the form of nilpotent operations a bit more as well, perhaps; how they are characterized by the dimensions of the iterated preimages of 0]. But regardless, there is this form of Jordan decomposition over arbitrary fields as well.

# Partial fraction decomposition

This is often phrased as being specifically about polynomials, but it applies to the elements of any Bezout domain. The observation is this: Suppose $$P$$ has a factorization as a product of $$F_i$$, where the $$F_i$$ are coprime. [In the case of a Euclidean domain or PID, which are automatically UFDs, we always have this factorization available into powers of distinct primes. And in particular, in the case of polynomials over an algebraically closed field, the primes will be linear factors. But regardless, this idea generalizes.]

Then $$P$$ is the least common multiple of the various $$F_i$$, which is to say, $$\frac{1}{P}$$ is the gcd of the various $$\frac{1}{F_i}$$ [put another way, $$1$$ is the gcd of the various $$\frac{P}{F_i}$$. In general, we can interpret the divisibility relationship on "rationals" to mean their quotient is a "whole value", and will have gcds and lcms in the same way for "rationals" as we do for "whole values", in any GCD domain].

This means, by Bezout's theorem, that we can express $$\frac{1}{P}$$ as a linear combination of the various $$\frac{1}{F_i}$$. And this is just what is called "partial fraction decomposition". For example, $$\frac{1}{2^2 \times 3} = -\frac{1}{2^2} + \frac{1}{3}$$.

[TODO: Discuss 3.1, 3.2, and 3.3]

[TODO: Discuss structure theorem for modules over a PID?]

Part of the structure theorem for modules over a PID is showing that any torsion-free finitely generated module is free and of finite rank. Why does this hold? It suffices to show inductively that given free module R^(n + 1) and taking some quotient of it which leaves the first R^n component unquotiented and the last R component unquotiented [that is, adding one new non-torsion generator at a time to a free module], the result is itself a free module of finite rank.

Here, let us observe that the kernel of our quotient of R^(n + 1) is in fact principal. This is because its projection onto the final R component is a principal ideal, thus generated by a single element r, for which there is some corresonding (a, b, c, ..., r) in this kernel. From any other value (x, y, z, ..., mr) in this kernel, we can produce (ma - x, mb - y, mc - z, ..., 0) in this kernel. But this kernel is supposed to leave the initial R^n unquotiented, so (ma - x, mb - y, mc - z, ..., 0) = 0, and thus m(a, b, c, ..., r) = (x, y, z, ..., mr), which is to say, (a, b, c, ..., r) is indeed a generator for this kernel.

What's more, by torsion freeness, we can assume that either (a, b, c, ..., r) is (0, 0, 0, ..., 0) or gcd(a, b, c, ..., r) = 1. In the former case, we are done, we are just dealing with R^(n + 1). So what remains is to show that taking the quotient of R^(n + 1) by the ideal generated by some (a, b, c, ..., r) with gcd(a, b, c, ..., r) = 1 yields a free module of finite rank. TODO