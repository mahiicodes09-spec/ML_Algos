# Decision Tree Regressor

## 1. What is Decision Tree Regression?

-   A Decision Tree Regressor predicts a numerical value.
-   Example: predicting house prices, marks, or salary.
-   It splits data into smaller groups by asking questions about
    features.

## 2. How Does It Work?

-   **Root node:** the first question or split.
-   **Branches:** the possible outcomes of a question.
-   **Leaf node:** the final prediction.
-   The model follows questions from the root to a leaf to make a
    prediction.
-   For squared-error-based regression, a leaf usually predicts the
    **mean** of the target values in that leaf.

## 3. How Is the Best Split Chosen?

-   The model checks possible splits and measures the error in the
    resulting groups.
-   It chooses a split that reduces the error the most.
-   A common criterion is **Mean Squared Error (MSE)**.

## 4. Mean Squared Error (MSE)

-   MSE is the average of the squared differences between actual and
    predicted values.
-   Formula: MSE = average of (actual value − predicted value)².
-   Lower MSE means predictions are closer to actual values.

## 5. Weighted MSE

-   After a split, the model combines the errors of both child groups.
-   Each group's MSE is weighted by the number of samples it contains.
-   The preferred split generally has the lowest weighted MSE.

## 6. Training and Prediction

-   Separate the dataset into **X (features)** and **y (target)**.
-   Split the data into training and testing sets.
-   Train the model using the training data.
-   Predict target values for the test data and compare them with actual
    values.

## 7. Evaluation Metrics

-   **MAE:** average absolute prediction error.
-   **MSE:** average squared prediction error; larger errors are
    penalised more.
-   **R² score:** shows how well the model explains variation in the
    target; closer to 1 is generally better.

## 8. Overfitting and Underfitting

-   **Overfitting:** the tree learns the training data too closely and
    performs poorly on unseen data.
-   **Underfitting:** the tree is too simple to learn the patterns
    properly.
-   Compare training and testing performance to help identify these
    issues.

## 9. Controlling Tree Complexity

-   **max_depth:** limits how deep the tree can grow.
-   **min_samples_split:** sets the minimum samples needed to split a
    node.
-   **min_samples_leaf:** sets the minimum samples allowed in a leaf.
-   **Pre-pruning:** limits the tree while it is growing.
-   **Post-pruning:** grows the tree first, then removes unnecessary
    branches.
-   Too much pruning can cause underfitting.

## 10. Key Takeaway

A Decision Tree Regressor predicts numbers by splitting data into
groups. It selects useful splits by reducing prediction error, often
using MSE. Limiting the tree's complexity helps it perform better on new
data.
