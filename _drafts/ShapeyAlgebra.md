---
title: "Shapey Algebra"
date: 2020-4-22
---
Key concepts: Preorders, (higher-)groupoids. As their intersection, setoids. As their union, (higher-)categories.

A preorder: You are given various points with names, and various edges between pairs of points. Edges come with an orientation; a left endpoint and a right endpoint. You are allowed to string them together into super-edges/paths, as long as the stringing together is coherent, in matching right endpoints to left endpoints (note: you cannot flip or turn edges). A "question" is like a pair of points, and an "answer"/"proof" is like a demonstration using the provided edges (perhaps some more than once) to go between these points.

This kind of diagrammatic reasoning models inequalities/partial orders.

A setoid: Same thing, except our edges no longer come with any orientation; you can place them into paths any which way. This is simpler in one sense (don't need to track orientation information) but also more complex in some sense (we have available to us the extra "move" of flipping edges we are given).

This kind of diagrammatic reasoning models equations/equivalences.

A groupoid: Same thing as a setoid, except we add 2d tiles as well, whose boundaries are loops made by the 1d edges. The edges now have names, just like points do, so that when tiles are placed next to each other, they have to match up along the corresponding edges. The 2d tiles themselves don't need to be given names, since names are of no use except to impose these kinds of matching conditions, and we don't have 3d blocks (yet) whose 2d faces would have to match. However, it is an obvious generalization to imagine having blocks of every dimension, and at that point, everyone should be given a name. We are allowed to turn and flip the edges and tiles and everything however we want. We can also think of them as squishy things; the lengths and angles and straightness doesn't matter, just the connectivities, when we put together diagrams.

A question now can be a pair of points to string edges between, or two paths between points/a loop of edges to try and fill with tiles with no holes. [Or, in high dimensions, any sphere to fill solidly as a ball]. The lowest-dimensional case of this, also, is the question of whether there is any point at all, filling the trivial (-1)-dimensional hole; this question was there as well for setoids and preorders, but sort of trivial so I didn't mention it before. Actually, more generally, questions are things like "Is there a diagram of this sort, such that there's no diagram of this sort, such that there is a diagram of this sort", etc, but nevermind that for now. The main thing is the business of being given a hole that may can be filled, and showing that it can be filled, given certain pieces to start. These are the algebraic (i.e., quantification-free) proofs.

Caveat to be aware of: Edges and paths basically act the same in all ways, there's really no harm in ever thinking of an edge as standing in for a longer path, EXCEPT, there's one thing edges can naively do that paths can't. Specifically, if you have an edge on the boundary of a tile, and its two endpoints are the same point, and you turn the tile around, it gets to match against itself along that edge, whereas a long path made of multiple edges may not line up against itself when turned around in this way. We really don't want this complication, we want to think of edges and paths as meaning the same thing, so we introduce the idea that a 1d edge has a 1d name that turns and flips as it does, and a 2d tile has a 2d name and so on. We can imagine an edge has an asymmetric 1d pattern on it, a 2d tile has an asymmetric 2d pattern on it, and so on. All these things could be represented with colors, if one likes. Like the piece has a bunch of flags all uniquely colored.

Of course, if one WANTS a certain piece to have certain symmetries, one can go ahead and impose those too, but whatever.

We can do algebra with these sorts of things, 2d algebra, higher dimensional algebra. What equations follow from what equations. [Illustrate with pinwheel]

Any polygon can be broken down into a bunch of triangles, and more generally by flag decomposition, we can represent everything using simplicies of the appropriate dimension, if for some reason we want to have a simpler theory in the formalities. But we are working now on an informal level; the time for formality is later. (If we were being very formal, I would note conditions like that we are definitely allowed to have infinitely many pieces, but each piece should be finite, etc. None of this really matters for now, except to say these conditions and corresponding concepts are all things we are free to think about. I am trying to convey the preformal concepts). Of course, this breaking down of tiles into simplicies introduces new points and edges and so on. Which means we are being given a different groupoid? Well, no, and this brings us to starting to think about the question of when two different groupoids should count as equivalent.

Just as for fractions, we have a non-syntactic, non-presentational notion of equivalence, coarser than the obvious presentational one. There's an obvious presentational notion of equivalence, where a set of pieces counts as the same as another set if the only thing changed is some renaming (obviously, the specific names shouldn't matter). Illustrate this with setoids and preorders as well. Note how one setoid/preorders may be renamed into another one in perhaps multiple ways; parallel inequivalent equivalences.

