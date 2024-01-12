---
title: "Conjugate Partitions As Adjoints"
date: 2024-1-11
---
Just a small note on conjugate partitions as adjoint functors (more specifically, Galois connections). Nothing earth-shattering but I wished to remember these thoughts for myself:

By a partition of a natural number n is meant a multiset of positive integers which sum to n. We can uniquely represent this as an ordered sequence of positive integers summing to n. Put another way, we can uniquely represent this as an infinite sequence of natural numbers summing to n, with each element of the sequence ≥ the next one, eventually hitting 0. For example, one partition of the number 10 is the sequence 5, 3, 1, 1, 0, 0, 0, …

It is common to correspond partitions with so-called "Young diagrams", and then use these to define "conjugate partitions". I wish to note here that this is all a special case of the standard category theoretic concept of adjoint functors (with Young diagrams as the corresponding bimodules/profunctors).

First of all, we may take a partition such as the 5, 3, 1, 1, 0, 0, 0, … example above and view it as a contravariant function from the poset of natural numbers to itself. Specifically, the function f such that f(0) = 5, f(1) = 3, f(2) = 1, and so on, with f(n) as the n-th element of the sequence, starting with a 0-th element.

We may then define more generally a binary relation r(m, n) by m < f(n). This relationship is contravariant in both its arguments in the sense that if m ≥ m' and n ≥ n', then r(m, n) implies r(m', n'). This r acts as our "Young diagram".

In general, a Boolean-valued contravariant binary relation like this will come from some f in this way just in case both r(0, n) and r(m, 0) can be made false with suitable choices of n and m.

In particular, this is a symmetric condition, so our relation m < f(n) must be equivalent to the relation n < g(m) for some function g (also contravariant from naturals to naturals).

In this way, we obtain from any f a "conjugate" g. And conversely, f will be the conjugate of g as well. These conjugates f and g will be partitions of the same number, since this number can be viewed as the number of ordered pairs satisfying the relation r.

In our example above, the conjugate to 5, 3, 1, 1, 0, 0, 0, … will be 4, 2, 2, 1, 1, 0, 0, 0, …, both partitions of 10.

This conjugate relationship that m < f(n) iff n < g(m) is very nearly the original definition of a Galois connection (aka, adjoint order-reversing maps between posets). Except we have used the strict inequality < here, rather than the ≤ which would be used for a Galois connection.

Much of the theory of adjunctions (such as the uniqueness of the adjoint) still works for an extensional strict ordering relation such as < on the natural numbers (extensional in the sense that the "Yoneda embedding" sending a value to the set of values below it remains injective). But we can make this into proper adjoint functors too.

To do so, we augment our poset to be not just the natural numbers, but the natural numbers with an added ∞ element on top. We now represent a partition as a contravariant endofunction which sends 0 to ∞ and sends ∞ to 0, while acting on the positive integers in the manner of the original sequence (thus, our example partition 5 + 3 + 1 + 1 becomes f(1) = 5, f(2) = 3, f(3) = 1, f(4) = 1, f(5) = 0, etc). Note that this is "shifted over by one", in some sense, from our original indexing. We will find that conjugate partitions become true adjoints with this representation, in the sense that m ≤ f(n) iff n ≤ g(m).