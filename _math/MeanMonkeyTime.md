---
title:  "Mean Monkey Time"
date: 2020-7-7
---
Suppose you have a monkey banging away at a typewriter with N keys, each keystroke at independent uniform random. Suppose you're waiting for the first occurrence of a particular string S. On average (in the sense of probabilistic mean), how many keystrokes will it take?

This is basically a Markov chain problem. For any particular string S, we set up a Markov chain with a bunch of states, one for each prefix of S [the amount of progress we may have made so far], and then consider all the transition probabilities. From any state, there's a 1/N chance of advancing one state further. However, the damage done by other keystrokes depends on the particulars of the string, the state we were in, and the keystroke; we may be sent all the way back to square zero or we may only be sent part way back to some partial progress state still.

Whatever the particular string S, we can readily set up this Markov chain and then do the linear algebra (solving $$\vert S \vert$$ many equations in $$\vert S \vert$$ many variables) for the mean time to the accepting state. However, there's a more clever way to think about this, which readily solves the problem in full generality:

Imagine a casino where, on every given day, a monkey hits a letter on the typewriter. Furthermore, everyone in the casino has kept track of the string of all letters they've seen so far, and each day puts all their money down on a bet that they will make it one character further into S. If they do not make such progress, they go bankrupt and leave the casino (no retreating into partial progress as in the Markov chain). If they do make such progress, the winnings from their bet are N times the amount they put down (making the profit N - 1 times the amount they put down). This ensures it's a fair odds bet, with mean profit zero. Finally, every day, one new person enters the casino with one dollar, betting it on starting off getting the first character of S.

If anyone ever makes it all the way through S, the casino pays out all its obligations and shuts down.

On average, how long will it take for someone to make it all the way through S? Well, let's consider what the casino's total profit is at the time someone does this. This total profit must have a mean value of zero, since all the bets individually have mean values of zero (this is a "Stopping Time" theorem, a theorem about martingales, in jargon). We can think of the money flow of the casino as having taken in one dollar from everyone who ever showed up, and having payed out some last round winnings to everyone who hasn't yet gone bust. The means of these two flows (dollars into the casino and dollars out) must be equal and cancel out. The former of these values is the number of rounds it took for someone to make it all the way through S. The latter of these values is the sum of N^k over everyone who successfully won precisely k many turns; that is, the sum of N^k over all positive k such that the first k characters of S match the last k characters of S.

This is the answer, then. The mean number of keystrokes it takes is the sum of N^k over all positive k such that the first k characters of S match the last k characters of S.

See https://projecteuclid.org/download/pdf_1/euclid.aop/1176994578 ("A Martingale Approach to the Study of Occurrence of Sequence Patterns in Repeated Experiments" by Shuo-Yen Robert Li) for some further generalizations.