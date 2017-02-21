---
id: 1876
title: Modeling website user growth
date: 2010-04-15T13:57:10+00:00
author: arisamuel
type: posts
layout: single
guid: http://www.directedattention.com/?p=1876
permalink: /modeling-website-user-growth
original_post_id:
  - "1876"
categories:
  - Notes
  - python
  - scripts
  - Uncategorized
---
Let&#8217;s build a simple model to understand (very unrealistically!) the impact of virality on user growth. That is, what is the impact of the spread rate on reaching a target number of users. The model will take several arguments as input: the number of starting users, the spread rate &#8211; how many friends a user will recruit, and the end target number of users. The output will be the number of cycles, let&#8217;s say months, to reach the target. In our case we hope our little startup will IPO after reaching the target!

So if we want to reach, say, 5 million users, how many months will it take if we start with 100 users with a spread rate of 2/user?

[sourcecode language=&#8221;python&#8221;]

\# Define a procedure that takes three inputs: the starting number of users, the spread
  
\# rate (how many new friends each user convinces to join per month),
  
\# and the target number, and outputs the number of months needed to reach
  
\# (or exceed) the target.

def users\_to\_ipo(n, spread, target):
      
if n >= target:
          
return 0
      
else:
          
return 1 + users\_to\_ipo(n * (1 + spread), spread, target)

\# let&#8217;s test some use-cases:

\# 0 more needed, since n already exceeds target
  
print users\_to\_ipo(100000, 2, 40000)
  
#>>> 0

\# after 1 cycle, there will be 100+ (100 * 2) users
  
print users\_to\_ipo(1000, 2, 3000)
  
#>>> 1

\# months needed to match or exceed the target
  
print users\_to\_ipo(50000, 2, 150001)
  
#>>> 2

\# only 13 months to exceed the current population of 7b!
  
print users\_to\_ipo(100, 2, 7 \* 10 \** 7)
  
#>>> 13

\# more friends means faster world domination!
  
print users\_to\_ipo(15000, 3, 7 \* 10 \** 7)
  
#>>> 10

#the original question:
  
print users\_to\_ipo(100, 2, 5000000)
  
#>>> 10

[/sourcecode]

So it takes 10 months to reach our target of 5MM. This is definitely an optimistic model and one that will need some refining before we secure funding for our venture!