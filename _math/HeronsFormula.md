---
title: "Heron's Formula"
date: 2020-5-3
---
When I was young, in middle school, high school, and even college, Heron's formula was such a bother to me; the one formula in geometry I was aware of, which would be listed in each geometry textbook formula "cheat sheet", that I didn't know how to prove.

Well, here's the clean way to prove it:

To prove Heron's formula for a triangle, first, observe that by using coordinates parametrized by distance from the sides of the triangle, we can find a point equidistant from all sides; i.e., an inscribed circle [TODO: Expand on this].

Next, by considering the three vertices and the three points where the circle is tangent to the sides, along with the center, we can split our big triangle up into six triangles, in three groups of two mirror image triangles.

Next, observe that this means taking just one of the angles around the center from each of these pairs of triangles yields a sum of half a full revolution, 180 degrees. So the corresponding complex numbers taking radii of these triangles to edges along the side of the outer triangle multiply to a negative number. This means, letting x, y, and z be the distances from the points of tangency to the outer vertices, and r the radius of the circle, we get the complex number equation (r + ix)(r + iy)(r + iz) = some negative value. Examining the zero imaginary component of this, we find that r^2(x + y + z) = xyz, giving us a formula for the radius of the inscribed circle.

And then by multiplying this inradius by the semiperimeter, we get the area.

[TODO: All of this is is much better understood with a diagram. The above is quite possibly unreadable without one.]

***

This all generalizes to $$N$$-gons, like so:

Tangential polygons:

[TODO: Again, illustrate all the following with diagrams]

Consider $$N$$ distinct points around a circle of positive radius, arranged such that no closed semicircular arc contains all of them. This amounts to saying that the angular distances between them, measured as we go around the circle in some consistent direction, are all strictly between zero and half a revolution, while summing to one full revolution.

With each of these points, we can associate a half-plane, bounded by the corresponding tangent line and containing the center of the circle. The intersection of all these half-planes will be the interior of a convex $$N$$-gon, whose edges lie along the tangent lines and whose vertices are the intersections between consecutive tangent lines. (Had all the points lied on a single semicircular arc, this intersection would be unbounded; thinking of the semicircular arc as the bottom half of the circle, this intersection would include all points above the circle).

In this case, we say the $$N$$-gon is a tangential polygon, inscribed by the circle (aka, circumscribing the circle).

Now as we go around in order, there are $$2N$$ points of interest, alternating between the N points of tangency and the $$N$$ vertices of our $$N$$-gon. The $$2N$$ line segments from the points of tangency to the adjacent vertices of our $$N$$-gon are called the tangent lengths (well, we can apply this name to the lengths of those segments as well, of course).

To each tangent length, we can associate a right triangle one of whose legs is that tangent length and the other leg of which is the radius of the circle to the corresponding point of tangency. This decomposes our entire $$N$$-gon into $$2N$$ many right triangles. Note that the two right triangles that meet at any vertex of our $$N$$-gon are mirror images, as they have the same opposite leg length (the radius of our circle) and the same angle at that vertex (since the center of our circle will lie on the angular bisector of our $$N$$-gons at each of its vertices, since it is equidistant between the corresponding tangent lines).

Thus, taking every other of these right triangles as we go around the circle, their angles around the center of our circle comprise half a revolution. In each case, the complex number which takes one leg of the right triangle (a radius of the circle $$R$$) to the other leg of the right triangle (a tangent length $$T$$) is given by $$R + iT$$. So the product of $$(R + iT)$$ over all tangent lengths $$T$$ will be a negative real number.

This gives us an inequality (the real component of this product is negative) and an equation (the imaginary component of this product is zero). Let us focus on this equation. Rescaling each factor to be $$(1 + iT/R)$$, the imaginary component of the product is given by an polynomial in $$1/R$$ whose coefficients are all of odd degree, extending from degree $$1$$ up through the largest odd degree upper-bounded by $$N$$. Multiplying through by the appropriate power of $$R$$, this becomes a polynomial of degree $$\lfloor (N - 1)/2 \rfloor$$ in $$R^2$$.

This gives us a formula for $$R^2$$ in terms of the tangent lengths. An affine formula when $$N$$ is $$3$$ or $$4$$, a formula as the solution to a quadratic equation when $$N$$ is $$5$$ or $$6$$, etc. In jargon, we say we have a formula for the inradius of a tangential polygon in terms of its tangent lengths.

Note also that once we know the inradius, we know the area of the polygon, as the area of each right triangle is the inradius times the tangent length over two. Thus, the area of the entire polygon is its inradius times half the sum of its tangent lengths, or equivalently, its inradius times its semiperimeter.

