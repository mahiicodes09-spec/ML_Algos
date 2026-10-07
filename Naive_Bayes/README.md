Naive Bayes Algo:-

1. What is Naive Bayes?

Naive Bayes is a supervised machine learning algorithm mainly used for classification problems.

It is based on Bayes' Theorem and conditional probability.

The main idea is to calculate the probability of each class and choose the class with the highest probability.

2. Bayes' Theorem

Naive Bayes is based on Bayes' Theorem:

P(A|B) = P(B|A) × P(A) / P(B)

In simple words, Bayes' theorem helps us find the probability of an event when some additional information is already known.

3. Conditional Probability

Conditional probability means finding the probability of an event when we already know that another event has happened.

For example, P(Sunny | No) means the probability of Sunny weather when we know that tennis was not played.

4. Why is it called "Naive"?

Naive Bayes makes a simple assumption that the features are independent of each other.

For example, in the Play Tennis dataset, the features are Outlook, Temperature, Humidity and Wind.

The algorithm treats these features independently while calculating probabilities.

This assumption may not always be true in real-world data, but Naive Bayes can still work well for many classification problems.

5. Dataset

For this project, the Play Tennis dataset is used.

The dataset contains weather conditions and information about whether tennis was played.

Input features:

-- Outlook
-- Temperature
-- Humidity
-- Wind

Target variable:

-- PlayTennis

The target has two values: Yes and No.

Therefore, this is a binary classification problem.

6. How Naive Bayes Works:

Suppose we get a new record with some weather conditions.

The model calculates the probability of the possible classes, such as:

PlayTennis = Yes

PlayTennis = No

It then compares these probabilities.

The class with the higher probability is selected as the final prediction.

In simple words:

Input features → Calculate probabilities → Compare classes → Make prediction

7. Implementation:

The main steps followed in the project are:

1. Load the dataset.
2. Separate the input features and target variable.
3. Convert categorical data into numerical form.
4. Split the data into training and testing sets.
5. Train the Naive Bayes model.
6. Make predictions.
7. Evaluate the model using accuracy, confusion matrix and classification report.

For this categorical dataset, CategoricalNB from Scikit-learn is used.

8. Advantages:

a. Simple and easy to understand.
b. Fast to train and predict.
c. Works well with small datasets.
d. Useful for classification problems.
e. Commonly used in spam detection, sentiment analysis and text classification.

9. Disadvantages

a. Assumes that features are independent of each other.
b. This assumption may not always be true in real-world datasets.
c. Performance depends on the quality and type of data.

10. Conclusion

Naive Bayes is a simple and fast classification algorithm based on Bayes' Theorem and conditional probability.

It calculates the probability of each class and selects the class with the highest probability.

In this project, the Play Tennis dataset is used to understand and implement Naive Bayes using Scikit-learn.
