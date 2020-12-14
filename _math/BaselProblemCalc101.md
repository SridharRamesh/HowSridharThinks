---
title:  "Solving the Basel Problem with Calc 101"
date: 2018-06-27
---
The Basel problem can be solved by simple integration!

Recall that the Basel problem is to determine the value of $$\frac{1}{1^2} + \frac{1}{2^2} + \frac{1}{3^2} + \ldots$$.

Consider $$f(x) = \ldots + e^{-3x} + e^{-2x} + e^{-1x} + e^{0x} + e^{1x} + e^{2x} + e^{3x} + \ldots$$. By double integrating $$f$$, we get $$h(x) = \ldots + \frac{e^{-3x}}{3^2} + \frac{e^{-2x}}{2^2} + \frac{e^{-1x}}{1^2} + \frac{x^2}{2} + \frac{e^{1x}}{1^2} + \frac{e^{2x}}{2^2} + \frac{e^{3x}}{3^2} + \ldots + C_1x + C_2$$. If we can figure out what $$h$$ amounts to with $$C_1$$ and $$C_2$$ chosen to be zero, then we can readily solve the Basel problem, as the Basel sum then amounts to simply $$h(0)/2$$.

Let us go through this in detail. First, observe that $$f(x)$$, which is to say $$\ldots + e^{-3x} + e^{-2x} + e^{-1x} + e^{0x} + e^{1x} + e^{2x} + e^{3x} + \ldots$$, is unchanged by multiplication by $$e^x$$; thus, wherever $$e^x \neq 1$$, we must have $$f(x) = 0$$, at least in some sense.


(When $$e^x$$ does equal $$1$$, on the other hand, $$f(x)$$ is an infinite sum of $$1$$s; this can be made sense of, with $$f$$ turning out to be interpretable as a kind of integrable entity slightly more general than familiar finite-valued functions, but we won't need to worry about this for now.



For those who care pedantically about formal technicalities, I should also note that our $$f(x) = 0$$ result doesn't hold in the traditional formalization of series convergence, as $$f(x)$$ is not a convergent series (its terms do not approach $$0$$, for example), but this equation still holds in a good enough sense for our purposes; for example, $$f$$ is "Cesàro summable", a slight extension of traditional summation-by-convergence which agrees with traditional summation where it is well-defined, and which suffices to formally carry out our argument, should we care to be formal)


Next, consider integrating $$f$$ once, to obtain the particular antiderivative $$g(x) = \ldots + \frac{e^{-3x}}{-3} + \frac{e^{-2x}}{-2} + \frac{e^{-1x}}{-1} + x + \frac{e^{1x}}{1} + \frac{e^{2x}}{2} + \frac{e^{3x}}{3} + \ldots$$ [note the middle $$x$$ term, slightly different from all the rest].

On any range where $$e^x \neq 1$$, we must have that $$g(x)$$ is constant (as its derivative is $$f(x) = 0$$). In particular, we must have that $$g(x)$$ is constant as $$x$$ ranges between $$0$$ and $$2 \pi i$$, the range to which we will restrict all attention from hereon out. But what particular constant is $$g(x)$$ on this range? Well, the answer is the same as the average value of $$g(x)$$ on this range.

But the average value of $$e^{nx}$$ over this range for nonzero $$n$$ is zero (as that average value must be invariant under multiplication by any value of $$e^{nx}$$ inside the range, and some (indeed, most!) of those values will differ from $$1$$; essentially, $$e^{nx}$$ spins around a circle $$n$$ times, whose average value is the origin zero). So in computing the average value of $$g(x)$$ on our range, all terms vanish except for the average value of $$x$$, which will be $$\pi i$$ (halfway between the range's two endpoints).

Thus, $$g(x) = \pi i$$ for $$x$$ between $$0$$ and $$2 \pi i$$. (The same reasoning also tells us that $$g(x) = - \pi i$$ for $$x$$ between $$0$$ and $$-2 \pi i$$, for what it's worth, and more generally, that $$g(x)$$ steps up by $$2 \pi i$$ whenever $$x$$ passes a multiple of $$2 \pi i$$)

Integrating again, we get the particular antiderivative $$h(x) = \ldots + \frac{e^{-3x}}{3^2} + \frac{e^{-2x}}{2^2} + \frac{e^{-1x}}{1^2} + \frac{x^2}{2} + \frac{e^{1x}}{1^2} + \frac{e^{2x}}{2^2} + \frac{e^{3x}}{3^2} + \ldots$$. This must equal $$\pi i x + C$$ for $$x$$ between $$0$$ and $$2 \pi i$$.

Again, to determine the value of this constant $$C$$, we can consider the question of the average value of $$h(x)$$ throughout our range of interest, which again reduces to the average value of the one non-exponential term $$\frac{x^2}{2}$$. By the "power rule" of calculus, the average value of $$\frac{x^2}{2}$$ between $$0$$ and $$2 \pi i$$ is $$\frac{(2 \pi i)^2/3}{2} = -\frac{2}{3} \pi^2$$. This must therefore also equal the average value of $$\pi i x + C$$ on our range, which is $$(\pi i)^2 + C = - \pi^2 + C$$. Thus, we get $$C = \pi^2 - \frac{2}{3} \pi^2 = \frac{1}{3} \pi^2$$.

And therefore $$h(0) = \frac{1}{3} \pi^2$$. And since, as we noted before, the Basel sum comes out to $$h(0)/2$$, we find that the Basel sum is $$\frac{1}{6} \pi^2$$. Ta-da!

What's more, we can carry on integrating in the same way, determining a polynomial expression in $$x$$ for $$\ldots + \frac{e^{-3x}}{3^n} + \frac{e^{-2x}}{2^n} + \frac{e^{-1x}}{1^n} + \frac{x^n}{n!} + \frac{e^{1x}}{1^n} + \frac{e^{2x}}{2^n} + \frac{e^{3x}}{3^n} + \ldots$$ for each natural number $$n$$, and by evaluating this at $$x = 0$$, determining the value of $$\ldots + \frac{1}{(-3)^n} + \frac{1}{(-2)^n} + \frac{1}{(-1)^n} + 0 + \frac{1}{1^n} + \frac{1}{2^n} + \frac{1}{3^n} + \ldots$$. This will come out to zero for odd $$n$$ (the negatively indexed and positively indexed terms cancelling each other out as negated mirror images), but for even $$n$$, we will get interesting results (which we can divide by two, in just the same fashion as we did here, to restrict attention to just the positively indexed terms of this summation).

For example, in just the same way, with two more integrations, we find that $$\frac{1}{1^4} + \frac{1}{2^4} + \frac{1}{3^4} + \ldots = \frac{1}{90} \pi^4$$. And with yet two more integrations, we find that $$\frac{1}{1^6} + \frac{1}{2^6} + \frac{1}{3^6} + \ldots = \frac{1}{945} \pi^6$$. And in general, for each (positive) even $$n$$, we find that $$\frac{1}{1^n} + \frac{1}{2^n} + \frac{1}{3^n} + \ldots$$ is some rational coefficient times $$\pi^n$$ (with a simple recursive computation for that rational coefficient). Ta-da again! Infinitely many "Ta-da!"-worthy results, all at once!

----
TODO: Relate this to solving the Basel problem using the cotangent series $$\pi \cot(\pi x) = \sum_{n \in \mathbb{Z}} \frac{1}{x + n}$$ and its derivatives. Can we evaluate a general Lerch transcendent or something like it in this way?