---
id: 1804
title: Interactive charts with the R Manipulate package
date: 2012-02-02T17:16:37+00:00
author: arisamuel
type: posts
layout: single
<!-- guid: http://www.directedattention.com/?p=1804 -->
permalink: /Interactive-charts-with-R-Manipulate-package
original_post_id:
  - "1804"
categories:
  - R
  - scripts
  - Uncategorized
---
Here is a nifty way to use the manipulate package to select different variables to display on a chart.  Here we look at some fake data for website subscribers. Our factors are new monthly users in the database versus the cumulative count of users. This is an R equivalent to using the drop down in Excel. We&#8217;re basically adding a selector tool to our chart based on the available factors.

[sourcecode language=&#8221;R&#8221;]

library("manipulate")
  
library("ggplot2")

us\_users\_test us\_stage EF\_data
  
manipulate(
    
barplot(as.matrix(us\_users\_test[,factor]),
            
beside = TRUE, main=factor),
    
factor = picker("total\_users", "total\_new_users"))

manipulate(
    
barplot(as.matrix(us_stage[,factor]),
            
beside = TRUE, main=factor),
    
factor = picker("Total.Users&#8230;EOM", "Total.New.Users", "Baby", "Preg"))
  
[/sourcecode]

[<img class="alignleft size-medium wp-image-1808" title="R manipulate package - output screenshot" src="https://i2.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/manipulate_f-300x149.png?fit=300%2C148" alt="" srcset="https://i1.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/manipulate_f.png?w=1139 1139w, https://i1.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/manipulate_f.png?resize=300%2C149 300w, https://i1.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/manipulate_f.png?resize=768%2C381 768w, https://i1.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/manipulate_f.png?resize=1024%2C508 1024w" sizes="(max-width: 300px) 85vw, 300px" data-recalc-dims="1" />](https://i1.wp.com/www.samuelakerstein.com/wp-content/uploads/2012/11/manipulate_f.png)