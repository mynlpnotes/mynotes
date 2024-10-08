# The Reverse Diffusion Process

* We build NN that can undo the noising process
* If we can do this, we can sample random noise from N(0, I) and then apply the reverse diffusion process multiple times in order to generate a novel image
*

    <figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* The difference between diffusion models and VAEs is that in a VAE the forward process (converting images to noise) is part of the model (i.e., it is learned), whereas in a diffusion model it is unparameterized.
* The focus in diffusion models is on learning the **reverse process** (denoising), which is where the trainable parameters are involved
* Same loss function as in a variational autoencoder
* we sample an image x0 and transform it by t noising steps to get the image xt.&#x20;
* We give this new image and the noising rate alpha to the neural network and ask it to predict noise, taking a gradient step against the squared error between the prediction noise and the true noise.
* Diffusion model actually maintains two copies of the network: one that is actively trained used gradient descent and another (the EMA network) that is an exponential moving average (EMA) of the weights of the actively trained network over previous training steps.
* The EMA network is not as susceptible to short-term fluctuations and spikes in the training process, making it more robust for generation than the actively trained network.&#x20;
* We therefore use the EMA network whenever we want to produce generated output from the network
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
