---
title: "Fixed Points of Cycled Compositions"
date: 2024-3-29
---
Suppose given 1-cells $$F : C \to D$$ and $$G : D \to C$$ in some 2-category. $$\newcommand{\id}{\mathrm{id}}$$

[^2Cat]: Everything in this post will generalize just as well to working in an arbitrary 2-category rather than specifically $$\mathrm{Cat}$$, but for convenience, I will use the language of "functors" rather than 1-cells and "natural transformations" rather than 2-cells, etc, regardless.

If we now have 2-cells $$\eta : \id_C \to GF$$ and $$\epsilon : FG \to \id_D$$ satisfying the triangle/zig-zag laws, this is an adjunction. In the further case where $$\eta$$ and $$\epsilon$$ are both isomorphisms, this is the definition of an adjoint equivalence (the appropriate notion of equivalence between objects in a 2-category).

As a reminder, the zig-zag laws are the following two commutative diagrams, which are related to each other by reversing all 1- and 2-cells and swapping the roles of $$(C, D)$$, $$(F, G)$$, and $$(\eta, \epsilon)$$, respectively:
<!-- https://q.uiver.app/#q=WzAsNixbMCwxLCJGIl0sWzEsMCwiRkdGIl0sWzIsMSwiRiJdLFszLDEsIkciXSxbNCwwLCJHRkciXSxbNSwxLCJHIl0sWzAsMSwiRiBcXGV0YSJdLFsxLDIsIlxcZXBzaWxvbiBGIl0sWzAsMiwiXFxtYXRocm17aWR9X0YiLDIseyJsZXZlbCI6Miwic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoibm9uZSJ9fX1dLFszLDQsIlxcZXRhIEciXSxbNCw1LCJHIFxcZXBzaWxvbiJdLFszLDUsIlxcbWF0aHJte2lkfV9HIiwyLHsibGV2ZWwiOjIsInN0eWxlIjp7ImhlYWQiOnsibmFtZSI6Im5vbmUifX19XV0= -->
<iframe class="quiver-embed" src="https://q.uiver.app/#q=WzAsNixbMCwxLCJGIl0sWzEsMCwiRkdGIl0sWzIsMSwiRiJdLFszLDEsIkciXSxbNCwwLCJHRkciXSxbNSwxLCJHIl0sWzAsMSwiRiBcXGV0YSJdLFsxLDIsIlxcZXBzaWxvbiBGIl0sWzAsMiwiXFxtYXRocm17aWR9X0YiLDIseyJsZXZlbCI6Miwic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoibm9uZSJ9fX1dLFszLDQsIlxcZXRhIEciXSxbNCw1LCJHIFxcZXBzaWxvbiJdLFszLDUsIlxcbWF0aHJte2lkfV9HIiwyLHsibGV2ZWwiOjIsInN0eWxlIjp7ImhlYWQiOnsibmFtZSI6Im5vbmUifX19XV0=&embed" width="828" height="304" style="border-radius: 8px; border: none;"></iframe>

(We might say the first is the zig-zag law for $$F$$ and the second is the zig-zag law for $$G$$.)

But now suppose instead of pointing in opposite directions from and towards identity, $$\eta$$ and $$\epsilon$$ were to point in the same direction. For example, if we had 2-cells $$\beta : GF \to \id_C$$ and $$\epsilon : FG \to \id_D$$.[^Flip2Cells]

[^Flip2Cells]: Just as well, we could consider $$\eta : \id_C \to GF$$ and $$\epsilon : \id_D \to FG$$, but this would be just the same thing with 2-cells reversed.

We could make corresponding "zig-zig" laws for this setup as well, as the following commutative diagrams, where $$\beta$$ takes the place of $$\eta$$ with direction flipped:

<!-- https://q.uiver.app/#q=WzAsNixbMCwxLCJGIl0sWzEsMCwiRkdGIl0sWzIsMSwiRiJdLFszLDEsIkciXSxbNCwwLCJHRkciXSxbNSwxLCJHIl0sWzEsMCwiRiBcXGJldGEiLDJdLFsxLDIsIlxcZXBzaWxvbiBGIl0sWzAsMiwiXFxtYXRocm17aWR9X0YiLDIseyJsZXZlbCI6Miwic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoibm9uZSJ9fX1dLFs0LDMsIlxcYmV0YSBHIiwyXSxbNCw1LCJHIFxcZXBzaWxvbiJdLFszLDUsIlxcbWF0aHJte2lkfV9HIiwyLHsibGV2ZWwiOjIsInN0eWxlIjp7ImhlYWQiOnsibmFtZSI6Im5vbmUifX19XV0= -->
<iframe class="quiver-embed" src="https://q.uiver.app/#q=WzAsNixbMCwxLCJGIl0sWzEsMCwiRkdGIl0sWzIsMSwiRiJdLFszLDEsIkciXSxbNCwwLCJHRkciXSxbNSwxLCJHIl0sWzEsMCwiRiBcXGJldGEiLDJdLFsxLDIsIlxcZXBzaWxvbiBGIl0sWzAsMiwiXFxtYXRocm17aWR9X0YiLDIseyJsZXZlbCI6Miwic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoibm9uZSJ9fX1dLFs0LDMsIlxcYmV0YSBHIiwyXSxbNCw1LCJHIFxcZXBzaWxvbiJdLFszLDUsIlxcbWF0aHJte2lkfV9HIiwyLHsibGV2ZWwiOjIsInN0eWxlIjp7ImhlYWQiOnsibmFtZSI6Im5vbmUifX19XV0=&embed" width="828" height="304" style="border-radius: 8px; border: none;"></iframe>

