---
layout: post
title:  "The Generalized Factorial"
date: 2018-06-27
---
Suppose you wanted to extend the factorial function to arbitrary arguments. How might you do it?

Well, of course, there are a million ways to do it. (Where "a million" = "infinitely many"). You could say the factorial function is the normal thing at natural numbers, and $$\sqrt{7}$$ everywhere else. This wouldn't be a very useful extension, but it technically qualifies.

What would make a more useful extension, then? Well, we want an extension that preserves the key properties of the factorial function. For example, that $$\frac{x!}{(x - 1)!} = x$$.

This still isn't enough to pin down an extension, though. There's still infinitely many extensions of that sort. (You could pick any values you want for input fractions between 0 and 1, for example, and then extend these using the recurrence to corresponding values elsewhere.)

But there's another interesting property of the factorial function: $$\frac{x!}{(x - r)!}$$ is the number of ways to pick a sequence of $$r$$ items from $$x$$ choices, with no repetition. This is similar to, albeit less than, the number of ways to do it if you allow repetition, $$x^r$$. And as $$x$$ gets larger and larger, the probability of repetition gets negligible; we find that the ratio between $$\frac{x!}{(x - r)!}$$ and $$x^r$$ approaches 1 as $$x$$ grows large while $$r$$ is held fixed. (For that matter, the same thing happens to the ratio between $$x - r$$ and $$x$$).

In other words, if the difference between $$a$$ and $$b$$ is held fixed while their individual values grow large, then the ratio between $$\frac{a!}{b!}$$ and $$b^{a - b}$$ approaches 1.

This is a very useful property. If we continue to demand this for our extension, on top of the basic $$0! = 1$$ and $$\frac{x!}{(x - 1)!} = x$$, we *will* pin down a unique function, like so:

$$x! = \frac{x!}{(x + N)!} \times \frac{(x + N)!}{N!} \times N!$$.

If $$N$$ is a natural number, then $$\frac{x!}{(x + N)!}$$ and $$N!$$ are easy to calculate as rising products; combining these two factors produces $$\frac{1}{x + 1} \times \frac{2}{x + 2} \times ... \times \frac{N}{x + N}$$.

Furthermore, our newest demand is that the middle factor, $$\frac{(x + N)!}{N!}$$, become replaceable with $$N^x$$ as $$N$$ grows large.

Thus, we have that $$x!$$ is the limit, as the natural number $$N$$ grows large, of $$N^x \times \frac{1}{x + 1} \times \frac{2}{x + 2} \times ... \times \frac{N}{x + N}$$. And this definition makes sense for all kinds of $$x$$, not just natural numbers.

(When $$x$$ is a negative integer, there will be a division by zero, but for all other $$x$$, this limit will be well-defined. Put another way, the reciprocal of $$x!$$ is (just reciprocating all the factors from before) the limit as $$N$$ grows large of $$N^{-x} \times \left(\frac{x}{1} + 1 \right) \times \left(\frac{x}{2} + 1\right) \times \dots \times \left(\frac{x}{N} + 1\right)$$, and this does indeed converge to a finite limit for every finite x, though that value is 0 at negative integers.)

This defines the usual extension of the factorial function to arbitrary inputs (fractions, complex numbers, even matrices, and so on). As we demonstrated, this is the unique way to do so while satisfying our key properties. As it turns out, other definitions accomplish the same effect (and therefore are equal to this one); for example, the famous integral $$\displaystyle \int_{t = 0}^{\infty} t^x e^{-t} \; dt$$ (which I will discuss more later!). But this product formula falls right out of our key properties, making it often superior to that famous integral for thinking about the generalized factorial.

One last note: the so-called Gamma ($$\Gamma$$) function is just this extension of the factorial function, shifted over by one. The shifting over by one is of no importance at all. It's just a stupid historical convention. So don't worry about it. All that actually matters is the argument above, constructing and establishing the uniqueness of a suitable interpretation of factorial for general (non-integer) inputs.

Connection to the sine function
There is a also a wonderful connection between the generalized factorial and the sine function. As we just saw, we have this product representation for the generalized factorial:

$$\frac{1}{x!} = \displaystyle \lim_{N \to \infty} N^{-x} \prod_{k = 1}^{N} \left(1 + \frac{x}{k} \right)$$.

And as we saw in a previous post [TODO: link], we also have a similar product representation for the sine function:

$$\frac{\sin(x \pi)}{x \pi} = \displaystyle \prod_{k = 1}^{\infty} \left(1 + \frac{x}{k} \right) \left(1 + \frac{x}{-k} \right)$$

There are only two differences between these: in the former, we have a factor of $$N^{-x}$$ around to make our limit converge to a finite value, which we don’t need in the latter. And in the former, we only go through factors corresponding to positive $$k$$, while in the latter, we’ve bundled these together with factors corresponding to negative $$k$$.

But now consider what happens when we multiply $$\frac{1}{x!}$$ by $$\frac{1}{(-x)!}$$. The $$N^{-x}$$ and $$N^x$$ factors cancel out, and the rest of the factors pair up, each $$\left(1 + \frac{x}{k}\right)$$ factor from $$\frac{1}{x!}$$ bundling together with a corresponding $$\left(1 + \frac{x}{-k}\right)$$ factor from $$\frac{1}{(-x)!}$$. We get precisely the product that equals $$\frac{\sin(x \pi)}{x \pi}$$.

And so we can conclude, $$\frac{1}{x!} \times \frac{1}{(-x)!} = \frac{\sin(x \pi)}{x \pi}$$, or, put another way, $$x! (-x)! = \frac{x \pi}{\sin(x \pi)}$$. This is often called “the reflection formula”, and also leads to related “reflection formulas” for other important functions in mathematics, which I may have occasion to describe here eventually. But I’ll leave that as just a teaser of the future for now...