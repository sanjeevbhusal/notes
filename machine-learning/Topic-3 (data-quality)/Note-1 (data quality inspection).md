
Data is considered of good quality if the data represents real world information accurately. Good data can be used for further planning and making business decisions. Good data has to be accurate, complete, consistent, timely and reliable.

- Accurate: The data represents real world entity accurately.
- Complete: The data is complete for its intended purpose. Example: For a Image data with RGB format, if one of the color is missing, then the image/data is not complete.
- Consistent: The data should be consistent according to the group it belongs to. If a excel column represents age, all the values under it must be in numbers. 
- Timely: The data should represents the correct state for which we are analyzing. Outdated data is worse than no data.
- Reliable: The data should be from a source that can be trusted i.e. reliable.

Data quality inspection is a process to analyze the quality of the data. This includes understanding various features of the data (content) and their relationship with each other. We analyze the quality of the data through 2 ways:

- Data Profiling
- Visualization

Here is a picture showing sub topics under data quality inspection.

![[data-quality-inspection.png | 600]]


# Data Profiling

Data Profiling is a process of getting a high level understanding of the data content and inter-relationship between multiple features of the data. Data Profiling includes 2 sub topics. 

- Descriptive Statistics
- Meta Data Information

## Descriptive Statistics

Descriptive statistics includes mathematical concepts that summarize the entire data. This includes, total rows/columns count , mean, median, standard deviation, Percentile, distibution etc. As we are using mathematical concepts, it is preety clear that descriptive statistics is only possible for numerical data. You can use `dataframe.describe()` method on a dataframe to get all the descriptive statistics of the data. This data then can be represented in visual formats i.e. data visualization which is discussed later.  

For more information, read this [[2.Data Quality Inspection.pdf |pdf]] 

## Meta Data Information

Meta Data Information includes finding the type of the data (int, object) in all the columns, finding total non-null values in all the columns, number of rows and columns etc. You can use `dataframe.info` method to find all this information.

For more information, read this [[2.Data Quality Inspection.pdf |pdf]] 


# Visualization

The output of data profiling can be harder to read and is also not suitable for all the audiences. To make the data easy to understand, we visualize the data through different visualization techniques . This helps you form your own hypothesis regarding the data. Visualization can be done for both numerical and categorical data. Some of the visualization techniques are:

- Bar graph
- Histogram
- Box Plot
- Scatter Plot
- HeatMap

For more information regarding all these techniques, read this  [[2.Data Quality Inspection.pdf |pdf]] 

