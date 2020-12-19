A **histogram** provides a visual interpretation to summarize discrete or continuous data. It is useful to view the distribution of your data points grouped by specified constraints, known as 'bins'. The Python library matplotlib.pyplot allows us to plot graphs like histograms from different datasets. 

To begin, lets import matplotlib.pyplot, which is commonly imported as plt:


```python
import matplotlib.pyplot as plt
```

Now we need data to plot. Here we create a list under the variable 'age'. It contains 100 random samples of people's ages.


```python
age = [1,1,2,3,3,5,7,8,9,10,
     10,11,11,13,13,15,16,17,18,18,
     18,19,20,21,21,23,24,24,25,25,
     25,25,26,26,26,27,27,27,27,27,
     29,30,30,31,33,34,34,34,35,36,
     36,37,37,38,38,39,40,41,41,42,
     43,44,45,45,46,47,48,48,49,50,
     51,52,53,54,55,55,56,57,58,60,
     61,63,64,65,66,68,70,71,72,74,
     75,77,81,83,84,87,89,90,90,91
     ]
```

Now we can plot this list into a histogram using the function plt.hist(), with the parameters set as 'age', which is the dataset we want to plot, and 'bins = 10', which sets the number of bins of the histogram. You can change the number of bins to whatever value will best suit your analysis. 


```python
plt.hist(age, bins=10)
plt.show()
```




    
<img width = '500' alt = 'Hist 1' src = 'Hist 1.png'>
    



Voila! A histogram! We can further add to our histogram by adding axes labels and a title. 


```python
plt.hist(age, bins=10)
plt.title('Random Distribution of Ages')
plt.xlabel('Number of Individuals')
plt.ylabel('Age')
plt.show()
```





<img width = '500' alt = 'Hist2' src = 'Hist 2.png'>
    


