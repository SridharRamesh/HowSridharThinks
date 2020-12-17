---
title: "Galois Theory and the Fourier Transform"
date: 2020-4-27
---
Consider a base field with a finite degree Galois extension with Galois group cyclic of order $$N$$ with generator $$\varphi$$. Suppose the base field also contains a primitive $$N$$th root of unity (thus, by the general theory of primitive roots of unity in a field, its $$N$$th roots of unity comprise a cyclic group of order $$N$$, and the field also allows division by $$N$$), so that we have the invertible discrete Fourier transform of order $$N$$ available to us.

We wish to show that this must be a radical field extension. First we will show this in the weak sense that every element of the extended field is a sum of $$N$$th roots of values in the base field. Then we will show this in the stronger sense that is there is some single value in the extended field whose $$N$$th power is in the base field, and which when adjoined to the base field generates the extended field.

(Note that the converse, that adjoining a new $$N$$th root to a base field containing a primitive $$N$$th root of unity results in a finite degree Galois extension with Galois group cyclic of order $$N$$, is obvious, with the automorphisms in the Galois group being those which multiply the adjoined value by each $$N$$th root of unity.)

***

By the fundamental theorem of Galois theory, a value lies in the base field just in case it is fixed by $$\varphi$$; put another way, just in case it multiplies by $$1$$ when $$\varphi$$ is applied to it. Since $$\varphi$$ and the identity both preserve multiplicative structure, and any pair of nonzero values are in some ratio, we see that more generally, a nonzero value is an $$M$$th root of someone in the base field just in case it is an eigenvector of $$\varphi$$ (construed as a linear operator with respect to the base field as scalars) whose eigenvalue is an $$M$$th root of unity. Since $$\varphi^N = 1$$, all the eigenvalues of $$\varphi$$ are $$N$$th roots of unity anyway.

