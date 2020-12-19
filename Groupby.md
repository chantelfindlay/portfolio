**Groupby()** is a function from the Pandas library that allows you to split your data into separate groups, allowing you to perform separate computations for better analysis. This is particularly helpful when you are interested in a subset of a dataframe rather than the whole dataframe. 

First we must import the library Pandas, which is commonly imported as pd:


```python
import pandas as pd
```

Next we read in a dataset. In this example we will be using a csv file that contains the top ten most stolen cars (make, model, AND year) by State in the United States in 2015. We do this using the Pandas function pd.read_csv():


```python
df = pd.read_csv("2015_State_Top10Report_wTotalThefts.csv")
```

Now lets print the first 5 rows of the dataframe to see what we are working with:


```python
df.head()
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
      <th>State</th>
      <th>Rank</th>
      <th>Make/Model</th>
      <th>Model Year</th>
      <th>Thefts</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alabama</td>
      <td>1.0</td>
      <td>Chevrolet Pickup (Full Size)</td>
      <td>2005.0</td>
      <td>499</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alabama</td>
      <td>2.0</td>
      <td>Ford Pickup (Full Size)</td>
      <td>2006.0</td>
      <td>357</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Alabama</td>
      <td>3.0</td>
      <td>Toyota Camry</td>
      <td>2014.0</td>
      <td>205</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Alabama</td>
      <td>4.0</td>
      <td>Nissan Altima</td>
      <td>2014.0</td>
      <td>191</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alabama</td>
      <td>4.0</td>
      <td>Chevrolet Impala</td>
      <td>2004.0</td>
      <td>191</td>
    </tr>
  </tbody>
</table>
</div>



We can see there are 6 columns (including the index): *State, Rank, Make/Model, Model Year, and Thefts*. Though all contain useful information, **we are concerned with the State, Make/Model, and Thefts columns.** So we want to separate these columns from the rest of the dataframe. We do this by creating a new dataframe under the variable df_state_makemodel_thefts, and use the Pandas function df.groupby(), selecting the column names that we are interested in. Finally, we want to look at the means of those columns, so we add the function mean() to the end of the command. 


```python
df_state_makemodel_thefts = pd.DataFrame(df.groupby(['State','Make/Model','Thefts']).mean())
```

Now lets print the first 5 rows of the new dataframe.


```python
df_state_makemodel_thefts.head()
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
      <th></th>
      <th></th>
      <th>Rank</th>
      <th>Model Year</th>
    </tr>
    <tr>
      <th>State</th>
      <th>Make/Model</th>
      <th>Thefts</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="5" valign="top">Alabama</th>
      <th>Chevrolet Impala</th>
      <th>191</th>
      <td>4.0</td>
      <td>2004.0</td>
    </tr>
    <tr>
      <th>Chevrolet Pickup (Full Size)</th>
      <th>499</th>
      <td>1.0</td>
      <td>2005.0</td>
    </tr>
    <tr>
      <th>Dodge Pickup (Full Size)</th>
      <th>138</th>
      <td>7.0</td>
      <td>1998.0</td>
    </tr>
    <tr>
      <th>Ford Explorer</th>
      <th>119</th>
      <td>9.0</td>
      <td>2002.0</td>
    </tr>
    <tr>
      <th>Ford Mustang</th>
      <th>122</th>
      <td>8.0</td>
      <td>2002.0</td>
    </tr>
  </tbody>
</table>
</div>



Nice! Now we can focus on our rows of interest and perform analysis on them. 
