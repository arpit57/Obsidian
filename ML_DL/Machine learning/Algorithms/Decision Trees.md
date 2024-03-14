# Bagging vs Boosting

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
