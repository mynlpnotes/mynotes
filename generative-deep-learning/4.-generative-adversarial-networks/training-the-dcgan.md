# Training the DCGAN

* Architectures of the generator and discriminator in a DCGAN are very simple and not so different from the VAE models
* We can train the discriminator by creating a training set where some of the images are real observations from the training set and some are fake outputs from the generator.&#x20;
* We then treat this as a supervised learning problem, where the labels are 1 for the real images and 0 for the fake images, with binary cross-entropy as the loss function.
*
