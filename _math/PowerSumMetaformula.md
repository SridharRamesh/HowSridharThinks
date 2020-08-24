---
title:  "The Meta-Formula for 1^n + 2^n + 3^n + ... + x^n"
date: 2018-06-27
---
[There's a better version of this post coming when I copy over https://howsridharthinks.wordpress.com/2019/11/19/difference-equations-infinite-sums-generalized-factorial-zeta-functions-etc/, but it's not fully ready yet. This is an archive of an old Quora answer, in the meanwhile. This is just for the sake of copying everything from the Wordpress site over to the Github site.]

You’ve probably seen formulas such $$1 + 2 + 3 + \ldots + x = \frac{x^2}{2} + \frac{x}{2}$$, $$1^2 + 2^2 + 3^2 + \ldots + x^2 = \frac{x^3}{3} + \frac{x^2}{2} + \frac{x}{6}$$, and so on before, and wondered where these come from, and if the same thing can be done for sums of powers of any degree.

Well, the answer (er, to the second question) is a resounding YES! Here is a general technique that will quite readily, quite easily give you the formula for the sum of consecutive values of any polynomial, as another polynomial. Indeed, here is a “meta-formula” for the desired formula.

Actually, I will explain this same underlying idea twice, in somewhat different ways. Once a little less abstractly, and once a little more abstractly. You may read whichever of these tickles your fancy best; whichever gives you the clearest understanding.

# The less abstract presentation

Suppose you already have a nice formula for $$R(x) = 1^n + 2^n + 3^n + \ldots + x^n$$ (in other words, $$R(0) = 0$$ and $$R(x) - R(x - 1) = x^n$$). How can we find a similar formula for $$(n + 1)$$th powers instead of $$n$$th powers?

Well, $$x^{n + 1}$$ is what we get if we integrate $$x^n$$ (with an initial value of $$0$$) and multiply by $$n + 1$$. And if we do this to $$R$$, so that $$Q' = (n + 1)R$$, this $$Q$$ will ALMOST give us exactly what we need: we will then have that the derivative of $$Q(x) - Q(x - 1)$$ is $$(n + 1)(R(x) - R(x - 1)) = (n + 1) x^n$$, which is the derivative of $$x^{n + 1}$$; it follows that $$Q(x) - Q(x - 1)$$ and $$x^{n + 1}$$ differ by at most a constant.

But we want them to match exactly! So to cancel out this constant, we can add an extra linear term to $$Q$$; as we add $$cx$$ to $$Q$$, we end up adding $$c$$ to $$Q(x) - Q(x - 1)$$, and so by using the appropriate $$c$$, we can get the exact equality we desire.

So that’s it, then. To get a formula for $$1^{n + 1} + 2^{n + 1} + 3^{n + 1} + \ldots + x^{n + 1}$$, we take a formula for $$1^n + 2^n + 3^n + \ldots + x^n$$, integrate it (with an initial value of $$0$$) and multiply by $$n + 1$$, then add $$cx$$ where the constant $$c$$ is chosen to ensure that we get the right values.

Thus, since we know that the formula for the sum of the first $$x$$ many $$0$$th powers $$1 + 1 + 1 + \ldots$$ is $$x$$ , we find that the formula to sum the first $$x$$ many $$1$$st powers $$1 + 2 + 3 + \ldots + x$$ is $$\frac{x^2}{2} + cx$$. What should we choose $$c$$ to be? We should choose it to give a total of $$1$$ when $$x = 1$$; thus. $$c = \frac{1}{2}$$, and our formula when $$n = 1$$ is $$\frac{x^2}{2} + \frac{x}{2}$$.

Next, to get the formula for $$1^2 + 2^2 + 3^2 + \ldots + x^2$$, we integrate, multiply by $$2$$, and add an unknown linear term, to get $$\frac{x^3}{3} + \frac{x^2}{2} + cx$$. Again, we should choose $$c$$ so that the total comes out to $$1$$ when $$x = 1$$; thus, $$c$$ now must be $$\frac{1}{6}$$.

Next, to get the formula for $$1^3 + 2^3 + 3^3 + \ldots + x^3$$, we do this all again, integrating, multiplying by $$3$$, and adding an unknown linear term, to get $$\frac{x^4}{4} + \frac{x^3}{2} + \frac{x^2}{4} + cx$$. In this case, to get the total to come out to $$1$$ when $$x = 1$$, we take $$c = 0$$.

And so on and so on; continuing in this way, we get the formulas for any degree we like.

# The more abstract presentation

Consider the linear “forward difference” operator which sends the polynomial $$P(x)$$ to the polynomial $$P(x + 1) - P(x)$$. Call this operator $$\Delta$$. Given a polynomial $$P$$, our goal is to find some polynomial $$Q$$ such that $$\Delta Q = P$$. Then $$Q(a) - Q(b)$$ will be $$P(b) + P(b + 1) + P(b + 2) + \ldots + P(a - 1)$$, which will allow us to easily solve any problem of this sort. (We could just as well think about “backward differences” or any such thing, but my own idiosyncratic preference is to have to keep track of less minus signs…)

But how do we find such a $$Q$$, given $$P$$?

Well, let’s consider two other linear operators of note on polynomials, that are closely related to this difference operator. First of all, there’s “differentiation” (in the sense of taking the derivative), whose name already belies it closeness; this is the familiar operator from calculus which sends $$x^n$$ to $$n x^{n - 1}$$. We’ll call this operator $$\delta$$. Secondly, there’s “integration” in the sense which sends each $$x^n$$ to $$\frac{x^{n + 1}}{n + 1}$$. We’ll call this operator $$\int$$. Note that integrating followed by differentiating is the same as doing nothing at all (i.e., $$\delta \int P = P$$).

