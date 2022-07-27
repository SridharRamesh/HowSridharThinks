---
title: "Associativity and the Associahedron"
date: 2022-7-16
---
The mean number of points in cycles of length 𝑘 over all permutations of an 𝑛-element set is 1. Why is this?

Well, a point in a cycle of length k is specified by first choosing k many elements to be in the cycle (in one of (n choose k) many ways), then putting an ordering on these elements (in one of k! many ways), with the first point in the ordering taken as our point of interest. Fleshing out the full permutation now comprises simply permuting the remaining points among themselves (in one of (n − k)! many ways).

So there are (n choose k) * k! * (n - k)! many points in cycles of length k overall, among all permutations of n elements. Finally, we divide by the number of permutations of n elements (which is n!) to compute the mean value, rather than the total value.

This gives us (n choose k) * k! * (n - k)! / n!. And this is clearly 1.

[Based off of my comment at https://golem.ph.utexas.edu/category/2019/12/random_permutations_part_6.html#c056936]