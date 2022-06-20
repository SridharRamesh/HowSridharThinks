---
title: "Abelian Categories"
date: 2022-6-19
---
Here, we give a manifestly self-dual presentation of the concept of abelian categories.

(We previously discussed abelian categories in terms of their relationship to [regular categories](./InternalLogicRegular.html).)

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


Clearly, the rest of the diagram is uniquely determined by the pullback/pushout square. Furthermore, once we know either the span or the cospan of the pullback/pushout square, this uniquely determines the rest. In an abelian category, any monic-epic span is the pushout of its pullback, and dually for monic-epic cospans as the pullback of their pushout (TODO: This sentence may be completely wrong, I should check it). (This has some relation to [commas and cocommas](./CommasCollages.html)).

We may consider such a diagram as indicating how SXQ = Y, and thus providing an associative law. That is, if we know that XQ = R and SR = Y, we obtain from this also some SX = L and LQ = Y. And dually, we obtain from the latter, the former, and the back and forth in either direction is identity (up to the appropriate notion of isomorphism). Thus, of the expressions S(XQ) and (SX)Q, the possible values for one (which may be undefined or multiply defined) are the same as the possible values of the other. In this way, our partial or multivalued monoid does indeed satisfy the associativity law. Thus allows us to say more generally that any n-valued composition for n ≥ 1 makes sense and can be rebracketed arbitrarily.

Clearly such squares can be composed in a straightforward way, using the pushback/pullout and composition structure.

We might imagine ourselves in a position where, although we do not know much, we know how to invert and compose isomorphisms, compose monics, compose epics, pullback monic-epic spans, and pushout monic-epic cospans. This is enough to know how to compose such squares.

If we also know about the zero object (which is simultaneously a quotient and a subobject of everything, in a trivial way), then we also have that X0 = X and 0X = X in a straightforward way, where 0 is the zero object of our abelian category (sorry for mixing multiplicative and additive notation like this). Thus we have a monoid (except, as always, for the partialness or multivaluedness).

Note that if AB = 0, then A = B = 0, as 0 has no nontrivial subobjects or quotients. Thus, we are in a monoid with no nontrivial inverses.

We might imagine that, though we know how to do the various things outlined above, we don't know how to take direct sums (aka direct products or biproducts, in the binary case we are interested in) in general. However, when the direct sum A + B exists, we get short exact sequences such that AB = A + B and BA = A + B; thus, AB = BA (I really must apologize for mixing multiplicative and additive notation now. The multiplicative notation refers to our monoid based on short exact sequences, the additive notation refers to the biproduct structure of the abelian category). Thus, direct sums induce commuting values.

Our monoid is also cancellative in the following sense: Suppose we have $$XY_1 = Z = XY_2$$ where the short exact sequences both use the same inclusion from X into Z. Then the cokernel of this inclusion is uniquely determined, so $$Y_1 = Y_2$$. Similarly dually for kernels of quotients (everything we do will be self-dual, because abelian categories are a self-dual concept).


In general, we may imagine ourselves fortunate enough to be in a position where, for any X and Y, we have nearly at most one way to see Y as of the form SXQ (thus, at most one canonical way to see X as "a part of" Y). We may specifically have that if there is any such decomposition, then there is some S, Q, and A such that any Y = S'XQ' is such that S' = SA_1 and Q' = A_2Q, with A_1, A_2, and X all commuting, and A_1 A_2 = A. We may call this strong cancellativity. We may think of S as what juts into X, Q as what X juts into, and A as the remainder of Y which commutes with X.

As a special case of this, we will have at most one injection or at most one projection between two objects. But in fact, this is an even stronger condition than one-sided cancellativity. We may also imagine ourselves so fortunate as that, for any A and B, there is at most one way we are aware of to solve AB = X. In these contexts, we are genuinely in a strongly cancellative partial (but not multi-valued) monoid with only trivial inverses.

In a strongly cancellative partial monoid with only trivial inverses, we get a nice poset (not simply preorder) structure for "part of". For if Y = SXQ while X = LYR, then I think it will follow that X = Y? (TODO)

All this strong cancellativity is maybe not bothering with? Well, no, maybe it makes sense. A subquotient X of Y can be thought of as a partial equivalence relation on Y. If we add in reflexivity, we get an equivalence relation, corresponding to the smallest quotient XQ of Y of which X is a subobject; this gives us our Q. On the other hand, if we take the partial equivalence relation, and just focus on its support (those elements which are reflexive), we get the smallest subobject SX of Y of which X is a quotient; this gives us our S. These are the corners of the pullback/pushout square from X to Y. Hm. This again makes it seem like we can't have arbitrary monic/epics in a pullback-pushout square. I think the problem here is that the same object may arise from different PERs. Consider how the zero object arises from total equivalence relations on any subobject. Consider the diamond lemma in general.

***

I know the above is unreadable. I like to take notes for my own purposes, that only I know how to read. This blog is for me, it's not for you. I'll do the blog for you to read later.