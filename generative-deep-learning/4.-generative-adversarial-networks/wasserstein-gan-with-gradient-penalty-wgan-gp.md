# Wasserstein GAN with Gradient Penalty (WGAN-GP)

* We will build a WGAN-CP to generate faces from the CelebA dataset
* Introduced in 2017
* With a few changes, the authors were able to show how to train GANs that have the following two properties

1. A meaningful loss metric that correlates with the generator’s convergence and sample quality
2. Improved stability of the optimization process

* The paper introduces the Wasserstein loss function for both the discriminator and the generator. Using this loss function instead of binary cross-entropy results in a more stable convergence of the GAN.
