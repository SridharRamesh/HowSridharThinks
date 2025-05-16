---
title: "Abelian Categories"
date: 2022-6-19
---
Here, we give a manifestly self-dual presentation of the concept of abelian categories.

(We previously discussed abelian categories in terms of their relationship to [regular categories](@/InternalLogicRegular.md).)

Consider the following properties a category may have:

1. Has finite limits and finite colimits.
    1. Has finite products and finite coproducts.
        1. Has terminal object and initial object.
        2. Has binary products and binary coproducts.
    2. Has equalizers and coequalizers.
2. Every map which is both a monomorphism and an epimorphism is an isomorphism.
    1. Every monic is regular monic.
    2. Every epic is regular epic.
3. The finite products and finite coproducts are in fact biproducts.
    1. The map from the initial object to the terminal object is an isomorphism.
        1. Any parallel maps into the initial object are equal.
        2. Any parallel maps out of the terminal object are equal.
    2. The map from A + B to A x B given by (TODO) is an isomorphism.
4. Every object has a negation endomorphism (TODO).

All of these conditions are manifestly self-dual, except for 2.1 and 2.2 being each others' duals, and 3.1.1 and 3.1.2 being each others' duals.

Clearly 1 is equivalent to 1.1 + 1.2, while 1.1 is equivalent to 1.1.1 + 1.1.2.

Condition 2 is called being a "balanced category". Either of 2.1 or 2.2 entails 2; conversely, in the context of 1, I believe 2 entails both of 2.1 and 2.2 (TODO: Check this).


The combination of 1 and 2 entails, among other things, the structure of an effective regular category (indeed, I believe simply finite limits, coequalizers of congruences, and being balanced entails being an effective regular category). Given the structure of 1 alone, any morphism canonically decomposes into the coequalizer of its kernel pair, followed by a monic-epic, followed by the equalizer of its cokernel pair. 2 is then the demand that the middle monic-epic be an isomorphism, giving us the usual image factorization. (TODO: I think this is all correct, but I should check on how this interacts with the pullback stability condition in the definition of a regular category, and also on how the definition of a regular category may not entail being balanced because epics need not be regular epic.)

Condition 3 is straightforwardly equivalent to 3.1 + 3.2, in the usual way that we get results for arbitrary finite arity from arities 0 and 2.

For interpreting condition 3.1, note that we have a unique map from the initial object to the terminal object (granted both by the terminality property, and also separately by the initiality property). In the context of 1.1.1 and 2, we have that 3.1 is equivalent to 3.1.1 + 3.1.2, since 3.1.1 says this map is monic, and 3.1.2 says this map is epic. 


In the context of 1.1.1, condition 3.1 is equivalent to having "zero morphisms"; that is, being enriched over pointed sets.

