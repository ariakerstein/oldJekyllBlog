---
id: 1498
title: Random Sampling in R
date: 2012-02-12T05:06:03+00:00
author: arisamuel
layout: post
guid: http://www.directedattention.com/?p=1498
permalink: /random-sampling-r
original_post_id:
  - "1498"
categories:
  - Notes
  - R
  - Uncategorized
tags:
  - R
---
[code language=&#8221;splus&#8221;]

A few quick notes on random sampling in R:

#random Sample of 5 numbers from 1:500
  
sample(500,5)

#input a vector x
  
x<-c(22, 23,21,34,67,78,45,34,23,45,56,76,56)

#sample from x with replacement
  
sample(x,5,replace=T)

#create random vector, y, of random permutation of 1:15
  
y <- sample(15)

#create a vector, y, to contain 5 through 15. Then sample randomly
  
y <- sample(5:15)
  
[/code]