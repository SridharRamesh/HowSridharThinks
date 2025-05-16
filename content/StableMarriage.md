---
title: "Transfinite Stable Marriage"
date: 2019-11-17
---
Suppose you have a set of men $$M$$ and women $$W$$, and every man comes with a well-order on the women (where we take the smallest woman in a set to be the man's favorite among that set; a well-order amounts to the same thing as a way of assigning to each inhabited set a favorite, such that the favorite is stable under constraining to any subset of options still containing the former favorite) and vice versa. Actually, we'll say each man $$m$$ comes with a well-order on some $$W_m = W' \cup \{Nobody\}$$, where $$W'$$ is some subset of $$W$$ and $$Nobody$$ is the maximal (i.e., least favored) element in this ordering. And symmetrically for the women having well-ordered preferences among the men. (This amounts to having favorites within any set that also includes a $$Nobody$$ option)

Given a function that assigns to each $$m \in M$$ an element of $$W_m$$ [and whenever I make a statement like this, it of course applies mathematically just as well with genders flipped], we may order these point-wise by the product of the preference orders among each person in the domain. These orderings on such functions comprise complete lattices (since any well-ordering with a maximum element is a complete lattice, and this is a property inherited by products). Call this sort of thing a "choice function for men".

We can turn a choice function $$f$$ for men into a choice function $$g$$ for women like so: say a man $$m$$ is eligible for a woman $$w$$ if $$m$$ favors $$w$$ over $$f(m)$$. Let $$g(w)$$ be $$w$$'s favorite man out of all those who are eligible for her (or $$Nobody$$).

This operation turning any choice function for one gender into a choice function for the other gender is order-reversing.

Invoking Knaster-Tarski, it now follows that there is a complete lattice of "stable" assignments; that is, choice functions for both genders, each of which is the other's image under this transformation. The lattice of these is complete with respect to the ordering on either gender's choice functions, which are precisely opposite orders.

In particular, there exists at least one stable assignment.

Note that in any stable assignment, $$m$$ is assigned $$w$$ if and only if $$w$$ is assigned $$m$$. Thus, a stable assignment is the same thing as a partial bijection between the men and the women, such that no man and woman each strictly prefer each other to their current assignment.

***

Much more generally, this works if each person has some complete lattice of options [of whatever sort; what dinner to have, which relative to visit for Christmas, whatever], with the available options for any person becoming narrower as people of the opposite gender get more favorable assignments [including restrictions triggered not by any individual's assignment but by coalitions' assignments], but the available options always having a most favorable value.

Just as well, it'd work the other way, cooperatively rather than competitively, if the available options for any person expanded as the other gender got more favorable assignments.

***

[To be expanded upon into a post talking about Knaster-Tarski, observation that it can be carried out from bottom up or from top down, initial algebras, coalgebras, Lambek's lemma, Adamek construction of initial algebras, initial objects as limits of entire categories (see [Total Limits Are Empty Colimits]({{ site.baseurl }}{% link _math/TotalLimits.md %}))]

[TODO: Talk about how stable matchings are preserved under pointwise inhabited meets, so to speak.]

[TODO: Perhaps also consider what happens when we allow ties? Perhaps also consider if there is some relation to voting systems here. For that matter, perhaps there is some relation to forcing. I don't know. These are vague thoughts.]

[TODO: Observe that the same Knaster-Tarski style argument gives us a much more general result along the lines of stable marriage; to wit, if every person has a well-ordered set of options available to them (not necessarily options among the other gender, just options of some sort), with various exclusion rules such that options are taken off the table when someone of the other gender selects at or better than some choice, but with last choice options always on the table, we get still a "stable" way of selecting options for each person; that is, a way of selecting options where everyone's selection is their favorite permitted given the other gender's selections]

[TODO: This framing in terms of best choices given the other gender's selections suggest a connection with the Nash equilibrium existence theorem, which is also proven using a fixed point theorem (though usually Brouwer's or Kakutani's). Is there a connection here?]