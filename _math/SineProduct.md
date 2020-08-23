---
layout: post
title:  "Wallis Product and the Sine Product"
date: 2018-06-27
---
In a past life, I worked for 3blue1brown, and I discovered and made a video for them on a simple new proof of the Wallis product and the sine product more generally. Alas, I no longer work for 3blue1brown. But I had a post on a number of supplements to that video, which I will keep archived for my own purposes here, as well transcribing the full argument from the video for this blog at some point as well:

# Recap of the argument from the video:


[The video](https://www.youtube.com/watch?v=8GPy_UMV-08)


Recap: \[TODO\]

# Commuting limits using Dominated Convergence:

This kind of interchanging of limits and infinitary arithmetic isn't actually always true, for arbitrary sequences. It often holds, but sometimes fails. Luckily, mathematicians have spent a lot of time thinking about these phenomena, and developing tools for quickly seeing certain conditions under which this interchanging of limits works. In this case, a particular standard result known as “Dominated Convergence” quickly assures us that we are indeed allowed to use this sleight-of-hand here. Let's see the details of how to use that for this argument:

Although Dominated Convergence is normally phrased entirely in terms of addition, we will use a form of it tailored to multiplication: specifically, the Dominated Convergence result we will use states that if you have a multiplicative series whose $$k$$-th factor at time $$N$$ is $$S_k(N)$$, and you want to show that $$\displaystyle \lim_{N \to \infty} \prod_{k} S_k(N) = \prod_{k} \lim_{N \to \infty} S_k(N)$$, it suffices to find an additive series of positive terms $$B_k$$ such that $$\sum_{k} B_k$$ converges, and such that $$\|S_k(N) - 1\| \leq B_k$$ for each $$k$$ regardless of $$N$$. (The “for each $$k$$” can even be relaxed to “for all but finitely many $$k$$”).

To apply this to our situation, recall that at the time when we have $$N$$ lighthouses, the contribution from the $$k$$-th lighthouse to the Sailor : Keeper distance-product ratio is $$\mathrm{Chord}((k - f)/N) : \mathrm{Chord}(k/N)$$, if the $$k$$-th lighthouse is present. And, presuming $$N$$ always odd for convenience, we can take the lighthouses which are present to correspond to those nonzero integers $$k$$ for which $$N > \|2k\|$$. (When $$N$$ is even, there is also the question of whether to use $$+N/2$$ or $$-N/2$$ to index the lighthouse diametrically opposite “the Keeper”, but we will ignore this wart; it makes no difference to anything to restrict attention to the behavior for odd $$N$$). Another way of saying that the $$k$$-th factor only enters once $$N > \|2k\|$$ is to say that the $$k$$-th factor is $$1$$ when this condition is not satisfied.

So this gives us our $$S_k(N) = \frac{\mathrm{Chord}((k - f)/N)}{\mathrm{Chord}(k/N)}$$ (when $$N > \|2k\|$$, and $$1$$ otherwise).

We also already know that $$\displaystyle \lim_{N \to \infty} S_k(N) = 1 - \frac{f}{k}$$, and we also have just seen that the product over all nonzero integers $$k$$ of $$S_k(N)$$ is equal to $$\frac{\mathrm{Chord}(f)}{N \times \mathrm{Chord}(f/N)}$$, whose limiting value for large $$N$$ is $$\frac{\mathrm{Chord}(f)}{f \times 2\pi} = \frac{\sin(f\pi)}{f\pi}$$.

So to complete the proof of our sine product result, we just need to be able to commute the limits here. In order to use our Dominated Convergence tool to commute these limits, we need to find a series of positive values $$B_k$$, such that the sum of the $$B_k$$ converges, and $$\|S_k(N) - 1\|$$ is bounded by $$B_k$$.

Alas... this is impossible: Note that the limiting value of (and thus the minimal size of any potential bound on) $$\|S_k(N) - 1\|$$ is on the order of $$\|k\|^{-1}$$, and this famously diverges (as the harmonic series) rather than converges.

BUT! If we bundle our factors together, bundling the $$k$$-th and $$-k$$-th factor together as $$S'_k(N) = S_k(N) \times S_{-k}(N)$$, and then consider this series (now indexed only by positive integers) instead, now we have a shot, as the limiting value of $$\|S_k(N) - 1\|$$ is now on the order of $$k^{-2}$$, which converges. Let's see if we can get an actual bound, irrespective of $$N$$, of this same quadratic order in $$k$$, which will allow us to use Dominated Convergence on the product with factors bundled in this way.

Expanding out $$S'_k(N)$$, it is $$\frac{\mathrm{Chord}((k - f)/N)}{\mathrm{Chord}(k/N)} \times \frac{\mathrm{Chord}((-k - f)/N)}{\mathrm{Chord}(-k/N)}$$, where $$N > 2k$$ (or $$1$$ otherwise). With a little trig identity elbow-grease, and keeping in mind that $$\mathrm{Chord}$$ is basically the same thing as $$\sin$$ (just with its inputs and outputs re-scaled by constant factors), we get that $$S'_k(N)$$ equals $$1 - \left( \frac{\mathrm{Chord}(f/N)}{\mathrm{Chord}(k/N)} \right) ^2$$ (under, as always, the condition that $$N > 2k$$, and being simply $$1$$ otherwise).

Our goal now is to bound $$\left( \frac{\mathrm{Chord}(f/N)}{\mathrm{Chord}(k/N)} \right) ^2$$ for $$N > 2k$$ by some function of $$k$$ on the order of $$k^{-2}$$ for large $$k$$, which is to say, we want to bound $$\frac{\mathrm{Chord}(f/N)}{\mathrm{Chord}(k/N)}$$ by a function of $$k$$ on the order of $$k^{-1}$$.

To show that such a bound holds, we begin by rewriting $$\frac{\mathrm{Chord}(f/N)}{\mathrm{Chord}(k/N)}$$ as $$\frac{\mathrm{Chord}(r x)} {\mathrm{Chord}(x)}$$ where $$x = k/N < \frac{1}{2}$$ and $$r = f/k$$.

Letting $$D(x) = \mathrm{Chord}(x)/x$$, we can furthermore rewrite this as $$\frac{D(r x)}{D(x)} \times r$$. As $$r$$ itself is proportional to $$k^{-1}$$, what remains is to show that $$\frac{D(r x)}{D(x)}$$ is bounded by a constant, for sufficiently large $$k$$. Since $$x \in [0, \frac{1}{2}]$$ and $$D(x)$$ is a continuous function which never takes the value $$0$$ in this range (including at $$x = 0$$, where $$D(x)$$ equals the nonzero derivative of $$\mathrm{Chord}(x)$$), we have that $$\frac{1}{D(x)}$$ is bounded by a constant.

Furthermore, since $$x$$ itself is bounded by a constant, and $$r$$ is bounded by a value proportional to $$k^{-1}$$, we have that for sufficiently large $$k$$, that $$rx$$ is arbitrarily close to $$0$$, and thus $$D(rx)$$ is arbitrarily close to the constant $$D(0)$$.

This completes the proof that $$\frac{D(r x)}{D(x)}$$ is bounded by a constant for sufficiently large $$k$$, and indeed, retracing back through what has taken us here, completes the proof that $$\|S'_k(N) - 1\|$$ is bounded by some function of $$k$$ which is additively convergent over all $$k$$, thus allowing us to apply Dominated Convergence to $$S'_k$$, filling in the final rigor on our proof of the sine product formula in general and the Wallis product in particular.

You may be wondering why our particular trick of bundling positive and negative index factors into a single factor was helpful and indeed necessary for us to get around the initial obstruction to using Dominated Convergence here. One way of looking at this is as so: The fact that we could not use Dominated Convergence with our pre-bundled product corresponds to how our pre-bundled product is only conditionally convergent, not absolutely convergent; re-ordering its factors wildly could give different limiting values. But the bundling we engaged in turned our product absolutely convergent, obviating these issues and in so doing also yielding a series to which we could apply our Dominated Convergence tool.

# The relationship to the Basel problem:

Not only is our sine product cool in its own right, but we can also use it to solve the Basel problem (and indeed, this was the way that the Basel problem was first solved by Euler, though he discovered the sine product in a different way than we've shown here):

Remember, the Basel problem is to understand what the sum of the reciprocal squares comes out to, $$\frac{1}{1^2} + \frac{1}{2^2} + \frac{1}{3^2} + \dots$$. How does this relate to our sine product?

Well, as we've just seen, we know that $$\sin(f \pi)$$ is $$f \pi$$ times the product of $$\left(1 - \frac{f}{k} \right) \times \left(1 - \frac{f}{-k} \right) = 1 - \frac{f^2}{k^2}$$ over all positive integers $$k$$. But we also know, from the fact that $$\sin$$ is the negation of its own second derivative, and from the values at $$0$$ of $$\sin$$ and its derivative, that we have the Taylor series expansion $$\sin(f \pi) = f \pi - \frac{(f \pi)^3}{3!} + \frac{(f \pi)^5}{5!} - \frac{(f \pi)^7}{7!} + \dots$$.

So the coefficients of $$f$$ in both of these series must be the same. In particular, let's look at the coefficient of $$f^3$$:

In the Taylor series $$\sin(f \pi) = f \pi - \frac{(f \pi)^3}{3!} + \frac{(f \pi)^5}{5!} - \frac{(f \pi)^7}{7!} + \dots$$, the coefficient of $$f^3$$ is $$-\frac{\pi^3}{3!}$$.

In our sine product $$\sin(f \pi) = f \pi \displaystyle \prod_{k \geq 1} \left(1 - \frac{f^2}{k^2} \right)$$, on the other hand, if we were to rewrite this as a "power series" by distributing out the giant multiplication, we would, among other terms, obtain the terms $$f \pi \times \left(-\frac{f^2}{1^2} -\frac{f^2}{2^2} - \frac{f^2}{3^2} + \dots \right)$$; these are the terms in our giant multiplication that come from choosing the "$$-\frac{f^2}{k^2}$$" from one factor and the "$$1$$" from all other factors. These are the terms which are multiples of $$f^3$$; all the other terms would correspond to higher or lower degree in $$f$$. So the coefficient of $$f^3$$ in our sine product series is $$-\pi$$ times the Basel sum $$\frac{1}{1^2} + \frac{1}{2^2} + \frac{1}{3^2} + \dots$$.

And thus, equating the results of the two last paragraphs, $$-\pi$$ times the Basel sum must equal $$-\frac{\pi^3}{3!}$$. This means the Basel sum must equal $$\frac{\pi^2}{3!} = \frac{\pi^2}{6}$$. Ta-da!

By equating coefficients at higher powers of $$f$$ between these two series, we can also go further and discover the sum of $$\frac{1}{1^n} + \frac{1}{2^n} + \frac{1}{3^n} + \dots$$ for each even $$n \geq 2$$, in each case finding it to be some rational multiple of $$\pi^n$$.

(But for a much simpler way of calculating these results, which does not require our sine product, or much anything beyond Calc 101 integration, see this other post \[TODO: link to be inserted\]!)

# Alternative proof of the Wallis product:

Check out another beautifully simple geometric proof of the Wallis product directly in terms of circles and spheres (and higher-dimensional spheres...) in [this post]({{"/math/WallisProductGeometric.html" | prepend:site.baseurl}})! No complex numbers or tricky polynomial algebra required!

# Much more to come:

[There's much more material to come on Euler's original method of discovery of the sine product, other methods of establishing it as well, what happens when we re-order our Wallis product to interleave its two halves at different speeds, other nice series for trig functions which follow from the sine product, further connections between these and the Basel problem, and more! This post will be updated continuously over time. Stay tuned!]


