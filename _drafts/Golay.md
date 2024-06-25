---
title: "Golay codes"
date: 2024-6-9
---
Assorted results about Golay codes:

***

Given two points in 2^N (i.e., two functions from an N-element set to the 2-element field), their Hamming distance is the number of coordinates (i.e., inputs) on which they differ. By weight, I mean Hamming distance from the zero vector.

By the perfect Golay code, I mean a subset S of 2^23 such that for every point P in 2^23, there is a unique Q in S at Hamming distance ≤ 3 from P.

By an extended Golay code, I mean a subset S of 2^24 containing only points of even Hamming distance from each other (that is, whose weights are all the same parity), such that for every point P in 2^24 at odd Hamming distance from S (that is, whose weight is the opposite parity), there is a unique Q in S at Hamming distance ≤ 3 from P.

Golay codes (of whichever type) containing point $$P_1$$ and Golay codes (of the same type) containing point $$P_2$$ are in 1:1 correspondence, through the map $$x \mapsto x - P_1 + P_2$$. For convenience, we therefore from hereon assume our Golay codes contain the zero vector.

Perfect Golay codes and extended Golay codes are in 1:1 correspondence, like so: Given a perfect Golay code, we may add a parity check bit at the end to obtain an extended Golay code. Conversely, given an extended Golay code, we may drop its last bit to obtain a perfect Golay code. TODO: Describe this less tersely.

We say an extended Golay code is doubly even if all its vectors have weight divisible by 4.

***

Proof that any two perfect Golay codes containing the zero vector have the same number of codewords of each particular weight (and thus the same is true for extended Golay codes): By induction on weight, we can calculate the number of codewords there must be of each particular weight. TODO.

It follows that we also have the same result for extended Golay codes.

In particular, once we know there is ANY doubly even extended Golay code, it follows that EVERY extended Golay code is doubly even. Actually, we can go ahead and calculate the unique potential weight distribution by the method of this proof without first knowing of the actual existence of a Golay code, and by examination we see that it is doubly even.

***

Proof that any extended Golay code is a linear subspace of 2^24:

Double-evenness of all Golay codes, and the ability to rebase our Golay code around any particular point reinterpreted as zero, tells us that all Hamming distances between codewords are doubly even; i.e., the dot product (v - w)^2 is always doubly even. But (v - w)^2 = v^2 + w^2 - 2vw, and since v^2 and w^2 are also doubly even, we may conclude the dot product vw is always even. Thus, any extended Golay code is "self-dual" (i.e., orthogonal to itself over the 2-element field). A counting argument shows we have 4096 = 2^12 codewords in the extended Golay code; these are contained in the subspace it generates, so said subspace must be at least 12 dimensional, making its orthogonal space at most 12 dimensional. Self-duality tells us the latter contains the former, and thus both are equal and exactly 12 dimensional. Our 2^12 codewords therefore comprise the entirety of this subspace, making the Golay code linear.

The relationship between perfect and extended Golay codes allows us to conclude now that perfect Golay codes are also linear.
***

Construction of an extended Golay code from a dodecahedron:

TODO

***

Construction of a cyclic perfect Golay code:

Note that, as long as the automorphism group of the extended Golay code has order divisible by prime 23 (which is a consequence of it being doubly transitive, which it certainly is at it is furthermore 5-transitive, though I don't know how to prove these multiple transitivities yet), it must contain an element of order 23, which acting on 24 elements must be a cycle of length 23 with one additional fixed point. Puncturing the code by dropping this fixed point, we thus obtain a cyclic perfect Golay code.

We can also obtain the cyclic perfect Golay code directly: Any linear cyclic code is given by taking a suitable factor of x^n - 1 (n = 23 in this case) as generator. Factoring this (over the field with two elements), we see that there are precisely two linear cyclic codes of dimension 12 in 23 dimensional space, and they are equivalent under reflection of coordinates. What remains is to prove the minimum distance this property. I don't yet know how to do this but it involves some infamous "square root bound" on quadratic residue codes. TODO

***

Relationship to (11, 5, 2) biplane: TODO

***

Uniqueness of the Golay code (up to permutation of coordinates):

TODO

***

5-transitivity of the Mathieu group:

TODO

***

Discussion of ternary Golay codes:

TODO

(Also related to (11, 5, 2) biplane)

***

Lack of existence of other perfect codes over prime power alphabets:

TODO

***

Proof of uniqueness of Hadamard codes:

TODO