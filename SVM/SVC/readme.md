# SVM (Support Vector Machine) Classifier

## 1. Overview

* Support Vector Machine (SVM) is a **supervised machine learning algorithm** used for classification and regression.
* In this project, SVM is used to classify whether a person purchases a product based on their **Age** and **Estimated Salary**.

## 2. How SVM Works

* SVM finds the best decision boundary, called a **hyperplane**, to separate different classes.
* It tries to maximize the margin, which is the distance between the decision boundary and the nearest data points from each class.
* The nearest points are called **Support Vectors**. They help determine the position of the boundary.
* A larger margin generally helps the model generalize better to unseen data.

## 3. Mathematical Intuition

* The decision boundary can be represented as: **w · x + b = 0**
* `w` represents the weights, `x` represents the input features, and `b` is the bias.
* SVM aims to maximize the margin, which is proportional to **2 / ||w||** for a linear SVM with the standard margin constraints.
* For data that is not perfectly separable, SVM can allow some classification errors using a **soft margin**, controlled by the parameter `C`.

## 4. Kernel Trick

* When a straight-line boundary cannot separate the classes effectively, SVM can use kernels to create nonlinear decision boundaries.
* Common kernels include:

  * **Linear:** For linearly separable patterns.
  * **Polynomial:** For curved relationships.
  * **RBF:** For more complex nonlinear patterns.
* This project uses the **RBF kernel**.

## 5. Implementation Workflow

* Load and inspect the dataset.
* Separate input features (`X`) and target (`y`).
* Split the data into training and testing sets.
* Apply `StandardScaler` because SVM is sensitive to feature scales.
* Train the model using `SVC`.
* Predict the test-set classes.
* Evaluate using accuracy, confusion matrix, precision, recall, and F1-score.

## 6. Evaluation

* **Accuracy:** Proportion of correct predictions.
* **Confusion Matrix:** Shows correct and incorrect predictions for each class.
* **Precision:** How many predicted positive cases were actually positive.
* **Recall:** How many actual positive cases were identified.
* **F1-score:** Harmonic mean of precision and recall.

## 7. Advantages of SVM

* **Effective in high-dimensional data:** Works well when there are many input features.
* **Good generalization:** Maximizing the margin can help the model perform well on unseen data.
* **Works with nonlinear data:** Kernels such as RBF can create nonlinear decision boundaries.
* **Memory efficient:** Uses support vectors to define the decision boundary rather than relying on every training point directly.
* **Regularization:** The `C` parameter controls the trade-off between margin width and classification errors.

## 8. Disadvantages of SVM

* **Slow on large datasets:** Training can become computationally expensive as the dataset grows.
* **Sensitive to feature scaling:** Features should generally be standardized before training.
* **Parameter tuning required:** Choosing the right kernel, `C`, and `gamma` can be challenging.
* **Less interpretable:** Nonlinear SVM models can be difficult to explain compared with simple decision trees.
* **Performance depends on the data:** SVM may not perform well when classes overlap heavily or the dataset contains substantial noise.