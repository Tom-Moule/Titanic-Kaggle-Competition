# Titanic-Kaggle-Competition
Predict whether passengers on the Titanic survived or died - by using data exploration, data preparation, model selection and model evaluation methodologies.

## Description

The Kaggle Titanic Competition aims to give developing machine learning enthusiasts the chance to apply their skills of data analysis and model development to the real world case of the Titanic. Specifically, competition participants are given training data - which includes details about passengers such as their sex, class and survival status -  so they can develop data handling processes and machine learning models to predict which passengers survived and died amongst those whose details are given in the test data.

In this project I show, step-by-step, how I explored the data and prepared my own datasets for making predictions with. I also show how I developed and tested a wide range of machine learning models, with varying hyperparameters; and how I selected those which I thought would be the best predictors.

Here is a high level overview of the project:
- **Data Exploration** -  Discover what variables I have, what information they confer, how they are each distributed/structured, their relationships with the target variable. Identify and investigate missing data. Establish whether the testing and training datasets are similar.
- **Data Preparation** Decide how to handle missingness, what new features can be engineered, how data should be transformed; and which features are suitable for my inclusion in datasets that I will use to make predictions
- **Model Testing** Develop, test and record key metrics for different ML models, parameters and data inputs
- **Model Evaluation** Establish which models perform best wrt various metrics, understand if there are patterns in which models/parameters/data inputs perform best. Decide whether further models/parameters should be explored
- **Model Selection and Predictions**

## Technologies and Methodologies used
- Python, numpy, pandas, matplotlib, regular expressions, sklearn
- Support Vector Machines, Random Forests, Logistic Regression, K Nearest Neighbor, Sequential Feature Selection, Lasso Regression



## Summary of Key Findings/Conclusions
### Data Exploration
My key findings from the data exploration phase were as follows: 
1. The test and train sets are very similar, so we can assume that patterns that exist in train also exist in test.
2. The cabin and name features can be used to create deck and title features, which show patterns and are more manageable
3. Age data is more likely to be missing for males and for 3rd class passengers
4. Cabin data is missing in most cases for 2nd and 3rd class passengers, still some missing data (~20%) for 1st class.
5. Missing data may also be due to processing issues at Queens
6. Information gain was highest for: female, fare, deck_unknown, deck_D, age, embarked_C, sibsp deck_T and Pclass - note that algorithm had bugs in how it dealt with nas (due to underfined log calculations) - so take this as indicative not facts
7. It was noteworthy that fare and deck_unknown were more informative than class
8. While there was a lot of shared information between fare/deck/class, there seem to be benefits from including both variables.
9. Embarked did not appear to be a useful variable
10. Title's information was 80% accounted for by gender, but it did add a reasonable absolute value.

### Data Preparation

The most significant decision to make during data preparation was feature selection. 

Based on evidence from: 
analysing information gain due to each variable (and due to pairs of variables)
SKlearn’s sequential feature selection model
Analysing coefficients after applying lasso regression

I decided that there was merit in using two datasets to make predictions, one which included all available features, and another which included only the features with the highest absolute coefficients as found via lass regression.


### Model Evaluation

I found that Support Vector Machine (SVM) and Random Forest (RF) classifiers outperformed KNN and Logistic Regression classifiers. 

I also found that RF classifiers tended to confer better results when coupled with the data set that included a maximal number of features; whereas SVM classifiers tended to confer better results when coupled with the data set that included a minimal number of features.



### Predictions

Based on evaluating accuracy scores and standard deviations between cross validation runs, I  chose two models with which to make predictions: one RF model, and one SVM model.

The RF model gave an accuracy of 0.77511 when submitted to Kaggle

The SVM model gave an accuracy of 0.77033


## File Structure
- Titanic Project.ipynb (main project file)
- test.csv
- train.csv 
