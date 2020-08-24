---
title:  "Queues and the Erlang B-Theorem"
date: 2020-8-12
---
Suppose you have a queue with finite capacity C, such that the queue can be entered whenever it has less than C people in it already, but the queue permanently turns away anyone who shows up while it has C people in it.

Suppose also that people show up to the queue as a Poisson process with rate $$\lambda$$, and once in the queue, remain in it for a random time independently drawn from a fixed distribution before leaving. In jargon (Kendall notation), this is an M/G/C/C queue, or "Erlang loss system".

Let's use $$f$$, $$F$$, and $$\mu$$ to stand for the density, cumulative distribution function, and mean of the distribution prescribing how long an entrant spends in the queue. (We'll allow ourselves to use Dirac densities and the like as well, so the results do not apply only to continuous distributions).

This system is a continuous-time Markov process on the continuous state-space of "Number of people currently in the queue and the amount of time each has spent within it". We can represent a state as a set $$T = \{(t_1, s_1), \ldots, (t_{ \vert T \vert }, s_{ \vert T \vert })\}$$ where $$ \vert T \vert  \leq C$$, with $$t_i$$ representing the time someone has spent already in the queue and $$s_i$$ representing the remaining time till they leave the queue.

This actually keeps track of more information than we need for evolving the dynamics; just keeping track of $$t_i$$ would suffice, using suitable stochastic dynamics for determining queue exits. But the result for this full information is pretty, so I might as well show it.

Over time, the probability distribution on the state space settles to a unique stationary one.

In particular, the stationary distribution is given by a density function proportional to $$p(T) = \prod_i [\lambda f(t_i + s_i)] = \lambda^{ \vert T \vert } \prod_i f(t_i + s_i)$$ (for allowed values $$ \vert T \vert  \leq C$$). (This is a density function in the sense of multiplying by $$\prod_i \delta t_i \delta s_i$$ to give the probability captured by allowing this much interval around each value). The actual density function is obtained by normalizing this to have total integral 1, of course. Note that the queue capacity $$C$$ only barely enters into this, just to determine the window of support!

To prove this is a stationary density, consider the dynamics of the system. It's a little tricky, because both time and state are continuous, while events include both continuous processes (aging of the amount of time spent in the queue) and discrete processes (arrivals and exits from the queue). But what we get is like so:

Consider the big old Markov chain graph of all states and all transitions over a fixed infinitesimal time period: The transitions are infinitesimal aging, queue entrances (technically, infinitesimal aging + queue entrance), and queue exits (technically, infinitesimal aging + queue exit).

Most states $$T$$ have two edges in and two edges out: You can age into them or age out of them, and you can queue exit into them or queue entrance out of them.

In our distribution $$p$$, because it is constant as all $$t_i$$ go up and all $$s_i$$ go down by the same amount, the flow into such a node via aging matches the flow out of that node by aging; the purely aging dynamics do not change the value of such a node.

The flow into a node by queue exit and the flow out of a node by queue entrance also match up: If $$ \vert T \vert  = C$$, these are both impossible. Otherwise, the rate of queue exit taking us to $$ \vert T \vert $$ is the integral over all $$(t, 0)$$ of $$p( \vert T \vert  \cup \{(t, 0)\} dt$$, which comes to $$\lambda p( \vert T \vert )$$. This matches the rate of queue arrival taking us out of state $$ \vert T \vert $$. [TODO: Be careful about the dt ds in (t, 0) here and in general]

There are some special states that cannot be aged into or aged out of. If a state has a $$t_i = 0$$, it cannot be aged into, but it CAN be queue arrivaled into. The amount of density which flows out of such $$T \cup \{0, s\}$$ by aging is all of $$p(T \cup \{0, s\})$$. And the queue arrivals come at exactly the rate to balance all the density aging out: The rate of queue arrivals into $$T \cup \{0, s\}$$ is $$\lambda f(s) p(T) = p(T \cup \{0, s\})$$.

If a state has a $$s_i = 0$$, it cannot be aged out of, but it WILL be queue exited out of. Here, aging in and queue exiting out exactly balance out. The amount of density which ages into such $$T \cup \{t, 0\}$$ is precisely $$p(T \cup \{t, 0\})$$, by the constantness of $$p$$ with respect to aging. And all density in such $$T \cup \{t, 0\}$$ will immediately queue exit out, so the amount which flows out is the same $$p(T \cup \{t, 0\})$$.

Thus, everything is in perfect balance and $$p$$ is indeed stationary, as claimed.

Anyway, having derived these densities, we can then integrate them to find that the probability of having precisely $$n$$ many people in the queue is proportional to $$\frac{\left(\lambda \mu\right)^n}{n!}$$. (The $$n!$$ comes from the fact that the integral we most naturally set-up counts $$T$$ a total of $$ \vert T \vert !$$ many times). This is called the Erlang B-Theorem. Note that the specific distribution given by $$f$$ no longer matters beyond its mean.

From this, we can quickly determine the mean number of people in the queue, either as an explicit sum over all $$n$$, or as the integral of $$\lambda$$ times the probability of not being full times $$(1 - F(t))$$, describing how many people tried to enter the queue in the past, arrived at a time when it wasn't full, and are still there. This simplifies to $$\lambda \mu$$ times the probability of not being full.

And once we know the expected number of people in the queue, we can also use this to model a line of infinite parking spaces 0, 1, 2, 3, …, with each person showing up taking the lowest-numbered space available. What I mean by this is, the probability that spot X is occupied at any moment is precisely the mean number of people in the first (X + 1) spots minus the mean number of people in the first X spots. Our previous formula gives us those values readily, since these amount to the same as looking at queues of capacity (X + 1) and X. This is a nice application on which to end this post. Indeed, it is the application which, in the form of a trivia question, first brought me to thinking about this.

***

Much of the above was drawn from https://math.stackexchange.com/questions/483160/hilberts-barber-shop, inspired by a Learned League question, and then also augmented after reading about the "insensitivity" of Erlang's B-theorem, allowing generalization to general distributions.