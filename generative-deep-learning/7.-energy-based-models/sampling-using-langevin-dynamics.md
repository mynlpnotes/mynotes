# Sampling Using Langevin Dynamics

* How to generate new samples to generate new samples that have a low score
* Langevin dynamics, which makes use of the fact that we can compute the gradient of the energy function with respect to its input.&#x20;
* If we start from a random point in the sample space and take small steps in the opposite direction of the calculated gradient, we will gradually reduce the energy function.&#x20;
* If our neural network is trained correctly, then the random noise should transform into an image that resembles an observation from the training set before our eyes
*

    <figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
* Above is gradient descent shown in 2 dimensional space with the energy function value on the third dimension
* The path is a noisy descent downhill, following the negative gradient of the energy function with respect to the input

**Difference w.r.t to NN:**

* In NN, we calculate gradient w.r.t loss and then using backpropagation we update the weights
* In langevin dynamic, we keep the weights fixed and calculate the gradients out the outputs w.r.t input, and then we update the input a small amount in the direction of the negative gradient



*

    ```python
    def generate_samples(model, inp_imgs, steps, step_size, noise):
        imgs_per_step = []
        for _ in range(steps): 
            inp_imgs += tf.random.normal(inp_imgs.shape, mean = 0, stddev = noise) 
            inp_imgs = tf.clip_by_value(inp_imgs, -1.0, 1.0)
            with tf.GradientTape() as tape:
                tape.watch(inp_imgs)
                out_score = -model(inp_imgs) 
            grads = tape.gradient(out_score, inp_imgs) 
            grads = tf.clip_by_value(grads, -0.03, 0.03)
            inp_imgs += -step_size * grads 
            inp_imgs = tf.clip_by_value(inp_imgs, -1.0, 1.0)
            return inp_imgs
    ```
* Loop over given number of steps
* Add a small amount of noise to the image
* Pass the image through the model to obtain the energy score
* Calculate the gradient of the output with respect to the input
* Add a small amount of the gradient to the input image
