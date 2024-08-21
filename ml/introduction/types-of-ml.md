# Types of ML

1. Supervised learning:

* The training set you feed to the algorithm includes the desired solutions, called labels
*   &#x20;&#x20;

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
* Classification, Regression
* Note that some regression algorithms can be used for classification as well, and vice versa. For example, Logistic Regression is commonly used for classification, as it can output a value that corresponds to the probability of belonging to a given class (e.g., 20% chance of being spam)
*   &#x20;&#x20;

    <figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
* k-Nearest Neighbors
* Linear Regression
* Logistic Regression
* Support Vector Machines (SVMs)
* Decision Trees and Random Forests
* Neural networks

2. **Unsupervised Learning:**

* Training data is unlabeled

Clustering

* K-Means
* DBSCAN
* Hierarchical Cluster Analysis (HCA)

Anomaly detection and novelty detection

* One-class SVM
* Isolation Forest

Visualization and dimensionality reduction

* Principal Component Analysis (PCA)
* Kernel PCA
* Locally Linear Embedding (LLE)
* t-Distributed Stochastic Neighbor Embedding (t-SNE)

Association rule learning

* Apriori
* Eclat
* Clustering algorithm to try to detect groups of similar visitors
* If you use a hierarchical clustering algorithm, it may also subdivide each group into smaller groups. This may help you target your posts for each group.
*   &#x20;&#x20;

    <figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
* Visualization algorithms: you feed them a lot of complex and unlabeled data, and they output a 2D or 3D representation of your data that can easily be plotted
* Can understand how the data is organized and perhaps identify unsuspected patterns.
*

    <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
* Dimensionality reduction, in which the goal is to simplify the data without losing too much information. One way to do this is to merge several correlated features into one. For example, a car’s mileage may be strongly correlated with its age, so the dimensionality reduction algorithm will merge them into one feature that represents the car’s wear and tear. This is called feature extraction.
* Anomaly detection: detecting unusual credit card transactions to prevent fraud, catching manufacturing defects, or automatically removing outliers from a dataset before feeding it to another learning algorithm. The system is shown mostly normal instances during training, so it learns to recognize them; then, when it sees a new instance, it can tell whether it looks like a normal one or whether it is likely an anomaly
*   &#x20;&#x20;

    <figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>
* Association rule learning, in which the goal is to dig into large amounts of data and discover interesting relations between attributes

3. **Semisupervised learning:**

* Since labeling data is usually time-consuming and costly, you will often have plenty of unlabeled instances, and few labeled instances. Some algorithms can deal with data that’s partially labelled
*

    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

4. **Reinforcement Learning:**

* The learning system, called an agent in this context, can observe the environment, select and perform actions, and get rewards in return (or penalties in the form of negative rewards). It must then learn by itself what is the best strategy, called a policy, to get the most reward over time. A policy defines what action the agent should choose when it is in a given situation.
*   &#x20;&#x20;

    <figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

&#x20;
