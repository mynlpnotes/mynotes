# ML Challenges

1. Insufficient Quantity of Training Data
2. Nonrepresentative Training Data

* Your training data be representative of the new cases you want to generalize to
* If the sample is too small, you will have sampling noise (i.e., nonrepresentative data as a result of chance), but even very large samples can be nonrepresentative if the sampling method is flawed. This is called sampling bias.

3. Poor Quality Data:

* If your training data is full of errors, outliers, and noise (e.g., due to poor-quality measurements), it will make it harder for the system to detect the underlying patterns, so your system is less likely to perform well
* If some instances are clearly outliers, it may help to simply discard them or try to fix the errors manually.
* If some instances are missing a few features (e.g., 5% of your customers did not specify their age), you must decide whether you want to ignore this attribute altogether, ignore these instances, fill in the missing values (e.g., with the median age), or train one model with the feature and one model without it.

4. Irrelevant Features:

* Garbage in, garbage out
* If the training data contains enough relevant features and not too many irrelevant ones

Feature engineering, involves the following steps:

* Feature selection (selecting the most useful features to train on among existing features)
* Feature extraction (combining existing features to produce a more useful one⁠—as we saw earlier, dimensionality reduction algorithms can help)
* Creating new features by gathering new data

5. Overfitting the training data

* Means that the model performs well on the training data, but it does not generalize well
* if the training set is noisy, or if it is too small, then the model is likely to detect patterns in the noise itself. Obviously these patterns will not generalize to new instances
* Simplify the model by selecting one with fewer parameters
* Gather more training data.
* Reduce the noise in the training data
* Constraining a model to make it simpler and reduce the risk of overfitting is called regularization
* The amount of regularization to apply during learning can be controlled by a hyperparameter
* It is not affected by the learning algorithm itself; it must be set prior to training and remains constant during training. If you set the regularization hyperparameter to a very large value, you will get an almost flat model (a slope close to zero); the learning algorithm will almost certainly not overfit the training data, but it will be less likely to find a good solution

6. Underfitting the training data:

* When your model is too simple to learn the underlying structure of the data
* Predictions are bound to be inaccurate, even on the training examples.
* Select a more powerful model, with more parameters.
* Feed better features to the learning algorithm (feature engineering).
* Reduce the constraints on the model
