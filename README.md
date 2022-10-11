# Neural Networks and Deep Learning Models

## Project Overview
The purpose of this project is to create a neural network model which will analyze past grant recipients' use of received funds in order to predict whether future applicants will successfully use received funds. Thus, the model will allow the funding organization to decide whether or not to allocate funds to each applicant.

## Resources
Data Source: charity_data.csv

Software: Python 3.7.6

## Results
The first part of the model creation consisted of data preprocessing, with results outlined below.
- The target variable is IS_SUCCESSFUL. This variable shows whether past applicants were successful in their use of received funds and is the basis of testing the created model.
- The feature variables are the following: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, and ASK_AMT. These are various categorical and numerical variables which the model will use as a basis for predicting whether an applicant will be successul in using received funds.
- The variables which should be removed from the input data as they are neither targets nor features are EIN and NAME. These are the applicants' tax identification numbers and organization names, which have no bearing on whether or not funds are used successfully, nor can they be predicted from other data.

The second part of model creation involved compiling, training, and evaluating the model, with results outlined below.
- The first model had two layers with 80 and 30 neurons, respectively, as well as an output layer. The hidden layers used the ReLu function and the output layer used the sigmoid function. Because the data set is relatively large, two layers and a larger number of neurons were a good starting point. Both the sigmoid and ReLu functions are useful for classification problems, which is what the model is trying to achieve. The model summary is illustrated below.

![This is an image](https://github.com/EricaEidelman/Neural_Network_Charity_Analysis/blob/main/Resources/Model_Summary.png)

- The first model was not able to achieve target performance, with an accuracy of 72.48% and a loss of 0.5591 (model output below).

![This is an image](https://github.com/EricaEidelman/Neural_Network_Charity_Analysis/blob/main/Resources/Model_Results.png)

- To attempt to increase model performance, several steps were taken. First, the number of neurons in each layer was increased to 100 and 50, respectively. This more than doubled the number of trainable parameters but provided a negligible improvement in accuracy (72.57%) and slightly increased loss (0.5599). Model summary and results are below.

![This is an image](https://github.com/EricaEidelman/Neural_Network_Charity_Analysis/blob/main/Resources/Model_Optim1_Summary.png)

![This is an image](https://github.com/EricaEidelman/Neural_Network_Charity_Analysis/blob/main/Resources/Model_Optim1_Results.png)

The next optimization attempt added a third hidden layer with 25 neurons. Accuracy was slightly higher than the original model but lower than the first optimization attempt (72.52%) and loss increased compared to the previous two iterations (0.5611). Model summary and results are below.

![This is an image](https://github.com/EricaEidelman/Neural_Network_Charity_Analysis/blob/main/Resources/Model_Optim2_Summary.png)

![This is an image](https://github.com/EricaEidelman/Neural_Network_Charity_Analysis/blob/main/Resources/Model_Optim2_Results.png)

The third optimization attempt kept the same parameters as the second, but changed the output layer to also have a ReLu activation function. This resulted in both the worst accuracy of all four models (72.40%) as well as the highest loss (0.5996). Model summary and results are below.

![This is an image](https://github.com/EricaEidelman/Neural_Network_Charity_Analysis/blob/main/Resources/Model_Optim3_Summary.png)

![This is an image](https://github.com/EricaEidelman/Neural_Network_Charity_Analysis/blob/main/Resources/Model_Optim3_Results.png)

## Summary
The highest accuracy, although not by a lot, was from the first optimization attempt which had two hidden layers of 100 and 50 neurons with a ReLu activation function in each layer, as well as an output layer utilizing the sigmoid function. Loss was lowest in the original model with 80 and 30 neurons. The lowest accuracy and highest loss both were in the third optimization attempt, which had three hidden layers of 100, 50, and 25 neurons, and ReLu functions in the hidden layers and the output layer. One can conclude that two hidden layers are likely the optimal amount for this data set.

Another model which can be used for this data set is the random forest. Random forests combine the output of smaller decision trees in order to make a final cateogrical decision. This dataset contains no images or natural language, so a random forest would be able to handle the classification. The model would be dependent on training on subsets of the dataset in order to predict whether applicants would be successful in using funds. Given that the neural network didn't see much improvement after increasing the number of hidden layers and neurons, the much faster random forest would be a good alternative to try.
