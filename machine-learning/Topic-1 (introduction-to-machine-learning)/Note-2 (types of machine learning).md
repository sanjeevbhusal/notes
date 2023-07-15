

# Types of Machine Learning

As we encountered different problems over time, we have developed different ways of solving those problems with machine learning. These different ways can also be called as types of machine learning.

Machine learning problems are classified into following 4 types:

1. Supervised Learning
2. Unsupervised Learning
3. Transfer Learning
4. Reinforcement Learning

---
# 1) Supervised Learning

If we have data and associated label with it, then the model we train is said to be trained using supervised learning.

The model will be a given a object and has to predict the label associted with the object. If the label is incorrect, we correct the model. This act of constant supervision is why this process of learning is called supervised learning.

Supervised Learning is used to mainly solve 2 kinds of problems.

1. Classification
2. Regression

---
## a) Classification

Classification is used when we have to classify a value to a certain category. 

If a problem statement goes by "Is this object a cat or a dog", then such problems are said to be Classification Problems. If we only have 2 options, then we call that classification problem as binary classification. If there are omore options, we call it as multi-class classification.

Example:

1. Predict if a person has a heart disease based on their medical records (Binary classification).

2. Predict the breed of a dog based upon a dog image. (Multi-class classification)

---
## b) Regression

Regression is used when we need to predict a number. This number can go up or down in a continuous fashion.

Example:

1. Predict the price of this apartment based upon number of bedroom, locality, area of the apartment etc.
2. Predict how many people will buy a app based upon website clicks or already existing similar functionality apps etc.

---
## Difference between Classification and Regression

The main differences between classfication and regression problems is the number of possible outputs a input can be mapped into.

Classification problem predicts a input data to small set of possible outputs or categories. Regression Problem predicts a input data to many or infinite possible outputs. The outputs can be so many that we dont even say them as category. 

Classification Example: Predicting if a person has heart disease or not has only 2 possible outcomes. Either yes or no. 
Regression Example: Predicting the sale price of a house can have hundreds or infinite amount of outcomes. It could be 100000 dollars, 120000 dollars or anything in between. It could even be in decimals such as 100034.56 dollars.

For Classfication Problem, it is not always necessary that the output value / category is in categorical format. You could also have numerical categories such as 0, 1, and 2 and map inputs to these categories. Even for numerical categories, the number of categories are finite/small. 

A Regression algorithm will not use output value in categorical format. As the possible output value can be very large or infinite, using numbers is the best approach.

---

# 2. Unsupervised Learning

Unsupervised learning algorithm takes data with no labels and tries to automatically groups them into multiple clusters based upon patterns in the data. Problems like these are also called clustering (making a group of data with similar patterns).

Example:

1. Recommending what music a user will like to listen based on their past listening history. 
2. Recommending what movie a user will like to watch based on their past movie watching history.
3. Identifying if a user will be intrested to buy summer clothes based on their past shopping choices.

Lets explain the first example.

In the first example we only have past data and no any labels are attached to the data. We apply unsupervised learning algorithms that looks upon different variables such as user's age, user's geographic location, user's playlist musics etc and find patterns in the data. We then make multiple clusters such as users that ony like Rap Song,users that only like Pop Song etc. We then add users to one or more of these clusters.

Some other types of unsupervised learning are:

- Anamoly detection: This is used to identify/detect unsual activities. This is really useful for fraud detection in financial systems.
- Dimensionlity reduction: It takes a massive dataset and compresses it to a small dataset without losing much information. 

---
# 3. Transfer Learning

Transfer learning leverages the knowledge gained by one machine learning model to solve similar problems.

You need to make different changes in the model to make it useful for your problem. But you also dont need to start from scratch.

Training a machine learning model is a expensive and time consuming process. The aim with transfer learning is to leverage the knowledge that is fundamentally same for both problems.

Example:

1. You might have a machine learning model that is trained to identify the type of the car in picture. You can then change that model to identify the breed of dog in the picture.

   In this case, the car identifying model is already aware of the environment such as what does a eye mean, what does a grass look like, how does a certain color looks like. It learned all these when it was trained with millions of car pictures.

   Now, for making a dog breed identifying model, instead of training all these attributes from scratch, we use a model that already knows all these concepts and build on top of it.

---
## 4. Reinforcement learning

Reinforcement lerning requires a computer program (agent) to perform a certain task/step within a defined environment. Based upon the task performed, the agent is either rewarded or punished. Being rewarded means that the task was done correctly and being punished means that the task was done poorly.

The model now learns to repeat those task which rewards it and not perform those task which punishes it.

The goal of reinforcement learning is to make model perform tasks that gives it the highest reward.

Example:

1. Lets say we want to teach a machine learning model how to play chess. We create a agent that will make different chess moves. The chess board is a environment that either rewards or punishes the agent. The action is moving a chess piece.

   By training the model multiple times, the agent will start to learn certain moves that incentivize the reward and also learn certain moves that minimizes the reward.

   The goal is to teach agent those moves that lead to win. If any action takes model closer to the win, the action is incentivized heavily.

Based on the problem defination, you should identify the type of machine learning solution which address your problem.
