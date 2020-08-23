---
layout: post
title:  "Prime-Generating Polynomial"
date: 2020-1-19
---
Some numbers p have the property that multiplying two consecutive integers and then adding p generates only prime number outputs, so long as both consecutive integers are less than p in size. (By symmetry of multiplication under negation, it suffices to consider just consecutive natural numbers less than p)

In particular, by considering the case of zero times one, we need p itself to be prime (unless p is one or smaller, a trivial loophole in the wording above).

When $$p = 2$$, we satisfy the condition, but this can be seen as another kind of too small triviality. Beyond this, any prime $$p$$ must be odd, and as we will see below, this brings us into a realm of nicer theory.

The relevant range of this monotonic polynomial $$G(n) = n(n + 1) + p = n^2 + n + p$$ then stretches from $$G(0) = p$$ up through $$G(p - 2)$$, after which we hit $$G(p - 1) = p^2$$. In particular, within the relevant range, all the outputs have size less than $$p^2$$; if any value of such size had any nontrivial factor, it would have a nontrivial factor less than $$\sqrt{p^2} = p$$.

Thus, to establish that $$p$$ has the relevant property, it suffices to establish that $$G(n)$$ is never divisible by any prime less than $$p$$ [if it were divisible by such a value at any point, it would have to be divisible by such a value at some point in the relevant range, by the fact that G(n) mod x = G(n mod x) mod x].

So long as $$p$$ is odd, we will always have that $$G(n) = n(n + 1) + p$$ is odd as well [the product of two consecutive values is always even], ensuring that $$G(n)$$ is never divisible by $$2$$. So what remains is to ensure that $$G(n)$$ is never divisible by any odd prime $$q < p$$.

For this consideration, we can apply the quadratic formula, to see that $$n^2 + n + p = 0$$ has solutions in mod $$q$$ land just in case there is a square root of the discriminant $$1 - 4p$$ in mod $$q$$ land.

TODO: Finish writing this out.

It turns out this all also happens just in case the ring of integers over $$Q(\sqrt{1 - 4p})$$ has unique factorization (i.e., class number one). And it turns out the largest $$p$$ with this property is $$41$$ (though this was only proven in the mid-20th century, and thus is probably a difficult result).

TODO: Speak of j-invariant as well.