In the context of 1.1, condition 3 is equivalent to being enriched multilinearly over abelian monoids (see [nLab](https://ncatlab.org/nlab/show/biproduct#BiproductsImplyEnrichment)). Adding in condition 4 then makes these abelian monoids into abelian groups.

I believe effective regular category structure + zero morphisms already entails that the subobjects of A are a retract of the congruences on A (i.e., subobjects of A x A which satisfy the equivalence relation conditions). Any congruence on A, though of as a subobject of A x A, induces a subobject of A by pulling back along $$\langle identity, zero \rangle : A \to A \times A$$, and conversely, any subobject of A induces a congruence on A by coequalizing against the parallel zero morphism and then taking the kernal pair. (TODO: Show this is a retraction; i.e., the induced endomorphism on subobjects of A is identity). I believe 5 then makes this retraction into a 1 : 1 correspondence. This has something to do with being a Malcev category.

The conjunction of all these conditions is the definition of an abelian category. Thus, an abelian category is a balanced category with finite biproducts, equalizers, coequalizers, and negation.

***

The category of abelian groups is of course the canonical abelian category.

Note that Set satisfies 1, 2, and 3.1.1, but does not satisfy 3.1.2, and thus does not satisfy 3.1. We cannot even interpret 3.2 and 4 in Set, since 3.2 depends on 3.1 to be interpreted, and 4 depends on 3 to be interpreted.

Note that the category of abelian monoids satisfies 1 and 3, but does not satisfy 2 or 4. That it does not satisfy 4 is unsurprising, but that it does not satisfy 2 is very worthy of note! Consider the inclusion from N into Z. This is both monic and epic, but not an isomorphism. I believe the category of abelian monoids (as with any category monadic over Set) satisfies 2.1; however, it does not satisfy 2.2.

***

1.597 and also 1.598 of Categories, Allegories by Freyd and Scedrov suggest that simply having finite limits and colimits with all monics and epics being regular, plus having the initial and terminal object coincide (thus, 1, 2.1 + 2.2, and 3.1), is enough to ensure being an abelian category? Essentially, if we consider the cokernel of the diagonal map from A into A x A, we find that A maps into this cokernel (via $$\langle identity, zero\rangle : A \to A \times A$$ followed by the cokernel map) both monically and epically (although I don't follow the argument for epically?), and thus this cokernel is isomorphic to A. This essentially means A is the same as the Grothendieck group on A. The diagonal cokernel from A x A to A gives us a subtraction operation. From this we also get negation (since we have zero already), and thus we get addition as well (now that we have subtraction and negation). With a modicum of work we see associativity, etc. So we are enriched over abelian monoids with negation, which gives us 3.2 and 4.

The argument for epicness that I couldn't follow in Freyd-Scedrov should I think be something like this: Let $$c : A \times A \to C$$ be the cokernel of $$\langle 1, 1 \rangle : A \to A \times A$$. Now consider the map $$m : A \to C$$ given by $$\langle 1, 0 \rangle :: A \to A \times A$$ followed by $$c$$. To show this map $$m$$ is epic, we will show that its cokernel is the zero object. Its cokernel amounts to the same thing as cokerneling $$A \times A$$ by both (1, 0) and (1, 1) simultaneously. But if (1, 0) goes to zero, and (1, 1) goes to zero, then keeping in mind that (1, 0) + (0, 1) = (1, 1), then (0, 1) goes to zero as well. And if (1, 0) and (0, 1) have both gone to zero, then everything goes to zero. QED.

***

The following are my attempts to make sense of the Venn-style diagrams by Ravi Vakli, Terry Tao, et al, for reasoning about abelian categories:

To an abelian category, we may attach a (partial, multivalued) monoid like so:

We say X = Y as shorthand for "There is an isomorphism from X to Y". Of course, for a given X and Y, there may be multiple isomorphisms. A more proper account of things would consider this.

We say AB = X as shorthand for "There is a short exact sequence $$0 \to A \to X \to B \to 0$$"; in other words, we say AB a shorthand for "The X such that there is a short exact sequence $$0 \to A \to X \to B \to 0$$. Of course for a given A and B, there may be no such X, or multiple such X, or even multiple such sequences for the same X. A more proper account of things would consider all this.

Note that in an abelian category, there is a 1 : 1 correspondence between ways in which X is a subobject of a quotient of Y and ways in which X is a quotient of a subobject of Y. That is, consider commutative diagrams of the following sort which are simultaneously pullbacks and pushouts, with the arrows being monic/subobjects and epic/quotients as indicated by tails or double heads, respectively, and with the correspondingly named $$i$$ and $$\pi$$ pairs comprising short exact sequences:

<!-- \[\begin{tikzcd}
    S && X && Q \\
    & L && R \\
    && Y
    \arrow["{i_{LQ}}"{description}, tail, from=2-2, to=3-3]
    \arrow["{\pi_{SR}}"{description}, two heads, from=3-3, to=2-4]
    \arrow["{\pi_{SX}}"{description}, two heads, from=2-2, to=1-3]
    \arrow["{i_{XQ}}"{description}, tail, from=1-3, to=2-4]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=45}, draw=none, from=2-2, to=2-4]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=-135}, draw=none, from=2-4, to=2-2]
    \arrow["{\pi_{XQ}}"{description}, two heads, from=2-4, to=1-5]
    \arrow["{\pi_{LQ}}"{description}, curve={height=24pt}, two heads, from=3-3, to=1-5]
    \arrow["{i_{SR}}"{description}, curve={height=24pt}, tail, from=1-1, to=3-3]
    \arrow["{i_{SX}}"{description}, tail, from=1-1, to=2-2]
