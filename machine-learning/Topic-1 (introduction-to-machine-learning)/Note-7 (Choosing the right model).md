# Chossing a model according to your data

If you have structured data, decision trees such as Random Forest or gradient boosting algorithms like CatBoost and XGBoost works best.

If you have unstructured data, deep learning, neural learning and transfer learning works best.

you first train the model for a small percentage of training data. If you are satisfied with the time it takes to train the model, then you might want to train the model in the entire training data set.

you should also be satisfied with the metrics. If metric isnt the same as you want, you might want to adjust hyperparameters of the model.

Example: Lets say you cook a chicken on a oven at around 100 degree for one hour. After one hour, you check the result and found that some parts are still uncooked. So, you change the temperature from 100 to 200 (hyperparamater) and cook another chicken for 1 hour. You could also change 1 hour to 2 hour (hyperparameter). You will keep on experimenting with hyperparameters untill you are satisfied by the result.