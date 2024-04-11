# Deep_Learning_Challenge

Overview:

The nonprofit foundation Alphabet Soup wants a tool that can help it select the applicants for funding with the best chance of success in their ventures. With the knowledge of machine learning and neural networks, by using the features in the provided dataset to create a binary classifier that can predict whether applicants will be successful if funded by Alphabet Soup.
From Alphabet Soup’s business team, have received a CSV containing more than 34,000 organizations that have received funding from Alphabet Soup over the years. Within this dataset are a number of columns that capture metadata about each organization, such as:

-EIN and NAME—Identification columns

-APPLICATION_TYPE—Alphabet Soup application type

-AFFILIATION—Affiliated sector of industry

-CLASSIFICATION—Government organization classification

-USE_CASE—Use case for funding

-ORGANIZATION—Organization type

-STATUS—Active status

-INCOME_AMT—Income classification

-SPECIAL_CONSIDERATIONS—Special consideration for application

-ASK_AMT—Funding amount requested

-IS_SUCCESSFUL—Was the money used effectively

**Steps Taken:**

1: Data Preprocessing
EIN and NAME—Identification columns removed from the input data because they are neither targets nor features 
Created cutoff point to bin "rare" categorical variables together in a new value, Other for both CLASSIFICATION and APPLICATION_TYPE  
Converted categorical data to numeric with pd.get_dummies, split the preprocessed data into features and target arrays, then lastly split into training and tesing datasets 

Target Variable for the model:
IS_SUCCESSFUL
Feature Variables for the model:
APPLICATION_TYPE
AFFILIATION
CLASSIFICATION
USE_CASE
ORGANIZATION
STATUS
INCOME_AMT
SPECIAL_CONSIDERATIONS
ASK_AMT

2: Compiling, Training, and Evaluating the Model

Building first model with the following parameters with low computation time in mind:
2 hidden layers with 95, 30 neurons split (the input (node) feature was 43, 85 was chosen as the first layer as it is almost double the input_feature). With an hidden layer activation function of relu as this our go to for the first model.
Output node is 1 as it was a binary classifier model with only one output: was the funding application successful. And an output layer activation of sigmoid as the model output is binary classification between 0 and 1.
I then increased the hidden layers to 3 and set the third hidden layer at 30 as the model prediction accuracy was below 64%: 
For the second model I decided to use tanh activation and 3 hidden layers with 85, 30, 20 neurons split and a sigmoid activation for output as the output doesn't change. 
I increased nodes and neurons, with changing other parameters to get a better accuracy but despite doing this both models came below the 64% threshold.
3: Optimize the Model
I decided to use an automated model optimizer to get the most accurate model possible by creating method that creates a keras Sequential model using the keras-tuner library with hyperparametes options.  Which will automatically tune the hyperpyrameters until it gets the most accurate model. 
The best model from the keras tuner method achieved 73% prediction accuracy using a sigmoid activation function with input node of 46, 6 hidden layers at a 51, 81, 71, 6, 41, 91 neurons split and 100 training epochs. 
Further and Final Optimization
I kept the Name column for my final Optimized Model as I still hadn't reached the goal of 75% accuracy. Keeping the keras-tuner the same apart from lowering the epochs from 100 to 50 for time optimization.

**All Top 3 Models were around 73%.**

**Summary:**
The final automatically optimized neural network trained model from the keras tuner method achieved 73% prediction accuracy with a 55% loss, using a tanh activation function with input node of 26; 5 hidden layers at a 16, 21, 26, 11, 21, neurons split and 50 training epochs. Performing better than the non automated model. Keeping the Name column was crucial in achieving and going beyond the target. This shows the importance of the shape of your datasets before you preprocess it.