But there's also a coarser notion that's usually of interest. There's multiple ways to say it, but one way is this: if we start with some bunch of pieces A, then add new pieces to extend this to B, we say this made no change if, every hole in A that can be filled in B, can also be filled in A, and the two fillings themselves make a sphere which is filled in in B. [TODO: Motivate this; but basically, everything in B is equivalent to something in A]

Of course, this notion needs to be made symmetric; the right notion is that A and B are equivalent if they have some simultaneously common extension C. This notion is also reflexive, and will turn out to be transitive as well.

[This notion of equivalence turns out to be the same as saying, any contractible blob should be replaceable by any other contractible blob.]

More generally, we have the concept of a homomorphism. A basic homomorphism is any way of extending A into B by adding new tiles. A homomorphism in general is this, up to the notion of equivalence we just talked about (so you can have a homomorphism between things whose tile sets are not a priori related).

[TODO: Illustrate all this for preorders/setoids as well].

All of this is well understood for groupoids, which as noted, have no notion of orientation. More generally, we can add back the notion of orientation, and demand at every dimension that things can only be thought of as connecting into larger blocks when the orientations line up correctly; pieces can't be flipped or turned but come with specified left, right, top, bottom, in, out, etc. But formalizing this is actually quite tricky in full generality allowing arbitrary dimensions. People have done it in various ways, but no one quite has settled on one of these ways as the right clean simple way to do it, or even really understands how all the formalizations related to each other, or whatever. But as a preformal concept, it's pretty simple. It's just the idea of our groupoids (which are completely well understood formally; even here, there's multiple ways to formalize them, but everyone perfectly well understands they're the same, and some of these formalizations are relatively graspably simple), combined with the orientability idea of our preorders (which are extremely simple to formalize and you've already used them a million times, just not thought about them as shapes).

Again, if you go the other way and look to find the intersection of the two ideas, the groupoids which are also preorders, these are the setoids we were talking about at the beginning.

Note that homomorphisms naturally bundle up into preorders, when we just pay attention to existence, and then into higher categories if we start looking at further questions.

Note that most people do not think of these structures this way. But I do, now. I never had to mention associativity laws or anything above, which is what most people spend so much time discussing when talking about groups, categories, etc. Here, it is subsumed into the presentational framework, as it should be.

***

What is meant by a path from A to B in groupoid/tileset T: A way of adding a new edge from A to B, plus adding other stuff as well, such that the result is a conservative extension of T.

What is meant by an equivalence between two such paths: A way of taking the union of these extended tilesets, adding a new tile between the two designated new edges from A to B, and then extending this further to be a conservative extension.

Etc.

***

