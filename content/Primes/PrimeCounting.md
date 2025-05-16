---
title: "Elementary Prime Counting"
date: 2018-06-27
---
Consider the question of how many primes are $$\leq n$$; let us call this quantity $$\pi(n)$$, as is traditional.

Understanding $$\pi(n)$$ is not just a random curiosity, but in fact ubiquitously useful for answering other questions in number theory, as the primes entirely determine the multiplicative structure of the integers. This is by virtue of the Fundamental Theorem of Arithmetic, which tells us that each positive integer has a unique prime factorization. The existence of these factorizations is easy to see (simply keep splitting an integer up into any possible smaller factors, and splitting those in turn, until nothing can be split any more). The uniqueness of these factorizations is a subtler, trickier point (it’s not nearly as obvious as people often naively take it to be!). I will write more about the Fundamental Theorem of Arithmetic in a separate post, but at any rate, take my word for it, it makes understanding the distribution of the prime numbers important! So let's see what we can quickly determine about $$\pi(n)$$.

The very first most basic question is, does $$\pi(n)$$ eventually grow larger than any finite value? That is, are there infinitely many primes?

Well, this was answered already for us in ancient times, by Euclid. Suppose given any finitely many primes. Let's see if we can find some other prime not among them. Well, consider taking the product of all those primes, and then adding $$1$$. The result is some integer $$> 1$$ which is indivisible by each of those primes. However, any integer $$> 1$$ has SOME prime factor (by the “keep splitting it up into smaller factors till you can’t anymore” method noted above; that is, by the existence half of the Fundamental Theorem of Arithmetic). Thus, the prime factors of this integer, of which at least one exists, are primes not among our original finitely many. We've shown there must be infinitely many primes.

This is often viewed as a merely qualitative argument, but we can consider it quantitatively as well.

Euclid's argument tells us that each next prime is at most $$1 +$$ the product of all the previous primes. Better yet, making no essential difference to the argument, we see in the same way that each next prime is at most $$-1 +$$ the product of all the previous primes, after the first two small primes $$2$$ and $$3$$. For convenience, let's not bother worrying about the $$-1$$, and just note that (after the first two small primes $$2$$ and $$3$$) each prime is at most the product of all the previous primes. This means the sequence of primes grows, at fastest, like the sequence starting with $$2$$ and $$3$$ in which each further term is the product of all the previous ones. This sequence is $$2, 3, 6^{2^0}, 6^{2^1}, 6^{2^2}, 6^{2^3}, ...$$, and thus we can conclude that $$\pi(n) \geq \lfloor \log_{2}(\log_{6}(n)) \rfloor + 3$$.

This gives us a loose lower-bound on the growth rate of $$\pi(n)$$. But we can do much better with a different simple argument, due to Chebyshev (this argument will also establish the infinitude of the primes as a consequence, in an entirely different manner to Euclid, with a much more impressive lower-bound on the growth rate of $$\pi(n)$$).

Our approach is as follows: we will find a positive integer-valued function $$f(n)$$ with the property that each of its prime power factors is $$\leq n$$. As every positive integer is the product of the prime powers in its prime factorization (this is essentially the Fundamental Theorem of Arithmetic), we can conclude that $$f(n) \leq n^{\pi(n)}$$, which is to say, that $$\pi(n)$$ is at least $$\log_{n}(f(n))$$. If furthermore $$f(n)$$ grows super-polynomially, this tells us that the number of primes grows infinite.

Specifically, we will take $$f(n)$$ to be $$\frac{\lfloor n \rfloor!}{\lfloor n/2 \rfloor !^2}$$. This certainly grows super-polynomially (expanding out the factorials, there are about $$n$$ factors in both numerator and denominator, with the former about twice as large as the latter, so this is approximately $$2^n$$; at any rate, it is at least as large as the central binomial coefficient $$\binom{\lfloor n \rfloor}{\lfloor n/2 \rfloor}$$, which is in turn at least as large as $$2^{\lfloor n \rfloor}/(\lfloor n \rfloor + 1)$$), so what remains is to see that each prime power dividing $$f(n)$$ is at most $$n$$.

In order to establish this, let's first note that the exponent of each $$p$$ in the prime factorization of $$\lfloor n \rfloor!$$ is the sum of $$\lfloor n/p^e \rfloor$$ over each positive integer $$e$$. (This is because the exponent of $$p$$ in the prime factorization of any positive integer $$m$$ is the same as the number of $$p^e$$ which divide $$m$$. The exponent in the prime factorization of $$\lfloor n \rfloor!$$ will then be the sum of that quantity over all $$m \leq n$$, which is to say, the number of pairs $$(m, p^e)$$ where $$p^e$$ divides $$m$$ which in turn is $$\leq n$$. For each $$p^e$$, there will be $$\lfloor n/p^e \rfloor$$ many choices of $$m$$, giving the stated result.)

Let's also note that $$\lfloor x \rfloor - 2\lfloor x/2 \rfloor$$ is the remainder when $$\lfloor x \rfloor$$ is divided by $$2$$, which is to say, $$0$$ or $$1$$ according as to whether $$\lfloor x \rfloor$$ is even or odd, respectively.

Putting those together, we find that the exponent of $$p$$ in the prime factorization of $$f(n)$$ is the number of $$\lfloor n/p^e \rfloor$$ which are odd. This is upper-bounded by the number of $$\lfloor n/p^e \rfloor$$ which are $$\geq 1$$, which amounts to the largest $$e$$ such that $$p^e \leq n$$. Thus, every prime power factor of $$f(n)$$ is $$\leq n$$, completing the proof.

How good is our bound $$\pi(n) \geq \log_n(f(n))$$? It's actually not too hard to show that the ratio of $$\pi(n)$$ to $$\log_n(f(n))$$ is also upper-bounded by a constant (perhaps I'll add that to this post later). So it's quite good! That having been said, we can go even further: The Prime Number Theorem says that this ratio approaches precisely $$1 : \ln(2)$$ as $$n$$ grows large [though it is usually phrased in more generally relevant terms than that].

And should anyone ever prove the Riemann Hypothesis, that would give us even tighter bounds on $$\pi(n)$$. (What a wonderful story that would make, to crack the most ancient chestnut of prime infinitude with the most advanced sledgehammer of the Riemann Hypothesis-turned-Theorem! It'd be the greatest saga of mathematics, spanning all the way from what's considered its most classic proof to what's considered its most sought-after one.)

***

For a much more advanced continuation of the story in this post, counting the number of primes much more exactly, see [here](@/Primes/ZetaPrimeCounting.md).

****

(TODO: Also worth discussing in a post somewhere, since no one seems to have written this up in a nice way for anyone: the heuristic/intuitive argument for the first Hardy-Littlewood conjecture (as well the intuition for the second conjecture, but also noting why the second conjecture is incompatible with the first one).)