# Mixture Distributions

* Improvement for PixelCNN
* We reduced the output of the PixelCNN to just 4 pixel levels to ensure the network didn’t have to learn a distribution over 256 independent pixel values, which would slow the training process.
* However, this is far from ideal—for color images, we wouldn’t want our canvas to be restricted to only a handful of possible colors
* We can make the output of the network a _mixture distribution_, instead of a softmax over 256 discrete pixel values
* A mixture distribution is quite simply a mixture of two or more other probability distributions
* For example, we could have a mixture distribution of five logistic distributions, each with different parameters.&#x20;
* The mixture distribution also requires a discrete categorical distribution that denotes the probability of choosing each of the distributions included in the mix
*

    <figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>
*

    ```python
    import tensorflow_probability as tfp

    dist = tfp.distributions.PixelCNN(
        image_shape=(32, 32, 1),
        num_resnet=1,
        num_hierarchies=2,
        num_filters=32,
        num_logistic_mix=5,
        dropout_p=.3,
    ) 

    image_input = layers.Input(shape=(32, 32, 1)) 

    log_prob = dist.log_prob(image_input)

    model = models.Model(inputs=image_input, outputs=log_prob) 
    model.add_loss(-tf.reduce_mean(log_prob))
    ```
*

    <figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption><p>The difference from our previous examples is that now the full range of pixel values is being utilized</p></figcaption></figure>
