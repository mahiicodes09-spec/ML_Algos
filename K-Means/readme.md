# K-Means Clustering

## 1. K-Means:

K-Means is an **unsupervised machine learning algorithm** used to group similar data points into clusters without requiring predefined labels.

It divides the dataset into K clusters, where each data point belongs to the cluster with the nearest centroid.

For example, K-Means can group customers based on their annual income and spending score to identify different customer segments.

## 2. Mathematical Intuition

K-Means aims to minimize the sum of squared distances between each data point and its assigned cluster centroid.

**Objective Function:**

J = Σᵢ₌₁ᴷ Σₓ∈Cᵢ ‖x − μᵢ‖²

Where:
- **K:** Number of clusters.
- **Cᵢ:** Set of data points belonging to cluster i.
- **x:** A data point.
- **μᵢ:** Centroid (mean) of cluster i.
- **‖x − μᵢ‖²:** Squared Euclidean distance between a data point and its centroid.

The goal is to minimize this objective function so that points within each cluster remain as close as possible to their centroid.

## 3. How K-Means Works

1. **Choose K:** Decide the number of clusters.
2. **Initialize centroids:** Select initial cluster centers.
3. **Assign points:** Assign each data point to its nearest centroid using Euclidean distance.
4. **Update centroids:** Calculate the mean of all points assigned to each cluster.
5. **Repeat:** Reassign points and update centroids until the assignments stabilize or the algorithm reaches its iteration limit.

## 4. Euclidean Distance

K-Means commonly uses Euclidean distance to measure the distance between a data point and a centroid.

**d(x, μ) = √Σⱼ₌₁ᵐ (xⱼ − μⱼ)²**

Where:
- **xⱼ:** Value of feature j for the data point.
- **μⱼ:** Value of feature j for the centroid.
- **m:** Number of features.

The data point is assigned to the cluster whose centroid has the smallest distance.

## 5. Data Preprocessing

1. Load the dataset and inspect its structure.
2. Select relevant numerical features for clustering.
3. Exclude identifiers such as CustomerID because they do not represent meaningful customer characteristics.
4. Apply StandardScaler to standardize features when they have different scales.
5. Fit the K-Means model on the processed features.

Scaling is important because K-Means relies on distances. Features with larger numerical ranges can otherwise dominate the clustering process.

## 6. Choosing K: Elbow Method

The Elbow Method helps estimate a suitable number of clusters.

It works by:
1. Training K-Means with different values of K.
2. Recording the **inertia** for each value.
3. Plotting K against inertia.
4. Selecting a reasonable K near the point where the reduction in inertia begins to slow down significantly.

**Inertia = Σᵢ₌₁ᴷ Σₓ∈Cᵢ ‖x − μᵢ‖²**

Inertia measures the sum of squared distances between data points and their assigned centroids. It generally decreases as K increases, so the elbow provides a useful estimate rather than a guaranteed optimal answer.

## 7. Important Hyperparameters

- **n_clusters:** Number of clusters to form.
- **init:** Method for initializing centroids; `k-means++` is the default and helps spread initial centers apart.
- **n_init:** Number of initializations performed; the best result is retained.
- **max_iter:** Maximum number of iterations for each run.
- **random_state:** Controls randomness to help produce reproducible results.

## 8. Model Evaluation

K-Means does not use ordinary classification accuracy because it is an unsupervised algorithm and generally has no true class labels.

Common evaluation methods include:

- **Inertia:** Measures within-cluster squared distances; lower is generally better for a fixed K comparison, but it always tends to decrease as K increases.
- **Silhouette Score:** Measures how well points fit within their own clusters compared with other clusters. Values range from −1 to +1; higher values generally indicate better-separated clusters.

Cluster plots can also help visualize and interpret the resulting groups.

## 9. Advantages

- Simple and easy to implement.
- Efficient on many small and medium-sized datasets.
- Works well when clusters are compact and reasonably separated.
- Scales well to many practical clustering tasks.

## 10. Disadvantages

- The number of clusters K must be selected beforehand.
- Sensitive to initial centroid positions and outliers.
- Requires numerical features and is affected by feature scaling.
- Can perform poorly with irregularly shaped or overlapping clusters.
- Different initializations may produce different results.

## 11. Conclusion

K-Means is an unsupervised clustering algorithm that groups similar data points by repeatedly assigning them to their nearest centroid and updating the centroids. In this project, feature scaling and the Elbow Method help prepare the data and select a suitable number of clusters, while inertia and silhouette score help evaluate the clustering quality.