# Classification
## Confusion Matrix

It is used in the classification problem to establish a relationship between predicted values and actual values. It shows how many values are predicted correctly and how many are predicted wrong for each class. We can derive the different type of metrics that will show how much good fit our model is.

![](https://miro.medium.com/v2/resize:fit:875/1*me1DR4K60MqT4Ftc4PtKwA.png)

## For balance dataset:

### 1. Accuracy

When the dataset is balanced we use Accuracy. Accuracy tells the percentage total correctly predicted value out of total values.

![](https://miro.medium.com/v2/resize:fit:459/1*PFkR6PqbjOgGhQ4lmvjbBg.png)

For an imbalanced dataset, we cannot use accuracy as it may not give a good result.

For Example: Out of 100 values if TP=90 TN=0 the accuracy still be 90%, which sounds good but not because TN is not detected correctly and output is more bias towards TP.

## For imbalance dataset

![](https://miro.medium.com/v2/resize:fit:625/1*vBKpEeHnQHybqHTnFRqyXQ.jpeg)

### 1. Precision

Out of all the **predicted** positive values how many are predicted correctly.

![](https://miro.medium.com/v2/resize:fit:346/1*8yUtYBc_k5Rz7o0BQPsw_A.png)

Precision is used when a False Positive is more important like in spam detection if a mail is not spam and the model predicted it as spam, we will miss a very important mail because of this error.

### 2. Recall or Sensitivity

Out of all the **actual** positive values how many are predicted correctly. It is also known as **True Positive Rate(TPR).**

![](https://miro.medium.com/v2/resize:fit:335/1*SVZ8cyS7gUOLD6yHvoUbFg.png)

Precision is used when a False Negative is more important like a patient is covid positive but the model detected it as negative, it will cause a great impact on healthcare. If the patient is not covid positive still detected as positive, we can do further testing for that but vice vera shouldn't happen.

### 3. Specificity

Out of all the **actual negative** values how many are predicted correctly. **False Positive Rate(FPR)**=1-Specificity

![](https://miro.medium.com/v2/resize:fit:396/1*szrYLZhH6RM4mxd3S5swgg.png)

### 4. F Beta Score

It shows a relationship between Precision and Recall.

![](https://miro.medium.com/v2/resize:fit:759/1*N43Zx1UQzkyARbY1DKonMw.png)

When F=1, F1 will be harmonic mean of Precision and Recall i.e 2*pr*re/(pr+re)

If Precision is more important to us than put F>1 and if Recall is more important to us put F<1.

### ROC and AUC curve

We need to try different threshold values to get the best TPR(Sensitivity) and FPR(1 - Specificity) value. We can’t try all the values manually(consider different confusion matrices for a different threshold value in case of logistic regression). For this, we use ROC and AUC curve.

![](https://miro.medium.com/v2/resize:fit:313/1*1Tu-av75J3e-VOXih4g6IA.png)

We can try for different values TPR and FPR and we can also try for the different algorithm to find the best fit for our data. The model that fit most data under the curve is considered the best model.

In an ROC (Receiver Operating Characteristic) curve, the model with the larger Area Under the Curve (AUC) is considered better.

# Regression
## **Mean Absolute Error (MAE)**

MAE = (1/n) * Σ |yi - ŷi|

- Measures average absolute difference between actual and predicted values.
- Gives equal weight to all errors.
- Scale dependent, easy to interpret.

## **Mean Squared Error (MSE)**

MSE = (1/n) * Σ (yi - ŷi)2

- Measures average squared difference between actual and predicted values.
- Accounts for large errors more than MAE.
- Scale dependent, difficult to interpret.

## **Root Mean Squared Error (RMSE)**

RMSE = √(MSE)

- Takes square root of MSE.
- Easier to interpret being in same units as target.

## **R-squared (R2)**

- R-squared measures the proportion of variance in the target variable that is explained by the independent variables in the model.
- It ranges from 0 to 1, with higher values indicating more variance explained by the model.
- It is calculated as 1 - (SSres/SStot), where:

SSres = Sum of squares of residuals SStot = Total sum of squares

- Residuals are the differences between the observed target values and the values predicted by the model.
- Total sum of squares is the sum of squares of differences between the observed values and their mean.
- So R2 compares the residuals to the total variance in y. The lower the residuals, the better the model fits the data.
## **Adjusted R-squared**

- The regular R2 always increases when new predictors are added, even if those predictors are insignificant.
- To account for this, adjusted R2 only increases if new terms improve the model more than expected by chance.
- It is calculated as:

R2_adj = 1 - (1 - R2)*(n-1)/(n-p-1)

Where: n = number of samples p = number of predictors

- Adjusted R2 increases only if new predictors improve model fit. It prevents overfitting.
- Generally used when comparing models with different numbers of predictors.

# Cheat Sheet
![[Slide2.png]]