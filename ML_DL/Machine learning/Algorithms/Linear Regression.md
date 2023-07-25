## Introduction

Linear regression is a statistical method used to determine the linear relationship between a dependent variable (also known as the outcome or response variable) and one or more independent variables (also known as predictors or explanatory variables).

In layman's terms, linear regression is a way to understand the relationship between different variables, and to make predictions about one variable based on the values of others. For example, you might use linear regression to understand the relationship between a person's age and their income, and then use that information to predict someone's income based on their age.

A technical explanation: Linear regression is a model that assumes a linear relationship between the input variables (x) and the single output variable (y). Mathematically, we can represent this relationship as y = w * x + b, where w is the weight and b is the bias. The goal of linear regression is to find the best values for w and b such that the difference between the predicted output and the actual output is minimized. This difference is called the cost, and it is commonly the sum of the squared differences between the predicted and actual outputs.

## Types of Linear regression

There are several different types of linear regression, each with its own strengths and weaknesses. Some of the most common types include:

1.  Simple Linear Regression: This type of linear regression is used when there is only one independent variable. It is used to study the relationship between two continuous variables, with one being the predictor (or independent) variable and the other being the response (or dependent) variable.

![[Pasted image 20230128150616.png]]

![[Pasted image 20230128150630.png]]

2.  Multiple Linear Regression: This type of linear regression is used when there are two or more independent variables. It is used to study the relationship between a response variable and multiple predictor variables. It can be used to understand how each predictor variable affects the response variable and how they work together.

          ![[Pasted image 20230128150511.png]]
    
3.  Polynomial Regression: This type of linear regression is used when the relationship between the independent and dependent variables is non-linear. It uses a polynomial equation to model the relationship between the variables, which allows for more flexibility in fitting the data.
    
4.  Logistic Regression: This type of linear regression is used when the response variable is binary (i.e. it only takes on two values, such as true/false or 0/1). It is used to model the probability of a certain event occurring, and is commonly used in classification tasks.
    
5.  Ridge Regression: This type of linear regression is used when there are a large number of predictor variables, and some of them are correlated. It adds a penalty term to the cost function to shrink the values of the coefficients, which can help prevent overfitting.
    
6.  Lasso Regression: This is also a type of linear regression which is used to prevent overfitting by adding a penalty term to the cost function, but this penalty term is the absolute value of the coefficients, which can shrink some of the coefficients to zero and thus perform feature selection.
    
It is important to note that different types of linear regression are suitable for different types of problems and data sets. The choice of which type to use will depend on the specific problem you are trying to solve and the characteristics of your data.

## Different ways to find best fit line

There are several ways to determine the best fit line when using linear regression. Some of the most commonly used methods include:

1.  Ordinary Least Squares (OLS): This is the most common method used to find the best fit line. It finds the line that minimizes the sum of the squared differences between the predicted and actual values. This method is sensitive to outliers and can be affected by the presence of correlated predictor variables.
    
2.  Gradient Descent: This method is an optimization algorithm that iteratively improves the line by adjusting the coefficients (i.e. the slope and y-intercept of the line) in the direction that reduces the cost function.
    
3.  Normal Equation: This method is an analytical solution for finding the best fit line, which is based on finding the inverse of the matrix of the input variable, this method is faster than gradient descent but it can be computationally expensive when the number of features is very high.
    
4.  Ridge Regression and Lasso Regression: These are regularized version of OLS, they add a penalty term to the cost function, which helps to prevent overfitting. Ridge regression adds a penalty term that is the sum of the squared coefficients, while Lasso regression adds a penalty term that is the sum of the absolute values of the coefficients.
    
5.  Bayesian Linear Regression: This method is based on Bayesian statistics, which allows for prior information about the model parameters to be incorporated into the estimation process.
    
It is important to note that the choice of which method to use will depend on the specific problem you are trying to solve and the characteristics of your data. For example, if your data has many correlated predictor variables, Ridge or Lasso regression may be more appropriate than OLS.

