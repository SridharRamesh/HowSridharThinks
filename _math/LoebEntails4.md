---
title: "Löb's Theorem Entails 4"
date: 2021-7-31
---
A curious fact about modal logic is that any normal (in the Kripke sense) modal logic containing Löb's theorem ($$\Box (\Box A \Rightarrow A) \vdash \Box A$$) as an axiom also contains 4 ($$\Box A \vdash \Box \Box A$$) as an axiom.

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

Conversely, given external Löb's theorem and 4, we can derive internal Löb's theorem, like so: Suppose given $$\Box(\Box (Box A \Rightarrow A) \Rightarrow \Box A)$$ and $$\Box (\Box A \Rightarrow A)$$ as hypotheses. Using 4 on the latter, we obtain $$\Box \Box (\Box A \Rightarrow A)$$. Combining this with the former, we get $$\Box \Box A$$. Combining this with $$\Box (\Box A \Rightarrow A)$$ again, we get $$\Box A$$. Thus, discharging our hypotheses, we are able to derive $$\Box(\Box (Box A \Rightarrow A) \Rightarrow \Box A) \vdash  (\Box (\Box A \Rightarrow A)) \Rightarrow \Box A$$. Applying external Löb's theorem to this, we obtain $$\vdash (\Box (\Box A \Rightarrow A)) \Rightarrow \Box A$$, or just as well, $$\Box (\Box A \Right arrow A) \vdash \Box A$$, which is internal Löb's theorem.