---
title:  "Boolean Algebras"
date: 2020-12-11
---
TODO: To be written out into a full thing on how Boolean algebra is the finitary theory of finite sets, of 2, etc. Limit vs. product theory perspective on Boolean algebra, etc.

But for now, I wanted to record this observation about Boolean rings: Why does adding the condition x^2 = x to the definition a ring suffice to make the theory equal the theory of Boolean aglebras (i.e., the finitary theory of {0, 1})? Well, clearly, what we need is something like that, for any polynomial P, if P(0) = P(1) = 0, then P vanishes, on top of the definition that 1 + 1 = 0.

Note that x^2 = x causes all the coefficients of nonzero degree in P to equivalently bundle up as the coefficient of x. So every polynomial might as well be of degree 1, and then having the two independent roots 0 and 1 makes it vanish. We need also that x^2 = x entails 1 + 1 = 0, but this is clear enough (from (1 + 1)^2 = 1 + 1).

A consequence of this (though it can be written out more explicitly) is that x^2 = x also entails commutativity, surprisingly enough.