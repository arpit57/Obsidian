1. **Definition**: A decision tree is a tree-like model of decisions and their possible consequences, including chance event outcomes, resource costs, and utility. It's a flowchart-like structure where each internal node represents a "test" on an attribute, each branch represents the outcome of the test, and each leaf node represents a class label or decision.
    
2. **How it works**:
    
    - Starts with a dataset at the root node.
    - Splits the data into subsets using feature values. These splits are chosen to maximize the homogeneity of the resultant subsets.
    - Continues splitting each subset recursively until stopping criteria are met (e.g., maximum depth reached, minimum node size, no further information gain).
3. **Entropy and Information Gain**:
    
    - Entropy measures the impurity or randomness in the dataset.
    - Information gain measures the reduction in entropy or impurity after a dataset is split on an attribute. Decision trees aim to maximize information gain.
4. **Gini Impurity**: An alternative to entropy used for calculating the impurity of a node. A lower Gini impurity indicates a better split.
    
5. **Types of Decision Trees**:
    
    - **Classification Trees**: Output is a class label (e.g., Yes/No).
    - **Regression Trees**: Output is a continuous value.
6. **Pruning**: The process of reducing the size of the tree to prevent overfitting by removing sections of the tree that provide little power in predicting target variables.
    
7. **Advantages**:
    
    - Easy to understand and interpret.
    - Can handle both numerical and categorical data.
    - Non-parametric, meaning they don’t require a particular model structure.
8. **Disadvantages**:
    
    - Prone to overfitting, especially with complex trees.
    - Can be unstable because small variations in data might result in a completely different tree.
    - Biased with imbalanced datasets, tending to favor dominant classes.
9. **Applications**: Used in various areas like finance (credit scoring, risk management), healthcare (diagnosis, patient management), marketing (customer segmentation, prediction of buying behaviors), and more.

# Ensemble Learning

- **Bagging (Bootstrap Aggregating)**: It works by creating multiple versions of a training dataset through random sampling with replacement, training a separate model on each dataset, and then combining the models' predictions. The goal is to reduce variance and avoid overfitting. Random Forest is a well-known example of a bagging ensemble.
    
- **Boosting**: This method builds a sequence of models in a way that each subsequent model attempts to correct the errors of the previous ones. The models are trained in sequence, and each model learns from the mistakes of the prior one, aiming to improve the overall performance. The final prediction is a weighted sum of the predictions from all models. Examples include AdaBoost, Gradient Boosting Machine (GBM), and XGBoost.

- Bagging trains models in parallel, boosting trains sequentially.
- Bagging combines models by averaging/voting, boosting uses weighted average/vote.
- Bagging reduces variance, boosting reduces bias and variance.
- Bagging models are independent, boosting models are dependent.
- Boosting can overfit with too many iterations, bagging is more robust.
- Bagging uses random subsets of data to reduce variance.
- Boosting uses full data with weighting to reduce bias.
- No random sampling of data takes place in boosting.
- The weighting focuses models on harder examples.
- This sequential approach is what allows boosting to incrementally improve its performance with each iteration.

![[Pasted image 20240319165944.png]]


![[Pasted image 20240319170041.png]]


![[Pasted image 20240319170234.png]]

# Random forest

1. **Definition**: Random Forest is an ensemble learning method that constructs a multitude of decision trees at training time and outputs the mode of the classes (classification) or mean prediction (regression) of the individual trees.
    
2. **How it works**:
    
    - Constructs several decision trees during training.
    - For classification tasks, the output class is the one with the majority vote across all trees.
    - For regression tasks, it predicts the average or mean of the outputs from all trees.
3. **Bagging (Bootstrap Aggregating)**: Random Forest uses bagging where each tree is built from a sample drawn with replacement (bootstrap sample) from the training set.
    
4. **Feature Randomness**: When building trees, each time a split is considered, a random subset of features is chosen as candidates from the full set of features. This adds diversity to the model, making it more robust.
    
5. **Advantages**:
    
    - Reduces overfitting: By averaging multiple trees, it balances the decision tree’s tendency to overfit.
    - High accuracy: Generally provides a high level of accuracy in predictions.
    - Handles both categorical and numerical data.
    - Provides indicators of feature importance.
6. **Disadvantages**:
    
    - Complexity: More complex and computationally intensive than a single decision tree.
    - Model size: Can take up a lot of memory and be slow to evaluate.
    - Less interpretable: The ensemble nature makes it harder to interpret than a single decision tree.
7. **Hyperparameters**:
    
    - Number of trees (n_estimators)
    - Maximum depth of trees (max_depth)
    - Minimum samples per leaf (min_samples_leaf)
    - Minimum samples for a split (min_samples_split)
    - Maximum number of features considered for a split (max_features)
8. **Model Evaluation**: Use cross-validation to assess the performance of a Random Forest model. Look at metrics like accuracy, precision, recall, and the confusion matrix for classification tasks, and MSE (Mean Squared Error) or MAE (Mean Absolute Error) for regression.
    
9. **Applications**: Widely used in various fields like banking (for fraud detection), healthcare (for predicting diseases), e-commerce (for predicting customer behavior), and more.

![[Pasted image 20240319173420.png]]
