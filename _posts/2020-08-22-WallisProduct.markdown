---
layout: post
title:  "A Simple Geometric Proof of the Wallis Product"
---
The $$n$$-dimensional unit sphere (in the indexing in which the Earth is a 3-dimensional sphere) has an inner volume which is its surface area divided by $$n$$ (by considering each tiny patch of its surface as the base of a figure tapering down to its center), and at the same time, by the argument that projecting two dimensions outwards to the enveloping "cylinder" is area-preserving (stretching latitudinally and longitudinally in precise cancellation, as in the Lambert map projection), we find that the unit $$n$$-sphere's surface area is $$\tau$$ times the unit $$(n - 2)$$-sphere's volume ($$\tau$$ here being the circumference of a unit circle).

[Footnote: Here, whenever I say “(inner) volume”, I mean in the sense appropriate to the number of dimensions, and similarly for “surface area”; thus, for example the “surface area” of a circle is its perimeter, and the “volume” of a circle is its area]

Putting these last two facts together, the unit $$n$$-sphere's volume is $$\frac{\tau}{n}$$ times the unit $$(n - 2)$$-sphere's volume.

Letting $$V(n)$$ be the unit $$n$$-sphere's volume, and letting $$D(n) = \frac{V(n + 1)}{V(n)}$$, we get that $$\frac{2}{3} \times \frac{4}{5} \times \frac{6}{7} \times \ldots \times \frac{n}{n + 1}$$ comes out to $$\frac{V(0)/V(n)}{V(1) / V(n + 1)} = \frac{V(0)}{V(1)} D(n) = \frac{1}{2} D(n)$$. And of course $$\frac{2}{1} \times \frac{4}{3} \times \frac{6}{5} \times \ldots \frac{n}{n - 1}$$, with as many factors, is just this same thing times $$n + 1$$. Putting these together, the Wallis product up through $$\frac{n}{n + 1} \times \frac{n}{n - 1}$$ is $$\frac{n + 1}{4} D(n)^2$$.

But what are the asymptotics of that $$D(n)^2$$ factor? Well, our recurrence $$V(n) = \frac{\tau}{n} \times V(n - 2)$$ is equivalently the recurrence $$D(n - 2) \times D(n - 1) = \frac{\tau}{n}$$. So both $$D(n - 1) \times D(n)$$ and $$D(n) \times D(n + 1)$$ are $$\sim \frac{\tau}{n}$$. If we just knew that $$D(n)$$ was monotonic in $$n$$, then $$D(n)^2$$ would be between those two and thus $$\sim \frac{\tau}{n}$$ itself. Given our previous paragraph's conclusion, the Wallis product would then come out to $$\frac{\tau}{4}$$ (i.e., $$\frac{\pi}{2}$$). Ta-da!

...Well, one lemma to establish, and then we can ta-da. Let's see why $$D(n)$$ is monotonic in $$n$$:

Considering the $$(n + 1)$$-sphere's volume in terms of its cross-sectional $$n$$-spheres, we have that $$D(n)$$ is twice the average value of $$f(x)^n$$ as $$x$$ runs from $$0$$ to $$1$$, where $$f(x) = \sqrt{1 - x^2}$$ is the cross-sectional radius at height $$x$$ above the center of a unit sphere. And since $$f(x)^n$$ is a decreasing function of $$n$$ (since $$f(x) \in [0, 1]$$), thus so is $$D(n)$$.

Now we are done. Ta-da!

This is actually related to Wallis's original proof (which was done not in terms of spheres but in terms of some messy integrals; even messier perhaps by virtue of being worked out before the general integral calculus had been developed!), but that is as this seen through a glass very darkly. I would be very curious to see if anyone has written on seeing the Wallis product this way in terms of sphere volumes before.