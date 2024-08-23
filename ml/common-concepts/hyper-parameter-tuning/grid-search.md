# Grid Search

* Which hyperparameters you want it to experiment with and what values to try out
*

    <figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
* The grid search will explore 12 + 6 = 18 combinations
*

    <figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
* If GridSearchCV is initialized with refit=True (which is the default), then once it finds the best estimator using cross-validation, it retrains it on the whole training set.&#x20;
* This is usually a good idea, since feeding it more data will likely improve its performance.
*

    <figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
