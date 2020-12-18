---
title: "Transfinite Stable Marriage"
date: 2020-12-17
---
A straight line is the shortest path between two points. Why is that?

Well, for any path between points $$A$$ and $$B$$ we can consider projecting it onto the line through $$A$$ and $$B$$. That is, each infinitesimal movement $$dv$$ along our path can be decomposed into $$dx + dy$$, where $$dx$$ is its component parallel to the relevant line and $$dy$$ is its component perpendicular to the relevant line. (Don't let my use of this notation fool you, this works just as well in three or higher dimensions, $$dy$$ can be anything perpendicular to the relevant line). When we project this to just $$dx$$ we make it smaller (if changed at all), as any leg of a right triangle is smaller than the hypotenuse (if different at all).

So any path between two points can be constrained to lie on the line between those points, and in so doing becomes shorter (if changed at all).

The next thing to note is fairly obvious, but let us note it all the same: Even among paths in one-dimension, the shortest one is the one which simply marches forwards directly from start to finish, while longer ones dither around making backwards motions that later must be cancelled out by further forwards motions. The shortest path is the direct straight path, not one that goes sometimes forwards and sometimes backwards.

All of this can be summarized by noting, $$\int \sqrt{dx^2 + dy^2} \geq \int \sqrt{dx^2} = \int |dx| \geq \int dx$$, and the last of these (the difference in x coordinates, so to speak) is the direct distance along the straight line.

Thus, the shortest path is the direct straight line path.

[TODO: The projection aspect of this is in the context of a Euclidean space, with parallel-perpendicular decomposition and the Pythagorean theorem around. How much of this generalizes to other kinds of metrics?]