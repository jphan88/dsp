[Think Stats Chapter 6 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2007.html#toc60) (household income)

InterpolateSample function will read in the income dataframe and take in the upper income limit to be 1 million. It will take the log 10 of the upper nad lower income and create an array with the ranges and its frequencies. It will thus return the log of the sample.
```
def InterpolateSample(df, log_upper=6.0):
 
    df['log_upper'] = np.log10(df.income)

    df['log_lower'] = df.log_upper.shift(1)
    df.loc[0, 'log_lower'] = 3.0
  
    df.loc[41, 'log_upper'] = log_upper
    arrays = []
    for _, row in df.iterrows():
        vals = np.linspace(row.log_lower, row.log_upper, row.freq)
        arrays.append(vals)

 
    log_sample = np.concatenate(arrays)
    return log_sample
    ```
First read the income data and produce the log sample of the data with the upper bound being 1 million (10^6)
import hinc
```
  income_df = hinc.ReadData()
  log_sample = InterpolateSample(income_df, log_upper=6.0)
  sample = np.power(10, log_sample)

```
Find the mean of the sample. mean = 74278.7075312
```
  print(sample.mean())
 ```
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
