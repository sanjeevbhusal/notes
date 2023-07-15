
## What is Linear Regression?

Linear Regression is a supervised learning model that predicts a numerical value by fitting a straight line across the data points. It is the most famous machine learning algorithm in terms of usage. 

## Example of Linear Regression

Lets say you have a dataset for the houses sold in a area. The dataset contains 2 variables

- size in sq feet
- price sold

Here, size in sq feet is the input variable and price sold is the output variable. We will use this data to train a model. This model will work as following:

- Plot all the data points in the graph: First, the model will plot all the values in the data set in a graph. The horizonal axis will represent size in sq feet and vertical axis will represent price of the house. This step is the training step.
- Form a straight line in the graph: You can make a straight line passing through the data points in the graph. When given a new input value i.e. size of house in sq feet, you can find the point where the line will be intercepted. You can trace the point to the vertical axis on the left. This will give you selling price of the house. 
 
![[Pasted image 20230312071524.png | 600]]
![[Pasted image 20230312072301.png | 600]]

![[Pasted image 20230312072518.png | 600]]

 Any kinds of supervised learning model that predicts the output in Numbers is addressing a problem called Linear Regression. There are many kinds of models that adderss the Regression Problem. Linear Regression is one of the models. 
 
 In this case, the output predicted is in numbers. The output can also be within a very huge range, in this case from 0 to 500 or more. Hence, this specific problem is a linear regression problem. We solved this problem using Linear Regression Model.

 This specific problem had only one single input value i.e. size in sq feet. Such linear regression problem are also known as univariate linear regression, where uni means single and variate means variable.


## Working with Linear Regression 

Lets say we have a training set. The training set contains 2 variables. 

- Size of the house
- Selling Price of the house

In this scenario, size of the house is the feature/input variable and selling price of the house is the output/target variable. We know that duch problems fall under Regression Problem. We also know that we can use one of the model for solving Regression Problem called Linear Regression Model.

Linear Regression Model takes both input variable and target variable seperately. In this scenario, we only have 1 input variable. So, we will seperate the variables from the data set. The input variable for training set is referred with variable x and the target variable for training set is referred as variable y. 

As we know Linear Regression Model fits a straight line in the data. This arises a question. What determines the position of the straight line? This is when we have to talk about the model function. Linear Regression Model analyzes both x and y variable and creates a model function. Model function maps a x value to y value. This function is an equation that receives the value of x and predicts the value of y.


## Model function 

Model function is used to predict the value of output/target variable y for every input/feature variable x. The formula for Model function is 
$$ f_{w,b}(x^{(i)}) = wx^{(i)} + b \tag{1}$$


This formula has 3 variables. x, w and b. x is the input variable whereas w and b are parameters. We use this function to generate data points. The data point is then plotted on the graph to form a line. Using this straight line, we can predict value of y for any new value of x. We saw the picture of a straight line [[#Example of Linear Regression|above]]. 

w and b are also known as coefficients or weights. You can adjust w and b variables to get a different function $f_{w,b}({x})$ which generates a different line on the graph.Out intention is to get a line that passes through or roughly passes through the training examples. $f_{w,b}({x})$ can be written in short form as $f({x})$.  

![[Pasted image 20230312132925.png|200]]
 ![[Pasted image 20230312133058.png|200]]

Lets see how the straight line changes when $w,b$ changes.


1) When w = 0 and b = 1.5, it doesnot matter what value we use for x, the output for function $f(x)$ is always going to be 1.5. This function will always give you 1.5 irrespective of the value of x. Notice that the slope of the line in this case is 0. When you plot it on the graph, this is what you get.
	![[Pasted image 20230312131621.png|200]]

2) When w = 0.5 and b = 0, the ouptut for function $f(x)$ will be different for different values of x. When x = 0, $f(x)$ is also 0. When x = 2, $f(x)$ is 1. Notice that the slope of the line in this case is 0.5 / 1 = 0.5. When you plot on the graph, this is what you get.
	![[Pasted image 20230312132050.png|200]] 
.
3) When w = 0.5 and b = 1, the ouptut for function $f(x)$ will be different for different values of x. When x = 0, $f(x)$ is also 1. When x = 2, $f(x)$ is 2. Notice that the slope of the line in this case is 0.5 / 1 = 0.5. When you plot on the graph, this is what you get.
	![[Pasted image 20230312132240.png|200]] 



## Example of Model Function and Linear Regression

Lets assume you have 2 datapoints for your training set. The data points are:

- first_house_data = {size: 1000 sqft, soldprice: 300,000$}
- second_house_data = {size: 2000sqft, soldprice: 500,000$}

Lets split the data into input values and output values. We will use the unit 1000's. So 1.0 sqft means 1000 sqft. 300$ means 300,000$.

x = [1.0, 2.0]
y = [300, 500]

The first step is to fit the data points on the plot. 

![[Pasted image 20230312123915.png|600]]


Its time to use a model to plot a line that best fits the data. We will pass both 1000 sqft as x to the function. The function will return the prize of the house. We will plot the prize in the graph. We will do the same for 2000sqft as well. Lets assume the value for w is 100 and b is 100.

- For $x^{(0)}$,  f_wb = 200 * x[0] + 1000 = 100 * 1 + 100 = 200
- Fo $x^{(1)}$,  f_wb = 1000 * x[1] + 1000 = 100 * 2 + 100 = 300

Lets plot this points on the plot.

![[Pasted image 20230312124921.png|600]]

As you can see the straight line didnot fit the data properly. Lets try it with w = 200.


![[Pasted image 20230312124731.png|600]]

 Under notebooks, study a notebook called linear_regression_algorithm.

## How do you know which values of w and b best fits the data?

Our model is best optimized if the difference between predicted value (y^) and actual value (y) is as less as possible for every value of x in the training data. The difference between predicted value (y^) and actual value (y) is know as Error.

Error = y^ - y

We can do so by fitting the model function with multiple variations of w and b, calculating the error for each set of variation and comparing the difference with other variations. The variation with the lesser error is the one that best fits the data.

We did this in [[Note-1 (Introduction to Liner Regression)#Example of Model Function and Linear Regression|above]] example, we manually played around with different values of w and b to generate the predicted value (y^). We then compared the predicted value against actual target value (y) to check if predicted value fits the target value. 

This process of identifying the model's performance is done by defining a Cost function.

## Summary of Linear Regression

- The goal of linear regression is to find the parameter $w$ and $b$ that results in the smallest possible value for cost function $J(w,b)$. 
- As you vary $w$ and $b$, you end up with different straight line. The straight line is then plotted in the graph and the error is calculated against y^. 
![[Pasted image 20230312170829.png|600]]








