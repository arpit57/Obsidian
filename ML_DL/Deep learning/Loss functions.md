## Introduction

A loss function is a mathematical function used in deep learning to measure how well a model is performing on a given task. It quantifies the difference between the model's predictions and the true values of the output, and the goal of the model is typically to minimize this loss function.

![[Pasted image 20230220173620.png]]


## Difference between loss and cost function

In deep learning, the terms "loss function" and "cost function" are often used interchangeably, but there is a subtle difference between the two.

A loss function is typically used to measure the difference between the predicted output of a model and the true output for a single training example. For example, in a regression problem, the loss function could be the squared difference between the predicted value and the true value for a single data point.

A cost function, on the other hand, is the average of the loss functions of all the training examples in a dataset. In other words, the cost function is the overall measure of how well the model is performing on the entire training set. The cost function is what the model tries to minimize during training, by adjusting its parameters to reduce the overall difference between the predicted and true outputs.

## Loss function for regression:

When we are dealing with numeric variables, we have to measure the losses numerically, meaning, just knowing if the predicted value is wrong is not enough, we have to calculate the amount of deviation of our prediction from the actual value, so we can train our network accordingly.

**The different loss functions for this are :**

-   Mean Absolute Error (MAE).
-   Mean Absolute Percentage Error (MAPE).
-   Mean Squared Error (MSE).
-   Root Mean Squared Error (RMSE).
-   Huber Loss.
-   Log-Cosh Loss.

### Mean Absolute Error (MAE) :

MAE is the simplest error function, it literally just calculates the **absolute difference** (discards the sign) between the actual and predicted values and takes it’s mean.

