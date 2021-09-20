---
title: "\"Sequent Calculi\" vs. \"Natural Deduction\""
date: 2019-07-30
---
When asked what the difference between sequent calculus and natural deduction logical systems is, everyone (e.g., Wikipedia, but also everyone you meet in the world too) says a bunch of stuff that makes no sense. For example, as to whether sequents are involved, or whether sequents can have more than one disjunct on the right. None of this is relevant.

The much more salient distinction has to do with things like the subformula property and the relation to cut elimination.

In general, in logic, we have various rules which are trying to give us, from some prerequisites, as their conclusion, some morphism $$F \vdash G$$.

And we can encode this in four ways: we can grant the morphism $$F \vdash G$$ directly, we can grant its precomposition action "If you furthermore know $$G \vdash Y$$, then you can conclude $$F \vdash Y$$", we can grant its postcomposition action instead as "If you furthermore know $$X \vdash F$$, then you can conclude $$X \vdash G$$", or we could even grant its inbetween-composition "If you furthermore know $$X \vdash F$$ and $$G \vdash Y$$, then you can conclude $$X \vdash Y$$".

That is, we can choose for both of $$F$$ and $$G$$ whether we want to deal with them as things we map into or things we map out of, and grant the morphism at different kinds of directness or indirectness accordingly.

From any of these, we can get any of the others, of course, by use of structural rules around binary composition (cut rule) and identity.

A sequent calculus, in my mind, is a system set up so that you don't actually need to use any binary compositions (cut elimination) or any identities other than identity at atomic variables in order to prove tautologies, and such that each rule is set up to have the subformula property that all formulas in its prerequisite sequents are subformulas of those appearing in the granted sequent.

In sequent calculus, we encode all rules as composition actions, so that we never need to invoke cut explicitly (in proving tautologies). We use whichever of post-composition or pre-composition encoding will, for that particular rule, give us the subformula property, based on whether F is a subformula of G or vice versa in the $$F \vdash G$$ we are trying to encode.

A natural deduction system, on the other hand, in my mind, is one set up with no worry about rules satisfying the subformula property, but instead is set up with rules emphasizing postcomposition actions: in general, $$F \vdash G$$ is encoded via "From $$X \vdash F$$, conclude $$X \vdash G$$". That is, rules which for the most part don't involve interacting with/thinking too much about the left sides of sequents. The left sides stay unchanged or minimally changed throughout inferences as much as possible.

(Often, natural deduction is also presented in such a way that things aren't even written explicitly as sequents, and keeping track of what assumptions are around is notationally implicit rather than explicit, but that's irrelevant to the underlying concept.)

Tl;dr: Natural deduction flavored systems are those designed to minimize explicitly thinking about left sides of sequents. Sequent calculus flavored systems are those designed to have the subformula property for their rules. Neither of these quite matches the explicit-composition-and-adjunction-emphasizing way I tend to formalize logical systems.

I think the name "sequent calculus" has led many people awry. It's a bad name for emphasizing the salient difference; it draws attention to the wrong detail.

[TODO: Speak about cut elimination as ways of reducing terms to normal forms (in the sense of maximally beta-reduced and eta-expanded); frame this 2-categorically for adjunctions in general (see the work of Kosta Dosen); do other posts on proofs of normalization and confluence for lambda calculus, on using scone categories, and so on]