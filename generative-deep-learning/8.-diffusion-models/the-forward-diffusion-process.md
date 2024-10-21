# The Forward Diffusion Process

* Suppose we have an image x0 that we want to corrupt gradually over a large number of steps (say, T = 1000 ), so that eventually it is indistinguishable from standard Gaussian noise (i.e., xT should have zero mean and unit variance)
* We can define a function that adds a small amount of Gaussian noise with variance βt to an image Xt-1 to generate a new image . If we keep applying this function, we will generate a sequence of progressively noisier images ( x0, x1,...xT)
*

    <figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* εt-1 is a standard Gaussian with zero mean and unit variance
*

    <figure><img src="../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
* We also scale the input image xt-1, to ensure that the variance of the output image xt remains constant over time. This way, if we normalize our original image to have zero mean and unit variance, then xT will approximate a standard Gaussian distribution for large enough T
* Root terms are added in equation, to specify how much original image remains and how much noise gets added
