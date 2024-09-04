# Loss Function

* Previously we used only reconstruction loss
* Now we also use KL loss
* KL divergence is a way of measuring how much one probability distribution differs from another. In a VAE, we want to measure how much our normal distribution with parameters z\_mean and z\_log\_var differs from a standard normal distribution
* ```
  kl_loss = -0.5 * sum(1 + z_log_var - z_mean ^ 2 - exp(z_log_var))
  ```
* kl\_loss is minimized to 0 when z\_mean = 0 and z\_log\_var = 0 for all dimensions. As these two terms start to differ from 0, kl\_loss increases

How does this loss help?

1. We now have a well-defined distribution that we can use for choosing points in the latent space—the standard normal distribution
2. Since this term tries to force all encoded distributions toward the standard normal distribution, there is less chance that large gaps will form between point clusters
