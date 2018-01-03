[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

In order to find the correlation, covariance must be found first. Covariance is the dot product of the difference between the value and its mean. The correlation will be found by dividing the covariance by the square root of the variance of x * variance of y. The correlation is 0.0688339703541
```
def Cov(xs, ys, meanx=None, meany=None):
    xs = np.asarray(xs)
    ys = np.asarray(ys)

    if meanx is None:
        meanx = np.mean(xs)
    if meany is None:
        meany = np.mean(ys)

    cov = np.dot(xs-meanx, ys-meany) / len(xs)
    return cov
def Corr(xs, ys):
    xs = np.asarray(xs)
    ys = np.asarray(ys)

    meanx, varx = thinkstats2.MeanVar(xs)
    meany, vary = thinkstats2.MeanVar(ys)

    corr = Cov(xs, ys, meanx, meany) / np.sqrt(varx * vary)
    return corr

import first

live, firsts, others = first.MakeFrames()
live = live.dropna(subset=['agepreg', 'totalwgt_lb'])
ages = live.agepreg
weights = live.totalwgt_lb

print(Corr(ages, weights))
```
The SpearmanCorr is 0.0946100410966.
```
def SpearmanCorr(xs, ys):
    xs = pd.Series(xs)
    ys = pd.Series(ys)
    return xs.corr(ys, method='spearman')
print(SpearmanCorr(ages,weights))
```
Plot the scatter plot to see the relationship between age and weight. It seems the relationship is very weak as the scatter plot appears to be quite flat on the graph.
```
thinkplot.Scatter(ages, weights, alpha=1.0)
thinkplot.Show(xlabel='Age (years)',
                     ylabel='Birth weight (lbs)')
                    