Speaking of which, suppose we know the edge lengths of the $$N$$-gon rather than its tangent lengths. Can we easily extract the tangent lengths? Well, the edge lengths are simply the sums of consecutive tangent lengths (after identifying each pair of twin tangent lengths as just one value). That is, the $$N$$-periodic sequence of edge lengths is the application of the operator $$1 + Shift$$ to the $$N$$-periodic sequence of tangent lengths. This operator is invertible when $$N$$ is odd, by noting that $$(1 + Shift)(1 - Shift + Shift^2 - \ldots + Shift^{N - 1}) = 1 + Shift^N = 2$$, so that the inverse is $$(1 - Shift + Shift^2 - \ldots + Shift^{N - 1})/2$$.

This operator is not invertible when $$N$$ is even, as the corresponding calculation results in $$1 - Shift^N = 0$$, demonstrating that $$1 + Shift$$ is a zero divisor. The kernel of this operator is of course $$N$$-periodic sequences where each value is the negation of the adjacent values. When $$N$$ is even, the range of this operator is sequences for which the sum of entries at indices of one parity matches the sum of entries at indices of the other parity. Given such a sequence of edge lengths $$S_0, S_1, S_2, \ldots$$, we can recover the possible preimage sequences of tangent lengths as $$K, S_0 - K, S_1 - S_0 + K, S_2 - S_1 + S_0 - K$$, etc, for arbitrary $$K$$.

Thus, we have an area formula for tangential polygons in terms of their tangent lengths and extracting roots of polynomial equations. The relevant polynomial has degree $$\lfloor (N - 1)/2 \rfloor$$, and when $$N$$ is odd, we can express this all in terms of edge lengths instead. Heron's formula (and our argument for it at the top of this post) is the special case of this for $$N = 3$$.

***

What about cyclic polygons? That is, suppose we took our N points of tangency and directly made a polygon with them as the vertices (the polygon circumscribed by the circle, rather than the polygon the circle is inscribed in)? Do we get an area formula for those? There is Brahmagupta's formula for $$N = 4$$. How does that relate? [TODO]

Clearly, there is a one-to-one correspondence between cyclic polygons and tangential polygons (in either case, we can find the center of the circle [intersection of angular bisectors from a tangential polygon or intersection of perpendicular bisectors from a cyclic polygon] and the points of tangency [directly given in a cyclic polygon, and the tangencies from the circle to the edges in a tangential polygon], and then the intersections of the tangent lines, and now have both the vertices of the cyclic polygon and the vertices of the tangential polygon).

Hm, except, in this duality, be careful, the same polygon might in a degenerate sense correspond to multiple "inscribed" circles (the exscribed circles, as in the excircles of a triangle), which would induce multiple cyclic polygons yielded from a tangential polygon. This is because angular bisectors actually come with two perpendicular choices. But the right one to pick is the one which cuts into the convex polygon, not the one which lies entirely to its side, or some such thing.

***

Another form of Heron's formula is like so: The squared area of a triangle with sides A, B, and C is 1/16 times $$(A^2 + B^2 + C^2)^2 - 2(A^4 + B^4 + C^4)$$. This is equal to $$S (S - A)(S - B)(S - C)$$, where $$S = \frac{A + B + C}{2}$$. We can see this to hold by thinking of area like so: The area of the triangle is half the area of the corresponding parallelogram, which in turn is given by $$ \vert A \times B \vert $$. But we have the higher-order Pythagorean theorem in the form of $$ \vert A \vert ^2  \vert B \vert ^2 = (A \cdot B)^2 +  \vert A \times B \vert ^2$$. Connecting that with $$ \vert C \vert ^2 =  \vert A \vert ^2 +  \vert B \vert ^2 + 2(A \cdot B)$$, we can express $$ \vert A \times B \vert ^2$$ in terms of $$ \vert A \vert ^2,  \vert B \vert ^2,  \vert C \vert ^2$$, and get our formula.

I'm not sure this second approach to Heron's formula, using the higher-order Pythagorean theorem, generalizes to $$N$$-gons so naturally, except in the sense that we can decompose any $$N$$-gon intro triangles using diagonal lines and then sum up Heron's formula over each of these triangles, giving a formula for its area in terms of edge lengths and diagonal lengths. [TODO: There is this formula area = 1/2 * sqrt((pq)^2 - (ac - bd)^2) for area of a tangential quadrilateral, with p and q as diagonal lengths and a, b, c, d as edge lengths. Think about that.]

***

[TODO: Connection to Cayley-Menger determinants, though these aren't really as nice as a higher-dimensional generalization as one might hope for. The things that make Heron's formula fully nice don't actually generalize in full nicety to higher dimensions.]

***

A property Wikipedia notes: "Let one n-gon be inscribed in a circle, and let another n-gon be tangential to that circle at the vertices of the first n-gon. Then from any point P on the circle, the product of the perpendicular distances from P to the sides of the first n-gon equals the product of the perpendicular distances from P to the sides of the second n-gon.". TODO: Think about this. Does this relate to our distance-product formula at [3blue1brown: The Wallis Product and the Sine Product]({{ site.baseurl }}{% link _math/3b1bSineProduct.md %})?