# Approaching a machine learning problem


Whenever we want to built a machine learning solution for  a problem, we should take it one step at a time. The following steps can be taken to learn about the problem, data and finding a solution.

- Business Understanding
- Data Understanding (Data collection and analysis)
- Data preparation
- Modelling
- Evaluation
- Deployment

Lets understand this approach using a example. 

## Problem

A school located in Protugal wants to predict their students final examination grade. 

## Business understanding

As machine learning engineer, you need to understand the requirements first. In this problem scneario, conventional programming is not feasible. There will hundreds of variables that might influence a students final grade. So, we will instead use Machine Learning. 

As we have decided to use machine learning, there are few questions that needs to be answered first. 

- What kind of machine learning algorithm will we use?
- Does this problem fall under Supervised or any other types? 
- What kind of data set is available?

Thats where we move to the next step i.e. Data understanding.

---
## Data understanding

In order to predict a students final grade , we will first need to collect data from past students. We will collct their final grade along with other variables. Our intention is to find a relationship on how other variables might have affected in the final grade. This way, we can also predict the final grade of current ongoing students.  Going forward, all the data collection ideas will be for past students.

One of the obious data choice will be **students previous examination grades**.  Analyzing previous examination marks, we can have a rough idea of sudent's capabiity.

Another criteria that might be helpful is **sudents attendance in school**. If a student is regularly attending school, the chance of student showing acive engagement  in class is high, which might result in better performance of student in examination.

Another criteria might be **Students Parents Profession**. If a students parent is a highly qualified professional (doctor, engineer, lawyer etc), the chance of a good home environment increases, which might result in better performance of student in examination. 

Similarly, there can a lot of other variables such as students studytime, travel time, internet usage, health status, extra classes and so on. These variables might not directly affect a students performance but collecting these variables will help us to better analyze someones grade with comaprison to things in their personal life.  Lets understand this with a example.

Example: If our research found that most of the students whose parents are teachers are better in examination compared to other students whose parents are doctor, enineer etc, we can conlude that a student with teacher parents has a higher chance of performing better in examination. To come to this conclusion, we must collect information about students parent's profession. 

### Data Collection

We can visit school and collect all the data from students. Ofcourse,  it might not be feasible to collect data from all the student provided that a school might have 1000's of student.  So, lets assume that we have collected data from 395 students.  

There will be certain variables/features as discussed above such as sex, address, parents profession, previous examination marks etc that will be collected for all the students. We can then store this information in a relational database or a csv file. Hence, the type of data collected is Structured data.

