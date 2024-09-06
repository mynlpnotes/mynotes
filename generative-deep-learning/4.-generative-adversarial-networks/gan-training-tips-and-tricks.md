# GAN Training: Tips and Tricks

**Discriminator overpowers the generator:**

*   The discriminator perfectly learns to separate real images from fake images and the gradients vanish completely, leading to no training whatsoever

    **Suggestions to overcome:**
* Increase the rate parameter of the Dropout layers in the discriminator to dampen the amount of information that flows through the network
* Reduce the learning rate of the discriminator
* Reduce the number of convolutional filters in the discriminator
* Add noise to the labels when training the discriminator
* Flip the labels of some images at random when training the discriminator

**Generator overpowers the discriminator:**

* If the discriminator is not powerful enough, the generator will find ways to easily trick the discriminator with a small sample of nearly identical images.&#x20;
* **This is known as mode collapse**
* The generator would be inclined to find a single observation (also known as a mode) that always fools the discriminator and would start to map every point in the latent input space to this image.

**Uninformative Loss:**

* Since the deep learning model is compiled to minimize the loss function, it would be natural to think that the smaller the loss function of the generator, the better the quality of the images produced.&#x20;
* However, since the generator is only graded against the current discriminator and the discriminator is constantly improving, we cannot compare the loss function evaluated at different points in the training process.&#x20;
* Indeed, the loss function of the generator actually increases over time, even though the quality of the images is clearly improving.&#x20;
* This lack of correlation between the generator loss and image quality sometimes makes GAN training difficult to monitor.

**Hyperparameters:**

*
