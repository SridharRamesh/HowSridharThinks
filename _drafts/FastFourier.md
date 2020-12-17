---
title:  "The Fast Fourier Transform"
date: 2020-11-29
---
Let $$B$$ be a value such that $$B^N = 1$$ and define the $$K$$-weighted base-$$B$$ transform of order $$N$$ of a function $$f$$ to be $$s \mapsto K \sum_{t = 0}^{N - 1} f(t) B^{st}$$. [The domains of these functions should be thought of as the integers modulo $$N$$, so that these function as bidirectionally infinite sequences]

As with any linear function, we can think of this as a matrix, or more to the point, we can ask, for each $$y$$-th entry of the output and $$x$$-th entry of the input, what is the coefficient by which the latter affects the former? And the defining characteristic of this transform is that this function of $$x$$ and $$y$$ is $$K$$ times an exponential function, whenever treated as a function of one of these variables by fixing the other, and specifically is $$B$$ when both values are set to $$1$$.

When $$N$$ factors as $$RC$$, we can compute this efficiently recursively like so: Arrange the $$N$$ many values of $$f$$ into a matrix with $$R$$ many rows and $$C$$ many columns.

Pick any two weights $$L$$ and $$M$$ such that $$LM = K$$.

Now replace each $$r$$-th row by the $$LB^{rC}$$-weighted base-$$B^R$$ transform of order $$C$$ of that row.

After having done so, replace each $$c$$-th column by the $$MB^{Rc}$$-weighted base-$$B^C$$ transform of order $$R$$ of that column.

[All the values here are the only things they can be, basically]

What appears in the $$r$$-th row and the $$c$$-th column in the end? It is the sum over all $$t$$ of $$MB^{(R + r)Ct}$$ times the $$t$$-th value in that column from the intermediate step, which itself was the sum over all $$s$$ of $$LB^{RC} B^{Rs}$$ times $$f($$

TODO

***

Runtime analysis: The above implies that the total run time $$T(AB)$$ for the FFT of order $$AB$$ can be made into $$AT(B) + BT(A)$$. With suitable care about the base cases (either prime values in a discrete context or infinitesimal values in a continuous context), it follows that $$T(n)$$ is proportional to $$n \log(n)$$. Specifically, our rule for combining $$A$$ and $$B$$ amounts to this: If $$A + T(A)x$$ is multiplied by $$B + T(B)x$$ where $$x^2 = 0$$, then the result is $$AB + T'(AB)x$$, where $$T'(AB)$$ is one allowed runtime for $$T(AB)$$. If we start only with base cases of the form $$A + A \log(A)kx = A(1 + \log(A)kx) = A^{kx + 1}$$, then everything we build up inductively has this form as well. More generally, if different building blocks have different $$k$$ here, what we discover is that the run-time for some $$N$$ which decomposes as $$A$$ times $$B$$ times $$C$$, etc, will be $$N [k_A \log(A) + k_B \log(B) + \ldots]$$, which is between $$N k_{min} \log(N)$$ and $$N k_{max} \log(N)$$.

***

In a discrete world, the above only lets us do fast Fourier transforms of highly composite order. It doesn't give us anything fast by default for large prime orders, say. Well, it turns out that we can also reduce the question of a fast Fourier transform of a given order to taking a suitable convolution quickly. And conversely, to do a convolution of a particular order, we can do a Fourier transform, then multiply component wise, then Fourier transform back. But once we're in the world of convolutions, there's no harm in zero-padding ourselves up to a higher order, so we can always just pad up to order some power of 2 (inflating our size by a factor less than 2), and then get away with the straightforward fast Fourier transform for that highly composite order.

Keep in mind, fast convolution means the same thing as fast polynomial multiplication, which would also give us fast integer multiplication, but there's one subtlety: We need to be working in a context where we actually have the appropriate primitive roots of unity. We can extend to the ring Z[a primitive nth roots of unity] abstractly, but the cost of individual arithmetic computations in this ring would itself be about as bad as convolving things of degree phi(n), which is itself on the order of n when we fix n to be a power of 2 or such things, saving us nothing. So either we can do something like work in the complex numbers [where it turns out we need $$\theta(log(n))$$ many bits of precision for representation of the complex numbers in order to keep them distinct enough to be able to distinguish different integers at the end of our computation, so that each step of the FFT of order n ends up calling out recursively to an FFT of order log(n)], as in the first Schonhage-Strassen algorithm, or we can work in arithmetic with a suitable modulus where the requires roots of unity exist automatically, but then must be more careful about controlling the costs; this is the second Schonhage-Strassen algorithm, which turns out to be slightly more efficient. We end up multiplying values of size N by using an FFT of order sqrt(N), over a ring whose elements themselves have size sqrt(N), so that each step of our recursion only reduces things from N to sqrt(N) but the order of the FFT itself is much lower.

Even more efficient than that, see "Integer multiplication in time O(n log n)" (https://hal.archives-ouvertes.fr/hal-02070778/document) by Harvey and van der Hoeven, the most efficient known, and which seems pretty readable.