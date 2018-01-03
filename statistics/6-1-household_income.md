[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

Find median of sample. median = 51226.4544789
```
def Median(sample)
  cdf = thinkstats2.Cdf(sample)
  return cdf.Value(.5)
 ```
Find the probability of households with incomes below the mean. It is 66%. 
```
cdf = thinkstats2.Cdf(sample)
print(cdf.Prob(sample.mean()))
```

Find Skewness which is 4.94992024443
```
def StandardizedMoment(xs, k):
  var = CentralMoment(xs, 2)
  std = math.sqrt(var)
  return CentralMoment(xs, k) / std**k
  
  def Skewness(xs):
  return StandardizedMoment(xs, 3)
  
  print(Skewness(sample))
  ```
 Find PearsonMedianSkewness which is 0.736125801914.
 ```
 def PearsonMedianSkewness(xs):
    median = Median(xs)
    mean = RawMoment(xs, 1)
    var = CentralMoment(xs, 2)
    std = math.sqrt(var)
    gp = 3 * (mean - median) / std
    return gp
   ```
The upper bound is assumed to be maxed at 1 million which limits the actual skewness of the distribution. The skewness can completely differ if the upper bound is higher. 
