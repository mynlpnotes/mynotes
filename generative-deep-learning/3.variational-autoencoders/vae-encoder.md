# VAE - Encoder

* Each image is instead mapped to a multivariate normal distribution around a point in the latent space
*

    <figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>
* The encoder only needs to map each input to a mean vector and a variance vector and does not need to worry about covariance between dimensions.&#x20;
* Variational autoencoders assume that there is no correlation between dimensions in the latent space
* Variance values are always positive, so we actually choose to map to the logarithm of the variance, as this can take any real number in the range (∞ , ∞ )
* To summarize, the encoder will take each input image and encode it to two vectors that together define a multivariate normal distribution in the latent space:
* z\_mean: The mean point of the distribution
* z\_log\_var: The logarithm of the variance of each dimension
* We can sample a point `z` from the distribution defined by these values using the following equation
* ```
  z = z_mean + z_sigma * epsilon
  z_sigma = exp(z_log_var * 0.5)
  epsilon ~ N(0,I)
  ```
*

    <figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>
* Previously, we saw that there was no requirement for the latent space to be continuous—even if the point (–2, 2) decodes to a well-formed image of a sandal, there’s no requirement for (–2.1, 2.1) to look similar. Now, since we are sampling a random point from an area around `z_mean`, the decoder must ensure that all points in the same neighborhood produce very similar images when decoded, so that the reconstruction loss remains small
