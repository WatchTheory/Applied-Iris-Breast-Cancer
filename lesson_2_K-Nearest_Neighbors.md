
# LESSON 02: K-Nearest Neighbors

Lesson Overview
In this lesson, we will explore K-Nearest Neighbors (KNN), a simple yet effective machine learning algorithm. You will learn the theory behind KNN, its applications, and how to implement it. By the end of this lesson, you’ll have a solid understanding of how KNN works, how to fine-tune it, and how to evaluate its performance.



## Introduction to KNN

A Classification Problem

- Imagine you have some data.
Each point consists of features (temperature, humidity) and a response (rain/no rain)

- A new point apprears 
We know the value of its two features(humidity, temperature) **but we don't know its label**( i.e whether that point represents a day when it rained or not)

How will you devide which label to give this point(rain/no rain) using only the information on this chart

- Now our new point is equidistant from a rainy day
How should we make our classification now?

- Instead of loooking at the **one** cloeset point, we might look at the **three** cloest points to our new point
This would give us more acculated classifciation

### Understanding K-Nearest Neighbors

K-Nearest Neighbors (KNN) is a simple, intuitive, and powerful algorithm used for both classification and regression tasks. It belongs to the category of supervised learning algorithms, meaning it requires labeled data to train. KNN is also known as a lazy learner since it doesn’t actually "train" a model, but instead stores the entire training dataset and makes predictions based on the similarity of new inputs to this stored data.

🗒️ Key Point: KNN makes predictions based on the K closest data points in the training set.

### Theoretical Concepts Behind KNN

**What is KNN?**
KNN operates on the principle that similar data points are likely to have similar outcomes. It classifies or predicts a value for a new point by:

1.Looking at the K nearest neighbors.
2.For classification, it assigns the most common class among these neighbors.
3.For regression, it calculates the average value of the neighbors.

**The Role of "K" in KNN**
The parameter K is critical in KNN:

- K = 1 means we look at just the nearest neighbor, which can make the algorithm sensitive to noise in the data.
- A larger K results in a smoother decision boundary, but if K is too large, the algorithm may become too generalized.

 Tip: The optimal value for K is often determined through techniques like splitting the data into training and testing sets. You want to balance noise sensitivity with generalization!

** Distance Metrics in KNN**
KNN relies heavily on distance metrics to find the "nearest" neighbors. Here are the most commonly used metrics:
- Euclidean Distance (most common, and the default) 

$$
d(p, q) = \sqrt{\sum_{i=1}^n (p_i - q_i)^2}
$$

- Manhattan Distance 
$$
d(p, q) = \sum_{i=1}^n |p_i - q_i|
$$


- Minkowski Distance (generalized form)

$$
d(p, q) = \left( \sum_{i=1}^n |p_i - q_i|^p \right)^{1/p}
$$

&nbsp;

⚠️ Important: Always scale your features before applying KNN, as features with larger ranges will dominate the distance calculations. We’ll discuss how to do this when we create our own KNN model later!

###  Voting Mechanism in KNN

In classification tasks, each of the K neighbors gets a "vote," and the class with the most votes wins. KNN uses two types of voting:

1. Majority Voting: Each neighbor has equal weight.
2. Weighted Voting: Closer neighbors have more influence.

## Steps in the KNN Algorithm

1. Choose the value of K.
2. Calculate the distance between the new data point and all the training data points.
3. Sort the distances and select the K nearest neighbors.
4. For classification, the majority class label is assigned. For regression, the average target value is used.
5. Return the prediction for the new data point

&nbsp;

1. **Choose the Value of K**:Select the number of nearest neighbors (K) that you want to consider for making predictions. In this case, K could be any value, such as 3 or 5, depending on the problem at hand. In the image above, we can see that the 5 closest neighbors were selected.
2. **Calculate Distance**:For each new data point (orange in the image), calculate the distance between this point and all other points in the dataset using a distance metric (such as Euclidean distance). The shorter the distance, the more similar the points are.
3. **Find the K Nearest Neighbors**:Sort the distances and select the K nearest neighbors (those closest to the new data point). In the image, the nearest points are circled. These neighbors could belong to **Category A** or **Category B**.
4. **Voting for Classification**:If the task is classification, each neighbor "votes" for its class. The new data point is assigned to the class with the most votes. In the image, you would count how many points around the new data point belong to Category A or Category B.
5.**Make a Prediction**:Based on the majority vote, assign the new data point to the predicted class. In this example, if more neighbors belong to **Category A**, the new point (orange) would be classified as Category A.

##  Advantages and Disadvantages of KNN

✅ Advantages:
- **Simplicity**: Very easy to understand and implement.
- **No Training Phase**: KNN is a lazy learner, which means no explicit training process is required.
- **Flexible**: Can be used for both classification and regression tasks.
- **Adaptable**: Can handle complex, non-linear decision boundaries.


❌ Disadvantages:
- **Computationally Expensive**: KNN must compute the distance to all points in the training set at prediction time.
- **Sensitive to Noise**: Especially when K is small.
- **Requires Feature Scaling**: Different feature scales can skew the distance metrics.


## 🎯 Conclusion
In this lesson, we've explored the fundamentals of the **K-Nearest Neighbors (KNN)** algorithm, including its core concepts, how it operates, and when it's most effective. You’ve learned about the importance of choosing the right **K** value, how to use **distance metrics**, and the role of **voting mechanisms** in classification tasks.

KNN is a simple yet powerful algorithm that excels in both classification and regression tasks. Its flexibility makes it a go-to solution for a wide variety of problems. However, as we discussed, it's important to carefully consider its computational costs, sensitivity to noise, and the need for feature scaling