[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

Find the square of the difference between estimates and actual  and return its square root of its mean
```
def RMSE(estimates, actual):
    e2 = [(estimate-actual)**2 for estimate in estimates]
    mse = np.mean(e2)
    return np.sqrt(mse)
```
n is the sample size, iter corresponds to 1000 iterations, lam corresponds to lamda (the exponential distribution parameter).
The exponential distribution is found by exponential of  1/lambda, finding it's mean, and finding the reciprocal of that. We can find the RMSE from the list of estimates which is 0.8234636561620. The 90% confidence interval is (1.2545640564302059, 3.6820013652559251).If you increase the sample size to 100, the standard error 0.21357109182 and confidence interval (1.6960554487719237, 2.3937103483053486). When the sample size is increased the standard error decreases and the confidence interval becomes narrower.
```
def SimulateSample(lam=2, n=10, iters=1000):
 
    def VertLine(x, y=1):
        thinkplot.Plot([x, x], [0, y], color='0.8', linewidth=3)

    estimates = []
    for _ in range(iters):
        xs = np.random.exponential(1.0/lam, n)
        lamhat = 1.0 / np.mean(xs)
        estimates.append(lamhat)

    stderr = RMSE(estimates, lam)
    print('standard error', stderr)

    cdf = thinkstats2.Cdf(estimates)
    ci = cdf.Percentile(5), cdf.Percentile(95)
    print('confidence interval', ci)
    VertLine(ci[0])
    VertLine(ci[1])


    thinkplot.Cdf(cdf)
    thinkplot.Config(xlabel='estimate',
                     ylabel='CDF',
                     title='Sampling distribution')

    return stderr
SimulateSample()

