---
id: 1868
title: Fibonacci in Python
date: 2011-11-14T21:45:51+00:00
author: arisamuel
layout: post
guid: http://www.directedattention.com/?p=1868
permalink: /?p=1868
original_post_id:
  - "1868"
categories:
  - Notes
  - python
  - scripts
  - Uncategorized
---
Here&#8217;s some python code to define a fibonacci sequence in python two ways: recursively and then non-recursively. The reason to write this non-recursively is that due to the nature of this sequence &#8211; in which the next result relies on the previous results &#8211; we end up making A LOT of redundant computations.

<img class="alignleft size-medium wp-image-1873" title="Fibonacci sequence" src="https://i0.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/fibonacci-300x186.png?fit=300%2C185" alt="" srcset="https://i0.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/fibonacci.png?w=802 802w, https://i0.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/fibonacci.png?resize=300%2C186 300w, https://i0.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/fibonacci.png?resize=768%2C476 768w" sizes="(max-width: 300px) 85vw, 300px" data-recalc-dims="1" />

This code is based on Udacity&#8217;s CS101 programming in Python course. The Fibonacci sequence can best be understood as the golden rectangle and has been seen in Greek architecture, flowers and perhaps most famously in Leonardo&#8217;s Mona Lisa and <a title="Vitruvian Man" href="http://en.wikipedia.org/wiki/Vitruvian_Man" target="_blank">Vitruvian man</a>.

[sourcecode language=&#8221;python&#8221;]
  
\# recursive fibonacci definition
  
def fibonacci(n):
      
if n < 2:
          
return n
      
else:
          
return fibonacci(n-2) + fibonacci(n-1)
  
[/sourcecode]

Let&#8217;s now write this in a way that computes faster. Why should it be faster? Because the number of computations in the previous code is many. How many? Well it turns out to be exactly the number of fibonacci sequences, n.

[sourcecode language=&#8221;python&#8221;]
  
#faster fibonacci since this is NOT recursive
  
def fibonacci(n):
      
current = 0
      
after = 1
      
for i in range(0,n):
          
current, after = after, current + after
      
return current

[/sourcecode]

And now the fun part. If bunnies (at 2kg/bunny) could multiply (and never die!) in Fibonacci fashion how long until they exceed the mass of earth? That is, how many cycles of bunny procreation would it take before they outweigh our fair planet.

[sourcecode language=&#8221;python&#8221;]
  
#how long until mass of rabbits exceeds mass of earth?
  
mass\_of\_earth = 5.9722 \* 10\**24 # in kilos
  
mass\_of\_rabbit = 2 # 2 kg per rabbits

n = 1
  
while fibonacci(n)*mass\_of\_rabbit < mass\_of\_earth:
      
n = n + 1
  
print n, fibonacci(n)
  
[/sourcecode]

. . . Turns out the answer is 119.