Let’s make more explicit the sense in which differentiation and forward difference are related. In particular, let’s note that we have, by Taylor expansion, that $$P(x + 1) = P(x) + \frac{\delta^1 P (x)}{1!} + \frac{\delta^2 P(x)}{2!} + \frac{\delta^3 P(x)}{3!} + \ldots = e^{\delta} P(x)$$. That is $$\Delta P(x) = P(x + 1) - P(x) = (e^{\delta} - 1) P(x)$$, which is to say, $$\Delta = e^{\delta} - 1$$. Conversely, we must have $$\delta = \ln(1 + \Delta)$$, which by Taylor series expansion again, comes out to $$\Delta - \frac{\Delta^2}{2} + \frac{\Delta^3}{3} - \frac{\Delta^4}{4} + \ldots$$.

(For what it’s worth, though these are phrased as infinite series here, when applied to any particular polynomial, only finitely many terms are nonzero, as $$\delta$$ or $$\Delta$$ applied more than $$n$$ times to a polynomial of degree $$n$$ results in zero. So there are no convergence issues which can arise, and all the results which we know to hold for Taylor series as abstract formal objects (e.g., that $$e^x - 1$$ and $$\ln(1 + x)$$ act as inverse functions) will necessarily work just as well for these series expansions in terms of our operators as applied to particular polynomials)

Let’s see how this helps us with our goal. We wanted to find a $$Q$$ such that $$\Delta Q = P$$. But we can rewrite this as $$\Delta Q = \delta\int P$$, which is to say, $$\Delta Q = \left( \Delta - \frac{\Delta^2}{2} + \frac{\Delta^3}{3} - \frac{\Delta^4}{4} + \ldots \right) \int P$$.

Now it’s easy enough to solve. Factoring a $$\Delta$$ out, we see that it suffices to take $$Q = \left(1 - \frac{\Delta}{2} + \frac{\Delta^2}{3} - \frac{\Delta^3}{4} + \ldots \right) \int P = \frac{\ln(1 + \Delta)}{\Delta} \int P$$. And as noted above, this is a finitary calculation for any particular $$P$$.

Actually, because $$\delta^n$$ is easier to compute for polynomials in standard representation than $$\Delta^n$$ (since $$\delta$$ takes monomials to monomials), it is often more convenient to rewrite $$\frac{\ln(1 + \Delta)}{\Delta}$$ as $$\frac{\delta}{e^{\delta} - 1} = 1 - \frac{\delta}{2} + \frac{\delta^2}{12} - \frac{\delta^4}{720} + \ldots$$. The Taylor series expansion here, as for any such symbolic expression, can be evaluated to any desired length by straightforward calculus, although there are cleverer ways as well. [The coefficients so produced happen to have been studied in their own right, in the theory of the closely related “Bernoulli numbers”, in case you care to read up more on these.]

So we have that $$Q = \frac{\delta}{e^{\delta} - 1} \int P \; = \left(1 - \frac{\delta}{2} + \frac{\delta^2}{12} - \frac{\delta^4}{720} + \ldots\right) \int P$$ $$= \left(\int - \frac{1}{2} + \frac{\delta}{12} - \frac{\delta^3}{720} + \ldots\right) P$$. And, remember, we can use this to calculate $$P(b) + P(b + 1) + P(b + 2) + \ldots + P(a - 1)$$ as $$Q(a) - Q(b)$$.

This completes our general technique. Let’s apply it to, for example, the particular question of a formula for $$1^2 + 2^2 + 3^2 + \ldots + x^2$$.

Suppose $$P(x) = x^2$$. Applying $$\left(\int - \frac{1}{2} + \frac{\delta}{12} - \frac{\delta^3}{720} + \ldots\right)$$ to this, we get $$\frac{x^3}{3} - \frac{x^2}{2} + \frac{x}{6} + 0 + 0 + 0 + \ldots$$.

Taking this to be $$Q(x)$$, we can now compute $$1^2 + 2^2 + 3^2 + \ldots + x^2$$ as $$Q(x + 1) - Q(1)$$. Eh, it’ll be slightly simpler in the terms we’ve put this in to think of this as $$0^2 + 1^2 + 2^2 + \ldots + (x - 1)^2 + x^2 = Q(x) - Q(0) + x^2$$, which is $$\frac{x^3}{3} + \frac{x^2}{2} + \frac{x}{6}$$. Ta-da! This is our final formula.

But the great value of the discussion in this post is that we do not need to apply new cleverness to solving this type of problem again for each new polynomial or degree of powers to be summed. We can mechanically produce the answers for each, simply applying $$\frac{\delta}{e^{\delta} - 1} \int = \left(\int - \frac{1}{2} + \frac{\delta}{12} - \frac{\delta^3}{720} + \ldots\right)$$ to the given polynomial.

This technique is general enough that it even works for some functions which aren’t polynomials, producing answers as convergent infinite series, which then can be used to interpolate/extrapolate the corresponding “sum consecutive values” function to new contexts beyond where this sum would ordinarily be interpretable. For example, these kinds of ideas can be used to generalize the factorial to non-integer arguments (by generalizing the logarithmic factorial, which is a sum of consecutive logarithms; of course, we’ve seen already how to generalize the factorial anyway, at [TODO: insert link]), and to extend the Riemann and Hurwitz zeta functions to arbitrary inputs (as with every topic I mention in passing, I promise I will write more on this in a later post...). It’s a very valuable idea to be aware of.

[TODO: Add the million others way of looking at this; e.g., through Stirling numbers of the first and second kinds, and through the Hurwitz zeta function.]