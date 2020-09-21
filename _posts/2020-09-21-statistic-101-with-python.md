---
layout: post
title:  "Statistic 101 with python using drilling data"
date:   2020-09-21 22:46:00 +0200
categories: [python,machinelearning,statsmodels]
---

I have always loved statistic, it was among my most favorite subject when I did my bachelor and master. In my most recent master thesis, I applied statistical quantitative approach in order to justify the effect of income inequality relative to entrepreneurial activities in 70 different countries. 
Some people may think it's boring, but I simply adore how one can generate patterns of information solely from a bunch of numbers in a table form. The more you dig into, the more you discover the hidden layers of information underneath. There is no right or wrong, it is just a question of which method would you like to associate your argument with. Perhaps that is the reason it becomes captivating, the fact that you could not manipulate details inside statistic? It is so pure and honest. 

Back in university, I normally used SPSS software to run statistical analysis. Now that I don't own any license of it, I challenged myself to use python instead. It is not easy at all obviously, however i believe it is the learning process that matter. Here I would like to share with you my starting journey of statistical analysis with python library in statistic such as statsmodels. Matplotlib and scikit come in handy too, especially to visualize the data. 

## Basic linear regression step-by-step
### Create a scatter-plot
1. In order to establish an assumption, we must first identify a scenario where our independent variable could potentially impose a positive or negative relationship to our dependent variable. One of the easiest way to find such relationship is by recognizing the trend exists in a scatter plot. 

I have plotted some drilling parameters in a well. The file is originally from .LAS then i converted it into .xlsx hence I can utilize dataframe to read the file.

```python
import pandas as pd

`
