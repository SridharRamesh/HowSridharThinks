---
title: "Small Free Nondeterministic Structures"
date: 2022-10-19
---
The following generalization of a certain traditional argument occurred to me today, my needing it in some argument, and so I thought I would record it for my own future use if ever I need it again:

Suppose given a (possibly large collection) V, along with a small number of operations from powers of V to itself. Each of these operations has a fixed small arity. Furthermore, these operations may be partial or nondeterministic: That is, instead of outputting a single element of V, they may output a set of elements of V. The cardinality of this set need not be bounded in any a priori fashion, except that it must indeed be a small set and not a proper class.

Then there is a small subset of V which is closed under all of these operations (in the sense that it includes ALL results of applying any of these operations to itself).

Proof: Consider all the well-founded syntax trees describing some way of composing these operations. There are only a small number of shapes such trees can take (we have a suitable W-type describing the set of such trees). For any such tree, we may inductively prove that the possible values taken by any node within that tree comprise a small set (there are a small number of children of this node, each of which may take on a small number of values, and also a small number of choices for the label at this node specifying which operation we are using. Thus, a small number of choices for the tuple altogether of what operation we are applying to what values. For each of these choices, we have a small number of possible outputs. And thus the number of possible values this node may take on is the union of a small set of small sets, thus itself small). Thus, the number of possible values output at the root is the union over a small number of tree shapes of the small number of possibilities at the root of each such tree shape. Thus, itself small, completing the proof.