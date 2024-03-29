---
title: "Eulerian Graphs"
date: 2020-5-4
---
Suppose given a directed multigraph, and suppose also that at each vertex, we are given a bijection between the edges into the vertex and the edges out of that vertex (think of this bijection as saying that the former edge is "followed by" the latter edge). Then every edge is in a line of edges (the edge after it, and the edge after that, and so on, as well as the edge before it, and the edge before that, and so on); either an infinite line of all distinct edges, or a periodically repeating line (i.e., a finite cycle).

That is, this structure is the same as a way of designating our graph as a union of lines and cycles, with some vertices identified among these.

In particular, even if we are given an arbitrary directed multigraph without the rest of this structure, we will be able to produce the rest of this structure just in case we can pick some bijection between incoming and outgoing edges at each vertex; i.e., just in case each vertex has the same indegree as outdegree.

So a graph is a union of lines and cycles just in case it has the same indegree and outdegree at each vertex.

The above was phrased in terms of directed graphs, but works the same way for undirected graphs as well, where now at each vertex, the relevant structure is not a bijection between incoming and outgoing edges, but rather, a pairing (aka, matching) between the undirected neighboring edges. [Put another way, we can think of an undirected graph as a directed graph with an edge-reversing operator (each undirected edge amounting to two directed edges), and we are now constraining our "following edge" structure so that when E is followed by F, we also have that reversed F is followed by reversed E]. We can create this structure just in case each vertex has even degree, and thus we find that an undirected graph is a union of lines and cycles just in case each vertex has even degree.

What's more, a cycle can be glued into any other cycle or line at any vertex they have in common (if we are in directed-world, there is a unique such gluing; if we are in undirected world, there are two such gluings). So if we have finitely many cycles and lines, we can keep gluing together until they are all vertex disjoint.

In particular, if our original graph was finite, then we have finitely many cycles, no infinite lines, and find that (just in case its vertices all satisfied the degree requirement) it has some representation as a union of finitely many disjoint cycles; the number of disjoint cycles will clearly be the number of connected components of the graph.

[We can consider the pathology of there also being vertices with no edges touching them, so the number of connected components of vertices is higher than the number of cycles of edges. But from now on, let us assume every vertex has some edge touching it, for convenience.]

In particular, in the case where all the edges of the graph can be made into one big cycle using each edge precisely once, we say it has an Eulerian cycle, aka Eulerian circuit. From the above, we see that a graph has an Eulerian cycle just in case it has one connected component and satisfies the degree constraint (indegree matches outdegree if directed, degree is even if undirected) at each vertex.

If, instead of one big cycle, we want one big path from A to B, hitting every edge precisely once (an Eulerian path), we can add to our original graph a dummy edge from B to A. Eulerian cycles on the graph augmented with the dummy edge correspond to Eulerian paths on the original graph from A to B, by dropping or adding the dummy edge.

The reason all these things are called Eulerian is because these are classic results by Euler, in a paper discussing the famed "Bridges of Königsberg" problem, and often considered to be the start of topology/analysis situs, in the sense of considerations of shapes purely in terms of connectivity structure, deliberately ignoring metric structure.

We can go even further and actually count the number of of Eulerian circuits/Eulerian paths in a directed graph, in an interesting way. This is called the BEST theorem, an acronym made of the initials of four authors, alphabetically. Normally, a cutesy acronym like this is contrived bullshit for a contrived bullshit result, but the BEST theorem is actually quite nice. I'll explain how it works first for counting Eulerian cycles ending in a designated edge; other counting problems will be obvious modifications of this one.

Suppose we have a directed graph of which we know the indegree at every vertex matches the outdegree, and we wish to specify an Eulerian cycle starting and ending at vertex V, starting with edge E out of V.

