---
title: "The Universal Cover of SO(3) is a Double Cover"
date: 2021-9-17
---
Let us prove that the universal cover of SO(3) is a double cover (thus, the homotopy group of SO(3) is $$\mathbb{Z}_2$$). This explains the famed Dirac belt trick and the concept of half-spin particles, among other things.

The proof is in three parts:

----

The first part is the observation that every non-identity rotation in three dimensions is a planar rotation by some angle around some axis. (This was famously proven by Euler, but we will establish it by modern methods.)

The observation we wish to establish is equivalent to saying that every rotation in three dimensions has 1 as an eigenvalue (as then the rotation decomposes into identity on an axis in the eigenspace for eigenvalue 1, and then a rotation on the 2D plane orthogonal to that axis). Put another way, if $$R$$ is our rotation, we need to establish that $$\det(R - 1) = 0$$. But $$\det(R - 1) = \det(R (1 - R^{-1})) = \det(R) \det(1 - R^{-1})$$ $$= \det(1 - R^T) = \det(1 - R) = (-1)^3 \det(R - 1)$$, and thus $$\det(R - 1) = 0$$.

(The same proof of course applies in any odd number of dimensions. We could also phrase it in terms of properties of the characteristic polynomial: If $$p$$ is the characteristic polynomial for $$R$$ and $$q$$ is the characteristic polynomial for $$R^{-1}$$, we have that $$\det(R) q(x) = p(1/x) (-x)^n$$, in $$n$$ dimensions. Thus, when $$R$$ and $$R^{-1}$$ have the same characteristic polynomial (as happens when they are each other's transpose), and $$\det(R) = 1$$, we may conclude $$p(1) = p(1) (-1)^n$$. If $$n$$ is odd, this tells us $$2p(1) = 0$$. In a characteristic where we may divide by $$2$$, we can conclude $$p(1) = 0$$, and thus $$1$$ is an eigenvalue.)

----

Now for the second part:

So SO(3) is almost the same as the following space: We consider a direction in 3D space (a value in the 2-sphere), and an angle strictly between 0 and 360 degrees by which to rotate around this axis ("clockwise looking down" from this direction, say). We could also specify an angle of 0 or 360 degrees, and in this case, we don't need to specify a direction. Rotation by an angle of 0 degrees is the limit of any sequence of rotations whose angles tend to 0 degrees, regardless of whether the directions converge to any direction, and similarly for rotation by 360 degrees.

Finally... We note the observation that rotation by angle X around direction D is the same as rotation by angle 360 degrees - X around direction -D. Each rotation has two antipodal representations of the above form.

If we don't identify these two antipodal representations, we get a space Q which is a covering space for SO(3). \[More generally, we could do the same thing for rotation around any number of dimensions of allowed axes, and everything from this second part onward will work the same.\]

It is easy enough to convince oneself it is a covering space, and a double cover at that: Each rotation has two disjoint preimages, and each of those preimages has a neighborhood which maps homeomorphically onto a neighborhood of the original rotation.

----

Now for the third part:

This covering space Q is clearly homotopic (indeed, homeomorphic) to the 3-sphere. But the 3-sphere is simply connected. Therefore, Q is the universal cover of SO(3).

Why is the 3-sphere simply connected? Because the 3-sphere is the union of two 3-disk hemispheres \[which are contractible and thus simply connected\] along a 2-sphere equator \[which is connected\].

Another way to see the 3-sphere is simply connected is by taking any loop within it, picking a point the loop doesn't hit, and unwrapping the 3-sphere minus that point into a contractible space homeomorphic to 3-space (through the stereographic projection, say). What if the loop hits every point on the 3-sphere (as a space-filling curve)? Because 3 > 1, there's enough degrees of freedom that we can pick some North Pole on the 3-sphere and nudge the loop to go around it instead of through it everytime it would've gone through it; thus, the loop is homotopic to one which does not go through the North Pole, and we can apply our same technique as just previously to conclude it is null-homotopic.

----

Putting together parts one, two, and three, the universal cover of SO(3) is a double cover.

It follows that the homotopy group of SO(3) is $$\mathbb{Z_2}$$; in general, given any path in X, its homotopies with one endpoint fixed and the other varying correspond to such homotopies at any preimage of the path in a covering space, by the path lifting properties. The homotopies with both endpoints fixed within X will end up corresponding also to homotopies with both endpoints fixed in its cover (because the only lifts of the identity path in X at the second endpoint would be identity paths in the cover, at one of the possible preimages). So the loops up to homotopy within X correspond to loops up to homotopy which are their preimages in the cover, with a designated preimage for the starting point. In particular, in a simply connected (i.e., universal) cover, this corresponds to choice of endpoint of the preimage. (TODO: Write this section out more clearly. I'm trying to say that the deck transformation group of the universal cover is the fundamental group. And for a double cover, this will be $$\mathbb{Z}_2$$.)

----

One particular way to represent this double cover explicitly is to think of vectors in 3D space as quaternions with real component 0 (i.e., purely imaginary), and the universal cover of SO(3) as unit quaternions [with rotation by angle $$\theta$$ around direction $$D$$ amounting to $$\cos(\theta/2) + \sin(\theta/2)D$$]. A value $$q$$ in the universal cover then acts on a value $$v$$ in 3D space to yield $$q v q^{-1}$$. Clearly, two unit quaternions induce the same rotation just in case they are antipodal; i.e., each others' negations. Thus, a double cover.

----

TODO: Add more on spinors and (s)pin group, generalizing this last segment. The general idea of thinking of reflections as acting by this conjugation, like in the last section, and rotations as composites of reflections.