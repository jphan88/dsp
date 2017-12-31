[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

This will create the PMF of the number of children under 18 in a household.  

    import nsfg
    df2 = nsfg.ReadFemResp()
    pmf1 = thinkstats2.Pmf(df2.numkdhh, label = "numkdhh")
This wil find the biased PMF by first copying the pmf of pmf1 and then multiplying the x number of kids by the probability.
          def BiasPmf(pmf, label):
              new_pmf = pmf.Copy(label=label)
              for x, p in pmf.Items():
                  new_pmf.Mult(x, x)
              new_pmf.Normalize()
              return new_pmf

          BiasPmf = BiasPmf(pmf1,label='observed')
          thinkplot.PrePlot(2)
          thinkplot.Pmfs([pmf1,BiasPmf])
          thinkplot.Show(xlabel='Number of children',ylabel = 'PMF',axis = [0,6,0,1])  
          
The mean of biased PMF is 2.40367910066.

      print(BiasPmf.Mean())
The mean of actual PMF is 1.02420515504.
