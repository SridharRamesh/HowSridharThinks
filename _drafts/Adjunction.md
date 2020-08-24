---
layout: post
title:  "Adjunctions"
date: 2020-4-26
---
[TODO: Equivalence between hom-set definition of adjunctions (including as abstracted to any 2-category) and unit/counit/triangle identities definition. Automatic equivalence also to the “backwards” definition: An adjunction between functors F : C → D (the left adjoint) and G : D → C (the right adjoint) is a bijective correspondence between Hom(xG, y) and Hom(x, yF), natural in x and y. Automatic because the unit/counit/triangle identities definition is symmetric. Note also the concept of an adjunction up to adjunction, aka “quasi-adjunction”, where we don’t get a bijection but only an adjoint correspondence in a higher category. Note how adjunction are like half-inverses, just enough to make the proof of unique inverses still go through.]

***

Backwards adjunction:

Define an adjunction F ⊣ R in a 2-category C as two 0-cells X and Y, two 1-cells F : X → Y and R : Y → X, two 2-cells η: 1_X → RF and ϵ: FR → 1_Y, and the triangle identities (moving from F to FRF with η then back to F with ϵ is equal to identity on F; moving from R to RFR with η then back to R with ϵ is equal to identity on R).

It is manifest in the very syntax of these data and axioms that reversing all 2-cells in an adjunction yields still an adjunction with "left" and "right" adjoint role swapped. Similarly, reversing all 1-cells in an adjunction yields still an adjunction with "left" and "right" adjoint role swapped.

It's also intuitive and straightforward that F ⊣ R leads to F ∘ -  ⊣ R ∘ -, where in the latter adjunction, the adjoints are not 1-cells between X and Y within the 2-category C, but rather, 1-cells between Hom(A, X) and Hom(A, Y) within the 2-category Cat, for any 0-cell A in C [indeed, we have this structure naturally in A]. This is just the idea of treating each object in C as a category in itself, and a walking category at that, which can be probed by maps into it. (And conversely, by Yoneda lemma, any adjunction between Hom(A, X) and Hom(A, Y) in this sense, natural in A, arises uniquely from an adjunction between X and Y in our original sense.)

Now, by looking at the last paragraph's in C^{op}, meaning C with 1-cells reversed, we get that F^{op} ⊣ R^{op} is equivalent to F^{op} ∘ -  ⊣ R^{op} ∘ -. But F^{op} ⊣ R^{op} is equivalent to R ⊣ F (this is what it means to say reversing 1-cells just swaps the two sides of an adjunction). And F^{op} ∘ -  ⊣ R^{op} ∘ - is equivalent to - ∘ F ⊣ - ∘ R (the composition order swaps when we move from C^{op} back to C, but the adjunction here does no swapping of left and right sides because it is an adjunction in Cat, and we've not swapped 1-cells or 2-cells in Cat, we've just replaced categories like Hom_{C^{op}}(A^{op}, X^{op}) with equivalent categories like Hom_C(X, A).)

So R ⊣ F is equivalent to - ∘ F ⊣ - ∘ R. Or renaming R into L for convenience, we have that L ⊣ F leads to - ∘ F ⊣ - ∘ L. This seems backwards, with the the left adjoint on the right and the right adjoint on the left in the conclusion, but it is indeed true. We can phrase this as a correspondence between Hom(xF, y) and Hom(x, yL).

[TODO: Rename standardized to L and R, or standardized to F and G]