---
layout: post
title:  "Statistic 101 with python using drilling data"
date:   2020-09-21 22:46:00 +0200
categories: [python,machinelearning,statsmodels]
---

I have always loved statistic, it was among my most favorite subject when I did my bachelor and master. In my most recent master thesis, I applied statistical quantitative approach in order to justify the effect of income inequality relative to entrepreneurial activities in 70 different countries. 
Some people may think it's boring, but I simply adore how one can generate patterns of information solely from a bunch of numbers in a table form. The more you dig into, the more you discover the hidden layers of information underneath. There is no right or wrong, it is just a question of which method would you like to associate your argument with. Perhaps that is the reason it becomes captivating, the fact that you could not manipulate details inside statistic? It is so pure and honest. 

Back in university, I normally used SPSS package to run statistical analysis. Now that I don't own any license of it, I challenged myself to use python instead. It is not easy at all obviously, however i believe it is the learning process that matter. Here I would like to share with you my starting journey of statistical analysis with python library in statistic such as Sci-kit and Matplotlib. Statsmodels comes handy too when it comes to advanced statistic. I will apply all these library in the study case to give general idea of how python can be used to interpret data :chart_with_upwards_trend:.

## Basic linear regression step-by-step
### 1. Create a scatter-plot
In order to establish an assumption, we must first identify a scenario where our independent variable could potentially impose a positive or negative relationship to our dependent variable. One of the easiest way to find such relationship is by recognizing the trend exists in a scatter plot. 
<br/>I plotted few random drilling parameters taken from a dummy well. The file is originally in .LAS then I converted and prepared it in .xlsx format hence we can utilize dataframe pandas to read the excel file. In this case, I would like to test hypothesis that Rate of Penetration (ROP) is directly depending on the Rotation per Minute (RPM) and Weight on Bit (WOB).

```python
import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_excel("/Users/berthaamelia/Documents/Python/sample/dummy_well.xlsx")
df["DATETIME"]= pd.to_datetime(df["DATETIME"])

plt.subplot(211)
plt.scatter(x= df["Bit_Weight"], y=df["ROP_-_Average"], c=df["DHT001_Depth", alpha=0.5, label= "colorbar=DHT001 Depth")
plt.title("surface WOB vs. ROP", fontsize=10)
plt.colorbar()
plt.legend()

plt.subplot(212)
plt.scatter(x= df["Top_Drive_RPM"], y=df["ROP_-_Average"], c=df["DHT001_Depth"], alpha=0.5)
plt.title("surface RPM vs. ROP", fontsize=10)
plt.colorbar()
```
![Scatterplot](https://raw.githubusercontent.com/berthaamelia/blog/master/images/scatterplot.png)

The number (211) refers to no.of row=2, no.of column=1 and the last digit is where you want to place your current plot.
Matplotlib.pyplot receives argument as such:
<br/>x= x-axis (surface WOB and RPM)
<br/>y= y-axis (ROP)
<br/>s= size 
<br/>c= color
<br/>alpha = 0.5 (transparency).
<br/>I am using the channel "Hole Depth" as the colorscale. You can as well play around with different colorscale, you may also assign a channel as the size reference too. 

### 2. Establish simple linear regression chart
As we see in the scatter-plot above, there seems to be a cluster of data towards the ROP. Although it is not exclusively apparent, we may want to establish a linear regression model to test whether our hypothesis is statistically significant or not. To do so I will use the module sklearn and import its linear model.

```python
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
import numpy as np
sns.set_style("whitegrid") #Use seaborns module for better visualisation

df = pd.read_excel("/Users/berthaamelia/Documents/Python/sample/dummy_well.xlsx", index=None)

#Convert all data into numpy 2-dimensional
x1 = np.array(df["Bit_Weight"]).reshape((-1, 1))
x2 = np.array(df["Top_Drive_RPM"]).reshape((-1, 1))
y = np.array(df["ROP_-_Average"])

model = LinearRegression()
model.fit(x1, y)
model.fit(x2,y)
model_WOB = LinearRegression().fit(x1, y)
model_RPM = LinearRegression().fit(x2, y)
r_sq_WOB = model_WOB.score(x1, y)
r_sq_RPM = model_RPM.score(x2, y)

#Print R-squared, gradient and intercept values for each regression
print('coefficient of determination:', r_sq_WOB) #This is R-squared
print('intercept:', model_WOB.intercept_) #This represents B0
print('slope:', model_WOB.coef_) #This represents the slope, or coefficient B1

print('coefficient of determination:', r_sq_RPM)
print('intercept:', model_RPM.intercept_)
print('slope:', model_RPM.coef_)

fig,axs = plt.subplots(ncols=2)
sns.regplot(x= df["Bit_Weight"],y= df["ROP_-_Average"], data= df,scatter_kws={'alpha':0.5}, line_kws={'color': 'red'}, ax=axs[0])
sns.regplot(x= df["Top_Drive_RPM"],y= df["ROP_-_Average"], data= df,scatter_kws={'alpha':0.5}, line_kws={'color': 'red'}, ax=axs[1])
plt.show()
```
![Linear regression plot](https://raw.githubusercontent.com/berthaamelia/blog/master/images/regressionplot.png)


### 3. Predict response using training set
Now that we have generated our linear regression model, we proceed with testing the model using some random data. For this purpose we will need to split the data, we will use 80% of total data for training dataset and 20% for testing dataset. 

<br/>Let us first test the regression model no.1, where surface WOB is the independent variable and ROP is our dependent variable. Then we will compare the result with another model where surface RPM is the predictor.




### 4. Advanced linear regression with statsmodels