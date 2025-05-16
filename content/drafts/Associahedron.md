---
title: "Associativity and the Associahedron"
date: 2020-12-29
---
The order $N$ associahedron is an abstract polytope whose vertices are all binary trees with $N$ many leaf nodes (where a binary tree is either a leaf node or an ordered pair of two child binary trees). One can describe this same thing in many different words, as having to do with parenthesization or such things. It's all the same.

To be a polytope, we must describe not just the vertices, but also the edges, faces, etc. To be an abstract polytope, we must satisfy the property that whenever an $N$-cell is contained within an $(N + 2)$-cell, there are precisely two intermediate $(N + 1)$-cells. There should also be a unique $(-1)$-cell and a unique top-dimensional cell.

Thus, in general, from any collection of finite sets all of size $N$ with the property that removing any element from such a set allows for the insertion of a unique different element to obtain any other set in the collection, we get an abstract polytope where the $(N - 1)$-cells are the subsets of size $N$ of any set in the collection, on top of which we add a unique $N$-cell, ordered by subset inclusion. The "Two ways to fill an intermediate value" property is automatic everywhere (between {a, b, ...} and {...}, there are intermediate subsets {a, ...} and {b, ...}) except at the top dimension, where we've imposed it by fiat as a property of our collection.

We can also dualize this by reversing the ordering, swapping our notion of $k$-cells and $(N - 1 - k)$-cells.

The associahedron is the dual polytope we obtain in this way, where the sets we are interested in are all the allowed sets of position-pairs at which to insert left and right parentheses between $N$ letters. [TODO: Elaborate on details and prove the nontrivial property at the top]

***

An interesting property is to show that the associahedron is connected at all. That is, for any two different parenthesizations, we can get from one to the other just using the (a + b) + c = a + (b + c) rule.

This is most cleanly shown like so: We will demonstrate inductively that any sum can be both left- and right-associated by this rule. This is trivially true for 0-ary and 1-ary sums. Everything else is built up by binary summation from the 1-ary sums.

So suppose we are looking at A + B where A and B are themselves complex summations. Inductively, take A as left-associated and B as right-associated. Now it is clear that we can one at a time move elements at the right end of A into the left end of B or vice versa by our (a + b) + c = a + (b + c) rule, and by doing so repeatedly fully in a consistent direction, we can move all of A into B and get a right-associated result, or all of B into A and get a left-associated result. This completes the proof.

***

[TODO: Describe Catalan numbers]