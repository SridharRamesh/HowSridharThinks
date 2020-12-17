---
title: "Brownian"
date: 2020-12-15
---
Extracted from Facebook comments:

Chenyu Zhao
Fun problem of the day: develop an algorithm that samples a Brownian Bridge (a Wiener process s.t. W(0) =W(1) = 0, i.e. the ends are fixed).

Richard Starfield
Simulate regular Wiener process. Subtract linear function to fix ends. Profit?

Chenyu Zhao
lol does that actually work? it makes sense, but it doesn't sit well with me... I'll need to think about it some more... my intuition is lacking...

Sridhar Ramesh
Think of it this way, Chenyu: A discrete Wiener process with N equally sized steps amounts to the same thing as N iid normal variables (representing the amount by which the function increases over each step). The corresponding Brownian bridge distribution is given by conditionalizing on the sum of these variables being zero. Richard’s claim is that this yields the same distribution as simply subtracting from each variable the average of all the variables.
Why is that? Well, another way of looking at N iid normal variables is as a single N-dimensional normal variable, which is to say, as a random vector V with a probability density function given by an exponential function of its squared magnitude. Subtracting from each coordinate the average of all coordinates is the same as projecting onto the space S where the coordinates sum to zero. Richard’s claim is that the conditional distribution of V given that it lies in S is the same as the distribution of V’s projection onto S; in fact, V's projection onto S is independent of the component of V perpendicular to S, by the property noted of the probability density function: as an exponential function of the squared magnitude of V, it is proportional to the product of its values on the components of V parallel and perpendicular to S.
Does that make any sense? I’ve phrased it in discrete terms, but nothing essential changes in the reasoning as applied to a continuous context (also, you can always think of a continuous Wiener process as a "tower" of discrete Wiener processes giving values on dyadic inputs, with values on other inputs determined from these by continuity).

TODO: Ito's lemma, all that stochastic calculus stuff