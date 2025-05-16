---
title: "Commas and Collages"
date: 2020-1-18
---
Subjects: Commas and Cocommas/Collages, Bifibrations (by which I mean two-sided fibrations, which apparently is not what people usually mean by this, oh well...), the Grothendieck construction, (bi)-indexed categories, perhaps profunctors, etc.

***

A span is a pair of maps with a common domain; dually, a cospan is a pair of maps with a common codomain.

By a lax square, I mean a span and a cospan such that the pair of codomains of the span matches the pair of domains of the cospan, along with a transformation (we are now working in a 2- or higher category) between the two paths from the domain of the span to the codomain of the cospan. [Commutative squares in the usual sense are the special case of this where the transformation is an equivalence]

Given a cospan, we can ask for the universal lax square extending it, in the sense that all other lax squares extending it factor uniquely through this one (via a map between the domains of the spans); this data is called its comma object; it consists of a span and a transformation. We will sometimes, in abuse of language, identify a comma object with just the span data.

[This is sometimes also called a "lax pullback", because of the obvious analogy to pullbacks, but note that there is also a conflicting terminology around what "lax limits" can mean, involving laxness in the cone conditions; I will not use the terminology "lax pullback" here.]

Dually, given a span, we can ask for the universal lax square extending it, in the dual sense to the above, which is called its cocomma object and consists of a cospan and a transformation. We will sometimes, in abuse of language, identify a cocomma object with just the cospan data.

We can think of a lax square as a morphism from a span to a cospan, and thus, presuming their existence, these cocomma and comma operations induce an adjunction between spans and cospans (each of which comprises a category of elements in a straightforward way, with morphisms as factorizations of one (co)span through another).

In fact, it turns out this adjunction is idempotent in Cat [though not in all other 2-categories!], where the equivalent fixed full subcategories of both spans and cospans are the ones corresponding to lax squares which are simultaneously comma and cocomma diagrams (i.e., simultaneously universal in both directions). That is, a comma span is automatically the comma span of its cocomma, and vice versa (these are equivalent statements, they all amount to different ways of saying that the adjunction is idempotent).

[In Cat, this can be seen as follows: it can be shown that whenever we have a cocomma cospan of functors, it satisfies these properties: A) it is jointly essentially surjective on objects, B) both functors individually are embeddings (that is, essentially surjective at every dimension beyond objects), C) Hom(g(x), f(y)) is empty for all x and y, where f is the leg of the cospan that is to be on the domain side and g on the codomain side. And conversely, whenever we have these properties of a cospan of functors, we can observe that it is the cocomma of its comma, by observing an explicit construction of that comma. Thus, each cocomma is the cocomma of its comma.

Alternatively, this can be seen in span land: it can be shown that whenever we have a comma span of functors, it satisfies certain lifting properties. And conversely, whenever we have a span satisfying these lifting properties, we can observe that it is the comma of its cocomma, by observing an explicit construction of that cocomma (in the fashion of the previous paragraph). Thus, each comma is the comma of its cocomma.

See more on this below, in the discussion of fibrations vs codiscrete cofibrations.]

Thus, we have this kind of data which can equivalently be represented as a comma span or a cocomma cospan. This data amounts also to the same thing as an bifunctor A^{op} x B -> Set (where A and B are the intermediate corners of these squares, with A on the domain and B on the codomain side of the transformation); that is, a bi-indexed set.

[TODO: In fact, we can readily define what maps from spans to bi-indexed categories, and maps from bi-indexed categories to cospans, are supposed to be, without the bother of commas and cocommas; that is, we have a "gamut" from spans to bi-indexed categories to cospans. The rest is then observing that we get adjunctions out of all this. (And idempotency in Cat, and the algebraic conditions defining the fixed values of the adjunction in Cat.). TODO: rewrite the above in terms of these bi-indexed categories, aka proarrows (which can then generalize to any context with a proarrow equipment). The key thing is that proarrows are both a reflective subcategory of the spans and a coreflective subcategory of the cospans.]

When represented as a comma span, what we get is what's called a discrete bifibration. The particular case where A or B is trivially the terminal category 1 comes up often, in which case it's just called a discrete fibration or opfibration. This is also called the category of elements, and is a special case of the general "Grothendieck construction" for bifunctors A^{op} x B -> (infinity-)Cat.