It is simplest to start off just discussing 2d groupoids, not introducing the notion of equivalence or homomorphism between them, and just directly defining path and (handwavily) 2d blob, and using these to do 2d algebra for a while. The notions of equivalence and homomorphism are only needed for more sophisticated things, and certainly must be gotten to eventually to understand the essence of group theory, but we can start out without them to just explore the quantification-free component of reasoning about groups (it's simple also to use homomorphisms in the sense of tile extensions, which does not demand quantification reasoning, but new homomorphisms between previously given groups demand talking about equivalence or some such [quantifying over the entire domain], and this is no longer simple).

***

Incidentally, there's nothing wrong of course with also studying these things with attention paid to distinctions of presentation; counting number of edges or such things. This indeed comes up fruitfully in talking about like Euler's polyhedron formula at that level and so on. But it is also useful to understand them presentation-freely/up to equivalence, to think of there being no distinction between simple cells and aggregates, to focus on compositionality, etc, and that is the concept we mean to highlight when we reason categorically/groupoidally/(po)setally/etc.

***

The names "groupoid", etc, are all archaic opaque accidents of history. Mention etymology but also mention that people are free to use whatever names they like personally. These names also make it look like certain notions are more basic than others in ways that needn't be correct perspective (privileging group over groupoid, set over setoid, set over poset over preorder, category over higher category, etc).

***

Ordered categories, and perhaps even ordered 2-categories, are still at a level where things are reasonably formalizable and graspable. Note that basically everything people do with categories might as well be done with ordered categories.

***

Extended discussion of the problem of definite descriptions, "the", equality, etc, in this context. Keep in mind also issues like that two edges between A and B may be equivalent as edges simpliciter (using automorphisms of A and of B), but not equivalent as edges between A and B specifically.

***

TODO: Lots of drawings, colorful diagrams.

***

Should do one post on 2d groupoids, as simply as possible. One post on preorders. One post on setoids. One post sketching higher groupoids. Then one post relating all these, hinting at higher categories. Then one post talking about issues like equivalence, homomorphism, etc, and all their complications, in this generality and also in specific for each of these. Maybe. Certainly, 2d groupoids, preorders, and setoids each deserve a simple post on their own, that could be swallowed even when not ready to swallow the complications. People should be able to see the pinorder as a bit of 2d equation wrangling without having to be able to grasp homomorphism/equivalence/higher dimensions/etc.

***

In a groupoid diagram, everything is willy-nilly. In an ordered category where, say, 1-cells go left to right and 2-cells go top to bottom, there should be no vertical edges, and on every polygon, the two paths from leftmost to rightmost point should be such that they proceed strictly left to right, no zagging back, and a particular one always higher or equal to the other, no crossing [e.g., no figure 8s interpreted as crossing domain and codomain paths of a 2-cell]. Actually, we probably shouldn't allow tiles to have repeated points on their boundary except by using the same name twice; that is, a tile should always be represented by a simple polygon, so to speak.

***

Everything should be drawn with a bit of automatic thickness in every dimension; thus, a point is already a line segment is already a square, etc. A point is an edge between itself and itself, and is also a square between those identity maps, and an edge is a square between itself composed with identity at its codomain and identity at its domain composed with itself, and so on. We can think of this as having extrusion operations for each dimension, available to act on everything in a suitably coherent way (and also repinchings? But perhaps this is unnecessary. Just keep in mind that when the question arises as to whether a particular hole can be filled in, the hole may need to be extruded to accommodate fillings that use this extrusion. But it's simpler to just imagine everything is automatically extruded in every dimension anyway.).

A path A B C D ... is really a big old chunk of as much identity as desired, then A, then a big old chunk of as much identity as desired, then B, etc. And so on for diagrams of any dimension.

Maybe to avoid Eckmann-Hilton difficulty and keep everything suitably weak, we should think of a diagram as coming with a coherent GLOBAL ordering all coordinates in all dimensions; . (And when a thing is thought of as extruded, its two coordinates along any dimension are infinitesimally close, in the sense that nothing comes strictly between them.). This can syntactically distinguish the different ways that two-cells between identity 1-cells might be composed with each other. But we need some rules that allow things to swim within identity blocks; i.e., so that identity composed with f composed with identity with one set of coordinates for f can become equivalent to identity composed with f composed with identity with the coordinates for f moved around? Hm, at this point the extrusion stuff doesn't seem convenient or to take care of everything anyway, and we probably just need rules for inserting identity blocks. Although... Maybe swimming can be achieved using the right way of thinking about extrusion and pinching in a row? This will all seem quite babbling in the morning.

Consider how extruding 1-cell f into a square can be seen as giving a map between id . f and f . id. This is a swimming map. This relies on extrusions of the same cell along any which dimension counting as the same thing, which makes sense. [We're dealing with 2-categories, not double categories, so vertical and horizontal identities are the same, so to speak]

For any cell you have, and any blob shape, you automatically also have this piece x that blob shape. Thus, piece x point = existing piece, piece x edge = extruded piece, piece x solid triangle (equivalence between point and edge) = equivalence between existing piece and extruded piece, etc.

Might also be simpler to say, any piece can be extruded into piece * cone(arbitrary shape). Thus, the apex of the cone corresponds to the original piece, and we do not need to define here the property of being a blob in general.

***

Instead of extrusion principles, perhaps the important thing is really resizing principles: a morphism of length M can be turned into a morphism of length N, and so on, so long as we don't turn positive into zero (but we can turn zero into positive). This is what ordinary composition does: n-ary composition turns length n into length 1. The resizing doesn't matter until you want to think about things like how different resizings interact.

When we have two loops F, G : A -> A, their composition can't just be drawing both loops on the same point. We need some different information to disambiguate the order of the composition. The composition must amount to untying these into : A -> B and : B -> A morphisms, for abstract B, in one of the two ways, and then joining them at the B. And something like this is important to explaining what goes on with the Eckmann-Hilton thing as well. A loop bulges out from its border; a 2d square whose border is all identity bulges out as well. Ramble, ramble…