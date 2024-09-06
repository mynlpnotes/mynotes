# Latent Space Arithemetic

* If we want to make a sad person, smile in the image
* We first need to find a vector in the latent space that points in the direction of increasing smile
* Each image in the CelebA dataset is labeled with attributes, one of which is Smiling.&#x20;
* If we take the average position of encoded images in the latent space with the attribute Smiling and subtract the average position of encoded images that do not have the attribute Smiling, we will obtain the vector that points in the direction of Smiling, which is exactly what we need
* `alpha` is a factor that determines how much of the feature vector is added or subtracted
* ```
  z_new = z + alpha * feature_vector
  ```
*

    <figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