![](https://miro.medium.com/max/475/1*F6ClwOW-dmFEnJrVLFCaqQ.png)
Graph :

The following figure shows that the MAE increases linearly with an increase in error.

![](https://miro.medium.com/max/800/1*oIvrB4yi0S4oumSDtKTH5g.jpeg)

Image by author

**Advantages :**

1.  MAE is the simplest method to calculate the loss.
2.  Due to its simplicity, it is computationally inexpensive.

**Drawbacks :**

1.  MAE calculates loss by considering all the errors on the same scale. For example, if one of the output is on the scale of hundred while other is on the scale of thousand, our network won’t be able to distinguish between them just based on MAE, and so, it’s hard to alter weights during backpropagation.
2.  MAE is a linear scoring method, i.e. all the errors are weighted equally while calculating the mean. This means that while backpropagation, we may just jump past the minima due to MAE’s steep nature.

### Mean Absolute Percentage Error (MAPE) :

MAPE is similar to that of MAE, with one key difference, that it calculates error in terms of **percentage**, instead of raw values. Due to this, MAPE is independent of the scale of our variables.


![](https://miro.medium.com/max/373/1*8cZ3S6_EHaWtM3qELhg3Uw.png)

MAPE Equation from [JIBC](https://lh3.googleusercontent.com/proxy/l27LUwKgwU7t5cnbrxr-gU07XgWGsTUhFmIYXN3L6a147THUjHo2YnQsMd2VTPa_KeEzY26C8NdWKTdsdXttRoxtl0MNz7pQKwafJBZwU94yNY5B1M6vOkpHyTMgnQ1ERJ4UNizRWeo)

Graph :

The following figure shows that the MAPE also increases linearly with an increase in error.

![](https://miro.medium.com/max/800/1*0hbNOtpfr6aoR_Bmty-JkA.jpeg)

Image by author

**Advantages :**

1.  Loss is calculated by normalizing all errors on a common scale (of hundred).

**Disadvantages :**

1.  MAPE equation has the expected output in the denominator, which can be zero. Loss cannot be calculated for these, as division by zero is not defined.
2.  Again, division operation means that even for the same error, the magnitude of actual value can cause a difference in loss. For example, if the predicted value is 70 and the actual value is 100, the loss would be 0.3 (30%), while for the actual value of 40, the loss would be 0.75 (75%), even though the error in both the cases is the same, i.e. 30.

### Mean Squared Error (MSE) :

In MSE, we calculate the square of our error and then take it’s mean. This is a **quadratic scoring** method, meaning, the penalty is proportional to not the error (like in MAE), but to the **square of the error**, which gives relatively higher weight (penalty) to large errors/outliers, while smoothening the gradient for smaller errors.


![](https://miro.medium.com/max/550/1*tD7k9QCX7QdQFurcy8jVIw.png)

MSE Equation from [Medium](https://miro.medium.com/max/880/1*20m_U-H6EIcxlN2k07Z7oQ.png) by [Lachlan Miller](https://medium.com/@lachlanmiller_52885)

Graph :

The above figure shows that the MSE increases exponentially with an increase in error.

![](https://miro.medium.com/max/800/1*1alssyRLNBz7CsPWUUAY_g.jpeg)

Image by author

**Advantage :**

1.  For small errors, MSE helps converge to the minima efficiently, as the gradient reduces gradually.

**Drawback :**

1.  Squaring the values does increases the rate of training, but at the same time, an extremely large loss may lead to a drastic jump during backpropagation, which is not desirable.
2.  MSE is also sensitive to outliers, i.e. outliers in data may impact our network more, as the loss for these will be considerably higher.

### Root Mean Squared Error (RMSE) :

RMSE is just the **square root** of MSE, which means, it is again, a linear scoring method, but still better than MAE as it gives comparatively more weightage to larger errors.


![](https://miro.medium.com/max/515/1*RSYTYpqyGDYWPmI0rD8zqA.png)


Graph :

![](https://miro.medium.com/max/800/1*fADKNrCC6-RqHSSSGmS_DA.jpeg)

Image by author

**Advantages :**

1.  Less extreme losses even for larger values.
2.  More sensitive to outliers than MAE.

**Disadvantage :**

1.  RMSE is still a linear scoring function, so again, near minima, the gradient is sudden.

### MAE vs MSE vs RMSE vs MAPE :

![](https://miro.medium.com/max/800/1*32P7CzvHv_M2QIG_GjKEJw.jpeg)

### Huber Loss :

Huber loss is a superb combination of **linear** as well as **quadratic** scoring methods. It has an additional hyperparameter **delta (δ)**. Loss is linear for values above delta and quadratic below delta. This parameter is tunable according to your data, which makes the Huber loss special.


![](https://miro.medium.com/max/875/1*2QDciI--0L5Zqd8UXgXaWg.jpeg)


Graph :

The following figure shows the change in Huber loss for different values of the δ against error.

![](https://miro.medium.com/max/800/1*gTUzf_mRdIPPZ96Qi5qrgw.jpeg)

Image by author

**Advantages :**

1.  Modifiable hyperparameter delta (δ).
2.  Linearity above delta ensures fair weightage to outliers (Not as extreme as in MSE).
3.  Curved nature below delta ensures the right length of steps during backpropagation.

**Disadvantages :**

1.  Due to additional conditionals and comparisons, Huber loss is comparatively expensive in terms of computations, especially if your dataset is large.
2.  To get the best results, δ also needs to be optimized, which increases training requirements.

### Log-Cosh Loss:

Graphically, Log-cosh is quite similar to Huber loss as it is also a combination of linear and quadratic scorings. One difference that sets this apart is that it is **double differentiable**. Some optimization algorithms like XGBoost prefer such functions over Huber, which is differentiable only once. Log-cosh calculates the log of hyperbolic cosine of the error.


![](https://miro.medium.com/max/875/1*E1rPO9300Z5eVcvugahskQ.png)


Where, p = predicted value and t = true value.

Graph :

![](https://miro.medium.com/max/800/1*3RVxHIFfoW1DldDVq0wulA.jpeg)


Advantages :

1.  Double Differentiable.
2.  Comparatively less computations required (than Huber).

Disadvantages :

1.  Less adaptive than Huber as it follows a fixed scale (no δ).

### MSE vs Huber vs Log-Cosh :

![](https://miro.medium.com/max/800/1*qtKawhrlhKoKhg7fYxKblw.jpeg)


### Mega comparison of loss functions:

![](https://miro.medium.com/max/800/1*eH-5v54TH2Lmo1hWrjQNjA.jpeg)

Image by author

These are the most common loss functions used for regression. There are other loss functions like quantile loss and Poisson loss, but in my opinion, these should be enough to get started. One can also design and implement their own **custom loss functions** that are specific to their use case. Sometimes, a **combination** of these loss functions is also used.

## Loss functions for classification:

When a neural network is trying to predict a **discrete** value, we can consider it to be a classification model. This could be a network trying to predict what kind of animal is present in an image, or whether an email is spam or not. First let’s look at how the output is represented for a classification neural network.

![](https://miro.medium.com/max/431/1*rFl5a2klSb0879Elf__Iqg.png)

Classification Neural Network Output Format

The number of nodes of the output layer will depend on the number of classes present in the data. Each node will represent a single class. The value of each output node essentially represents the **probability** of that class being the correct class.

Pr(Class 1) = Probability of Class 1 being the correct class

Once we get the probabilities of all the different classes, we will consider the class having the **highest** probability to be the predicted class for that instance. First let’s explore how **binary classification** is done.

### Binary Classification

In binary classification, there will be only one node in the output layer even though we will be predicting between two classes. In order to get the output in a probability format, we need to apply an activation function. Since probability requires a value in between 0 and 1 we will use the **sigmoid function** which can _squish_ any real value to a value between 0 and 1.

![](https://miro.medium.com/max/495/1*5mGgjZYOd6Xtu1cNPE8k6Q.png)

Sigmoid Function Graph Visualization

As the input to the sigmoid becomes larger and tends to plus infinity, the output of the sigmoid will tend to 1. And as the input becomes smaller and tends to negative infinity, the output will tend to 0. Now we are guaranteed to always get a value between 0 and 1, which is exactly how we need it to be since we require probabilities.

If the output is above 0.5 (50% Probability), we will consider it to be falling under the **positive class** and if it is below 0.5 we will consider it to be falling under the **negative class.** For example if we are training a network to classify between cats and dogs, we can assign dogs the positive class and the output value in the dataset for dogs will be **1**, similarly cats will be assigned the negative class and the output value for cats will be **0.**

The loss function we use for binary classification is called **binary cross entropy (BCE)**. This function effectively penalizes the neural network for binary classification task. Let’s look at how this function looks.

![](https://miro.medium.com/max/875/1*7nqhvFpW5-D55z4ejalnjQ.png)

Binary Cross Entropy Loss Graphs

As you can see, there are two separate functions, one for each value of Y. When we need to predict the **positive class** (Y = 1), we will use

Loss = -log(Y_pred)

And when we need to predict the **negative class** (Y = 0), we will use

Loss = -log(1-Y_pred)

As you can see in the graphs. For the first function, when Y_pred is equal to 1, the **Loss is equal to 0**, which makes sense because Y_pred is **exactly the same** as Y. As Y_pred value becomes closer to 0, we can observe the Loss value increasing at a **very high rate** and when Y_pred becomes 0 it tends to infinity. This is because, from a classification perspective, 0 and 1 have to be polar opposites due to the fact that they each represent completely different classes. So when Y_pred is 0 when Y is 1, the loss will have to be very high in order for the network to learn it’s mistakes more effectively.

![](https://miro.medium.com/max/645/1*-bEoqRQKmBye7iqv7PUJBA.png)

Binary Classification Loss Comparisons

We can mathematically represent the entire loss function into one equation as follows:

![](https://miro.medium.com/max/875/1*EJPT0utTkQ2qrHfjDID5RA.png)

Binary Cross Entropy Full Equation

This loss function is also called as **Log Loss.** This is how the loss function is designed for a binary classification neural network. Now let’s move on to see how the loss is defined for a multiclass classification network.

### Multiclass Classification

Multiclass classification is appropriate when we need our model to predict **one** possible class output every time. Now since we are still dealing with probabilities it might make sense to just apply sigmoid to all the output nodes so that we get values between 0–1 for all the outputs, but there is an issue with this. When we are considering probabilities for multiple classes, we need to ensure that the **sum** of all the individual probabilities is **equal to one**, since that is how probability is defined. Applying sigmoid does not ensure that the sum is always equal to one, hence we need to use another activation function.

The activation function we use in this case is **softmax.** This function ensures that all the output nodes have values between 0–1 and the **sum of all** output node values **equals to 1 always**. The formula for softmax is as follows:

![](https://miro.medium.com/max/875/1*T6ZFOuQgnaXg914MjQpA1g.png)

Softmax Formula

Let’s visualize this with an example:

![](https://miro.medium.com/max/521/1*17kG7Wk8sX4K514lhk7MTQ.png)

Softmax Example Visualization

So as you can see, we are simply passing all the values into a exponential function. After that, to make sure they are all in the range of 0–1 and to make sure the sum of all the output values equals to 1, we are just dividing each exponential with the sum of all exponentials.

So why do we have to pass each value through an exponential before normalizing them? Why can’t we just normalize the values themselves? This is because the goal of softmax is to make sure **one value is very high** (close to 1) and all **other values are very low** (close to 0). Softmax uses exponential to make sure this happens. And then we are normalizing because we need probabilities.

Now that our outputs are in a proper format, let’s go ahead to look at how we configure the loss function for this. The good thing is that the loss function is essentially the same as that of binary classification. We will just apply **log loss** on each output node with respect to its respective target value and then we will find the sum of this across all output nodes.

![](https://miro.medium.com/max/670/1*g5VvhALGnJJYhSkoYccDxA.png)

Categorical Cross Entropy Visualization

This loss is called as **Categorical Cross Entropy.** Now let’s move onto a special case of classification called multilabel classification.

### Multilabel Classification

Multilabel classification is done when your model needs to predict **multiple classes** as the output. For example, let’s say you are training a neural network to predict the ingredients present in a picture of some food. There will be multiple ingredients we need to predict so there will be **multiple 1’s** in Y.

For this we can’t use softmax because softmax will always force only one class to become 1 and other classes to become 0. So instead we can simply keep sigmoid on all the output node values since we are trying to predict each class’s **individual probability**.

As for the loss we can directly use log loss on each node and sum it, similar to what we did in multiclass classification.