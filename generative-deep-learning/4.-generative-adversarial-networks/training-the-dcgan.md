# Training the DCGAN

* Architectures of the generator and discriminator in a DCGAN are very simple and not so different from the VAE models
* We can train the discriminator by creating a training set where some of the images are real observations from the training set and some are fake outputs from the generator.&#x20;
* We then treat this as a supervised learning problem, where the labels are 1 for the real images and 0 for the fake images, with binary cross-entropy as the loss function.
* We can generate a batch of images and pass these through the discriminator to get a score for each image.&#x20;
* The loss function for the generator is then simply the binary cross-entropy between these probabilities and a vector of ones, because we want to train the generator to produce images that the discriminator thinks are real
* We must alternate the training of these two networks, making sure that we only update the weights of one network at a time
*

    <figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption><p>Gray boxes indicate that the weights are frozen during training</p></figcaption></figure>
*

    ```python
    class DCGAN(models.Model):
        def __init__(self, discriminator, generator, latent_dim):
            super(DCGAN, self).__init__()
            self.discriminator = discriminator
            self.generator = generator
            self.latent_dim = latent_dim

        def compile(self, d_optimizer, g_optimizer):
            super(DCGAN, self).compile()
            self.loss_fn = losses.BinaryCrossentropy() 
            self.d_optimizer = d_optimizer
            self.g_optimizer = g_optimizer
            self.d_loss_metric = metrics.Mean(name="d_loss")
            self.g_loss_metric = metrics.Mean(name="g_loss")

        @property
        def metrics(self):
            return [self.d_loss_metric, self.g_loss_metric]

        def train_step(self, real_images):
            batch_size = tf.shape(real_images)[0]
            random_latent_vectors = tf.random.normal(
                shape=(batch_size, self.latent_dim)
            ) 

            with tf.GradientTape() as gen_tape, tf.GradientTape() as disc_tape:
                generated_images = self.generator(
                    random_latent_vectors, training = True
                ) 
                real_predictions = self.discriminator(real_images, training = True) 
                fake_predictions = self.discriminator(
                    generated_images, training = True
                ) 

                real_labels = tf.ones_like(real_predictions)
                real_noisy_labels = real_labels + 0.1 * tf.random.uniform(
                    tf.shape(real_predictions)
                )
                fake_labels = tf.zeros_like(fake_predictions)
                fake_noisy_labels = fake_labels - 0.1 * tf.random.uniform(
                    tf.shape(fake_predictions)
                )

                d_real_loss = self.loss_fn(real_noisy_labels, real_predictions)
                d_fake_loss = self.loss_fn(fake_noisy_labels, fake_predictions)
                d_loss = (d_real_loss + d_fake_loss) / 2.0 

                g_loss = self.loss_fn(real_labels, fake_predictions) 

            gradients_of_discriminator = disc_tape.gradient(
                d_loss, self.discriminator.trainable_variables
            )
            gradients_of_generator = gen_tape.gradient(
                g_loss, self.generator.trainable_variables
            )

            self.d_optimizer.apply_gradients(
                zip(gradients_of_discriminator, discriminator.trainable_variables)
            ) 
            self.g_optimizer.apply_gradients(
                zip(gradients_of_generator, generator.trainable_variables)
            )

            self.d_loss_metric.update_state(d_loss)
            self.g_loss_metric.update_state(g_loss)

            return {m.name: m.result() for m in self.metrics}

    dcgan = DCGAN(
        discriminator=discriminator, generator=generator, latent_dim=100
    )

    dcgan.compile(
        d_optimizer=optimizers.Adam(
            learning_rate=0.0002, beta_1 = 0.5, beta_2 = 0.999
        ),
        g_optimizer=optimizers.Adam(
            learning_rate=0.0002, beta_1 = 0.5, beta_2 = 0.999
        ),
    )

    dcgan.fit(train, epochs=300)
    ```

1. The loss function for the generator and discriminator is `BinaryCrossentropy`
2. To train the network, first sample a batch of vectors from a multivariate standard normal distribution
3. Next, pass these through the generator to produce a batch of generated images
4. Now ask the discriminator to predict the realness of the batch of real images…
5. …​and the batch of generated images
6. The discriminator loss is the average binary cross-entropy across both the real images (with label 1) and the fake images (with label 0)
7. The generator loss is the binary cross-entropy between the discriminator predictions for the generated images and a label of 1
8. Update the weights of the discriminator and generator separately



* The discriminator and generator are constantly fighting for dominance, which can make the DCGAN training process unstable.
* Ideally, the training process will find an equilibrium that allows the generator to learn meaningful information from the discriminator and the quality of the images will start to improve.&#x20;
* After enough epochs, the discriminator tends to end up dominating
*

    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
