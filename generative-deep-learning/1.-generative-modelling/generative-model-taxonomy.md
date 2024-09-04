# Generative Model Taxonomy

<figure><img src="../../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

Three possible approaches:

1. **Implicit density models:**

* Do not aim to estimate the probability density at all, but instead focus solely on producing a stochastic process that directly generates data
* Example: GAN

2. **Explicit Tractable models:**

* Place constraints on the model architecture, so that the density function has a form that makes it easy to calculate
* For example, autoregressive models impose an ordering on the input features, so that the output can be generated sequentially—e.g., word by word, or pixel by pixel.

3. **Explicit Approximate models:**

* Include variational autoencoders,  which introduce a latent variable and optimize an approximation of the joint density function

