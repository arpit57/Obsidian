Overfitting refers to a model that has low bias but high variance. An overfit model is one that fits the training data very well but does not generalize well to new, unseen data. Overfitting occurs when a model is too complex relative to the amount of training data available.

Underfitting refers to a model that has high bias and low variance. An underfit model has not learned the relevant patterns in the training data and therefore has poor accuracy on both training and test data. Underfitting occurs when a model is too simple relative to the complexity of the problem.

So in summary:

- High bias, low variance: Underfitting
- Low bias, high variance: Overfitting
- High bias, high variance: Poorly specified model, neither fits training data nor generalizes
- Low bias, low variance: Goal for a production model
- ![[Slide1.png]]