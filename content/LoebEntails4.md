---
title: "Löb's Theorem Entails 4"
date: 2021-7-31
---
A curious fact about modal logic is that any normal (in the Kripke sense) modal logic containing Löb's theorem ($$\Box (\Box A \Rightarrow A) \vdash \Box A$$) as an axiom also contains 4 ($$\Box A \vdash \Box \Box A$$) as an axiom. <!-- more -->

Proof:
$$A \vdash \Box(A \wedge \Box A) \Rightarrow A \wedge \Box A$$, fairly straightforwardly.

Thus,

$$\Box A \vdash \Box( \Box(A \wedge \Box A) \Rightarrow A \wedge \Box A)$$. But this in turn, via Löb's theorem, entails $$\Box(A \wedge \Box A)$$, which of course entails $$\Box \Box A$$.

Thus, $$\Box A \vdash \Box \Box A$$.

****

[In the above, $$\Box$$ and $$\wedge$$ are to be read with tightest possible scope, while $$\Rightarrow$$ is read with loosest possible scope]


****

Note that containing $$\Box (\Box A \Rightarrow A) \vdash \Box A$$ as an axiom is different than containing the inference rule that you can conclude $$ \vdash A$$ from $$\Box A \vdash A$$. The latter (external Löb's theorem) corresponds to having a well-founded accessibility relation. The former (internal Löb's theorem) corresponds to being both well-founded and transitive.

Accordingly, we can derive the external Löb's theorem from the internal Löb's theorem. Like so: Suppose we have internal Löb's theorem in play. Then from $$\Box A \vdash A$$ we derive $$\vdash \Box A \Rightarrow A$$ and thus $$\vdash \Box(\Box A \Rightarrow A)$$. Applying our internal version of Löb's theorem, we get $$\vdash \Box A$$. But now we can combine this with our starting presumption of $$\Box A \vdash A$$, and conclude $$\vdash A$$, as desired.

Conversely, given external Löb's theorem and 4, we can derive internal Löb's theorem, like so: Suppose given $$\Box(\Box (\Box A \Rightarrow A) \Rightarrow \Box A)$$ and $$\Box (\Box A \Rightarrow A)$$ as hypotheses. Using 4 on the latter, we obtain $$\Box \Box (\Box A \Rightarrow A)$$. Combining this with the former, we get $$\Box \Box A$$. Combining this with $$\Box (\Box A \Rightarrow A)$$ again, we get $$\Box A$$. Thus, discharging our hypotheses, we are able to derive $$\Box(\Box (\Box A \Rightarrow A) \Rightarrow \Box A) \vdash  (\Box (\Box A \Rightarrow A)) \Rightarrow \Box A$$. Applying external Löb's theorem to this, we obtain $$\vdash (\Box (\Box A \Rightarrow A)) \Rightarrow \Box A$$, or just as well, $$\Box (\Box A \Rightarrow A) \vdash \Box A$$, which is internal Löb's theorem.

****

It is worth noting that our argument deriving 4 from Löb's theorem doesn't actually depend on $$\Box$$ distributing over conjunctions, and thus holds in even greater generality. For example, it tells us this more general fact: Let $$f$$ be an operator on a meet-semilattice such that, whenever any $$x$$ and $$y$$ are such that $$x \wedge f(y) \leq y$$, then furthermore $$f(x) \leq f(y)$$. Then $$f \leq f^2$$.

Or even more generally: Let $$f$$ and $$g$$ be endofunctors of a meet-semilattice such that whenever $$x \wedge f(y) \leq y$$, then furthermore $$g(x) \leq g(y)$$. Then $$g \leq gf$$. Because we can consider $$y = x \wedge f(x)$$, for which we have $$x \wedge f(y) \leq y$$, to derive $$g(x) \leq g(y) = g(x \wedge f(x)) \leq g(f(x))$$.[^Functoriality]

Even more generally: Let $$B(-, =) : C^{\mathrm{op}} \times C \rightarrow \Omega$$ be a bifunctor on some monoidal closed category with terminal object $$1$$, let $$C'$$ be a full sub-monoidal-category of $$C$$, let $$\Box : C' \to C'$$ be an oplax monoidal endofunctor on $$C'$$, and suppose $$B(\Box p \rightarrow (p \otimes 1), p)$$ is inhabited for all $$p$$ in $$C'$$. Then $$B(p, 1 \otimes \Box^n p)$$ is inhabited for all $$n \in \mathbb{N}$$ and all $$p$$ in $$C'$$. This is by noting that, setting $$q = \bigotimes_{i = 0}^{n} \Box^i p$$, we have $$B(p, \Box q \rightarrow (q \otimes 1))$$ using the oplax monoidal property of $$q$$. We also have $$B(q, 1 \otimes \Box^n p)$$ trivially. Composing these with our Löb-like presumption at $$q$$ in the middle, we get $$B(p, 1 \otimes \Box^n p)$$ as desired. Note that we can take $$C = \mathrm{Psh}(C')$$ (preserving any monoidal or cartesian structure already in $$C'$$) and lift to $$C$$ any bifunctor on $$C'$$. Note also that, for cartesian monoidal structure, all functors are automatically oplax. Finally, with $$C = \mathrm{Psh}(C)$$, we can Yoneda-ize the first argument of $$B$$ and rewrite our Löb condition without exponentials as that, whenever $$C'(x \otimes \Box p, p \otimes 1)$$ is inhabited, then $$B(x, p)$$. After rephrasing in this way, we no longer even need $$B$$ to be functorial in its first argument.

\[TODO: Clean up having rephrased back and forth between $$f$$ and $$\Box$$ here for no reason.\]

[^Functoriality]: We can even drop the precondition that $$g$$ is functorial/order-preserving, as this is recoverable anyway from the Löb condition.

Curiously, there is another approach we can take in the context of a complete lattice. The above initial argument just depends on the existence of some value t such that $$x \wedge f(t) \leq t \leq f(x)$$. The particular $$t$$ used was $$x \wedge f(x)$$, but any other choice will suffice. Note that, for the endofunctor $$t \mapsto x \wedge f(t)$$, any coalgebra will be $$\leq f(x)$$, so it would also suffice to have any pair of an algebra $$\leq$$ a coalgebra. In particular, it would suffice for this endofunctor to have a fixed point, and the Knaster-Tarski theorem assures us (in complete lattices) that it does. (However, I do not see that this approach could be made to cover general meet-semilattices.)