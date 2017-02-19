---
id: 2134
title: Using the R Lattice package for data analysis
date: 2012-06-01T10:54:30+00:00
author: arisamuel
layout: post
guid: http://www.directedattention.com/?p=2134
permalink: /Using-R-Lattice-package-for-data-analysis
original_post_id:
  - "2134"
geo_public:
  - "0"
categories:
  - R
---
R is this language I feel like I&#8217;ve had to re-learn like 10 times. Every time I stop for more than a month it&#8217;s like starting from scratch. Very annoying. So I can have a reference and stop repeating myself I&#8217;m finally putting some of this into posts. Hopefully if you find yourself in a similar situation this&#8217;ll help. The below analysis is based on a Coursera class in data modeling using R.

Let&#8217;s first do a categorical break-out using the base package. We&#8217;ll separate groups of variables on a single scatter plot:

{% highlight r %}
y <- x + rnorm(100)
  
g <- gl(2,50)
  
g <-gl(2, 50, labels = c("male", "female"))

{% endhighlight %}
##let&#8217;s check the structure
  
str(g)
  
\# Factor w/ 2 levels "male","female": 1 1 1 1 1 1 1 1 1 1 …

{% highlight r %}
plot(x, y)
  
plot(x, y, type = "n")
  
points(x[g== "male"], y[g=="male"], col = "green")
  
points(x[g== "female"], y[g=="female"], col = "blue", pch=19)
  
title("break out male from female")
  
{% endhighlight %}

<!-- ![Ari headshot]({{ site.url }}/images/arihead.jpg) -->
[categorical scatter plot using lattice]({{site.url}}/wp-content/uploads/2013/04/malevfem_basecharts-150x150.png)
<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/malevfemalev2/" rel="attachment wp-att-2169"><img class="aligncenter size-medium wp-image-2169" src="http://www.directedattention.com/wp-content/uploads/2013/04/MaleVfemaleV2.tiff" alt="categorical scatter plot, base package" /></a>

In contrast to the base graphics package, Lattice functions generate plots in one shot rather than building them up piecewise: xyplot, bwplot, histogram, stripplot, dotplot, splom (like pairs in base system), levelplot.
  
Generically,

y ~ x | f * g

* on the left of the ~ is the y variable, on the right is the x variable
  
\* after the | are conditioning variables = they are optional; the \* indicates an interaction.
  
* lattice plots functions DIRECTLY on the graphics device
  
* lattice graphics functions return an object of the class trellis
  
* the print methods for lattice functions actually do the work of plotting the data on the graphics device
  
* lattice functions return &#8220;plot objects&#8221; that can, in principle, be stored (but it&#8217;s usually better to just save the code + data)
  
* on the command line, trellis objects re auto-printed so it appears the function is plotting the data

The following example plots y vs x conditioned on f:

{% highlight r %}
  
x <- rnorm(100)
  
y <- x + rnorm(100, sd = 0.5)
  
f <- gl(2, 50, labels = c("group 1", "group 2"))
  
xyplot(y ~ x | f)
  
{% endhighlight %}

<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/xyplot2/" rel="attachment wp-att-2171"><img class="aligncenter size-medium wp-image-2171" src="http://www.directedattention.com/wp-content/uploads/2013/04/xyplot2.tiff" alt="xyplot2" /></a>

Let&#8217;s now do a little exploration of the environmental dataset. Here&#8217;s what it looks like:

{% highlight r %}
> head(environmental)
 {% endhighlight %}
 {% highlight r %}
ozone radiation temperature wind
  
1 41 190 67 7.4
  
2 36 118 72 8.0
  
3 12 149 74 12.6
  
4 18 313 62 11.5
  
5 23 299 65 8.6
  
6 19 99 59 13.8

{% endhighlight %}
  
<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/ozonevrad/" rel="attachment wp-att-2172"><img class="aligncenter size-medium wp-image-2172" src="http://www.directedattention.com/wp-content/uploads/2013/04/OzoneVrad.tiff" alt="ozone vs. radiation" /></a>
  