#### OLS(ordinary leats squares)

The Ordinary Least Squares (OLS) method is a widely used method for finding the best fit line in linear regression. The goal of OLS is to find the line that minimizes the sum of the squared differences between the predicted and actual values. The equation of the best fit line is represented as:

y = w * x + b

Where y is the dependent variable, x is the independent variable, w is the slope of the line, and b is the y-intercept.

The OLS method uses a cost function, also called the residual sum of squares (RSS), to measure the differences between the predicted and actual values. The cost function is defined as:

RSS = ∑(y - (w * x + b))^2

where the summation is taken over all the data points.

To find the best fit line, OLS method tries to minimize this cost function by adjusting the values of the coefficients (w and b) iteratively until the cost function reaches a minimum value.

Once the coefficients have been determined, the OLS method can be used to predict the value of the dependent variable for a given value of the independent variable.

It is important to note that OLS method assumes that the errors are normally distributed, and that there is no multicollinearity among the independent variables. OLS method also assumes that there is no outliers in the data, as those can have a big impact on the result.

y = β0 + β1 x + ε — — — — — — — — — — (1)

Where β0: intercept

β1: slope (unknown constant)

ε: random error component

This is a line where y is the dependent variable we want to predict, x is the independent variable, and β0 and β1 are the coefficients that we need to estimate.

**Estimation of β0 and β1 :**

The OLS method is used to estimate β0 and β1. The OLS method seeks to minimize the sum of the squared residuals. This means from the given data we calculate the distance from each data point to the regression line, square it, and the sum of all of the squared errors together.

