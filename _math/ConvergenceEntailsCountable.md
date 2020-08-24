---
title:  "Convergence Entails Countable Support"
date: 2020-4-22
---
Consider a multiset of values, all $$\geq 0$$ ("semipositive", as I often say in my head). It is clear how any finite submultiset of these are to be summed, and we can define the sum of the multiset overall as the supremum of the sum of its finite submultisets.

This reproduces the schoolbook limit-based definition, when the multiset is countable and arranged into a series with whatever order you like. However! This definition does not automatically restrict us to only considering countable multisets.

Naturally, the question then arises, can we have examples of multisets which converge to a finite sum, but whose support is uncountable?

Alas, the answer is no, and for a very simple reason: suppose the sum converges to L. Then there is at most 1 value in our mulutiset of size up to L, at most 2 values of size up to L/2, at most 3 values of size up to L/3, etc. Putting all this together, there are at most countably many values which are finitesimal in comparison to L. Working within an Archimedean framework (i.e., $$\mathbb{R}$$), as we usually must to make sense of suprema, the infinitesimal values are all zero, and so our support is countable.

***

One consequence of this is that any ordinal which embeds into the reals is countable: WLOG, it can be reparametrized to embed into a finite interval. The jumps between values and their successors then form a multiset whose sum converges to at most the size of the interval. Thus, there are at most countably many embedded values. Another way of proving this result, not using the above, is by noting that each of the intervals between a value and its successor must contain a rational, and there are at most countably many rationals. I wonder how to relate these arguments, or how to relate the relation between these to the above.