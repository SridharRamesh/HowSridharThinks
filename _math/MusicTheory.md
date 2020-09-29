---
title:  "The Fundamental Theorem of Equal Temperament Arithmetic"
date: 2020-9-29
excerpt_separator: "\n\n\n"
---
The Fundamental Theorem of Equal Temperament Arithmetic is that log(2) : log(3) : log(5) is 12 : 19 : 28.

What do I mean by this? This is a statement about music theory.


Consonant intervals are generally characterized by nice frequency ratios. In particular, n + 1 : n ratios are of note, as every other rational ratio can be built out of these short intervals. The smaller the n here, the more consonant the ratio, in some sense.

The most important such interval is the octave (called "octave" after 8 for stupid fencepost reasons I won't get into right now, but a better name would be 7-based; all the intervals have names that are off by one from what they should be). Two notes separated by an octave are in a frequency ratio of 2 : 1.

In the familiar chromatic scale, this interval is considered to be twelve notes each a "semitone" apart; in equal temperament tuning, each semitone is taken to have the same frequency ratio, so each semitone has frequency ratio 2^(1/12).

The next most important intervals are the perfect fifth, which in just intonation has a frequency ratio of 3 : 2, the perfect fourth, which in just intonation has a frequency ratio of 4 : 3, the major third, which in just intonation has a frequency ratio of 5 : 4, and the minor third, which in just intonation has a frequency ratio of 6 : 5.

None of these can be represented exactly in our equal temperament tuning system, though, which can only represent ratios of the form 2^(n/12). So instead, best approximations are taken.

A perfect fifth (3 : 2 frequency ratio) is taken to be 7 semitones. Thus, 2^(7/12) is taken to approximate 3/2. This amounts to approximating log(2) : log(3) as 12 : 19.

[Specifically, for variables Two and Three, we have that Two^(7/12) = Three/Two is equivalent to log(Two) : log(Three) = 12 : 19]

A perfect fourth (4 : 3 frequency ratio) is taken to be 5 semitones. Thus, 2^(5/12) is taken to approximate 4/3 = 2^2/3. This again amounts to approximating log(2) : log(3) as 12 : 19.

[Specifically, for variables Two and Three, we have that Two^(7/12) = Two^2/Three is equivalent to log(Two) : log(Three) = 12 : 19]

A major third (5 : 4 frequency ratio) is taken to be 4 semitones. Thus, 2^(4/12) is taken to approximate 5/4. This amounts to approximating log(2) : log(5) as 12 : 28.

[Specifically, for variables Two and Five, we have that Two^(4/12) = Five/Two^2 is equivalent to log(Two) : log(Five) = 12 : 28]

A minor third (6 : 5 frequency ratio) is taken to be 3 semitones. Thus, 2^(3/12) is taken to approximate 6/5. This fits coherently with all the above, as again approximating log(2) : log(3) : log(5) as 12 : 19 : 28.

[Specifically, for variables Two, Three, and Five, if log(2) : log(3) : log(5) is 12 : 19 : 28, then Two^(3/12) = Two * Three / Five]

So all of these equal temperament approximations of just intonation's simple rational n + 1 : n frequency ratios, using powers of irrational 2^(1/12) instead, up through n = 5, fit together in this simple way, following just from the rule that log(2) : log(3) : log(5) is approximated as 12 : 19 : 28.

We can keep going in this same way and, using equal temperament approximations for finer intervals, also deduce rational ratio approximations between logarithms of further primes such as 7. So, there is a similarity to the Fundamental Theorem of Arithmetic here. And thus I call this the Fundamental Theorem of Equal Temperament Arithmetic.

***

[TODO: Nicer formatting, discussion of other music theory, in general make the discussion friendlier-paced]