# 19-Neural_Network_Deep_Learning
Module 19: Neural Networks and Deep Learning Models

## Overview
We've been tasked with building our own machine learning model that will be able to the success of a venture paid by Alphabet soup.

## Resources
- Python 3.7, Scikit-learn 0.21+, tensorflow
- charity_data.csv

## Summary

### Preprocessing
- as EIN and NAME are identifications columns(neither features nor targets), we have EIN as the index, and drop NAME from the DataFrame (while keeping it as a separate DatafRame)
- we drop the column "IS SUCCESSFUL"  and use it as our target values
- STATUS and ASK_AMT are the only numerical columns. STATUS is a categorical column though, but as it's a boolean one,it doesn't need to be encoded
- from the list of categorical columns, APPLICATION_TYPE and CLASSIFICATION need bucketing
- after hot encoding the categorical columns, and merging them into the Dataframe, it is scaled and ready to be trained, with 44 input features

### First Neural Network
- we chose to start with a neural model with 1 layer and 88 nodes, following a rule of thumb of having twice the amount of features, and 50 epochs
- we choose the Relu activation function for the first layer, and sigmoid for the binary output layer
- we get an accuracy of 72.2%, lower than the target 75%

### Optimization
- we add layers and spread the number of nodes through these layers - We don't want to add too many layers so not to overfit our model. After evaluating models with 2-3-4-5-6 layers, with different amount of nodes spreaded, the best accuracy scores we got, at 72.9%, were obtained with the models at 2 layers (70-18 nodes) and 3 layers (70-18-8)
- we change the type and order of the activation functions for both these models (relu, sigmoid, tanh, linear, softmax), and got the highest accuracy score at (slightly above) 72.9% for the 2-layers model with sigmoid-relu-sigmoid activation functions
- we add more epochs to this model but don't get a higher accuracy score

### Final Neural Network
- 2 layers 
- 70 nodes in first hidden layer, and 18 nodes in second hidden layer 
- Activation functions: Sigmoid - Relu - Sigmoid
- 50 epochs
- accuracy score at 72.9%, still lower than target 75%

To achieve better performace (over 75% accuracy) we could first try to bucket the ASK_AMT column so all the features would be categorical. We could also try to use a supervised_learning model (random forest per example)
