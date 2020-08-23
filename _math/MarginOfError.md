---
layout: post
title:  "Margin of Error"
date: 2020-2-3
---
When polls report a “margin of error”, it doesn’t mean what almost everyone takes it to mean.

Tl;dr: In the sense of “margin of error” that you typically see reported for polls, it just means 98% / sqrt(the number of people polled).

——

When polls list a margin of error, generally they are using the formula that the margin of error is a constant divided by the square root of the sample size, where the particular constant depends on whether you are listing a 90% confidence margin of error, a 95% confidence margin of error, a 99% confidence margin of error, etc.

[Specifically, the constant used is the radius required for a mean-centered interval to capture the desired percentage of all the weight of a bell curve distribution with standard deviation 50%]

A 95% confidence margin of error is typically what’s reported, and in this case the formula as above is ≈ 98% / sqrt(sample size).

As for why this particular formula is called the “margin of error”, and the exact meaning or significance of the number calculated this way, well, that’s a longer discussion. There’s reasoning behind these formulas [TODO: expand on this in terms of standard deviation, error introduced purely by randomness of samples as opposed to systemic biases, question wording, people’s responses not matching their ultimate votes because of changing their mind or just not reporting their true dispositions, etc], but, frankly, I think calling this the “margin of error” is misleading terminology; it’s not at all easy to interpret this number, and it certainly doesn’t mean “This is the maximum amount by which these sample results may be off from the actual percentage in the population at large” or even “There’s a 95% chance that these results are not off by more than this margin”. Nonetheless, it provides some heuristic value.

For utter pedants, in case you ever see a margin of error reported that isn’t just 98% / sqrt(sample size):

This is because occasionally you’ll see poll results where they choose to make some respondents’ votes count more heavily than others’, instead of just reporting the direct percentages. (They do this to try to compensate for differences between the frequencies of various demographics in their sample vs. the frequencies of those demographics in the population at large). This changes the effective sample size, so far as the margin of error calculation goes.

Specifically, supposing each respondent is given some weight in the reported poll results, with these weights summing to 100%, the margin of error is the chosen constant (usually 98%) times the square root of the sum of the squared weights. If there were N people all given equal weight 1/N, this becomes $$98\% \times \sqrt{N \times (1/N)^2} = \frac{98\%}{\sqrt{N}}$$, as above. However, if you start giving some people different weight than others, this calculation increases.

***

TODO: Write up how the probability distribution of error due purely to randomness of samples really does just depend on the sample size, and not at all on the population size (when drawing samples at independent random with replacement). Scaling up the population does not change the probabilities of any particular occurrence on any particular sample, so all that matters is the probabilities within the population and the number of samples, not the population size. Everyone gets this wrong too, though this point (polls with small sample sizes relative to population size can still have quite small “margin of error”s and can still be quite reliable in some sense), if mis-emphasized, sort of cuts against my point above (“margin of error” calculated in this way doesn’t really tell us how reliable to find a poll as a predictor of a future vote, for many reasons; math does not give us hidden knowledge of the future).

TODO: Speak about frequentist vs Bayesian statistics, and how both are misguided in various ways, probabilities do not really capture uncertainty in most situations. (Frequentist philosophy of probability is fine, for interpretation probability in those particular contexts where this interpretation makes sense. Frequentist statistics as done in terms of p-values, confidence intervals, etc, is misguided because it doesn’t answer the questions people actually care about, instead performing sleight of hand. Bayesianism as a philosophy is misguided from the start, in presuming probabilities to represent all kinds of uncertainties, and introducing this mysterious prior, then making up arbitrary entropy-maximizing or whatever rules to guide the prior. Bayesian statistics thus continues to be misguided because of this ill-foundation)