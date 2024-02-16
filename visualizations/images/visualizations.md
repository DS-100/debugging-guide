---
title: Visualizations
format:
  html:
    toc: true
    toc-depth: 5
    toc-location: right
    code-fold: false
    theme:
      - cosmo
      - cerulean
    callout-icon: false
jupyter: python3
---

Visualizations are how data scientists use to communicate their insights to the world. In the process of making a [good visualization](https://ds100.org/course-notes/visualization_2/visualization_2.html#harnessing-context), be it while adding a legend or setting the x-axis label, we may run into some errors. Let's take a look at how to resolve them below!


### My legend’s labels don’t match up / my legend isn’t displaying properly

If you simply add `plt.legend()` after your plotting line of code, you should see a legend. When using seaborn, sometimes it will automatically populate the legend. However, if you’re plotting multiple lines or sets of points on a single plot, the labels in the legend may not correctly line up with what’s shown. 

Make sure to pass in the `label` argument into the function call with the label you want associated with that individual plot. For example, 

```
sns.histplot(means_arr, label = 'simulated values') # informative label name
plt.title('Simulated values') 
plt.plot(original, 10, 'bo', label = 'original test statistic') # informative label name
plt.legend(loc = 'upper left') # can specify location of legend
```
<center><img src = "example_label_plot.png" width = "500"></img></a></center>
<br>

## The y-axis of my `histplot` shows the count, not the density

Look into the `sns.histplot` [documentation](https://seaborn.pydata.org/generated/seaborn.histplot.html) and see what arguments the `stat` parameter takes in. By default, `stat=count`, but if you wanted to normalize the distribution such that the total area is 1, you could consider passing `stat=density` into the plot function.


