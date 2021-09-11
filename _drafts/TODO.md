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
Functional equation for the zeta function (see comment "(1) Titchmarsh points out in his book on the zeta function (section 2.3) that if you blindly apply the Poisson summation formula to the function 𝑓(𝑠)=|𝑥|𝑠, you get the functional equation of the Riemann zeta function immediately, and gives a reference to a paper of Mordell where this procedure is justified." at https://mathoverflow.net/questions/58004/how-does-one-motivate-the-analytic-continuation-of-the-riemann-zeta-function. See also "EASY PROOFS OF RIEMANN’S FUNCTIONAL EQUATION…" by Knopp and Robins, and "AN ALTERNATIVE FORM OF THE FUNCTIONAL EQUATION FOR RIEMANN′S ZETA FUNCTION" by Ossicini. See also https://mathoverflow.net/questions/381935/deriving-the-functional-equation-for-zetas-from-summing-the-powers-of-the-z/381942#381942). See also https://terrytao.wordpress.com/2008/07/27/tates-proof-of-the-functional-equation/.
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
Resultants/discriminants/Bezout matrix/etc
Symmetric polynomials, the theorem that any symmetric polynomial of r1, ..., rn is a polynomial in the coefficients of (x + r1)...(x + rn). [Note that, replacing "polynomial" by "rational function" here, this follows directly from Galois theory. Can we get the polynomial version from that in some way, or is there some relation? I suppose we can get the polynomial version fully from the rational version, because we can readily check whether a rational function is actually polynomial by investigating whether it has poles. But I also suppose the fundamental theorem of symmetric polynomials is probably part of the proof of the fundamental theorem of Galois theory in the first place. Anyway, see https://math.stackexchange.com/questions/192565/a-proof-of-the-fundamental-theorem-of-symmetric-polynomials which answers some of this.]
Galois theory, with reference to the abstract model-theoretic perspective from the Alice Medvedev et al paper, plus the points that are more field specific having to do with dimension. Building off the Discrete Fourier Transform and Galois theory post we already did.
Counterfeit coin balance problems (see http://math.uni.lodz.pl/~andkom/Marcel/Kule-en.pdf)
Proof that the covering group of SO(n) is Z_2, for n >= 3. Simpler: The covering group of the space of planar rotations around one axis, plus identity, is Z_2. The covering space can be taken as an angle between 0 and 360, plus a direction for the axis, with angles of 0 or 360 not needing to specify a direction. This is a double cover, and it's homotopic (indeed, homeomorphic) to the (n - 1)-sphere, which is simply connected for n >= 2. [But also discuss Euler rotation theorem]

Talk about the Legendre transform from a tropical Fourier-transform perspective (keeping in mind how the ordinary properties fail a little and one must use one sup- Legendre transform followed by one min- Legendre transform, to recover the original function, with this working just in case the original function is convex). Discuss duality in linear programming from this perspective.

Partial derivative notation is awful because it doesn't make clear what's allowed to vary with what, but people lie about how the chain rule in terms of fractions "breaks" in this situation. Re-use the writing already done on MathOverflow/Quora for this situation.

Find the monotonicity/least fixed point probability thing I'd once written about on SDMB.

Discuss Karatsuba, Toom-n, and FFT based convolution/multiplication algorithms

***
To think about:

Sum of [2^(-2n) * zeta(2n)]/n from n = 1 to infinity is log(pi/2) [this is an expansion of the Wallis product using the Mercator series at the logarithmic level], but pi itself is closely related to zeta(2), zeta(4), etc. So there's some special fact here.

Sum of [2^(-2n) * zeta(2n)]/(2n) is mean of log(1/2!) and log(-1/2!)? Well, this is just the Wallis product observation.

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

---

Write up the general theory of Clifford algebras, including the observation that the Clifford algebra can be taken as isomorphic as a vector space to the exterior algebra (non-obvious! See Chevalley's linear identification at http://people.math.harvard.edu/~shlomo/docs/lie_algebras.pdf). Relate this to quaternions, write about spinors. Note the observation that spinors are closed under addition for quaternions because of dimension concerns (two planes in 3d space must intersect in a line).