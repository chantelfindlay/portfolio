Here I am going to show you how to create a Two-Way ANOVA table. 

The purpose of a two-way ANOVA is to determine how two independent variables impact a dependent variable, and to determine whether or not there is an interaction between the two independent variables on the dependent variable.

To do this, you first need to call upon a package and two modules, which are listed below:


```python
# Statistical testing packages
import statsmodels.api as sm
from statsmodels.formula.api import ols
from scipy import stats
```

**statsmodels** is a package that provides classes and functions for the estimation of many different statistical models, as well as for conducting statistical tests and statistical data exploration. You can use R-style formulas together with pandas dataframes to fit your models.

**OLS** stands for *Ordinary Least Squares*. It is a module from the statsmodels package that minimizes the sum of the squares of the differences between the observed dependent variable and predicted dependent variable.

**stats** is a module from the scipy package that ontains a large number of probability distributions and statistical functions.

Next we need data to use to create the ANOVA table. 

A botanist wants to know whether or not plant growth is influenced by sunlight exposure and watering frequency. We can use a two-way ANOVA to determine if watering frequency and sunlight exposure have a significant effect on plant growth, and to determine if there is any interaction effect between watering frequency and sunlight exposure.

Here we create a pandas DataFrame that contains **three** variables:

-**water**: how frequently each plant was watered: daily or weekly (independent)

-**sun**: how much sunlight exposure each plant received: low, medium, or high (independent)

-**height**: the height of each plant (in inches) after two months (dependent) 



```python
import numpy as np
import pandas as pd

#create data
df = pd.DataFrame({'water': np.repeat(['daily', 'weekly'], 15),
                   'sun': np.tile(np.repeat(['low', 'med', 'high'], 5), 2),
                   'height': [6, 6, 6, 5, 6, 5, 5, 6, 4, 5,
                              6, 6, 7, 8, 7, 3, 4, 4, 4, 5,
                              4, 4, 4, 4, 4, 5, 6, 6, 7, 8]})

#view first ten rows of data 
df[:10]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>water</th>
      <th>sun</th>
      <th>height</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>daily</td>
      <td>low</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>daily</td>
      <td>low</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>daily</td>
      <td>low</td>
      <td>6</td>
    </tr>
    <tr>
      <th>3</th>
      <td>daily</td>
      <td>low</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>daily</td>
      <td>low</td>
      <td>6</td>
    </tr>
    <tr>
      <th>5</th>
      <td>daily</td>
      <td>med</td>
      <td>5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>daily</td>
      <td>med</td>
      <td>5</td>
    </tr>
    <tr>
      <th>7</th>
      <td>daily</td>
      <td>med</td>
      <td>6</td>
    </tr>
    <tr>
      <th>8</th>
      <td>daily</td>
      <td>med</td>
      <td>4</td>
    </tr>
    <tr>
      <th>9</th>
      <td>daily</td>
      <td>med</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>



Below is a generalized code to create a Two-Way ANOVA table:


```python
model = ols(formula='dependent ~ C(independent 1) + C(independent 2) + C(independent 1):C(independent 2)', data=df).fit()
sm.stats.anova_lm(model, typ=2)
```

As you can see, we create a variable 'model', then use the ols module from the statsmodels package to create a formula for the ANOVA table. 

Next we create a variable 'res' with the function model.fit(), which we use in the sm.stats.anova_lm function from statsmodels to determine the fit of the model. 

typ=2 distinguishes that it is a Two-Way ANOVA (typ=1 would make it a One-Way ANOVA). 

Now to take our data and fit it to the Two-Way ANOVA table code:


```python
model = ols(formula='height ~ C(water) + C(sun) + C(water):C(sun)', data=df).fit()
sm.stats.anova_lm(model, typ=2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sum_sq</th>
      <th>df</th>
      <th>F</th>
      <th>PR(&gt;F)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>C(water)</th>
      <td>8.533333</td>
      <td>1.0</td>
      <td>16.0000</td>
      <td>0.000527</td>
    </tr>
    <tr>
      <th>C(sun)</th>
      <td>24.866667</td>
      <td>2.0</td>
      <td>23.3125</td>
      <td>0.000002</td>
    </tr>
    <tr>
      <th>C(water):C(sun)</th>
      <td>2.466667</td>
      <td>2.0</td>
      <td>2.3125</td>
      <td>0.120667</td>
    </tr>
    <tr>
      <th>Residual</th>
      <td>12.800000</td>
      <td>24.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



From the Two-Way ANOVA table we are able to interpret some results from our data. 

> Since the p-values for water and sun are both less than .05, this means that both factors have a statistically significant effect on plant height. And since the p-value for the interaction effect (.120667) is not less than .05, this tells us that there is no significant interaction effect between sunlight exposure and watering frequency.
