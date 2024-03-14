Linear Regression is a supervised ML algorithm used to find a relationship between dependent and independent variables. It does this by finding the best-fit line that minimizes the Sum of Squared Residuals (SSR).

### Methods:

- **Gradient Descent**: An optimization algorithm used to minimize the cost function.
- **Ordinary Least Squares (OLS)**: A mathematical approach that calculates the exact coefficients to minimize the sum of the squared differences between observed and predicted values.

### Pros:

- **Easy to Implement**: Simple to understand and code.
- **Interpretable**: The relationship between variables is clear and easy to explain.
- **Scalable**: Can be used with large datasets.

### Cons:

- **Prone to Overfitting**: Especially when dealing with many features or if the data is too noisy.
- **Doesn't Work Well with Non-linear Data**: Assumes a linear relationship between variables.
- **Sensitive to Outliers**: Outliers can significantly impact the best-fit line.

### Assumptions:

- **Linearity**: Assumes a linear relationship between dependent and independent variables.
- **No Multicollinearity**: Assumes that the independent variables are not highly correlated with each other.
- **Homoscedasticity**: Assumes that the residuals have constant variance across all levels of the independent variables.
- **Errors are Normally Distributed**: Assumes that the errors are normally distributed around the best-fit line.

### Types

1. **Simple Linear Regression**: This involves a single independent variable and a dependent variable. The relationship is modeled as a straight line.
    
2. **Multiple Linear Regression**: In this type, there are two or more independent variables. The model tries to fit a hyperplane to the data in higher-dimensional space.
    
3. **Ridge Regression (L2 Regularization)**: This is a form of linear regression that includes a penalty on the size of coefficients, specifically the squared magnitude of coefficients. It helps to prevent overfitting.
    
4. **Lasso Regression (L1 Regularization)**: Similar to Ridge, but the penalty is on the absolute value of the coefficients. It can lead to some coefficients being exactly zero, thus performing feature selection.
    
5. **Elastic Net Regression**: A combination of Ridge and Lasso, this model includes both L1 and L2 penalties, and it can be particularly useful when there are correlated variables.
    
6. **Polynomial Regression**: Although it's called linear, this model allows for polynomial relationships between independent and dependent variables. The linearity refers to the coefficients being linear, not the powers of the variables.