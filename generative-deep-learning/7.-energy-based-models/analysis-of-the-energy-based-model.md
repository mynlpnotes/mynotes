# Analysis of the Energy-Based Model

*

    <figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

1. The loss calculated during the training step is approximately constant and small across epochs. While the model is constantly improving, so is the quality of generated images in the buffer that it is required to compare against real images from the training set, so we shouldn’t expect the training loss to fall significantly
2. To judge model performance, we also set up a validation process that doesn’t sample from the buffer, but instead scores a sample of random noise and compares this against the scores of examples from the training set. If the model is improving, we should see that the contrastive divergence falls over the epochs (i.e., it is getting better at distinguishing random noise from real images)
3.
