---
layout: post
title:  "The Internal Logic of Effective Regular and Abelian Categories"
date: 2020-1-16
---
[TODO: LaTeXify]

The internal logic of effective regular categories (aka, "exact categories", though this term is overloaded, or "Barr-exact categories") can be given in many different ways, but is perhaps most easily spelt out in terms of thinking of relations, rather than functions as such. Any theory of the following form presents an effective regular category, and any effective regular category has such a presentation:

We have various sorts and various finitary relations in our language (including an equality relation at each sort). In addition to the usual structural operations of substitution into a relation on A, B, C ... to get a relation on D, E, F, ..., using any sort-preserving relabelling mapping from {A, B, C, ...} to {D, E, F, ...}, we can also form new relations using conjunction and the existential quantifier (abstracting away one variable); substitution preserves these conjunction and existential quantification operations in the usual automatic syntactic way [this preservation can also be taken as a proof rule rather than a syntax rule, if one likes].

Our primitive judgement is that one relation entails another (universally over the variables in their presumed identical context). Our proof rules are all the usual ones for these operators; entailments are functorial over substitution, x = y \vdash R(x, y, ...) iff True \vdash R(x, x, ...) [equality given via left adjoint to contraction/diagonalization], every relation respects equality in the sense that x = y & P(x, ...) \vdash P(y, ...) [this would follow from the previous equality rule if we presumed an implication operator adjoint to conjunction, but we do not], X \vdash A & B & C & ... iff all of X \vdash A, X \vdash B, X \vdash C, ... [conjunction is a meet], and exists x . Phi(x, ...) \vdash Psi(...) iff Phi(x, ...) \vdash Psi(...), where in the latter statement Psi has been implicitly "weakened with unused dummy variable x" [existential quantification is left adjoint to such weakening]. We also have the coherence condition that A & exists x . Phi(x, ...) \vdash exists x . (A & Phi(x, ...)) [what Lawvere calls "Frobenius reciprocity"; note that this would follow automatically if we had "A implies -" as right adjoint to "A & -", by how left adjoints preserve left adjoints, but we do not actually presume such an implication operator here].

[The reason for Frobenius reciprocity in our proof rules, incidentally, is because everything in an effective regular category is pullback-stable, and conjunction can be seen as a kind of pullback.]

This should be all the needed proof rules. Again, I emphasize that these are precisely the provabilities in classical logic for this particular fragment of operations; extending to full classical logic is conservative over this fragment.

As noted, any theory of this form presents an effective regular category, and any effective regular category has such a presentation. Specifically, the effective regular category corresponding to such a syntactic presentation has an object for every subquotient of a product of primitive sorts [that is, for any partial equivalence relation (symmetric and transitive) on a tuple of sorts], with the morphisms between these given by functional relations up to equivalence.

Note that the same effective regular category may have multiple presentations; a presentation designates some particular sorts and relations as primitive, out of which the others are built. Different designations of primitivity correspond to different presentations. There is a natural sense in which the category of effective regular categories is a reflective full subcategory of the category of these presentations, as those presentations in which every complex thing which can be built-up also has a unique corresponding primitive symbol.

***

Incidentally, there is also a notion of a "regular category" (not necessarily EFFECTIVE regular), where we only demand quotients for those equivalence relations arising as kernel pairs of functions previously known to exist (i.e., just those quotients needed to obtain the image factorization of a function, as a quotient of its domain). But any regular category can be completed into an effective regular category by adding all the remaining quotients for arbitrary equivalence relations, so we may as well think of regular categories as just an intermediate concept between the above presentation-full syntactic concept and fully presentation-free effective regular categories.

***

An Abelian category can be defined in multiple ways, but in particular, an Abelian category is the same thing as an effective regular category enriched over Abelian groups. This means, for the internal logic of an Abelian category, we simply add to the above the presumption of Abelian group structure at every primitive sort [this structure then automatically transfers to all the subquotient sorts as well], and the presumption that all relations respect this Abelian group structure in the sense that whenever R(...) simultaneously holds of various tuples, it follows that R(...) also holds of any component-wise sum or difference of those tuples [it suffices to presume this for primitive relations, from which it will follow that it holds for their conjunctions and existential quantifications, and again transfers automatically as we transfer to these relations considered as acting on subquotients].

