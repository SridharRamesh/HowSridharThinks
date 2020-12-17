---
title: "Difference Equations, Infinite Sums, Generalized Factorial, Zeta Functions, Etc"
date: 2019-11-19
---
Suppose given a difference relation $$F(x + 1) - F(x) = f(x)$$, where $$f$$ is known but $$F$$ is not. What should $$F$$ be?

Of course, there are many choices of $$F$$; on each equivalence class of integer-separated inputs, we can choose one starting value arbitrarily at one input, and get a corresponding version of $$F$$.

But if we add in the idea that $$F(x + N)$$ should approach $$0$$ as $$N$$ approaches infinity, then $$F$$ is uniquely determined. For we have that $$F(x) = -f(x) - f(x + 1) - f(x + 2) - ... - f(x + N - 1) + F(x + N)$$, and if this last term must approach $$0$$, then $$F(x)$$ must be the sum of the infinite series $$-f(x) - f(x + 1) - f(x + 2) - \ldots$$.

This only works if $$f$$ has the appropriate convergence property, of course. If $$f$$ does not have the appropriate convergence property, there will be no solution with the desired asymptotics.

Note next that, given the difference relation $$F(x + 1) - F(x) = f(x)$$, then by taking derivatives, we find that this entails also the difference relation $$F'(x + 1) - F'(x) = f'(x)$$. And by iterating, we obtain just as well $$F^{(n)}(x + 1) - F^{(n)}(x) = f^{(n)}(x)$$, for derivatives of any order.

