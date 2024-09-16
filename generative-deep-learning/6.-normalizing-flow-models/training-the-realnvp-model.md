# Training the RealNVP Model

* We want to minimize the negative log-likelihood  -logpx(x) of the data under the model
*

    <figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>
* We choose the target output distribution pz(z) of the forward process to be a standard Gaussian, because we can easily sample from this distribution.&#x20;
* We can then transform a point sampled from the Gaussian back into the original image domain by applying the inverse process g
*

    <figure><img src="../../.gitbook/assets/image (51).png" alt=""><figcaption><p>Transforming between the complex distribution and a simple Gaussian in 1D (middle row) and 2D (bottom row)</p></figcaption></figure>
*

    ```python
    class RealNVP(models.Model):
        def __init__(self, input_dim, coupling_layers, coupling_dim, regularization):
            super(RealNVP, self).__init__()
            self.coupling_layers = coupling_layers
            self.distribution = tfp.distributions.MultivariateNormalDiag(
                loc=[0.0, 0.0], scale_diag=[1.0, 1.0]
            ) 
            self.masks = np.array(
                [[0, 1], [1, 0]] * (coupling_layers // 2), dtype="float32"
            ) 
            self.loss_tracker = metrics.Mean(name="loss")
            self.layers_list = [
                Coupling(input_dim, coupling_dim, regularization)
                for i in range(coupling_layers)
            ] 

        @property
        def metrics(self):
            return [self.loss_tracker]

        def call(self, x, training=True):
            log_det_inv = 0
            direction = 1
            if training:
                direction = -1
            for i in range(self.coupling_layers)[::direction]: 
                x_masked = x * self.masks[i]
                reversed_mask = 1 - self.masks[i]
                s, t = self.layers_list[i](x_masked)
                s *= reversed_mask
                t *= reversed_mask
                gate = (direction - 1) / 2
                x = (
                    reversed_mask
                    * (x * tf.exp(direction * s) + direction * t * tf.exp(gate * s))
                    + x_masked
                ) 
                log_det_inv += gate * tf.reduce_sum(s, axis = 1) 
            return x, log_det_inv

        def log_loss(self, x):
            y, logdet = self(x)
            log_likelihood = self.distribution.log_prob(y) + logdet 
            return -tf.reduce_mean(log_likelihood)

        def train_step(self, data):
            with tf.GradientTape() as tape:
                loss = self.log_loss(data)
            g = tape.gradient(loss, self.trainable_variables)
            self.optimizer.apply_gradients(zip(g, self.trainable_variables))
            self.loss_tracker.update_state(loss)
            return {"loss": self.loss_tracker.result()}

        def test_step(self, data):
            loss = self.log_loss(data)
            self.loss_tracker.update_state(loss)
            return {"loss": self.loss_tracker.result()}

    model = RealNVP(
        input_dim = 2
        , coupling_layers= 6
        , coupling_dim = 256
        , regularization = 0.01
    )

    model.compile(optimizer=optimizers.Adam(learning_rate=0.0001))

    model.fit(
        normalized_data
        , batch_size=256
        , epochs=300
    )
    ```
* The target distribution is a standard 2D Gaussian
* Here, we create the alternating mask pattern
* A list of `Coupling` layers that define the RealNVP network
* In the main `call` function of the network, we loop over the `Coupling` layers. If `training=True`, then we move forward through the layers (i.e., from data to latent space). If `training=False`, then we move backward through the layers (i.e., from latent space to data)
* This line describes both the forward and backward equations dependent on the `direction` (try plugging in `direction = -1` and `direction = 1` to prove this to yourself!
* The log determinant of the Jacobian, which we need to calculate the loss function, is simply the sum of the scaling factors
* The loss function is the negative sum of the log probability of the transformed data, under our target Gaussian distribution and the log determinant of the Jacobian