This is all a categorified version of how the slice category Set/X represents Set^X (note that in Set, ALL spans are comma spans and thus ALL morphisms are fibrations). A further special case of that is how monomorphisms in Set represent TruthValue-valued indexed Sets; that is, predicates (and jointly monic maps represent relations).

When represented as a cocomma span, what we get is what's called a collage [for the sake of noting How Sridhar Thinks, I often called these "bridges" in my head, before I learnt the word "collage"]; a category bi-indexed by A^{op} x B is represented by making a new category extending A and B, with A and B living in this fully faithfully, the hom categories between A objects and B objects being those given by our bi-indexed category, and the hom categories between B objects and A objects being empty.

Note that the cocomma span requires us to create an n-category with n one level higher than the comma span requires, and without presumption of inverses; the latter prevents us from doing this construction in Set, and the former means that even doing this construction in Poset, we can only represent Poset-indexed truth values as cospans of Posets; we can not represent Poset-indexed Posets as cospans of Posets (but rather, must use a cospan whose codomain is an ordered category).

***

[TODO: Talk about how the Grothendieck construction is also some kind of colimit of (infinity-)Cat-valued diagrams. Is there any analogue of this for the collage construction?]

[TODO: Relate this comma/cocomma correspondence somehow to the correspondence in abelian categories between subobjects of A and quotient objects of A, or more generally, to relations on A, B, C, D, ..., represented either as subobjects or quotient objects of the biproduct (thus, either as limit cones or colimit cocones, or something)]

Generally, what happens is this:

Consider ourselves working with some kind of category of categories (k-tuply monoidal (n, r)-categories for some particular k, n, and r, say).

We can generally take comma objects and cocomma objects still. And comma objects will generally still always be bifibrations; however, our constraints on the kind of category will perhaps impose further immediate constraints now beyond just those of being a bifibration. E.g., discreteness. But we can take all these constraints together and define some constrained bifibration notion appropriate to the context.

E.g., if we are working with sets or just as well inside an ordinary 1-category, the constrained bifibration notion is of jointly monic maps into X and Y which define a relation such that r(x, y), r(x', y), r(x', y') entails r(x, y') [that is, r r^\* r entails r, where r^\* is the converse of r, and binary relations compose in the usual way].

If we then demand that every such constrained bifibration has a cocomma and is the comma of that cocomma (which is a generalization of the condition defining an effective regular category), we have a context where the span-cospan adjunction is indeed idempotent via simultaneous comma-cocomma diagrams, all as above.

***

(This is where the connection to abelian categories comes up, since an abelian category is just an effective regular category enriched over abelian groups. This is the cleanest way to think about the cokernel/kernel condition in abelian groups: the comma/cocomma adjunction exists with jointly monic maps or jointly epic maps being in correspondence. Because everything is invertible when we deal with groups, we can just as well talk about k-tuples of maps and not just pairs, since the co vs. contravariance makes no difference.)

Note that there's an asymmetry in the notion just given, though (as in the fact that the dual of an effective regular category, or even of a pretopos, needn't be effective regular). We had these constrained bifibration conditions on spans through which everything was mediated. Alternatively, instead of mediating this through the straightforward conditions on spans, it could be mediated through the dual conditions on cospans (the constrained cofibration conditions).

(This asymmetry goes away for abelian categories, because the bifibration conditions turn out to be just joint monicity and the co-bifibration conditions are just joint epicity, which is dual. I think?)

This also has some relation to the idea that every internal category of the appropriate sort is actually represented by a quotient object. That is, given an object of objects and an object of morphisms, we can quotient the object of objects to get the appropriate object representing the internal category.

***

