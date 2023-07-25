Cross-entropy is a concept that originates from information theory and has been adopted in the field of machine learning as a commonly used loss function, especially for tasks like binary and multi-class classification.

1. **Definition**:

In the context of machine learning, cross-entropy is a measure of the difference between two probability distributions. For classification tasks, these distributions are often the model's predicted probabilities and the true labels. The lower the cross-entropy, the more similar the two distributions are.

For binary classification, cross-entropy can be defined for a single sample as:

scssCopy code

`H(y, p) = -y*log(p) - (1-y)*log(1-p)`

where y is the true label (0 or 1) and p is the predicted probability for the class with label 1.

For multi-class classification, the formula generalizes to:

scssCopy code

`H(y, p) = - Σ y_i*log(p_i)` 

where y_i are the elements of the one-hot encoded true label, and p_i are the elements of the predicted probability distribution.

2. **Applications in Machine Learning**:

Cross-entropy is often used as a loss function in machine learning models, particularly in logistic regression and neural networks. The model's goal during training is to minimize the cross-entropy loss. This means the model is trying to make its predicted probabilities as close as possible to the true labels.

3. **Advantages**:

Cross-entropy is differentiable, making it suitable for gradient-based optimization algorithms. It also puts more emphasis on getting the probabilities of the correct classes right compared to other loss functions like Mean Squared Error (MSE). For example, in the case of a wrong prediction, increasing the probability of the correct class from 0.1 to 0.2 decreases the cross-entropy loss more than increasing it from 0.6 to 0.7, even though the absolute change is the same.

4. **Properties**:

One key property of cross-entropy is that it is always non-negative, and is equal to zero when the predicted distribution matches the true distribution exactly. Also, cross-entropy doesn't require the true labels to be probabilities - they can be any non-negative values, as long as they sum to 1, which is convenient when working with one-hot encoded labels.

5. **Limitations**:

Cross-entropy can lead to numerical instability because it involves the logarithm of predicted probabilities. When these probabilities are very close to 0, the logarithm will be a very large negative number, which can cause issues in the computations. To mitigate this, it's common to add a small constant to the predicted probabilities when computing the logarithm, or to use functions provided by machine learning libraries that have numerical stability built-in.
