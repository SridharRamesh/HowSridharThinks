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

***

For square root bound on quadratic codes, see https://sci-hub.ru/https://www.jstor.org/stable/2100534 ("A New Form of the Square Root Bound" by Assmus et al)

***

Let p be a prime which is -1 mod 8. We consider the two polynomials in mod 2 land given by Q(x) = sum of x^j over all j which are (nonzero) quadratic residues mod p and N(x) = sum of x^j over all j which are (nonzero) quadratic nonresidues mod p \[where representatives of mod p classes are taken in the range \[0, p)\]. Clearly, 1 + N(x) + Q(x) = 1 + x + x^2 + ... + x^(p - 1) = (x^p - 1)/(x - 1). \[Let's use the name U(x) for (x^p - 1)/(x - 1) \]. Also, since p is -1 mod 4, we have that N(x) and Q(x) are each other's reverses, in the sense that N(x) = Q(1/x) x^p.

Finally, observe that Q(x) N(x) mod (x^p - 1) = sum of x^(q + n) where q is a quadratic residue and n is a quadratic nonresidue. The constant term here is (p - 1)/2 = -1 mod 4 = 1 mod 2, as this is the number of quadratic residues paired with their negation, a quadratic nonresidue. For each other term x^d with nonzero d, we get a coefficient corresponding to the number of ways to express d as a sum of a quadratic residue and nonresidue (equivalently, a difference between quadratic residues) in mod p land. This is 1/4 the number of expressions of d as a^2 - b^2 = (a + b)(a - b) for nonzero a, b. Since p is odd, this is just 1/4 * (the number of expressions of d as a product of two values, minus the 2 ways to express d as either a square \[if d is a residue\] or a negated square \[if d is a nonresidue\]). Since mod p land is a field, the number of expressions of d as a product of two values is p - 1. So we get 1/4 * (p - 1 - 2) = (p - 3)/4 = (-4 mod 8)/4 = -1 mod 2 = 1 mod 2. Thus, Q(x) N(x) mod x^p - 1 = U(x).

Consider also A(x) = product of (x - z^j) over all quadratic residues j mod p, where z is a primitive p-th root of unity, and B(x) = product of (x - z^j) over all quadratic nonresidues j mod p, using the same z. Replacing z with z^t either preserves A and B or swaps them, depending on whether t is a quadratic residue or nonresidue. Clearly, A(x) B(x) = U(x) as well (straight up), and A(x) and B(x) are each other's reverses in the sense that A(x) = B(1/x) x^((p - 1)/2).

What's more, {GCD(Q(x), x^p - 1), GCD(N(x), x^p - 1)} = {A, B}. Why is this? To compute gcds with x^p - 1, it suffices to see which p-th roots of unity are roots of a polynomial. 1 is clearly not a root of Q nor of N \[as both send 1 to (p - 1)/2, which is -1 mod 4, and thus nonzero in mod 2 land\]. Recalling that Q(x) = Q(x^quadratic residue) and similarly for N, while Q(x) + N(x) = -1 for roots of U(x), and finally observing that x^p - 1 doesn't divide Q or N \[as their degrees are too small\], we have that the roots of GCD(Q(x), x^p - 1) must comprise one equivalence class of powers of nontrivial p-th roots of unity and the roots of GCD(N(x), x^p - 1) must comprise the other, where two p-th roots of unity are considered equivalent if either is given by raising the other to a quadratic residue.

Thus, the cyclic codes (of cycle length p) generated by A or B are the same as those generated by Q or N \[in one way of pairing these up or the other\], and also, either of these codes is just obtained from the other by reversing all codewords. Since A and B have degree (p - 1)/2 and divide x^p - 1, we see that the dimension of the space of codewords is in any case (p + 1)/2.

The polynomials in mod x^p - 1 land which are multiples of these generators are closed under multiplication by powers of x (obviously) and also are closed under sending any P(x) to P(x^quadratic residue) (as A or B are themselves fixed by this action). Thus, the automorphism group of any of these codes (in the sense of permutations of coordinates that take codewords to codewords) includes the cyclic group and includes multiplication by any quadratic residue.

Under the cyclic group, any set of size 2 is equivalent to {0, x} for some nonzero x, and also just as well equivalent to {0, -x}; thus, between the two of these, it is equivalent to something of the form {0, x} for a quadratic residue x. And any two sets of the for {0, x} for a quadratic residue x are equivalent under multiplication by some quadratic residue. Thus, the automorphism group of this code is 2-transitive.

In particular, this means that for any set of size 2, there is the same number of Hamming weight w codewords containing it as for any other set of size 2. Call this number λ. \[λ of course depends on w, but we will take w as fixed for the following discussion for a second\]. We will come back to this in a second, let us generalize our discussion now.

Suppose given a t-(v,k,λ) design (https://en.wikipedia.org/wiki/Block_design#General_balanced_designs_(t-designs)), in the sense of a collection of subsets (of a universe of size v), called "blocks", with each block having size k, such that any subset of size t (presumed ≤ k) is contained in precisely λ blocks. (It follows that for each t' < t, the number of blocks containing a subset of size t' is fixed as well, but this is not important for us). Let B be some block, and let x0, x1, x2, …, be the number of blocks of which intersect B in precisely 0, 1, 2, …, locations.

The number of ways to choose a set of size s and a block whose intersection with B contains s, is given by the sum of x_j * (j choose s), of course. But when s ≤ t, it is also given by (k choose s) * (v - s choose t - s) * λ / (k - s choose t - s).

In particular, since (j choose 2) ≥ (j choose 1)/2 for j ≠ 1, if x1 = 0, then we have that the value of this for s = 2 is at least half the value of this for s = 1. This means (k choose 2) (v - 2 choose t - 2) / (k - 2 choose t - 2)

\[To be continued...\]

****

By the Hamming code of length 7, we mean the the classic Hamming code of length 7. By the reverse, we mean the same thing with all codewords reversed (so their first bit becomes their last and their last bit becomes their first). By extending either of these, we mean adding a new parity bit at the end so that all codewords have even Hamming weight. (Note that the extended reverse Hamming code is NOT the reverse of the extended Hamming code, because we don't reverse the parity bit at the end. Our interest is in the extended Hamming code and the extended reverse Hamming code.)

Note that the intersection of the Hamming code and the reverse Hamming code contains just the all zero and all ones words (this follows by the observation that these are cyclic codes generated by the two coprime reverse factors of (x^7 - 1)/(x - 1) in mod 2 land). Thus, the same holds for their extended counterparts.

Note that the minimum Hamming weight of a nonzero codeword in an original Hamming code is 3 (by the property of correcting single errors) and thus in an extended Hamming code is 4.

Consider triples (A, B, C) where each value is of length 8, any two values sum to something in the extended Hamming code, and all three values sum to something in the extended reverse Hamming code.

We will show that every nonzero such (A, B, C) has weight at least 8.

If, e.g., A is zero, we must have that B and C are both in the (extended) Hamming code, and B + C is in the intersection of the extended Hamming code and extended reverse Hamming code. Thus, either B and C are equal Hamming codewords or complements. If they are equal and nonzero, they each have weight at least 4, so (A, B, C) has weight at least 8. If they are complements, their combined weight is exactly 8.

Thus, we can restrict our attention to the case where all of A, B, C are nonzero. As they each have even weight, the only way the total weight can be less than 8 is if all have weight 2. Since any two must sum to a value in the Hamming code, each pair must be either disjoint or equal. But if two are equal, then the sum of all three has weight 2. And if all three are disjoint, then the sum of all three has weight 6. Either of these is incompatible with the sum of all three being in the extended reverse Hamming code, contradicting that the sum of all three is in the extended reverse Hamming code.

Thus, we have a linear binary code of codeword length 24 with minimum weight at least 8. Finally, let us observe that the space of codewords is 12 dimensional: It can be alternatively described as the range of the map (a + x, b + x, a + b + x) where a and b come from the extended Hamming code (whose codewords comprise a 4-dimensional space) and x from the extended reverse Hamming code (again 4-dimensional). This map is readily seen to be injective (we can recover a, b, and x as suitable combinations of components of the output), and thus its range is 12 dimensional.

So we have a 12 dimensional subspace of 24-dimensional binary space, with minimum Hamming weight at least 8, and in which each value has even weight. Accordingly, dropping any one bit, we get a 12 dimensional subspace of 23-dimensional binary space, with minimum Hamming weight at least 7. By the standard calculation (23 choose 0) + (23 choose 1) + (23 choose 2) + (23 choose 3) = 2^(23 - 12), we see that this is a perfect code, correcting up to three errors.