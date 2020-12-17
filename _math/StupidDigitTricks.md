---
title: "Stupid Digit Tricks"
date: 2020-08-25
---
One thing people are often amused by is observations like that $$\frac{1}{998001}$$ comes out to .000 001 002 003 004…, with every three digit string appearing in order except for 998, and then repeating back from 999 to 000.

Why does this happen? Well, .000 001 002 003… times (10^3 - 1) equals 000.001 001 001 001…, since each 3 digit piece of .000 001 002 003… is 001 higher than the 3 digit piece before it.

Multiplying by (10^3 - 1) again, we get 001 exactly, since each 3 digit piece of 000.001 001 001… exactly equals the piece before it.

So .000 001 002 003… = $$\frac{1}{\left(10^3 - 1\right)^2} = \frac{1}{998001}$$.

998 is missing because we can't actually make each piece 001 higher forever while staying 3 digits. By doing 997 999 000…, we get 002 followed by -999 for the differences here, which after "borrowing" is as good as 001 001, and then everything starts over and works the same way as before.

***

[TODO: Discuss the less stupid digit trick of why cyclic decimals correspond to rationals. Do the tricks like Fibonacci sequences and the like too.]