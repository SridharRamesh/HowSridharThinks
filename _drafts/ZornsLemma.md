---
title: "Zorn's Lemma"
date: 2022-12-12
---
Here are two framings and proofs of Zorn's Lemma:

(Throughout the following, given a set or predicate S and an element x, we write S_{< x} to mean those elements of or satisfying S which are < x.)

1. In any poset whose underlying set is well-orderable, there is a chain with no strict upper-bound.

Proof: Let (P, <) be our poset, and let |<| be the well-ordering on its elements. By transfinite recursion with respect to |<|, we construct a predicate In on the elements of P, such that In(p) holds just in case p is a strict upper bound on those elements |<| p which satisfy In. The elements which satisfy In are totally ordered (as the < and |<| relations coincide on these). However, no element p can be a strict upper bound on the elements satisfying In (for either p satisfies In itself, or if not, this is because p is not even a strict upper bound on those elements |<| p which satisfy In).

2. Given any partial function Bound from chains in a poset P to strict upper bounds on those chains, there is some chain for which Bound is undefined.

Proof: Let us say a subset S of P is "inductive" if it is well-ordered and each element s of S is equal to Bound(the subset of S which is less than s). Given any two inductive sets, we can readily observe by transfinite recursion that one is an initial segment of the other (this is the same as the standard proof that ordinals are linearly ordered). With this in mind, it's easy to show also that any union of inductive sets is inductive, and thus by taking the union of all inductive sets, we obtain a largest inductive set. But a largest inductive set must be such that applying Bound to it does not yield a new upper bound by which it can be extended to an even larger inductive set. Thus, the largest inductive set is a chain for which Bound is undefined.

****

Note that the second framing here makes Zorn's lemma very similar to the bottoms-up proof of Knaster-Tarski; i.e., Adamek's construction. This is the main thing I wished to point out in this post. \[TODO: Flesh this out.\]

Note also that neither framing here relies upon the Axiom of Choice. The Axiom of Choice is just used to provide well-orderability in the first place, or to make a single-valued function Bound assigning strict upper bounds to every chain which has one.

Note also that to say that all chains have a strict upper bound is the same as to say that all chains have an upper bound and all elements have a strict upper bound. In practice, Zorn's Lemma is often applied in situations where all chains have a least upper bound. In this case, we may in #2 consider some partial function f which assigns strict upper bounds to elements, and define Bound(chain) as f(least upper bound(chain)). #2 then finds us a value (the least upper bound of the largest inductive set) for which f is undefined. In the context of the Axiom of Choice, f can be chosen at random to be defined on all values which have strict upper bounds, so this is the same as finding a maximal value.

****

TODO: Discuss the web of entailments between choice-free Zorn's lemma, choiceful Zorn's lemma, the Axiom of Choice, and the well-ordering principle.