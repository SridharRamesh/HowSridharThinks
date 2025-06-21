---
title: "Hamming Codes Over Arbitrary Fields"
date: 2025-06-21
---
Hamming codes are well-understood in binary, but here I describe how they generalize to arbitrary fields. (This was apparently first described by Golay in passing in his short article on Golay codes, but I find his description there quite difficult to read.)

Let $$V$$ be some vector space over some field. Define an equivalence relation on the nonzero elements of $$V$$, under which two vectors are equivalent just in case they are each scalar multiples of the other. Let us say a "word" is a finite set of nonzero vectors of $$V$$, no two of which are equivalent. In other, er, words, a "word" is a choice function which assigns to each line through the origin of $$V$$ some vector on that line, and which furthermore has finite support (only finitely many lines are assigned nonzero values).

When $$V$$ is finite-dimensional over a finite field, these words can be thought of as strings of a particular finite length (the number of equivalence classes of nonzero vectors) over an alphabet of a particular finite size (the number of vectors on a line; i.e., the size of the field).

The finite support condition ensures that the sum of a word is a well-defined vector. We will say a word is a "codeword" if this sums to zero.

The Hamming distance between two words is the number of lines on which they make different choices.

Our observation is that for every word, there is a unique codeword at Hamming distance ≤ 1 from it. In other words, our choice of codewords makes a perfect single-error correcting code.

This is like so: Given any word, look at its sum. If this is zero, this is already a codeword (and changing any single of its "letters" will change its sum to no longer zero, thus no longer a codeword). If this is nonzero, then we must subtract this nonzero value from the sum to get to a codeword. Well, there is a unique line on which this nonzero value lives, and so that tells us precisely which "letter" we must change and by how much.

----

This gives us a method of constructing perfect single error correcting codes over an alphabet of size $$q = \abs{V}$$, using encoded messages of length $$\ell = \frac{q^n - 1}{q - 1} = 1 + q + q^2 + \ldots + q^{n - 1}$$, for any prime power $$q > 1$$ and choice of $$n$$.

(Note that such message lengths are the only possibilities available for a perfect single error correcting code over an alphabet of prime power size, as we need $$1 + \ell (q - 1)$$ to divide some power of $$q$$. The prime power condition on $$q$$ then forces $$1 + \ell (q - 1)$$ to itself be a power of $$q$$, from which we get $$\ell = \frac{q^n - 1}{q - 1}$$.)

No instance is known of a perfect single error correcting code over different parameters (i.e., over an alphabet whose size is not a prime power), though no proof is known that this is impossible, either (as I understand it).

The above describes a "linear" scheme for constructing perfect single error correcting codes. Note that there also exist non-linear codes with the same alphabet size and message length parameters in some instances (TODO: describe an example). There seems some ambiguity in whether such non-linear codes with these parameters are also called "Hamming codes".

----

Does the above extend to anything interesting over the "field with one element"? The appearance of the [q-analog](https://en.wikipedia.org/wiki/Q-analog) $$\ell = \[n\]_q$$ is suggestive, but I'm not sure what to say along these lines.