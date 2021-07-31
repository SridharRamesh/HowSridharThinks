---
title: "Loeb's Theorem Entails 4"
date: 2021-7-31
---
A curious fact about modal logic is that any normal (in the Kripke sense) modal logic containing Loeb's theorem ($$\Box (\Box A \Rightarrow A) \vdash \Box A$$) as an axiom also contains 4 ($$\Box A \vdash \Box \Box A$$) as an axiom.

Proof:
$$A \vdash (\Box(A \wedge \BoxA) \Rightarrow A \wedge \BoxA)$$, fairly straightforwardly.

Thus,

$$\Box A \vdash \Box( (\Box(A \wedge \BoxA) \Rightarrow A \wedge \BoxA))$$. But this in turn, via Loeb's theorem, entails $$\Box(A \wedge \Box A)$$, which of course entails $$\Box \Box A$$.

Thus, $$\Box A \vdash \Box \Box A$$.