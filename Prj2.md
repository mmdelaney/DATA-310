
# Project 2

## Modeling Liberia's DHS Data

For this project, I chose to analyze DHS data from Liberia. I created multiple models to predict wealth in Liberia based on factors such as age, gender, education, and household size. The plot below shows the wealth distribution of the entire sample.

![image](https://user-images.githubusercontent.com/78870884/117078002-12fed900-ad07-11eb-9b7a-d9518ca292f3.png)

### Model 1 - Penalized Logistic Regression


#### Using the R script provided, split and sample your DHS persons data and evaluate the AUC - ROC values you produce. Which "top_model" performed the best (had the largest AUC)?

See the results of the top_models below:

```
    penalty .metric .estimator  mean     n std_err .config              
      <dbl> <chr>   <chr>      <dbl> <int>   <dbl> <chr>   
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

Based on just the top_models output, all the models between Model 1 and Model 10 have the same AUC of 0.607. So, with only this data, it is difficult to determine which specific model performed the best.


See the plot of penalty vs area under the roc curve below:

![image](https://user-images.githubusercontent.com/78870884/117159799-94e61500-ad8e-11eb-8e51-ae0f4ad16b17.png) 

#### Are you able to use the feature selection penalty to tune your hyperparameter and remove any potentially irrelevant predictors? Provide justification for your selected penalty value.

Based on a number of factors, I selected model 8 with a penalty value of 0.000530. The results of top-models output were not definitive since models 1-10 were so similar, so I looked at the penalty vs. area under the roc curve plot above. I found that there was a slight drop-off in the graph at model 8, which suggests that this model was able to eliminate some irrelevant predictors.  I also looked at the ROC curves for each of the models, and I found that model 8 resulted in a slightly larger AUC than the other modelsm though this assessment was based on my eye-balled estimation.

#### Finally, provide your ROC plots and interpret them. How effective is your penalized logistic regression model at predicting each of the five wealth outcomes?

See the ROC curves for model 8 (penalty 0.000530) below:
![image](https://user-images.githubusercontent.com/78870884/117162132-8698f880-ad90-11eb-8880-3e0ff360fc50.png)


Looking at the ROC curves, the dotted diagonal lines show what each curve would be if the model predicted wealth with the same accuracy as it would predict by randomly guessing. Therefore, the further the ROC curve is from that middle 45 degree line, or the further the curve bends to the upper-left corner of the graph, the better the model can predict that wealth category. Based on the plots above, the model is clearly best at predicting wealth group 5, and is fairly decent at predicting wealth group 1 as well. This is interesting considering that wealth group 5 contains the wealthiest individuals and wealth group 1 contains the least wealthy individuals. The model is much worse at predicting wealth groups 2, 3, and 4. For wealth groups 2 and 3, the model's predictions were barely distinguishable from its random-guessing accuracy would have been. Therefore, the model is clearly much worse at predicting the middle-wealth categories.

### Model 2 - Random Forest

#### Using the R script provided, set up your random forest model and produce the AUC - ROC values for the randomly selected predictors, and the minimal node size, again with wealth as the target. 

![image](https://user-images.githubusercontent.com/78870884/117163599-cdd3b900-ad91-11eb-9daf-39e6e18fd11d.png)


#### How did your random forest model fare when compared to the penalized logistic regression? 

See the graph comparing the AUCs of the penalized logistic regression model to those of the random forest model:

![image](https://user-images.githubusercontent.com/78870884/117164193-636f4880-ad92-11eb-844b-0b114cfd6cd0.png)

Based on the graph above, the penalized logistic regression model performed very similarly to the random forest model. Though each model's accuracy varied between the different wealth groups, I would say that overall, neither model outperformed the other.


#### Provide your ROC plots and interpret them.

See the random forest model ROC plots below:
![image](https://user-images.githubusercontent.com/78870884/117164445-a0d3d600-ad92-11eb-9504-d9446431c9aa.png)

Similar to the penalized logistic regression model, the random forest model was much better at predicting wealth groups 1 and 5 than it was at predicting groups 2, 3, and 4.  However, when comparing the ROC curves of the penalized logistic regression model to those of the random forest model, it looks as though the random forest model was slightly better at predicting wealth categories 2, 3, and 4, but not by much. Again, the two models performed very similarly.

#### Are you able to provide a plot that supports the relative importance of each feature's contribution towards the predictive power of your random forest ensemble model?

![image](https://user-images.githubusercontent.com/78870884/117164493-aa5d3e00-ad92-11eb-80ae-c89bc76c2ca7.png)

The plot above shows that age is the most important factor in predicting a surveyed individual's wealth. Household size is also a fairly important factor. Gender is the least important predictive factor.

### Model 3 - Logistic Regression

#### Using the python script provided, train a logistic regression model using the tensorflow estimator API and your DHS data, again with wealth as the target. Apply the linear classifier to the feature columns and determine the accuracy, AUC and other evaluative metrics towards each of the different wealth outcomes. Then continue with your linear classifier adding the derived feature columns you have selected in order to extend capturing combinations of correlations (instead of learning on single model weights for each outcome). Again produce your ROC curves and interpret the results.

##### Wealth 1
```
'accuracy': 0.6883451 
'average_loss': 0.59280825
'loss': 0.5929089
'global_step': 11310
```

![image](https://user-images.githubusercontent.com/78870884/118855527-d7861200-b8a3-11eb-8821-d514bee26123.png)


##### Wealth 2

```
'accuracy': 0.73396933
'average_loss': 0.57869893
'loss': 0.5787238
'global_step': 11310
```

![image](https://user-images.githubusercontent.com/78870884/118856281-c5f13a00-b8a4-11eb-9610-f9c749102692.png)


##### Wealth 3

```
'accuracy': 0.7888013
'average_loss': 0.5132873
'loss': 0.51334107
'global_step': 11310
```

![image](https://user-images.githubusercontent.com/78870884/118857072-a3135580-b8a5-11eb-9c3d-81c2f9184843.png)


##### Wealth 4

```
'accuracy': 0.8763169
'average_loss': 0.36728418
'loss': 0.367226
'global_step': 11310
```

![image](https://user-images.githubusercontent.com/78870884/118857768-6a27b080-b8a6-11eb-8fc4-dc1d77a32a26.png)


##### Wealth 5

```
'accuracy': 0.90825385
'average_loss': 0.2762886
'loss': 0.2762716
'global_step': 11310
```

![image](https://user-images.githubusercontent.com/78870884/118859052-cb03b880-b8a7-11eb-83df-e99e0310cb32.png)



### Model 4 - Gradient Boosting

#### Using the python script provided, train a gradient boosting model using decision trees with the tensorflow estimator. Provide evaluative metrics including a measure of accuracy and AUC. Produce the predicted probabilities plot as well as the ROC curve for each wealth outcome and interpret these results.


##### Wealth 1
```
accuracy                  1.000000
accuracy_baseline         0.696972
auc                       1.000000
auc_precision_recall      1.000000
average_loss              0.091349
label/mean                0.303028
loss                      0.091349
precision                 1.000000
prediction/mean           0.304993
recall                    1.000000
global_step             100.000000
```

![image](https://user-images.githubusercontent.com/78870884/118860801-cf30d580-b8a9-11eb-9542-308a8fd8c514.png)


![image](https://user-images.githubusercontent.com/78870884/118860285-35692880-b8a9-11eb-8822-c27b18b023a7.png)


##### Wealth 2

```
accuracy                  0.738200
accuracy_baseline         0.738366
auc                       0.770746
auc_precision_recall      0.453652
average_loss              0.464010
label/mean                0.261634
loss                      0.464010
precision                 0.444444
prediction/mean           0.272995
recall                    0.002536
global_step             100.000000
```

![image](https://user-images.githubusercontent.com/78870884/118861611-b248d200-b8aa-11eb-8605-bfad9371af93.png)

![image](https://user-images.githubusercontent.com/78870884/118861840-f89e3100-b8aa-11eb-80df-f45f7ce5a4b5.png)


##### Wealth 3

```
accuracy                  0.789631
accuracy_baseline         0.789631
auc                       0.675607
auc_precision_recall      0.277711
average_loss              0.442328
label/mean                0.210369
loss                      0.442328
precision                 0.000000
prediction/mean           0.218761
recall                    0.000000
global_step             100.000000
```

![image](https://user-images.githubusercontent.com/78870884/118862684-01dbcd80-b8ac-11eb-91e3-8ff8644362d6.png)

![image](https://user-images.githubusercontent.com/78870884/118862771-191abb00-b8ac-11eb-9f3b-516ef3036e44.png)


##### Wealth 4

```
accuracy                  0.873828
accuracy_baseline         0.873828
auc                       0.714548
auc_precision_recall      0.235693
average_loss              0.341665
label/mean                0.126172
loss                      0.341665
precision                 0.000000
prediction/mean           0.135295
recall                    0.000000
global_step             100.000000
```

![image](https://user-images.githubusercontent.com/78870884/118864018-8da22980-b8ad-11eb-979c-2c5b9cc11506.png)

![image](https://user-images.githubusercontent.com/78870884/118864084-a14d9000-b8ad-11eb-8241-e3bdccddc205.png)


##### Wealth 5

```
accuracy                  0.901120
accuracy_baseline         0.901120
auc                       0.755125
auc_precision_recall      0.280141
average_loss              0.283597
label/mean                0.098880
loss                      0.283597
precision                 0.000000
prediction/mean           0.105340
recall                    0.000000
global_step             100.000000
```

![image](https://user-images.githubusercontent.com/78870884/118865047-921b1200-b8ae-11eb-9a33-22bfeee2cba9.png)

![image](https://user-images.githubusercontent.com/78870884/118865124-a65f0f00-b8ae-11eb-87ae-c6e22a4371e6.png)


### Analysis of 4 Models

#### Analyze all four models. According to the evaluation metrics, which model produced the best results? Were there any discrepancies among the five wealth outcomes from your DHS survey dataset?

