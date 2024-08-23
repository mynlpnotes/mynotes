# Cross Validation

* Randomly splits the training set into 10 distinct subsets called folds, then it trains and evaluates the Decision Tree model 10 times, picking a different fold for evaluation every time and training on the other 9 folds.&#x20;
* The result is an array containing the 10 evaluation scores
*

    <figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>
* Scikit-Learn’s cross-validation features expect a utility function (greater is better) rather than a cost function (lower is better), so the scoring function is actually the opposite of the MSE (i.e., a negative value), which is why the preceding code computes -scores before calculating the square root.
