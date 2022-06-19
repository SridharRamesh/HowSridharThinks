---
title: "Confluence"
date: 2019-11-18
---
A) Say relation → is "confluent against" ↓ if, given a→b and a↓c, ∃d with b↓d and c→d (ie, given the top and left of a square, you can fill out the rest).

Claim: If → is confluent against ↓, then →\* is confluent against ↓\*, where \* denotes reflexive transitive closure

Proof: Given the top and left of a rectangle, fill out the rest with squares, piece by piece.

B) Say → is "near-confluent against" ↓ if the above confluence property is only demanded when b and c are distinct.

Claim: If → is near-confluent against ↓, then →+ is confluent against ↓+, where + denotes reflexive closure.

Proof: Easy examination of cases.

So if one relation is near-confluent against another, then their reflexive transitive closures are confluent against each other. In particular, if a relation is near-confluent against itself (what we might call the relation being near-confluent simpliciter), then its reflexive transitive closure is confluent against itself (confluent simpliciter). This comes up often.

Note that if we attach labels to instances of these relations, and have an equivalence relation on products of labels, and demand that both paths from starting to ending corner of a confluence square give equivalent products of labels, this aggregates to the same equivalence of label products property for confluence rectangles in general, and thus the at most one irreducible value reachable from a starting point also has a unique-up-to-equivalence product of labels en route to it.

For example:

[TODO: Define sandpile toppling]. Note that the one-step sandpile toppling relation is near-confluent (even when labelling reductions by locations of topples), as, whenever one has two distinct toppling locations available, either one remains available after toppling the other, and toppling the two successively in either order brings one to the same resulting state. Thus, the many-step sandpile toppling relation is confluent. As a corollary, there is at most one stable sandpile reachable from a given sandpile, and any way of reaching it topples the same locations the same number of times.

The Jordan-Holder theorem is another instance of this labelled confluence unique factorization result: If $$G$$ is a group, with $$N_1$$ and $$N_2$$ as distinct normal subgroups with corresponding simple quotient groups $$s_1$$ and $$s_2$$, then $$N_1 \cap N_2$$ is a normal subgroup of both $$N_1$$ and $$N_2$$, and the quotients are nontrivial normal subgroups of $$s_2$$ and $$s_1$$ respectively; thus, $$s_2$$ and $$s_1$$ respectively. This gives us labelled near-confluence, taking multiset equivalence on products of labels, establishing that any two composition series for the same group have the same multiset of composition factors.

[TODO: Perhaps discuss lambda calculus confluence as well. Here, we can use "parallel one-step reduction" to get confluence; i.e., the method of Tait and Martin-Loef]

[TODO: Note that uniqueness of prime factorizations in a GCD domain follows this pattern as well (though it's easy enough to see without using this formulation, but nonetheless, it is a special case of this, closely related to the Joran-Holder instance above). This is a "commutative" example; one where the moves available only shrink after moves are taken, never expand in any way, so that it follows that, given (near-)confluence, we can transpose any two adjacent moves, and therefore EVERY permutation of a reduction to normal form gives another reduction to the same normal form]

[TODO: The fact that any two ways of counting a finite set yield the same ordinal is a consequence of confluence: consider a stage in counting to be the set of elements uncounted so far, with all single-step labels being the ordinal 1 and label product equivalence being as concatenation of ordinals. This is readily seen to be near-confluent, and thus we have unique ordinals attached to each finite set, and indeed, given the existence of an ordinal length n path to normal form, any random path of ordinal length m from the start will not have hit normal form yet if $$m < n$$, hitting normal form precisely when $$m = n$$, preventing $$m > n$$ from being reached.

Actually, there's a property in play here that's not just confluence: from any position, all the moves available are actually isomorphic, in some sense. "All moves available are isomorphic" and confluence are incomparable properties (the former doesn't guarantee a unique normal form, just a unique normal form up to isomorphism, and the latter doesn't guarantee a unique reduction sequence up to isomorphism), but both are special cases of some more general bisimulation property, which guarantees a unique length, and indeed unique label-product, of reduction to normal form.]

An important counterexample to keep in mind is that proving confluence by taking in one-steps as input and yielding many-steps as output doesn't work. That is, "Given a→b and a↓c, ∃d with b↓\*d and c→\*d" does not entail that →\* is confluent against ↓\*. Indeed, even if → and ↓ are presumed the same, this entailment fails. A very simple example is where A → B, B → A, A → X, and B → Y, with no other relations. An acyclic example of which this is a quotient is where we consider two countably infinite sets A(i) and B(i) indexed by natural numbers, such that A(i) → A(i + 1), A(i) → B(i), and B(i) → B(i + 2), with no other relations.

However, to show →\* is confluent against ↓, it DOES suffice to show that → and ↓ can be confluently completed to →\* and ↓. This is an easy induction in the length of the provided top →\* side in the desired →\* against ↓ confluence rectangle. It follows that to show →\* confluent against ↓\*, it DOES suffice to show that → and ↓\* can be confluently completed to →\* and ↓\*. [This is used in the proof of the Church-Rosser theorem; i.e., lambda calculus confluence]

[TODO: Actually illustrate the rectangle diagrams in all the above visually]