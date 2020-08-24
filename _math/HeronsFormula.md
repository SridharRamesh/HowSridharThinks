---
title:  "Heron's Formula"
date: 2020-5-3
---
When I was young, in middle school, high school, and even college, Heron's formula was such a bother to me; the one formula in geometry I was aware of, which would be listed in each geometry textbook formula "cheat sheet", that I didn't know how to prove.

Well, here's the clean way to prove it:

To prove Heron's formula for a triangle, first, observe that by using coordinates parametrized by distance from the sides of the triangle, we can find a point equidistant from all sides; i.e., an inscribed circle [TODO: Expand on this].

Next, by considering the three vertices and the three points where the circle is tangent to the sides, along with the center, we can split our big triangle up into six triangles, in three groups of two mirror image triangles.

Next, observe that this means taking just one of the angles around the center from each of these pairs of triangles yields a sum of half a full revolution, 180 degrees. So the corresponding complex numbers taking radii of these triangles to edges along the side of the outer triangle multiply to a negative number. This means, letting x, y, and z be the distances from the points of tangency to the outer vertices, and r the radius of the circle, we get the complex number equation (r + ix)(r + iy)(r + iz) = some negative value. Examining the zero imaginary component of this, we find that r^2(x + y + z) = xyz, giving us a formula for the radius of the inscribed circle.

And then by multiplying this inradius by the semiperimeter, we get the area.

[TODO: All of this is is much better understood with a diagram. The above is quite possibly unreadable without one.]

[TODO: Connection to Brahmagupta's formulas for cyclic and non-cyclic quadrilaterals; for polygons in general? These are about cyclic polygons, not tangential polygons, but there's some kind of duality swapping these, and perhaps the effect of this duality on area is easy to see as well.]

[TODO: Connection to Cayley-Menger determinants, though these aren't really as nice as a higher-dimensional generalization as one might hope for. The things that make Heron's formula fully nice don't actually generalize in full nicety to higher dimensions.]

Another form of Heron's formula is like so: The squared area of a triangle with sides A, B, and C is 1/16 times $$(A^2 + B^2 + C^2)^2 - 2(A^4 + B^4 + C^4)$$. This is equal to $$S (S - A)(S - B)(S - C)$$, where $$S = \frac{A + B + C}{2}$$. We can see this to hold by thinking of area like so: The area of the triangle is half the area of the corresponding parallelogram, which in turn is given by $$ \vert A \times B \vert $$. But we have the higher-order Pythagorean theorem in the form of $$ \vert A \vert ^2  \vert B \vert ^2 = (A \cdot B)^2 +  \vert A \times B \vert ^2$$. Connecting that with $$ \vert C \vert ^2 =  \vert A \vert ^2 +  \vert B \vert ^2 + 2(A \cdot B)$$, we can express $$ \vert A \times B \vert ^2$$ in terms of $$ \vert A \vert ^2,  \vert B \vert ^2,  \vert C \vert ^2$$, and get our formula.