Regularization is a technique used in machine learning to prevent overfitting by adding a penalty term to the loss function. This penalty discourages the learning algorithm from assigning too much importance to any individual feature, thereby enhancing model generalization.

There are two main types of regularization: L1 and L2.

1. **L1 Regularization (Lasso)**: Adds an absolute value of magnitude of the coefficient as penalty term to the loss function. This can lead to sparse models where some feature weights can be zero, essentially performing feature selection.
    
    Formula: L(Regularized) = L(Original) + λ|w|
    
2. **L2 Regularization (Ridge)**: Adds a squared magnitude of the coefficient as penalty term to the loss function. This shrinks the coefficients but doesn't set any to zero, hence it doesn't perform feature selection like L1.
    
    Formula: L(Regularized) = L(Original) + λw²
    

In both formulas, L represents the loss, w represents the model weights (coefficients), and λ is the regularization strength parameter that determines how much we penalize high values of our weights. The values for λ are usually determined through cross-validation.

## How does adding a penalty term affect weights

Let's consider a simple linear regression model where we want to minimize the Mean Squared Error (MSE). Without regularization, we're trying to find parameters w that minimize the loss function L:

L = Σ(y_i - w*x_i)^2, where the sum is over all data points i in our training set, y_i is the actual value, and x_i is the corresponding input.

In Ridge Regression (L2 Regularization), we add a penalty term to the loss function:

L' = Σ(y_i - w*x_i)^2 + λw^2.

This new loss function L' will be minimized when both Σ(y_i - w*x_i)^2 and λw^2 are small.

Suppose the loss is minimized without any regularization (λ=0) at some w=w*. Now, suppose we have a non-zero λ. If |w*| is large, then λw*^2 can be quite large, which will increase the total loss L'. In order to minimize L', the model will try to reduce |w*|. So, the regularization term encourages the model to use smaller values for the weights w.

Similarly, in Lasso Regression (L1 Regularization), we minimize:

L' = Σ(y_i - w*x_i)^2 + λ|w|.

Again, if |w*| is large, then λ|w*| is large, and to minimize L', the model will try to reduce |w*|.

So, in both cases, the model is encouraged to use smaller values for the weights to minimize the loss function with the regularization term, which helps prevent overfitting by not allowing the model to rely too heavily on any single feature and by making the model more robust to noise in the data.

## Why does L1 can help in feature selection but not L2

The difference between L1 and L2 regularization that leads to L1 (Lasso) being used for feature selection is due to how they handle the penalty terms for the model coefficients. Let's see why.

1. **L1 Regularization (Lasso):** The L1 regularization adds a penalty equal to the absolute value of the magnitude of coefficients. As a result, some of the coefficients can become zero. The level of shrinkage is controlled by the regularization parameter λ. If λ is large enough, some coefficients will be exactly zero. Hence, L1 regularization performs feature selection by excluding the non-informative or less important features (those features having zero as coefficient after regularization).
    
2. **L2 Regularization (Ridge):** In contrast, L2 adds a penalty equal to the square of the magnitude of coefficients. This process reduces the magnitude of the coefficients but does not make them zero, hence it cannot exclude the less important features.
    

Mathematically, consider the following regularization terms:

- L1: λ|w|
- L2: λw²

In L1, as λ increases, the penalty also linearly increases, leading to coefficients being zero when the penalty exceeds the original coefficient value.

In L2, as λ increases, the penalty increases quadratically, but never completely nullifies the original coefficient since the derivative of the penalty term w.r.t. the coefficient w (which leads to the update of the coefficient) is proportional to w itself. When w is very small, the update is also very small, hence it never completely becomes zero.

The difference in behavior between L1 and L2 regularization gives L1 an advantage in situations where we want to reduce the number of features, as it can effectively perform feature selection by forcing some coefficients to be exactly zero.

## how can we decide the value of lambda?

Determining the optimal value of the regularization parameter λ is a critical step in successfully applying L1 or L2 regularization. The parameter λ controls the trade-off between the bias and variance in the model, or in other words, the trade-off between overfitting and underfitting.

