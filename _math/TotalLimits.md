---
title: "Total Limits Are Empty Colimits"
date: 2019-11-17
---
Here's a simple fact from order theory: Suppose $$X$$ is a least element of partial order $$C$$. Then $$X$$ is the meet of all of $$C$$. In fact, for any order-preserving function $$F$$, we have that $$F(X)$$ is the meet of all of $$F(C)$$.

In this post, we will strengthen this fact to the most natural corresponding theorem on categories (requiring us to now pay attention to the equalities between morphisms). Furthermore, we'll see how many of the celebrated big-name theorems of category theory (the Adjoint Functor Theorem, the Yoneda lemma) are equivalent to or follow from it.

***

Let $$C$$ be a category, let $$X$$ be an object in $$C$$, and let $$X_C$$ be a cone from $$X$$ to all of $$C$$ (that is, a collection of projections $$X_Y : X \to Y$$ from $$X$$ to each object $$Y$$ in $$C$$, such that for any $$f : Y \to Z$$ in $$C$$, we have the equation $$f \circ X_Y = X_Z$$). Call this a "total cone".

One case where we get total cones is when $$X$$ is an initial object for $$C$$, with the unique maps from $$X$$ to each object of $$C$$ clearly satisfying the cone property. Note that in this case, the self-projection $$X_X$$ is the identity $$1_X$$. And conversely, whenever we have a total cone such that the self-projection is the identity, it arises from an initial object (for the cone conditions then tell us $$f = f \circ 1_X = f \circ X_X = X_Z$$ for any $$f : X \to Z$$, granting uniqueness of the maps out of $$X$$).

Another case where we get a total cone is if $$X$$ is the limit of all of $$C$$ [the "total limit"]. Indeed, to say that some object is the limit of some diagram is to use that apex object merely as shorthand for some implicit cone from the apex object to the diagram, with this cone being the actual structure of the limit. (Specifically, to say a cone is a limit cone is to say that every other cone into the same diagram is equal to the limit cone composed with a unique corresponding map into its apex object; in other words, a limit cone for some diagram means a terminal object within the category of all cones for that diagram.)

Note that if $$X_C$$ is any collection of maps from $$X$$ into the objects of $$C$$ (satisfying the cone conditions or not), and we consider any functor $$F$$ out of $$C$$ [i.e., diagram of shape $$C$$ in an arbitrary category], and any arbitrary other cone into the diagram $$F$$, this other cone will factor through $$F(X_C)$$. Specifically, this other cone will equal its projection into $$X$$ followed by $$F(X_C)$$, by its cone conditions applied to the fact that $$X_C$$ lives within $$C$$.

So when $$X_C$$ is a total cone, the only possible obstacle to $$F(X_C)$$ being a limit cone is uniqueness of factorizations; i.e., joint monicity of $$F(X_C)$$.

We will now show that the following are equivalent for a total cone $$X_C$$:

1. $$X_C$$ is jointly monic. [I.e., $$X_C$$ is a total limit cone]
2. The self-projection in $$X_C$$ is identity. [I.e., $$X$$ is an initial object of $$C$$]
3. $$F(X_C)$$ is jointly monic for every functor $$F$$. [I.e., $$X_C$$ is a total absolute limit cone]

Proof:
1 implies 2: By our observation above, the self-projection in $$X_C$$ followed by $$X_C$$ must yield $$X_C$$ again. This is the same as the identity followed by $$X_C$$, and thus when $$X_C$$ is jointly monic, we must have that the self-projection is identity.

2 implies 3: If the self-projection in $$X_C$$ is identity, so is its image under $$F$$, and therefore this image is a fortiori monic, and therefore $$F(X_C)$$ is a fortiori jointly monic.