[TODO: Something to understand better about the (constrained as need be) two-sided fibration conditions. By virtue of being a comma category [or comma n-category for whatever n] in ANY ambient context, certain algebraic properties automatically are satisfied (call this being a two-sided fibration); conversely, in Cat specifically, any span satisfying these algebraic properties is the comma of its cocomma. This so far is fairly understandable; the comma of its cocomma in Cat is like the free completion into having the properties of a Hom-category of some concrete Cat, and the properties required to be a Hom-category of some concrete Cat are precisely the properties guaranteed by being a comma object in any ambient context, by how (n + 1)-categories are modeled on the properties of the particular concrete (n + 1)-category n-Cat.

It's also the case that cocomma categories in ANY ambient context have the dual algebraic properties [they are cofibrations], since a cocomma internal to context $$K$$ is just a comma internal to context $$K^{\operatorname{op}}$$.

However, what's left unexplained is this: In Cat, any cospan which is a cofibration is the cocomma of its comma. Why is this?! This property is dual to how any span which is a fibration is the comma of its cocomma, but the duality is surprising. [Added later: Is this really what I meant? Or did I only mean that discrete fibrations and codiscrete cofibrations are the (co)commas of their (co)commas? Because that's the true statement in Cat; the commas are the discrete fibrations and the cocommas are the codiscrete cofibrations. This must be what I meant above by "constrained as need be"; that I am talking about fibrations and cofibrations as automatically implicitly constrained by certain dimensionality presumptions.]

Perhaps what it is is that, in Cat, every square where the span is a fibration and the cospan is a cofibration is automatically a comma/cocomma square?

Also, I'm not sure if it's actually true in n-Cat in general that every cofibration is the cocomma of its comma; I just know this is the case for codiscrete cofibrations in Cat. If this isn't true in general, then the mystery lessens. In fact, I think this is the entire answer: a cospan is a cofibration just in case it is a gamut (a category with a functor into \* -> \* -> \*), while it is codiscrete just in case it is a collage (the preimage of the middle * is empty). Discreteness of a span is a red herring that only seems to mirror the relevant codiscreteness condition on cofibrations when we are concerned about low Set-valued bifunctors rather than Cat-valued bifunctors more generally (i.e., a low n coincidence).

In fact, even codiscreteness is a convoluted way of looking at things. The appropriate condition telling us which cospans are collages/cocommas is that we have a functor into the arrow category, whose preimages at the objects are the corners of the cospan.]

