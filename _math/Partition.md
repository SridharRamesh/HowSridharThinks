---
title:  "Partitions"
date: 2020-7-20
---
There’s lots to say about partitions. I’ll just write some things scattershot, most of which are due to Euler or from thinking about transposing Ferrers/Young diagrams:

The number of partitions of N with distinct parts matches the number of partitions of N with odd parts:

Proof: Let us focus just on those parts whose odd component, in the sense of prime factorization, is M. Thus, parts M, 2M, 4M, 8M, etc. There’s precisely one way to combine distinct such values to obtain any particular positive integer multiple of M [given by binary representation of the positive integer]. This is the same as the precisely one way to repeat M itself many times to get the same sum [unary representation]. Applying this over all odd M, this establishes the theorem.

Put another way, consider these two inverse moves: taking a partition with two repeated parts X + X and combining it into a partition of the same value with one even part 2X, or vice versa. Each of these moves defines a system readily seen to be confluent (in the sense of [this post]({{ site.baseurl }}{% link _math/Confluence.md %})) and for which termination is clear by how the number of parts changes monotonically. So we get two inverse functions between the terminal partitions: that is, between the partitions with no repeated parts and the partitions with no even parts. (This is the same as what was described above in terms of binary and unary representation, just presented in different terms.)