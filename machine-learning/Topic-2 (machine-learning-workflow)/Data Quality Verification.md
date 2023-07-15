Data is consider to be high quality if it represents real world variables properly to which we are aiming to relate. We can consider following aspects of data to maintain data quality

- missing or outlier values
- unusable data
- imbalance data
- data quality checks


# missing value

Missing values in a cell means either the cell contains null value or the cell is empty. As the cell donot represent any value, such cells should not be considered going forward. 

To identify all the missing values in a dataframe, 

```python
df.isna().mean().(axis=1)
```

`isna` method is used to check for missing or null values in a pandas DataFrame. It returns a DataFrame of the same shape as the input DataFrame, with each cell containing a Boolean value indicating whether that cell is missing or not. True represents a missing or null value, while False represents a non-null value. 

The output is then fed to `mean` function which sums all the values in a cell of a column and finds the mean of that column. `true` represent 1 and `false` represent 0.

## Handling missing data

In order to handle missing data, we should either delete the entire record, or replace the missing value using various techniques such as Mean/Median values, most frequent values, constant values, zero value etc.



---
# outlier value

Outliers are values that fall a long way compared to most of the values in the data. Such values should not be considered as they dont represent majority of the data. 

Example: Lets say out of 100 students, 3 students are not even absent a single day, 10 studetns are absent for over 20 days. Lets say the mean of absence is 5 days. In such cases, we might consider students that  are absent for a maximum of 8 days (upper range) and students that are absent for a minimum of 2 days (lower range). Students falling outside of these category are consider to be outliers.  

The upper and lower range is generated using quartile division (q1 and q3).

## Handling outlier values

In order to handle outlier values, we can either delete the entire record, or assign a new value such as mean, median, mode etc. The purpose is to either completely remove the reccord or adjust the record within the lower and upper range.




---
# imbalance data

The term "imbalance" refers to the situation where the distribution of classes (or labels) is not equal. For example, if you have a dataset with 100 samples, and 90 of them belong to class A and the remaining 10 belong to class B, then you have a class imbalance problem.

If you train a model with a imbalanced dataset, then the model will not represent all the classes, hence making it extemely biased towards a certain class.  In such cases, the algorithm may be biased towards the majority class, leading to poor performance in detecting the minority class.

Example: 
- Lets say your dataset consists of 80% Python code and 20% Javascript code. If you train a model with this data, the model will be preety good at understanding Python code. Hence, it will perform good in real world scenarios for understanding Python code but will perform poorly whwn it comes to understanding Javascript code. 
- Lets say you train a model for predicting students final grade. You took a dataset of previous year and fed it to model. If that dataset only consisted of students who had good marks, the the model will be biased. The model has never seen low marks, hence it will always predict high marks for any new data set.

To check for class imbalance, you can simply count the number of samples in each class and compare them. If the number of samples in each class is approximately equal, then the dataset is balanced. If one class has significantly more or fewer samples than the others, then the dataset is imbalanced.

To perform this in code, you can use matplotlib and seaborn.

```python
mpl.rcParams['figure.figsize'] = 15, 8
sns.countplot(x = 'G3', data=df)
```

ALternatively, you can also plot a bar graph with matplotlib.pyplot

```python
plt.figure(figsize=(10,4))
df["G3"].value_counts().plot(kind='bar')
plt.show()
```

---
> [!info]
> There are several other data quality (DQ) checks such as Completeness, Precision, Validity, Accuracy, Consistency, Confirmity and Integrity, etc.