[TODO: Actually, for n-categories, I'm not sure the comma construction is the right way to extract Hom-categories from the collage, and similarly therefore the cocomma may not be right. Consider that a natural transformation between two functors from \*->\* into C does not give a non-invertible 2-cell in C. See https://nforum.ncatlab.org/discussion/3533/extracting-homcategories-as-limits/]

[TODO: Discuss Kan extensions, pointwise Kan extensions, and Kan lifts]

----

Kan lifts: We need to discuss profunctors first, aka bimodules or bi-indexed sets (as above) or distributors or the Kleisli category of the free cocompletion (which matches the presheaf category, with unit given by the Yoneda embedding; TODO: write a post on this). 

A key thing to note about profunctors: Cat embeds into Prof in four different ways: The canonical one, but also, since $$Cat = Cat^{co}$$ (via reading a functor from C to D also as a functor from C^{op} to D^{op}) and $$Prof = Prof^{op}$$ (via reading a bifunctor C^{op} x D -> Set not just as a profunctor from D to C but also a profunctor from C^{op} to D^{op}), we also have that Cat embeds into Prof^{co}, Prof^{op}, and Prof^{coop}.

Another key thing to note about profunctors: Every ordinary functor has a right adjoint, as a profunctor. This is just by taking f : A -> B and turning it into g(b) = Hom(f(a), b), the map from B to Psh(A) which would be the right adjoint for f as a genuine functor if its outputs were always representable presheaves.

Because every ordinary functor has a right adjoint as a profunctor, we automatically get the right Kan lift of an ordinary functor along an ordinary functor, as a profunctor (as composition with a right adjoint yields a Kan lift). The formula this yields is that the right Kan lift of s : B -> C along r : A -> C is the profunctor from B to A given by Hom_C(r(a), s(b)).

Note that this is precisely the same as the bi-indexed set that corresponds to this cospan under the right adjoint or coreflection in the gamut/idempotent adjunction noted above.

\[Note that, if A is cocomplete, we also automatically get a way to turn profunctors into A into ordinary functors into A. TODO: Speak more on the implications of this with respect to size.\]

It turns out, we can even take the right Kan lift of a profunctor along a profunctor in the same way. Just interpret the profunctors as ordinary functors into a presheaf category, and use the same formula. It's not quite automatic to see that this follows from the above, we can reason to this from the fact that the Yoneda embedding acting on a category which is already a presheaf category has as a left adjoint the multiplication for the free cocompletion monad. But that's a pain. We can also see it just by working through the formula to explicitly confirm that it works: When C is replaced by Set^{C^{op}} and then r and s are replaced by profunctors accordingly \[but for which I will write the contravariant argument first rather than the covariant argument, for my convenience\], the formula turns into "forall c. Hom_C(r c a, s c b)". It's not hard to show that another profunctor g a b entails this iff we have a map from r composed with g into s, given the definition of profunctor composition in terms of a co-end. \[TODO\]

Thus, we have the general formula for right Kan lifts of profunctors along profunctors, yielding profunctors. Of course, if we right Kan lift a functor along a functor this way within Prof, and the result is a gneuine functor, it remains also a right Kan lift in Cat. This gives us our "pointwise" right Kan lifts (TODO: talk more about why this is the right notion of pointwise).

By swapping out the way that Cat embeds into Prof for one of the other ways of the four, we can turn this also into pointwise right Kan extensions as profunctors, or pointwise left Kan lifts/extensions as "ind-functors" (by which I mean, maps into (Set^C)^{op} rather than Set^(C^{op})).

----

It's very easy to get my head turned around on all this, so I've written it out explicitly, the four ways to map the 2-category Cat into the 2-category Prof (possibly with contravariance or opvariance):

A profunctor from C to D is a bifunctor C x D^{op} -> Set

Hom(d, Fc), we have c as the first argument, d as the second argument, and the categories involved are C and D.
C x D^{op} -> Set; profunctor from C to D.
This embedding is a 2-functor from Cat to Prof which keeps 1-cells oriented the same and 2-cells oriented the same.

Hom(d, Fc), we have d as the first argument, c as the second argument, and the categories involved are D^{op} and C^{op}.
D^{op} x C -> Set; profunctor from D^{op} to C^{op}.
This embedding is a 2-functor from Cat to Prof which turns 1-cells around and keeps 2-cells the same.

Hom(Fc, d), we have c as the first argument, d as the second argument, and the categories involved are C^{op} and D^{op}
C^{op} x D -> Set; profunctor from C^{op} to D^{op}.
This embedding is a 2-functor from Cat to Prof which keeps 1-cells oriented the same and turns 2-cells around.

Hom(Fc, d), we have d as the first argument, c as the second argument, and the categories involved are D and C.
D x C^{op} -> Set; profunctor from D to C.
This embedding is a 2-functor from Cat to Prof which turns 1-cells around and turns 2-cells around.

----

As mentioned above, a better perspective on comma, cocommas, etc, is available by thinking about profunctors.

In the following diagram, squiggly arrows represent profunctors (and we follow the usual, though arbitrary, convention for the direction in which these point). The indicated 2-cells are the universal ones provided by the Kan extensions/lifts.

<iframe class="quiver-embed" src="https://q.uiver.app/?q=WzAsNCxbMCwwLCJcXGJ1bGxldCJdLFsyLDIsIlxcYnVsbGV0Il0sWzQsMCwiXFxidWxsZXQiXSxbNiwyLCJcXGJ1bGxldCJdLFswLDEsIkwiLDJdLFswLDIsIlQiXSxbMiwzLCJSIl0sWzEsMywiQiIsMl0sWzEsMiwiXFxtYXRocm17TGFufV9MKFQpIiwwLHsib2Zmc2V0IjotMiwic3R5bGUiOnsiYm9keSI6eyJuYW1lIjoic3F1aWdnbHkifX19XSxbMSwyLCJcXG1hdGhybXtSaWZ0fV9SKEIpIiwyLHsib2Zmc2V0IjoyLCJzdHlsZSI6eyJib2R5Ijp7Im5hbWUiOiJzcXVpZ2dseSJ9fX1dLFs1LDEsIiIsMCx7InNob3J0ZW4iOnsic291cmNlIjoyMH19XSxbMiw3LCIiLDAseyJzaG9ydGVuIjp7InRhcmdldCI6MjB9fV1d&embed" width="944" height="432" style="border-radius: 8px; border: none;"></iframe>
<!--
\[\begin{tikzcd}
  \bullet &&&& \bullet \\
  \\
  && \bullet &&&& \bullet
  \arrow["L"', from=1-1, to=3-3]
  \arrow[""{name=0, anchor=center, inner sep=0}, "T", from=1-1, to=1-5]
  \arrow["R", from=1-5, to=3-7]
  \arrow[""{name=1, anchor=center, inner sep=0}, "B"', from=3-3, to=3-7]
  \arrow["{\mathrm{Lan}_L(T)}", shift left=2, squiggly, from=3-3, to=1-5]
  \arrow["{\mathrm{Rift}_R(B)}"', shift right=2, squiggly, from=3-3, to=1-5]
  \arrow[shorten <=7pt, Rightarrow, from=0, to=3-3]
  \arrow[shorten >=7pt, Rightarrow, from=1-5, to=1]
\end{tikzcd}\]
-->

Note that Cat embeds into Prof in a way which is surjective on 0-cells, 2-cells, and 3-cells, just not on 1-cells. Prof introduces new 1-cells, but no new 0-cells, no new 2-cells between existing 1-cells, and no new 3-cells between existing 2-cells.

Every span induces a corresponding profunctor via left Kan extension, as indicated. And every cospan induces a corresponding profunctor via right Kan lift, as indicated. What's more, these right Kan lifts are pointwise/absolute: We have that $$ L ; \mathrm{Rift}_R(B) = \mathrm{Rift}_R(L ; B) $$.

As a result, note that 2-cells from $$ \mathrm{Lan}_L(T) $$ to $$\mathrm{Rift}_R(B) $$ correspond (by the universal property of left Kan extension) to diagrams of the following form, where now the indicated 2-cell on the left is arbitrary, while the 2-cell on the right remains the designated one for the Kan lift:

<iframe class="quiver-embed" src="https://q.uiver.app/?q=WzAsNCxbMCwwLCJcXGJ1bGxldCJdLFsyLDIsIlxcYnVsbGV0Il0sWzQsMCwiXFxidWxsZXQiXSxbNiwyLCJcXGJ1bGxldCJdLFswLDEsIkwiLDJdLFswLDIsIlQiXSxbMiwzLCJSIl0sWzEsMywiQiIsMl0sWzEsMiwiXFxtYXRocm17UmlmdH1fUihCKSIsMix7Im9mZnNldCI6Miwic3R5bGUiOnsiYm9keSI6eyJuYW1lIjoic3F1aWdnbHkifX19XSxbNSwxLCIiLDAseyJzaG9ydGVuIjp7InNvdXJjZSI6MjB9fV0sWzIsNywiIiwwLHsic2hvcnRlbiI6eyJ0YXJnZXQiOjIwfX1dXQ==&embed" width="944" height="432" style="border-radius: 8px; border: none;"></iframe>
{% comment %}
\[\begin{tikzcd}
    \bullet &&&& \bullet \\
    \\
    && \bullet &&&& \bullet
    \arrow["L"', from=1-1, to=3-3]
    \arrow[""{name=0, anchor=center, inner sep=0}, "T", from=1-1, to=1-5]
    \arrow["R", from=1-5, to=3-7]
    \arrow[""{name=1, anchor=center, inner sep=0}, "B"', from=3-3, to=3-7]
    \arrow["{\mathrm{Rift}_R(B)}"', shift right=2, squiggly, from=3-3, to=1-5]
    \arrow[shorten <=7pt, Rightarrow, from=0, to=3-3]
    \arrow[shorten >=7pt, Rightarrow, from=1-5, to=1]
\end{tikzcd}\]
{% endcomment %}

These in turn correspond, by the universal property of right Kan lifts and the fact that  $$ L ; \mathrm{Rift}_R(B) = \mathrm{Rift}_R(L ; B) $$, to diagrams of the following form, with an arbitrary 2-cell:

<iframe class="quiver-embed" src="https://q.uiver.app/?q=WzAsNCxbMCwwLCJcXGJ1bGxldCJdLFsyLDIsIlxcYnVsbGV0Il0sWzQsMCwiXFxidWxsZXQiXSxbNiwyLCJcXGJ1bGxldCJdLFswLDEsIkwiLDJdLFswLDIsIlQiXSxbMiwzLCJSIl0sWzEsMywiQiIsMl0sWzIsMSwiIiwwLHsic2hvcnRlbiI6eyJ0YXJnZXQiOjIwfSwibGV2ZWwiOjJ9XV0=&embed" width="944" height="432" style="border-radius: 8px; border: none;"></iframe>
{% comment %}
\[\begin{tikzcd}
    \bullet &&&& \bullet \\
    \\
    && \bullet &&&& \bullet
    \arrow["L"', from=1-1, to=3-3]
    \arrow["T", from=1-1, to=1-5]
    \arrow["R", from=1-5, to=3-7]
    \arrow["B"', from=3-3, to=3-7]
    \arrow[shorten >=11pt, Rightarrow, from=1-5, to=3-3]
\end{tikzcd}\]
{% endcomment %}

In this way, we get our gamut from spans to profunctors to cospans, defining maps from each to each later thing as the suitable commutative diagrams. We also have functors from spans to profunctors representing that leg of the gamut (left Kan extension), and from cospans to profucntors representing that leg of the gamut (right Kan lift). And it turns out by our last argument that these also represent the full gamut; that is, a map from a span to a cospan is the same as a map of profunctors between the left Kan extension and right Kan lift.

All this should be worded better, of course.

Anyway, it turns out these functors also have adjoints; there is a right adjoint to turning a span into a profunctor, and there is a left adjoint to turning a cospan into a profunctor.

In this way, the notion of span to cospan maps is also representable, both by turning a span into a profunctor and then into a cospan (cocomma category), and by turning a cospan into a profunctor and then into a span (comma category).

Incredibly, both the adjunction between spans and profunctors and the adjunction between profunctors and cospans are idempotent, in such a way as that profunctors are a reflective full subcategory of the spans and a coreflective full subcategory of the cospans.

These are the observations that were made above. Finally, we note that the way in which nCat-valued profunctors on nCats embed as spans is as an nCat, but the way in which these embed as cospans involves an (n + 1)Cat.

----

Note that by thinking about proarrow equipments, we can also better understand the significance of lexcategories. A lexcategory is like a 1-category equipped also with a 2-category which it maps into surjectively on 0-cells, 2-cells, and 3-cells. (That is, a 1-category acting like Set, and a 2-category acting like Set-valued profunctors between sets). We might axiomtize all this as a 1-category Set, a 2-category SetProf, a functor from Set into SetProf which is surjective on 0-, 2-, and 3-cells (everything but 1-cells), such that every 1-cell in Set has a right adjoint in SetProf, and such that Set has a terminal object 1, and the 1-category SetProf(1, 1) is equivalent to Set. We can also add rules for left Kan extensions and right Kan lifts to SetProf, and that the right Kan lifts should be pointwise/absolute. Then we will find that any instance of this structure is such that Set is a category with finite limits (buildable from this structure), and conversely, any category with finite limits gives rise to an instance of this structure, in a 1 : 1 way.

We might want to axiomatize this differently, by saying not that Set is included in SetProf, but rather, profunctors can be composed on either side with functions from Set (covariantly on one side and contravariantly on the other side), or some such principles. We might want to axiomatize this in a way where we don't take the Yoneda embedding, etc, as a given, but somehow can derive these. I will think about this more. But something like this is where the great significance of lexcategories can be seen to come from, from viewing Set as also having proarrows with suitable properties.

The 0-ary compositions of 1-cells in SetProf are the Hom functors, and correspond in this context to having equality types/identity types (thus, yielding equalizers, pullbacks, etc, of which binary products are a special case). The 2-ary compositions of 1-cells in SetProf involve a summation, and thus induce sigma types (of which also binary products are a special case).

Probably the best thing to do is to consider a 1-category Set with proarrow equipment (giving rise to ProfSet, including composability of profunctors; note that we can think of this in terms of double categories with universal fillings for niches), which also has a terminal object 1. Note that we obtain a functor from Set into ProfSet(1, 1) by considering the composite profunctor 1 to A to 1 for each object A of set, using the unique morphism from A to 1 (which can be read as a profunctor in either direction). If we further demand that this functor from Set into ProfSet(1, 1) be an equivalence, I believe the result may be the same as making Set a lexcategory and Prof the corresponding canonical proarrow equipment? And maybe this extends to Cat and Prof as well?