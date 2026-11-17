---
title: "The Hoffman bound"
date: 2026-11-17
---
Consider strings of length n over an alphabet of size S. What is the maximum number of such strings we can put in a set, such that no two strings in the set differ at every position? Well, it's relatively easy to see it is $$S^(n - 1)$$ (presuming $$n > 0$$), and that one way of doing so is to take all strings with a particular character at a particular position. Is this the only way of achieving this? 

More generally, how can we determine the largest cliques or anti-cliques in a graph? (In this case, the relevant graph is the product in a suitable sense of $$n$$ many copies of the complete graph on $$S$$ many vertices). A powerful technique for doing so is the Hoffman bound, from spectral graph theory.
<!--more-->

----

To understand the Hoffman bound, let us start by considering some general linear (and quadratic) algebra, before specializing it to graph theory.

Let Q be a quadratic form (equivalently, a symmetric bilinear form; equivalently, a self-adjoint operator T) on a real inner product space V. Furthermore, let v be an eigenvector of T with a non-zero eigenvalue. Without loss of generality, by rescaling Q if need be, we can presume Q(v) positive.

Note that, given a value w orthogonal to v, there is a uniquely determined c^2 such that Q(cv + w) = 0, as Q(cv + w) = c^2 Q(v) + Q(w). Thus, projection is a surjection from the zeroes of Q onto the dual space of V (the correspondence is 1:1 where the range is among the zeroes of Q and 2:1 elsewhere). Letting f(x) = Q(x) / |x|^2, we have that f(w) also determines, in a strictly order-reversing way, the squared cosine of the angle between v and such a cv + w (as this squared cosine is 1 / (1 - f(v) / f(w)) ). Thus, maximizing this squared cosine amounts to minimizing f(w).

f applied to a sum of one or more eigenvectors for T yields a value between the lowest and highest associated eigenvalues (strictly between, unless there is just one associated eigenvalue). Thus, if every vector is a sum of eigenvectors (as for example ensured by the spectral theorem in the finite-dimensional context), f is minimized precisely at the eigenvectors for the minimum eigenvalue.

----

Now let's specialize this linear algebra to graph theory. A graph amounts to an adjacency matrix. A subset of the nodes of the graph amounts to an indicator function encoded as a vector with {0, 1}-valued coordinates. The dot product of two such subsets is the size of their intersection; thus, the squared cosine between two such is the squared size of their intersection over the product of their individual sizes. Fixing one subset to be the set of all nodes, this squared cosine is proportional to the size of the other subset. What's more, in a regular graph, the set of all nodes is an eigenvector of T (with eigenvalue the degree of each node of the graph). And the condition Q(v) = 0 states that the subset encoded by v contains no two adjacent nodes (it is an anti-clique).

So the above tells us how to maximize the size of an anti-clique in a regular graph, by looking at its spectrum: The largest anti-cliques are those whose indicator functions correspond (under 2:1-ish projection as described above) to eigenvectors of the adjacency matrix of minimum eigenvalue orthogonal to the all 1s vector… as long as there is at least one anti-clique of this sort at all (i.e., as long as solving the maximization problem among vectors with real coordinates includes at least one solution with {0, 1}-valued coordinates).

----

Now let's specialize to the graph whose anti-cliques we are interested in in particular. It's the tensor product of n many copies of the complete graph on S nodes. The complete graph on S nodes is regular of degree S - 1, while every vector orthogonal to the all 1s vector is an eigenvector of eigenvalue -1. Thus, in the n-fold tensor power, the entire vector space is spanned by tensor products of vectors whose coordinates are either constant or sum to zero, with the corresponding eigenvalue being (S - 1)^x (-1)^y, for x many factors with constant coordinates and y many factors with coordinates summing to zero.

So long as S > 2, the smallest of these eigenvalues is -(S - 1)^(n - 1). The corresponding eigenvectors are functions from S^n to reals which sum to zero overall, and which satisfy the "linearity" property that changing any particular coordinate from any particular starting value to any particular ending value increments the function by the same amount no matter what the other coordinates are taken to be. Adding a constant to these removes the "sum to zero overall" constraint, but retains the "linearity" property.

Because of "linearity", the {0, 1}-valued functions we can obtain in this way cannot depend on more than one coordinate (for if they were able to achieve a +1 change via values on one coordinate, and also a +1 change via values on another coordinate, then by combining these linearly, a +2 change could be achieved overall, contra being {0, 1}-valued).

