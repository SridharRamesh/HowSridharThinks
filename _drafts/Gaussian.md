---
title: "Gaussian Functions"
date: 2022-7-12
---
Some facts about Gaussian functions (exponentiated quadratics):

Let g(x) = Exp(x^2) for some base of exponentiation. Note that g(ax) = g(x)^a^2. In other words, log(g(sqrt(x))) is a linear function of x. This is characteristic of g, in that any f such that f(ax) = f(x)^a^2 is such that f(x) = g(kx) for some k \[possibly a non-real k...\]. Put another way, the characteristic property is that g(ax)g(bx) = g(x)^(a^2 + b^2) = g(sqrt(a^2 + b^2)x).

Now consider the Gaussian in two dimensions, G(x, y) = g(x^2 + y^2) = g(x)g(y). That is, G(x, y) = Exp(q(x, y)) where q(x, y) is the quadratic form x^2 + y^2[^QuadraticForm].

[^QuadraticForm]: We could consider any positive-definite quadratic form q, but we can always reparametrize so q(x, y) = x'^2 + y'^2 for some basis x', y'.

Note that, if V and W are perpendicular vectors, we have that G(V + W) = G(V) G(W), since q(V + W) = q(V) + q(W) (this is essentially the definition of perpendicularity, relative to an arbitrary quadratic form).

Indeed, G is manifestly rotation-invariant, since it is a function of q, which is tautologously rotation-invariant. Thus, the above is just a rotated version of the fact that G splits into independent factors multiplied along the x and y coordinates, each of these factors being 1 at the origin.

Thus, any line through the origin is such that G restricted to this line looks like g, and such that the marginal distribution on this line after perpendicular projection also looks like g. From this, it follows that for any two independent standard Gaussian distributed variables X and Y, and any coefficients a and b, we have that aX + bY is also Gaussian distributed, rescaled from a standard Gaussian distribution by a factor of sqrt(a^2 + b^2).

This is precisely to say that the Fourier transform of a Gaussian distribution also satisfies the characteristic property of our first paragraph. Thus, the Fourier transform of a Gaussian is a Gaussian.

TODO: Word better, more clearly.

***

Gauss sums:

See https://sbseminar.wordpress.com/2008/10/11/the-sign-of-the-gauss-sum/ for one approach. Note that this makes use of the same distance product "Lemma 2" as in the Wallis Product 3blue1brown video.

See https://web.williams.edu/Mathematics/lg5/GaussSum.pdf, https://mast.queensu.ca/~br66/421/gauss_sums_handout.pdf, and https://e.math.cornell.edu/people/belk/numbertheory/GaussSums.pdf. The basic idea is at https://math.stackexchange.com/questions/27489/the-discrete-fourier-transform-of-a-dirichlet-charachter, but when it says "the uniqueness/inversibility of the Fourier transform implies that the other values of 𝜒's Fourier transform must be 0", I don't follow that part.