\end{tikzcd}\] -->
<iframe class="quiver-embed" src="https://q.uiver.app/?q=WzAsNixbMSwxLCJMIl0sWzIsMiwiWSJdLFszLDEsIlIiXSxbMiwwLCJYIl0sWzQsMCwiUSJdLFswLDAsIlMiXSxbMCwxLCJpX3tMUX0iLDEseyJzdHlsZSI6eyJ0YWlsIjp7Im5hbWUiOiJtb25vIn19fV0sWzEsMiwiXFxwaV97U1J9IiwxLHsic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoiZXBpIn19fV0sWzAsMywiXFxwaV97U1h9IiwxLHsic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoiZXBpIn19fV0sWzMsMiwiaV97WFF9IiwxLHsic3R5bGUiOnsidGFpbCI6eyJuYW1lIjoibW9ubyJ9fX1dLFswLDIsIiIsMSx7InN0eWxlIjp7Im5hbWUiOiJjb3JuZXIifX1dLFsyLDAsIiIsMSx7InN0eWxlIjp7Im5hbWUiOiJjb3JuZXIifX1dLFsyLDQsIlxccGlfe1hRfSIsMSx7InN0eWxlIjp7ImhlYWQiOnsibmFtZSI6ImVwaSJ9fX1dLFsxLDQsIlxccGlfe0xRfSIsMSx7ImN1cnZlIjo0LCJzdHlsZSI6eyJoZWFkIjp7Im5hbWUiOiJlcGkifX19XSxbNSwxLCJpX3tTUn0iLDEseyJjdXJ2ZSI6NCwic3R5bGUiOnsidGFpbCI6eyJuYW1lIjoibW9ubyJ9fX1dLFs1LDAsImlfe1NYfSIsMSx7InN0eWxlIjp7InRhaWwiOnsibmFtZSI6Im1vbm8ifX19XV0=&embed" width="688" height="300" style="border-radius: 8px; border: none;"></iframe>


Clearly, the rest of the diagram is uniquely determined by the pullback/pushout square. Furthermore, once we know either the span or the cospan of the pullback/pushout square, this uniquely determines the rest. In an abelian category, any monic-epic span is the pushout of its pullback, and dually for monic-epic cospans as the pullback of their pushout (TODO: This sentence may be completely wrong, I should check it). (This has some relation to [commas and cocommas](@/CommasCollages.md)).

We may consider such a diagram as indicating how SXQ = Y, and thus providing an associative law. That is, if we know that XQ = R and SR = Y, we obtain from this also some SX = L and LQ = Y. And dually, we obtain from the latter, the former, and the back and forth in either direction is identity (up to the appropriate notion of isomorphism). Thus, of the expressions S(XQ) and (SX)Q, the possible values for one (which may be undefined or multiply defined) are the same as the possible values of the other. In this way, our partial or multivalued monoid does indeed satisfy the associativity law. Thus allows us to say more generally that any n-ary composition for n ≥ 1 makes sense and can be rebracketed arbitrarily.

For illustration, here is a 5-ary composition (and it's clear how any n-ary composition would work analogously). The entire diagram is uniquely determined just by knowing enough information to specify any particular bracketed breakdown of it (e.g., in terms of 2-ary compositions).

<!--
\[\begin{tikzcd}
    A && B && C && D && E \\
    & AB && BC && CD && DE \\
    && ABC && BCD && CDE \\
    &&& ABCD && BCDE \\
    &&&& ABCDE
    \arrow[tail, from=2-2, to=3-3]
    \arrow[two heads, from=3-3, to=2-4]
    \arrow[two heads, from=2-2, to=1-3]
    \arrow[tail, from=1-3, to=2-4]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=45}, draw=none, from=2-2, to=2-4]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=-135}, draw=none, from=2-4, to=2-2]
    \arrow[two heads, from=2-4, to=1-5]
    \arrow[tail, from=1-1, to=2-2]
    \arrow[tail, from=1-5, to=2-6]
    \arrow[two heads, from=2-6, to=1-7]
    \arrow[tail, from=2-4, to=3-5]
    \arrow[two heads, from=3-5, to=2-6]
    \arrow[tail, from=3-3, to=4-4]
    \arrow[two heads, from=4-4, to=3-5]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=45}, draw=none, from=2-4, to=2-6]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=-135}, draw=none, from=2-6, to=2-4]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=45}, draw=none, from=3-3, to=3-5]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=-135}, draw=none, from=3-5, to=3-3]
    \arrow[tail, from=1-7, to=2-8]
    \arrow[two heads, from=2-8, to=1-9]
    \arrow[tail, from=2-6, to=3-7]
    \arrow[two heads, from=3-7, to=2-8]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=45}, draw=none, from=2-6, to=2-8]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=-135}, draw=none, from=2-8, to=2-6]
    \arrow[tail, from=3-5, to=4-6]
    \arrow[two heads, from=4-6, to=3-7]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=45}, draw=none, from=3-5, to=3-7]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=-135}, draw=none, from=3-7, to=3-5]
    \arrow[tail, from=4-4, to=5-5]
    \arrow[two heads, from=5-5, to=4-6]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=45}, draw=none, from=4-4, to=4-6]
    \arrow["\lrcorner"{anchor=center, pos=0.125, rotate=-135}, draw=none, from=4-6, to=4-4]
