---
title:  "Donvolution"
date: 2019-11-26
---
Let's consider the general problem of determining the volume $$v(K)$$ of the region where $$\sum f_i(x_i) < K$$; that is, of determining $$\int_{\sum f_i(x_i) < K} \prod dx_i$$. Let us define new variables $$y_i = f_i(x_i)$$; the problem is now expressed as $$\int_{\sum y_i < K} \prod d g_i(y_i)$$, where $$g_i$$ is the inverse of $$f_i$$. In other words, the derivative of $$v$$ is the convolution of the derivatives of the $$g_i$$. Let us refer to this sort of relationship by saying $$v$$ is the "donvolution" of the $$g_i$$.

For convenience, we may also suppose that all the $$g_i$$ take input zero to output zero, and in general act on only nonnegative inputs and outputs, and thus so does $$v$$.

Note that as convolution is commutative, associative, and linear in each argument, so is donvolution.

Let us now consider the specific case where $$g_i(x) = x^{p_i}$$. Our goal, then, is to understand donvolution of power functions.

Note also that convolving a function with the constantly $$1$$ function (restricted to nonnegative inputs) is as good as integrating it from a starting point of $$0$$; this means donvolving a function with the 1th power function, i.e. the identity function, is as good as integrating it (from a starting point of $$0$$).

[TODO: Rewrite the following. Note how the general observation that x^n donvolved with x^m is some scalar times x^(n + m) allows us to derive SOME function n! such that x^n/n! donvolved with x^m/m! = x^(n + m)!/(n + m)!, unique up to multiplication by an exponential function, since we can calculate this function's second multiplicative differential and its value at 0. It's clear that 0! = 1, and the power rule of integration tells us that n!/[(n - 1)! 1!] = n; more generally, we find the asymptotics that (N + x)!/N! ~ (kN)^x, for some base of exponentiation k such that k^1 = 1!. Since we have the degree of freedom to change exponential factors, we can set k to 1 (including in the sense that its fractional powers are all 1), and now the factorial is uniquely defined, and matches the factorial we would get from https://howsridharthinks.wordpress.com/2019/11/19/difference-equations-infinite-sums-generalized-factorial-zeta-functions-etc/ .]

Thus, the $$n$$-fold donvolution of $$x$$ with itself is the result of integrating the constantly 1 function n times, x^n/n! [that this is the n-fold integral of the constantly 1 function corresponds to the basic power rule that x^n integrates to x^(n + 1)/(n + 1)]. Which means x^n/n! donvolved with x^m/m! must be x^(n + m)/(n! m!). And more generally, the donvolution of various x^{p_i}/p_i! will be x^{\sum p_i}/(\sum p_i)!.

Which, put another way, tells us that donvolution of various x^{p_i} will be x^{\sum p_i} divided by the multinomial coefficient (\sum p_i)!/(\prod (p_i!)). This gives us our v(x), completing our desired result.