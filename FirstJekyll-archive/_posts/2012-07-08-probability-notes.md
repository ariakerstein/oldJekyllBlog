---
id: 1362
title: Probability notes
date: 2012-07-08T06:58:02+00:00
author: arisamuel
layout: post
guid: http://www.directedattention.com/?p=1362
permalink: /probability-notes
original_post_id:
  - "1362"
categories:
  - Science, Experiments and Technical Stuff
  - Uncategorized
---
[latexpage]

I&#8217;ve decided that in order to keep my brain from rotting &#8211; it can happen quickly in business if you&#8217;re not careful &#8211; I thought I&#8217;d embark on a project to itemize and deepen my understanding of probability. So here we go:

Below are some study notes on probability &#8211; more for personal reference than anything else (I tend to lose notebooks). This&#8217;ll also give me a good excuse to work my LaTex skills.

**Sample Space & Events: **

The set of all possible experimental outcomes is called the sample space, S. An event, A, is a set of outcomes &#8211; a subset of S. Note that $emptyset $ and S itself are subsets of S, and hence are considered events. Events can be combined to form new events using set operators: $ A cap B $ is the event that occurs iff A OR B occurs (or both) $ A cup B $ is the event that occurs iff A AND B occurs $ A^complement$ is the complement of A &#8211; the event that occurs if A does NOT occur. Two events are mutually exclusive if $A cap B = emptyset $

**Finite Probability Spaces &#8211;** **(Equiprobable space):  **

Suppose S contains n points in an equiprobable space &#8211; the various outcomes of the sample space have equal probabilities &#8211; then the probability of each point is 1/n. Note this cannot be generalized to spaces that are non-equiprobable. If an event A contains r points then the probability is r(1/n) = r/n We can say that $$P(A) = frac { n(A)} {n(S)} $$, where n(A) is the number of elements in a set A. The saying, &#8220;at random&#8221; can only apply to an equiprobable space.

****Finite Probability Spaces &#8211;** (Addition Principle):** For any events A and B, $$ P(Acup B) = P(A) + P(B) &#8211; P(A cap B) $$

**Conditional Probability:**

Suppose E is an event in S with P(E) > 0. The probability that an event A occurs once E has occurred &#8211; _the conditional probability of A given E &#8211; _is given by, $$ P(A|E) = frac {P(A cap E)} {P(E)} $$. If S is an equiprobable space with events A and E, then, $$ P(A|E) = frac {n(A cap E)} {n(E)}  $$

**(multiplication theorem for conditional probability):  **

If we take the definition of conditional probability, $$ P(B|A) = frac {P(A cap B)} {P(A)}  $$ and multiply the both sides by P(A), we get the following useful definition: $$ P(A cap B) = P(A) P(B|A) $$ Note this can easily be extended to three or more events.

**Independent Events:**

Events A and B are independent if $$P(Acap B) = P(A) P(B)$$, otherwise they are dependent.

**Independent Repeated Trials, Binomial Distribution&#8230;****_Repeated trials with two outcomes, Bernoulli Trials, Binomial Experiment_:**

p = probability of success; q = 1 &#8211; p, the probability of failure. A binomial experiement consists of a fixed number of Bernoulli trials with B(n, p) denoting a binomial experiment with n trials with p probability of success.  The probability of k successes, P(k) = $$ C_r =  {nchoose k} = frac {n!}{k!(n-k)!} $$ $$ [P(E) = {n choose k} p^k (1-p)^{ n-k} $$

**Random Variables:**

We frequently wish to assign a number to each outcome in an experiment. For example, if we flip a coin, the outcomes are H or T; if we toss a pair of dice the outcomes are a pair of integers. Let&#8217;s say we want to assign 1 to H, or assign the sum of the two integers to the outcome. For this we will use a random variable: A random variable  $mathrm{X}$ is a rule that assigns a numerical value to each outcome in a sample space S. Let $R\_mathrm{X}$ denote the set of numbers assigned by a random variable $mathrm{X}$. $R\_mathrm{X}$ is called the _range space_.

_TBC in a later post&#8230;._