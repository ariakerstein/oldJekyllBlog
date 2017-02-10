---
id: 1285
title: Everyday Poisson
date: 2012-06-18T16:17:42+00:00
author: arisamuel
layout: post
guid: http://www.directedattention.com/?p=1285
permalink: /?p=1285
original_post_id:
  - "1285"
categories:
  - Notes
  - Uncategorized
tags:
  - R
  - statistics
---
The Poisson distribution is both extremely useful and quite under-utilized in everyday applications. The basic idea is that if a historical quantity of success events are known, then it is possible to predict the probability of future such successes per unit time or space. Classical applications include defects on a sheet of metal, given a known defect rate and number of cars crossing a bridge, given known traffic rates.

Consider the following

P(_x_; μ) = (e<sup>-μ</sup>) (μ<sup>x</sup>) / x!

_e_: ~ 2.71828

μ: The mean number of successes that occur in the region of interest

_x_: The actual number of successes that occur in the region of interest

P(_x_; μ): The **Poisson probability** that **exactly** _x_ &#8216;successes&#8217; occur in a Poisson experiment, when the mean number of successes is μ. Note the plain fact that this distribution relies on historical precedent, μ,  to make future predictions. So please heed the wisdom of Sir Isaac Newton who famously lost a fortune in the South Sea Bubble:

> I have learned to _predict_ the movement of celestial _bodies_ but not the movement of _man_ in markets

That said, let&#8217;s take an example:

Suppose we want to know the probability of having fewer than four people in Starbucks line tomorrow? We already know that the mean number of people in line at 10:00 am is 8 will need to calculate the sum of probabilities for each case. (Note how this is similar to other mathematical expectation,  for example as in understanding payoff of a game of dice).

P(x <span style="text-decoration:underline;"><</span> 3, 8) = P(0; 8) + P(1; 8) + P(2; 8) + P(3; 8)

Typically we&#8217;ll want to know the probability that the Poisson random variable is greater than some specified lower limit and less than some specified upper limit. For this we use a **cumulative Poisson probability. **

****We can do this easily in R (note that lambda is used instead for μ). So in our example, if we wanted to know the probability of fewer than 4 people waiting in line we would use the lower.tail=TRUE argument.

&nbsp;

> ppois(4, lambda=8, lower.tail=TRUE)

&nbsp;

[1] 0.0996324

So the probability of having fewer than 4 people waiting in line is 9.9%

> ppois(4, lambda=8, lower.tail=FALSE)

[1] 0.9003676

whereas the probability of having greater than 4 people in line is much higher, 90%.

&nbsp;