Maybe we want to distinguish a subset of text from another, or maybe we want to make a bold statement within a markdown cell. Regardless, adding colored text to your markdown cells can make your code pop. All you need is a small snip-it of code with your desired text embedded in it, like this:


```python
<span style="color:'your desired color here';">'your desired text here'</span>
```

Of course, you would replace 'your desired color here' with the color that you want the text to appear as (e.g., 'red', 'blue', 'green', 'purple', etc.) and you would replace 'your desired text here' with the text that you want to be colored. Down below are some examples, with the raw code followed by the resulting outcome in markdown: 


```python
<span style="color: red;">This sentence is red</span>
```

<span style="color: red;">This sentence is red</span>


```python
<span style="color: blue;">This sentence is blue</span>
```

<span style="color: blue;">This sentence is blue</span>


```python
<span style="color: green;">This sentence is green</span>
```

<span style="color: green;">This sentence is green</span>

**A VERY IMPORTANT NOTE:** This snip-it of code will only work if you spell 'color' *WITHOUT A U*, as in the American spelling of color. *It does not work if you use the English/Canadian spelling of colour!*
