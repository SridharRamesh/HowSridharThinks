---
title: "Supply chain stuff to write up"
date: 2021-7-19
---
Supply chain phenomena to write about:

– Economic order quantity
– Newsvendor
(The above two don’t seem to relate to general phenomena but should still be written. EOQ sort of sets up (s, S) policies, I guess. Newsvendor can be immediately solved by the general theory of convex optimization, though it is also nice to make the observation which turns it from a one parameter to a two parameter game and solves it by techniques which do not generalize.)

– Optimal policy is generally a function of inventory position (on hand + on order) alone
– Optimal policy is generally a base stock policy, for linear ordering cost, plus shortage and holding costs which are convex. Including a backwards induction over time.
– Optimal policy is an (s, S) policy, for linear ordering cost + cost to place an order at all. This is the theory of K-convex functions. Including a backwards induction over time.
– The above with stochastic lead times as well.
– Casepack theory (optimal policy is a contiguous range of OTLs; how does this interact with backwards induction over time, with K-convexity, etc?).
– Multi-echelon theory, such as Clark-Scarf for serial systems (or for distribution systems with balance assumption).
– Necessity of backordering assumption for most of the above; what changes when we use a lost sales model?