A common method to select the best value for λ is through cross-validation. In k-fold cross-validation, the training data is randomly partitioned into k equal-sized subsamples. Of the k subsamples, a single subsample is retained as the validation data for testing the model, and the remaining k-1 subsamples are used as training data. The process is then repeated k times, with each of the k subsamples used exactly once as the validation data. The k results can then be averaged to produce a single estimation.

For each split of the data, a model is trained for different values of λ, and the performance of the model is evaluated. The value of λ that gives the best average performance on the validation data is chosen as the optimal value of λ.

A variant of this approach is to perform a grid search across multiple hyperparameters simultaneously. For example, if you are using a support vector machine, you might perform a grid search across both the regularization parameter and the kernel bandwidth parameter, training a model for every combination of parameters and selecting the combination that performs the best on the validation data.

Note that it's important to evaluate the models on the validation data, not the training data, since we want to select the value of λ that results in the best generalization to unseen data, not the one that results in the best fit to the training data.

## Applications

Regularization is a technique applicable to a number of machine learning algorithms, particularly those involving the learning of weight parameters. Here are some examples:

**Applicable:**

1. **Linear Regression**: Regularization is commonly applied in linear regression to prevent overfitting, resulting in Ridge Regression (L2 regularization) and Lasso Regression (L1 regularization).
    
2. **Logistic Regression**: Logistic Regression can also be regularized using L1 or L2 penalties to prevent overfitting when there are many input features.
    
3. **Neural Networks**: Regularization, particularly L2, is often used in training deep neural networks to prevent overfitting. Dropout is another form of regularization used in deep learning to prevent complex co-adaptations on training data.
    
4. **Support Vector Machines**: The C parameter in SVMs plays a role similar to the inverse of the regularization strength λ, i.e., smaller values of C specify stronger regularization.
    

**Not Applicable:**

1. **Decision Trees**: Regularization in the form of L1 or L2 is not applicable to decision tree models because they do not involve the learning of continuous weight parameters. Instead, complexity control is typically achieved through methods like pruning, setting the maximum depth of the tree, or setting the minimum samples required at a leaf node.
    
2. **Naive Bayes**: Regularization isn't applicable because Naive Bayes is based on applying Bayes' theorem with strong (naive) independence assumptions between the features. There aren't continuous weight parameters being learned.
    
3. **K-Nearest Neighbors (KNN)**: Regularization isn't applicable here because KNN does not have a typical training phase to learn parameters. The model's complexity is controlled by the hyperparameter K (the number of neighbors), but it doesn't have continuous weights or coefficients to regularize.
    
4. **Random Forests**: Regularization methods like L1 and L2 are not directly applicable to Random Forests, as they build upon decision trees. They handle overfitting by creating a large number of them and then averaging their results.
    

Remember, the list above is not exhaustive, and there may be exceptions or specific implementations that differ from these general rules.

## Other forms of normalization

1. **Elastic Net Regularization:** A combination of L1 and L2 regularization, it adds both an absolute value of the magnitude and a squared magnitude of the coefficients as penalty term to the loss function.
    
2. **Dropout:** A technique primarily used in neural networks where randomly selected neurons are ignored during training. This helps to prevent overfitting by ensuring that the model does not become too reliant on any one neuron.
    
3. **Early Stopping:** In this form of regularization, we stop the training before the model has had a chance to overfit to the training data.
    
4. **Data Augmentation:** While not a form of regularization in the traditional sense, it does increase the amount and diversity of training data, preventing overfitting by helping the model generalize better.
    
5. **Noise Injection:** Noise is added to the inputs or even inside the network to make the model more robust and prevent overfitting.
    
6. **Weight Decay:** This is another name for L2 regularization, often used in the context of neural networks.
    
7. **Batch Normalization:** Again, while not a traditional form of regularization, it has a regularizing effect and can sometimes reduce the need for dropout or L2 regularization.
    
8. **Max-Norm Regularization:** In this type, a maximum value of the norm of the weight vector for each neuron is enforced by adjusting the weights after gradient descent has been applied.
    
9. **Parameter Norm Penalty:** Adds a penalty term equivalent to the norm of the parameters of the model to the loss function.

## Cheat Sheet

![[Slide6.png]]

