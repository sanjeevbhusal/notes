# Features

Feature refer to different forms of data within structured or unstructured data.

In a patients medical record, we might have data related to weight, chest pain, sex, heart rate, height, eyesight etc. If our goal is to predict heart disease, we are only intrested in data such as weight, chest pain, sex and heart rate. These data are called features or feature variables.

We use feature variables to predict target variable (has a heart disease/ doesnot has a heart disease).Feature variable could be numerical like weight, chest pain, heart rate etc and categorical like sex.

You can also create derived variable by looking at numerical or categorical features. One derived variable could be, has the patient visited in hospital last year ? This process of deriving a data from existing data is called feature enginnering.

You can also derive features from unstructed data. From hundreds of dog pictures, you could identify that a dog has 4 legs, a dog has a round strucuture on the face (eye) etc.

We need to make sure that a vast percentage of sample data has a common field if we want to consider it as a feature. In medical records, you might have a column called most eaten food. But if this field only exist in 10% of data, it might not be that valuable. This process of ensuring that a feature is available in x% of sample data is called feature coverage.
