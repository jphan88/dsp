[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

This will generate a random sample of 1000 numbers.  
```
      import numpy as np
      sample = np.random.random(1000)
```
This will plot the PMF and CDF  
```
              pmf_rand = thinkstats2.Pmf(sample,label='random num')
              thinkplot.Pmf(pmf_rand, linewidth=0.1)

              cdf_rand = thinkstats2.Cdf(sample,label='random num')
              thinkplot.Cdf(cdf_rand)
              thinkplot.Show(xlabel='random num',ylabel='CDF')

```
The CDF distribution is uniform as the graph appears as a straight line.
