# Analysis of the DCGAN

* As epoch increases more realistic images are produced
*

    <figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
* Another requirement of a successful generative model is that it doesn’t only reproduce images from the training set.&#x20;
* To test this, we can find the image from the training set that is closest to a particular generated example. A good measure for distance is the L1 distance
