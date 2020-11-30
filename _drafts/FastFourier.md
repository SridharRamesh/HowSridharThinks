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

----

Runtime analysis: The above implies that the total run time $$T(AB)$$ for the FFT of order $$AB$$ can be made into $$AT(B) + BT(A)$$. With suitable care about the base cases (either prime values in a discrete context or infinitesimal values in a continuous context), it follows that $$T(n)$$ is proportional to $$n \log(n)$$. Specifically, our rule for combining $$A$$ and $$B$$ amounts to this: If $$A + T(A)x$$ is multiplied by $$B + T(B)x$$ where $$x^2 = 0$$, then the result is $$AB + T'(AB)x$$, where $$T'(AB)$$ is one allowed runtime for $$T(AB)$$. If we start only with base cases of the form $$A + A \log(A)kx = A(1 + \log(A)kx) = A^{kx + 1}$$, then everything we build up inductively has this form as well. More generally, if different building blocks have different $$k$$ here, what we discover is that the run-time for some $$N$$ which decomposes as $$A$$ times $$B$$ times $$C$$, etc, will be $$N [k_A \log(A) + k_B \log(B) + \ldots]$$, which is between $$N k_{min} \log(N)$$ and $$N k_{max} \log(N)$$.