[Beware: If you have the relation R(x, y, z, ...), and specialize its first value like S(y, z, ...) = R(k, y, z, ...), then S will not respect Abelian group structure in itself; e.g., we do not have S(0, 0, ...) automatically, or that S(y1, z1, ...) & S(y2, z2, ...) \vdash S(y1 + y2, z1 + z2, ...). When using the fact that relations are closed under group operations on their input variables, one really must take into account ALL variables, and cannot consider any to be fixed non-variable parameters.]

Note that, in an Abelian category, we automatically have that our product types are also coproduct types [since any function f(x, y, ...) : X x Y x ... -> Z will satisfy f(x, y, ...) = f(x, 0, ...) + f(0, y, ...) + ..., thus being uniquely decomposed as a sum of maps from X into Z, Y into Z, etc]. We also automatically get a (covariant!) correspondence between the subobject slice category over A and the quotient object coslice category under A, for any A [both of these correspond to predicates on A; the former via inclusion of the subgroup where the predicate holds, the latter via quotienting to zero this same subgroup. Note that every quotient takes the form of quotienting some particular subgroup to zero, since whenever R is an equivalence relation, we have that R(a, b) can be combined with the reflexivity R(b, b) to give R(a - b, 0), or vice versa, so that an equivalence relation is fully determined by the unary predicate of what is equivalent to zero].

[The equivalence of products and coproducts holds in any category enriched over Abelian monoids; it is not necessary to demand full-on groups for this. However, the equivalence between subobjects and quotient objects does not hold merely for Abelian monoids, and does require we go to full-on groups. See more generally the concept of "Mal'cev theories".]

Indeed, as a result of the above, one great fact about the concept of an Abelian category, which is not made obvious in this particular presentation of its internal logic, is that the opposite category of an Abelian category is itself an Abelian category. [Remember, the notion of "internal logic" is up to taste; we could choose a different account for what the internal logic of Abelian categories is (that is, a different way of presenting them syntactically) which made this self-duality in the concept more apparent, directly axiomatizing coproducts and so on. However, the account we give here is the one which most directly emphasizes the connection to effective regular categories instead. For more on the duality between subobjects and quotient objects in an Abelian category and its generalization, see https://howsridharthinks.wordpress.com/2020/01/18/commas-and-cocommas/, to which there is some relation.]

Beware some ways in which Abelian categories do not act as one might expect from working with effective regular categories simpliciter. E.g., every slice category of an effective regular category is also effective regular, and effective regular structure is preserved by pullback. But not every slice category of an Abelian category is an Abelian category [the effective regular structure must persist in every slice, but the enrichment over Abelian groups needn't; for example, given two arbitrary maps over A, there's no reason to presume that the zero map between them creates a commutative triangle], and not even all Abelian category structure as does automatically exist in the slices is preserved under pullback.

Expanding on this last point, note that in an Abelian category, we can actually define coproducts of subobjects; that is, what one might call "unions" or "disjunction". This is given by taking P(x) v Q(x) v R(x) v ... to be "exists a, b, c, ..., such that x = a + b + c + ..., and P(a) & Q(b) & R(c) & ...". However, these unions are not preserved under pullback! Indeed, conjunction will not distribute over these disjunctions; rather than our predicate lattices being distributive lattices, they will in general satisfy only the weaker property of being modular lattices.

***

Incidentally, there is also terminology like "Ab-enriched", "preadditive", "additive", etc., categories for categories enriched over Abelian groups with some but not all the further structure of a full-on Abelian category. I actually hate all this terminology and can't keep it straight. I always want to use the term "Abelian category" to mean simply "category enriched over Abelian groups", and to have some other term for the full thing. Alas, though this is how Sridhar thinks, this isn't how the world talks.