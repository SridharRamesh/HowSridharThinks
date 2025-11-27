---
title: "GL Fixed Points"
date: 2025-11-25
---
A curious fact about GL modal logic is that, even without any special arrangements, we have guarded fixed points:

For any formula $$\phi(p, X)$$ (where $$p$$ is a propositional variable and $$X$$ represents any number of other propositional variables taken as fixed parameters), such that $$p$$ is guarded in the sense that each occurrence of $$p$$ is under the scope of a modal operator $$\Box$$, there is a formula $$f(X)$$ such that $$f(X)$$ is provably equivalent to $$\phi(f(X), X)$$. In particular, in the case where $$X$$ is empty, we have that for any $$\phi(p)$$, there is a sentence $$f$$ such that $$f$$ is provably equivalent to $$\phi(f)$$.

How is this proven? Like so: 

First of all, there is the observation that GL has the uniform Craig interpolation property: That is, from any formula $$\phi(p, X)$$, there is another formula $$\exists p . \phi(p, X)$$, satisfying the adjunction: $$\exists p . \phi(p, X) \vdash \psi(X)$$ if and only if $$\phi(p, X) \vdash \psi(X)$$, for any formula $$\psi(X)$$ whose free variables are entirely among those in $$X$$. \[I believe there also will be the mirror image property that there is a formula $$\forall p . \phi(p, X)$$ such that $$\psi(X) \vdash \forall p . \phi(p, X)$$ iff $$\psi(p, X) \vdash \phi(X)$$. At any rate, the existential version of this was proven by Shavrukov; originally in their dissertation, which is hard to find a copy of, but also explained in their paper ["Subalgebras of diagonalizable algebras of theories containing arithmetic"](https://eudml.org/doc/219353).\].

From this, we obviously get Craig interpolation: For any two formulas $$\phi(X, Y)$$ and $$\psi(Y, Z)$$ in the indicated sets of free variables, if we have the entailment $$\phi(X, Y) \vdash \psi(Y, Z)$$ over the union of their free variables, then we also have an interpolant formula $$F(Y)$$ in just the common free variables, such that $$\phi(X, Y) \vdash F(Y)$$ and $$F(Y) \vdash \psi(Y, Z)$$. Here, $$F$$ can be taken to be $$\exists X . \phi(X, Y)$$ (meaning the repeated quantification over each propositional variable in $$X$$), or just as well, $$\forall Z . \psi(Y, Z)$$ if this is available.

From Craig interpolation, we get Beth definability: If $$\phi(p, X) \wedge \phi(q, X) \vdash p \leftrightarrow q$$, then there is a particular formula $$F(X)$$ such that $$\phi(p, X) \vdash p \leftrightarrow F(X)$$. For our presumption tells us that $$\phi(p, X) \wedge p \vdash \phi(q, x) \rightarrow q$$, and thus by Craig interpolation, we have some $$F(X)$$ for which $$\phi(p, X) \wedge p \vdash F(X)$$ and $$F(X) \vdash \phi(q, X) \rightarrow q$$. Substituting $$q$$ for $$p$$ in the latter and combining the two, we have $$\phi(p, X) \vdash p \leftrightarrow F(X)$$ as desired.

Now, observe that for formulas $$\phi(p, X)$$ where $$p$$ is guarded, we have $$\Box(p \leftrightarrow q) \vdash \phi(p, X) \leftrightarrow \phi(q, X)$$.

This tells us fixed points are unique, like so: Suppose $$p \leftrightarrow \phi(p, X)$$ and similarly for $$q$$. Then the previous observation tells us that from $$\Box(p \leftrightarrow q)$$ we can conclude $$p \leftrightarrow q$$. Applying Löb's theorem, we conclude $$\Box (p \leftrightarrow \phi(p, X)) \wedge \Box (q \leftrightarrow \phi(q, X)) \vdash \Box(p \leftrightarrow q)$$. But we also have $$\Box(p \leftrightarrow q) \vdash \phi(p, X) \leftrightarrow \phi(q, X)$$. Thus, $$\Box (p \leftrightarrow \phi(p, X)) \wedge \Box (q \leftrightarrow \phi(q, X)) \vdash \phi(p, X) \leftrightarrow \phi(q, X)$$. Thus, defining $$m(y)$$ as $$y \wedge \Box y$$, and defining $$n(p)$$ as $$m(p \leftrightarrow \phi(p, X))$$ (so that $$n(p)$$ asserts that $$p$$ both actually and provably is a fixed point), we straightforwardly have $$n(p) \wedge n(q) \vdash p \leftrightarrow q$$. \[TODO: Use better notation than $$n(p)$$, to make clear this depends on $$\phi$$ and has $$X$$ as free variables\]
 
So applying Beth definability, there is some $$F(X)$$ such that $$n(p) \vdash p \leftrightarrow F(X)$$. That is, $$F(X)$$ is the only thing that a fixed point of $$\phi$$ can be.

This is enough to conclude that $$F(X)$$ actually is a fixed point of $$\phi$$, using Löb's theorem like so: Note that $$\Box (F(X) \leftrightarrow \phi(F(X, X))) \vdash \phi(F(X), X) \leftrightarrow \phi(\phi(F(X), X), X)$$ and thus $$\Box (F(X) \leftrightarrow \phi(F(X, X))) \wedge n(\phi(F(X), X)) \vdash \phi(F(X), X) \leftrightarrow F(X)$$, and so by Löb's theorem, we can conclude $$\vdash \phi(F(X), X) \leftrightarrow F(X)$$. \[TODO: Check that everything here is correct.\]

Furthermore, this fixed point is unique, because for any $$F_1(X)$$ and $$F_2(X)$$ which each satisfy $$\vdash F(X) \leftrightarrow \phi(F(X), X)$$, we have $$\Box(F_1(X) \leftrightarrow F_2(X)) \vdash F_1(X) \leftrightarrow F_2(X)$$ and thus have by Lôb's theorem $$\vdash F_1(X) \leftrightarrow F_2(X)$$.

****

The above argument is given in Boolos' "The Logic of Provability" as "Third proof of the fixed point theorem", except with Craig's interpolation theorem for GL proven directly rather than from uniform Craig's interpolation theorem.

****

TODO: Rewrite the above to use $\Box$ throughout rather than $n$, and then invoke the reflection rule at the end.

Rewrite the above to use coalgebra-to-algebra hylomorphisms where appropriate, instead of just maps between fixed points.