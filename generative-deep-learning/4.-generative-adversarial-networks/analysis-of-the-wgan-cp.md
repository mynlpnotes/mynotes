# Analysis of the WGAN-CP

*

    <figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Output after 25 epochs</p></figcaption></figure>
* The model has learned the significant high-level attributes of a face, and there is no sign of mode collapse
* We can also see how the loss functions of the model evolve over time - the loss functions of both the critic and generator are highly stable and convergent
*

    <figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>
* If we compare the WGAN-GP output to the VAE output, we can see that the GAN images are generally sharper—especially the definition between the hair and the background.&#x20;
* This is true in general; VAEs tend to produce softer images that blur color boundaries, whereas GANs are known to produce sharper, more well-defined images