Next, we&#8217;ll create a shingle variable. We&#8217;ll see shortly how useful this can be when using lattice for plotting.
 {% highlight r %}
  
summary(environmental$temperature)
  
temp.cut <- equal.count(environmental$temperature, 4) # create s shingle variable
  
help(equal.count)
  
{% endhighlight %}

Below are some details from R help below on shingles:

> A shingle is a data structure used in Trellis, and is a generalization of factors to ‘continuous’ variables. It consists of a numeric vector along with some possibly overlapping intervals. These intervals are the ‘levels’ of the shingle. The levels andnlevels functions, usually applicable to factors, also work on shingles. The implementation of shingles is slightly different from S.
  
> There are print methods for shingles, as well as for printing the result of levels() applied to a shingle. For use in labelling, theas.character method can be used to convert levels of a shingle to character strings.

Here&#8217;s what this shingle variable looks like:

 {% highlight r %}
  
> temp.cut
  
{% endhighlight %}

Data:
  
[1] 67 72 74 62 65 59 61 69 66 68 58 64 66 57 68 62 59 73 61 61 67 81 79 76
  
[25] 82 90 87 82 77 72 65 73 76 84 85 81 83 83 88 92 92 89 73 81 80 81 82 84
  
[49] 87 85 74 86 85 82 86 88 86 83 81 81 81 82 89 90 90 86 82 80 77 79 76 78
  
[73] 78 77 72 79 81 86 97 94 96 94 91 92 93 93 87 84 80 78 75 73 81 76 77 71
  
[97] 71 78 67 76 68 82 64 71 81 69 63 70 75 76 68

Intervals:
  
min max count
  
1 56.5 76.5 46
  
2 67.5 81.5 51
  
3 75.5 86.5 51
  
4 80.5 97.5 51

Overlap between adjacent intervals:
  
[1] 27 30 31


  
#next let&#8217;s plot ozone vs. radiation, conditioned on temp.cut

 {% highlight r %}
  
xyplot(ozone ~ radiation | temp.cut, data = environmental)
  
{% endhighlight %}

From the chart below we can see that the relationship between ozone and radiation is dependent on the temperature: the bottom left and right panels (in which temp is lowest and second lowest) show not much of a relationship, whereas the top left &#8211; and even more so the top right &#8211; shows an increasing relationship between radiation and ozone.

<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shinglesplot1v2/" rel="attachment wp-att-2175"><img class="aligncenter size-medium wp-image-2175" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShinglesPlot1v2.tiff" alt="lattice shingle plot" /></a>

  
#let&#8217;s modify the layout to make it more intuitive &#8211; top-bottom layout, rather than quadrants.
  
 {% highlight r %}
xyplot(ozone ~ radiation | temp.cut, data = environmental, layout = c(1, 4))
{% endhighlight %}

<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shingleplot2/" rel="attachment wp-att-2151"><img class="aligncenter size-medium wp-image-2151" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShinglePlot2.tiff" alt="shingle plot using R on environmental dataset" /></a>

 {% highlight r %}
  
xyplot(ozone ~ radiation | temp.cut, data = environmental, layout = c(1, 4), as.table = TRUE)
  
#orders from top to bottom, ascending by temperature &#8211; much better
  
{% endhighlight %}

<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shingleplot3/" rel="attachment wp-att-2153"><img class="aligncenter size-medium wp-image-2153" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShinglePlot3.tiff" alt="shingle plot reordered using R and lattice" /></a>

Finally, we can modify the layout ordering of the first chart to make it more intuitive:

 {% highlight r %}
  
> xyplot(ozone ~ radiation | temp.cut, data = environmental, layout = c(2, 2), as.table = TRUE)
  
{% endhighlight %}

<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shingleplot4/" rel="attachment wp-att-2155"><img class="aligncenter size-medium wp-image-2155" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShinglePlot4.tiff" alt="shingle plot using lattice and R on environmental dataset" /></a>

Next we will create a custom panel in which we add a regression line to each panel. This is done by creating a custom function.

