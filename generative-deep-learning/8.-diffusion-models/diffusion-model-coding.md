# Diffusion Model - Coding

```python
class DiffusionModel(models.Model):
    def __init__(self):
        super().__init__()
        self.normalizer = layers.Normalization()
        self.network = unet
        self.ema_network = models.clone_model(self.network)
        self.diffusion_schedule = cosine_diffusion_schedule

    ...

    def denoise(self, noisy_images, noise_rates, signal_rates, training):
        if training:
            network = self.network
        else:
            network = self.ema_network
        pred_noises = network(
            [noisy_images, noise_rates**2], training=training
        )
        pred_images = (noisy_images - noise_rates * pred_noises) / signal_rates

        return pred_noises, pred_images

    def train_step(self, images):
        images = self.normalizer(images, training=True) 
        noises = tf.random.normal(shape=tf.shape(images)) 
        batch_size = tf.shape(images)[0]
        diffusion_times = tf.random.uniform(
            shape=(batch_size, 1, 1, 1), minval=0.0, maxval=1.0
        ) 
        noise_rates, signal_rates = self.cosine_diffusion_schedule(
            diffusion_times
        ) 
        noisy_images = signal_rates * images + noise_rates * noises 
        with tf.GradientTape() as tape:
            pred_noises, pred_images = self.denoise(
                noisy_images, noise_rates, signal_rates, training=True
            ) 
            noise_loss = self.loss(noises, pred_noises)  
        gradients = tape.gradient(noise_loss, self.network.trainable_weights)
        self.optimizer.apply_gradients(
            zip(gradients, self.network.trainable_weights)
        ) 
        self.noise_loss_tracker.update_state(noise_loss)

        for weight, ema_weight in zip(
            self.network.weights, self.ema_network.weights
        ):
            ema_weight.assign(0.999 * ema_weight + (1 - 0.999) * weight) 

        return {m.name: m.result() for m in self.metrics}

    ...
```

* We first normalize the batch of images to have zero mean and unit variance
* Next, we sample noise to match the shape of the input images
* We also sample random diffusion times…
* …​and use these to generate the noise and signal rates according to the cosine diffusion schedule
* Then we apply the signal and noise weightings to the input images to generate the noisy images
* Next, we denoise the noisy images by asking the network to predict the noise and then undoing the noising operation, using the provided `noise_rates` and `signal_rates`
* We can then calculate the loss (mean absolute error) between the predicted noise and the true noise…
* …​and take a gradient step against this loss function
* The EMA network weights are updated to a weighted average of the existing EMA weights and the trained network weights after the gradient step
