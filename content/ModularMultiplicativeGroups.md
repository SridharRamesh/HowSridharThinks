---
title: "Multiplicative Groups in Modular Arithmetic"
date: 2019-11-28
---
By the Chinese Remainder Theorem, the ring of integers modulo N is the product of the rings of integers modulo p^n, for each prime power p^n in the factorization of N. To study the integers modulo p^n, it is helpful to consider the p-adics.

By Fermat's little theorem and Hensel's lemma, there is for every possible last digit in the p-adic integers, a unique value x with that last digit satisfying x^p = x. If that last digit is 0, then x = 0 of course. The rest of these form a cyclic group of order p - 1 [by the cyclicity of the multiplicative group of a finite field; see https://howsridharthinks.wordpress.com/2019/12/02/field-multiplication-cyclicity/ ].

Every invertible (i.e., indivisible by p) p-adic integer can uniquely be written as one of these (p - 1)-th roots of unity times a p-adic integer whose last digit is 1.

So what is left is to determine the structure of the multiplicative group of p-adic integers whose last digit is 1.

Note that (1 + p^j x)^p = 1 + p^{j + 1}x + (p choose 2)p^{2j} x^2 + a bunch of terms which include at least a p^{3j} factor.

If j \geq 1, then all the elided terms have more factors of p than p^{j + 1}x. If p is odd or j > 1, the same is true of the (p choose 2)p^{2j} x^2 term. Thus, we find that in these cases, the number of 0 digits in a row after the initial (least significant) 1 digit goes up by precisely 1 when we take p-th powers. This establishes that in these cases, the multiplicative group of n digit values with last digit 1 is cyclic, with generator any value which has no 0 digits after the initial 1 digit (since such a value would have order dividing p^{n - 1} but not dividing p^{n - 2}, and thus precisely p^{n - 1}, the order of the entire group).

The remaining case is where p is 2 and j = 1. But we can handle this by observing that, in the 2-adics, every value ending in 1 either ends in 01 or ends in 11, with negation switching between these two. So we can negate as necessary to ensure an ending value of 01 (i.e., j > 1), and then use the fact from before. This tells us the multiplicative group of n digit values with last digit 01 is cyclic, and the multiplicative group of n digit values with last digit 1 is Z_2 times that subgroup.

These cylicity results state that there is an isomorphism between the multiplicative group of values with last digit 1 and the additive group of values with last digit 0 in the integers modulo p^n for odd p (or between the values with last digit 01 and the values with last digit 00, respectively, for p = 2). This isomorphism amounts to logarithm, with exponential as its inverse; we can in fact construct the natural logarithm and natural exponential by power series as well, paying suitable attention to the radius of convergence to get the same results as above.

This completes the description of the multiplicative group of invertible values in the p-adics and thus in the N-adics (and thus also the structure of the corresponding groups mod N for any finite N). The full multiplicative monoid of p-adics is this previous group times the additive monoid of natural numbers (the multiplicative monoid of powers of p), of course. And the full multiplicative group of p-adic rationals uses "integers" in place of the previous line's "natural numbers".

[TODO: Rewrite stuff on values = 1 mod p in terms of the observation that they come with a valuation under multiplication which has the right properties to match a valuation under addition, and the construction of the logarithm automatically from this]

[TODO: LaTeXify the above]