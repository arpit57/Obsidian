# Why Pre-Process Data

> Garbage In, Garbage Out.

Datasets are very rarely found in perfect condition. More often than not, your data will contain missing values, non-numerical data, and noise. Sometimes, your data isn’t enough, and you have to rely on other datasets to enrich the information you have. As data scientists, it’s our job to make sure that our data is clean, complete, and can be used to extract as much information as possible.

# Different Data Types

## Nominal

Nominal data is data that can be divided into groups, rather than being represented in a numerical format. Examples of nominal data are gender, age group, or race. It’s important to note that there’s no specific order in which these groups are arranged. Take a person’s gender, for example. Nothing distinguishes a male from a female, and vice versa.

One way to deal with categorical data is `label-encoding`. Label-encoding assigns a number value to each group. Consider the following dataset which gives us information about a customer:

![](https://miro.medium.com/v2/resize:fit:633/1*uH1NHI_eX8K07ji1GsBc7Q.png)

**Table 1:** Customer Data

In this dataset, `country` is a nominal variable, with possible values existing in the set `{France, Canada, Germany}`. Label-encoding would mean that we assign each value in the set of countries a number value, such as 1,2, and 3, respectively. We obtain:

![](https://miro.medium.com/v2/resize:fit:634/1*O7p01HMCxyS_p3R3oRINjA.png)

**Table 2:** Customer Data After Applying Label-Encoding

A major issue with label-encoding is that it introduces the notion of order to our otherwise non-ordered attribute. With Germany given a value of three, and France given a value of one, there’s now a difference of two between the two countries, implying that one is greater than the other and adding a larger weight to the latter.

A better way of dealing with nominal data is by `one-hot encoding`. With one-hot encoding, a new column is created for each individual group. The column that satisfies a particular entry will have a value of one, while the rest will have a value of zero. Let us one-hot encode our original customer data:

![](https://miro.medium.com/v2/resize:fit:875/1*egkCiacbHKQ1qv-JA0TIyw.png)

**Table 3:** Customer Data After Applying One-Hot Encoding

This technique is most widely used when dealing with nominal data. One-hot encoding, however, can become inefficient when the nominal attribute has very high cardinality (a large number of groups implies a large increase in columns)

## Ordinal

Ordinal data, unlike nominal data, is ordered. Take `education level`, for example. There is a logical ordering between a high school diploma, bachelor’s degree, and a master’s degree.

A first step to dealing with ordinal data is using the aforementioned label-encoding technique. But that’s not enough. As we’ll see in the section on numerical data, it’s important that we then **scale the feature**, so that it doesn’t hold significantly more weight than other data. More on this later.

Let’s label-encode the education level column of our customer data by replacing {ES, HS, BS, MS} with {1, 2, 3, 4}, respectively.

![](https://miro.medium.com/v2/resize:fit:875/1*RQx-6z4k3Yiw6D7Blrqq2Q.png)

**Table 4:** Customer Data After Applying Label-Encoding To The Education Level Column

## Symmetric and Asymmetric Binary

Binary data is data that consists of only two possible values. In our customer data example, gender is binary, since the only possible values are `Male` and `Fermale`. We normally replace binary data with ones and zeroes.

The difference between symmetric and asymmetric binary data is the importance of one value over the other. For example, neither the male nor female group holds more importance than the other. As such, this attribute is symmetric and it doesn’t matter which value is assigned one, and which is assigned zero. Let’s update our customer data to reflect this:

![](https://miro.medium.com/v2/resize:fit:875/1*BLzIpvx5GsSSzbVm5ToQFg.png)

**Table 5:** Customer Data After Dealing With Binary Attributes

On the other hand, when classifying a patient as having tested positive or negative for COVID-19, we tend to care more about the positive cases. In this scenario, a positive case holds more importance, making this attribute asymmetric. We normally assign the more important value a one, and the other a zero.

## Numerical

Numerical data is measurable and is represented in number form. Data in this format is extremely useful and enhances our model’s accuracy greatly. `Age` is an example of a numerical attribute in our customer data.

When dealing with numerical data, it’s important that we understand the concept of **feature scaling**. Consider the `age`and `education level`columns in our customer data. Assume now, that the largest possible value for a person's age is 130. With 4 being the maximum value for education level, age will hold greater weight when used in our models. This, however, doesn’t reflect the real-world scenario where, in reality, a person’s age doesn’t hold more value than his education level. We deal with this issue by ensuring that all numerical data is represented by an equal scale. There are two different approaches to doing this:

1. **Standardizing**: Rescales the values to have a mean of 0 and a standard deviation of 1

![](https://miro.medium.com/v2/resize:fit:458/1*uQTfi-oOhyt3x5zw01dU2A.png)

2. **Normalizing**: Rescales the values into a range of [0,1]

![](https://miro.medium.com/v2/resize:fit:445/1*uqLybmAH9GU7XqbAs7ZRQg.png)

Standardizing is the technique most widely used, and it’s the one we will use to scale our numerical data.

![](https://miro.medium.com/v2/resize:fit:875/1*Lp2nbgsraatK2hENCNxobA.png)

**Table 6:** Customer Data After Standardizing

There are two important points to make here. One, the age and education level columns are now on the same scale, and we can use them in our models without one wrongfully outweighing the other. Two, we didn’t scale our binary data. That’s because all binary attributes are already in the range [0,1], and so standardizing would actually harm your dataset.

- **Normalize** when the algorithm requires features on the same scale but does not make any assumptions about the distribution of your data (e.g., Neural Networks).
- **Standardize** when the algorithm makes some statistical assumptions about your data, or when you want to suppress the effects of different units (e.g., SVM, PCA).

# Dealing With Missing Values

Finally, dealing with missing data. How you decide to do this depends on your situation. Let’s look at a few options:

1. **Removing the entry with missing values**: This is a good solution when the number of entries with missing values, compared to the total number of entries you have, is minimal. For example, if you have 100000 customer entries in your customer data, but one customer’s age is missing, removing this customer wouldn’t be too big of an issue.
2. **Manually inserting the value:** Assume now, that you have this customer’s phone number. You then have the option of calling them and asking for their age. This would imply that you manually enter the missing value, and is a plausible solution when you can find the information yourself.
3. **Replacing it with the mean or average:** This is another option, but, could introduce some bias in your dataset.
4. **Predicting the value:** A slightly more complicated option, but you could use some machine learning algorithms (e.g. regression) to predict the missing value based on your current data

# Feature Engineering

Feature engineering is the process of selecting and transforming variables when creating a predictive model using machine learning or statistical modeling.

#### **1. Feature Selection**

- **What**: Choosing the most important features that are relevant to the task.
- **Why**: By selecting the most informative features, you can improve model performance and reduce overfitting.
- **How**: Techniques might include mutual information, correlation with the target variable, or using model-based approaches like L1 regularization.

#### **2. Feature Extraction**

- **What**: Transforming high-dimensional data into a lower-dimensional form.
- **Why**: Helps in reducing the dimensionality, making the model easier to understand, and can lead to better performance.
- **How**: Techniques include Principal Component Analysis (PCA), Linear Discriminant Analysis (LDA), and t-SNE.

#### **3. Feature Creation 

- **What**: Creating new features from existing ones.
- **Why**: Can help the model to capture underlying patterns in the data.
- **How**: Techniques include polynomial features, interaction terms, and domain-specific calculations.


# Code

``` python
from sklearn.preprocessing import LabelEncoder

labelencoder = LabelEncoder()
data['Region'] = labelencoder.fit_transform(data['Region'])
```

``` python
from sklearn.preprocessing import OneHotEncoder

onehotencoder = OneHotEncoder()
onehot_encoded = onehotencoder.fit_transform(data[['Product']]).toarray()
```


```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
data['Quantity'] = scaler.fit_transform(data[['Quantity']])
```

```python
from sklearn.preprocessing import StandardScaler

standardizer = StandardScaler()
data['Quantity'] = standardizer.fit_transform(data[['Quantity']])
```

```python
from sklearn.impute import SimpleImputer

imputer = SimpleImputer(strategy="mean")
data['Quantity'] = imputer.fit_transform(data[['Quantity']])
```