*[This is part of a more general theory fully characterizing absolute limits; see [nLab](https://ncatlab.org/nlab/show/absolute+colimit#particular_absolute_colimits_2)]*

3 implies 1: Obvious (1 is the special case of 3 where $$F$$ is the identity).

We have now established that total limits are the same as initial objects, and are automatically absolute limits (i.e., limits preserved by all functors).

The two most famous named theorems in category theory, the Adjoint Functor Theorem and the (Co)Yoneda lemma/theorem, are special cases of the above, as follows.

## Representability Theorem

Consider the question of when some functor $$F : C \to \mathrm{Set}$$ is representable. To any such functor, we can associate a category of elements $$\mathrm{el}(F)$$, which is the comma category $$(\mathrm{pt} / F)$$ where $$\mathrm{pt}$$ is the one-point set. We say $$F$$ is representable when $$\mathrm{el}(F)$$ has an initial object.

Observe that $$\mathrm{el}(F)$$ comes with a forgetful functor $$: \mathrm{el}(F) \to C$$, which creates any limits preserved by $$F$$ [meaning that any diagram in $$\mathrm{el}(F)$$ whose corresponding diagram in $$C$$ has a limit preserved by $$F$$, already has a limit in $$\mathrm{el}(F)$$ with this limit preserved by the forgetful functor]. Thus, in this context we can apply our equivalence of initial objects and total limits, the latter automatically absolute, to conclude that $$\mathrm{el}(F)$$ has an initial object (i.e., $$F$$ is representable) if and only if the entire diagram of shape $$\mathrm{el}(F)$$ within $$C$$ has a limit preserved by $$F$$. And in this case, this limit is then automatically preserved by all functors (and $$F$$ automatically preserves all limits).

[One simple story that falls out of this is that if $$C$$ has and $$F$$ preserves all limits, then $$F$$ is representable. However, for "size" reasons, it is rare formally, and impossible in classical set theory, for a non-preorder category to actually have ALL limits.]

This limit criterion for representability of functors deserves a nice name of its own, though I do not know one. It nonetheless comes up often [TODO: see Set as free cocompletion; see the representability of various functors on presheaf categories thus establishing them as elementary toposes; see the HSP theorem]. For now, we shall push on.

Conversely, our original result about total limits being empty colimits is a special case of this now-generalized Representability Theorem, considering that the constantly 1 functor on C is automatically limit-preserving and its category of elements is just C itself, so that this functor is representable (i.e., C will have an initial object) just to the extent that the necessary limit (of all of C) exists in C. [And in this case, the limit is automatically absolute as well]

## Yoneda Lemma

The above "Representability Theorem" gives a criterion for when a functor is representable; what follows by applying this to the explicitly representable functor $$\mathrm{Hom}(x, -)$$ is the Yoneda lemma. [TODO: Write this out]. Another way to look at this is as so:

Note that, in any category $$C$$ with any object $$X$$, the under category $$X / C$$ (whose objects are maps out of $$X$$, and whose morphisms are commutative triangles between these) has an initial object; namely, the identity map on $$X$$.

By the above, this initial object is a total absolute limit; in particular, it will be preserved under the codomain projection functor $$: X/C \to C$$, and then further preserved under any further functor $$F$$ out of $$C$$. So for any functor $$F : C \to D$$, we have that $$F(X)$$ is the limit of $$F$$ applied to the codomain projection of $$X/C$$. To choose an "element" of $$F(X)$$ is to choose for every value in $$\mathrm{Hom}_C(X, -)$$ a corresponding value in $$F(-)$$, in a way which commutes with all the actions of $$C$$. This is the content of the Yoneda lemma, which is usually stated for $$F$$ with codomain $$Set$$. [TODO: Expand on this]. This can also be viewed as telling us how to construct free models of unary algebraic theories, as term models. (See ["The Yoneda Lemma"]({{site.baseurl}}{% link _math/Yoneda.md %})). In type-theory/dependent types language, we can say "$$F(X) = \Pi_{X \to Y} F(Y)$$".

Dually, we also have that $$F(X)$$ is the colimit of $$F$$ applied to all maps into $$X$$. This is the content of the co-Yoneda lemma, again generally stated for $$F$$ with codomain $$Set$$, which can also be viewed as telling us that the Yoneda embedding is the free cocompletion for a category. [TODO: Expand on this]. This can also be viewed as telling us how every model has a canonical full presentation in terms of generators and relations. (Again, see ["The Yoneda Lemma"]({{site.baseurl}}{% link _math/Yoneda.md %})). In type-theory/dependent types language, we can say "$$F(X) = \Sigma_{Y \to X} F(Y)$$".

TODO: Can we recover that total limits are initial objects from the Yoneda lemma?

## Adjoint Functor Theorem

Another corollary of our Representability Theorem is the Adjoint Functor Theorem. A functor of the form $$\mathrm{Hom}(x, G-)$$ preserves any limits $$G$$ preserves, and so by the Representability Theorem criterion, this functor is representable (which is to say, $$G$$ has a left adjoint at $$x$$) if and only if the diagram corresponding to the forgetful functor out of its category of elements has a limit which $$G$$ preserves.

This is the adjoint functor theorem, though it is usually stated a little differently. If the indicated limits exist and are preserved for each possible $$x$$, then $$G$$ has a fully defined left adjoint. In this case, we can conclude that $$G$$ in fact preserves ALL limits that exist.

[Thus, again, the simple but formally rare story is when all limits do in fact exist, in which case we can say that $$G$$ has a left adjoint iff it preserves all limits]

Note that an instance of all this is a criterion for when a category has any particular colimit, given in terms of the existence of a corresponding "large" limit. [Again, the simple but formally rare story is that a category with all limits also has all colimits]

Conversely, our original result about total limits being empty colimits is a special case of this now-generalized Adjoint Functor Theorem, considering that a functor from C to C^0 = 1 always preserves all limits, so it will have a left adjoint (i.e., C will have an initial object) just to the extent that the necessary limit (of all of C) exists in C. [TODO: Pay more attention to deriving the absoluteness of the limit here as well]

***

Incidentally, a certain addendum which is sometimes useful is that we can obtain an initial object by taking any weakly initial object (one with existence, but not necessarily uniqueness, of morphsims into every other object; that is, any object which becomes initial in the preorder reflction of the category), and equalizing all its endomorphisms. [TODO: Why is this? I believe this is because the inclusion functor of the equalizer morphism $$E \to W$$, where $$W$$ is weakly initial and $$E$$ is the common equalizer of on a weakly initial object is automatically an [initial functor](https://ncatlab.org/nlab/show/final+functor), and thus has the same limit as the identity functor. But I need to work this out. I can then perhaps apply this to bottoms-up Knaster-Tarski, by doing such a coequalizer of all endomorphisms at every stage.]

***

[TODO: Note that all the results in this post are essentially equivalent; they each entail each other relatively quickly. The trickiest thing is showing that the Yoneda lemma implies the rest (actually, this might not be true; the Yoneda lemma might be the one result weaker than the others); TODO: write this up. Even though this is perhaps how we are trained to think as category theorists, with Yoneda as fundamental, I now think the most fundamental ideas here (whatever that amounts to) are the first two in this post: total limits are initial objects, and the "Representability Theorem". Note that the observation that total limits are initial objects is easy to make direct sense of for internal categories in various senses, including 0-cells internal to higher categories, as it makes no reference to Set as such, while the Yoneda lemma can be more difficult to directly interpret (though not impossible to indirectly interpret via slice nonsense) in such contexts because Set is generally not itself an internal category in Set.]

[TODO: Something with the observation that a natural transformation from F to G : C -> Set is an element of the limit of the composite el(f) --forgetful--> C --G--> Set. Perhaps this generalizes in some way beyond Set, probably through Yoneda-izing other categories.]