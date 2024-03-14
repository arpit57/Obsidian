Statistical Hypothesis testing is to test the assumption (hypothesis) made and draw the conclusion about the population. This is done by testing the sample representing the whole population and based on the results obtained; the hypothesis is either rejected or accepted.

> **“Hypothesis is an idea that can be tested”**

# **Steps to perform hypothesis testings**

![](https://miro.medium.com/v2/resize:fit:875/1*_f5bSTN6ULE_qQn3sM8QuA.png)

# **Null Hypothesis and Alternative Hypothesis**

The null and alternative hypothesis is represented by Ho and Ha respectively.

> **Hypothesis 0 (Ho):** It is an assumption made about the population which needs to be tested and is considered to be true until evidence is found against it
> 
> **Hypothesis 1 (Ha):** It is the opposite of the assumption made and is accepted when the former is rejected.

Let us understand both of these terms by an experiment of flipping a coin and determine if the coin is biased towards heads or not.

![](https://miro.medium.com/v2/resize:fit:875/1*CdeNESVU-H4EqRkz-cvdmQ.png)

## **The Null and Alternate Hypothesis is:**

**_Ho:_** _The coin is not biased towards the head._

**_Ha:_** _The coin is biased towards the head._

# **Significance level, P-value & Confidence Level**

The significance level is represented by the Greek letter alpha (α).

The common values used for alpha is 0.1%, 1%, 5%and 10%. A smaller alpha value suggests a more robust interpretation of the null hypothesis, such as 1% or 0.1%.

The hypothesis test returns a probability value known as **p-value**. Using this value we can either reject the null hypothesis and accept the alternate hypothesis or accept the null hypothesis.

**_p-value= Probability(Data | Null Hypothesis_)**

**_p-value <= alpha_**: Reject the null and accept the alternate hypothesis

**_p-value > alpha_**: Failed to reject the null hypothesis

_Let us experiment on the above hypothesis by flipping a single coin five times._

![](https://miro.medium.com/v2/resize:fit:875/1*pXz1u1ECRJjM0p_qDA6qWQ.png)

**Experiment Performed:**

After flipping the coin five times, we got five heads in a row (X) = 5

Considering alpha = 0.05

p-value :probability(X=5 |Ho)

![](https://miro.medium.com/v2/resize:fit:875/1*LiUWaFqOvuLE3N3Yu5sElQ.png)

**Result:**

No. of events in possible outcomes with all five heads = 1

So,P(X=5 |Ho) = 1/32 = 0.03

0.03 signifies that there is only a 3% chance of getting **_all five heads in a row which is less than alpha._**

P(X= 5 |Ho) = 0.03 < alpha( 0.05)

As the ground truth observed cannot be rejected, hence **_the null hypothesis(Ho) is rejected, and the alternate hypothesis is accepted._**

**_The confidence level_** can be obtained by subtracting the significance level of the hypothesis from 1 of the given observed sample data.

**Confidence level = 1 — significance level (α)**

![](https://miro.medium.com/v2/resize:fit:875/1*jPjadpy3PiDNMUTmH0XM-A.png)

# **Two-Tailed Hypothesis Testing**

The two-tailed hypothesis would be independent of the direction because the effect is tested in both directions. The significance level is split into two halves between both tails of the distribution. So, it will reject the test score if is too large or too small.

**_Let’s understand this with an assumption “Average height of women in India is 5.4 inches ”._** _Let the significance value be 0.05, the sample size is 50, and a standard deviation of 0.2 inches_

**_Ho : Mean height(μ) = 5.4 inches_**

**_Ha: Mean height(μ) ≠ 5.4 inches_**

![](https://miro.medium.com/v2/resize:fit:875/1*F5Vjqla18RCXrialcwUy3Q.png)

# **One-Tailed Hypothesis Testing**

One-tailed hypothesis tests are also known as directional and one-sided tests because you can test for effects in only one direction. When you perform a one-tailed test, the entire significance level percentage goes into the end of any one tail of the distribution.

One-Tailed Hypothesis into two distributions:

1. Left-tailed Distribution

**2.** Right-tailed Distribution

## **Left-t**ailed Distribution

If the assumption is “**_Average height of women in India is less than 5.4 inches ”_**

**_Ho : Mean height(μ) = 5.4 inches_**

**_Ha : Mean height(μ) < 5.4 inches_**

![](https://miro.medium.com/v2/resize:fit:875/1*DF7hpmV1XzraC4QHKB8nLw.png)

## Right-tailed Distribution

If the assumption is **_“Average height of women in India is greater than 5.4 inches”_**

**_Ho : Mean height(μ) = 5.4 inches_**

**_Ha : Mean height(μ) > 5.4 inches_**

![](https://miro.medium.com/v2/resize:fit:875/1*bi6lwH_okp9tzLkmIK3RAQ.png)

# Type 1 and 2 errors

In the context of hypothesis testing, a Type 1 error occurs when you incorrectly reject a true null hypothesis, while a Type 2 error happens when you fail to reject a false null hypothesis.

### Why:

- **Type 1 Error**: This is essentially a "false positive." You're saying something is true when it actually isn't. In medical testing, it's like saying a healthy person has a disease.
- **Type 2 Error**: This is a "false negative." You're saying something is not true when it actually is. In the medical analogy, it's like saying a sick person is healthy.

### How:

- **Type 1 Error**: Occurs when the p-value is less than the chosen significance level (alpha), leading you to reject the null hypothesis even though it is true.
- **Type 2 Error**: Occurs when the p-value is greater than alpha, leading you to fail to reject the null hypothesis even though it is false.

### When:

- **Type 1 Error**: Generally occurs when you are being "too strict" with your acceptance criteria.
- **Type 2 Error**: Usually happens when your test lacks the power to detect the effect, often because the sample size is too small.

# tests for calculating p values

Commonly used statistical tests for calculating p-values encompass a variety of scenarios, ranging from comparing means to analyzing categorical data. Here's a quick rundown:

### Tests for Comparing Means

1. **T-Test**: Used for comparing the means between two groups.
    - One-sample T-Test
    - Independent samples T-Test
    - Paired sample T-Test
2. **ANOVA (Analysis of Variance)**: Used when you have more than two groups to compare.
    - One-way ANOVA
    - Two-way ANOVA
3. **MANOVA (Multivariate Analysis of Variance)**: Similar to ANOVA but for multiple dependent variables.

### Tests for Categorical Data

1. **Chi-Square Test**: Used to test relationships between categorical variables.
    - Chi-Square Test for Independence
    - Chi-Square Goodness-of-Fit Test
2. **Fisher's Exact Test**: Used for small sample sizes where the Chi-Square test is inappropriate.

### Non-parametric Tests

1. **Wilcoxon Rank-Sum Test / Mann-Whitney U Test**: Non-parametric alternative to the T-Test for independent samples.
2. **Wilcoxon Signed-Rank Test**: Non-parametric alternative to the paired T-Test.
3. **Kruskal-Wallis Test**: Non-parametric alternative to ANOVA for more than two groups.

### Regression Analysis

1. **Linear Regression**: Generates a p-value for each coefficient to test if it's significantly different from zero.
2. **Logistic Regression**: Same as linear regression but used for binary dependent variables.

### Correlation Analysis

1. **Pearson Correlation Coefficient**: Tests if two continuous variables are linearly correlated.
2. **Spearman Rank Correlation**: Non-parametric test to measure the strength and direction of the relationship between two variables.

### Other Tests

1. **Binomial Test**: Used for testing proportions in binomial distribution.
2. **Poisson Test**: Used when modeling events that happen at a constant rate over time.
