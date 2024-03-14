
**Principal component analysis** (**PCA**) is a statistical procedure that is used to reduce the dimensionality. It uses an orthogonal transformation to convert a set of observations of possibly correlated variables into a set of values of linearly uncorrelated variables called principal components. It is often used as a dimensionality reduction technique.

# Intiution

## 1. Plot data

Let’s assume our data looks like below. On the left, are features x1, x2, x3. On the right, those points are plotted.

![](https://miro.medium.com/v2/resize:fit:875/1*98SpEWcSAynwppAPo3hlcw.png)

## 2. Mark center of the data

Green circle is the mean of features: x1, x2, x3.

![](https://miro.medium.com/v2/resize:fit:875/1*Jv4fiyEjMkyplY_iGtDzxw.png)

## 3. Center shifting

Shift the center of axes to the mean of the data points.

![](https://miro.medium.com/v2/resize:fit:875/1*g1VhQu6vpMhzxFcNxwF3tw.png)

_Note data points relative position doesn’t change_

## 4. Line of best fit

The line of best fit is called PC1 (principal component 1). PC1 **maximizes** the sum of squared distances from where points meet the line of best fit at a right angle. **Principal Component’s direction of the data is that along which the observations vary the most.**

PC1 is a [linear combination](https://en.wikipedia.org/wiki/Linear_combination#:~:text=From%20Wikipedia%2C%20the%20free%20encyclopedia,a%20and%20b%20are%20constants).) of x1, x2 and x3, meaning it contains parts of each x1, x2 and x3. PC2 is also a linear combination of each x1, x2 and x3 but exactly in perpendicular direction to PC1. PC1 and PC2 now both explain most of the variance in our features.

![](https://miro.medium.com/v2/resize:fit:875/1*aUNV3Dul59ilZg-JWZhygA.png)

**Orthogonal Principal Components** preserving most of the information of our data

## 5. Readjusting the axes

Rotate the axes such that PC1 is X and PC2 is Y axes respectively. Post-rotation, our data is now in just 2 dimensions! And clusters are easy to spot.
![](https://miro.medium.com/v2/resize:fit:875/1*h-SR4eYSW0Op7mMCbqKXLQ.png)


# Steps Involved in the PCA

**_Step 1:_** Standardize the dataset.

**_Step 2:_** Calculate the covariance matrix for the features in the dataset.

**_Step 3:_** Calculate the eigenvalues and eigenvectors for the covariance matrix.

**_Step 4:_** Sort eigenvalues and their corresponding eigenvectors.

**_Step 5:_** Pick k eigenvalues and form a matrix of eigenvectors.

**Step 6:** Transform the original matrix.

Let's go to each step one by one.

## **1. Standardize the Dataset**

Assume we have the below dataset which has 4 features and a total of 5 training examples.

![](https://miro.medium.com/v2/resize:fit:650/1*LRIwao7YjAvYfkWpWVrQ_A.png)

Dataset matrix

First, we need to standardize the dataset and for that, we need to calculate the mean and standard deviation for each feature.

![](https://miro.medium.com/v2/resize:fit:303/1*X4YeGxtzOhnnOWBfoBBJfA.png)

Standardization formula

![](https://miro.medium.com/v2/resize:fit:809/1*FmF9jyYmoapgK1_1U6UxfA.png)

Mean and standard deviation before standardization

After applying the formula for each feature in the dataset is transformed as below:

![](https://miro.medium.com/v2/resize:fit:649/1*AGic5zirVFgu81HU4Srenw.png)

Standardized Dataset

## 2. Calculate the covariance matrix for the whole dataset

The formula to calculate the covariance matrix:

![](https://miro.medium.com/v2/resize:fit:724/1*ptVjFC7JUJVgnoFEEt6R8w.png)

Covariance Formula

the covariance matrix for the given dataset will be calculated as below

![](https://miro.medium.com/v2/resize:fit:808/1*OqKstUmkOHkTO3dayB1QIA.png)

Since we have standardized the dataset, so the **mean for each feature is 0** and the standard deviation is 1.

var(f1) = ((-1.0-0)² + (0.33-0)² + (-1.0-0)² +(0.33–0)² +(1.33–0)²)/5  
**var (f1) = 0.8**

cov(f1,f2) =  
((-1.0–0)*(-0.632456-0) +  
(0.33–0)*(1.264911-0) +  
(-1.0–0)* (0.632456-0)+  
(0.33–0)*(0.000000 -0)+  
(1.33–0)*(-1.264911–0))/5  
**cov(f1,f2 = -0.25298**

In the similar way be can calculate the other covariances and which will result in the below covariance matrix

![](https://miro.medium.com/v2/resize:fit:809/1*fyL-SEd7KhNT2WWTjdU_GQ.png)

covariance matrix (population formula)

## 3. Calculate eigenvalues and eigen vectors.

An **eigenvector** is a nonzero vector that changes at most by a scalar factor when that linear transformation is applied to it. The corresponding **eigenvalue** is the factor by which the eigenvector is scaled.

Let A be a square matrix (in our case the covariance matrix), ν a vector and λ a scalar that satisfies Aν = λν, then λ is called eigenvalue associated with eigenvector ν of A.  
Rearranging the above equation,

> Aν-λν =0 ; (A-λI)ν = 0

Since we have already know ν is a non- zero vector, only way this equation can be equal to zero, if

> det(A-λI) = 0

![](https://miro.medium.com/v2/resize:fit:810/1*I-Zum-NHZUnZgACi_ePjuw.png)

A-λI = 0

Solving the above equation = 0

**_λ = 2.51579324 , 1.0652885 , 0.39388704 , 0.02503121_**

**Eigenvectors:**

Solving the (A-λI)ν = 0 equation for ν vector with different λ values:

![](https://miro.medium.com/v2/resize:fit:808/1*isDsfzvBy8OkFpWib65Uuw.png)

For λ = _2.51579324, solving the above equation using Cramer's rule, the values for v vector are_

_v1 = 0.16195986  
v2 = -0.52404813  
v3 = -0.58589647  
v4 = -0.59654663_

Going by the same approach, we can calculate the eigen vectors for the other eigen values. We can from a matrix using the eigen vectors.

![](https://miro.medium.com/v2/resize:fit:476/1*Q7vYpDjZzA_CBk2jZinVkg.png)

eigenvectors(4 * 4 matrix)

## **_4._ Sort eigenvalues and their corresponding eigenvectors.**

Since eigenvalues are already sorted in this case so no need to sort them again.

## **_5._** Pick k eigenvalues and form a matrix of eigenvectors

If we choose the top 2 eigenvectors, the matrix will look like this:

![](https://miro.medium.com/v2/resize:fit:241/1*meALpdF0_Ry7SzIRafwFLg.png)

Top 2 eigenvectors(4*2 matrix)

## **6.** Transform the original matrix.

Feature matrix * top k eigenvectors = Transformed Data

![](https://miro.medium.com/v2/resize:fit:875/1*mnMItx1CCKgiFtCRPi97wA.png)

# Assumptions

- **Sample size**: Ideally, there should be at least 150 cases and there should be a ratio of a minimum five cases for each variable
- **Correlations:** Some kind of correlation must exist between the variables or factors to be considered for PCA
- **Linearity:** A linear relationship must exist between the variables
- **Outliers:** There should be no outliers present in the data as it causes disturbance during PCA

![](https://miro.medium.com/v2/resize:fit:380/0*JQmnUETkSOweMxVT)

Picture 2

# Objectives of PCA

1. PCA reduces attribute or characteristic space from a larger set of variables into a smaller set of factors and does not depend on the dependent variable to be specified, or in other words, **PCA is a ‘non-dependent’ type of procedure**.
2. **PCA is a data compression or dimensionality reduction technique**. The goal of PCA is to reduce the space between the variables and there is no guarantee that the dimensions are interpretable
3. PCA basically **creates a subset of variables from the main set** based on which all variables from the main set have the highest correlation with the prime components