# K- Means Clustering

## What is K-means Clustering?
**K-means** is an **unsupervised machine learning algorithm** used to partition data into `k` distinct clusters based on feature similarity. It assigns **data points to the nearest centroid**, then recalculates centroids iteratively until convergence. The algorithm aims to minimize the within-cluster variance (sum of squared distances between points and their centroids). For example online store uses K-Means to group customers based on purchase frequency and spending creating segments like Budget Shoppers, Frequent Buyers and Big Spenders for personalised marketing.

## How does the K-means algorithm work?
The K-means algorithm follows these steps:
- **Initialization:** Choose k random **centroids** from the dataset.
- **Assignment:** Assign each data point to the nearest centroid based on **Euclidean distance**, creating k clusters.
- **Update:** Recalculate the centroids by taking the mean of the data points assigned to each cluster.
- **Repeat:** Repeat the assignment and update steps until the centroids no longer change significantly.

```
python
from sklearn.cluster import KMeans

# Applying KMeans from scikit-learn
k = 3  # Number of clusters
kmeans = KMeans(n_clusters=k, random_state=42)

# Fit the KMeans model to the data
kmeans.fit(X)

# Get the cluster centers and labels
centroids = kmeans.cluster_centers_
labels = kmeans.labels_
```

## How do you choose the number of clusters (k) in K-means?
- **[Elbow Method](https://www.geeksforgeeks.org/elbow-method-for-optimal-value-of-k-in-kmeans/)**: It is a graphical tool used to determine the optimal number of clusters (k) in K-means. Selecting the right number of clusters is crucial for meaningful segmentation. The Elbow Method plotts the sum of squared distances (inertia) for different values of k. As k increases, inertia decreases. The "elbow" of the curve indicates the optimal value of k, where further increases in k result in only marginal improvements in inertia.
  ![Elbow Method](https://media.geeksforgeeks.org/wp-content/uploads/20241028173908396970/Elbow-Method.png)
- **[Silhouette Score](https://www.geeksforgeeks.org/silhouette-algorithm-to-determine-the-optimal-value-of-k/?ref=asr4)**: Measures how similar a data point is to its own cluster compared to other clusters.
  A higher score indicates better clustering.

## 4. What are the advantages and disadvantages of K-means clustering?

**Advantages:**
- **Simplicity**: K-means is easy to implement and computationally efficient.
- **Scalability:** It works well for large datasets.
- **Efficiency:** It often performs well when the clusters are compact and spherical.

**Disadvantages:**
- **Sensitive to Initialization**: Poor initial centroids can lead to suboptimal results. To overcome this **K-means++** method is used
- **Choosing k**: The number of clusters must be predefined, which is not always straightforward.
- **Assumes Spherical Clusters**: It works best when clusters are spherical and of similar size.
- **Sensitive to Outliers:** Outliers can significantly affect centroid placement and result in inaccurate clustering.

## 5. Why is it important to scale the data before applying K-means?
K-means uses Euclidean distance to assign data points to centroids. If features have different scales (e.g., one feature in the range 0-1 and another in the range 1000-10000),
the feature with the larger range will dominate the distance calculation. Scaling ensures that all features contribute equally to the distance metric.

## 6. Explain the K-means++ initialization method.
[K-means++](https://www.geeksforgeeks.org/ml-k-means-algorithm/) is an initialization method that spreads out the initial centroids by selecting the first centroid randomly and 
then choosing the next centroids based on their distance from the already chosen centroids. This helps in selecting better initial centroids,
reducing the chances of getting stuck in local minima and improving the algorithm’s performance compared to random initialization.

## 7. What is inertia in K-means clustering?
Inertia is the sum of squared distances between each data point and its assigned centroid. It is a measure of how well the clusters fit the data.
A lower inertia means the points are closer to their centroids, indicating better clustering.
However, inertia alone cannot guarantee the best model as it tends to decrease as the number of clusters (k) increases.

## 8. How can you handle outliers in K-means clustering?
Outliers can significantly affect K-means clustering, as they may pull centroids toward them. To handle outliers:

- **Use K-medoids:** K-medoids is a variant of K-means that uses actual data points as centroids, making it less sensitive to outliers.
- **Remove outliers:** Outliers can be identified and removed before applying K-means.
- **Use more robust algorithms:** Algorithms like DBSCAN or hierarchical clustering can handle outliers better than K-means.

## 9. What happens if you choose a very high or low value for k?
- **Low k (e.g., k=1):** The model will over-simplify the data, potentially putting all points into a single cluster and **missing underlying patterns**.
- **High k:** The model may **overfit the data**, creating many small, less meaningful clusters and reducing generalization.

Choosing k too low or too high can lead to poor results, which is why techniques like the Elbow Method and Silhouette Score are used to select an appropriate k.

## 10. What is the difference between K-means and hierarchical clustering?
- **K-means** is a partitional clustering algorithm that assigns each data point to one cluster and works by minimizing within-cluster variance.
- **Hierarchical clustering** builds a tree-like structure of clusters (dendrogram), allowing data points to belong to multiple clusters at different levels of hierarchy. It doesn't require k to be predefined.

## 11. How does K-means handle categorical data?
K-means works best with continuous numerical data, as it uses Euclidean distance for cluster assignment. For categorical data, the distance measure should be different (e.g., Hamming distance).
Alternatively, you can use algorithms like K-modes or K-prototype clustering that are designed specifically for categorical data.

## 12. Explain the convergence criteria in K-means.
K-means converges when the centroids do not change significantly between iterations, indicating that the algorithm has found stable clusters. The algorithm stops when either:

- The maximum number of iterations `max_iter` is reached.
- The change in centroid positions between iterations is less than a specified tolerance `tol`.

## 13. Can K-means clustering work with non-spherical clusters?
K-means works best with spherical (globular) clusters of roughly equal size and density. For non-spherical clusters, K-means may not perform well as it relies on Euclidean distance,
which is sensitive to the shape of the clusters. In such cases, other clustering algorithms like DBSCAN or Gaussian Mixture Models may be more effective.

## 14. What would you do if the K-means algorithm gets stuck in a local minimum?
- **Multiple initializations:** Run the algorithm multiple times with different random initializations and choose the result with the lowest inertia.
- **K-means++:** Use K-means++ initialization to improve centroid selection and avoid poor initial clusters.

---
# Reference
- [K-Means by Geesforgeeks](https://www.geeksforgeeks.org/k-means-clustering-introduction/)
