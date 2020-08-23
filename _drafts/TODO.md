Thesis stuff (tree-categories)
Cut elimination theorem/sequent calculus
Laplace/Fourier in terms of translations and exponentiations and so on
Prime counting
Different views on (n-)categories, geometric, algebraic, proof systems, etc
When is mod n cyclic, exp and log in p-adics, etc
UFD, PID, etc, in abstract.
Gaussian integer UFD, etc.
Quaternions
Delay differential equations
Heron’s formula
Cayley’s theorem in matrix algebra
Platonic solids and Coxeter groups
Functional equation for the zeta function
Puzzle from work about rotating table and blindly flipping glasses
Borsuk-Ulam etc (and see old MathOverflow post about broken proof)
Jordan decomposition for linear operators and its relationship to partial fraction decomposition and Bezout’s theorem/Chinese Remainder Theorem, three instances of the same fact
General theory of solving all linear recurrences / differential equations (reduce to first-order, construct appropriate matrix, and exponentiate)
Calculating square roots by the Babylonian method/Newton’s method, vs. the mediant approximation to this, and also the relation of all of this to split-complex numbers/Z[sqrt(n)] \(related to solving recurrences efficiently more generally, a la Fibonacci\), Pell’s equation, continued fractions, etc.
Pell’s equation
Our fixed point fact for probability things, from that SDMB post way back when
General stuff on category theory and logic, for beginners
Different ways of looking at and reasoning about monads (from adjunctions, in terms of algebras, in terms of Lawvere theories, etc.)
The equivalence of various definitions of adjunctions, including the “backwards” one.

***
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