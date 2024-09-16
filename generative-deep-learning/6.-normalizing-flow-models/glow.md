# GLOW

* 2018
* GLOW was one of the first models to demonstrate the ability of normalizing flows to generate high-quality samples and produce a meaningful latent space that can be traversed to manipulate samples.&#x20;
* The key step was to replace the reverse masking setup with invertible 1 × 1 convolutional layers.&#x20;
* For example, with RealNVP applied to images, the ordering of the channels is flipped after each step, to ensure that the network gets the chance to transform all of the input.&#x20;
* In GLOW a 1 × 1 convolution is applied instead, which effectively acts as a general method to produce any permutation of the channels that the model desires
