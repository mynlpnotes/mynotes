# CelebA - Analysis

* Successfully captured the key features of each face—the angle of the head, the hairstyle, the expression, etc. Some of the fine detail is missing
*

    <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
* Check that the distribution of points in the latent space approximately resembles a multivariate standard normal distribution.&#x20;
* If we see any dimensions that are significantly different from a standard normal distribution, we should probably reduce the reconstruction loss factor, since the KL divergence term isn’t having enough effect
*

    <figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
