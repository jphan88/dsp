[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)

This function input will be two groups: pregnancy length and birthweight. It will find the difference in means by using resampling. The  p value, actual value, and MaxTestStat will be found to compare the two groups.
The pregnancy length values are : p-value = 0.164 actual = 0.078 ts max = 0.215. The birthweight values are:  p-value = 0 actual = 0.125
ts max = 0.106. The resampling model does not have much affect than the permutation model.

```
class DiffMeansResample(DiffMeansPermute):
    """Tests a difference in means using resampling."""
    
    def RunModel(self):
      
        group1 = np.random.choice(self.pool, self.n, replace=True)
        group2 = np.random.choice(self.pool, self.m, replace=True)
        return group1, group2
    def RunResampleTest(group1,group2):
   

    data = group1.prglngth.values, group2.prglngth.values
    ht = DiffMeansResample(data)
    p_value = ht.PValue(iters=10000)
    print('\ndiff means resample preglength')
    print('p-value =', p_value)
    print('actual =', ht.actual)
    print('ts max =', ht.MaxTestStat())

    data = (firsts.totalwgt_lb.dropna().values,
            others.totalwgt_lb.dropna().values)
    ht = DiffMeansPermute(data)
    p_value = ht.PValue(iters=10000)
    print('\ndiff means resample birthweight')
    print('p-value =', p_value)
    print('actual =', ht.actual)
    print('ts max =', ht.MaxTestStat())
