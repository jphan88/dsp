[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

In order to find the range of U.S. males that are between the heights of 5'10 and 6'1 which is equivalent to 177.8-185.4cm I must create the distribution with mean =178 and standard deviation of 7.7. Next I will hae to find the CDF (integral) of men that fall between the range.
```
import scipy.stats

loc = 178
scale = 7.7
distrib = scipy.stats.norm(loc=loc,scale=scale)
min_height = distrib.cdf(177.8)
max_height = distrib.cdf(185.4)
range_pct = max_height - min_height
print(range_pct)

```
34.2% of U.S. men will qualify to be in the Blue Man Group. 
