---
title: "Hylomorphisms"
date: 2022-12-3
---
Here I record some simple thoughts on hylomorphism correspondences.

Let $$F$$ be an endofunctor on some category, let $$W : w \to F(w)$$ be an $$F$$-coalgebra, and let $$M : m \to F(m)$$ be an $$F$$-algebra. Then by an $$F$$-hylomorphism, we mean a commutative square of the following form:

<iframe class="quiver-embed" src="https://q.uiver.app/?q=WzAsNCxbMCwxLCJ3Il0sWzAsMCwiRih3KSJdLFsxLDAsIkYobSkiXSxbMSwxLCJtIl0sWzAsMSwiVyJdLFsxLDIsIkYoeCkiXSxbMiwzLCJNIl0sWzAsMywieCIsMl1d&embed" width="325" height="304" style="border-radius: 8px; border: none;"></iframe>
<!--
\[\begin{tikzcd}
    {F(w)} & {F(m)} \\
    w & m
    \arrow["W", from=2-1, to=1-1]
    \arrow["{F(x)}", from=1-1, to=1-2]
    \arrow["M", from=1-2, to=2-2]
    \arrow["x"', from=2-1, to=2-2]
\end{tikzcd}\]
-->

In other words, a fixed point for the map $$x \mapsto M \circ F(x) \circ W$$.

Recall that, when dealing with two functions $$f$$ and $$g$$ in opposite direction between two sets, the fixed points of $$f \circ g$$ and of $$g \circ f$$ are in bijection, as induced by $$g$$ and $$f$$.

Thus, when $$F$$ and $$G$$ are functors in opposite direction between two categories, we have a bijective correspondence between $$FG$$-hylomorphisms $$F(V) \circ W \to M \circ F(N)$$ and $$GF$$-hylomorphisms $$G(W) \circ V \to N \circ G(M)$$, as illustrated below:

<iframe class="quiver-embed" src="https://q.uiver.app/?q=WzAsMTIsWzMsMiwidiJdLFs0LDIsIm4iXSxbMywwLCJHKEYodikpIl0sWzQsMCwiRyhGKG4pKSJdLFszLDEsIkcodykiXSxbNCwxLCJHKG0pIl0sWzAsMSwiRih2KSJdLFswLDAsIkYoRyh3KSkiXSxbMSwwLCJGKEcobSkpIl0sWzEsMSwiRihuKSJdLFswLDIsInciXSxbMSwyLCJtIl0sWzAsMSwieSIsMl0sWzIsMywiRyhGKHkpKSJdLFs0LDIsIkcoVykiXSxbMyw1LCJHKE0pIl0sWzAsNCwiViJdLFs1LDEsIk4iXSxbNiw3LCJGKFYpIl0sWzgsOSwiRihOKSJdLFs3LDgsIkYoRyh4KSkiXSxbMTAsMTEsIngiLDJdLFsxMCw2LCJXIl0sWzksMTEsIk0iXV0=&embed" width="912" height="432" style="border-radius: 8px; border: none;"></iframe>
<!--
\[\begin{tikzcd}
    {F(G(w))} & {F(G(m))} && {G(F(v))} & {G(F(n))} \\
    {F(v)} & {F(n)} && {G(w)} & {G(m)} \\
    w & m && v & n
    \arrow["y"', from=3-4, to=3-5]
    \arrow["{G(F(y))}", from=1-4, to=1-5]
    \arrow["{G(W)}", from=2-4, to=1-4]
    \arrow["{G(M)}", from=1-5, to=2-5]
    \arrow["V", from=3-4, to=2-4]
    \arrow["N", from=2-5, to=3-5]
    \arrow["{F(V)}", from=2-1, to=1-1]
    \arrow["{F(N)}", from=1-2, to=2-2]
    \arrow["{F(G(x))}", from=1-1, to=1-2]
    \arrow["x"', from=3-1, to=3-2]
    \arrow["W", from=3-1, to=2-1]
    \arrow["M", from=2-2, to=3-2]
\end{tikzcd}\]
-->

This is by considering the two operations $$x \mapsto N \circ G(x) \circ V$$ and $$y \mapsto M \circ F(y) \circ W$$, and the fixed points of their compositions in either order.

For example, if we take $$V$$ and $$N$$ to be identities, then this tells us that the $$FG$$-hylomorphisms from $$W$$ to $$M$$ are in bijection (via applying $$G$$) with the $$GF$$-hylomorphisms from $$G(W)$$ to $$G(M)$$.

Or if we take $$W$$ and $$N$$ to be identities, then this tells us that the $$FG$$-hylomorphisms from $$F(V)$$ to $$M$$ are in bijection with the $$GF$$-hylomorphisms from $$V$$ to $$G(M)$$. \[This special adjunction-like case is discussed in "Conjugate Hylomorphisms" by Hinze et al, under the name "rolling rule", and attributed to Eppendahl. Indeed, it is lemma 3.1 in Eppendahl's "Coalgebra-to-Algebra Morphisms". Neither author discusses our more general observation or even our first special case. There is some interesting discussion by Eppendahl at the end of his paper on Freyd's iterated square and Lambek's lemma, as concerns initial algebras for squared endofunctors.\]