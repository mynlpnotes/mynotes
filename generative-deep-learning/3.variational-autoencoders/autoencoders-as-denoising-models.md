# Autoencoders as Denoising Models

* Autoencoders can be used to clean noisy images
* <mark style="color:purple;background-color:purple;">**Since the encoder learns that it is not useful to capture the position of the random noise inside the latent space in order to reconstruct the original.**</mark>&#x20;
* For tasks such as this, a 2D latent space is probably too small to encode sufficient relevant information from the input.&#x20;
* However, increasing the dimensionality of the latent space quickly leads to problems if we want to use the autoencoder as a generative model.
