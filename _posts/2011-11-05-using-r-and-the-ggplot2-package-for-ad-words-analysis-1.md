---
id: 878
title: Using R for PPC regression analysis
date: 2011-11-05T21:27:09+00:00
author: arisamuel
type: posts
layout: single
guid: http://www.diffusionreactor.com/?p=878
permalink: /?using-r-ppc-analysis
gwo4wp:
  - 'a:4:{s:7:"enabled";s:0:"";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
  - 'a:4:{s:7:"enabled";s:0:"";s:14:"control_script";s:0:"";s:15:"tracking_script";s:0:"";s:17:"conversion_script";s:0:"";}'
ks_metadata:
  - |
    a:7:{s:4:"lang";s:2:"en";s:8:"keywords";s:76:"reg,total,cost,csv,data,keymarkets_paidsearch_adwords_ef_2011,market,markets";s:19:"keywords_autoupdate";s:1:"1";s:11:"description";s:165:"Reg, colour = Portfolio) + geom_smooth(method=&quot;lm&quot;, se=T) Here's what the output looks like (with a minor annotation added after the fact). We can see that";s:22:"description_autoupdate";s:1:"1";s:5:"title";s:0:"";s:6:"robots";s:12:"index,follow";}
kdc_metadata:
  - 'a:1:{s:4:"lang";s:2:"en";}'
original_post_id:
  - "878"
categories:
  - R
  - scripts
  - Uncategorized
---
Analyzing paid search campaigns in many markets can sometimes be overwhelming. Too much data locked in too many spreadsheets. It can sometimes be difficult to actually see what is happening across each market at once. I recently discovered Wickham&#8217;s ggplot2 for R data visualization. Generally I&#8217;ll use Pivot tables for quick & dirty analysis of ad words campaign performance. Rather than writing a macro let&#8217;s write an R script to automate some of this.

Below is a quick look at two regressions plotting some (fake) company data for registrations versus ad words spend.

<pre>KeyMarkets_PaidSearch_AdWords_EF_2011 &lt;- read.csv("~/Dropbox/R/DataSets/Acquisition/KeyMarkets_PaidSearch_AdWords_EF_2011.csv")

qplot(Cost, Total.Reg, colour = Portfolio) + geom_smooth(method="lm", se=T)</pre>

Here&#8217;s what the output looks like.

<p style="text-align:center;">
  <a title="multiple regression by portfolio" href="http://www.directedattention.com/research-and-code/simple-scripts/using-r-and-the-ggplot2-package-for-ad-words-analysis-1/attachment/multipleregressionbyportfolio/" rel="attachment wp-att-2211"><img class="aligncenter  wp-image-2211" title="Linear Regression by Portfolio" alt="Regression by Portfolio" src="https://i1.wp.com/www.samuelakerstein.com/wp-content/uploads/2013/08/multipleregressionbyportfolio.png?resize=300%2C201" srcset="https://i1.wp.com/www.samuelakerstein.com/wp-content/uploads/2013/08/multipleregressionbyportfolio.png?w=550 550w, https://i1.wp.com/www.samuelakerstein.com/wp-content/uploads/2013/08/multipleregressionbyportfolio.png?resize=300%2C201 300w" sizes="(max-width: 300px) 85vw, 300px" data-recalc-dims="1" /></a>
</p>

[<img title="Regression by market" alt="" src="https://i1.wp.com/www.diffusionreactor.com/wp-content/uploads/2011/11/Rplot1.png?resize=670%2C455" data-recalc-dims="1" />](https://i1.wp.com/www.diffusionreactor.com/wp-content/uploads/2011/11/Rplot1.png)

We can see that Brazil looks great and Mexico is showing promise.

Next I ran a regression combining all the markets.

<pre>library(ggplot2)

#import dataset
KeyMarkets &lt;- read.csv("~/Dropbox/R/DataSets/Acquisition/KeyMarkets_PaidSearch_AdWords_EF_2011.csv")
attach(KeyMarkets)

#To add faceted regressions just add this argument: facet_grid(. ~ Portfolio)
#note that the argument se=T was added for explicitness. The default is set to True.
qplot(Cost, Total.Reg, data=KeyMarkets, main="Total Reg vs. Cost in Key Markets") + geom_smooth(method="lm", SE=T)</pre>

Below is the chart this generates. Note the grey band is the Standard error.

[<img class="alignnone size-full wp-image-881" title="Regression on all markets" alt="" src="https://i1.wp.com/www.diffusionreactor.com/wp-content/uploads/2011/11/AllMarketsRegression.png?resize=560%2C379" data-recalc-dims="1" />](https://i1.wp.com/www.diffusionreactor.com/wp-content/uploads/2011/11/AllMarketsRegression.png)

Finally, let&#8217;s have a look at the relative competitiveness by market. We&#8217;ll do a scatter plot of the cost per registration versus the total registrations to get both a sense of spend efficiency as well as volume.

<pre># let's plot efficiency, reg vs. CPR
qplot(Cost/Total.Reg, Total.Reg, data=KeyMarkets,
      colour = factor(Portfolio),
      main="Performance by Key market: CPR vs. Volume")</pre>

[<img class="alignnone size-full wp-image-886" title="CPR2" alt="" src="https://i2.wp.com/www.diffusionreactor.com/wp-content/uploads/2011/11/CPR2.png?resize=670%2C455" data-recalc-dims="1" />](https://i2.wp.com/www.diffusionreactor.com/wp-content/uploads/2011/11/CPR2.png)

This is a fantastic package with lots of flexibility to create custom charts based on the data. In future posts I&#8217;ll plan to build on these and take advantage of the flexibility contained in this package.