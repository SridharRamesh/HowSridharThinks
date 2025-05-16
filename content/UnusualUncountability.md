---
title: "Unusual Uncountability Proofs"
date: 2020-4-22
---
Everyone knows the diagonalization proof of uncountability. Some are familiar with other uncountability proofs as well; e.g., Cantor's original proof of the uncountability of R [TODO: discuss this, relate it to the diagonalization proof] [TODO: Discuss all the famed antinomies and how they become uncountability proofs; e.g., Burali-Forti/Mirimanoff]. Here's one I came up with which I've never seen anyone else mention, though:

***

**Lemma:** Let $$X$$ be a partially ordered set [TODO: What changes for a preorder?] and let $$\mathcal{P}(X)$$ be its powerset, ordered by inclusion. Given any monotonic map $$F : \mathcal{P}(X) \to X$$, there is some point at which this map fails to be strictly monotonic (that is, $$A \subsetneq B$$ such that $$F(A) = F(B)$$).

**Proof:** We can define an increasing transfinite sequence of values in $$X$$, defined by the rule that each value in the sequence is $$F$$ applied to the set of previous values. We extend this sequence as far as it can go. The only situation under which we cannot extend the sequence any further is when the next value we wish to add to it is already in it; at this point, the sequence ceases to strictly increase and becomes constant. I.e., we must stop when we hit some point at which $$F(S)$$ is already in $$S$$, the sequence so far. At this point, we find that $$F(S) = F(S - F(S))$$, which is the violation of strict monotonicity we seek. Since we extend our sequence as far as we can go, by definition, the sequence we produce cannot be extended any further, and so this must happen eventually. This is an preformal way of saying that our sequence must stop increasing eventually because its definition yields a map from the ordinals into our set, and the proper class of ordinals cannot embed into a set.

Why are the ordinals a proper class? Well, the defining property of ordinals is that every set of ordinals is followed by another ordinal strictly larger than all of them. Thus, there is no set of all ordinals.

This can all be phrased without ever referencing the ordinals, though. Another way of putting it is this:

Say a well-ordered subset of $$X$$ is inductive if each value within it is equal to $$F$$ applied to the set of lesser values within it.

It is easy to show that, for any two inductive sets, one is an initial segment of the other. Using this, it is then easy to show that the union of any collection of inductive sets is itself inductive. Using this, we can take the union of all inductive sets, to find a maximum inductive set.

Furthermore, applying $$F$$ to any inductive set yields a value at least as large as all the elements of the inductive set (since each element within the inductive set is $$F$$ applied to some subset of the inductive set). Thus, for any inductive set $$S$$, we have that $$S \cup \{F(S)\}$$ is also an inductive set. When $$S$$ is the maximum inductive set, we must therefore have that $$S = S \cup \{F(S)\}$$, and thus that $$F(S)$$ is itself the maximum element of $$S$$. But then $$F(S)$$ must equal $$F(S - F(S))$$, which is the violation of strict monotonicity that we sought.

[This is related to [the proof of Knaster-Tarski](@/LambekKnasterTarski.md)]

***

**Theorem:** The reals are not in bijection with the naturals. Indeed, they are not even a subquotient of the naturals.

**Proof:** Take your favorite convergent countably infinite collection of positive reals (e.g., assign to each natural $$n$$ the value $$2^{-n}$$). This induces a strictly monotonic map from $$\mathcal{P}(\mathbb{N})$$ to $$\mathbb{R}$$, by sending a set of naturals to the sum of the correspondingly indexed entries of the convergent collection. But we cannot have a strictly monotonic map from $$\mathcal{P}(\mathbb{R})$$ to $$\mathbb{R}$$, as noted in our lemma. Thus, $$\mathbb{N}$$ and $$\mathbb{R}$$ cannot be isomorphic.

In the above argument, the only important fact about the naturals was that they index a convergent collection of positive values. Any subset of a convergent collection of positive values is also a convergent collection of positive values. Furthermore, any quotient of the indices of a convergent collection of positive values can be made to to index a convergent collection of positive values, by assigning to each element of the quotient the sum of the values at the indices corresponding to this quotient element. Thus, the reals cannot even be a subquotient of the naturals.

***

Note that one corollary of our lemma is that the powerset of $$X$$ can't inject into $$X$$. For then we could simply define on $$X$$ the partial ordering pushed forward from the ordering on its powerset, and then appeal to the lemma for a contradiction. (This amounts to the Burali-Forti paradox). This gives us another way to prove the uncountability of the reals, given that the powerset of the naturals injects into the reals, but this would not be very far from the traditional proof. Note that we do not actually use this embedding of the powerset of the naturals into the reals in the above argument.