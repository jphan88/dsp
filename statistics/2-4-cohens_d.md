[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

1. Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. 
  
I decided to create a histogram to compare the distribution of weights from 'first' and 'others' babies.  

        firsts = live[live.birthord == 1]
        others = live[live.birthord != 1]
        
        first_wgt = thinkstats2.Hist(firsts.totalwgt_lb)
        other_wgt = thinkstats2.Hist(others.totalwgt_lb)

        width = 0.10
        thinkplot.PrePlot(2)
        thinkplot.Hist(first_wgt, align='right', color='red', width=width)
        thinkplot.Hist(other_wgt, align='left', color='blue', width=width)
        thinkplot.Show(xlabel='weight', ylabel='frequency',xlim=[0, 16])
        
I also decided to find the means of the weights.  

      first_mean = firsts.totalwgt_lb.mean()
      other_mean = others.totalwgt_lb.mean()
      print(first_mean)
      print(other_mean)
      
The mean weight for first babies is 7.201094430437772 and for other babies is 7.325855614973262. Therefore, on average other babies tend to be heavier than first time babies.  
2. Calculate Cohen D  

        import math
        def CohenD(group1,group2):
            x1 = group1.mean()
            x2 = group2.mean()
            x1var = group1.var()
            x2var = group2.var()
            n1, n2 = len(group1), len(group2)
            s = ((n1 * x1var) + (n2 * x2var)) / (n1 + n2)
            return (x1 - x2)/math.sqrt(s)
        print(CohenD(firsts.totalwgt_lb,others.totalwgt_lb))

Cohen D is -0.088672927072602  
3. How does it compare to the difference in pregnancy length?  
The difference in pregnancy length was .029 standard deviations which is considered to be small. Likewise the difference in weight was -.089 which is also considered very small. 
