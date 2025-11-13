---
title: "Random Walks (Probability and Least Fixed Points)"
date: 2025-11-02
---
There's a lot to say about random walks, but I mainly wanted to record for posterity one particular observation relating probability to least fixed points:

Consider a biased random walk with probability p of moving up one position (call this gaining a dollar, say) and q of moving down one position (losing a dollar). What is the probability of ever ending up down one position from the start (losing a dollar in total)?

There are two ways one can eventually lose a dollar: One can immediately lose the dollar. Alternatively, one can first immediately gain a dollar, then through some complex of steps eventually lose a dollar in total, then again lose a dollar in total.

This gives a recurrence: The probability $$x$$ of ever being down one dollar is equal to $$q + px^2$$. This quadratic equation has two solutions: $$x = 1$$ and $$x = q/p$$. If $$q/p > 1$$, it is not a probability, so the answer is $$x = 1$$. But if $$q/p < 1$$, how do we know whether $$x = 1$$ or $$x = q/p$$?

Let us consider the situation in more detail:

* One can immediately lose the dollar. Let us say this means of losing a dollar has "rank" 0.

* Alternatively, one can first gain a dollar, then eventually lose a dollar in total, then eventually lose a dollar in total again. Let's say this means of losing a dollar has "rank" equal to 1 + the maximum of the "ranks" of the two noted dollar losses within it.

Thus, the probability of losing a dollar by a means of rank less than $$n$$ is $$T^n(0)$$, where $$T(x) = q + px^2$$.

Clearly, the events "losing a dollar by rank < 0", "losing a dollar by rank < 1", "losing a dollar by rank < 2", etc, form a chain, each included in the next. The event we are interested in is the union of this chain. So we have that $$T^0(0) \leq T^1(0) \leq T^2(0) \leq \ldots$$, and the probability we are interested in the limit of this sequence.

As $$T$$ is an order-preserving continuous function from \[0, 1\] to itself, this must be the least fixed point of $$T$$. Thus, when $$q/p < 1$$, the answer is $$x = q/p$$, not $$x = 1$$.

The fact that the limit of this sequence is the least fixed point of $$T$$ is essentially [the Knaster-Tarski-Adamek theorem](@/LambekKnasterTarski.md).

Recapping Knaster-Tarski-Adamek in this context, we have:

If $$T$$ is an order-preserving continuous operator on a space with a least element $$0$$ and containing limits of all increasing sequences, then

A) $$0 \leq T(0) \leq T(T(0)) \leq \ldots$$

B) The limit $$L$$ of this sequence is a fixed point of $$T$$

C) Every other fixed point of $$T$$ (indeed, every other solution to $$T(x) \leq x$$) is $$\geq L$$.

Proof:

A) is from $$T$$ being order-preserving and 0 being a least element.

B) is because the limit of $$0, T(0), T(T(0)), \ldots$$ is the same as the limit of $$T(0), T(T(0)), T(T(T(0))), \ldots$$, and the latter sequence is $$T$$ applied to the former sequence, and $$T$$ is continuous.

C) is by noting that $$0 \leq x$$ leads to $$T^n(0) \leq T^n(x) \leq x$$ for every $$x$$ such that $$T(x) \leq x$$

QED. This kind of relationship of probability to least fixed points, allowing disambiguation of seemingly underdetermined solutions to recurrence equations, is frequently useful in probability (not just for random walks).

****

Incidentally, we may be interested in the question "What is the probability of eventually being down a dollar, and never prior being up by n dollars?". Call this $$f(n)$$. By the decomposition above, we have the recurrence that $$f(n) = q + p f(n - 1) f(n)$$.

Note that this is not quite the same as $$f(n) = T(f(n - 1)) = T^n(0)$$ with $$T(x) = q + px^2$$, the recurrence we were able to use for our previous definiton of "rank". Rather, we now have that $$f(n) = U(f(n - 1)) = U^n(0)$$ with $$U(x) = q / (1 - p x)$$. Still, this $$U$$ remains a continuous order-preserving function from $$\[0, q/p\]$$ to itself, and so we could again reason that the the limiting value of $$f(n)$$ (which again is the probability of ever being down a dollar) is the least fixed point of $$U$$.

This $$U$$ has dynamics which are easy to understand also, since it sends a fraction $$x = n/d$$ to the fraction $$U(x) = qd / (d - pn)$$. Thus, $$U$$ can be represented as a 2x2 matrix \[\[0, q\], \[-p, 1\]\], thought of as acting on the projective line. This matrix is easily diagonalized with eigenvalues p and q.

(But a more general way of thinking about this is in terms of random walks with two absorbing states. See https://bsky.app/profile/radishharmers.bsky.social/post/3m4mah776uk27)

****

TODO: Add more on random walks, as there is much more to say on various kinds of random walks. Note that the above also relates to Catalan numbers, as we may think of these up and down moves as left and right parentheses balanced right before the final dollar loss.