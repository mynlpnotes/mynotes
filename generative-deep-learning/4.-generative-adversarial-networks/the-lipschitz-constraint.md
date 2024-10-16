# The Lipschitz Constraint

* We are now allowing the critic to output any number in the range (∞ , ∞ )
* The Wasserstein loss can therefore be very large, which is unsettling—usually, large numbers in neural networks are to be avoided!
* So we also need to place an additional constraint on the critic
* It is required that the critic is a 1-Lipschitz continuous function
* The critic is a function D that converts an image into a prediction. We say that this function is 1-Lipschitz if it satisfies the following inequality for any two input images, x1 and x2:
* ![](<../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)\\
* Here, |x1 - x2| |is the average pixelwise absolute difference between two images and |D(x1) - D(x2) | is the absolute difference between the critic predictions.
* We require a limit on the rate at which the predictions of the critic can change between two images (i.e., the absolute value of the gradient must be at most 1 everywhere).