\end{tikzcd}\]
-->
<iframe class="quiver-embed" src="https://q.uiver.app/?q=WzAsMTUsWzEsMSwiQUIiXSxbMiwyLCJBQkMiXSxbMywxLCJCQyJdLFsyLDAsIkIiXSxbNCwwLCJDIl0sWzAsMCwiQSJdLFs2LDAsIkQiXSxbNSwxLCJDRCJdLFs0LDIsIkJDRCJdLFszLDMsIkFCQ0QiXSxbOCwwLCJFIl0sWzcsMSwiREUiXSxbNiwyLCJDREUiXSxbNSwzLCJCQ0RFIl0sWzQsNCwiQUJDREUiXSxbMCwxLCIiLDEseyJzdHlsZSI6eyJ0YWlsIjp7Im5hbWUiOiJtb25vIn19fV0sWzEsMiwiIiwxLHsic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoiZXBpIn19fV0sWzAsMywiIiwxLHsic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoiZXBpIn19fV0sWzMsMiwiIiwxLHsic3R5bGUiOnsidGFpbCI6eyJuYW1lIjoibW9ubyJ9fX1dLFswLDIsIiIsMSx7InN0eWxlIjp7Im5hbWUiOiJjb3JuZXIifX1dLFsyLDAsIiIsMSx7InN0eWxlIjp7Im5hbWUiOiJjb3JuZXIifX1dLFsyLDQsIiIsMSx7InN0eWxlIjp7ImhlYWQiOnsibmFtZSI6ImVwaSJ9fX1dLFs1LDAsIiIsMSx7InN0eWxlIjp7InRhaWwiOnsibmFtZSI6Im1vbm8ifX19XSxbNCw3LCIiLDEseyJzdHlsZSI6eyJ0YWlsIjp7Im5hbWUiOiJtb25vIn19fV0sWzcsNiwiIiwxLHsic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoiZXBpIn19fV0sWzIsOCwiIiwxLHsic3R5bGUiOnsidGFpbCI6eyJuYW1lIjoibW9ubyJ9fX1dLFs4LDcsIiIsMSx7InN0eWxlIjp7ImhlYWQiOnsibmFtZSI6ImVwaSJ9fX1dLFsxLDksIiIsMSx7InN0eWxlIjp7InRhaWwiOnsibmFtZSI6Im1vbm8ifX19XSxbOSw4LCIiLDEseyJzdHlsZSI6eyJoZWFkIjp7Im5hbWUiOiJlcGkifX19XSxbMiw3LCIiLDEseyJzdHlsZSI6eyJuYW1lIjoiY29ybmVyIn19XSxbNywyLCIiLDEseyJzdHlsZSI6eyJuYW1lIjoiY29ybmVyIn19XSxbMSw4LCIiLDEseyJzdHlsZSI6eyJuYW1lIjoiY29ybmVyIn19XSxbOCwxLCIiLDEseyJzdHlsZSI6eyJuYW1lIjoiY29ybmVyIn19XSxbNiwxMSwiIiwxLHsic3R5bGUiOnsidGFpbCI6eyJuYW1lIjoibW9ubyJ9fX1dLFsxMSwxMCwiIiwxLHsic3R5bGUiOnsiaGVhZCI6eyJuYW1lIjoiZXBpIn19fV0sWzcsMTIsIiIsMSx7InN0eWxlIjp7InRhaWwiOnsibmFtZSI6Im1vbm8ifX19XSxbMTIsMTEsIiIsMSx7InN0eWxlIjp7ImhlYWQiOnsibmFtZSI6ImVwaSJ9fX1dLFs3LDExLCIiLDEseyJzdHlsZSI6eyJuYW1lIjoiY29ybmVyIn19XSxbMTEsNywiIiwxLHsic3R5bGUiOnsibmFtZSI6ImNvcm5lciJ9fV0sWzgsMTMsIiIsMSx7InN0eWxlIjp7InRhaWwiOnsibmFtZSI6Im1vbm8ifX19XSxbMTMsMTIsIiIsMSx7InN0eWxlIjp7ImhlYWQiOnsibmFtZSI6ImVwaSJ9fX1dLFs4LDEyLCIiLDEseyJzdHlsZSI6eyJuYW1lIjoiY29ybmVyIn19XSxbMTIsOCwiIiwxLHsic3R5bGUiOnsibmFtZSI6ImNvcm5lciJ9fV0sWzksMTQsIiIsMSx7InN0eWxlIjp7InRhaWwiOnsibmFtZSI6Im1vbm8ifX19XSxbMTQsMTMsIiIsMSx7InN0eWxlIjp7ImhlYWQiOnsibmFtZSI6ImVwaSJ9fX1dLFs5LDEzLCIiLDEseyJzdHlsZSI6eyJuYW1lIjoiY29ybmVyIn19XSxbMTMsOSwiIiwxLHsic3R5bGUiOnsibmFtZSI6ImNvcm5lciJ9fV1d&embed" width="1353" height="688" style="border-radius: 8px; border: none;"></iframe>

