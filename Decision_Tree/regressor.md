Decision Tree Regression

1. What is Decision Tree Regression?

Decision Tree Regression is a supervised machine learning algorithm used to predict continuous numerical values, such as salary, house prices, and temperature.

It splits data into smaller groups using conditions and predicts a value at each leaf node.

2. How Does It Work?

1. Select an input feature.
2. Sort its values and identify possible split points.
3. Calculate the variance reduction for each split.
4. Choose the split with the highest variance reduction.
5. Repeat the process until a stopping condition is reached.
6. Predict the mean target value of the final leaf node.

3. Variance and Mean Squared Error (MSE)

Variance measures how much the target values differ from their mean.

$$
V(R)=\frac{1}{n}\sum_{i=1}^{n}(y_i-\bar{y})^2
$$

Where:

- (n) = number of observations
- (y_i) = actual target value
- (\bar{y}) = mean of target values

Mean Squared Error (MSE) measures the average squared difference between actual and predicted values.

$$
MSE=\frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2
$$

Where:

- (y_i) = actual value
- (\hat{y}_i) = predicted value

At a leaf node, the prediction is usually the mean of the target values in that leaf.

$$
\hat{y}{leaf}=\frac{1}{n{leaf}}\sum_{i=1}^{n_{leaf}}y_i
$$

4. Variance Reduction

Variance reduction measures how much the weighted variance decreases after splitting a parent node into child nodes.

$$
VR=V(R)-\sum_{i=1}^{k}w_iV(C_i)
$$

Where:

- (V(R)) = variance of the parent node
- (V(C_i)) = variance of child node (i)
- (k) = number of child nodes
- (w_i) = proportion of observations in child node (i)

The weight of each child is calculated as:

$$
w_i=\frac{n_i}{n}
$$

Where:

- (n_i) = number of observations in child node (i)
- (n) = total observations in the parent node

For a binary split:

$$
VR=V(R)-[w_LV(C_L)+w_RV(C_R)]
$$

The split with the highest variance reduction is preferred, because it produces child nodes with lower weighted variance.

5. Overfitting

Overfitting occurs when a decision tree becomes too complex and learns noise from the training data.

An overfitted model performs well on training data but poorly on unseen data.

6. Hyperparameters

Hyperparameters control the growth and complexity of a decision tree.

- "max_depth": Maximum depth of the tree.
- "min_samples_split": Minimum number of samples required to split a node.
- "min_samples_leaf": Minimum number of samples required in a leaf.
- "max_leaf_nodes": Maximum number of leaf nodes.
- "criterion": Function used to measure split quality, such as "squared_error".

7. Pruning

Pruning helps reduce tree complexity by limiting growth or removing unnecessary branches.

- Pre-pruning: Stops the tree from growing too much using hyperparameters.
- Post-pruning: Grows the tree first and then removes unnecessary branches.

Pruning helps reduce overfitting and improve generalization.

8. Hyperparameter Tuning

"GridSearchCV" tests different hyperparameter combinations using cross-validation to find a suitable configuration.

Cross-validation divides the training data into multiple folds. The model is trained and evaluated on different combinations of these folds.

It helps select hyperparameters that generalize better to unseen data.

9. Model Evaluation Metrics

Regression models can be evaluated using the following metrics.

Mean Absolute Error (MAE)

Measures the average absolute difference between actual and predicted values.

$$
MAE=\frac{1}{n}\sum_{i=1}^{n}|y_i-\hat{y}_i|
$$

Mean Squared Error (MSE)

Measures the average squared prediction error.

$$
MSE=\frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2
$$

Root Mean Squared Error (RMSE)

Measures prediction error in the same unit as the target variable.

$$
RMSE=\sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2}
$$

R-squared ((R^2))

Measures how well the model explains variation in the target variable.

$$
R^2=1-\frac{\sum_{i=1}^{n}(y_i-\hat{y}i)^2}{\sum{i=1}^{n}(y_i-\bar{y})^2}
$$

Where:

- (y_i) = actual value
- (\hat{y}_i) = predicted value
- (\bar{y}) = mean of actual target values
- (n) = number of observations

Interpretation:

- Lower MAE, MSE, and RMSE generally indicate better predictions.
- An (R^2) closer to 1 generally indicates a better fit.
- A negative (R^2) means the model performs worse than predicting the target mean on the evaluated dataset.

10. Advantages and Limitations

Advantages

- Easy to understand and visualize.
- Can capture non-linear relationships.
- Requires little data preprocessing.
- Does not require feature scaling.

Limitations

- Can overfit easily.
- Small data changes can produce a different tree.
- A single decision tree may perform worse than ensemble methods on complex datasets.

Key Takeaway

Decision Tree Regression predicts continuous numerical values by splitting data into smaller groups. It selects useful splits based on variance or error reduction and uses hyperparameters, pruning, and cross-validation to control overfitting and improve generalization.