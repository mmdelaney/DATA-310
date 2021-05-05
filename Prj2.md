
# Project 2

## Modeling Liberia's DHS Data


![image](https://user-images.githubusercontent.com/78870884/117078002-12fed900-ad07-11eb-9b7a-d9518ca292f3.png)

### Model 1 - Penalized Logistic Regression


#### Using the R script provided, split and sample your DHS persons data and evaluate the AUC - ROC values you produce. Which "top_model" performed the best (had the largest AUC)?

See the results of the top_models below:

```
 1 0.0001   roc_auc hand_till  0.607     1      NA Preprocessor1_Model01
 2 0.000127 roc_auc hand_till  0.607     1      NA Preprocessor1_Model02
 3 0.000161 roc_auc hand_till  0.607     1      NA Preprocessor1_Model03
 4 0.000204 roc_auc hand_till  0.607     1      NA Preprocessor1_Model04
 5 0.000259 roc_auc hand_till  0.607     1      NA Preprocessor1_Model05
 6 0.000329 roc_auc hand_till  0.607     1      NA Preprocessor1_Model06
 7 0.000418 roc_auc hand_till  0.607     1      NA Preprocessor1_Model07
 8 0.000530 roc_auc hand_till  0.607     1      NA Preprocessor1_Model08
 9 0.000672 roc_auc hand_till  0.607     1      NA Preprocessor1_Model09
10 0.000853 roc_auc hand_till  0.607     1      NA Preprocessor1_Model10
11 0.00108  roc_auc hand_till  0.606     1      NA Preprocessor1_Model11
12 0.00137  roc_auc hand_till  0.606     1      NA Preprocessor1_Model12
13 0.00174  roc_auc hand_till  0.606     1      NA Preprocessor1_Model13
14 0.00221  roc_auc hand_till  0.606     1      NA Preprocessor1_Model14
15 0.00281  roc_auc hand_till  0.605     1      NA Preprocessor1_Model15
```

See the plot of penalty vs area under the roc curve below:



![image](https://user-images.githubusercontent.com/78870884/117159799-94e61500-ad8e-11eb-8e51-ae0f4ad16b17.png)

I chose top model 8 

#### Are you able to use the feature selection penalty to tune your hyperparameter and remove any potentially irrelevant predictors? 

#### Provide justification for your selected penalty value? Finally, provide your ROC plots and interpret them. How effective is your penalized logistic regression model at predicting each of the five wealth outcomes.

![image](https://user-images.githubusercontent.com/78870884/117162132-8698f880-ad90-11eb-8880-3e0ff360fc50.png)


### Model 2 - Random Forest

#### Using the R script provided, set up your random forest model and produce the AUC - ROC values for the randomly selected predictors, and the minimal node size, again with wealth as the target. How did your random forest model fare when compared to the penalized logistic regression? Provide your ROC plots and interpret them. Are you able to provide a plot that supports the relative importance of each feature's contribution towards the predictive power of your random forest ensemble model?

### Model 3 - Logistic Regression

#### Using the python script provided, train a logistic regression model using the tensorflow estimator API and your DHS data, again with wealth as the target. Apply the linear classifier to the feature columns and determine the accuracy, AUC and other evaluative metrics towards each of the different wealth outcomes. Then continue with your linear classifier adding the derived feature columns you have selected in order to extend capturing combinations of correlations (instead of learning on single model weights for each outcome). Again produce your ROC curves and interpret the results.

### Model 4 - Gradient Boosting

#### Using the python script provided, train a gradient boosting model using decision trees with the tensorflow estimator. Provide evaluative metrics including a measure of accuracy and AUC. Produce the predicted probabilities plot as well as the ROC curve for each wealth outcome and interpret these results.

### Analysis of 4 Models

#### Analyze all four models. According to the evaluation metrics, which model produced the best results? Were there any discrepancies among the five wealth outcomes from your DHS survey dataset?

