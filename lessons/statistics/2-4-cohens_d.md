[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

**Exercise 4**  
*Using the variable ```totalwgt_lb```, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?*

[Python code that computes Cohen’s d:](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24)
```python
def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / math.sqrt(pooled_var)
    return d
```

[Cohen's d](https://en.wikipedia.org/wiki/Effect_size) 

|Effect size|d|
|:-:|:-:|:-:|
|Very small|0.01|
|Small|0.20|
|Medium|0.50|
|Large|0.80|
|Very large|1.20|
|Huge|2.0|

**Difference in pregnancy length:**
```python
>>> CohenEffectSize(firsts.prglngth, others.prglngth)
0.028879044654449834
```
*The difference in means is 0.029 standard deviations, which is small.*  
There's no significant difference between pregnancy length of first babies and pregnancy length of others babies (2nd, 3rd, ...).


**Difference in weight between first babies and others:**
```python
>>> CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
-0.088672927072602
```
> The minus result is a result of subtracting the larger mean (```others.mean()```) from the smaller mean (```firsts.mean()```).  
[Cohen's d is a measure of the magnitude of effect and cannot be negative](https://www.researchgate.net/post/When_calculating_effect_size_EF_using_Cohens_formula_how_does_a_negative_result_influence_the_result_or_do_we_ignore_the_sign/597b630df7b67ef8a105285f/citation/download), we have to treat the result as the absolute value of the effect: ```0.09```.  

The difference in means is small, there's no significant difference in weight between first babies and others (2nd child, 3rd, ...).

# Solution
We can interpret the minus sign got in difference in weight (```-0.09```) as other babies (2nd child, 3rd, ...) tending to be **slightly heavier** than first babies.  
Or, the absolute value of the effect (```0.09```) as first babies tending to be **slightly lighter** than other babies.  

As of pregnancy lengths, pregnancy lengths of first babies tend to be **slightly shorter** than other babies.  
Or, pregnancy lengths of other babies tend to be **slightly longer** than first babies.

For both differences (*pregnancy length* and *weight*) the effect was **very small**, which suggests that there’s no practical significance in the differences between either of the groups.