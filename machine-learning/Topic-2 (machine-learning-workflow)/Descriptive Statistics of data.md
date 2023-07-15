Descriptive statistics are a type of statistical analysis used to summarize and describe the main features of a dataset. Descriptive statistics provide a summary of the data and help to identify patterns, trends, and insights that may be hidden within the dataset.

Descriptive statistics are typically broken down into two main types of measures: 
- measures of central tendency and 
- measures of variability. 

Measures of central tendency describe the typical or average value of the dataset, and include measures such as the mean, median, and mode.
Measures of variability describe how spread out the data is from the central tendency, and include measures such as the range, variance, and standard deviation.

Together, measures of central tendency and measures of variability provide a comprehensive view of the dataset, helping to identify patterns and insights that may be hidden within the data. Descriptive statistics are an important tool for understanding data and making informed decisions based on the data.

Code snippet:

There are different ways to perform statistical analysis. Fot both categorical and numerical data, we have different fields that define descriptive statistics. So, we should first identify numerical columns and categorical columns in the data set.
```python
f"Categorical Features : {[column for column in df if df[column].dtype == object]})"
f"Numerical Features : {[column for column in df if df[column].dtype == int]})"
```

Lets  describe the statistics for both categories of data
```python
df.describe(include=[np.number])
df.describe(include=["O"])