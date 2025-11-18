
# 📚 03. Applied Lesson - Iris & Breast Cancer Datasets


##  Applying KNN with the Iris Dataset

Now that we've covered the theory behind K-Nearest Neighbors (KNN), it’s time to put our skills into practice. In this section, we’ll use the Iris dataset, one of the most famous datasets in machine learning, to build a KNN classifier. This dataset contains measurements of different flower species and is a great starting point for classification tasks.

**The Iris Dataset Overview**

The Iris dataset consists of 150 samples from three species of Iris flowers: setosa, versicolor, and virginica. Each sample has four features:

1.Sepal length (cm)
2.Sepal width (cm)
3.Petal length (cm)
4.Petal width (cm)

The goal of this task is to classify the species of each Iris flower based on these four features.


### The Importance of Feature Scaling: Standard Scaler
Before diving into the K-Nearest Neighbors (KNN) implementation, it’s important to talk about **feature scaling**. KNN relies heavily on distance calculations (e.g., Euclidean distance), which means that the scale of the features can significantly impact the model’s performance. If your dataset has features that vary widely in scale, the larger values may dominate the distance calculations, leading to biased results


for example:
- **Petal length** might be measured in centimeters (ranging from 1 to 7), while **sepal width** might have a much smaller range (e.g., 0.1 to 2).
- Without scaling, features with larger numerical ranges will disproportionately affect the distance calculations in KNN.


To solve this issue, we use **feature scaling** methods like the **Standard Scaler.**

## What is Standard Scaler?

The **Standard Scaler** is a popular method in data preprocessing that standardizes the features by removing the mean and scaling to unit variance. It transforms the features in such a way that they follow a standard normal distribution, i.e., with a mean of 0 and a standard deviation of 1.


The formula for standard scaling 
$$
Z = \frac{X - \mu}{\sigma}
$$
- X is the original features value
- u is the mean of the features
- thea is the standard diviation of the feature

After applying the standard scaler, all features will have a similar scale, making the distance calculation in KNN more balanced.

####  When to Use Standard Scaler
The Standard Scaler is typically used when:
- Your data contains features with different units or scales.
- Algorithms like KNN (which are distance-based) are being used.
- You want to ensure that each feature contributes equally to the distance metric.


## Key Parameters in KNN
When building a K-Nearest Neighbors (KNN) model, there are several key parameters that control how the algorithm behaves. Understanding these parameters will help you fine-tune your model for better performance. Let's walk through the most important ones and how they affect the KNN classifier.

1. N Neighors (K)
- **Definition**: The number of neighbors to consider for classification or regression.
- **Default value** : 5 
- **Description** : This parameter defines how many neighbors (K) the algorithm should look at when making a prediction. Choosing the right value for K is crucial
    - A smaller K (e.g., K=1) may lead to a more flexible model that can fit very specific patterns but risks overfitting.
    - A larger K results in smoother decision boundaries, but it may underfit by ignoring important details in the data.
- Example: Setting K=3 means that the algorithm will look at the three nearest neighbors when making a prediction.
```python
knn = KNeighborsClassifier(n_neighbors=3)
```

2. Weights
- **Defintions** :
- **Default value**:
- **Options**:
    - ```uniform``` : All neighbors have equal weight.
    - ```distance```: Closer neighbors are weighted more heavily than those further away.
- **Description**: When using weights='distance', closer neighbors have more influence on the prediction, which can improve performance, especially in noisy datasets.
- **Example**: Giving more weight to closer neighbors:
```python
knn = KNeighborsClassifier(n_neighbors=5, weights='distance')
```