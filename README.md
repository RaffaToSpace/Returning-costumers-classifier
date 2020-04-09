# Predict audiobooks returning customers

I have built a model that analysises data from customers of an audiobook app to classify them as returning or not, in a boolean way. By "returning" I mean returning customers, i.e. if they will go back to using the app to purchase more products.
Methods used:
- NN
- SVM (as comparison)

The data are imported from an attached csv file, and is tabled as follows:

| customer id | average minutes spent per book | total minutes spent on app  |average price of book   |total spent on app   |has left reviews?|review score|completion fraction| minutes listened |number of support requests|Last visited time minus purchase date| Target (dependent variable)|
|---------------|-------|---|---|---|---|---|---|---|---|---|---|
|   x   |   x    |  x | x  | x  |x|x|x|x|x|x|x|

### Methodology - preprocessing

- Balancing the data: the original data is not balanced in terms of target (outcome) values, which means that the evaluation of the accuracy would be skewed. I removed values in order to have a roughly equal number of target values;
- Standardize the values;
- shuffling values: this is to avoid any order that might be present in the way the data is collected;
- saving data into csv: this will be handy for any other analysis;
- Split into train, validation and test datasets;
- Saving into npz format;

### Methodology - NN model

- data loading from the npz files saved in the BC_preprocessing notebook;
- model definition: NN with adjustable number of layers, nodes, etc;
- definition of an alternative model with an early stopping mechanism, to avoid overfitting;
- testing the model, and table with 2 examples of values obtained with slightly different models;


### Methodology - SVM model

- importing the data: data shown as it is in a pandas dataframe, then imported from the csv files generated in the BC_preprocessing notebook;
- splitting into train and test datasets;
- definition of the model;
- testing of the model;

This work is based on an exercise from https://www.udemy.com/course/the-data-science-course-complete-data-science-bootcamp/

## Conclusions
The SVM has performs well and has the following outcomes:

SVM Accuracy: 0.8994  
Test set Jaccard similarity score:  0.8994  
Test set F1 score: 0.8991 

The feature coefficient plots shows how some features, such as the ones regarding minutes or money spent on the app, have a moderate impact on the predicted outcome, whereas the completion of books is strongly inversely proportional to the outcome.

![alt text](https://github.com/RaffaToSpace/Returning-costumers-classifier/blob/master/Feature%20coefficients.png "Feature coefficients of the SVM model")

The NN has shown an accuracy on the test set of 0.8862.

Further analysis could be performed by using a random forest predictor, as they generally perform well with dataset made of combinations of numerical and categorical variables.

## How to use it
Tu run the model, simply download the repository files and store them in the same folder. Run BC_preprocessing first, as it will generate the preprocessed dataset for the models, then run either BC_NN or BC_SVM, depending on the model you'd like to use.

## How to contribute
Please drop a message if you'd like to comment on my work, I'm very much open to suggestions and feedback.
