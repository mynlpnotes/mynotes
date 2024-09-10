# Training the CGAN

*

    ```python
    def train_step(self, data):
        real_images, one_hot_labels = data 

        image_one_hot_labels = one_hot_labels[:, None, None, :] 
        image_one_hot_labels = tf.repeat(
            image_one_hot_labels, repeats=64, axis = 1
        )
        image_one_hot_labels = tf.repeat(
            image_one_hot_labels, repeats=64, axis = 2
        )

        batch_size = tf.shape(real_images)[0]

        for i in range(self.critic_steps):
            random_latent_vectors = tf.random.normal(
                shape=(batch_size, self.latent_dim)
            )

            with tf.GradientTape() as tape:
                fake_images = self.generator(
                    [random_latent_vectors, one_hot_labels], training = True
                ) 

                fake_predictions = self.critic(
                    [fake_images, image_one_hot_labels], training = True
                ) 
                real_predictions = self.critic(
                    [real_images, image_one_hot_labels], training = True
                )

                c_wass_loss = tf.reduce_mean(fake_predictions) - tf.reduce_mean(
                    real_predictions
                )
                c_gp = self.gradient_penalty(
                    batch_size, real_images, fake_images, image_one_hot_labels
                ) 
                c_loss = c_wass_loss + c_gp * self.gp_weight

            c_gradient = tape.gradient(c_loss, self.critic.trainable_variables)
            self.c_optimizer.apply_gradients(
                zip(c_gradient, self.critic.trainable_variables)
            )

        random_latent_vectors = tf.random.normal(
            shape=(batch_size, self.latent_dim)
        )

        with tf.GradientTape() as tape:
            fake_images = self.generator(
                [random_latent_vectors, one_hot_labels], training=True
            ) 
            fake_predictions = self.critic(
                [fake_images, image_one_hot_labels], training=True
            )
            g_loss = -tf.reduce_mean(fake_predictions)

        gen_gradient = tape.gradient(g_loss, self.generator.trainable_variables)
        self.g_optimizer.apply_gradients(
            zip(gen_gradient, self.generator.trainable_variables)
        )
    ```