By understanding, data we also get an idea that using Regression Algorithm might be right for this kind of problem. [[Note-2 (types of machine learning)#1) Supervised Learning#b) Regression|Regression ]]

### Data Analysis

Now we have to analyze the data to make sure we remove all the noises and unconsistent data. Here we will be using many libraries.

1. First, we will use Pandas to actually load the csv file containing all the data about students. We will create a dataframe in panda representing csv file. This will allow us to modify data in csv file programtically. 
	```python
	import pandas as pd
	DATASET_URL = "https://storage.googleapis.com/codehub-data/1-lv1-1-student-mat.csv"
	df = pd.read_csv(DATASET_URL, sep=";")
	```

2. Now, we need to have a good understanding of what each column represent. In our data set, these are the explanations of all the columns
	```python
	Attributes for _Student Performance Dataset_ provided are:

	1.  school - student's school (binary: 'GP' - Gabriel Pereira or 'MS' - Mousinho da Silveira)
	    
	2.  sex - student's sex (binary: 'F' - female or 'M' - male)
	    
	3.  age - student's age (numeric: from 15 to 22)
	    
	4.  address - student's home address type (binary: 'U' - urban or 'R' - rural)
	    
	5.  famsize - family size (binary: 'LE3' - less or equal to 3 or 'GT3' - greater than 3)
	    
	6.  Pstatus - parent's cohabitation status (binary: 'T' - living together or 'A' - apart)
	    
	7.  Medu - mother's education (numeric: 0 - none, 1 - primary education (4th grade), 2 - 5th to 9th grade, 3 - secondary education or 4 - higher education)
	    
	8.  Fedu - father's education (numeric: 0 - none, 1 - primary education (4th grade), 2 - 5th to 9th grade, 3 - secondary education or 4 - higher education)
	    
	9.  Mjob - mother's job (nominal: 'teacher', 'health' care related, civil 'services' (e.g. administrative or police), 'at_home' or 'other')
	    
	10.  Fjob - father's job (nominal: 'teacher', 'health' care related, civil 'services' (e.g. administrative or police), 'at_home' or 'other')
	    
	11.  reason - reason to choose this school (nominal: close to 'home', school 'reputation', 'course' preference or 'other')
	    
	12.  guardian - student's guardian (nominal: 'mother', 'father' or 'other')
	    
	13.  traveltime - home to school travel time (numeric: 1 - < 15 min., 2 - 15 to 30 min., 3 - 30 min. to 1 hour, or 4 - >1 hour)
	    
	14.  studytime - weekly study time (numeric: 1 - < 2 hours, 2 - 2 to 5 hours, 3 - 5 to 10 hours, or 4 - >10 hours)
	    
	15.  failures - number of past class failures (numeric: n if 1<=n< 3, else 4)
	    
	16.  schoolsup - extra educational support (binary: yes or no)
	    
	17.  famsup - family educational support (binary: yes or no)
	    
	18.  paid - extra paid classes within the course subject (Math or Portuguese) (binary: yes or no)
	    
	19.  activities - extra-curricular activities (binary: yes or no)
	    
	20.  nursery - attended nursery school (binary: yes or no)
	    
	21.  higher - wants to take higher education (binary: yes or no)
	    
	22.  internet - Internet access at home (binary: yes or no)
	    
	23.  romantic - with a romantic relationship (binary: yes or no)
	    
	24.  famrel - quality of family relationships (numeric: from 1 - very bad to 5 - excellent)
	    
	25.  freetime - free time after school (numeric: from 1 - very low to 5 - very high)
	    
	26.  goout - going out with friends (numeric: from 1 - very low to 5 - very high)
	    
	27.  Dalc - workday alcohol consumption (numeric: from 1 - very low to 5 - very high)
	    
	28.  Walc - weekend alcohol consumption (numeric: from 1 - very low to 5 - very high)
	    
	29.  health - current health status (numeric: from 1 - very bad to 5 - very good)
	    
	30.  absences - number of school absences (numeric: from 0 to 93)
	    
	
	These grades are related with the course subject, Math or Portuguese:
	
	31.  G1 - first period grade (numeric: from 0 to 20)
	    
	32.  G2 - second period grade (numeric: from 0 to 20)
	    
	33.  **G3 - final grade (numeric: from 0 to 20, output target)**
	```

 From this data we can get following observations.
 - Some columns name maps to a different name. Example:  `F_job` for `Fathers Job`
 - Some columns values maps to a different value. Example:  `F` for `Female`, `nominal` for `Teacher`
 - There are few categorical columns. Example:  `Fjob, famsize` etc
 - There are few categorical columns whose values are represented in numbers. Example `Medu, Fedu`
 
3. Lets now look at quick summary of the data using a statstical analysis method called Descriptive Statistics [[Descriptive Statistics of data|Descriptive Statistics]] .
	```python
	df.describe(include=[np.number]) # STATISTICS of numerical columns
	df.describe(include=["O"]) # STATISTICS of categorical columns
	```
	
	Here we will be looking at different fields such as mean, min, std, frequency etc to get a quick summary of the data.

4. Lets now plot histogram of this dataframe to get a graphical representation of the data.  [[histogram, bar graph|histogram]] 
	```python
	fig = plt.figure(figsize=(15, 12))
	ax = fig.gca()
	df.select_dtypes(include=np.number).hist(ax=ax)
	plt.show()
	```
	
	Here we will be looking about distriution of each feature in the data set and learn about the skeweness of the data. [[skeweness]]
	Here we can see that the column absences is not skewed. The data is distibuted in uneven fashion. Majority of the studetns have taken very less leave whereas few students have taken leave for more than 40 days. 

5. Lets now plot correlation matrix of this dataframe to get a comparision between multiple variables. [[Correlation, Correlation Matrix, HeatMap|Correlation]]
	```python
	import matplotlib as mpl
	import seaborn as sns
	mpl.rcParams['figure.figsize'] = 10, 6
	new_df = df.select_dtypes(include=np.number).corr()
	sns.heatmap(new_df, vmin=-1, vmax=1, center=0, cmap=sns.diverging_palette(220, 20, n=200))
	```

	From this heatmap, we can see that `medu` and `fedu` are very closely related. `G1`, `G2` and `G3`  are also closely related in a positive direction.

6. Lets now plot bar graph of this dataframe to compare between multiple categorical data. 
	```python
	plt.figure(figsize=(3,4))
	for category in df.select_dtypes(include='O'):
	  df[category].value_counts().plot(kind='bar')
	  plt.show()
	```

	By looking at bar graph for each column of the dataset, we can idenitify how a column is distributed across multiple diferent values. In case of address column, frequency of `U` is much more greater than frequency of `R`.  

7. Now lets perform various kinds of data quality verification . [[Data Quality Verification|Data Quality Verification]]
	 
	 1. First we can find out if there are any null values in the data set and see their percentage.
		 ```python
			df.isna().mean(axis=1)
		```
		
		In this data set there are no null values hence the percentage is also 0%.
	
	 2. Second, we can find about outliers by plotting a boxplot graph 
		 ```python
		mpl.rcParams['figure.figsize'] = 30, 10
		df.select_dtypes(include=np.number).boxplot()
		```
		
		Here, we can see that column `absences` has a lot of outliers. 

	3. Third, lets find out if the taget column is imbalanced
		```python
			mpl.rcParams['figure.figsize'] = 15, 8
			sns.countplot(x = 'G3', data=df)
		```

		Here we can see that the target column `G3` has very few students who scored marks such as  `4`, `20` etc. These studetns cannot  be neglected from the dataset. So, the dataset is said to be imbalanced. 
	
	4. There are several other data quality (DQ) checks such as Completeness, Precision, Validity, Accuracy, Consistency, Confirmity and Integrity, etc



---
## Data preparation

We have already performed data analysis and identified the good and bad aspects of the data. We have  identified issues such as outliers, missing values etc. 

Now its time to prepare the data by removing all the problems and make it ready for feeding into the model. 

In this phase, we will 

- clean the data
- encode the data
- split the dataset
- generate new attributes (feature enginnering)
- integrate data (merge/aggregate)

### Clean the data 

Data cleaning involves handling 2 things. 
- handling missing data [[Data Quality Verification#Handling missing data|handling missing data]]
- handling outliers.  [[Data Quality Verification#Handling outlier values|handling outlier values]]

As we donot have any missing data in this data set,  we can skip it and move to  handling outliers.  

For handling outliers in `absences` column, we will 
- first, calculate the mode of the `absences` column. 
- generate a new column based on `absences` column replacing all values greater than `15` with the mode. 
- Replace `absences` column with this new column. 

```python
df["absences"] = np.where(df["absences"] > 15, df["absences"].mode(), df["absences"])
```






	 

---

---
### Encode the data

We have few categorical features in the data set. for machines it is extremely hard to process categorical data since models are based on mathematical equations. So, we will convert/encode categorical data into numerical data. 

There are 2 ways to encode the data. 
- Label Encoding [[Data Encoding#Label Encoding|Label Encoding]]
- One Hot Encoding - Label Encoding [[Data Encoding#One Hot encoding | One Hot encoding]]

```python
from sklearn.preprocessing import LabelEncoder
cat_binary = ['school', 'sex', 'address', 'famsize', 'Pstatus', 'schoolsup', 
                  'famsup', 'paid', 'activities', 'nursery', 'higher', 'internet', 'romantic']
df[cat_binary] = df[cat_binary].apply(LabelEncoder().fit_transform)  ## label_encoding
```

This piece of code does Label Encoding for all the columns in cat_binary list.  If you look closely, you can see that all the columns have only 2 categories. school has only 2 options, sex also has 2 options, address also has 2 options etc.  

By defination, label encoding should be used for columns whose categories have a ordinal relationship. But can also be used when it makes sense to represent categories with numbers. This is especially true when you only have 2 categories, just like the example above. In case of sex column, female can be represented with 1 whereas male can be represented with 0.

The resulting encoded values do not carry any inherent meaning, and therefore, using them in a way that assumes an ordinal relationship between the categories can lead to incorrect interpretations of the data. So, looking at the encoded values, we cant make an assumption that female is somehow higher in order as compared to male.

> [!info]
> We could have used one hot encoding to represent binary categorical features. But using label encoding is easier and simpler compared to one hot encoding for binary categorical features. 
> 
> Using One-Hot Encoding for binary categorical features like 'sex' would result in an additional column. Therefore, in this specific case, using One-Hot Encoding for the 'sex' column would not add any additional information and would unnecessarily increase the number of columns in the dataset.

```python
from sklearn.preprocessing import LabelEncoder
cat_nominal = ['Mjob', 'Fjob', 'reason', 'guardian']
df = pd.get_dummies(df, columns=cat_nominal, prefix=cat_nominal) ## One hot encoding
```

This piece of code does one hot encoding for all columns in cat_nominal list. If you look closely, all the columns have more than 2 categories. Mjob has teacher, civil services, other etc.

If we used Label encoding for Mjob, it would assign 0 to teacher, 1 to civil services, 2 to other etc. When the model interprets the encoded data, it thinks that there is a ordinal relationship among those jobs and will treat job with value 2 with more significance than job with value 1 and 0. As this is not true, we had to use one hot encoding. 

---
### Split the dataset

We will now split the dataset into training set and test set. [[Note-6 (Breaking model training data)|split the data]]

```python
from sklearn.model_selection import train_test_split

y = df["G3"] # target column
X = df.drop(columns=["G3"]) # features column
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0) 
```


We are splitting 80% of data into training and 20% of data in testing. As we know, we are using 32 different input features to predict a target feature `G3`. So, we need to feed both input features and target feature seperately to model and let it figure out the relationship between input features and target feature. This way model will learn how to predict a target feature, given a input feature.

`train_test_split` method will return 4 items. First 2 will be dataframe and rest 2 will be series. We will feed X_train dataframe as input feature and y_train series as target feature. Once the model has trained, we will see if model can predict target feature y_test  given a dataset X_test.


---
## Modeling

In this section, we will create a model, train it and test it. We have already prepared training and test data in above step. 

In order to select a modeling technique, we will consider computation time, computation resources, etc.  We have to consider various factors when we evaluate model such as Algortihm selection [[Note-7 (Choosing the right model)| Right Model selection]], overfitting/underfitting [[Note-8 (Model Generalization, Overfitting, Underfitting) | overfitting/underfitting]] etc.

---

## Deployment

In this phase, we deploy the model and integrate it with our frontend/backend application. We should also need to monitor the performance of our model and constantly improve it. 

---

# Summary Picture

![[../assets/images/machine-learning-workflow.png | 1200]]