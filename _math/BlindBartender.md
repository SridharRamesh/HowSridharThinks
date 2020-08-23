---
layout: post
title:  "Blind Bartender Problem"
date: 2020-8-10
---
Suppose you play a game: You have a bidirectionally infinite sequence of coins, heads or tails. Your goal is to make this into some particular target sequence. At any moment, you announce some set of positions that you wish to flip. Your opponent, however, can respond by translating your set by some amount before it takes effect; e.g., if you wanted to flip positions -9, 8, and 20, your opponent can turn that into -4, 13, and 25. You keep going like this in turns. From what starting positions can you force a win, how do you do so, and how does your opponent stymie you otherwise?

Let V_0 be the bi-infinite string of all 0s, representing zero difference from the target. Let V_{n + 1} be all those bitstrings of differences from the target from which you can force your way to some position in V_{n} in the next turn.

We will prove inductively that each V_{n} is closed under translation and bitwise XOR. These properties clearly hold for V_0. Assuming they hold for V_{n}, let’s show they hold for V_{n + 1}. Indeed, a fortiori, we’ll show that V_{n + 1} is all those positions such that (1 – R) applied to them lives in V_{n}, where R is the translation operator and + or – are given by bitwise XOR.

Suppose you can force your way from Position into V. That means there is some Move such that Position + Move is in V, and so is Position + R^m Move for any power of the translation(/rotation) operation R. In particular, Position + R Move is also in V, and thus, taking the difference of these two and noting that V is closed under difference, we find that (1 – R)Move is in V. Furthermore, since Position + Move is in V and V is closed under multiplication by (1 – R), we find that (1 – R)(Position + Move) is in V. And thus, taking the difference of the last two results, we find that (1 – R)Position is in V.

So everyone position which can be forced into V is such that (1 – R) applied to it is in V.

Conversely, if (1 – R)Position is in V, then by applying R^m for any power m, we find also that (R^m – R^{m + 1})Position is in V. By adding a suitable sequence of these, we find that (1 – R^m)Position is in V for any power of R. And therefore, we can take Move to be Position itself. Any Position such that (1 – R)Position is in V can be forced into V in this way.

We’ve proven that V_{n + 1} is precisely those values which multiply by (1 – R) to land in V_n. Since V_n is closed under translation and XOR, it follows that so is V_{n + 1}. These results now extend inductively to all n.

V_n is precisely those values which, when multiplied by (1 – R)^n, yield 0. I.e., those sequences which are of degree (n – 1) if thought of as polynomial functions from Z to Z_2. Note that this means each V_n is also a superset of the previous one.

From this we see that furthermore V_{\omega} = union of all V_n is also closed under translation and XOR. From this, we conclude that a Position is such that it can be forced by some move into V_{omega} just in case (1 – R)Position is already in V_{omega}. But this means (1 – R)Position is already in V_n for some n, and this means Position is already in V_{n + 1}, and thus already in V_{omega}. So positions which are not in V_{omega} cannot be forced into V_{omega}, while positions which are in V_{omega} are in V_{n} for some finite n and can be forced into V_0 after n moves. You are able to win from a starting position in V_{omega} and your opponent is able to win otherwise.

If (1 – R)^n annihilates X, so does (1 – R)^{smallest power of 2 >= n}. By freshman’s dream, this is 1 – R^{same power of 2}. For X to be annihilated by this is to say that X is periodic with period that same power of 2. So we see that those positions which are power of 2 periodic are ones from which we can win, and those positions which are not power of 2 periodic are ones from which we can’t win.

It turns out, even if we are blindfolded, we can win from the power of 2 periodic positions as well. To be continued…

[TODO: Talk more about degrees and how they add when sequences add, relate to the standard Gray code, talk about nonstandard Gray codes and how they aren’t useful here but everyone forgets them]