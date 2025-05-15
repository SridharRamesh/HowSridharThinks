---
title: "Quadratic Forms"
date: 2020-12-29
---
There are lots of things to say about quadratic forms (or equivalently when division by 2 is available, symmetric bilinear forms, or the symmetric component of arbitrary bilinear forms), a notion which comes up over and over in math. Particularly positive-definite ones (which are often studied under the name "geometry", as this is what the theory of geometry amounts to; an inner product space is a positive-definite quadratic/bilinear form).

But for now, I just want to note down one basic observation: Sylvester's law of inertia. Given an arbitrary finite-dimensional symmetric bilinear form valued in one linearly ordered dimension of scalars, the space it acts on decomposes uniquely into a fixed subspace of degenerate (i.e., orthogonal to everyone) vectors, and quotienting away by those, into a fixed number of dimensions each of orthogonal "positive" and "negative" vectors.

The first part is easy, too easy to deserve comment. Degenerate vectors obviously comprise a subspace, and we can quotient out by it. This part doesn't even require the presumption of finite-dimensionality. [Though, if we have finite-dimensionality of the quotient, we can non-canonically split the quotient, so that the original space is viewed as as direct sum of the quotient and an orthogonal complement of degenerate vectors.]

Anyway, looking at the quotient, now we are left with a non-degenerate form. Let us decompose this into orthogonal vectors, each of nonzero quadratic form.

It suffices inductively just to note that any non-degenerate form on a positive-dimensional space has at least one vector of nonzero form. For then we can split the space into the direct sum of the one-dimensional space spanned by this vector, and its orthogonal complement.

[This orthogonal complement direct sum business is just the classical argument that vectors decompose into parallel and orthogonal components: If $$v$$ has nonzero form, then for any vector $$w$$, we can consider $$(w - \lambda v) \dot v$$. Since $$v \dot v$$ is nonzero, we can uniquely adjust $$\lambda$$ to make this take on any particular value; in particular, there is a unique option to set $$\lambda$$ to $$\frac{w \dot v}{v \dot v}$$, to obtain $$w - \lambda v$$ which is orthogonal to $$v$$, and thus obtain $$w$$ as a unique linear combination of values parallel to and orthogonal to $$v$$.]

So why must there be at least one vector of nonzero form in a positive-dimensional space with a non-degenerate form? Well, because the space is positive-dimensional, there is some nonzero vector $$v$$. Since the form is non-degenerate, there is thus also some nonzero vector $$w$$ such that $$v \dot w \neq 0$$. As our scalars are linearly ordered, any nonzero value doubles to a nonzero value of the same sign, so we can double this equation without difficulty (no worries about characteristic two, that is), to find that $$2 v \dot w \neq 0$$. And now we invoke the observation that $$2v\dot w = (v + w) \dot (v + w) - v \dot v - w \dot w$$, to conclude that out of $$v$$, $$w$$, and $$v + w$$, at least one of these must have nonzero quadratic form, as desired.

We've now shown that any finite-dimensional non-degenerate quadratic form admits some decomposition as orthogonal directions, each with nonzero form. Some number of "positive" and "negative" directions, called its signature. But how do we know this signature is unique? Might not another decomposition (our decomposition process here involved some arbitrary choice) produce a different signature?

TODO

----

Another observation about quadratic forms, unrelated to the above, which is sometimes of interest:

