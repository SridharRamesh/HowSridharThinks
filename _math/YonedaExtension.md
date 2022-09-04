---
title: "Yoneda Extension"
date: 2022-7-26
---
Why is the Yoneda embedding the free cocompletion?

Let $$\newcommand{\Set}{\mathrm{Set}} \newcommand{\Hom}{\mathrm{Hom}} \newcommand{\Psh}{\mathrm{Psh}} \newcommand{\Rsh}{\mathrm{Rsh}} A$$ and $$B$$ be arbitrary categories, with $$y : A \to \Set^{A^{op}}$$ and $$Y : B \to (\Set^B)^{op}$$ as the Yoneda embeddings of the indicated type. By the Yoneda embedding lemma, these can be thought of as inclusions of full subcategories. Note that $$y$$ preserves any limits which exist in $$A$$, while $$Y$$ preserves any colimits which exist in $$B$$.

Recall that every functor $$f : A \to B$$ is the left $$y$$-relative adjoint of a profunctor $$g : B \to \Set^{A^{op}}$$. Specifically, if we define $$g(b)(a) = \Hom_B(f(a), b)$$, then we have a correspondence $$\Hom_B(f(a), b) = \Hom_{\Set^{A^{op}}}(y(a), g(b))$$ by the Yoneda lemma. Note that such $$g$$ preserves all limits, as would be expected from its right adjoint nature.

Dually, every functor $$g : B \to A$$ is the right $$Y$$-relative adjoint of an "indfunctor" $$h : A \to (\Set^B)^{op}$$. Specifically, if we define $$h(a)(b) = \Hom_A(a, g(b))$$, then we have a correspondence $$\Hom_A(a, g(b)) = \Hom_{(\Set^B)^{op}}(h(a), Y(b))$$ by the Yoneda lemma. Note that such $$h$$ preserves all colimits, as would be expected from its left adjoint nature.

In this last paragraph, the category $$A$$ is arbitrary, so we can just as well replace $$A$$ throughout it by $$\Set^{A^{op}}$$.

Thus, let arbitrary $$f : A \to B$$ be given, define $$g : B \to \Set^{A^{op}}$$ as above so as to make $$f$$ the left $$y$$-relative adjoint of $$g$$, and define $$h : \Set^{A^{op}} \to (\Set^B)^{op}$$ as above so as to make $$g$$ the right $$Y$$-relative adjoint of $$h$$.

Now let us show that $$h \circ y = Y \circ f$$. That is, we will show that $$h(y(a))(b) = Y(f(a))(b)$$ for $$a \in A, b \in B$$. By definition, $$h(y(a))(b)$$ is $$\Hom_{\Set^{A^{op}}}(y(a), g(b))$$, which by the Yoneda lemma is $$g(b)(a)$$, which by definition is $$\Hom_B(f(a), b)$$, which is the definition of $$Y(f(a))(b)$$.

Let us now write $$\Psh(A)$$ for the full subcategory of $$\Set^{A^{op}}$$ which is generated from $$y(A)$$ by small colimits. (Note that, by [the co-Yoneda lemma](./TotalLimits.html), we will have that $$\Psh(A)$$ is all of $$\Set^{A^{op}}$$ when $$A$$ is itself small). We can now observe that $$h$$ applied to an arbitrary object in $$\Psh(A)$$ (that is, $$h$$ applied to an arbitrary colimit of a small diagram in the range of $$y : A \to \Psh(A)$$) is a colimit of a small diagram in the range of $$h \circ y$$, which by the previous paragraph is a small colimit of a diagram in the range of $$Y \circ f$$.

Let us now presume that $$B$$ has all small colimits. Recalling that $$Y$$ preserves any colimits that exist in $$B$$, this last diagram turns into $$Y$$ applied to a colimit of a small diagram in the range of $$f$$. Thus, the range of $$h$$ acting on domain $$\Psh(A)$$ is included in the range of $$Y$$.

We can thus now reinterpret $$h$$ as having domain $$\Psh(A)$$ and codomain $$B$$. As small colimits in $$B$$ match those in $$(\Set^B)^{op}$$ (which is just to say, $$Y$$ preserves small colimits), while small colimits in $$\Psh(A)$$ are inherited from $$\Set^{A^{op}}$$, our $$h : \Psh(A) \to B$$ continues to preserve small colimits under this reinterpretation.

Thus, when $$B$$ has all small colimits, we are able to find, for arbitrary $$f : A \to B$$, a corresponding $$h : \Psh(A) \to B$$ such that $$h \circ y = f$$ and such that $$h$$ preserves all small colimits. Such an $$h$$ is unique, as well, since every object in its domain is a colimit of a small diagram in the range of $$y$$, on which its action is prescribed.

Thus, composition with the Yoneda embedding $$y : A \to \Psh(A)$$ gives us a 1:1 correspondence between arbitrary functors $$: A \to B$$ and small colimit preserving functors $$: \Psh(A) \to B$$. This exhibits the Yoneda embedding as the free cocompletion.

***

We can also consider free cocompletions which preserve specified colimits. This is just the full subcategory of $$\Psh(A)$$ respecting those colimits, with this following quickly from the above result.

That is, let us write $$\Rsh(A)$$ for the full subcategory of $$\Psh(A)$$ restricted to those presheaves respecting our special colimits (note that every representable presheaf is in $$\Rsh(A)$$, since these will always respect any existing colimits in $$A$$). Note that these special colimits thus remain colimits in $$\Rsh(A)$$, essentially by the defining condition on $$\Rsh(A)$$, as interpreted through the Yoneda lemma.

Let $$y : A \to \Psh(A)$$ be the Yoneda embedding and let $$B$$ be some arbitrary category with all small colimits, as above. We can also think of the codomain of $$y$$ as $$\Rsh(A)$$, as noted above.

We already know that composition with the Yoneda embedding induces a 1:1 correspondence between small colimit preserving functors from $$\Psh(A)$$ to $$B$$, and arbitrary functors from $$A$$ to $$B$$. For every arbitrary functor $$f: A \to B$$, there is one and only one small colimit preserving $$F : \Psh(A) \to B$$ such that $$F \circ y = f$$.

There is also at most one small colimit preserving $$\phi : \Rsh(A) \to B$$ such that $$\phi \circ y = f$$, for the exact same reason (every object in $$\Rsh(A)$$ is a small colimit of representable presheaves). 

We want to show, when $$f$$ preserves the special colimits, there is a unique choice of such $$\phi$$ that preserves the special colimits as well, and then we are done in establishing $$\Rsh(A)$$ as the free cocompletion of $$A$$ preserving the chosen colimits. We've already established uniqueness of $$\phi$$ so we just need existence. The obvious choice is to take $$\phi$$ to be $$F$$ restricted to $$\Rsh(A)$$.

We then just need to show that $$F$$ preserves the special colimits, so long as $$f$$ does. But of course it does, because $$F$$ takes the special colimits to the same thing $$f$$ does, because $$F$$ and $$f$$ agree on diagrams in $$A$$.