[TECHNICAL FOOTNOTE: For our purposes here, the derivative (or perhaps we should say "differential"?) of a function means just information about the differences in this function's values at different inputs; i.e., the derivative is just the information of the function up to an additive constant. Derivatives have no purpose other than to be integrated across intervals between two points, and are considered equal when their integrals across all intervals are equal. Similarly, second derivatives have no purpose but to be integrated across parallelograms of four points, tracking the difference between sums of the original function over the two parities of vertices, and so on. Among other things, this means nothing here depends on working over any kind of continuous domain; this all makes sense even in purely discrete contexts.]

We might hope that this process would be invertible; that is, that any solution to the derivative difference equation is indeed the derivative of a unique solution to the original difference equation. ...Well, unique is too much to hope for, as the original difference equation is unaffected by addition of a constant to $$F$$, but such constants will vanish in its derivative. But we may still hope that any solution to the derivative difference equation at least describes up to an additive constant SOME solution to the original difference equation.

Well, observe: Given any $$G$$ satisfying $$G(x + 1) - G(x) = f'(x)$$, we may consider $$F(x + 1) - F(x)$$ for any antiderivative $$F$$ of $$G$$. We will find that $$F(x + 1) - F(x)$$ is some antiderivative of $$f'(x)$$. It may not be $$f(x)$$, though! All that is guaranteed is that its difference from $$f(x)$$ is some constant. ...Uh-oh.

However!

Given any $$G$$ satisfying $$G(x + 1) - G(x) = f'(x)$$, after we go ahead and compute the constant $$C = -f(x) + \int_{x}^{x + 1} G$$, we can now look for an antiderivative not of $$G$$, but of $$G - C$$. Let $$F$$ be an antiderivative of $$G - C$$. Then $$F(x + 1) - F(x) = \int_{x}^{x + 1} (G - C) = f(x) + C - C = f(x)$$. This $$F$$ satisfies the desired difference equation; furthermore, its derivative is $$G$$ plus some constant. Indeed, this is the unique solution up to an additive constant to our original difference equation whose derivative is $$G$$ up to an additive constant.

[TECHNICAL FOOTNOTE: Implicit here is that there is a unique linear function taking any particular value at $$1$$. This requires us to be working over a "torsion-free" codomain, so to speak (and "one-dimensional" domain). Otherwise, for example, working over a codomain modulo 1, "Increase at integer speed" for any of infinitely many possible different speeds is a solution to $$F(x + 1) - F(x) = 0$$ whose derivative is constant and whose second derivative vanishes.]

Thus, when differentiation is viewed as an operation whose inputs and outputs are both only up to an additive constant, it yields a bijection between solutions to a difference equation and solutions to the derivative difference equation. Iterating in this same way, higher differentiation induces a bijection between solutions to a difference equation and solutions to any higher derivative of that difference equation, again when both are treated as up to an additive constant.

Along with our uniqueness result from before, and the fact that any function which vanishes in the limit also has a derivative which vanishes in the limit [Technical note: for this last claim, keep in mind our notion of derivative is in terms of total differences, and not instantaneous rates of change!], it follows that any difference equation has at most one solution up to an additive constant with the property that any of its higher derivatives asymptotically vanish.

[TODO: Discuss constant. There's some sort of normalization property to note where the constant will always be $$-f^{(n - 1)}(\infty)$$.]

Specifically, if $$f^{(n)}(x) + f^{(n)}(x + 1) + f^{(n)}(x + 2) + \ldots$$ converges, then the unique up to an additive constant solution to $$F(x + 1) - F(x) = f(x)$$ which has any higher derivatives asymptotically vanish is one whose $$n$$-th derivative is $$-f^{(n - 1)}(\infty) + f^{(n)}(x) + f^{(n)}(x + 1) + f^{(n)}(x + 2) + \ldots$$. Higher derivatives follow from this term-wise. Lower derivatives follow by integrating this and choosing appropriate additive constants to satisfy the appropriate difference equations.

As applications of this: There is up to an additive constant precisely one function $$L(x)$$ such that $$L(x) - L(x - 1) = \log(x)$$ with some higher derivative vanishing asymptotically. When we set the constant such that $$L(0) = 0$$, this is the logarithmic factorial function. Since the second derivative of $$\log(x)$$ is $$-\frac{1}{x^2}$$, which has the appropriate convergence property, while the first derivative of $$\log(x)$$ vanishes asymptotically, we see that the second derivative of $$L(x)$$ is $$\frac{1}{x^2} + \frac{1}{(x + 1)^2} + \frac{!}{(x + 2)^2} + \ldots$$; i.e., the Hurwitz zeta function at degree $$-2$$.

[TECHNICAL FOOTNOTE: We presume throughout this a particular branch of $$\log(x)$$; specifically, the one such that $$\log(x)$$ has infinitesimal imaginary component when $$x$$ has infinite positive real component. Otherwise, we could consider things like $$R^x x!$$ for some unit periodic base of exponentiation $$R$$, still satisfying the recurrence, initial condition, and vanishing second logarithmic derivative conditions of the factorial, while differing from the standard generalized factorial at fractional arguments. This is related to our observation about torsion-free codomains from earlier, given the natural $$2 \pi i$$ torsion to impose on the codomain of the logarithm.]

We can also find unique-up-to-an-additive constant asymptotically-vanishing-higher-derivative $$F(x)$$ such that $$F(x) - F(x - 1) = x^p$$ for each power $$p$$. Differentiating these and then dividing by $$p$$ gives us the Hurwitz zeta function (and makes its pole location clear). [TODO: Discuss analyticity with respect to $$p$$; this is because we have a complex derivative with respect to $$p$$, derived from the function satisfying the corresponding recurrence for $$\frac{d}{dp} x^p$$]. Then specializing to starting value $$1$$ gives us the Riemann zeta function. This is a much nicer approach to its analytic continuation, I think, than I've ever seen anyone write up anywhere.

[TODO: Describe the fully explicit finitary formula for the construction in this post, using the fact that our derivatives are purely finitary]

[TODO: Relate to https://howsridharthinks.wordpress.com/2018/06/27/the-meta-formula-for-1n-2n-3n-xn/, in the case where $$f(x)$$ is polynomial so its higher derivative vanishes completely. All this amounts to is that we can calcualate the Bernoulli polynomials straightforwardly, by repeatedly integrating starting from the constantly 0 function, and picking the right constants.]

[TODO: Investigate how to carry out the Fourier-theoretic proof of the functional equation for the zeta functions, and particularly in the context of this approach to the analytic continuation]

[TODO: Because of the relationship between decay of a function and the smoothness of its Fourier transform, this approach to finding F from f should amount to something like, in Fourier transformed space, dividing Fourier(f) by 1 - R^x for suitable base R to get Fourier(F), choosing the sufficiently smooth result of this division to handle the ambiguity at the zeros of 1 - R^x. Flesh this out.]