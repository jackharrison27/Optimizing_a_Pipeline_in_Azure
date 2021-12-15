# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
**This dataset contains data about bank marketing. The point of the dataset tells whether an person ends up subscribing to a term deposit. Using this data to create a classification model, we can predict whether a person is likely to subscribe to a term deposit.**

**We tested two ways to create classification models using AzureML. The first was using linear regression with parameters tuned by Hyperdrive. The second was using AutoML which automated model creation and parameter selection. The best preforming model was an AutoML voting ensamble with an accuracy of 91.8%. The Hyperdrive logistic regression model scored close with a 91.3%.**

## Scikit-learn Pipeline
**The Scikit-learn pipeline used was a logistic regression model. This combined a train Python file which describes how the data is prepared and cleaned as well as the model creation. A jupyter notebook was then used add the Hyperdrive component which ran multiple experiments using different hyperparameters.**

**I used a random parameter sampling with regularization strength chosen from a uniform distribution between 0 and 1 and max iterations chosen from the values 10, 40, 80, 100, 120, and 150. Using random sampling, we are able to search for good hyperparameter values without having a preconceived notion of what is good. This, combined with an early stopping method, allows us to search many parameter values for good values without wasting too much computing power.**

**I also used a bandit policy that terminates when any runs best metric is less than 1/(1+0.1) or 91% of the best run's best metric.**

**The best logistic regression run had a reguralization strength of 0.402 and a max iteration of 100.** 

## AutoML
**The AutoML experiment performed about 35 runs using many different models and hyperparameters. The best model that the AutoML came up with was a Voting Ensemble. A voting ensemble algorithm taking a majority vote from several algorithms in order to achieve beter results than a single model would.**

**The paramaters from the 'prefittedsoftvotingclassifier' voting ensemble model had a reg_lambda value of 0.52,  a scale_pos_weight of 1, and a subsample of 0.6.**

## Pipeline comparison

**In reality, the two best models performed identically. Due to the nature of AutoML, like how it creates many different types of models and not just changes hyperparameters, AutoML seems like the best method when first starting a prediction model. This feature allows you to get a better understanding of what type of model might be best for your problem.**

**The voting ensemble model takes into account many different models and combines them to ideally create one model better than any individual model. The logistic regression model just uses logistic regression. Since the scores are so similar, it goes to show that a complex model doesn't always give you better results and sometimes, simpler is better.**


## Future work
**What are some areas of improvement for future experiments? Why might these improvements help the model?**


## Proof of cluster clean up
**If you did not delete your compute cluster in the code, please complete this section. Otherwise, delete this section.**
**Image of cluster marked for deletion**
