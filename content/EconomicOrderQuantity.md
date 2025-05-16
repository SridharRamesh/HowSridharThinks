---
title: "Supply Chain Theory: The Economic Order Quantity"
date: 2018-12-19
---

I have a job now where I do stuff with supply chains and inventory control/optimization. I'd never thought about or been aware of any of this stuff before, but it turns out there's a surprisingly large amount of interesting math in "supply chain theory". So, inbetween my explorations of pure math for pure math's sake on this (infrequently updated…) blog, I'll also be posting recaps/explanations of this supply chain math, for my own reference.

***

Today, I'll start by discussing the very first problem in this field I ever saw, the so-called "Economic Order Quantity" problem. (For what it's worth, "Economic" here means something like "optimal to minimize costs").

The setup of this problem is this: Suppose you are running a store which sells an item, and which experiences demand for quantities of that item at a constant rate over time. You have a certain amount of inventory of that item, which depletes via this demand but can be replenished via placing an order to your supplier (which will be delivered immediately, we can imagine for now). These orders can be for any finite quantity of the item you like, but will carry a flat (aka, "fixed") transaction cost. You also must pay a "holding cost" over time, which is at any moment proportional to the current amount of unsold inventory you hold.

(This holding cost is meant to capture the burden of having to take up space and logistics in your store/warehouse/whatever handling unsold inventory. In the real world, considering it linear in this way may not be realistic, but hey, it makes for nice math. In later, more sophisticated problems, we'll occasionally think about non-linear holding costs as well, although still from the perspective of what makes for nice math; this is a math blog, after all.)


Under the constraint that you MUST always carry enough inventory to satisfy demand (i.e., if your inventory drops to zero, you are forced to place an order, so as to be able to keep satisfying imminent demand), what is the optimal strategy for when to place orders of what size, in order to minimize your costs (in the sense of their average rate over time)?


Note, first of all, that there is a memoryless property to this system: Whatever the optimal strategy is when you are currently at an inventory level of L, it will be the same optimal strategy every time you come to inventory level L, regardless of what you've done so far (because the cost dynamics going forward are similarly memoryless).

And secondly, note that you should never place an order at a moment when you have nonzero inventory: by doing so, you will incur early holding costs on the items to be delivered, costs which could be avoided by waiting a bit and placing the order later (and if you delay ordering long enough that you can combine two previously distinct planned orders into one, you can also reduce the number of transaction costs involved). The only situation in which you can't delay ordering is when you've hit zero inventory and have to place an order to keep going.

Thus, the optimal strategy is to place orders of some constant size every time your inventory hits zero, and never at any other time.

But what size should that order be? Well, this depends on the rate of demand, transaction cost, and holding cost rate.

Specifically, if the rate of demand is $$\lambda$$, and one places orders of size $$Q$$ on each required replenishment, then the frequency of replenishments will be $$\frac{\lambda}{Q}$$. If the transaction cost is $$K$$, and the holding cost is $$h$$ per item per unit of time, then the amortized rate at which costs are paid will be $$\frac{K \lambda}{Q} + \frac{Qh}{2}$$ (the first term here comes from the transaction costs, and the second term here comes from the holding costs, noting that the amount of inventory over time will be uniformly distributed between $$Q$$ and $$0$$, and thus $$\frac{Q}{2}$$ on average).

What's important about this expression is that it contains one term directly proportional to $$Q$$ (the holding costs) and one term inversely proportional to $$Q$$ (the transaction costs).

Thus, the geometric mean of these two terms is a constant, and by applying the inequality of geometric and arithmetic means, we know the minimum is reached when the two terms are made equal, at which point the sum is twice that geometric mean.

Specifically, letting $$A = K \lambda$$ and $$B = \frac{Q}{2}$$ for convenience, our sum is $$A/Q + BQ$$, the geometric mean of its two terms is $$\sqrt{AB}$$, the sum is minimized when the two terms are made equal by setting $$Q = \sqrt{A/B}$$, and in this case the sum comes out to $$2 \sqrt{AB}$$.

We have now completely solved the "Economic Order Quantity" problem, as such. This is just a simple toy problem, just an exercise in elementary algebra, but it begins to illustrate the idea of trade-offs of holding costs vs. order frequency, which often comes up in supply chain theory.

(You may note how we did not consider in our analysis either the revenue gained from selling items, or the cost per item our supplier may charge us beyond the fixed transaction cost of placing an order in itself. These might be considered the two most basic terms of the profit of our business! But that's because these are both irrelevant to the minimization problem at hand: the rate of revenue gained from selling items is constant, given the constant demand, and similarly, since we purchase items at the same amortized rate that we sell them, the corresponding component of the ordering cost is constant as well.)

Incidentally, note how, by suitable choice of units, every instance of this problem is simply an examination of the dynamics of the function $$X + \frac{1}{X}$$; this tells us how poorly we do if instead of choosing the optimal $$Q$$, we instead must choose a value $$rQ$$ (modifying the order quantity from its optimal value by a factor of $$r$$ will inflate the incurred costs by a factor of $$\left(r + \frac{1}{r}\right)/2$$). And, by connecting this problem to the arithmetic/geometric mean inequality, we quickly connect it to a whole web of interesting and well-studied other mathematics.

Much of this is obscured in all the traditional writeups of the Economic Order Quantity I see, which, instead of noting the arithmetic/geometric mean inequality, carry out the optimization by taking derivatives and setting the derivative to zero. This does at least connect to another notable aspect of the problem which comes up again throughout supply chain theory (the "convexity" of the cost function whose minimum is sought, such that the minimum is precisely the point at which marginal costs shift from decreasing to increasing), but at the cost (heh) of making it seem far less elementary than it really is (as though it requires calculus, and not merely basic algebra). C'est la vie.

***

Anyway, I will likely have another post on the arithmetic/geometric mean inequality to come at some point, as well as a post on the concept of function convexity, both from the point of view of pure mathematics and highlighting some of its extremely important applications in supply chain theory (including the generalization to the concept of "K-convexity", a beautiful bit of mathematics that seems to live in supply chain theory alone and not yet have found other uses).
