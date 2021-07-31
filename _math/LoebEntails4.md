---
title: "Loeb's Theorem Entails 4"
date: 2021-7-31
---
A curious fact about modal logic is that any normal (in the Kripke sense) modal logic containing Loeb's theorem ($$\Box (\Box A \Rightarrow A) \vdash \Box A$$) as an axiom also contains 4 ($$\Box A \vdash \Box \Box A$$) as an axiom.

Proof:
$$A \vdash \Box(A \wedge \Box A) \Rightarrow A \wedge \Box A$$, fairly straightforwardly.

Thus,

$$\Box A \vdash \Box( \Box(A \wedge \Box A) \Rightarrow A \wedge \Box A)$$. But this in turn, via Loeb's theorem, entails $$\Box(A \wedge \Box A)$$, which of course entails $$\Box \Box A$$.

Thus, $$\Box A \vdash \Box \Box A$$.

****

[In the above, $$\Box$$ and $$\wedge$$ are to be read with tightest possible scope, while $$\Rightarrow$$ is read with loosest possible scope]


****

Note that containing $$\Box (\Box A \Rightarrow A) \vdash \Box A$$ as an axiom is different than containing the inference rule that you can conclude $$ \vdash A$$ from $$\Box A \vdash A$$. The latter (external Loeb's theorem) corresponds to having a well-founded accessibility relation. The former (internal Loeb's theorem) corresponds to being both well-founded and transitive.

Accordingly, we can derive the external Loeb's theorem from the internal Loeb's theorem. Like so: Suppose we have the former in play. Then from $$\Box A \vdash A$$ we derive $$\vdash \Box A \Rightarrow A$$ and thus $$\vdash \Box(\Box A \Rightarrow A)$$. Applying our internal version of Loeb's theorem, we get $$\vdash \Box A$$. But now we can combine this with our starting presumption of $$\Box A \vdash A$$, and conclude $$\vdash A$$, as desired.