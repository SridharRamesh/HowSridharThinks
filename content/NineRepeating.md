---
title: "0.999... = 1"
date: 2020-2-17
---
This comes up a lot in pop math discussion, so I’ll just post here the thing I’ve written about it in various other places previously.

One must distinguish between notation and what that notation represents. Different notation can represent the same entity, as in, for example, the equality of “1/3” and “2/6”: they are not equal as notation, but the fractions they denote are equal.

Now, does “0.9999…” denote the same thing as “1”?

Well… first off, a disclaimer: of course, one could invent an interpretation of this notation on which they denoted different things, just as one could invent an interpretation of notation on which “1/3” and “2/6” denoted different things (for example, they denote different dates…). But I’m not going to talk about that sort of thing right now. Instead, I’m going to talk about the standard, conventional interpretation of infinite decimal notation, the one that mathematicians mean when they use this notation, and the one which justifies the claim that “0.9999…” denotes 1.

When a mathematician gives an infinite decimal as notation for a number, what they mean by it is this: the* number which is >= the rounding downs of the infinite decimal at each decimal place, and <= the rounding ups of the infinite decimal at each decimal place. This is the definition of what infinite decimal notation means; it’s true because we say it is, just as the three letter word “dog” refers to a particular variety of four-legged animal because we say it does.

So, for example, when a mathematician says “0.166666…”, what they mean, by definition, is “The number which is >= 0, and also >= 0.1, and also >= 0.16, and also >= 0.166, and so on, AND also <= 1, and also <= 0.2, and also <= 0.17, and also <= 0.167, and so on.” What number satisfies all these properties? 1/6 satisfies all these properties. Thus, when a mathematician says “0.16666…”, what they mean, by this definition, is 1/6.

Similarly, when a mathematician says “0.9999…”, what they mean, by that same definition, is “The number which is >= 0, and also >= 0.9, and also >= 0.99, and also >= 0.999, and so on, AND also <= 1, and also <= 1.0, and also <= 1.00, and also <= 1.000, and so on.” What number satisfies all these properties? 1 satisfies all these properties. Thus, when a mathematician says “0.9999…”, what they mean, by definition, is 1.

[*: Of course, when one says a thing like “THE number which is…”, this may be taken to involve an implicit claim that there is a unique such number. So when mathematicians use infinite decimal notation, they also generally have a very particular number-system in mind in which these uniqueness claims are all justified. But, there are many other number-systems (just as useful ones, or even more useful ones, for many purposes; the world is diverse and our mathematical analyses needn’t be shoehorned into “one size fits all” form) in which there may be no number or many different numbers satisfying such systems of constraints; in such contexts, infinite decimal notation is generally less useful as a way to denote numbers, though it can still be used in essentially the same way to denote certain intervals instead.]