Thus, our first task is to show that every value in the extension is a sum of eigenvectors of $$\varphi$$; i.e., that $$\varphi$$ is diagonalizable. But this is immediate by general theory: $$\varphi$$ is a root of a polynomial (in this case, $$\phi^N - 1$$, but it'd work for any polynomial), which splits into distinct linear factors. Jordan decomposition (aka partial fraction decomposition, aka the Chinese Remainder Theorem, etc; see https://howsridharthinks.wordpress.com/2020/05/01/bezout-etc/) then automatically diagonalizes it. We've now proven that every value in the extension field is a sum of $$N$$th roots of values in the base field.

***

The Jordan decomposition is perfectly constructive, so this gives an explicit construction, though actually seeing that construction overtly was elided above.

In the particular case of Jordan decomposition on roots of unity, we get the very pretty Fourier transform, so I'll write out now the specifics of the construction:

Defining $$T(\zeta, x)$$ as the average value of $$\varphi^i(x) / \zeta^i$$ [well-defined for $$N$$th roots of unity $$\zeta$$], we have that $$T(\zeta, x)$$ is always an eigenvector (possibly zero) of $$\varphi$$ with eigenvalue $$\zeta$$. [Incidentally, if $$x$$ is already such an eigenvector, then $$x = T(\zeta, x)$$. That is, $$T(\zeta, -)$$ is a retraction from arbitrary values onto the $$\zeta$$-eigenvectors of $$\varphi$$. Indeed, it specifically is the retraction which sends all eigenvectors with other eigenvalues to zero. This motivates our looking at it in the first place.]

At this point, the wonderful observation is that $$T(-, x)$$ is a (discrete, order $$N$$) Fourier transform of the sequence $$\langle x, \varphi(x), \varphi^2(x), \ldots \rangle$$. Thus, its outputs [all of whose $$N$$th powers lie in the base field, recall] can be inverse Fourier transformed (by essentially the same transform, up to a flip and a rescaling by $$N$$), to recover $$\langle x, \varphi(x), \varphi^2(x), \ldots \rangle$$. And in particular, we recover $$x$$ as the average value of $$T(-, x)$$. Ergo, $$x$$ is a sum of values whose $$N$$th powers lie in the base field.

***

Now let us move on to the stronger task of showing that there is some single value in the extension whose $$N$$th power is in the base field, and which when adjoined to the base field generates the extension. This is a strong form of the primitive element theorem for the particular case of cyclic extensions. WLOG, we can presume the adjoined value to be nonzero, of course.

We want $$x$$ to be a nonzero root of a value in the base field (i.e., an eigenvector of $$\varphi$$) which also generates the entire extension, which by the fundamental theorem of Galois theory is the same as saying it should only be fixed by those powers of $$\phi$$ which are identity (ergo, its corresponding eigenvalue should be a primitive $$N$$th root of unity, corresponding to how $$\varphi$$ has order $$N$$).

The eigenvalues of $$\varphi$$ are closed under multiplication, as $$g(x) = \varphi(x)/x$$ [well-defined for nonzero $$x$$] preserves multiplicative structure just as $$\varphi$$ and the identity function do. Thus, the eigenvalues comprise some multiplicative subgroup of the $$N$$th roots of unity. By the nature of cyclic groups, they will be precisely the $$M$$th roots of unity for some $$M$$ dividing $$N$$. The minimal polynomial of $$\varphi$$ will then be $$\varphi^M - 1$$.

But by the fundamental theorem of Galois theory, the only powers of $$\varphi$$ which are identity are the multiples of $$N$$. Thus, $$M = N$$, which is to say, its eigenvalues include all the $$N$$th roots of unity, and in particular, primitive $$N$$th roots of unity. This establishes what we sought.

The constructive content of the above is this: For every proper factor $$M$$ of $$N$$ (or it would suffice to just consider those proper factors which are $$N$$ divided by a prime), we can find some value in our extension not fixed by $$\phi^M$$, using the fundamental theorem of Galois theory. We can then take the Fourier transform of the orbit of this value under $$\phi$$, and are guaranteed that at some $$N$$th root of unity $$\zeta$$ which is not an $$M$$th root of unity, we get a nonzero Fourier coefficient, which is to say, we can find some value which is sent by $$g$$ to $$\zeta$$. The least common multiple of the orders of all these $$\zeta$$ must be $$N$$, and so there is some product of powers of these $$\zeta$$ by Bezout's theorem which is sent to a primitive $$N$$th root of unity, and taking the corresponding product of powers of their preimages under $$g$$, we find a preimage under $$g$$ of a primitive $$N$$th root of unity. This amounts to a nonzero value whose $$N$$th power lies in the base field, and whose adjunction to the base field generates the entire extension, as desired.

[TODO: Make a Fourier transform post. Link to that]

[TODO: Make a post on Jordan decomposition, aka partial fraction decomposition, aka Bezout's theorem on gcds as linear combinations, aka the Chinese Remainder Theorem, aka the extended Euclidean algorithm, and how all these are the same. Link to that.]

[TODO: I've never seen anyone else mention this connection between the discrete Fourier transform and Galois theory, except for the use of it at https://en.wikipedia.org/wiki/Cubic_equation#Lagrange's_method. Is it out there in the literature somewhere?]

[TODO: Talk about the rest of Galois theory as well. Talk about the abstract model theoretic approach to Galois theory given in Alice Medvedev's paper]

[TODO: Actually, it might be misleading to title this particular post Galois theory and lump it in with the rest of Galois theory construed abstractly, because this is one of the two points in standard Galois theory which do not generalize to or even makes sense as a statement which can be stated in the abstract model theoretic account of Galois theory: the correspondence between cyclic Galois groups and specifically radical extensions. (The other such point is the correspondence between the order of the Galois group and the dimension of the extension as a vector space over the base field.)]

[TODO: Discuss and illustrate in detail how we can use this to produce the solutions in radicals to polynomials of degree < 5; i.e., the quadratic, cubic, and quartic formulas. This amounts to starting with the field Q + all roots of unity [the inverse integers and roots of unity we don't need we might as well toss in; we can then observe that the ones that don't come up in the resulting formula aren't needed for the formula to work], then adjoining less than 5 indeterminates A, B, C, .... The permutation group on the indeterminates induces corresponding automorphisms of this structure. We now define our base field as the values fixed by all permutations, and the extension field as the full structure. It's straightforward to see that this is a finite degree Galois extension whose Galois group is the permutation group on the indeterminates, and that the coefficients of the polynomial (x + A)(x + B)(x + C)... lie in and generate the base field (they are the elementary symmetric functions). A composition series for the permutation group with cyclic factors shows us how to generate the full extension by radical extensions over the base field, and thus gives us a way to represent each root of the polynomial in terms of the coefficients of the polynomial.]

[TODO: Discuss the general theory of arbitrary symmetric functions as generated by elementary symmetric functions. Can this be proven by Galois theory considerations (e.g., considering the arbitrary symmetric functions as a field extension of the field generated by the elementary symmetric functions, and proving that this is finite degree Galois with trivial Galois group)? If not, of course there are inductive ways to show this.]