# Adding noise to the labels

* A useful trick when training GANs is to add a small amount of random noise to the training labels
* This helps to improve the stability of the training process and sharpen the generated images
* This _label smoothing_ acts as way to tame the discriminator, so that it is presented with a more challenging task and doesn’t overpower the generator
