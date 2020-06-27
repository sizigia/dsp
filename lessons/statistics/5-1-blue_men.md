[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

**Exercise 1**  
*In the BRFSS (see Section 5.4), the distribution of heights is roughly normal with parameters µ = 178 cm and σ = 7.7 cm for men, and µ = 163 cm and σ = 7.3 cm for women.
In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.*

```python
import scipy.stats as ss

mu = 178
sigma = 7.7

distrib = ss.norm(loc=mu, scale=sigma)

def ft_to_cm(ft, in_=None):
    length = ft * 30.48
    if in_:
        length += (in_ * 2.54)
    return length

lower_bound = ft_to_cm(5, 10)
higher_bound = ft_to_cm(6, 1)

low = distrib.cdf(lower_bound) * 100
high = distrib.cdf(higher_bound) * 100

print("Approximately {:.2f}% of the U.S. male population have heights between 5’10” and 6’1”.".format(high - low))
```

Approximately 34.27% of the U.S. male population have heights between 5’10” and 6’1”.