Note that all it takes to specify an Eulerian cycle is to say, at every vertex, a list in order of the edges with which this vertex is exited. Then, starting from V, we just follow the instructions: every time we come to a vertex, we take the next edge out in order that we haven't yet taken. If everything goes well [and we're about to pin down the conditions under which it will], we will never come to a vertex again after exhausting its outlist, and we will exhaust every vertex's outlist at just the moment that we return to V, finishing our cycle.

Note also that, for every vertex W other than V, there is some last time in the cycle we exit W. We exit W along some particular edge LastOut(W). Collecting together all these edges LastOut(W) produces a tree, with V at the root, and directed edges from every other vertex to a parent. People call this an "arborescence" rooted at V.

So however we order the outgoing edges at each vertex, the last edges at the non-V vertices must combine into an arborescence rooted at V. We also have fixed by fiat that the first edge out of V must be E. Thus, what remains after specifying the arborescence is the choice of one of (outdegree - 1)! many orderings on the remaining out-edges at each vertex.

It turns out, any system of such choices does arise from an Eulerian cycle. That is, for any system of such choices, as you run around following its instructions, you will land back at V just in time to have exhausted every vertex's outlist. This gives a one-to-one correspondence between <arborescence rooted at V, orderings of out-edges at each vertex such that the final out-edges at non-V vertices comprise the arboresecence, and the first out-edge at V is E> and <Eulerian cycle starting with edge E out of V> data.

Why does everything go well? Note that, any time we come to a vertex other than the starting vertex V, we have come into it one more time than we have exited it. Since it has equal indegree and outdegree, and we traverse edges only once, we never come back to a vertex which has already exhausted its outlist. So we can never get stuck, except by returning to the starting vertex V.

Furthermore, at the moment that a vertex has exhausted its outlist, we must have entered it as many times as it has outdegree, equivalently, indegree; that is, we must have also exhausted its inlist. That means for all its children in our arboresescence, we've taken the final edge out of them up to their parent. So when a vertex has exhausted its outlist, so already have all its children (thus, in the same way, all its descendants).

So, as we run around, the only way we can get stuck is that we return to V having used up its outlist. But at precisely the moment we do so, all its descendants' outlists have been used up as well. Every edge appears in some outlist, so this is precisely the moment at which we have run across all edges once. This completes the proof.

This proof counts the total number of Eulerian circuits up to cyclic rotation as the product of (outdegree - 1)! at each vertex times the number of arborescences rooted at a particular vertex. This demonstrates that the numbers of arborescences rooted at any two vertices are the same.

[TODO: How does the BEST theorem work for undirected graphs? I suppose you start off by choosing some way to orient all the edges, such that the in-degree and out-degree match at each vertex, and then deal with it as a directed graph. Note also that the number of undirected arborescences of an undirected graph are the same rooted at every vertex since an undirected tree has no concept of distinguished root; these are just spanning trees. From a counting perspective, we can do the counting without first orienting the edges, since we know the final outdegree will be half the starting degree at each vertex anyway. The fact that we can orient the edges in a suitable fashion at all is maybe not obvious, except by doing the cycle decomposition proof at the beginning? It appears to be a nontrivial problem to compute the number of acceptable ways to orient the edges. Is the number of directed arborescences the same regardless of orientation choice?]

[TODO: This Eulerian fact tells us that, in homology, a chain of 1-cells with null boundary always decomposes into a combination of 1-spheres. I believe this fact fails in higher dimension; check as to whether it does and then write more about that]

Specifically, for homology with coefficients, the relevant variation on the above argument is this: suppose given a directed multigraph where each edge is assigned a nonzero weight in some Abelian group, such that at every node, the total weight of the edges in equals the total weight of the edges out. Then it is possible to select a set of cycles-with-weights (allowing negative weights) such that each edge's weight is the sum of the weights of the selected cycles in which it appears.

Proof: Ignoring the weights for a second, consider this as just a directed multigraph. We don't know that every node has equal indegree and outdegree, but we do at least know that every node with positive indegree also has positive outdegree. So pick a random node with an outgoing edge and run around burning bridges around at random till you arrive at a node with no edges out left. It cannot be that this is the first time you've come to this final node (or else there would still be an edge out left); thus, you've created some positive-length cycle from a previous visit to this node to the final visit to this node. Within this cycle, pick any edge; assign that edge's weight to this cycle, and now remove that edge from the original graph, along with that weight from every other edge in the cycle. In this way, we've reduced our original graph to one weighted cycle plus another graph with less edges, with the smaller graph still having the property of equal in- and out-weight at every node. Continuing inductively in this way, we get the desired result.

Similarly, suppose the graph we are given is undirected, and each edge's weight can be read as the negated weight when the edge is traversed in the opposite direction, and each node has total weight zero when all edges around it are oriented to point towards it (equivalently, on any orientation of the edges around it, the total weight in matches the total weight out). After we throw away weight information, we don't know that every node has even degree, but we do know that no node has degree 1. So as we run around randomly, the very first time we come to a node can't have exhausted the possibility to leave the node. Put another way, any acyclic undirected graph is a forest of trees, which must have degree 1 at its leaves (however you choose what to call the roots). Thus, so long as we still have edges we must have some cycle available, which we can then pull out with the weight of some edge within it, carrying out the inductive decomposition as above.

[TODO: Can all the directed vs. undirected and degreed vs weighted theorems be combined into one single general theorem with unified proof?]

***

What happens if we have a finite connected directed multigraph with matching indegree and outdegree at each vertex, and an ordering of outgoing edges at each vertex, but these final outgoing edges at non-V vertices do not comprise an arborescence rooted at V?

It's still the case that walking around in this manner, starting with edge E, we must end up first exhausting an outlist upon a revisit of dom(E). That is, we trace out a cycle which starts with E, repeats no edges, and contains every edge into and out of the domain of E.

Put another way, suppose we instead treat these orderings of outgoing edges as cyclic orderings: that is, rather than removing the first entry from an outlist as we cross it, we simply move it to the end of the outlist.

We now have that walking in this way, starting with any edge E, we trace out a cycle which starts with E, repeats no edges, and contains every edge into and out of the domain of E. Call this the initial loop of the walk. (It is then followed by a repeat occurrence of E.)

Let walk W = edge E followed by walk W'. Note that the initial loop of W contains a subset of the edges in the initial loop of W' \[since walk W starts with "E, F, other edges, E", of which the "E, F, other edges" is the initial loop of W, while the initial loop of F contains at least the "F, other edges, E"\]. (Note also that the new initial loop will be essentially unchanged (just rotated by one edge) from the old initial loop iff the old initial loop contained every edge in and out of cod(E) = dom(F))

Thus, initial loops only increase as starting points move further into the walk, so to speak, and they stabilize forever just when they become Eulerian cycles.

(This explains, for example, the phenomenon observed at https://twitter.com/AshtonSix/status/1753224084496740541, by applying this to a de Bruijn graph).

Also, once the starting point has moved to any occurrence of vertex V, the initial loop contains every edge in and out of V, so once our walk has visited every node, it must thereafter settle into its Eulerian cycle. That is, the first time at which the walk has visited every node is somewhere between the start and the end of the first instance of the Eulerian cycle in the walk.

***

Let us say a "state" on one of these graphs is a choice of cyclic ordering of outgoing edges at every node, a choice of active outgoing edge at every node, and a choice of active node. Any state "evolves" into a successor state which has the same cyclic orderings, and almost all the same active outgoing edges, but the old active node's outgoing edge is shifted one further along in its cyclic ordering, while the new active node is the old active node's old active outgoing edge's codomain. This describes the kind of cyclic outgoing edge walks we were using above.

Our reasoning from before shows us that evolving states in this way always eventually stabilizes into an Eulerian cycle. We can also make the following observation: A state S is such that there exists a state T with active node V which evolves into S iff there is a path from V to the active node of S using only "last outgoing edges" (that is, the edges which precede the active outgoing edges in their cyclic orderings).