# Training with Contrastive Divergence

* We cannot apply maximum likelihood estimation, because the energy function does not output a probability; it outputs a score that does not integrate to 1 across the sample space
* We want to train the model to output large negative energy scores for real observations and large positive energy scores for generated fake observations so that the contrast between these two extremes is as large as possible
* We can calculate the difference between the energy scores of real and fake samples and use this as our loss function
* We can use our Langevin sampling procedure to generate a set of observations with low energy scores.&#x20;
* The process would need to run for infinitely many steps to produce a perfect sample (which is obviously impractical), so instead we run for some small number of steps, on the assumption that this is good enough to produce a meaningful loss function.
* We also maintain a buffer of samples from previous iterations, so that we can use this as the starting point for the next batch, rather than pure random noise
*

    ```python
    class Buffer:
        def __init__(self, model):
            super().__init__()
            self.model = model
            self.examples = [
                tf.random.uniform(shape = (1, 32, 32, 1)) * 2 - 1
                for _ in range(128)
            ] 

        def sample_new_exmps(self, steps, step_size, noise):
            n_new = np.random.binomial(128, 0.05) 
            rand_imgs = (
                tf.random.uniform((n_new, 32, 32, 1)) * 2 - 1
            )
            old_imgs = tf.concat(
                random.choices(self.examples, k=128-n_new), axis=0
            ) 
            inp_imgs = tf.concat([rand_imgs, old_imgs], axis=0)
            inp_imgs = generate_samples(
                self.model, inp_imgs, steps=steps, step_size=step_size, noise = noise
            ) 
            self.examples = tf.split(inp_imgs, 128, axis = 0) + self.examples 
            self.examples = self.examples[:8192]
            return inp_imgs
    ```
* The sampling buffer is initialized with a batch of random noise
* On average, 5% of observations are generated from scratch (i.e., random noise) each time
* The rest are pulled at random from the existing buffer
* The observations are concatenated and run through the Langevin sampler
* The resulting sample is added to the buffer, which is trimmed to a max length of 8,192 observations
* The scores of real observations are pushed down by the algorithm and the scores of fake observations are pulled up
