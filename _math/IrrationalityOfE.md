---
layout: post
title:  "The Irrationality of e"
date: 2020-1-21
---
This is actually quite easy to show.

Let’s look at $$e^{-1} = \frac{1}{0!} - \frac{1}{1!} + \frac{1}{2!} - \frac{1}{3!} + \ldots$$. As an alternating series whose terms’ magnitudes keep diminishing (from the second term onward), its limiting value lies strictly inbetween any two consecutive partial sums.

But each term’s denominator divides the next, and thus any partial sum ending at or before a given term can be expressed as some rational value with the same denominator as that term. In particular, the partial sum up through and including $$\frac{1}{k!}$$, and the partial sum up till but excluding $$\frac{1}{k!}$$, can both be written as fractions with denominator $$k!$$.

But their numerators will differ by one, and our limiting value must fall strictly between these. Therefore, our limiting value can’t be written with denominator $$k!$$ (for *any* $$k$$). But every possible denominator divides *some* $$k!$$, so this means our limiting value can’t be written as a rational with ANY denominator!

This means $$e^{-1}$$ is irrational. And therefore so is its reciprocal, $$e$$.

In the same way, for any eventually increasing sequence of positive integers with the property that each value divides the next, and the property that the sequence is eventually divisible by any value you like, the alternating sum of its reciprocals defines an irrational value. (Furthermore, we can just as well think of these values as the partial products of any sequence of positive integers eventually greater than 1 with the property that, for each prime, there are infinitely many multiples of that prime in the sequence. In the given case, this sequence is the simple $$1, 2, 3, 4, \ldots$$, which is then transformed into the factorials, and then into the alternating sum of the reciprocal factorials, but many other such possibilities are available, to which the exact same irrationality proof reasoning applies.)