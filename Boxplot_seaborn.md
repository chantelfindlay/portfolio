**Seaborn** is a data visualization library that builds on top of matplotlib. It allows us to create attractive and informative statistical plots using pandas data structures, with minimal coding required. Below we will be using a dataset pre-loaded into Python known as 'tips', which shows the amount of money that customers left as a tip for a server over the period of four days (i.e., Weekend Shift). 

First, we must import the seaborn library, which is commonly imported as sns. Since seaborn builds on top of matplotlib, we will also load in the matpotlib library, which is commonly imported as plt. 


```python
import seaborn as sns
import matplotlib.pyplot as plt
```

Next we will load in the dataset 'tips' using the function sns.load_dataset():


```python
# load the dataset 
tips = sns.load_dataset('tips') 
```

We can print the first five rows of the dataset to ensure that it has been loaded in correctly, and to further understand the dataset that we are working with:


```python
tips.head()
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
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>



Now we can create a boxplot where the total bill amount is plotted by the day. We use the function sns.catplot() to do this, with the parameters 'kind' set to box, 'data' set to the dataset you wish to plot, 'y' set to the dependent variable, 'x' set to the independent variable, and 'palette' set to the color you wish the boxplot to be. Here, I set the palette to 'Set3', which is a pre-generated palette in Python. 

Further, you can use matplotlib functions to add a title and x and y labels to the boxplot. 


```python
sns.catplot(kind = 'box', data = tips, y= 'total_bill', x = 'day',
                 palette = "Set3")
plt.title("Tips from Weekend Shift")
plt.xlabel('Day')
plt.ylabel('Total Bill')
plt.show()
```




    
![png](Boxplot_seaborne_files/Boxplot_seaborne_9_0.png)
    


