
# Breaking the data down

data used for training in machine learning is broken down into 3 categories based upon their usage.

1. training data
2. validation data
3. testing data

training data is used to train the model, validation data is used to tune the model and testing data is used to test and compare different models.

First you train the model using training data (course material), then you validate the model's ability using validation data (practice exam) and then you finally test the models capability using testing data (final test).

This adaptaion that the model had from training data and validation data to perform well in testing data is called generalization.

You want to split the data as 70-80% to training data, 10-15% to validation data and 10-15% to testing data.

You dont want your machine learning models to just be a memorization machine. The model has to predict on a real-world-previously-unseen data.

You also need to make sure that the validation data should not ben same as testing data. If it happens to be same, then the model will perform excellently but might perform poorly on real world data.