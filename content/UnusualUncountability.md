---
title: "Unusual Uncountability Proofs"
date: 2020-4-22
---
Everyone knows the diagonalization proof of uncountability. Some are familiar with other uncountability proofs as well; e.g., Cantor's original proof of the uncountability of R [TODO: discuss this, relate it to the diagonalization proof] [TODO: Discuss all the famed antinomies and how they become uncountability proofs; e.g., Burali-Forti/Mirimanoff]. Here's one I came up with which I've never seen anyone else mention, though:
<!--more-->

\[Edited to add in 2026: Alas, there's nothing new under the sun. See https://arxiv.org/abs/0901.0446 for a similar uncountability proof by Eliahu Levy (inspired by Bourbaki's proof of chapter 1, section 2, Proposition 2, from "Fonctions d'une variable reelle", though that proposition concerning the mean value theorem is in very different and more specific terms, and not framed as an uncountability proof).\]

***

**Lemma:** Let $$X$$ be a partially ordered set and let $$\mathcal{P}(X)$$ be its powerset, ordered by inclusion. Given any monotonic map $$F : \mathcal{P}(X) \to X$$, there is some point at which this map fails to be strictly monotonic (that is, $$A \subsetneq B$$ such that $$F(A) = F(B)$$).

**Proof:** We can define an increasing transfinite sequence of values in $$X$$, defined by the rule that each value in the sequence is $$F$$ applied to the set of previous values. We extend this sequence as far as it can go. The only situation under which we cannot extend the sequence any further is when the next value we wish to add to it is already in it; at this point, the sequence ceases to strictly increase and becomes constant. I.e., we must stop when we hit some point at which $$F(S)$$ is already in $$S$$, the sequence so far. At this point, we find that $$F(S) = F(S - F(S))$$, which is the violation of strict monotonicity we seek. Since we extend our sequence as far as we can go, by definition, the sequence we produce cannot be extended any further, and so this must happen eventually. This is an preformal way of saying that our sequence must stop increasing eventually because its definition yields a map from the ordinals into our set, and the proper class of ordinals cannot embed into a set.

Why are the ordinals a proper class? Well, the defining property of ordinals is that every set of ordinals is followed by another ordinal strictly larger than all of them. Thus, there is no set of all ordinals.

This can all be phrased without ever referencing the ordinals, though. Another way of putting it is this:

Say a well-ordered subset of $$X$$ is inductive if each value within it is equal to $$F$$ applied to the set of lesser values within it.

It is easy to show that, for any two inductive sets, one is an initial segment of the other. Using this, it is then easy to show that the union of any collection of inductive sets is itself inductive. Using this, we can take the union of all inductive sets, to find a maximum inductive set.

Furthermore, applying $$F$$ to any inductive set yields a value at least as large as all the elements of the inductive set (since each element within the inductive set is $$F$$ applied to some subset of the inductive set). Thus, for any inductive set $$S$$, we have that $$S \cup \{F(S)\}$$ is also an inductive set. When $$S$$ is the maximum inductive set, we must therefore have that $$S = S \cup \{F(S)\}$$, and thus that $$F(S)$$ is itself the maximum element of $$S$$. But then $$F(S)$$ must equal $$F(S - F(S))$$, which is the violation of strict monotonicity that we sought.

Note that we can still carry out this argument even if $$X$$ has no particular presumed partial order. We can define an inductive subset of $$X$$ as one which admits _some_ well-ordering such that each value within it is equal to $$F$$ applied to the set of lesser values within it. We can still show the same facts about inductive sets as above (in particular, for any two inductive sets, one is an initial segment of the other, and thus there is at most one way to order a given set as an inductive set), and thus conclude that there is a largest inductive set $$S$$, and that this $$S$$ has a maximum element equal to both $$F(S)$$ and $$F(S - F(S))$$.

\[This is related to [the proof of Knaster-Tarski](@/LambekKnasterTarski.md)\]

***

**Theorem:** The reals are not in bijection with the naturals. Indeed, they are not even a subquotient of the naturals.

**Proof:** Take your favorite convergent countably infinite collection of positive reals (e.g., assign to each natural $$n$$ the value $$2^{-n}$$). This induces a strictly monotonic map from $$\mathcal{P}(\mathbb{N})$$ to $$\mathbb{R}$$, by sending a set of naturals to the sum of the correspondingly indexed entries of the convergent collection. But we cannot have a strictly monotonic map from $$\mathcal{P}(\mathbb{R})$$ to $$\mathbb{R}$$, as noted in our lemma. Thus, $$\mathbb{N}$$ and $$\mathbb{R}$$ cannot be isomorphic.

In the above argument, the only important fact about the naturals was that they index a convergent collection of positive values. Any subset of a convergent collection of positive values is also a convergent collection of positive values. Furthermore, any quotient of the indices of a convergent collection of positive values can be made to to index a convergent collection of positive values, by assigning to each element of the quotient the sum of the values at the indices corresponding to this quotient element. Thus, the reals cannot even be a subquotient of the naturals.

***

Note that one corollary of our lemma is that the powerset of $$X$$ can't inject into $$X$$. (We can either use the partial ordering on $$X$$ pushed forward from the ordering on its powerset, or we can understand the lemma in terms which do not involve a partial ordering). This amounts to the Burali-Forti paradox. So our argument can be seen as a particular way of thinking about the Burali-Forti paradox: We know that the powerset of the naturals injects into the reals via probabilities (in some distribution with everywhere positive support), and thus Burali-Forti prevents us from having the reals inject into the naturals (which in turn prevents the well-ordered naturals from having any partial surjection onto the reals).