# Generalizing

Once you test your model with test set and get the evaluation metric, you compare it with the training data set's evaluation metric.

Slight difference in the accuracy is ok but there shouldnt be any drastic differences between test metric and training mmetric.

If the model performs really poorly for test data set as compared to training data set, it is called underfitting.

If the model performs really well for test data set as compared to training data set, it is called overfitting.

If either of those cases occur, it means that the model was not able to generalize well.

Data leakage happens when some of your test data is a part of training data. In this case, the model already is trained on some of the test data. This results in overfitting.

Data mismatch happens when the data who use for training is different as compared to data you use for test such as having different features in training data and test data. In this caes, the model is unable to understand the test data well. This results in underfitting.

There are some other ways to fix underfitting. They are:

1. use a more advanced model.
2. reduce the amount of features (model might find it hard to identify patterns if there are more features).
3. increase the models hyperparameters (increase experimentation).
4. train longer.

There are some other ways to fix overfiting. They are:

1. collect more data (more data will provide different patterns, hence lowering the chance of correct prediction)
2. try a less advanced model