(We might say the first is the zig-zig law for $$F$$ and the second is the zig-zig law for $$G$$.)

In the case where $$\eta$$ and $$\beta$$ are inverses, the zig-zig law for $$X$$ and zig-zag law for $$X$$ are equivalent conditions (where $$X$$ may be either $$F$$ or $$G$$).

Note also that any of these zig-zag or zig-zig laws has the property that if any one of the top arrows is an isomorphism, so is the other. (For the zig-zag laws, the top arrows are inverses, while for the zig-zig laws, they are equal). Call this "the isomorphism-to-isomorphism property".

Let us now presume for convenience of language that we are working specifically in the 2-category $$\mathrm{Cat}$$, so $$C$$ and $$D$$ are actual categories. (Everything we say will extend suitably to arbitrary 2-categories via the Yoneda lemma.) We presume the existence of $$\epsilon$$ and one of either $$\eta$$ satisfying both zig-zag laws, or $$\beta$$ satisfying both zig-zig laws.

Let $$c$$ be any object in $$C$$ such that $$X_c$$ is an isomorphism (where $$X$$ is either $$\eta$$ or $$\beta$$ depending on which we presume to exist in the first place). By the isomorphism-to-isomorphism property, we then have that $$\epsilon_{F(c)$$ is also an isomorphism. Thus, defining $$C'$$ as the inverter of $$X$$ and $$D'$$ as the inverter of $$\epsilon$$ (i.e., these are the full subcategories restricted to objects on which the indicated natural transformations are invertible), we find that $$F$$ acts also as a functor from $$C'$$ to $$D'$$.

Conversely, by the same isomorpism-to-isomorphism property in the same way, $$G$$ acts also as a functor from $$D'$$ to $$C'$$. Furthermore, $$\epsilon$$ and $$\eta$$ or $$\beta$$ continue to act on $$F$$ and $$G$$ when these are understood as going between $$C'$$ and $$D'$$, and continue to satisfy the zig-zag or zig-zig laws. But in this new context, $$\epsilon$$ and $$\eta$$ or $$\beta$$ will both be invertible. Thus, $$F$$, $$G$$, $$\epsilon$$, and $$\eta$$ or $$\beta$$ act as an adjoint equivalence between $$C'$$ and $$D'$$.

This is well known and familiar in the $$\eta$$ case; restricting an adjunction to inverters of its unit and co-unit yields an adjoint equivalence. But it is interesting to see that it works in the $$\beta$$ case as well, where we do not start with an adjunction as such.

A particular application of this which is of interest is like so: Consider some functors $$f$$ and $$g$$ in opposite direction. Let $$C$$ be the category of $$gf$$-algebras and let $$D$$ be the category of $$fg$$-algebras. The action of $$f$$ acts as a functor $$F : C \to D$$, and similarly $$g$$ acts as a functor $$G : D \to C$$. There are canonical maps $$\beta : GF \to \id_C$$ and, dually, $$\epsilon : FG \to \id_D$$, and these satisfy the zig-zig identities \[TODO: Explain this out more\]. Thus, restricting to $$C'$$ and $$D'$$ as the invertible $$gf$$- or $$fg-$$ algebras, respectively (i.e., the categories of fixed points of $$gf$$ and $$fg$$), we find that the actions of $$f$$ and $$g$$ on these, along with $$\beta$$ and $$\epsilon$$, comprise an adjoint equivalence.

In the particular case where the original $$f$$ and $$g$$ go between discrete sets, this is the familiar fact that $$f$$ and $$g$$ act as inverse bijections between the fixed points of $$gf$$ and of $$fg$$.

The whole purpose of this post was to show how this familiar fact extends to the case where $$f$$ and $$g$$ are functors rather than mere functions, and does so by an argument which can be unified with the familiar fact that adjunctions restrict to equivalences on fixed points of their units and co-units.

----
Footnotes: