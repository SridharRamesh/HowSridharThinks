---
title: "Arrow's Impossibility Theorem"
date: 2020-10-16
---
The content of Arrow's Impossibility theorem is actually extremely closely related to ultrafilters, and, in fact, the eponymous “impossibility” is essentially the same as a very basic fact about ultrafilters on finite sets. Yet, for some reason, I have rarely (if ever) seen the theorem presented in such a way as even mentions this connection (e.g., the word “filter” appears not once in the relevant Wikipedia article, nor in any of the references within it). A shame, which I shall rectify in this post.

[I originally wrote all this on April 19, 2009 (see https://pleasantfeeling.wordpress.com/2009/04/19/arrowstheorem/). But now I copy it over here and slightly edit it.]

Current requirements to understand this post: Basic knowledge of what filters and ultrafilters are [I shall probably come back and expand this post to actually kick off an introduction to the concepts for those who don’t already know]

***

Suppose you have a fixed set of voters and a set of ballot options (aka, candidates) for them to choose between. By a (deterministic) voting system on these voters and ballot options, we mean some function which takes as input any assignment from voters to their preferences (expressed as a linear ordering upon the ballot options) and produces as output some cumulative ranking of the ballot options (again, expressed as a linear ordering upon the ballot options). What Arrow’s Impossibility Theorem shows is that, if there are at least 3 ballot options, the voting systems satisfying some basic desirable criteria come only in one very particular (in some cases, rather undesirable) form.

What criteria exactly? Well, the first is “Pareto efficiency”, aka “unanimity”: if all voters have the exact same preferences, then the cumulative ranking should be the same as this. Surely, this is the most natural, basic voting system property one could ask for.

The second criterion is “independence of irrelevant alternatives” (IIA): in the cumulative ranking, the relative position of any two ballot options depends only on the voters’ relative preferences between them (i.e., to figure out if option A beats option B in the cumulative ranking, one only needs to ask which voters ranked A higher than B and which ranked B higher than A; one doesn’t need to know anything about how voters felt about any other, “irrelevant” options). This is one way of formalizing that there should be no “spoiler” effect (Nader shouldn’t be able to steal votes away from Gore to win the election for Bush).

Let’s start exploring the effects of these criteria on the design of a voting system. First, for simplicity’s sake, we’ll act as though there are exactly 3 ballot options (we’ll use A, B, and C to denote arbitrary ballot options, with different letters being distinct options), and we’ll restrict voters to turning in preferences without ties, but we’ll not explicitly restrict the cumulative ranking from having ties. All of these assumptions could be dropped/changed, but as they only make things easier for the voting system designer, our impossibility results will immediately generalize even to these other cases.

Ok, so what can we conclude from these criteria? Well, by independence of irrelevant alternatives, we know that whether A beats B in the final ranking or not just depends on which set of voters choose A over B [and which set chooses the opposite, but as voters’ preferences have no ties, these two sets are complements and so the latter is redundant data on top of the former]; so, we’ll say that a set of voters M wins for A over B if the cumulative ranking has A beating B when the voters who prefer A to B are precisely those in M. The Pareto efficiency condition then becomes just that the set of all voters wins for every candidate over every other candidate. The voting system is entirely determined by this ternary relation, so let’s see what kind of properties it has.

Suppose M wins for A over B. Then consider the situation where voters vote as follows:

* In M: A > B > C
* Outside M: B > C > A

Since the voters who choose A over B are precisely those in M, A will beat B. Furthermore, since everyone chooses B over C, B will beat C; thus, transitively, A will beat C. Since the voters who chose A over C are precisely those in M, we see that M wins for A over C as well.

So we’ve proven that if M wins for A over one candidate, then it also wins for A over any other candidate; thus, we can speak just of “winning set for A over others” rather than “winning set for A over B” and such.

But, everything here is symmetric; just reversing all the orders above, we see that if a set wins for some other candidate over A, then it wins for any candidate over A, and so we can speak generally of “winning set for others over A”. [And, of course, instead of A in these, we could use any other candidate]

And so we have that winning set for A over others = winning set for A over B = winning set for others over B = winning set for C over B = winning set for C over others. Thus, any two candidates have the same winning sets over others, and so we can just speak of winning sets in absolute terms, without having to specify which candidates are involved. Now we just have to see what kind of properties the system of winning sets is constrained to have.

By the unanimity condition, the set of all voters is a winning set. Furthermore, suppose M and N are winning sets and consider the situation where voters vote as follows:

* In M and N: A > B > C
* In M but not N:  C > A > B
* In N but not M: B > C > A
* In neither M nor N: C > B > A

In this case, the voters who choose A over B are precisely the ones in M, and the voters who choose B over C are precisely the ones in N; thus, the result must be that A wins over B and B wins over C. But this means that A wins over C; since the voters who choose A over C are precisely the ones in both M and N, we see that the intersection of M and N must win for A over C. So, the winning sets are closed under intersection as well.

Now, let us demonstrate that the winning sets are upwards closed. Suppose M is a winning set, N is a superset of M, and voters vote as follows:

* In M: A > B > C
* In N but not M: B > A > C
* Outside N: B > C > A

Then the voters who choose A over B are those from M, so A beats B. And everyone chooses B over C, so B beats C. Thus, transitively, A beats C; as the voters who choose A over C are precisely those in N, we have that N is a winning set as well.

So we see that winning sets are closed under finite intersection and upwards closed, which makes them a filter. Finally, let’s show that they actually form an ultrafilter: this means of every set of voters, either it or its complement wins, but not both. The not both part is automatic (two candidates can’t both beat each other), and the first part is nearly as automatic; we just have to show that there can’t be any ties. Well, suppose there existed some tying set M (i.e., such that neither M nor its complement were winning sets). Then consider the voting situation

* In M: A > B > C
* Outside M: B > C > A

In this case, A ties with B and A ties with C, so transitively, we should have that B ties with C. However, by unanimity, we also have that B beats C, which is a contradiction. Thus, we can conclude, there cannot actually exist any tying sets; no one ever actually ties.

Thus, the winning sets necessarily form an ultrafilter. Conversely, it is readily seen that any ultrafilter gives a suitable system of winning sets (you can verify this directly, but those in the know should recognize this as just an instance of Łoś‘s Theorem, the voting system being naught but an ultraproduct). And so we have that (with at least 3 candidates), the Pareto efficient voting systems satisfying IIA are precisely those given by ultrafilters. This is Arrow’s Impossibility Theorem (albeit phrased in a more general form than than it is usually given in).

Why “Impossibility”, you ask? Well, in particular, the ultrafilters on finite sets are precisely the principal ones; thus, on a finite set of voters, the only Pareto efficient IIA voting systems are “dictatorships”; there is a fixed voter whose preferences are always taken verbatim as the overall result. Which is to say, on a finite set of voters, it is impossible to construct a voting system satisfying the above criteria as well as that of non-dictatorship (this, of course, being the way AIT is usually stated).