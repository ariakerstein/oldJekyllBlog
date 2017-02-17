---
id: 1524
title: Python script to loop over a list
date: 2011-03-13T16:34:20+00:00
author: arisamuel
layout: post
guid: http://www.directedattention.com/?p=1524
permalink: /python-script-loop-over-a-list
original_post_id:
  - "1524"
categories:
  - scripts
tags:
  - python
  - scripts
---
Below is some python code to loop over a list of lists and return some output. In this case we have 2 lists of websites and want to return some KPIs &#8211; page views, unique visitors, and engagement (page views/visitor) &#8211; at the list level.

[sourcecode language=&#8221;python&#8221;]
  
\# define a procedure, called traffic, that takes as input
  
\# a list and returns as output three numbers providing the
  
\# total number of page views, unique visitors
  
\# and page views per visitor.
  
\# For now we will not worry about sig figs.

list_1 = [[&#8216;site&#8217;,4500,25000]]

list_2 = [ [&#8216;site1&#8217;,2175,37704],
  
[&#8216;site2&#8217;,19627,39849],
  
[&#8216;site3&#8217;,10566,40732],
  
[&#8216;site4&#8217;,7802,37000],
  
[&#8216;site5&#8217;,5879,35551],
  
[&#8216;site6&#8217;,19535,40569],
  
[&#8216;site7&#8217;,11701,40500]  ]

def total_traffic(p):
	  
total\_unique\_visitors = 0
	  
total\_page\_views = 0
	  
for site, unique\_visitors, page\_views in p:
		  
total\_unique\_visitors = total\_unique\_visitors + unique_visitors
		  
total\_page\_views = total\_page\_views + page_views
		  
pv\_uv = total\_page\_views / total\_unique_visitors
	  
return total\_unique\_visitors, total\_page\_views, pv_uv

print total\_traffic(list\_1)
  
#>>> (4500, 25000, 5)
  
print total\_traffic(list\_2)
  
#>>> (77285, 271905, 3)
  
[/sourcecode]