![](https://miro.medium.com/max/625/0*gglavDlTUWKn4Loe)

The difference between actual and predicted values is called residual (e) and can be negative or positive depending on whether the model overpredicted or underpredicted the outcome. Hence, to calculate the net error, adding all the residuals directly can lead to the cancellations of terms and reduction of the net effect. To avoid this, we take the sum of squares of these error terms, which is called the **_Residual Sum of Squares (RSS)._**
![Image for post](https://miro.medium.com/max/249/0*1m12le87BriQkEMF.png)

From equation (1) we may write

yi = β0 + β1 x + εi, _i_ = 1, 2, …..n — — — — — — — — — (2)

The equation (2) is a sample regression model, written in terms of the n pairs of data (yi, xi) (i = 1, 2,……..,n). Thus, the least-squares criteria are

![](https://miro.medium.com/max/875/1*d4y8jE1R6yPlnh7BsuOBcA.jpeg)

![](https://miro.medium.com/max/875/1*Jmh8qropV2EluJcnbS501w.jpeg)

![](https://miro.medium.com/max/875/1*fkZUx5bMN6RyJSP_msvDZA.jpeg)

![](https://miro.medium.com/max/875/1*esj6-SmvIKPVEENEYDCimA.jpeg)

Ordinary Least Square Method

![](https://miro.medium.com/max/588/1*RFfg-kIoXyw8beUndWIhDw.png)

Let’s take a simple example. This table shows some data from the manufacturing company. Each row in the table shows the sales for a year and the amount spent on advertising that year. Here our target variable is sales-which we want to predict.

Linear Regression estimates that Sales = β0 + β1 * (Advertising)

**Estimating the Slope ( β1):**

1.  Calculate the mean value of x and y

![](https://miro.medium.com/max/551/1*_eIxoB-P736SGJTTy2Yxww.png)

2. Calculate the error of each variable from the mean

![](https://miro.medium.com/max/665/1*YT_NvQhLDhkUt1-LkEIHIA.png)

3. Multiply the error for each x with the error for each y and calculate the sum of these multiplications

![](https://miro.medium.com/max/843/1*rI7k_qWUI4FeOCOHOKrXZg.png)

4. Square the residual of each x value from the mean and sum of these squared values

![](https://miro.medium.com/max/875/1*u46I8hxohOrEviOa6xofaA.png)

Now we have all the values to calculate the slope (β1) = 221014.5833/8698.694 = 25.41

**Estimating the Intercept ( β0):**

β0 = mean(y)-(β1* mean(x))

we already know all the values to calculate β0.

β0 = 968.5-(37.83333333 * 25.41)=7.239

**Making Predictions:**

Now, we have the coefficients for our simple linear regression.

y = 7.239 + 25.41* x

Let’s make predictions for our data.

![](https://miro.medium.com/max/875/1*ADgCdalF6qctPjG19vaExg.png)

**Estimating Error:** Calculate the error for our predictions (Root Mean Squared Error or RMSE)

![](https://miro.medium.com/max/450/1*3iS6PJV54Kn_VR0YGVX82g.png)
Root Mean Squared Error

![](https://miro.medium.com/max/875/1*wUJhzUt_QTb8OEkoEtf1Yg.png)

From the calculated RMSE we can say that each prediction is on average wrong by about 39.2059 units.

#### Gradient Descent

![](https://miro.medium.com/max/564/1*SN8YgZ4MPxnTxZDUYKWVUA.png)

![](https://miro.medium.com/max/525/1*Hls-F1jj-RSfR-eFs8-Ymw.png)

![](https://miro.medium.com/max/525/1*Hls-F1jj-RSfR-eFs8-Ymw.png)

Our goal is to minimize the cost as much as possible in order to find the best fit line. We are not going to try all the permutation and combination of **m** and **c** (inefficient way) to find best fit line. For that we will use Gradient Decent Algorithm.

Gradient Decent is an algorithm that finds best fit line for a given training dataset in less number of iteration.

If we plot m and c against MSE, it will acquire a bowl shape (As shown in the diagram below)

![](https://miro.medium.com/max/361/1*4ov6t0bikVu2xTrJXlJZEw.png)
For some combination of m and c we will get the least Error (MSE). That combination of m and c will give us our best fit line.

The algorithm starts with some value of m and c (usually starts with m=0, c=0). We calculate MSE (cost) at point m=0, c=0. Let say the MSE (cost) at m=0, c=0 is 100. Then we reduce the value of m and c by some amount (Learning Step). We will notice decrease in MSE (cost). We will continue doing the same until our loss function is a very small value or ideally 0 (which means 0 error or 100% accuracy).

*Step By Step Algorithm

1.  Let m = 0 and c = 0. Let L be our learning rate. It could be a small value like 0.01 for good accuracy.

> Learning rate gives the rate of speed where the gradient moves during gradient descent. Setting it too high would make your path instable, too low would make convergence slow. Put it to zero means your model isn’t learning anything from the gradients.

2. Calculate the partial derivative of the Cost function with respect to m. Let partial derivative of the Cost function with respect to m be Dm (With little change in m how much Cost function changes)

![](https://miro.medium.com/max/651/1*nEsjBQMJSFYHTclhUhgJXg.png)

Similarly let’s find the partial derivative with respect to c. Let partial derivative of the Cost function with respect to c be Dc (With little change in c how much Cost function changes).

![](https://miro.medium.com/max/633/1*KmcMvLHTl4ZN8r4mTCJryQ.png)

3. Now update the current values of m and c using the following equation:

![](https://miro.medium.com/max/165/1*QCSAUCGY8Rg7eyrx3g2olQ.png)

4. We will repeat this process until our Cost function is a very small (ideally 0).

**Gradient Decent Algorithm** gives optimum values of m and c. With these values of m and c we will get the equation of the best-fit line and ready to make predictions.

## Multiple linear regression

## Polynomial linear regression

## Regression metrics

<iframe width="560" height="315" src="https://www.youtube.com/embed/Ti7c-Hz7GSM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Ridge regression

## Lasso regression

## Implementation



