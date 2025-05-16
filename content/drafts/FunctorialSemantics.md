---
title: "Functorial Semantics"
date: 2021-1-1
---
TODO: Scratch notes for a post on Lawvere theories, monads, functorial semantics, categorical logic, etc. Taken from a Twitter DM conversation.

A Lawvere theory, in the sense I like to think of it though others take different views, is just a category with products. What kind of products? All finite products? All small infinitary products? Well, it's up to you, these are all different notions we can consider.

This is considered to describe a theory of some kind of algebraic structure (like the theory of groups or the theory of rings or what have you). A functor from this Lawvere theory to Set preserving all those products is then a model of this theory, and natural transformations between such functors are homomorphisms between such models. More generally, one can consider any product-preserving functor to any category C to be a C-valued model of the theory; it's not necessary for C to be Set. [This is called "functorial semantics", but names are just jargon]

If we have some set of objects X such that all the objects are generated from X by appropriate products, we can think of this as really a theory on X many sorts. Very frequently, people intend for there to be a single object, of which all other objects are product-powers (as in the theory of groups, rings, etc, which are all single-sorted).

Any theory with some sorts/datatypes (corresponding to our generating objects X), and some operations of appropriate arity (the arity corresponding to the arities of products, and the operations corresponding to the morphisms of the category), and some universal identities between compositions of such operations (corresponding to the equations between parallel morphisms of the category) has a representation as such a Lawvere theory, and conversely, any such category with products gives rise to a theory in the more familiar sense of writing down sorts for its objects, operations for its morphisms, equations, etc, blah blah. We might say two theories should be considered fundamentally the same, only presented differently, if they give rise to the same category in this way.

This all can be generalized a bit beyond just product structure, but requires a bit more care for that, but I won't bother with that for now.

The relationship of Lawvere theories to monads is this:

A monad M on Set gives rise to a Kleisli category, where the objects in the Kleisli category are the same as the objects in Set, and a morphism in the Kleisli category from A to B amounts to a morphism from A to MB in Set, with composition in the Kleisli category being the only thing it possibly could be at this level of abstraction.

Since the objects in Set are precisely the set-sized (aka, "small") coproduct-powers of 1, it will follow that the same property holds for the Kleisli category of any monad. Taking the dual category of the Kleisli category, there is one object which generates all the other objects as product-powers. Thus, it is a single-sorted Lawvere theory with set-sized products.

Conversely, given any single-sorted Lawvere theory with set-sized products, we can see it as arising from a monad on Set in this way. There is a one-to-one correspondence.

In that way, monads on Set correspond to single-sorted Lawvere theories with set-sized arity operations.

The Eilenberg-Moore category of the monad is then the same as the category of models of this theory and homomorphisms between them.

We can think of the monad as assigning to each set S the underlying set MS of the free structure of whatever sort on S many generators.
So, for example, the list monad will correspond to the theory of monoids, as the free monoid on S has as its underlying set the set of lists from alphabet S.