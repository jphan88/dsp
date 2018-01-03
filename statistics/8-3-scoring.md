[Think Stats Chapter 8 Exercise 3](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77)

Input is the rate of goals per game which is denoted by lambda. The time between goals is a random expovariate. When the total time exceeds 1 the totals goals will be returned. 
```
def SimulateGame(lam):
    """Simulates a game and returns the estimated goal-scoring rate.

    lam: actual goal scoring rate in goals per game
    """
    goals = 0
    t = 0
    while True:
        time_between_goals = random.expovariate(lam)
        t += time_between_goals
        if t > 1:
            break
        goals += 1

   return goals
 ```
 The function will run the stimulation game 1000 times and use the list of estimates of goals made to find the RMSE of a more accurate lambda (goals made per game rate). The RMSE is 1.413749977 and  mean error is 0.001003. Since the mean error is small it seems that this simulation is not biased. 
 ``` 
def Estimate6(lam=2, iter=1000):

    estimates = []
    for i in range(0, iter):
        L = SimulateGame(lam)
        estimates.append(L)

    RMSE = RMSE(estimates,lam)
    meanerr = MeanError(estimates,lam)

    pmf = thinkstats2.Pmf(estimates)
    thinkplot.Hist(pmf)
    thinkplot.Config(xlabel='Goals scored', ylabel='PMF')
