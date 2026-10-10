# Decision Tree Classifier

## What is Classification?

Classification is a machine learning task in which we predict a category or class for a given input. For example, predicting whether a student will pass or fail, whether an email is spam or not spam, or classifying wine quality into different classes.

## What is a Decision Tree Classifier?

A Decision Tree Classifier is a supervised machine learning algorithm that makes predictions by asking a series of questions about the input features. It looks like a tree, where each question splits the data into smaller groups.

For example, to predict whether a student will pass or fail, the tree may check their attendance and marks. Based on the answers, it follows a path until it reaches a final decision.

## Main Parts of a Decision Tree

* **Root Node:** The first node of the tree, where the first split takes place.
* **Decision or Internal Node:** A node that checks a condition and splits the data further.
* **Branch:** The path followed based on the result of a condition.
* **Leaf Node:** The final node that gives the predicted class.

## How Does the Algorithm Work?

The algorithm starts with the training data and looks for a feature that can separate the classes effectively. It creates a split using that feature and repeats the process on the resulting groups.

For example, in a wine quality dataset, the tree may use alcohol content or acidity to divide the samples. It keeps splitting the data until a stopping condition is reached.

When a new sample is given, it follows the conditions from the root node to a leaf node. The class at that leaf becomes the prediction.

## How Does the Tree Choose the Best Split?

The tree needs a way to measure how well a split separates the classes. Two common measures are Gini Impurity and Entropy.

### 1. Gini Impurity

Gini Impurity measures how mixed the classes are in a node. A lower Gini value means the node contains fewer mixed classes. A value of zero means all samples in that node belong to the same class.

### 2. Entropy

Entropy measures the uncertainty or disorder in a node. If the classes are mixed, entropy is higher. If all samples belong to one class, entropy is zero.

### 3. Information Gain

Information Gain measures how much entropy decreases after a split. The tree prefers splits that reduce uncertainty more.

For both Gini and Entropy, the tree compares possible splits and chooses one that creates better-separated groups. The exact split depends on the selected criterion.

## Numeric and Categorical Features

A tree can split numeric features using conditions such as “alcohol content is less than or equal to a certain value.” Categorical features can be handled using suitable encoding or preprocessing when required.

The algorithm learns these conditions from the training data instead of requiring us to write all the rules manually.

## Overfitting and Underfitting

A very deep tree can learn unnecessary details or noise from the training data. It may achieve high training accuracy but perform poorly on unseen data. This is called **overfitting**.

A tree that is too simple may fail to learn important patterns and perform poorly on both training and test data. This is called **underfitting**.

## Pruning and Hyperparameters

Pruning helps control the complexity of a tree by limiting its growth or removing unnecessary branches.

* **Pre-pruning:** Stops the tree from growing too much while it is being built.
* **Post-pruning:** Grows a larger tree first and then removes branches that do not help enough.

Some useful hyperparameters are:

* `max_depth`: Sets the maximum depth of the tree.
* `min_samples_split`: Sets the minimum number of samples required to split a node.
* `min_samples_leaf`: Sets the minimum number of samples required in a leaf.
* `criterion`: Selects the measure used to evaluate splits, such as Gini Impurity or Entropy in classification.

These settings help balance model complexity and performance. Pruning may reduce overfitting, but too much pruning can cause underfitting.

## Model Training and Evaluation

The dataset is divided into input features (X) and the target class (y). It is then split into training and testing sets. The classifier learns from the training data and predicts classes for the test data.

Common evaluation metrics include:

* **Accuracy:** The proportion of predictions that are correct.
* **Precision:** Out of the samples predicted as a particular class, how many actually belong to that class.
* **Recall:** Out of the actual samples of a class, how many the model correctly identifies.
* **F1-score:** The balance between precision and recall.
* **Confusion Matrix:** Shows correct and incorrect predictions for each class.

Accuracy alone may not be enough when the dataset has class imbalance, so precision, recall, and F1-score can also be useful.

## Conclusion

A Decision Tree Classifier is easy to understand because its decisions can be followed as a series of rules. It works by repeatedly splitting the data based on features and selecting splits that improve class separation.

Gini Impurity, Entropy, and Information Gain help the tree choose useful splits, while pruning and hyperparameters control its complexity. Evaluating the model on unseen data helps check whether it can make reliable predictions.