We might imagine ourselves in a position where, although we do not know much, we know how to invert and compose isomorphisms, compose monics, compose epics, take kernels and cokernels, pull back monic-epic spans, push out monic-epic cospans, and take the factorizations coming from those those pullback or pushout universal properties. This is enough to know how to compose such diagrams.

The zero object of our abelian category arises as the kernel or cokernel of identity, from which we also have that X0 = X and 0X = X in a straightforward way (sorry for mixing multiplicative and additive notation like this). Thus we indeed have an identity and thus have a monoid (except, as always, for the partialness or multivaluedness).

Note that if AB = 0, then A = B = 0, as 0 has no nontrivial subobjects or quotients. Thus, we are in a monoid with no nontrivial inverses.

We might imagine that, though we are given the operations above, we are not in general given the operation of direct sum (aka direct products or biproducts, in the binary case we are interested in). However, when the direct sum A + B exists, we get short exact sequences such that AB = A + B and BA = A + B; thus, AB = BA (I really must apologize for mixing multiplicative and additive notation now. The multiplicative notation refers to our monoid based on short exact sequences, the additive notation refers to the biproduct structure of the abelian category). Thus, the direct sums we happen to have induce commuting values.

Our monoid is also cancellative in the following sense: Suppose we have $$XY_1 = Z = XY_2$$ where the short exact sequences both use the same inclusion from X into Z. Then the cokernel of this inclusion is uniquely determined, so $$Y_1 = Y_2$$. Similarly dually for kernels of quotients (everything we do will be self-dual, because abelian categories are a self-dual concept).

If we are fortunate to be ignorant in just the right way of the full scope of what exists in the world, we may be in a position where we know so little, that our monoid remains at most single-valued (this is why it is key to not know how to take direct sums in general, which would automatically induce a particular monoid product for any two objects which might not be the one we want in a single-valued world).

Scratch the above a bit. Perhaps this is the way to go: We imagine ourselves in a category with a subcategory of M-maps and a subcategory of E-maps. The isomorphisms are precisely the maps which are both M and E. The M maps all are monic (though other maps may also be monic, for all I care about right now), and similarly the E maps all are epic. This category has (E; M) factorization. Furthermore, all pullbacks of M maps exist and are M, and all pushouts of E maps exist and are E. Finally, for each object X, we have a suitably monotonic bijection between the M-subobjects of X and the E-quotients of X. And this bijection interacts appropriately with the pullback/pushout structure (I'm not sure what the appropriate interaction is, exactly, but consider for example that an (M, E)-cospan has a pullback which can be computed purely by swinging the M map into an E-map, composing the two E-maps, then swinging this back into an M map, or also dually computed in the other way starting with swinging the E map. So we need to at least say these two processes result in the same object in the end, and also dually for (M, E) spans.)

We also have a zero object, with no nontrivial subobjects or quotient objects. If we are fortunate, it may be that from any A to B, there is at most one M-or-E-or-both map.

This should be enough structure to set up much of what we want with our partial monoids, while still allowing the possibility of having somewhat unique containments as illustrated by Ravi Vakli style diagrams.

Note that we can't really in general hope to do everything the Ravi Vakli style diagrams do in terms of identifying subquotients, because these diagrams carry implications which are not in general valid. For example, these diagrams imply that if A, B, and C are subspaces of an ambient space, with A and B complementary, and A and C complementary, then B = C (not just as isomorphic spaces, but equal qua subspace). Since B and C will both be identified with the quotient by A, in a Ravi Vakli diagram. But this implication is not true in general, because of failure of distributivity in lattices of subspaces.

***

I know the above is unreadable. I like to take notes for my own purposes, that only I know how to read. This blog is for me, it's not for you. I'll do the blog for you to read later.