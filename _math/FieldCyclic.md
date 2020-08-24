---
title:  "Field Multiplication Cyclicity"
date: 2019-12-2
---
Let $$G$$ be a finite subgroup of the multiplicative group of a field. We shall show that it is cyclic.

In fact, we will show something far stronger: if $$G$$ is a group with at most $$n$$ solutions to $$x^n = 1$$ (i.e., at most $$n$$ elements of order dividing $$n$$) for each $$n$$, then every finite subgroup of $$G$$ is cyclic. (Note that we do not even presume abelianness here, though we will get it as a consequence). A field's multiplicative group of course satisfies the stated property by the fact that a polynomial of degree $$n$$ can have at most $$n$$ distinct roots.

Proof: Let $$G$$ be finite and have at most $$n$$ elements of order dividing $$n$$, for each $$n$$; we shall show that $$G$$ is cyclic.

Let $$g$$ be any element in $$G$$, of order $$n$$; note that the powers of $$g$$ will then provide $$n$$ many values of order dividing $$n$$. This is the maximum allowed by our presumption. Thus, these are ALL the values of order dividing $$n$$, and among them, we find that precisely $$\phi(n)$$ are of order precisely $$n$$ [where $$\phi$$ refers to the Euler totient function; see also [Möbius inversion]({{ site.baseurl }}{% link _math/MoebiusInversion.md %})].

Thus, there are either zero or $$\phi(n)$$ many values of order $$n$$, for each $$n$$. Can there be zero values of order $$ \vert G \vert $$? No, for summing up the upper bound $$\phi(n)$$ over all proper divisors of $$ \vert G \vert $$ [^Lagrange], we get $$ \vert G \vert  - \phi( \vert G \vert )$$; since this is less than $$ \vert G \vert $$, these proper divisor orders cannot account for all the elements of the group, and thus there must be at least one (indeed, precisely $$\phi( \vert G \vert )$$) many elements of order $$ \vert G \vert $$, i.e. generating the entire group, completing our proof.

***
Footnotes:

[^Lagrange]: Remember, by Lagrange's theorem, every element's order must divide $$ \vert G \vert $$.