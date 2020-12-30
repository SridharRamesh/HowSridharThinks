---
title: "Clifford Algebra"
date: 2020-12-18
---
I don't really care for Clifford algebra, but here's my attempt to understand the parts of it that aren't obvious anyway:

TODO: Write out why I don't care for them.

What's the value of bundling together dot product and cross product as even and odd components of a shared product? Well, this is the one thing I do care for, and it lets us see the higher-order Pythagorean theorem. TODO

Given the linear isomorphism between the exterior algebra and the Clifford algebra, how do we abstractly (basis-freely) interpret the Clifford product as acting on exterior powers? TODO

How do we abstractly (basis-freely, Clifford-freely) interpret the Pin and Spin groups? Well, the pin groups are something like series of reflections, and the Spin groups are series of even many reflections, but there's some identities that do and don't hold. TODO

Note that the (S)Pin(n) groups are the universal cover (i.e., simply connected, and thus identifiable with the path space) of (S)O(n) for n \geq 3, but not for n = 2 or less, and not in general when looking at (S)Pin(p, q) for a non-positive-definite form. So even though people often describe the (S)Pin groups in terms of these universal covers, talking about the belt trick for Spin(3) over SO(3) and such, and perhaps that's the motivation of looking at these originally, that's not quite what the Clifford algebra thing is always doing. It's some double cover but not the universal cover.

Note that there are two different Pin(n) groups, as Pin(n, 0) vs Pin(0, n), the two different sign conventions on Clifford algebras (do unit vectors square to 1 or -1?). There would be two different Spin(n) groups in the same way, but they turn out to be canonically isomorphic.

When I speak about "the" Pin group being the universal cover, this is maybe slightly confused, since as I just said there are two Pin groups. I believe this is possible because O(n) is itself not connected, so even though its component at identity receives a simply connected cover or some such thing, the Pin group overall also has some kind of action on swapping components that differs between the two Pin group constructions, or something.

The right way to think about Clifford algebras without presupposing a unit magnitude is presumably to impose the condition that A dot A = B dot B means A^2 = B^2, or equivalently, perpendicular values anticommute. (This is all over a field not of characteristic 2, of course, with square roots and so on, usual stuff, over the reals)

***

Clifford algebras are good for one thing: A nice construction of the universal cover of SO(n) for n >= 3. In general, the way this works is by starting with Clifford algebras over directions (so there is a god-given sense of a unit vector). And it will be useful to say, for a unit vector $$u$$, that $$u^2 = -1$$ rather than the positive convention. Then $$u u u = u^2 u = -u$$, while $$u v u = -u^2 v = v$$ for any vector $$v$$ perpendicular to $$u$$, so that being multiplied on both sides by $$u$$ acts as reflection in one dimension, upon vectors. We can then consider general compositions of these "Multiply by $$u$$ on both sides" actions, over all directions $$u$$, generating some subset of the Clifford algebra. This is essentially the pin group, and restricting to even index gives essentially the spin group. The point is that the Clifford algebra imposes certain identities on these compositions of reflection operations, but those identities are a little coarser than the identities of SO(n) itself (consider that $$u$$ and $$-u$$ impose the same reflection action). Indeed, we end up with a double cover of SO(n) [TODO: How to show this?].