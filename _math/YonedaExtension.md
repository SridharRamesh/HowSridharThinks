---
title: "Yoneda Extension"
date: 2022-7-26
---
Why is the Yoneda embedding the free cocompletion?

Recall that every ordinary functor $$\newcommand{\Set}{\mathrm{Set}} \newcommand{\Hom}{\mathrm{Hom}} f : A \to B$$ has a right adjoint qua profunctor, where a profunctor from $$B$$ to $$A$$ is an ordinary functor from $$B$$ to $$\Set^{A^{op}}$$, with suitable composition rules. (It has also has a left adjoint qua "indfunctor", where by an indfunctor from $$B$$ to $$A$$, I mean an ordinary functor from $$B$$ to $$(\Set^A)^{op}$$.)

Thus, if we have an ordinary functor $$f : A \to B$$, it has a right adjoint $$g : B \to \Set^{A^{op}}$$. We could think of this $$g$$ as a profunctor into $$A$$, but also as an ordinary functor into $$\Set^{A^{op}}$$. Thus, when thinking of $$g$$ as an ordinary functor, it in turn has a left adjoint indfunctor $$h: \Set^{A^{op}} \to (\Set^B)^{op}$$. As a left adjoint, this $$h$$ preserves all colimits.

Furthermore, let us show that $$h(y(-)) = Y(f(-))$$ where $$y : A \to \Set^{A^{op}}$$ and $$Y : B \to (\Set^B)^{op}$$ are the appropriate Yoneda embeddings: Given $$h$$'s definition as left adjoint to $$g$$, we must show that $$\Hom(Y(f(-)), Y(b)) = \Hom(y(-), g(b))$$, for $$b$$ in $$B$$. By the definition of $$g$$ as right adjoint profunctor to $$f$$, the right hand side is $$\Hom(f(-), b)$$, which is also the left hand side by the Yoneda embedding lemma, completing the proof. (TODO: Fill in more details about this kind of reasoning about profunctors and indfunctors as adjoints.)

Note that $$Y$$ preserves any colimits that exist in $$B$$. Furthermore, by [the co-Yoneda lemma](./TotalLimits.html), every object of $$\Set^{A^{op}}$$ is a small colimit of objects in the range of $$y$$. Recalling that $$h$$ preserves colimits, we can thus conclude that $$h$$ applied to an arbitrary presheaf is given as a small colimit of $$h$$ applied to presheaves of the form $$y(-)$$, which is a small colimit of values of the form $$Y(f(-))$$.

If $$B$$ has all small colimits, this then turns into $$Y$$ applied to a small colimit of values of the form $$f(-)$$. Thus, the range of $$h$$ is included in the range of $$Y$$. We can reinterpret the codomain of $$h$$ therefore as the full subcategory $$B$$ of $$(\Set^B)^{op}$$. As small colimits in $$B$$ are inherited from those in $$(\Set^B)^{op}$$, our $$h$$ continues to preserve small colimits under this reinterpretation.

Thus, when $$B$$ has all small colimits, we are able to find an $$h : \Set^{A^{op}} \to B$$ such that $$h(y(-)) = f(-)$$ and such that $$h$$ preserves all small colimits. Such an $$h$$ is unique, as well, since every object in its domain is a small colimit of objects of the form $$y(-)$$, on which its action is prescribed.

Thus, composition with the Yoneda embedding $$y(-)$$ gives us a 1:1 correspondence between arbitrary functors $$: A \to B$$ and small colimit preserving functors $$: \Set^{A^{op}} \to B$$. This exhibits the Yoneda embedding as the free cocompletion.

***

We can also consider free cocompletions which preserve specified colimits. This should just be the full subcategory of $$\Set^{A^{op}}$$ respecting those colimits, with this following quickly from the above result.

That is, let us write Psh(A) for the category of all small presheaves on A (that is, small colimits of representables), and Rsh(A) for the full subcategory of Psh(A) restricted to those presheaves respecting our special colimits (note that every representable presheaf is in Rsh(A), since these will always respect any existing colimits in A). Note that these special colimits thus remain colimits in Rsh(A), essentially by the defining condition on Rsh(A), as interpreted through the Yoneda lemma.

Now let B be some other category with all small colimits.

We already know that composition with the Yoneda embedding induces a 1:1 correspondence between small colimit preserving functors from Psh(A) to B, and arbitrary functors from A to B. For every arbitrary functor $$f: A \to B$$, there is one and only one small colimit preserving $$F : Psh(A) \to B$$ such that F following Yoneda = f.

There is also at most one small colimit preserving $$\phi : Rsh(A) \to B$$ such that $$\phi$$ following Yoneda = f, for the exact same reason (every object in Rsh(A) is a small colimit of representable presheaves). 

We want to show, when f preserves the special colimits, there is a unique choice of such $$\phi$$ that preserves the special colimits as well, and then we are done in establishing Rsh(A) as the free cocompletion of A preserving the chosen colimits. We've already established uniqueness of $$\phi$$ so we just need existence. The obvious choice is to take $$\phi$$ to be F restricted to Rsh(A).

We then just need to show that F preserves the special colimits, so long as f does. But of course it does, because F takes the special colimits to the same thing f does, because F and f agree on diagrams in A.