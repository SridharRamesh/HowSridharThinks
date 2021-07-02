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
Functional equation for the zeta function (see comment "(1) Titchmarsh points out in his book on the zeta function (section 2.3) that if you blindly apply the Poisson summation formula to the function 𝑓(𝑠)=|𝑥|𝑠, you get the functional equation of the Riemann zeta function immediately, and gives a reference to a paper of Mordell where this procedure is justified." at https://mathoverflow.net/questions/58004/how-does-one-motivate-the-analytic-continuation-of-the-riemann-zeta-function. See also "EASY PROOFS OF RIEMANN’S FUNCTIONAL EQUATION…" by Knopp and Robins, and "AN ALTERNATIVE FORM OF THE FUNCTIONAL EQUATION FOR RIEMANN′S ZETA FUNCTION" by Ossicini)
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
A general post on things students are made to tackle by induction that are seen more clearly in other ways
A general post on things people tackle by +1 reasoning instead of general monoid reasoning, that are seen more clearly in the full picture (including, e.g., the Mobius inversion chromatic polynomial thing)
Monty Hall/two boys/etc probability puzzle ambiguity language rant

Talk about the Legendre transform from a tropical Fourier-transform perspective (keeping in mind how the ordinary properties fail a little and one must use one sup- Legendre transform followed by one min- Legendre transform, to recover the original function, with this working just in case the original function is convex). Discuss duality in linear programming from this perspective.

Partial derivative notation is awful because it doesn't make clear what's allowed to vary with what, but people lie about how the chain rule in terms of fractions "breaks" in this situation. Re-use the writing already done on MathOverflow/Quora for this situation.

Find the monotonicity/least fixed point probability thing I'd once written about on SDMB.

Discuss Karatsuba, Toom-n, and FFT based convolution/multiplication algorithms

***
To think about:

Sum of [2^(-2n) * zeta(2n)]/n from n = 1 to infinity is log(pi/2) [this is an expansion of the Wallis product using the Mercator series at the logarithmic level], but pi itself is closely related to zeta(2), zeta(4), etc. So there's some special fact here.

Sum of [2^(-2n) * zeta(2n)]/(2n) is mean of log(1/2!) and log(-1/2!)? Well, this is just the Wallis product observation.

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

----

Generalized factorial

Generalized Riemann zeta?

Generalized power sum formula?

Set up Wallis product recurrence, but have to go over:
Volume is unaffected by shearing
Volume of tapering figures in n-dimensional space (pyramids)
Area relates to surface area on a ball
Finally, surface of any ball is... (alas, this goes over the same ground as a 3b1b video)
Talk about Lambert equal area projection and map projection in general, curvature, etc?
Having gotten the recurrence, we relate to ! and find (1/2)! = sqrt(pi)/2.

Philosophical discussion of how pi comes up in many different contexts.

Do donvolution approach instead as well.

----
Blind Bartender Problem

Links to game theory in general; tic-tac-toe, Hex, Nim

----

If a monad has a left adjoint, then this left adjoint is a comonad with the same Kleisli category and same inclusion of the pure category into the Kleisli category. If a monad has a right adjoint, then this right adjoint is a comonad with the same Eilenberg-Moore category and the same forgetful functor out of the Eilenberg-Moore category.

Write up the general theory of Clifford algebras, including the observation that the Clifford algebra can be taken as isomorphic as a vector space to the exterior algebra (non-obvious! See Chevalley's linear identification at http://people.math.harvard.edu/~shlomo/docs/lie_algebras.pdf). Relate this to quaternions, write about spinors. Note the observation that spinors are closed under addition for quaternions because of dimension concerns (two planes in 3d space must intersect in a line).