---
title: "Thoughts on what calculus is about"
date: 2022-7-25
---
Calculus is about certain kinds of weighted sums.

An easy kind of weighted sum against a function f is to extract the value f(x) for a specific x. This is like integrating against a Dirac delta.

We might also consider the integral of f along some interval (or across some region more generally/higher dimensionally). This is like integrating against a rectangle function. (Thus, the weights here are infinitesimal in comparison to the Dirac delta case). Note that a Dirac delta is like the limiting case of a rectangle function of height inversely proportional to its width, as the width goes to zero around a point. 

We might also consider the derivative of f at some point. This is like integrating against the derivative of a Dirac delta. Note that f'(x) is like (f(a) - f(b))/(a - b) in the limit as a, b -> x. Thus, we have two weights of equal magnitude but opposite sign right up against each other, and that magnitude is 1/(a - b) times that of a Dirac delta; thus, the weights here are infinite in comparison to the Dirac delta case.

Any linear operator from a space of functions to a space of outputs can be thought of as a kind of weighted sum of the function's values \[in the same way that any linear operator can be thought of as represented by a matrix\]; a kind of general "distribution" (and we can consider ones even more general than Schwarz space distributions or tempered distributions or whatever). Actually, what we really mean here is a natural family of linear operators, going from -^domain (where these are arbitrary set functions) to weight tensor -, natural in linear maps on -. This naturality ensures that our weights are scalar like, not arbitrary linear operators on the values of our functions (so conjugation, for example, is not counted as a weighted sum acting on single complex numbers. Though we could always imagine applying some linear operation to the result of the weighted sum anyway, like an evaluation map of pairings of vectors and matrices. So maybe this kind of distinction isn't worth worrying about. Perhaps it would be better to think of weights as arbitrary linear maps.).

In particular, even things like "The limit of the function at x" (which can be distinct from the value of the function at x) can be thought of as certain kinds of weighted sums, albeit we do not normally think of these this way. A kind of weighted sum where all the weight is right up against but not actually at x.

When the linear functional sends positive functions to positive outputs and sends the constantly 1 function to 1, it is a kind of average. Thus, in particular, limits are a kind of average, in addition to extracting values (Dirac delta; average at a point) or taking the average across an interval in the usual sense.

The fundamental theorems of calculus, in the punctile-to-extensive and extensive-to-punctile forms from https://sridharramesh.github.io/HowSridharThinks/math/FundamentalTheoremsCalculus.html, are the observation that, in suitable contexts, average across a region is an average of Dirac delta functions at points, and conversely, a Dirac delta at a point is a limit of averages across regions. (This is sure convergence of distributions)

Thus, the fundamental concepts of calculus are these:

Totals (can be weighted)
Averages (can be weighted). (Normally, we think of totals and averages as just rescaled versions of each other, but the difference between the two can be an infinite factor. E.g., summing an infinite series versus taking its average value.)
Limits, but these are just a special case of weighted averages, as said above.
Rates of change. We can think of these as given by limits of secant functions, but we can also think of these as primitive concepts in themselves, acting on tangent vectors.

All of these are certain kinds of weighted sums.

Some kinds of distributions have behavior that is in some sense thoroughly well-described just by their induced measure (their behavior on indicator functions for regions). But things like the derivative of the Dirac delta do not have this kind of behavior (they act best on differentiable, etc, smooth functions). \[Similarly for extracting limits or taking asymptotic density averages? Similarly for "average value around point", as opposed to the Dirac delta itself\]. This is perhaps related to the idea of absolute continuity vs. singularity of distributions/measures?