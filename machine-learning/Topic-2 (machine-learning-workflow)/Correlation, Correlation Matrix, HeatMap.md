
Correlation shows how much 2 numeric columns in a dataframe are related to each other.  The relation between 2 columns is identified by correlation cofficient. 

Correlation cofficient ranges from -1 to +1.  It shows both the strength of relationship between 2 columns as well as the direction of relationship between 2 columns.  If the correlation cofficient between 2 columns is 1, then both columns have a very strong correlation i.e. they both are related with each other strongly.  

The correlation cofficient 1 could either be positive (+1) or (-1). This determines the direction of relationship. +1 means, if value of 1 column increases, the value of another column also increases by same extent. -1 means, if value of 1 column increases, the value of another column also increases by same extent but in reverse order.  In other words, we are measuring linear relationship between 2 variables. 

A linear relationship between two variables is a mathematical relationship in which the value of one variable changes proportionally with the value of the other variable. In other words, a change in one variable is associated with a constant rate of change in the other variable.

Example: 
- Lets say column A has a correlation coefficient of 0.5 with column B. This means if values of column A increases by 50% then, values of column B will also increase by 0.5 times 50%.  If correlation cofficient was -0.5, this means value of column B wil decrease by 0.5 times 50%.
- Correlation cofficient of a column with itself should alwasy be positive 1 (+1).

If a column has 0 correlation cofficient with another column that means there isnt any relationship between those columns that could be identified.

When I say What is the Correlation between A and B, am I refering to how 2 variables are related to each other and when I express the relationship between A and B in numbers, that is Correlation Cofficient


# Correlation Matrix

Correlation Matrix is a table that shows correlation between all the pairs of variables in a dataset.  In the output provided, each row and column corresponds to a variable, and the values in the table are the correlation coefficients between the variables.  The diagonal elements (top-left to bottom-right) represent the correlation of each variable with itself, and they are always equal to 1.

If you have a dataframe, you can calculate correlaton cofficient between multiple columns with the following code.
```python
df.select_dtypes(include=np.number).corr()
```

# HeatMap

You can use a library called seaborn to represent correlation cofficient with colors. This is caled a heatmap because it shows bright colors for sronger relationships and less bright colors for weak relationships. This helps to quickly identify which correlation coefficient is stronger or weaker and also the direction.

```python
import matplotlib as mpl
import seaborn as sns
mpl.rcParams['figure.figsize'] = 10, 6
new_df = df.select_dtypes(include=np.number).corr()
sns.heatmap(new_df, vmin=-1, vmax=1, center=0, cmap=sns.diverging_palette(220, 20, n=200))

## vmax=1, center=0, cmap=sns.diverging_palette(220, 20, n=200) are used to customize the heatmap
```
