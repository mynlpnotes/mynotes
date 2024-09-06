# Wasserstein Loss

* The generator tries to minimize the distance between the real and generated data distributions, using a measure called Wasserstein distance
* Here distribution of different features like pattern, colour, shapes etc is matched
* The discriminator outputs a probability (between 0 and 1) indicating whether an input is real or fake.
* The critic (sometimes still called a discriminator) doesn’t give a probability. Instead, it gives a real-valued score (which could be any positive or negative number) to each input.
* The critic's job is to give higher scores to real data and lower scores to generated data.
* In standard GANs, when the discriminator becomes too confident (outputting values close to 0 or 1), the generator can struggle to improve because the gradients (used to update the generator) become very small—this is called the vanishing gradient problem.
* In WGAN, because the critic outputs real-valued scores (which can be any number), the loss is smoother and provides more meaningful feedback to the generator, even when the generator’s outputs are far from real.

**Critic Loss:**

*   LD​=−Ex∼pdata​​\[C(x)]+Ez∼pz​​\[C(G(z))]

    Where:

    * x∼pdata​ refers to samples from the real data distribution.
    * z∼pz​ is a latent variable (random noise) fed into the generator.
    * G(z) is the generator’s output (generated data).
    * C(x) and C(G(z)) are the scores given by the critic for real data and generated data, respectively

**Generator Loss:**

* LG​=−Ez∼pz​​\[C(G(z))]
* Here, the generator tries to maximize the score C(G(z)) given to the generated data by the critic, which effectively minimizes the Wasserstein distance between real and generated data distribution
