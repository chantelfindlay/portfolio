Here I will show you how to read in raw data from *numerous individual files* that can be used for data analysis. To do this, we will be using the **glob()** function from the **glob module**. The glob module is used to retrieve files matching a specified pattern, so files that share the same naming criteria can all be read into python using a **for loop**. First we must import glob: 


```python
from glob import glob
```

Next, we can make a list that contains the **general path name** of the data files. In this case, we will be using data that we used in Project 1 of NESC 3505. The list is called 'filename' that contains multiple files, each starting with 'spid' and ending with 'data.txt'.


```python
filenames = glob('spid*/spid*_data.txt')
```

Notice that after 'spid' there is an asterisk. This is known as a *wildcard*, which is a symbol used to replace or represent one or more characters. By using a wildcard, it allows us to read in files that start (i.e., 'spid') and end (i.e., 'data.txt') with the specified code and that contain other characters within the filename. 

Next, we want to create a list where each index is an individual dataframe containing data for each subject in the study. 


```python
df = [pd.read_csv(filename, sep='\t') for filename in filenames]
```


```python

```
