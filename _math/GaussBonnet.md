---
title: "Gauss-Bonnet"
date: 2020-8-8
---
Euler characteristic is the sort of thing which adds up as you combine regions (combining them not in the union sense, but in the addition sense. So $$F(A \cup B) + F(A \cap B) = F(A) + F(B)$$).

Also adding up in the same way, albeit this is less obvious perhaps, is "How much does it feel like I turn, as I walk around the outside of this region?". Aka, border geodesic curvature. What's non-obvious here is the way border interacts with intersection and union. [Also, the border here needs to be understood as including not just smooth arcs, but also potentially sharp turns at points. Even two smooth figures may, when unioned, result in a figure whose border has sharp turns.]

Therefore, the difference between Euler characteristic and border geodesic curvature (in suitably scaled common units) also adds up in the same way. This is Gaussian curvature. For an ordinary 2d blob, we say the Euler characteristic is 1, and it feels like we make 1 full revolution as we walk around it, and taking the difference in these units, the Gaussian curvature is zero.

Note that you can have non-zero Gaussian curvature concentrated at a point, as at the corners of a cube, each with Gaussian curvature 1/4 (in an infinitesimal blob region of the point, it feels like we take 3/4 of a revolution as we walk around it, though the Euler characteristic is 1). I can't think of how to get non-zero Gaussian curvature concentrated on a 1d edge.

At any rate, this is the Gauss-Bonnet theorem: Gaussian curvature + border geodesic curvature = Euler characteristic, where all three of these are integrals of the appropriate type. Euler characteristic comes out to 1 on a blob, border geodesic curvature only depends on the border, and Gaussian curvature comes out to 0 on a flat blob but not necessarily on all blobs.

***

As part of all this, it's useful to keep in mind that a smooth non-self-intersecting loop has turning number 1, in the sense that walking around it feels like making 1 full revolution. Why is this? Let T(a, b) for a <= b be the angle of the vector from the point at time a to the point at time b, with T(a, a) being the angle of the tangent vector at time a. Note that for T(a, b) to be well-defined, we need that the points at time a and at time b are never the same for different a and b; hence, the non-self-intersecting. This gives a continuous map from a triangle (0 <= a <= b <= 1 as the domain for a and b) to the circle of angles. In particular, along the diagonal a = b from (0, 0) to (1, 1), we get the turning number. But this is homotopic to what we get by moving from (0, 0) straight up to (0, 1) and then straight over to (1, 1). So turning number must change smoothly as we morph between these two paths from (0, 0) to (1, 1), while always being an integer overall; thus, these two turning numbers must be equal.

So let us examine how much we turn along the straight paths from (0, 0) to (0, 1) and then to (1, 1).

Without loss of generality, we can assume that we start at time 0 at the lowest point on the loop [which must exist by continuity on a compact domain]. At the lowest point, the tangent must be horizontal, and without loss of generality, we can call its orientation "left". So T(0, 0) points to the left. As we swing along the loop to time 1, we must end up now coming back to our starting point from the other side, on the right; T(0, 1) points to the right. But T(0, x) must never point down, since the point at time 0 was the lowest point on the loop. So the angle swings from left to right while never pointing down, which means a total swing of 180 degrees clockwise.

Thus, the turning from (0, 0) to (0, 1) is 180 degrees clockwise. By the same argument, the turning from (0, 1) to (1, 1) is 180 degrees clockwise [indeed, T(x, 1) = the antipode to T(0, x), so this is just the same turning process carried out again on the antipodes]. Adding these together, we get 1 clockwise revolution.

Presumably this same fact can also be demonstrated by using the Gauss-Bonnet theorem as above and integrating Gaussian curvature, using a decomposition of our shape into lots of little bits with zero curvature. That is, we Jordan curve theorem our loop into the boundary of a region that we fill with these zero curvature bits.

***

Combinatorial analog of Gauss-Bonnet: Imagine a network of points, edges, and faces, with internal angles assigned wherever one edge meets another, and a turning amount assigned to each oriented edge (turning by reverse amount in the reverse direction).

We define the geodesic curvature at a point as the sum of its interior angles and the geodesic curvature around the border of a face as the sum of its exterior angles, then define Gaussian curvature at a point or face as one revolution minus the geodesic curvature.

If we sum the Gaussian curvature at all points and all faces and add to this the sum of the exterior angles around the entire boundary, we should get the Euler characteristic.

One proof is by attaching exterior faces, Barycentrically dividing each face into triangles and assigning all face curvature to the barycenter, also adding a point inside each edge to make its turning into an exterior angle, then proving the reduced result for closed surfaces made of triangles with all curvature concentrated at points. (We can also just as well blow points up into faces to move all curvature into faces)

But I'll just spell it out directly in full complexity:

On each face, we have that the sum of its oriented edges' turns, plus the sum of its external angles (i.e., 1/2 - its internal angles), plus the face's Gauss curvature, is 1.

On each internal vertex, we have that the sum of its internal angles, plus its Gauss curvature, is 1. On each border vertex, we have that the sum of its internal angles, plus its external angle, is 1/2.

Adding these together over all faces and all vertices, every internal edge is double counted with both orientations and cancels out. Every internal angle is double counted with opposite signs and cancels out. We get that the sum of face Gauss curvature, internal point Gauss curvature, boundary external angles, boundary edges' turns, and half the sum of "face-lengths", is F + V_{internal} + V_{border}/2.

Face length is number of angles in a face; equivalently, the number of edges in the face. Adding this up over all faces, we double count all internal edges, but single count border edges. So half the sum of "face-lengths" is E_{internal} + E_{border}/2.

Thus, we've demonstrated that the sum of face Gauss curvature, internal point Gauss curvature, boundary external angles, and boundary edges' turns is F + V_{internal} + V_{border}/2 - E_{internal} - E_{border}/2.

This differs from Euler characteristic by half of the difference between V_{border} and E_{border}. But there are the same number of vertices and edges on the boundary, so this difference is zero, so we're done.

***

Euler characteristic involves a simple contribution for points, edges, and faces.

Gaussian curvature makes contributions for faces and internal points.

The remaining geodesic curvature of the boundary makes contributions for border points and border edges.

It's interesting that we can do the accounting in this different way. We don't have internal edges contribute at all, and change the contribution of a point based on whether it is internal or external, which is to say, we change their contributions based on whether we do or don't include faces next to them, and in all cases the actual contribution is a different value than before, but still we get the same total.

***

We can define the Gaussian curvature of a large region as just the sums of these contributions from the faces and internal points within it. This is easiest to discuss if Gaussian curvature never concentrates at a point, in which case, this is a straightforwardly additive function on regions, and we've just proved above that this additive function is equal to the difference between Euler characteristic and border geodesic curvature; thus, that this difference is additive.

***

None of the above discusses Gaussian curvature in the explicit sense as the determinant of the shape operator, but the relationship between that and turning number in the infinitesimal region around a point should be straightforward.