We can see from the panels below that as the temperature increases, so does the ozone level with respect to radiation….

 {% highlight r %}
  
#create a custom panel function to add a regression line to each panel
  
xyplot(ozone ~ radiation | temp.cut, data = environmental, as.table = TRUE, pch=20,
         
panel = function(x, y, &#8230;){
           
panel.xyplot(x, y, &#8230;)
           
fit panel.abline(fit)
         
})
  
{% endhighlight %}

<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shingleplot5/" rel="attachment wp-att-2158"><img class="aligncenter size-medium wp-image-2158" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShinglePlot5.tiff" alt="shingle plot with regressions by panel" /></a>

But on closer inspection it looks like panel 4 (bottom right) is non-linear. Let&#8217;s try this again using another function called loess (local polynomial regression fitting).

 {% highlight r %}

xyplot(ozone ~ radiation | temp.cut, data = environmental, as.table = TRUE, pch=20,
         
panel = function(x, y, &#8230;){
           
panel.xyplot(x, y, &#8230;)
           
panel.loess(x, y)
         
}, xlab = "solar radiation", ylab = "ozone (ppb)",
            
main = "Ozone vs. Solar Radiation")
  
{% endhighlight %}

<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shingleplot6/" rel="attachment wp-att-2160"><img class="aligncenter size-medium wp-image-2160" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShinglePlot6.tiff" alt="regressions using polynomial fitting on shingles" /></a>

Now it&#8217;s looking better. In the environmental data set we have another variable, wind. let&#8217;s put this all together including the wind variable.

 {% highlight r %}
  
#first create a wind cut, similar to what we did with temp
  
wind.cut
  
\# repeat, but on the wind cut and temp cut
  
xyplot(ozone ~ radiation | temp.cut * wind.cut, data = environmental, as.table = TRUE, pch=20,
         
panel = function(x, y, …){
           
panel.xyplot(x, y, …)
           
panel.loess(x, y)
         
}, xlab = "solar radiation", ylab = "ozone (ppb)",
         
main = "Ozone vs. Solar Radiation")
  
{% endhighlight %}

<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shingleplot7/" rel="attachment wp-att-2162"><img class="aligncenter size-medium wp-image-2162" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShinglePlot7.tiff" alt="regression on multiple shingles" /></a>

we can see how the relationship changes: high temp and low/med wind is most interesting. the highlighting illustrates where we are on the two conditioning variables, temp and wind.

We can also do other interesting things in Lattice. For example we can use splom function (for scatter plot matrix) to generate a scatter plot matrix of all variables in the data set.

> splom(~ environmental)
  
<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/scatterplotmatrix/" rel="attachment wp-att-2164"><img class="aligncenter size-medium wp-image-2164" src="http://www.directedattention.com/wp-content/uploads/2013/04/ScatterPlotMatrix.tiff" alt="scatter plot matrix" /></a>

Another interesting thing we can do is generate a histogram with the conditional variable:

> histogram(~ ozone | wind.cut, data = environmental, as.table=TRUE)
  
we can see that as the wind increases the distribution changes as well &#8211; ozone is more concentrated in the lower wind ranges.
  
<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shinglehistogram/" rel="attachment wp-att-2165"><img class="aligncenter size-medium wp-image-2165" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShingleHistogram.tiff" alt="shingled histogram" /></a>

we can of course condition on both wind and temp as with the xyplot function:
  
> histogram(~ ozone | wind.cut * temp.cut, data = environmental, as.table=TRUE)
  
<a href="http://www.directedattention.com/research-and-code/r/plotting-r-simulations-using-lattice/attachment/shinglehistogram_interactions/" rel="attachment wp-att-2166"><img class="aligncenter size-medium wp-image-2166" src="http://www.directedattention.com/wp-content/uploads/2013/04/ShingleHistogram_interactions.tiff" alt="shingled histogram with interactions" /></a>
  
We can see in the bottom left panel that when the wind is low and temp high that the values of ozone are spread out, whereas in the top right panel we see that most of the ozone values are zero when the temp is low and the wind is high.