Thus, in this case, the maximum size anti-cliques are precisely the non-empty anti-cliques whose indicator functions depend on no more than one coordinate.

----

Of course, searching for cliques in a graph is just as well searching for anti-cliques in the complementary graph. So the Hoffman bound technique works for either of these.

More interestingly, in the above, we gave the Hoffman bound technique as applicable specifically to regular graphs. But we can apply it to finding anti-cliques in arbitrary finite undirected graphs as well:

First of all, we can ignore isolated vertices (non-adjacent to everyone), because these will automatically be included in every maximal anti-clique. So get rid of those. Next, we assign positive weights to the edges of the graph however we like, but shrink these down enough that each node has total weighted degree ≤ 1. For any node whose weighted degree is less than 1, we add on a new edge to a new node, whose weight makes up the difference; on each new node, we add a loop whose weight brings its weighted degree to 1 as well (this loop will have nonzero weight since the original node was non-isolated).

So now, we've created a symmetric stochastic matrix, whose loopless nodes have the adjacencies of our original graph. Solving the maximal anti-clique problem for this stochastic matrix is the same as solving it for our graph, since an anti-clique only contains loopless nodes. And our technique from above works for this stochastic matrix just as for any regular graph (the only invocation of regularity was in making the all 1s vector an eigenvector with nonzero eigenvalue, which will continue to hold in any stochastic matrix).

Of course, there's always the question of how to choose particular weights so as to create a stochastic matrix whose eigenvalue structure is nicely analyzable. There seems to be some freedom to play around here, for any particular graph. Relatedly there's also the issue that it may be that in some graph or matrix, the {0, 1}-valued anticliques do not achieve the optimum value achievable using arbitrary coordinates. I'm not yet sure if there's anything useful to say about that.

----

For our particular problem with strings, there is also an elementary solution which does not explicitly reason about eigenvalues: 

If we impose a cyclic ordering on each of the $$n$$ factors of $$S^n$$, then within any orbit of the operation of simultaneously incrementing each coordinate, at most one point can lie in our chosen subset. So the maximum achievable size is $$S^(n - 1)$$, achieved when we choose precisely one point from each orbit.

We don't have to identify each coordinate with the same cyclic ordering, though. Given any $$S$$ many points which pairwise differ at every position, we can impose some cyclic ordering on these points, and from this we get a system of cyclic orderings at each coordinate such that these points become an orbit. So our result is really that given any $$S$$ many points which differ everywhere, precisely one of them must be chosen.

From now on, let us presume we have chosen a clique of size $$S^(n - 1)$$; we will establish that it must be of the form defined by a particular coordinate value at a particular position.

To be clear about terminology, we are using the convention that a collection of points where every pair differs at every position is a "clique", while a collection where no two points differ at every position is an "anticlique". If a clique has size $$S$$ (thus containing precisely one chosen point) it's a "maximal clique". Let's say two cliques are "complementary" if their union is a maximal clique; thus, of complementary cliques, the one contains a chosen point iff the other does not. Let's say two cliques are "cognate" if they have the same image under projection to each coordinate. Observe that cognate-ness is an equivalence relation respected by complementary-ness. Thus, cliques are cognate iff they have a common complement. Thus, of cognate cliques, the one contains a chosen point iff the other does.

We only need one special case of this in the end: Suppose we have a "parallelogram" A-B-C-D, meaning points for which {A, C} and {B, D} are cognate cliques. Then if A is chosen and B is unchosen, then also D is chosen and C is unchosen. We only need one special case of this special case even: The case where A and B differ in a single coordinate.

What this says is that, if changing a single coordinate can change the chosen status of a point, then in the "hyperplane" defined by that coordinate value at the point, the chosen points are closed under changing all other coordinates. Of course, changing a single coordinate CAN take an unchosen point to a chosen point (since the transitive closure of changing a single coordinate relates all points, and not all points have the same chosen-ness). So this tells us there is a hyperplane in which the chosen points are an inhabited set closed under changing all coordinates other than the one defining the hyperplane.

Finally, when S > 2, the transitive closure of "all coordinates differ" relates any two points. Thus, every point in the above hyperplane is chosen. QED.